+++
title = "Why Functional Programming Matters"
tags = ["programming"]
+++

__Abstract__: *As software grows in complexity, it is more important to structure it properly. Well structured software is easier to debug, and provides a collection of re-usable components. This paper, focuses on two aspects of functional languages, which are higher-order functions, and lazy evaluation*.

## 1. Introduction

Functional programming is called so because the main operation is the application of functions to arguments.
Typically, functions are built up from language primitives.
Functions contain no side-effects, meaning a function can have no effect other than to compute its result.

This makes the order of execution irrelevant, since expression values don't change, allowing them to be evaluated at any time.
One can (or at least should be able to) replace functions with definitions, and variables with values, (and vice versa), without changing the behavior of the program, which is called referential transparency.

- In pure FP, a function has no side-effects. Functions are deterministic. This is called referential transparency, and allows the compiler to reason about the program, and you to easily deduce that a function is correct.
- A function takes one or more inputs, performs some operation, and returns a value. If the output only depends on the input, then the function is *pure* or has *referential transparency*.

## 2. An Analogy with Structured Programming.

Structured programs contain no `goto` statements, and blocks in a structured program do not have multiple entries or exits. The most important distinction between structured and unstructured programs is that structured programs are designed modularly, which allows for quicker extension and more efficient debugging.

### 3. Gluing Functions Together.

The first of the two new kinds of glue, enables simple functions to be able to be glued together to make more complex ones.

This can be illustrated with a list processing problem: adding elements of a list.

$listof\; *::= Nil\; |\; Cons * (listof *)$

This states that a list of $*s$ (whatever * is), is either $Nil$, representing an empty lit, or a $Cons$ of a $*$ and another list of $*s$.

A $Cons$ represents a list whose first element is the $*$, and whose second and subsequent elements are the elements of the other list of $*s$.
Here, $*$ may stand for any type.

The elements of a list can be summed recursively: the function $sum$ must be defined for two kinds of argument: an empty list, and a list with elements.

Given that the sum of no numbers is zero, we define: 
    $sum\; Nil\; = 0$.

Since the sum of a $Cons$ can be calculated by adding the first element of the list, to the sum of the others, we can define:
    $sum\; (Cons\; n\; list) = num\; +\; (sum\; list)$.

Since only the 0 and plus sign are specific to computing a sum, the computation of a sum, can modularized by creating a recursive pattern with the specific parts, often called __foldr__, so we can define sum for $Nil$ and a $Cons$ as:

- $sum = foldr\; (+)\; 0$.

__Modularity via parameterization.__

This definition can be derived by parameterizing the definition of sum:
- Parameterization is the the term for labeling arguments as functions of a variable.
- Remember, parameters are placeholders for arguments.

Sum is the process of aggregating a list of elements into a single element, and we usually take the head element, and the list, and continue recursively, as we're iterating through a list from left to right (or **__fold__**ing **__r__**ight), and applying a function $f$ to a value $x$.

$foldr\;\;f\;\;x\;\; Nil\; = x$.
    
 $(foldr f x)\; (Cons\; a\; l) = f\; a\; ((foldr f x)\; l)$ 
    
- Here we bracket $(foldr f x)$ to show that it replaces sum.


A function of three arguments, such as __foldr__, applied to only two, can be thought of as a function of the one remaining argument, and in general, a function of __n__ arguments, applied to __m__ of them, can be thought of as a function taking __n__- __m__ remaining arguments. 
Now that we've abstracted summation away from numbers, we can apply __foldr__ to lists of different types of elements, with different functions, such as multiplying the elements of the list:
    
- $product = foldr\;\; (*)\; 1$.

- $anytrue = foldr\;\; (\lor)\; False$.

- $alltrue - foldr\;\; (\land)\; True$.
    
