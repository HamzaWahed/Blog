---
layout: post
title: "A Simple Example of Lean Interfaces"
date: 2025-07-09 12:40:00 -0300
categories: SOLID
---

Suppose that I have an interface called $I$ that requires a single method
called $M$. Currently, there are two client using this interface, called $C_1$
and $C_2$. Now suppose we introduce a new client $C_3$ that requires the method
$M$ and a method $N$. Adding the method $N$ to $I$ would simply bloat $I$ as
the previous two clients do not need it, but have to implement it.

We could make $N$ degenerate in $I$, to ensure that we do not have to manually
update every derived class. However, that can lead to LSP violations (as for
some derived classes, the function $N$ would not behave as expected).
Therefore, the solution would be to create a new interface called $I'$ and
define $N$ there. Then, we can use multiple inheritance on $C_3$, as it
requires both $I$ and $I'$.
