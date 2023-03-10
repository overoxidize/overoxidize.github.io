+++
title ="Ch.1: Vector Spaces"
tags = ["mathematics", "linear-algebra-done-right", "linear algebra"]
+++

\toc 

## Intro 

Linear algebra is the study of *linear maps* on finite-dimensional *vector spaces*.

Within this study, it is beneficial not to study just real numbers, but [complex numbers]([[Mathematical Interlude - Complex Numbers]]) as well.
We will generalize the concepts of a plane, and ordinary space to $\R^{n} and\; \mathbb{C}^{n}$, which will then be generalized to a __vector space__.


Following this, we will consider __subspaces__, which are to vector spaces, what subsets are to sets, __sums__, which are to vector spaces what __unions__ are to subsets, and finally __direct sums of subspaces__, which are analogous to the union of disjoint sets.

Complex numbers were created so that negative numbers could be given square roots, with the chief assumption being that: $i^2 = -1$.

Complex numbers  are numbers that can be expressed in the form $a + bi$, or $x + iy,$ where $a,b,x,y$ are *real numbers* and $i$ is the imaginary unit, where $i^{2} = 1$.

* While $b$ is a real number, $bi$ constitutes an imaginary value.
Complex Addition is defined: $(a + bi) + (c + di) = (a + c) + (b + d)i$
Complex Multiplication is defined: $(a + bi) \cdot (c + di) = (ac - bd) + (ad + bc)i$
* In the event that $a \in \R$, we associate $a + 0i$, with the real number $a$, which indicates that $\R$ is a __subset__ of $\mathbb{C}$.
* We treat the number $0 + bi$ as $bi$, and also $0 + 1i$, as $i$.
  * The symbol $i$ was first used to represent $\sqrt{-1}$ by Euler in 1777.
  
## Properties of Complex Arithmetic:

Commutativity:

*Addition:* $\alpha + \beta = \beta + \alpha, \forall \alpha, \beta \in \mathbb{C}$.

*Multiplication:* $\alpha (\beta) = \beta (\alpha), \forall \alpha, \beta \in \mathbb{C}$.

Assume that we have $ \alpha = a + bi$, $\beta = c + di$, where $a, b, c, d \in \mathbb{R}.$


* $\alpha(\beta) = (a + bi)(c + di) =$
  * $(ac - bd) + (ad + bc)i.$
* $\beta(\alpha) = (c + di)(a + bi) =$
  * $(ca - db) + (cb + da)$
We know that from the commutativity of addition that operations such as $(ac - bd) + (ad + bc), (ca - db) + (cb + da)$ are equivalent .
The same follows for $ac, ca, bd, db$, from the commutativity of multiplication.

Associativity:

* $(\alpha + \beta) + \lambda = \alpha + (\beta + \lambda), \forall \alpha, \beta, \lambda \in \mathbb{C}$.
* $\alpha(\beta \lambda) = (\alpha \beta)\lambda, \forall \alpha, \beta, \lambda \in \mathbb{C}$.

Identity:

* $1\lambda = \lambda, \forall \lambda \in \mathbb{C}$

Additive Inverse:

* $\forall \alpha \in \mathbb{C}, \exists ! \beta \in \mathbb{C} : \alpha + \beta = 0$.

Multiplicative Inverse:

* $\forall \alpha \in \mathbb{C}, \exists! \beta: \alpha \beta = 1,\; \text{where}\; a \neq 0\;$

Distributive Property:

* $\lambda (\alpha + \beta) = \lambda ( \alpha) + \lambda 
(\beta), \forall \alpha, \beta, \lambda \in \mathbb{C}$.

Additive Inverse:

Let $\alpha, \beta \in \mathbb{C}$:

* Let $-\alpha$ denote the additive inverse of $\alpha$, thus $\exists! (-\alpha)$, such that $\alpha + (- \alpha) = 0$.

Subtraction of complex numbers is defined like so:

* $\beta - \alpha = \beta + (- \alpha)$.

Division is defined as: $\beta / \alpha = \beta(1 / \alpha)$.

Also, if we let $\alpha \gt 0$, then $1/\alpha$ is the multiplicative inverse of a, such that $\alpha(1 / \alpha) = 1$

Notation:
Throughout this book, we will use $\mathbb{F}$, as a stand in for $\mathbb{R}, \text{and}\; \mathbb{C}$, as both of these are examples of [fields]([[Numerical Field]]).
What this means, is that if we can prove a theorem holds for $\mathbb{F}$, then we can prove that it holds for $\mathbb{R}, \text{and}\; \mathbb{C}$.
The elements of some fields $\mathbb{F}$, are referred to as __scalars__, which is a fancy term for number.
For $\alpha \in \mathbb{F}$, we consider $\alpha^{m}$, to be the product of $\alpha$ with itself $m$ times: $a^{m} = \underbrace{\alpha \cdot \cdot \cdot \alpha}_{\text{m times}}$.
From this we can comfortably assume that: 

* $(a^{m})^{n} = a^{mn},\forall m,n \in \mathbb{N}\;\text{where}\; m,n \gt 0.$
* $(\alpha \beta)^{n} = \alpha^{n}\beta^{n}, \forall \alpha, \beta \in \mathbb{F}.$

## Lists


Before we go into the definition of $\mathbb{R}^{n}$ and $\mathbb{C}^{n}$, we should consider two important examples:
The set $\mathbb{R}^{2}$, which can be thought of as a plane, and is the set of all ordered pairs of real numbers, and $\mathbb{R}^{3}$, the set of all points in 3-space:

* $\mathbb{R}^{2} = \{(x,y): x,y \in \mathbb{R} \}$
* $\mathbb{R}^{3} = \{(x,y,z): x,y,z \in \mathbb{R} \}$
In order to generalize these concepts to higher dimensions we need to use the concept of lists:

A list of length $n$, is an ordered __collection__ of $n$ elements: $(x_1 \ldots x_n)$.
* Two lists are equal __iff__ they have the same number of elements in the same order.
Also, in order to define these higher dimensional analogues, we will use $\mathbb{F}$ which is equivalent to $\mathbb{C}\; \text{or}\; \mathbb{R}.$

$\mathbb{F}^{n}$ is the set of all lists of elements of $\mathbb{F}$, where the lists are of length $n$.

We can't visualize $\R^{n},\; \text{where}\; n \geq 4$, and the same also holds for $\mathbb{C}^{n},\; \text{where}\; n > 1$. However, while these lack physical geometric representations, we can still manipulate elements of $\mathbb{F}^n$ algebraically.

Addition in $\mathbb{F}^{n}$ is defined by adding the corresponding coordinates:
* $(x_{1} \ldots x_n) + (y_1 \ldots y_n) = (x_1 + y_1 \dots x_n + y_n)$
However, it is typically easier to replace these lists with the variable that is subscripted to represent an element __of the list__, and results in cleaner mathematics.
* If $x, y \in \mathbb{F}^n, x + y = y + x$, meaning commutativity extends to $\mathbb{F}^n$.
**Proof of Commutativity of Addition**

Let $x = (x_1 \ldots x_n)$, and let $y = (y_1 \ldots y_n)$.

* $x + y = (x_1 \ldots x_n) + (y_1 \ldots y_n) =$
* $(x_1 + y_1 \ldots x_n + y_n) =$
* $(y_1 + x_1 \ldots y_n + x_n) =$

This following line holds, due to the commutativity of addition in $\mathbb{F}$.

* $(y_1 \ldots y_n) + (x_1 \ldots x_n) =$
* $y + x\;\;\;\ $ $ \blacksquare.$

## Chapter 1.A Exercises
[Find A Four-Tuple That Satisfies The Equation](/linear-algebra-done-right/find-four-tuple-satisfying-equation/)
## Chapter 1.C Exercises


[Proof the Union of Subspaces of V is a Subspace of V](/proof-of-subspaces/)
