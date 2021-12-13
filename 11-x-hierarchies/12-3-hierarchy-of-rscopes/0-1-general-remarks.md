
<!-- ======================================================================= -->
# general remarks on reversed scopes

<!-- ======================================================================= -->
## trees in DST

Recall that a tree `T` in descriptive set theory (DST) is a collection of
sequences over a set of elements `N` such that every prefix `p` of each
sequence in `T` is also an element in `T`.

The concept of trees in DST therefore
**corresponds with a hierarchy of rooted paths (Hrp)**.

<!-- ======================================================================= -->
## trees in AST

Recall that a tree `T(N,<)` in axiomatic set theory (AST) is a partially
ordered set of nodes such that for each `(n in N)` the set `ht(n,N)` is
well-ordered.

* `ht(n,N) := { (a in N) | (a < n) }`

Recall that **a well ordered set** is a total order such that each subset has
a least element. One also needs to keep in mind, that the focus of Mathematics
is in general on sets of numbers, with the least number being "downwards" and
the greatest number being "upwards". These sets of numbers are however such
that `ht(n,N)` is not necessarily finite - e.g. the set of (negative) integers.

Since the focus of this discussion is on finite sets of nodes, the mathematical
definitions need to be translated into the context of this discussion. That
is because each non-empty finte ordered sequence of nodes always has a least
element, its root node. Consequently, and due to the focus of this discussion
(i.e. finite node trees), `ht(n,N)` corresponds with the set of ancestors `A(n)`
of node `n`.

* `ht(n,N) <-> A(n,T)`

Recall that a tree `T(N,E)` can be understood to be equivalent to its ordered
set of nodes `N`, if the tree is understood to define a partial order `P(N,<)`.

* `(a < d), (a presequent-to d), (a ancestor-of d) := aPd` for `(a,d in N)`

The concept of trees in AST therefore
**corresponds with a hierarchy of reversed scopes (Hrs)**.

<!-- ======================================================================= -->
## applied to node trees

Recall that the (default) scope of a node `Hs[n]` is equal to the set of nodes
in the induced subtree that has the defining node as its root. That is, the
scope of a node contains the node and its descendants in the corresponding tree.

* `Hs[n] := D*(n)`

The reversed scope of a node `Hrs[n]` is dual to that since it is equal to the
set of nodes in the rooted path of its defining node. That is, the reversed
scope of a node contains the node and its ancestors in the corresponding tree.

* `Hrs[n] := A*(n)`

Note that future discussions will eventually define the **reversed scope**
of a node as the node's **context**. After all, each such scope contains all
the nodes that may be the defining nodes of one or more abstract properties
such that the defining node `n` is within the scopes of these properties.
At this point, such a definition is however not required since the current
focus is on structure, not on semantics.
