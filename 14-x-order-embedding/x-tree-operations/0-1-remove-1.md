
<!-- ======================================================================= -->
# The removal of a node (1)

The following exemplifies the element-based and the suffix-based removal
from and ordered sequence and an un-ordered tree.

<!-- ======================================================================= -->
## (Ex-1) an element-based removal from an ordered sequence

```
s* := remove(s,2)
==============================================
s := (1,2,3)   =>   s \ (2)   =>   s* := (1,3)
```

Given an ordered sequence `s` and an element (i.e. `2`) we want to remove, we
implicitly restrict the operation to the input element. Because of that, the
result can in general be described as appending a suffix to a prefix (i.e.
`s* := (t × v)`, where `t := (1)` and `v := (3)`). As such, the operation can
be described as **an element-based removal** (i.e. `s := (t × (u) × v)` where
`u := 2`).

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 3 ) \ ( 2 ) = ( 1 -> 3 )
     |----->|
```

Since the focus of this discussion is on ordered sequences, and since such
sequences correspond with ordered sets of elements, one can look at this type
of removal from an order-based perspective. That is, this operation can be
said to form a suborder `S*` (i.e. a "sub-sequence" rather than a "sub-string")
by removing a suborder `R` from an input order `S`.

* `S* := S \ R` where `R := ({2},<)`

Recall that the set of edges in an order relation is not defined as an explicit
set of edges, but as "contains all the edges for which the order operator (e.g.
`<`) returns true". Because of that, removing one element from an ordered set
does not affect the relationships between the remaining elements. That is, an
element in prefix `t` remains to be related to all the elements in suffix `v`.
Since the edges are a matter of consequence, the removal operation can be said
to focus on the elements, not on the edges.

`S := (V,G)` where `V := E(s)` and ...

* `G := { (a,b) | (a < b) for (a,b in V) }`
* i.e. `G := { (1,2), (1,3), (2,3) }`

`S* := (V*,G*)` where `V* := V\{2} := {1,3}` and ...

* `G* := { (a,b) | ((a,b) in G) and (a,b in V*) }`
* i.e. `G* := { (1,3) }`

Note that, in regards to graph `G*`, graph `G` in order relation `S` can be
understood to define the order operator in `S*`. That is, `G` can be said to
define whether two elements in `S*` are related or not.

The to-be-removed element can therefore be understood to first be removed from
the set of elements. After that, the edges to which the element is a source or
a sink need to be removed. That is because the remaining elements can not be
related to an element which no longer exists (see border edges).

<!-- ======================================================================= -->
## (Ex-2) a suffix-based removal from an un-ordered tree

```
S                 \ R            = S*
========================================
( 1 -> 2 -|-> 3 ) \ ( 2 -|-> 3 ) = ( 1 )
          |-> 4          |-> 4
```

Recall that the nodes in a tree need to be understood as node identifiers
rather than as number values. That is, even though number 3 is comparable
to 4, the corresponding nodes are not since both are siblings to each other.

In general, given a tree `t` and a to-be-removed node (e.g. `2`),
we implicitly treat the node and its descendants as a composite unit.

Such a unit is in general referred to as an induced subtree (i.e. `t[2]`)
which has the given node as its root, and which contains all the nodes that
can be reached from that root. That is, the input node is understood to
define a subtree which contains these nodes and all the edges in between
them. Because of that, this type of removal can be described as the removal
of an induced subtree.

Since a tree can be understood as the cover graph of a partial order, this
type of removal can also be understood from an order-based perspective.
That is, the resulting suborder `S*` can be said to be formed by removing
a suborder `R` from an input order `S`.

* `S* := S \ R` where `R := t[2] := (N,E)` and ...
* `N := {2,3,4}` and `E := { (2,3), (3,4) }`

`S := (N,E)` where `N := {1,2,3,4}` and ...

* `E := { (a,b) | (a < b) for (a,b in N) }`
* i.e. `E := { (1,2), (1,3), (1,4), (2,3), (2,4) }`

`S* := (N*,E*)` where `N* := N\{2,3,4} := {1}` and ...

* `E* := { (a,b) | ((a,b) in E) and (a,b in N*) }`
* i.e. `E* := { }`

Note that only the given node, its descendants and the edges between them are
removed explicitly. That is because these elements are elements in the induced
subtree. In contrary to that, all the edges in super-tree `S` which connect a
node in the resulting tree `S*` with a node in the induced sub-tree `R` (i.e.
`(1,2)`, `(1,3)` and `(1,4)`) must be removed implicitly. As before, a node
can not be related to a node which no longer exists (see border edges).

Note that an induced subtree can be understood as a **suffix** to a super-tree.
That is because it contains the given node as its root and all the nodes which
are subsequent to it in the super-tree. This type of removal will therefore be
referred to as **a suffix-based removal**.

Note that the element-based and the suffix-based operations are both independent
of a particular context since one does not have to distinguish between the nodes
that can be reached - they all are either included or not. Because of that, both
types of operations represent strict binary all-or-nothing decisions.

Note that the resulting tree contains nodes which are presequent to the root
of the induced subtree (i.e. the nodes in the rooted path of the root's parent)
and nodes which are neither presequent nor subsequent to that root (e.g. nodes
that are siblings to that root). Based on that, and from a strict perspective,
an induced (total) subtree which begins at the root of its super-tree (e.g. a
rooted path) could be referred to as a **prefix** of the super-tree. Likewise,
and from a less strict perspective, `S*` could be seen as a prefix to `S`.

<!-- ======================================================================= -->
## (Ex-3) a suffix-based removal from an ordered sequence

```
S               \ R          = S*
====================================
( 1 -> 2 -> 3 ) \ ( 2 -> 3 ) = ( 1 )
```

Recall that an ordered sequence of elements can be understood to define a path
graph. As such, an ordered sequence satisfies the requirements of a node tree,
which is why the above suffix-based removal is applicable in the context of an
ordered sequence.

Given a sequence `s` and a to-be-removed element (e.g. `2`), we can again treat
the element as the root of an induced subtree (e.g. `t[2]`). That is, the input
node is in this case understood to define a suffix to `s`.

Note that, since each node in an ordered sequence of nodes has one child only,
there is no difference between a type-1 and a type-2 removal in regards to an
ordered sequence of nodes. After all, no child has a subsequent sibling, which
is why a path graph can be seen as an unordered, or as an ordered tree (note -
each child-order is a 1-element ordered sequence).

<!-- ======================================================================= -->
## (Ex-4) an element-based removal from an unordered tree

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 4 ) \ ( 2 ) = ( 1 -|-> 4 )
     |-> 3  |-> 5                  |-> 5
                                   |-> 3
```

Since each tree `t` corresponds with a partial order, the removal of a node
can also be restricted to the input node. That is, the to-be-removed node
`2` and its descendants are not understood to form an induced subtree (i.e.
`t[2]`, i.e. not seen as a composite unit).

* `S* := S \ R` where `R := ({2},<)`

`S := (N,E)` where `N := {1,2,3,4,5}` and ...

* `E := { (a,b) | (a < b) for (a,b in N) }`
* i.e. `E := { (1,2), (1,3), (1,4), (1,5), (2,4), (2,5) }`

`S* := (N*,E*)` where `N* := N\{2} := {1,3,4,5}` and ...

* `E* := { (a,b) | ((a,b) in E) and (a,b in N*) }`
* i.e. `E* := { (1,3), (1,4), (1,5) }`

As can be seen, if the to-be-removed node is treated as an isolated node,
its child nodes become child nodes of the node's parent. However, all the
child nodes of the node's parent are equally relevant to it (i.e. there
is no child order).

Note that this corresponds with the element-based removal in regards to an
ordered sequence, if such a sequence is seen as a path graph (i.e. as a tree).
That is, the removal of node `2` from sequence `(1,2,3)` can be said to turn
node `3` into a child of node `1`.
