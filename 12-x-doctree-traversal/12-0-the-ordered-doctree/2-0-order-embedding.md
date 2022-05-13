
<!-- ======================================================================= -->
# the ordered document tree

For as long as a doctree is considered to be associated with an external child
order (i.e. an unordered doctree), nothing needs to be done since the formal
definition remains as-is without a child order embedded into it.

However, it is needlessly difficult to derive any conclusion since one then
has to deal with two separate node orders (i.e. the tree order and its child
order). Because of that, it is essential to embed the child order of a doctree
into its node order in order to determine **the doctree's overall node order**.

<!-- ======================================================================= -->
## a set of complex edges

One way to embed the child order into a node tree is to redefine its set of
edges as **a set of complex edges**, each of which has a parent as its source
and an ordered sequence of siblings as its sink. That is, the sink of an edge
no longer is a single node, but an ordered sequence of child nodes.

* `T(N,E)` where `E := { (p,co(p)) | (p in PN) }`
* e.g. `E := { (1, (2,3) ) }`

Note that this definition reflects the general practice to implement trees
as lists of child nodes that are embedded into the corresponding parent nodes.

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
that, the set of simple edges of such a tree can be understood to consist of
two disjoint sets of edges such that both sets have homogenous semantics.

* `T(N,E)` where `E := (E1 + E2)`
* `E1 := {(1,2),(1,3)}` where `sem(E1) := (a parent-of b)`
* `E2 := {(2,3)}` where `sem(E2) := (a previous-sibling-of b)`

The definition of a set of complex edges is therefore only superficial since
it does not truly embed the child order into the document tree.

<!-- ======================================================================= -->
## embedding a child order (1)

Recall that a **parent** is defined as a node that is the source of an edge,
and that a **child** is defined as a node that is the sink of an edge. Also,
a **tree** is defined as a graph that is required to have one root and a unique
rooted path for each node in it. Defined as such, each child in a tree always
has one parent only since otherwise not all nodes would have a unique rooted
path.

```
graph T1        associated expressions
========   =>   ==================================
   1
   |            (1,2) => (1 parent-of 2)
-------         (1,3) => (1 parent-of 3)
|     |         (2,3) => (2 previous-sibling-of 3)
2 --> 3
```

As can be seen, adding the set of edges of a child order to the set of edges
of an undordered document tree will (initially) result in **a non-tree graph**.

Note that `2`, the former presequent sibling of `3`, now acts as an additional
parent to `3`. Because of that, `3` is now such that it has two distinct rooted
paths: `(1,2,3)` and `(1,3)`. Consequently, and since any non-first child will
no longer have a unique rooted path, the resulting graph can no longer satisfy
the requirements of a node tree.

<!-- ======================================================================= -->
## transitive reduction

Recall that each tree is isomorphic to an actual partial order. That is, the
endo-relation of a tree is the cover relation of an order relation and as such
the transitive reduction of a (strict) partial order.

* transitive if `aEb` and `bEc`, then also `aEc`

This effectively states that, if a path `aPc` of two or more edges can be
formed, then an edge `aEc` must exist that connects both of the endpoints
of that path. Because of that, the rule can be generalized as follows:

* transitive if `aPb`, then also `aEb`

Note that a "transitive closure" will add an edge `aEb` for each path `aPb`
that can be formed. Hence, the transitive closure iteratively connects the
endpoints of each path that can be formed over the existing edges. Because of
that, each edge in the transitive closure of a relation can be understood to
state that a path of one or more edges can be formed in the source relation.

* `aEb` in the transitive closure of `R` => a path can be formed over `R`

With the above in mind, one can generalize the transitive reduction such that,
if a path `aPb` of two or more edges exists, then an edge `aEb` (if it exists)
will be dropped. Because of that, the order in which **implicit edges** such
as `aEb` are removed during a transitive reduction is non-relevant.

* reduction := drop `aEb`, if a path `p(a,b)` exists such that `(p != (a,b))`

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

With the above in mind, edges `(1,2)` and `(2,3)` can both be described as
**explicit edges**, and edge `(1,3)` as an implicit edge since it can be
derived from the previous two. That is because the former two edges allow
to form path `(1,2,3)`.

Because of that, adding a child order to a tree will result in a graph that
is **no longer the cover relation** of an order relation since it will in
general contain edges that can be derived from other existing edges. The
modified graph can therefore not be described as being "tranistively reduced",
which is why edge `(1,3)` must be dropped (T1 -> T2).

Note that `3` in T2 is no longer a child to root `1`, but a child to its former
previous sibling `2` instead. As can be seen in the final cover graph T3, `3`
will be the single child of `2`, and `4` the single child of `3`.

Note that the transitive order relation of T3 will still contain the edge
`(1,3)`. That is, `aEb` over the transitive closure of T3 is true for both
nodes, which is why the order between both nodes is maintained.

<!-- ======================================================================= -->
## restricted amount of affected edges

Apart from their ancestors (e.g. `1`) any other non-ancestor that may exist
(e.g. siblings to `1`) remain to be incomparable to the child nodes (e.g.
`2`). That is, the child order of `1` will not affect any of these nodes.
Likewise, the child order of `1` will not establish a path between `1` and
the descendants of its child nodes.

Since a child order will only establish new edges in between the child nodes
of a parent, no further reduction can apply. That is, only the edges from a
parent to its non-first child nodes will be dropped.

The embedding of the child order of a parent of `N` child nodes will add
`(N-1)` edges. After that, `(N-1)` edges will be dropped. Consequently,
**the overall number of edges remains unchanged**.

* `#E` => `+(N-1)` => `-(N-1)` => `#E`

Based on that, one might already suspect that the graph, that results from
the transitive reduction, will once again satisy the requirements of a node
tree, and will represent the true node order of the ordered doctree.
