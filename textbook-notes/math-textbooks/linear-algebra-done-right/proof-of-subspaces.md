+++
title = "Proof of Subspaces"
tags = ["mathematics", "linear algebra"]
+++

Suppose $U_1$ and $U_2$ are subspaces of $V$. Prove that $U_1 \cap U_2$ is a subspace of $V$.

By the definition of subspaces we have:
        
1. Additive Identity: $\vec{0} \in U.$
   
2. Closed Under Addition: $u,w \in U \implies u + w \in U.$

3. Closed Under Scalar Multiplication: $a \in \mathbb{F}, u \in U \implies au \in U.$

From the hypothesis we know $\vec{0}$ is an element of $U_1$ and $U_2$ via condition __1__, and that $\vec{0}$ is an element of $U_1 \cap U_2$ from the definition of intersection.


Labeling $U_1 \cap U_2$ as $U_3$, we can say $\vec{0} \in U_3$, satisfying condition 1.

In the event that $U_3 = \{\vec{0}\}$, we can consider it a subspace of $V$, since $\{\vec{0}\}$ easily satisfies conditions __1__, __2__, and __3__. If my mathematical parlance is correct, I believe this is the __trivial__ case of $U_1 \cap U_2$ being a subspace of $V$.
    
If $U_3 \neq \{\vec{0}\}$, however, then we have additional work to do, to show it satisfies conditions __1__, __2__, and __3__, with regard to the other elements it may contain. We've already demonstrated, however, that $U_3 = U_1 \cap U_2$ contains __at least__ $\vec{0}$, so we don't need to prove that it satisfies condition __1__, in the event that there are additional elements.
    
Moving forward, assume two elements $u, w$ that are common to $U_1$, and $U_2$: from the hypothesis, we know $u + w \in U_1$, and $u + w \in U_2$, via condition __2__, meaning that $u + w \in U_3 = U_1 \cap U_2$, for any $u, w$, in $U_1$, and $U_2$, so that $U_3$ satisfies condition __2__.
    
Next taking some element $u$, common to $U_1$ and $ U_2$,  we know that for some $a \in \mathbb{F}$, we have $au \in U_1$, and $au \in U_2$, via condition __3__, so that $au \in U_3$, meaning $U_3 = U_1 \cap U_2$ satisfies condition __3__. 
    
Also, since our subspaces, and their union satisfy condition __3__, if we choose our $a \in F$ to be $-1$, and select some $u$, common to $U_1$ and $U_2$, then $(-1)u = -u \in U_3$, so that $U_3$ has an additive inverse.
Since $U_3 = U_1 \cap U_2$ satisfies conditions __1__, __2__ and __3__, of being a subspace, $U_1 \cap U_2$ is a subspace of $V$.
    Additionally, I decided to investigate the case where there are both elements common to $U_1$, and $U_2$, and elements that aren't, because I wanted to convince myself whether or not the stated intersection would still be a valid subspace.
    
Assuming $u, w \in U_1$ and $u, v \in U_2$:
        The fact that $u + w, u + v \notin U_3 =U_1 \cap U_2$, doesn't violate the conditions for being a subspace, since the definition of closure under addition requires $v, w \in U_3$, which would contradict the definition of intersection, and $U_3$ is an intersection.
        The fact that $av, aw \notin U_3$, for some $a \in \mathbb{F}$ doesn't violate the conditions because the definition of closure under scalar multiplication again requires $v, w \in U_3$, which again contradicts the definition of intersection. This also means that the lack of an additive inverse for $v, w$ in $U_3$ doesn't violate the conditions for being a subspace, because the additive inverse of $v$, $-v = (-1)v$, which is just scalar multiplication, and even if we wanted to use addition, say $v + (-2v)$, we'd still need $v \in U_3$, which we already ruled out.
