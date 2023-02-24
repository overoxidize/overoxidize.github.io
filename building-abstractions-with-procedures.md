+++
title = "Building Abstractions With Procedures"
hascode = true
tags = ["Building Abstractions With Procedures", "lisp"]
+++
@def hascode = true
\toc

> The acts of the mind, wherein it exerts its power over simple ideas, are chiefly these three: 1. Combining several simple ideas into one compound one, and thus all complex ideas are made. 2. The second is bringing two ideas, whether simple or complex, together, and setting them by one another so as to take a view of them at once, without uniting them into one, by which it gets all its ideas of relations. 3. The third is separating them from all other ideas that accompany them in their real existence: this is called abstraction, and thus all its general ideas are made. - John Locke, An Essay Concerning Human Understanding (1690)

We begin with the study of computational processes, the result of executing programs on properly working CPU's.

To study these, we'll use a version of Lisp, a family of languages, the eldest of which was implemented by John McCarthy, as based on his paper "Recursive Functions of Symbolic Expressions and Their Computation by Machine". The name is an acronym for the phrase "LISt Processing", and provides the manipulation of symbols, with the inclusion of code as data. The dialect used here is Scheme.

### The Elements of Programming
#### 1.1 Primitive expressions
A program, as built in a powerful programming language, provides the three following mechanisms:

- primitive expressions: the simplest entities in the language.

- means of combination: the techniques for compounding simple entities into complex ones.

- means of abstraction: the tools for naming compound elements to use them as units (*or, dare I say, primitives*).

#### 1.1.1 Expressions

Expressions, when *evaluated* by the interpreter, results in some value being displayed in the terminal.

These can in term be compounded with primitive operations, to yield compound expressions, such as the application of addition to numbers `(+ a b)`.

* One particular oddity of lisp, is the prefix notation, where operators are placed in front of a series of arguments, as opposed to interleaved between them, allowing for arithmetic operators to be n-ary, as opposed to binary.

This ability extends into combinations of nested expressions, which can be
made more legible to the human eye via *pretty-printing*, which will be handled by the read-eval-print-loop (repl) in the terminal.
```scheme
(+ (* 3 
        (+ (* 2 4) 
            (+ 3 5))) 
    (+ (- 10 7) 
        6))
```

#### 1.1.2 Naming & the Environment

A foundational tool in programming is naming, by which a variable is associated with some value, which is done with the *define* keyword in Scheme, i.e:

```scheme
(define one_hundred 100)

(define pi 3.14159)

(define (circumference radius)
    (* 2 pi radius))
```
```lisp
(defun)
```

Source code itself is not an explanation for what the code does: try writing the program in a conditional flattened, linear way, in english, and then observe the difference.