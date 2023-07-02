+++
title = "Crust's Device (WIP)"
tags= ["rust", "C"]
+++

\toc

## Overview
From the beginning of my foray into programming, I've been pretty intrigued by one of the most well-known, and controversial pieces of code ever written:

@@dark-pink,f2,bold,avenir,pa1,center,relative,glow
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

	send(to, from, count) /* 1. */ 
	register short *to, *from; /* 2. */ 
	register count; /* 3. */ 
	{
		register n=(count+7)/8; /* 4. */ 
		switch(count%8){ /* 5. */ 
		case 0:	do{	*to = *from++; /* 6. */ 
		case 7:		*to = *from++; /* 7. */ 
		case 6:		*to = *from++; /* ... */ 
		case 5:		*to = *from++;  
		case 4:		*to = *from++;  
		case 3:		*to = *from++; 
		case 2:		*to = *from++; /* ... */ 
		case 1:		*to = *from++; /* 13. */ 
			}while(--n>0);
		}
	}
```
Here's the same code, in terms of functionality, with the while loop and the switch statement separated from each other.

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
`send` is a function signature, indicating the types of values expected by the function:

- *to & from* are *pointers* (variables which contain memory addresses of other variables, as their value), with the former two being pointers to *short*, and *count* being a variable for the number of elements to be copied between registers (areas within hardware that firmware can read to/write from).




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

## Footnotes

[^1]: [Tom Duff on Duff's Device](https://www.lysator.liu.se/c/duffs-device.html)
[^2]: The term used in the above email was `sobleq`, which I've changed to subleq, making a comfortable assumption due to the similarity of the instructions, that they're effectively the same, and for familiarity to modern readers- however I did find a text file containing the [CVAX CPU Chip Microcode Documentation](https://pdp-11.ru/simh_trailing-edge_com/semi/docs/cvaxudoc.txt), from the PDP-11, dated ~4 years after the invention of Duff's Device, containing what I believe is the actual instruction he was referencing. I'm not familiar enough with assembly to be certain they are the same, but in the documentation `sobleq` takes two arguments, and branching is mentioned (in terms of cycle cost), so I'm acceptably comfortable with this bit of technical/historical innacuracy. If anyone can explain the instruction(s) with a bit more detail, I can be reached at overoxidized@protonmail.com, and will update this article with credit given, of course.
[^3]: [Duff Code Pseudo](https://www.drdobbs.com/a-reusable-duff-device/184406208)