
- proper subtrees - inner trees
- ancestor trees - outer trees
- disjoint trees are not outside of each other

<!-- ======================================================================= -->
## The graph of a strict setup

**CLARIFICATION**
Each strict setup `S := (P,U)` corresponds with a forest of trees `G`.

* `G := (P,E)` where `(E subset-of P×P)`
* `P` in `G` is the set of vertices and equal to `P` in `S`
* `E` in `G` the set of edges such that ...
* `e := (p1,p2) in E` such that `(p1 parent-tree-of p2)`

Note that any strict setup can therefore be understood to be accompanied
by a set of edges `E` that represents the relationships between its sets.
Because of that, a strict setup may be represented as `S := (P,U,E)` where
`E` is the set of edges in the above graph. (Note that `E` may also be
represented as `G` since it is understood as the graph of the strict setup).

* `S := (P,U,E)` or `S:= (P,U,G)` is a strict setup

Note that, in strict setup `S := (P,U,G)`, the union graph `U` is unequal
to the tree represented by `G`. That is because the set of vertices in `U`
contains vertices of anything, whereas the set of nodes in `G` is equal to
`P` and as such a set of trees. Also, and since both graphs have distinct
sets of vertices, the edges of the trees in `P` do not correspond with the
edges in `G`.

* `(U <=!=> G)`

<!-- ======================================================================= -->
## (Simple) Hierarchy/Forest of trees

**CLARIFICATION**
A setup is said to be **a (simple) hierarchy (of trees)**,
if the following requirements are met:

1. `H := (P,U)` is a strict setup
2. The setup has one and only one root tree.

A simple hierarchy has the following properties:

* A hierarchy is not empty since it must have a root.
* No tree in a hierarchy equal to the empty graph.
* A hierarchy has no loops and no cycles.
* A hierarchy has no overlapping trees (req-2).
* Two trees in a hierarchy are either disjoint ex-or related.
* Two distinct trees are either disjoint ex-or strictly related.
* Each tree either has no ex-or one parent.
* A hierarchy always has one or more leafs.
* Ancestors have more elements than their descendants.
* In a hierarchy, each tree has a unique rooted path.

Note that each hierarchy is a strict setup, but not necessarily vice versa.

* simple hierarchy -> strict setup

**CLARIFICATION**
A setup is said to be **a (simple) forest (of hierarchies)**
or "a forest of simple hierarchies", if the following requirements are met:

1. `F := (P,U)` is a strict setup.
2. The setup has zero, one or more root trees.

Note that a forest is not strictly "a set of sets of trees" (i.e. "a set of
hierarchy entities"). A forest is like a hierarchy, one "flat" set of trees.
Because of that, any operation defined on a set of trees (e.g. union, subset,
etc.) can be used in the context of forests.

Note that any two hierarchies in a forest of `N` hierarchies are disjoint. That
is because the forest would otherwise either have less than `N` hierarchies, or
it would not even be a strict setup. A forest therefore corresponds with a set
of disjoint hierarchies.

* Each forest is the union of disjoint hierarchies.

Note that, since the definition of a forest is almost identical to that of a
hierarchy, the only difference between the two is in the number of its root
sets. That is because a hierarchy has one and only one root set whereas a
forest may have any number of root sets. As such, a forest may even be empty.
Put differently, each strict setup is a forest, but not necessarily also a
hierarchy.

* strict setup <-> simple forest
* simple hierarchy -> simple forest

**CLARIFICATION**
The theoretical **set of all possible hierarchies (H)** and the theoretical
**set of all possible forests (F)** are defined as follows:

* `H := { h | "h is a hierarchy" }`
* `F := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in H)` states that `h` is expected to be
a hierarchy. Likewise, `(f in F)` states that `f` is expected to be a forest
of hierarchies.

* `(H strict-subset-of F)`

Note that an empty setup is a forest, but not a hierarchy.

<!-- ======================================================================= -->
## remarks

**CLARIFICATION**
The root `(r in P)` of a hierarchy `H := (P,U)` is equal to `U`. Because
of that, a hierarchy's root is the largest tree (i.e. in terms of number
of elements) in `P`.

That is because (1) `U` is the union of all trees in `P` (i.e. `U := E(P)`),
and (2) any other tree `(t in P)` is a proper subtree to the root (since the
setup would otherwise have more than one root).

**CLARIFICATION**
Two hierarchy instances `H1` and `H2` are disjoint, if their roots are
disjoint. (The focus here is on two entities, i.e. two separate setups).

Note that, if root `r1` of `H1` is disjoint to `r2` of `H2`,
then any subtree `t1` of `r1` is disjoint to any subtree `t2` of `r2`.

**CLARIFICATION**
Any subset of a hierarchy `H := (P,U)` (i.e. more accurately any subset
of `P`), corresponds with a forest of hierarchies.

Note that the subset of a hierarchy will itself be a hierarchy,
if the hierarchy's root is included.
