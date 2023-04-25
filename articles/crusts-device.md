+++
title = "Crust's Device (WIP)"
tags= ["rust", "C"]
+++

\toc

## Overview
From the beginning of my foray into programming, I've been pretty intrigued by one of the most well-known, and controversial pieces of code ever written:

@@dark-pink,f2,bold,avenir,pa1,center,relative
Duff's Device.
@@

The history behind it actually starts at the intersection of two cornerstones of nerd/geek culture: programming, and Lucasfilm. 

In 1983, Tom Duff was working for the film studio, possibly the subsidiary known as ILM- Industrial Light & Magic, on an animation program, using the Evans & Sutherland Picture System II, and discovered that there was a bottle-neck in the program, which was hindering the speed at which it could process the necessary data.

According to Tom, the original loop (shown below), was a bottle-neck for the animation play-back program[^1], that was resulting in a 50% decrease in the speed at which the program executed.


## Analyzing The Code

The original loop:

```C
    send(to, from, count)
    register short *to, *from;
    register count;
    {
        do
            *to = *from++;
        while(--count>0);
    }

```

Tom Duff states that the Vax C compiler, compiles the original loop into a movw, and a sobleq, instructions in assembly language: movw copies the data from the first operand, to the second operand, which are both registers, i.e `movw %CS 5(%ebx)`, and sobleq, an operation similar to subleq[^2], which takes three arguments, all memory addresses, and subtracts the data in the second operand, from the the data in the second operand, storing the result in the address of the second operand, and jumping to the memory address in the third operand, if the value stored in the second operand is less than or equal to zero.

The idea that lead to the in(genius/famous) piece of code, was borne out of Tom's in depth understanding of C and assembly, which both allowed him to percieve the limitation inherent in the situation, and subsequently surpass it. The loop as written, compiled to assembly, that had an unecessary number of sobleq instructions- or at least a number that could be decreased with some sophisticated technical optimization.

```C

	send(to, from, count)
	register short *to, *from;
	register count;
	{
		register n=(count+7)/8;
		switch(count%8){
		case 0:	do{	*to = *from++;
		case 7:		*to = *from++;
		case 6:		*to = *from++;
		case 5:		*to = *from++;
		case 4:		*to = *from++;
		case 3:		*to = *from++;
		case 2:		*to = *from++;
		case 1:		*to = *from++;
			}while(--n>0);
		}
	}
```

Here's the same code, in terms of funcionality, with the while loop and the switch
statement separated from each other.

```C
send(to, from, count)
register short *to, *from;
register count;
{
    register n = (count + 7) / 8;
    switch (count % 8) {
        case 0: *to = *from++;
        case 7: *to = *from++;
        case 6: *to = *from++;
        case 5: *to = *from++;
        case 4: *to = *from++;
        case 3: *to = *from++;
        case 2: *to = *from++;
        case 1: *to = *from++;
    }
    while (--n > 0) {
        *to = *from++;
        *to = *from++;
        *to = *from++;
        *to = *from++;
        *to = *from++;
        *to = *from++;
        *to = *from++;
        *to = *from++;
    }
}
```

## Crust's Device: C -> Rust

So, in my desire to get understand Rust better, I decided to try and port this famous bit of C code to Rust[^3]
```Rust

let (*mut to, *mut from, count) = (u32, u32, u32);

fn send(to: *mut T, from *mut T, count: u32) {

    let n = (count + 7) / 8;
    while (n > 0) {
        n -= 1
        match (count % 8) {
            case_0 => { *to = (*from += 1)},
            case_7 => { *to = (*from += 1)},
            case_6 => { *to = (*from += 1)},
            case_5 => { *to = (*from += 1)},
            case_4 => { *to = (*from += 1)},
            case_3 => { *to = (*from += 1)},
            case_2 => { *to = (*from += 1)},
            case_1 => { *to = (*from += 1)},
        }

        todo!()
}
```

Alright, so the code doesn't look too different, but there will most certainly be some interesting opinions from the type system.

As a first approximation, one can think of a repository as a single file represented by a directed graph $G = (V, E)$ of lines of text, where each vertex $v\in V$ represents a line of text, and an edge from $u \in V$ to $v\in V$, labelled with a change (also called patch) number $c$, could be read as “according to change $c$, line $u$ comes before $v$”.

This means that changes may introduce both vertices and edges, as in the following example, where a line of text $D$ is introduced between $A$ and $B$:

https://pijul.org/manual/repos-line-add.svg


Here, the thick arrow represents a change $c_0$ from a file containing the lines $A$, $B$, $C$, to a file which includes the line $D$. As mentioned above, the edges are labelled with the change that introduced them, in this case $c_0$. An important feature to note is that vertices are uniquely identified, by the hash of the change that introduced them, along with a position in that change. This means that two lines of text with the same content, introduced by different changes, will be different. It also means that a line keeps its identity, even if the change is applied in a totally different context.

Moreover, this system is append-only, in the sense that deletions are handled by a more sophisticated labelling of the edges. In the example above, if we want to delete line $D$, we just need to make a change mapping the edge introduced by $c_0$ to a deleted edge, which is also labelled with the change in which it was introduced, this time $c_1$:


From now on, we call the full edges alive, and the dashed ones dead.

We have just described the two basic kinds of actions in Pijul. There are no other. One kind adds vertices to the graph, along with “alive” edges around them, and the other kind maps an existing edge label onto a different one. The edge labels are fully described by two parameters: (1) their status (alive, deleted, and a few others related to multiple files and technical details explained below), and (2) the change that introduced them.

Dependencies

This scheme allows one to define dependencies between changes:

If a change $c$ adds a vertex, we must have its “context”, i.e. the lines before and after it, hence the changes that introduced these lines are in the dependencies of $c$.

If a change $c$ deletes a vertex, or in other words maps an existing edge introduced by a change $d$, then $c$ must depend on $d$.

Of course, this is just the minimal set of dependencies needed to make sense of the text edits. Hooks and scripts may add extra language-dependent dependencies based on semantics.

Are edge labels minimal?

Our goal is to find the smallest possible system, both for reasons of mathematical aesthetics (why store useless stuff?) and the other one for performance. Therefore, one immediate question comes to mind: why even keep the change number on the edges?

In order to answer that question, suppose we don’t keep the labels, meaning that the maps happen between statuses only. Then, consider the following two situations:

Change inverses

The first issue happens when two authors delete a line in parallel, and one of the authors reverts their change. Applying these changes yields the following diagram, where the two deletions get merged into one, and the inverse applies to both:


However, this is not what we expect, since one of the authors explicitly reverted the deletion, while the other performed the same deletion in parallel. By keeping the labels, this is what we get instead:


Missing contexts

For the sake of clarity, in the rest of this post, we name two users Alice (with pronouns “she/her”) and Bob (with pronouns “he/his”).

In this scenario, Alice writes something in the middle of a paragraph $p$, while Bob deletes $p$ in parallel. One issue here is that the situation is not symmetric: when Bob applies Alice’s change, he can tell immediately that something is wrong, because the context of Alice’s edits is labelled as deleted in his repository.


However, Alice’s situation is different: indeed, consider the case where instead of deleting $p$ in parallel of her changes, Bob deleted $p$ after applying Alice’s change. The edges deleted are exactly the same, but this is not a conflict, as shown in the following diagram:


The situation is further complicated by the fact that this system doesn’t behave symmetrically with the contexts above and below the new line. Indeed, if Bob deleted the down context of the line (i.e. if he deleted line $C$) instead of the up context (line $B$), Alice could detect the conflict, since in that case, $C$ would have both an alive and a dead edge pointing to it ($C$ is called a “zombie vertex” internally), as shown in the following diagram:


Keeping the change identifiers on each edge allows us to solve this. Bob adds the labels of all the edges around the deleted lines to the dependencies of his change. Then, Alice can tell whether Bob knows of her change before applying it. The changes are conflict if and only if Bob doesn’t know of the new lines.

Conflicts and CRDTs

According to what we described so far, there are three types of conflicts in Pijul:

Two alive vertices that do not have a (directed) path between them, in either direction.
Two alive vertices have paths in opposite directions between them, meaning that the graph has a cycle.
Or zombie vertices.
Moreover, it is easy to show that Pijul implements a conflict-free replicated datatype (CRDT): indeed, we’re just adding vertices and edges to a graph, or mapping edge labels which we know exist because of dependencies.

However, Pijul’s datastructure models, in a conflict-free way, the conflicts that can happen over a text file. In fact, Pijul would remain a CRDT with or without the design choices explained above about edge labels: for example, we could decide that the “deleted” status has higher precedence. But as shown above, that wouldn’t model conflicts accurately.

Pseudo-edges

Moving back to the sequential (i.e. single-user) situation, suppose we start a file with many lines. Our user deletes all of them, adds one new line at the very beginning, and one at the very end, as shown in the following diagram:


If we represented this situation naively like in that diagram, the complexity of applying changes and outputting the repository would depend linearly on the size of the graph, as we would need to traverse the entire thing to know about line $C$, and know it comes after $B$.

The trick is to use what we call “pseudo-edges”, which are not part of any change, but are just here to keep the “alive subgraph” (the subgraph of the alive vertices) connected. Every time we delete an edge, we add pseudo-edges between the source of the edge and all the descendants of the target, like the dotted edge in the graph below:


Multiple files

The extension of this scheme to multiple files is done in the following way:

We introduce another type of edge label to indicate that edges represent files, and hence are not be transitive. In particular, when we delete a file, all descendant vertices below must be deleted.

Each file or directory is represented by two separate vertices: one is its name, the other one is an “inode” vertex representing the file itself. This allows directory renames to commute with file renames, and file renames to commute with edits at the beginning of the file. The naive representation where files are represented as just their name would cause the kind of conflicts described above when the contexts of new vertices are deleted in parallel.

The non-conflicting case is where the graph of alive files, reduced by contracting the edges from and to name vertices, is a tree, and each file has exactly one unique name.

Negating this last sentence yields four different types of conflicts:

First, the graph of alive files can be disconnected, when a file is introduced in a directory deleted in parallel. When that happens, we double the deleted graph path with a path of pseudo-edges.
Another kind of conflict is when a file $a$ is renamed in parallel, to $b$ by Alice, and to $c$ by Bob. This includes the case where a file gets moved to two different directories, yielding a non-tree DAG.
Yet another one is when two different files are given the same name in parallel.
Finally, one can create a cyclic graph of directories: starting from two directories $a$ and $b$ at the root of the repository, Alice can move $a$ to a subdirectory $b/a$ of $b$, while Bob moves $b$ to a subdirectory $a/b$ of $a$.


## A less naive representation

We now revisit the first two diagrams in this post: adding and deleting lines. Vertices are now referenced by a change number (for example $c_0$) and a byte interval in that change (for example $[0, n[$, which means “bytes from offset $0$ included to offset $n$ excluded”). Note that vertices can now represent an arbitrary number of lines. Moreover, the size they occupy in memory is independent from $n$ (assuming $n < 2^{64}$).

Starting from a single vertex $c_0:[0, n[$ with $n$ bytes (containing an arbitrary number of lines), introduced by change $c_0$, adding a line is done by first splitting $c_0:[0, n[$ at some offset $i < n$, and inserting the new vertex just like before.

This means in particular that the splitting of content into lines is done by the diff algorithm and is encoded in the changes, instead of being set in stone for all repositories. With a different diff algorithm, we could imagine splitting contents according to programming language structure.


Once we know how to split vertices, deletions are handled almost as before: as shown in the following diagram, where we first apply the same change $c_1$ as in the previous example, and go on to applying change $c_2$, which deletes the end of vertex $c_0: [0, i[$ from some $j < i$ to $i$, and the beginning of vertex $c_1:[0, m[$, from $0$ to some $k < m$.


One important difference with before is that our previous edges had two different roles which were not clearly distinguishable from one another until now. One of these meanings was to order the lines, and the other one was the status. However, now that vertices can be split, the “status” role of edges becomes ambiguous: for example, a deleted edge pointing to vertex some vertex $c:[i, j[$ means that bytes $[i, j[$ of change $c$ are deleted, but what if we split that vertex into $c:[i, k[$ and $c: [k, j[$? 

Should we add an extra deleted edge, and if so, where?

There is a simple solution: by introducing a new kind of edge label (named BLOCK in the source code) we can distinguish between “internal” or “implicit” edges that are only here to order the blocks, and “status” edges informing about the status of their target vertex. I’ll probably explain more about this in a future blog post, or in the manual, or in a paper.

Version identifiers

Version identifiers need more sophistication in Pijul than in other version control systems, because any two patches $c_0$ and $c_1$ that could be produced independently commute, meaning that applying $c_1$ after $c_0$ yields the same repository as applying $c_0$ after $c_1$, and we want version identifiers to reflect that.

This means that meaningful version identifiers must be independent from the order. While this could be achieved easily with any linear function of the hashes, for example taking the bitwise XOR of hashes, some naive schemes have the problem that servers could trick clients into accepting that versions are synchronised, even though they are not. The bitwise XOR described above has this problem, and so do other linear functions: since the hashes are random, there is a high probability that any $n$ hashes form an independent linear basis of the vector space of hashes. The problem of forging a version identity becomes easy, as it is just a matter of solving a linear equation.

Our new scheme for version identifiers comes from the discrete log problem. The version identifier of an empty repository is always the identity element $1$, and applying a change with hash $h$ on top of version $V = e^{v}$ is $V^h = e^{v\cdot h}$.

Now, because getting from $V$ to the exponent $v$ is hard (at least for a classical computer), forging a version identity is hard, since we would need to generate hashes whose multiplication is $v$, without even knowing what $v$ is.

As pointed by Dan Robertson, this scheme is similar to homomorphic hashing.
## Footnotes

[^1]: [Tom Duff on Duff's Device](https://www.lysator.liu.se/c/duffs-device.html)
[^2]: The term used in the above email was `sobleq`, which I've changed to subleq, making a comfortable assumption due to the similarity of the instructions, that they're effectively the same, and for familiarity to modern readers- however I did find a text file containing the [CVAX CPU Chip Microcode Documentation](https://pdp-11.ru/simh_trailing-edge_com/semi/docs/cvaxudoc.txt), from the PDP-11, dated ~4 years after the invention of Duff's Device, containing what I believe is the actual instruction he was referencing. I'm not familiar enough with assembly to be certain they are the same, but in the documentation `sobleq` takes two arguments, and branching is mentioned (in terms of cycle cost), so I'm acceptably comfortable with this bit of technical/historical innacuracy. If anyone can explain the instruction(s) with a bit more detail, I can be reached at overoxidized@protonmail.com, and will update this article with credit given, of course.
[^3]: [Duff Code Pseudo](https://www.drdobbs.com/a-reusable-duff-device/184406208)