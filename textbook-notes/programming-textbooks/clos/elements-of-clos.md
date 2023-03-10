+++
title = "Elements of CLOS"
tags = ["lisp", "programming"]
+++

As expected of OOP, CLOS contains classes, instances, generic functions and methods, and allows for the interweaving of these concepts.

2.1 Classes and Instances.

- The fundamental unit in writing CLOS programs is the *class*, a type in Common Lisp, from which instances are derived, or instantiated, and the type of an instance can be extracted via the [`type-of object`](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/node53.html) function.

2.2 Slots

All instances