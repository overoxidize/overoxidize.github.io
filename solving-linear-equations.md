+++
title = "Systems of Linear Equations"
tags =["linear-algebra"]
+++

# Systems of Linear Equations and Matrices.
   
**Introduction to Systems of Linear Equations.**


Information can be presented and constructed with rows and and columns, to form a group of arrays, or a matrix and these matrices contain all of the information necessary to solve a system of equations.

For example, the system $\begin{array}{lcl} 5x + y = 3\\ 2x - y = 4 \end{array}$ is encoded within the matrix $\begin{bmatrix} 5 & 1 & 3 \\ 2 & -1 & 4 \end{bmatrix}$, and by applying the proper transformations to the matrix, we can extract the solution to the system.

Matrices are more than just tools for finding solutions to these systems of equations: they are rich mathematical objects in their own right, and it is the study of them that __defines linear algebra__.

**1.1 Systems of Linear Equations**

In two dimensions, a line given in a rectilinear coordinate system can be defined as $ax +by = c, \text{where}\; a \lor b > 0 $, and a line can also be defined in three dimensions $ax + by + cz = d: (a \lor b \lor c)\; \neq \; 0 $.

- ### Thoughts: One of the great things about Mathematics is how things get built upon each other, into wildly new fields, yet retaining fundamental concepts, and being relatable to other field: $c$ and $d$ are functions of $ax + by$ and $ax + by + cz$ respectively, and this also relates to the function focused aspect of the fundamentals of calculus, in that we can say $ y = f(x) = ax+by+cz$. Also, we know that we are dealing with real numbers, due to the nature of the coordinate system not being complex, so we can assume that $a,b,c,x,y,z \in \mathcal{R}$, which is the set of real numbers for which they have membership, so there are even reminisces of set theory hidden within this. This makes sense though, because the foundations of mathematics have been set theoretic since the early 1900's.

More generally, a linear equation of $n$ variables can be written as: 

$a_1x_1 + a_2x+2+ \ldots a_nx_n = b$.
- ### A homogeneous linear equation is one where $b = 0$.
- 
Within this class of equation, there are no products or roots of variables, and said variables only appear in the first power.
Within a system of linear equations, the variables are the unknowns of the system, with the values being coefficients.

A general linear system of $m$ equations and $n$ unknowns is of the form:
$\begin{array}{lcl} a_{11}x_1 + a_{12}x_2 + \ldots + a_{1n}x_n = b_1 \\ a_{21}x_1 + a_{22}x_2 + \ldots + a_{2n}x_{n} = b_2 \\ \vdots \\ a_{m1}x_1 + a_{m2}x_2 + \ldots + a_{mn}x_n = b_m  \end{array}$

The double subscript on coefficients $a_{ij}$ gives their location in the system, with the $_{i}$ indication the equation in which the coefficient appears, and the $_{j}$ indicating the unknown it multiplies.

A solution for a system is the the sequence of numbers that, when substituted for the unknowns ($x_i$), makes each equation a true statement.
Alternatively, they can be seen as matrix coordinates, with the first subscript indicating the row the coefficient is located in, and the second indicating the column the coefficient is located in.

**Linear Systems in Two and Three Unknowns**

These kinds of linear systems coincide with the intersections of lines:

For instance the equations of the system $\begin{array}{lcl} a_1x +b_1y = c_1 \\ a_2x + b_2y = c_2 \end{array},$ when graphed, are lines, and so each solution ($x,y$) corresponds to a point of intersection, so there are three possibilities: If a system has at least one solution it is called __consistent__, otherwise, __inconsistent__, thus a consistent linear system has either __one__ solution __or__ **__infinitely many__** solutions, and this extends to systems of equations in three unknowns, for example, the following system, the graphs of which are planes:
$\begin{array}{lcl} a_1x +b_1y + c_1z = d_1 \\ a_2x + b_2y + c_2z = d_2 \\ a_3x + b_3y + c_3z = d_3  \end{array}$.

While these planes can relate to each other (geometrically) in __six__ different ways now, the solution(s) of the system are still restricted to the three types of possibilities:
    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FPhysics-Lournal%2Fa-3L7SDWrE.png?alt=media&token=2a95d91d-5991-45e4-a749-cc700a7a6d21)

**Augmented Matrices & Elementary Row Operations**

The higher the number of equations in a system, the higher the complexity of the algebra required to find a solution: this can be made more simple by removing the $+$'s, the variables, and the $=$'s.

This allows us to write the system $\begin{array}{lcl} a_{11}x_1 + a_{12}x_2 + \ldots + a_{1n}x_n = b_1 \\ a_{21}x_1 + a_{22}x_2 + \ldots + a_{2n}x_{n} = b_2 \\ \vdots \\ a_{m1}x_1 + a_{m2}x_2 + \ldots + a_{mn}x_n = b_m  \end{array}$, as so:
$\begin{bmatrix} a_{11}\; a_{12}  \ldots  a_{1n}\; b_1 \\ a_{21} \; a_{22} \; \ldots  a_{2n} \; b_2 \\ \vdots \\ a_{m1}\; a_{m2} \ldots  a_{mn}\;b_m  \end{bmatrix}$

This is the **__augmented matrix__** for the system.

The basic method for solving a system is to apply algebraic operations to the system that preserve the solution set, to produce increasingly simple systems, until it can be determined if the system is consistent.
The algebraic operations are:

- Multiplying each term of an equation by a constant.
- Interchanging two equations.
- Multiplying each term of an equation by a constant and adding it to another equation.
  
Due to the relationship between rows of a matrix and equations in a system, these operations are easily applied to matrices, where equations become the rows.

**Exercise Set 1.1**

### For each equation, determine whether the equation is linear in $x_1, x_2$ and $x_3.$

a.) $x_1 +5x_2 − \sqrt{2}x_3 =1$.
    
    Linear in all three. The third term, $\sqrt{2}x_3$ was tricky, as linear equations do not involve roots of __variables__, so seeing a radical confused me, but it turns out, in this case, $\sqrt{2}$ is a constant by which $x_3$ is multiplied, and thus is valid.

b.) $x_1 + 3x_1 + x_1x_3 = 2$
    
    Not linear in all three. The terms $x_1$ and $3x_2$ are linear, but $x_1x_3$ is a product of variables, which is a violation of the definition of a linear equation.

c.) $x_1 = -7x_2 + 3x_3$
    
    Linear in all three, no products, roots of variables, or powers beyond the first.

d.) $x^{\scriptsize{-2}}_1 +x_2 +8x_3 = 5$
    
    Not linear in all three, as the term $x^{-2}_1$ is raised to the second power, and violates the definition of a linear equation.

e.) $x^{3/5}_1 - 2x_2 + x_3 = 4$
    
    Not linear in all three.

f.) $\pi x_1 - \sqrt{2} x_2 = 7^{1/3}$
    
    Not linear in all three.

### For each equation, determine whether the equation is linear in $x_1$ and $x_2$:

a.) $2^{1/3}x + \sqrt{3}y = 1$
    
  Linear in both. 

b.) $2x^{1/3} + 3 \sqrt{y} = 1$
 
    Not linear in both, due to exponentiation of the first variable in the first term and the square root of the second variable in the second term.
c.) $cos(\frac{\pi}{7})x - 4y = log3$
    
    Linear in both. The first term is a bit dense but $cos(\frac{\pi}{7})$ is a constant by which the variable is multiplied- the variable itself is consistent with definitions of linear equations.

d.) $\frac{\pi}{7}cos x - 4y = 0$
  
  Not linear in both as the cos(x) is a trigonometric function applied to the first variable which is a violation of the definition of linear equations.

e.) $xy = 1$

    Not linear in both, products of variables aren't valid.

f.) $y + 7 = x$.

- Linear in both, also can be rewritten as $y + 7 - x = 0$.

### Using the specified notation,write down a general linear system of:

a.) Two equations in two unknowns:

$\begin{array}{lcl} a_{11}x_1 + a_{12}x_2 = b_1 \\ a_{21}x_1 + a_{22}x_2 = b_2 \end{array}$

b.) Three equations in three unknowns:

$\begin{array}{lcl} a_{11}x_1 + a_{12}x_2 + a_{13}x_3 = b_1 \\ a_{21}x_1 +a_{22}x_2 + a_{23}x_3 = b_2 \\ a_{31}x_1 + a_{32}x_2 + a_{33}x_3 = b_3 \end{array}$

c.) Two equations in four unknowns:

$\begin{array}{lcl} a_{11}x_1 + a_{12}x_2 + a_{13}x_3 + a_{14}x_4 = b_1 \\ a_{21}x_1 + a_{22}x_2 + a_{23}x_3 + a_{24}x_4 = b_2 \end{array}$


### Find the augmented matrix for the linear system.

a1.)
    $\\-2x_1 = 6 \\$ 
    $3x_1  = 8$ $\\9x_1 = -3\\$
        $\\ \begin{bmatrix} -2 & 6 \\ 3 & 8 \\ 9 & -3 \end{bmatrix}$

b1.)
    $ \\ 6x_1 - x_2 + 3x_3 = 4 \\ \hspace{2.9em} 5x_2 - x_3 = 1$
        $\\ \begin{bmatrix} 6 & -1 & 3 & 4 \\ 0 & 5 & -1 & 1 \end{bmatrix}$

- c1.) 
    $\\ \begin{array}{c} 0x_1 + 2x_2 + 0x_3 -3x_4 + x_5 = 0 \\ -3x_1 - x_2 + x_3 + 0x_4 + 0x_5 = -1 \\ 6x_1 + 2x_2 - x_3 + 2x_4 - 3x_5 = 6\end{array}$
        $\begin{bmatrix} 0 & 2 & 0 & -3 & 1 & 0 \\ -3 & -1 & 1 & 0 & 0 & -1 \\ 6 & 2 & -1 & 2 & -3 & 6 \end{bmatrix}$

a2.) $3x_1 - 2x_2 = -1 \\ \hspace{2em} 4x_1 + 5x_2 \hspace{0.3em}= 3 \\ \hspace{2em} 7x_1 + 3x_2 \hspace{0.3em}= 2\\$

$\\\begin{bmatrix} 3 & -2 & -1 \\ 4 & 5 & 3 \\ 7 & 3 & 2 \end{bmatrix}$
    
b2.)$\; 2x_1 \hspace{2em} +2x_3 = 1 \\ \hspace{2.2em} 3x_1 - x_2 + 4x_3 = 7 \\ \hspace{2.2em} 6x_1 + x_2 - x_3 \hspace{0.5em}= 0$
    
$\begin{bmatrix} 2 & 0 & 2 & 1 \\ 3 & -1 & 4 & 7 \\ 6 & 1 & -1 & 0 \end{bmatrix}$

c2.) $x_1 = 1 \\ \hspace{2.4em} x_2 = 1 \\ \hspace{2.4em} x_3 = 1$

$\begin{bmatrix} 1 & 0 & 0  & 1 \\ 0 & 1 & 0 & 1 \\ 0 & 0 & 1 & 1 \end{bmatrix}$
