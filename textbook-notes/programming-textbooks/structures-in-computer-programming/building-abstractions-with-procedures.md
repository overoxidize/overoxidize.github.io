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


Define is the fundamental tool for abstraction, and allows for referring to complex operations with simple symbols. Computational objects can be complex, and having to remember implementation details every time we want to use them, would be unfeasible.

Because the interpreter is required to keep track of and retrieve symbol associated values, it requires a memory, of sorts, which is typicalled called the environment, and computation can involve a number of these.

#### 1.1.3 Evaluating Combinations

When evaluating combinations, the interpreter evaluates sub-expressions, and applies the value of the left-most sub-expr, typically the operator, to the other sub-expr's, which are typically operands.

The evaluation rule is recursive, or having the ability to refer to itself in one of its steps.

```scheme 
(* (+ 2 (* 4 6))
    (+ 3 5 7))
```
The evaluation of this code can be represented in a n-ary tree, given that there isn't a limit on the number of sub-expr's a given expression can have, based on the way the interpreter works through applying operations to operands, starting from the terminal nodes, with the results of operations being passed upwards- this is often referred to as tree accumulation.

The evaluation of primitives is as follows:

- Values of numerals are just that number.
- Values of built-in operators are the associated machine code.
- The values of other names are the objects associated with them in that environment.
  
The environment plays an important role in assessing the meaning of expressions, as it provides a context in which evaluation can take place.

There are exceptions to the evaluation rule, which are the special forms:

```scheme 
(define x 3)
```

The interpreter doesn't apply define to 3, and `x`, as the role of the keyword is to associate the two as a value and a name.

Each special form has its own evaluation rule.

#### 1.1.4 Compound Procedures

Procedure definitions, are an even more powerful method of abstracting that we can take advantage of, because they allow for the naming of compound operations:

```scheme
(define (square x) (* x x))
```

This is a compound procedure, that multiplies something by itself, which will be the named argument defined in the procedure, and some associated value.

Generally procedures need a name, a list of formal parameters, and a body, describing what should be done with the list of formal parameters, and that will yield the result of that computation.

Because we can refer to the square operation, we can use it as a building block for a more involved procedure, like sum-of-squares:

```scheme
(define (sum-of-squares x y)
    (+ (square x) (square y)))
```

And again:

```scheme
(define (f a )
    (sum-of-squares (+ a 1) (* a 2)))
```

TBD: 1.1.5 The Substitution Model for Procedure Application