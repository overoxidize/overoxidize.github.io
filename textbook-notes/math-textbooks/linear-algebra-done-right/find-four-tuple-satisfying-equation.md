+++
title = "Find Four Tuple Satisfying The Equation"
tags = ["mathematics", "linear algebra"]
+++

Find $x \in R^4$ such that $(4, -3, 1, 7) + 2x = (5, 9, -6, 8)$

Since arithmetic operations on 4-tuples is done by applying the operation to the
corresponding components of the tuple, we can do so, after we subtract the 4-tuple on the LHS, from the L/RHS:

$2x = (5, 9, -6, 8) - (4, -3, 1, 7)$.

Re-arranging the terms to show the component-wise operations:

$2x = ((5 - 4), (9 + 3)), ((6 + 1), (8 - 7))$.

Computing the arithmetic leaves $2x = (1, 12, 7, 1)$.

From here, in order to find $x$, we simply divide the LHS by $2$:

$x = ((\frac{1}{2}),(\frac{12}{2}),(\frac{7}{2}),(\frac{1}{2}))$.

From this we see $x = (0.5, 6, \frac{7}{2}, 0.5)$, a vector that exists in $R^4$.

Checking our work we see:

$2x = 2(0.5, 6, \frac{7}{2}, 0.5) = (1, 12, 7, 1)$.

And from this we can check:

$(4, -3, 1, 7) + (1, 12, 7, 1) = (5, 9, -6, 8)$.

Which gives us $((4 + 1),(12 - 3),(1 - 7),(9 - 1)) = (5, 9, -6, 8)$.
