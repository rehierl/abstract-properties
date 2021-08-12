
<!-- ======================================================================= -->
## a generic method to form a subtree

There are obviously several ways to form a subtree `S := (T,U)` based on a
super-tree `G := (N,E)`. However, and independently of how exactly a subtree
is formed, a subtree must be a tree and must therefore always have a single
root `r`. All the nodes in `S` must consequently be descendants of `r` in `G`.

Note that the root of `S` is not required to be identical to the root of `G`
(i.e. `(RN(S) == RN(G)` is not necessarily true).

However, a subtree is in general not required to include all the descendants
of `r` in `G`. Consequently, `S` may have leaf nodes that are no leaf nodes
in `G`. Because of that, the subtree of a tree can in general be defined by
its root `r` and by its set of leaf nodes `LS` since every node in a tree
always has a unique rooted path.

A **generic subtree** may be formed as `S := subtreeOf(G,r,LN)`, where ...

* `subtreeOf(G,r,LN)` := the union of all top-down paths in `P`
* `P(G,r,LN) := { (p in G) | p := (r,...,l) for a leaf (l in LN) }`
* i.e. `(#P == #LN)` is true

That is, the paths in `P`, begin in `r` and end in a leaf `l` of `S`. Hence,
each top-down path in `P` is a root-to-leaf path in `S` and as such understood
to define a path graph. Because of that, the resulting subtree can be formed
as the union of path graphs.

Note that any tree, which can be formed based on this generic method, may be
referred to as a "generic subtree". Hence, the set of all generic subtrees
that can be formed based on a given tree may be referred to as the tree's
"class of generic subtrees".

<!-- ======================================================================= -->
## induced by its root

A disadvantage of the above generic method is that one first has to determine
for each node in `G`, whether or not that node is a node in `S`. Based on these
nodes, one then has to determine the root `r` of `S` and its leaf nodes `LS`.
However, the second aspect (i.e. determining the leaf nodes) can be greatly
simplified, if none of the descendants of `r` in `G` are excluded. That is,
if all the descendants of `r` in `G` are included.

An **induced subtree** may be formed as `S := subtreeOf(G,r)`, where ...

* `subtreeOf(G,r) := G[r] := G[X]` where `X := {r} + D(r)`

That is, such a subtree is defined as an induced subtree, induced by a subset
of nodes. Simply put, this class of subtrees contains those subtrees that are
**induced by the subtree's root** (i.e. `G[r]`).

Note that any subtree of a tree, that can be formed based on this (simplified)
method, will be referred to as an "induced subtree". Hence, the set of induced
subtrees that can be formed based on a given tree will be referred to as
**the tree's family of induced subtrees**.

<!-- ======================================================================= -->
## example

```
tree S            tree T           tree U
=============     ===========      ========
1 -|-> 2 -> 4     1 -> 2 -> 4      1 -|-> 2
   |-> 3                              |-> 3
```

S compared to T:

* `T` is a (generic) subtree of `S`
* `T` and `S` do not overlap each other
* `T` is no induced subtree of `S` - i.e. `(T != S[1])`
* note - `3` is no node and therefore no leaf in `T`

T compared to U:

* `T` and `U` overlap each other
* note - `4` is no node and therefore no leaf in `U`
* note - `3` is no node and therefore no leaf in `T`
* `T` and `U` are unrelated with each other

S compared to U:

* `U` is a (generic) subtree of `S`
* `U` and `S` do not overlap each other
* `U` is no induced subtree of `S` - i.e. `(U != S[1])`
* note - `2` is a leaf in `U`, but no leaf in `S`
* note - `4` is no node and therefore no leaf in `U`

Note that not every generic subtree is an induced subtree of the form `G[r]`.
Because of that, the family of induced subtrees of a tree has in general
fewer elements than its family of generic subtrees.
