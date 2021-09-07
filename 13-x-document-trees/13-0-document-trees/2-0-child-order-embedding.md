
<!-- ======================================================================= -->
# the document tree order

For as long as a doctree is considered to be associated with an external child
order (i.e. an unordered doctree), nothing needs to be done since the formal
definition remains as-is without a child order embedded into it. However, it
is needlessly difficult to derive any conclusion since one still has to deal
with two separate node orders (i.e. the tree order and its child order).
Because of that, it is essential to merge both node orders into one and by
that to determine **the true node order of an ordered doctree**.

<!-- ======================================================================= -->
## a set of complex edges

One way to embed the child order into a node tree is to redefine its set of
edges as **a set of complex edges**, each of which has a parent as its source
and an ordered sequence of siblings as its sink. That is, the sink of an edge
no longer is a single node, but an ordered sequence of nodes.

* `T(N,E)` where `E := { (p,CO(p)) | (p in PN) }`
* e.g. `E := { (1, (2,3) ) }`

Note that this definition reflects the general practice to implement trees
as lists of child nodes that are embedded into their parent nodes.

```
Example:                heterogenous graph T
================   =>   =====================
T := (N,E)                    1        parent-of
N := {1,2,3}                  |        (top-down oriented)
E := {(1,(2,3))}        -------------
                        |           |  previous-sibling-of
                        2   ---->   3  (left-to-right oriented)
```

Defined as such, each complex edge corresponds with one or more simple edges
of two distinct semantics: "parent-of" and "previous-sibling-of". Because of
that, the edges of such a tree can be understood to consist of two disjoint
sets of simple edges such that both have homogenous semantics.

* `T(N,E)` where `E := (E1 + E2)`
* `E1 := {(1,2),(1,3)}` where `sem(E1) := (a parent-of b)`
* `E2 := {(2,3)}` where `sem(E2) := (a previous-sibling-of b)`

The definition of a set of complex edges is therefore superficial, and can
thus not be used to truly embed a child order into a node tree.

<!-- ======================================================================= -->
## embedding a child order (1)

Recall that a **parent** is defined as a node which is the source of an edge,
and a **child** as a node which is the sink of an edge. Also, a **tree** is
defined as a graph such that it has one root and a unique rooted path for each
of its nodes. Defined as such, each child in a tree always has one parent only.

```
graph T1        associated expressions
========   =>   ==================================
   1
   |            (1,2) => (1 parent-of 2)
-------         (1,3) => (1 parent-of 3)
|     |         (2,3) => (2 previous-sibling-of 3)
2 --> 3
```

Note that `2`, the former presequent sibling of `3`, now acts as an additional
parent to `3`. That is, `2` is no longer a sibling to `3`. Since any non-first
child in a tree will end up having two parent nodes, the resulting graph no
longer satisfies the requirements of a node tree.

Note that `3` is now such that it has two distinct rooted paths: `(1,2,3)` and
`(1,3)`. Since any non-first child will no longer have a unique rooted path,
the resulting graph no longer satisfies the requirements of a tree.

As can be seen, adding the set of edges of a child order to the set of edges of
a node tree **will (initially) result in a non-tree graph**.

<!-- ======================================================================= -->
## transitive reduction

Recall that each tree is isomorphic to an actual partial order. That is, the
endo-relation of a tree is the cover relation of an order relation and as such
the transitive reduction of a (strict) partial order.

* transitive if `aEb` and `bEc`, then also `aEc`

This transitivity rule effectively states that, if a proper path `aPc` of two
or more edges can be formed, then an edge `aEc` must exist that connects both
of the endpoints of that path. Because of that, the transitivity rule can be
generalized as follows:

* transitive if `aPb`, then also `aEb`

With that in mind, one can also generalize the transitive reduction such that,
if a proper path `aPb` of edge-length two or more exists, then the edge `aEb`
(if it exists) can be dropped. Consequently, the order in which implicit edges
are removed during a transitive reduction is **non-relevant**.

<!-- ======================================================================= -->
## embedding a child order (2)

```
                 graph T2         graph T3
graph T1         drop (1,3)       drop (1,4)       cover graph T3
===========  =>  ===========  =>  ===========  =>  ================
     1                1                1           1 -> 2 -> 3 -> 4
     |                |                |
-----------      -----------      -<--<-
|    |    |      |         |      |
2 -> 3 -> 4      2 -> 3 -> 4      2 -> 3 -> 4
```

With that in mind, edges `(1,2)` and `(2,3)` can both be described as explicit
edges, and edge `(1,3)` as an implicit edge since it can be derived from the
previous two edges. Because of that, adding a child order to a node tree will
also result in a graph that is **no longer the cover relation** of an order
relation since it will in general contain edges that can be derived from other
existing edges. In other words, **a transitive reduction can be performed**
on T1.

Note that `3` is no longer a child of root `1`, but a child of its (former)
previous sibling `2` instead. As can be seen in the final cover graph T3,
`3` will become the single child of `2`, and so on.

<!-- ======================================================================= -->
## restricted amount of affected edges

Apart from their ancestors (e.g. `1`) any other non-ancestor node that may
exist (i.e. siblings to `1`) remain to be incomparable to the child nodes
(e.g. `2`). That is the child order of `1` will not affect any of these nodes.
Likewise, the child order of `1` will not establish a path between `1` and
any of the descendants of its child nodes.

Since the child order will only establish new paths in between `1` and its
child nodes no further reduction can apply. That is, only the edges from
`1` to its non-first child nodes will be dropped.

The addition of a child order of `N` child nodes will therefore add `(N-1)`
new edges. After that, `(N-1)` edges will be removed. Because of that,
**the overall number of edges remains the same**.

* `#E` => `+(N-1)` => `-(N-1)` => `#E`

Note that, based on that one might already suspect that the graph, that results
from the transitive reduction, is once again a node tree and as such represents
the true node order of the ordered doctree.