+++
title = "Numbers Of Various Sorts"
tags = ["calculus", "mathematics"]
+++


The previous chapter makes frequent use of the word number, of which there are various kinds.

The counting numbers are symbolized by $$\N$$, a group of numbers for which not all of the aforementioned properties of numbers hold, such as $$P2, P3$$.
- ### $$P2$$ contains zero, which isn't a counting number, and $$P3$$ contains a negative number, and negatives also aren't counting numbers.

The most basic property of this group of numbers is the induction principle, which says that if $$P(x)$$ is true for some $$x$$, the property should hold for all numbers $$x$$, and whenever $$P(k)$$ is true $$P(k+1)$$ should be as well.

The second condition, is asserted to be true under the assumption that the first is, and in the event that $$P(1)$$ is true, we can show the property for the case $$P(2)$$, using the second condition with the case $$k=1$$, and so on.

An example of induction is a formula that provides the sum of the first $$n$$ numbers:

$$1 + \ldots + 1 = \frac{n(n+1)}{2}$$.

In order to prove this is true, we first show that it holds for $$n=1$$.
    - ### $$\frac{1(1+1)}{2} = 1$$.

Now, we assume for some $$k, k \in N$$, we have: $$1 + \ldots + k = \frac{k(k+1)}{2}$$.

Then $$\\1 + \ldots + k + (k+1) =\\[3pt] \frac{k(k+1)}{2} + (k+1) =\\[5pt] \frac{k(k+1) + 2k + 2}{2} =\\[5pt]  \frac{k^2 + 3k+2}{2} =\\[5pt] \frac{(k+1)(k+2)}{2}$$

The inductive principle can be shown without reference to numerical properties, more precisely, if $$A$$ is a set and $$1 \in A$$, as well as $$k+1 \in A$$, if $$k \in A$$,  $$A = \N$$.
