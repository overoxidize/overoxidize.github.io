+++
title = "Axioms Of Set Theory"
tags = ["physics", "geometry", "mathematics"]
+++

\toc

## The $\in$ relation: we do not define this symbol, or a set, but rather the associated axioms, telling how they should be used, and then definition is done in terms of these.

There are four axioms regarding existence and the empty set, four regarding constructing new sets, and the axiom of foundation.

The $\in$ relation allows us to define:

$x \notin y :\iff \neg (x \in y)$.

$x \subseteq y :\iff \forall a : ( a \in x \implies a \in y)$.

$x = y :\iff (x \subseteq y) \land (y \subseteq x)$.

$x \subset y :\iff (x \subseteq y) \land \not(x = y)$.


## Zermelo-Fraenkel Axioms

$\in$ relation axiom: $x \in y$ is a proposition *iff* $x$ and $y$ are sets.

Symbolically: $\forall x : \forall y : (x \in y) \veebar \neg(x \in y)$.

### Russel's Paradox

Suppose a set $U$, with the property $\forall x: (x \notin x \iff x \in u)$.

$U$ contains all sets which do not contain themselves, and we want to know if $U$ is a set as well. We then consider $U \in U$, which is a proposition, if $U$ is a set.

If $U \in U$ is true, then $\neg (U \in U)$ is true as well, meaning that $U$ is not an element of itself, leading us to the contradiction $u \in u \implies \neg(u \in u)$, which indiciates $U \in U$ is not a proposition.

However if $U \notin U$, then we have a contradiction in the other direction, which is $u \notin u \implies \neg(u \notin u)$.

This means $U \in U$ is not a proposition, as it is neither true, nor false, implying that in fact, $U$ is not a set.

## Empty Set Existence Axiom