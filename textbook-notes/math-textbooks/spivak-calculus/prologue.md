+++
title = "Basic Properties of Numbers"
+++

\toc

There are twelve properties of numbers to be discussed, the first nine of which concern addition and multiplication.

Addition is the operation performed on two numbers, with the sum $a + b$ existing for any $a, b$.

It may seem straightforward to extend this operation to multiple numbers, i.e:
$a_1 + a_2 + \ldots + a_n$, but it is more expedient to restrict it to pairs of numbers, and define higher sums in terms of these.

For the sum of three numbers, as opposed to doing $a + b + c$, we can do $a + (b + c)$, with $b + c$, taking the role of the __original__ $b$. It is also possible to take $(a + b) + c$, with $a + b$ taking the role of the original __a__.

This is $P1$: $a+ (b + c) = (a + b) + c$. 

Four numbers $a + b + c + d$, can be grouped in multiple ways, all of which are equal:
- $((a + b) + c) + d$
- $(a + ( b + c)) + d$
- $a +(( b + c) + d)$
- $(a + b) + (c + d)$

This method becomes unwieldy with 5 or more numbers, and with $P1$, we can't prove the equality of all of the possible sums of a finite list of numbers $a_1\ldots a_n $.

The number $0$ has an important property, which is $P2:$

If $a$ is any number $a + 0 = 0 + a = a$.

Zero also plays an important role in $P3:$

For any $a$, there exists $-a$ such that $a + (-a) = (-a) + a = 0$.

Property two presents a notable characteristic of zero, which is if $a + x = a,$ then $x = 0$, which holds for all numbers __a__.

Proof:

If $a + x = a$

then $(-a) + a + x = a + (-a) = 0$

hence $((-a) + a) + x = 0$

hence $0 + x = 0$

hence $x = 0\;\;\; \blacksquare$.

It's hinted in the above proof that it's convenient to think about subtraction in terms of addition.

We consider $a - b$ to be equivalent to $a + (-b)$.

The remaining property of addition is related to $P1$,which is that in the case of $a + (b + c)$, the order is irrelevant:

$P4:a + b = b + a$

This is necessary because it is possible to consider that the order of the pairs of elements in addition may effect the end result, and while it doesn't, not all operations are so easily dealt with, for instance, the behavior of $P4$ does not hold for subtraction.

**Furthermore, while we might consider when** $a - b = b - a$, $P1-P4\;$ **are not sufficient to prove the case.**

The properties of multiplication are very much similar to those of addition, so much so that most of what changes is the operation mentioned in the properties.


$P5: a \cdot (b \cdot c) = (a \cdot b) \cdot c$.

$P6: a \cdot 1 = a \cdot a = a, 1 \neq 0$.

$P7: a \cdot a^{-1} = a^{-1} \cdot a = 1$.

$P8: a \cdot b = b \cdot a$.

One important detail to note is the fact that $a \neq 0\; \text{in}\; P7$, which is necessary, as $0 \cdot b = 0$, for every b, there is no number $0^{-1}$ such that $0 \cdot 0^{-1} = 1$.

Just as subtraction is predicated on addition, division is predicated on multiplication: $a  / b = a \cdot b^{-1}$, and since $0^{-1}$ is meaningless, so is $a/0$, which is why we don't divide by zero.

$P7$ has some important consequences, which are that if $a \cdot b = a \cdot c$, it may not be true that $ b = c$, as if $a = 0$, then it turns out that $a \cdot b, a \cdot c = 0$, regardless of the value of $b,c$.

However, should $a = 0$, then the fact that $b = c$, can be easily deduced:


If $a \cdot b = a \cdot c, a \neq 0$

then $a^{-1} \cdot (a \cdot b ) = a^{-1} \cdot (a \cdot c)$

hence $(a^{-1} \cdot a) \cdot b = (a^{-1} \cdot a) \cdot c$

hence $1 \cdot b = 1 \cdot c$

hence $b = c\;\;\; \blacksquare$.

Additionally, due to $P7$, it's true that if $a \cdot b = 0$, then $a = 0\; \text{or}\; b = 0$:

If $a \cdot b = 0, a \neq 0$

then $a^{-1} \cdot (a \cdot b) = 0$

hence $(a^{-1} \cdot a) \cdot b = 0$

hence $1 \cdot b = 0$

hence $b = 0\;\;\; \blacksquare$.

__It is possible that both__ $a,b = 0$, due to mathematics use of the inclusive __or__.

This latter consequence of $P7$ is often used in the solution of equations, for instance, if some number $x$ satisfies $(x - 1)(x - 2) = 0$, that $x - 1 = 0$, or $x - 2 = 0$, meaning $x = 1\; \text{or}\; x = 2$.

With the 8 properties covered so far, not much can be proved, however the this will change greatly by way of $P9$: $a \cdot ( b + c) = a \cdot b + a \cdot c$

Note that via $P8$:$(b + c) \cdot a = b \cdot a + c \cdot a$

With $P9$ we have the ability to prove when $a - b = b - a$:


If $a - b = b - a$

then $ (a - b) + b = (b - a) + b \\= b + (b - a)$

hence $a = b + b - a$

hence $a + a = (b+b-a) = b+b$

Consequently $a \cdot (1+1) = b \cdot (1 + 1)$

Therefore $ a = b\;\;\; \blacksquare$.

A second use of $P9$ is as justification of the statement $a \cdot 0 = a$, which is exampled in the proof of the consequence of $P9$, that if $a \cdot b = 0$, $a \lor b = 0$.

Additionally, $P9$, and it's consequences serve to express why the product of two negative numbers is positive, and this fact follows from the prior properties of numbers.

The remaining properties to be discussed govern inequalities.

There are two notions of inequality: $\\ a\gt b, a \lt b$, with the numbers satisfying $ a \gt 0$ being positive, and the numbers satisfying $ a \lt 0$ being negative.

$P10:$ For every number a, only one of the following holds.

$ a = 0$.

$a \in P$.

$-a \in P$.

$P11$: If $a, b \in P$, then $ a + b \in P$

$P12:$ If $a,b \in P$, then $a \cdot b \in P$.

- **These properties are complemented with the following definitions:**
  - $a\gt b $ if $ a -b \in P$
  - $a \lt b$ if $ b \gt a$
  - $a \geq b$ if $ (a \gt b) \lor (a = b)$
  - $a \leq b$ if $ (a \lt b) \lor (a = b)$
The facts of inequalities follow from properties $P10-P12$, for instance, precisely one of the following holds:
- $a-b=0$
- $a-b \in P$
- $-(a-b)=b-a \in P$
Another interesting fact shows up, which is that since $a \lt b$ requires $ b-a \in P$, then $(b+c) - (a+c) \in P$, meaning if $a \lt b$, $(a + c) \lt (b + c)$.
Also, given that $a \lt b, b \lt c$, then it follows that:

$b - a \in P$.

$c - b \in P$

$c - a = (c - b) + (b - a) \in P$.

From this we observe that $a \lt b, b \lt c$ indicates $a \lt c$.

Additionally, if $a \lt 0, b \lt 0$, that means $ab > 0$, since $a \lt 0 \iff 0 \gt a$,
which means $0 - a = -a \in P$, and since the same holds for $b$, partially as a consequence of $\mathcal{P}12$ (if $a, b \in P, ab \in P$), $(-a)(-b) = ab \in P$.

From the fact that $-a \gt 0$ if $a \lt 0$, we can define the absolute value function: 

$|a| = a,\; \text{if}\;a \geq 0, -a,\; \text{if} \;a \leq 0$.