
<!-- ======================================================================= -->
# trees in set theory

<!-- ======================================================================= -->
## trees in DST

Recall that a tree `T` in descriptive set theory (DST) is a collection of
sequences over a set of elements `N` such that every prefix `p` of each
sequence `(s in T)` is also an element in `T`.

The concept of trees in DST therefore
**corresponds with a hierarchy of rooted paths (Hrp)**.

<!-- ======================================================================= -->
## trees in AST

Recall that a tree `T(N,<)` in axiomatic set theory (AST) is a partially
ordered set of nodes such that for each `(n in N)` the set `ht(n,N)` is
well-ordered.

* `ht(n,N) := { (a in N) | (a < n) }`

Recall that **a well ordered set** is a total order such that each subset has
a least element. One should also keep in mind that the focus of Mathematics
is in general on sets of numbers, with the least number being "downwards" and
the greatest number being "upwards". These sets of numbers are however such
that `ht(n,N)` may even be infinite - e.g. the set of (negative) integers.

Since the focus of this discussion is on finite sets of nodes, the mathematical
definitions need to be translated into the context of this discussion. That
is because each non-empty finite ordered sequence of nodes always has a least
element, its root node. Consequently, and in the context of this discussion
(i.e. finite node trees), `ht(n,N)` corresponds with the set of ancestors
`A(n)` of node `n`.

* `ht(n,N) <-> A(n,T)`

Recall that a tree `T(N,E)` can be understood to be equivalent to its ordered
set of nodes `N`, if the tree is understood to define a partial order `P(N,<)`.

* `(a < d), (a presequent-to d), (a ancestor-of d) := aPd` for `(a,d in N)`

The concept of trees in AST therefore
**corresponds with a hierarchy of reversed scopes (Hrs)**.
