
<!-- ======================================================================= -->
# (finite directed) node trees

A node tree is a digraph `T := (N,E)` such that ..

* `N` is the non-empty set of nodes
* `E` is the possibly empty set of edges
* `(E(e) subset-of N)` for each `(e in E)`
* `(E subsetof N×N)`

As with any vertex in a graph, each node `(n in N)`
is understood to represent a unique object.

* `o(n)` returns the object that node `n` represents
* `n(o) := v(o)` returns the id/reference/node of object `o`

The following can be said about the nodes of an edge `(e in E)`:

* `e := (x -> y) := (x,y)`
* `y` is a root, if there is no `x` such that `xEy` is true
* `x` is a parent of `y`, and `y` is a child of `x`
* `(x parent-of y)` is true, iff `x` is the parent of `y`
* `(y child-of x)` is true, iff `y` is a child of `x`
* `x` is super-ordinate to `y`, and `y` is sub-ordinate to `x`
* `x` is more significant than `y`, and `y` is less significant than `x`
* all graph-based definitions still apply - endpoints, source, sink, ..

The following can be said about any edge `(e in E)`
and the relationship it has with both of its vertices:

* `e` is downward-directed/oriented
* from a super-ordinate towards a sub-ordinate node

Like any (directed) graph, each tree can be understood to be associated
with an indicator function `E()` (i.e. its characterisitc funciton):

* `(E: N×N -> Bool)` or `E(x,y) := ((x,y) in E)`
* notational simplification - `xEy := E(x,y)`

<!-- ======================================================================= -->
## restrictions, requirements

Further requirements on node trees are:

* a node that is no source to any edge is a root
* each tree has a root, and one root node only
* any edge connects a parent (source) with a child (sink)
* each child has one and only one incoming edge

Since no node is considered to be super- or sub-ordinate to itself,
no edge begins and ends in the same node.

* `xEx` is not allowed for any `(x in N)`
* a tree has no loops (and no cycles)
* each edge is an ordered pair of distinct nodes
* `xEy` may be true iff `(x != y)`

Note that such a node tree can be described as an **arborescence**. That is,
any tree in the context of this dicsussion is considered to be defined as
an arborescence - a directed acyclic graph (dag) that has a unique rooted
path for each node in it.

<!-- ======================================================================= -->
## (sub)sets of nodes

As a matter of simplification, the following sets of nodes can be defined:

* `RN := { (r in N) | (r !in VI) }`
* `RN` is the set of nodes that have no incoming edge
* note - `RN` is similar, but not equal to `SRC`
* note - `(n in SRC) -> (n in RN)`
* `PN := { (p in N) | (p in VO) } := VO`
* `PN` is the set of nodes that are parent to some child node
* `CN := { (c in N) | (c in VI) } := VI`
* `CN` is the set of child nodes that have a parent node
* `IN := INT := { (n in N) | (n in VO) and (n in VI) }`
* `IN` is the set of inner nodes that are a parent and a child
* note - each inner node is an internal vertex
* `LN := { (l in N) | (l !in VO) }`
* `LN` is the set of leaf nodes that have no child

<!-- ======================================================================= -->
## (helper) functions

A function `(p: N -> P(N))` can be defined that returns the set of parent nodes
of the input node `n`. Put differently, `p(n)` returns all the nodes to which
`n` is a child.

* `p(n) := { (p in N) | pEn } := src(n)`
* `p(n)` is the set of parent nodes of `n`

A function `(c: N -> P(n))` can be defined that returns the set of child nodes
of the input node `n`. Put differently, `c(n)` returns all the nodes to which
`n` is a parent.

* `c(n) := { (c in N) | nEc } := snk(n)`
* `c(n)` is the set of child nodes of `n`

Based on the characteristics of a node tree `p()` can be redefined as below.
As a matter of simplification, one can still assume that `p()` is defined to
return a set of nodes (i.e. a 1-element set of nodes).

* `(p: N -> N)` such that `p(n) := p` for `pEn`
* `p(n)` is the parent node of `n`
* `p(r)` is undefined for `(r in RN)`

<!-- ======================================================================= -->
## conclusions

* a root has no parent, but may itself be one
* a root is no child, but may itself have one
* `(#RN == 1)` and `(#N >= 1)` are both always true
* `(#p(c) == 1)` must be true for any `(c in CN)`
* `(#N == 1)` => `(RN,LN == {r})` and `(PN,CN,IN == {})`
* `(#N >= 2)` => `(RN,PN,CN,IN,LN != {})`
* a tree always has one or more leaf nodes
* trees may or may not have inner nodes

With regards to a node's parent - a parent-based view:

* `RN := (N \ CN)`
* note - `RN` and `CN` are disjoint
* any node is either a root ex-or a child
* all nodes, except for the root, are child nodes
* a leaf is no parent, but may itself have one

With regards to a node's child nodes - a child-based view:

* `PN := (N \ LN)`
* note - `PN` and `LN` are disjoint
* any node is either a parent ex-or a leaf
* any node, except for a leaf, is a parent
* a leaf has no child, but may itself be one

Note that each non-root node `(n in N\RN)` is a sink to one and only one edge.
That is, each child node has exactly one incoming edge. In contrary to that,
each non-leaf node `(n in N\LN)` is a source to one or more edges. That is,
each parent node has one or more outgoing edges. Put differently, each node
may be the sink of an edge no more than once. In contrary to that, any node
may act as a source to any number of edges.
