
<!-- ======================================================================= -->
# Unary operations on trees

Note that the overall focus is on the subtrees of a document tree. In addition
to that, each subtree is in general assumed to be induced by its root node
(i.e. `S := T[r]`).

Recall that, if two graphs have an edge in common, then both graphs also have
both of the endpoints of that edge in common. In contrary to that, two graphs
may have one or more vertices, but no edge in common.

The following operations `(op: T -> X)` take a single input tree `T`
in order to produce a result:

* a single tree `T := (N,E)` is used to create some result
* e.g. a new graph `op(T) -> (V',E')`

<!-- ======================================================================= -->
## converse/transpose graph

Like any other directed graph, a tree can be transposed. However, the resulting
converse graph `T°` is in general not a tree.

* `conv(T) -> T° := (N,F)`
* `F := { (b,a) | aEb }`

`T°` will in general not be a tree since the parent nodes in `T` will be turned
into child nodes in `T°`. Likewise, the child nodes in `T` will be turned into
parent nodes in `T°`. Because of that, the child nodes in `T°` may end up having
multiple incoming edges and therefore multiple parent nodes.

`T°` will have the converse `child-of` semantics.

<!-- ======================================================================= -->
## reflexive reduction

The reflexive reduction of a tree `T` will return the input tree as-is.

Note that a tree can be considered minimal in regards to having loops. That is
because a tree, in the context of this discussion, is required to have no loop
at all. In contrary to that, a preorder can be considered maximal in that regards.

<!-- ======================================================================= -->
## reflexive closure

The reflexive closure of a tree `T` will return a non-tree graph that has a loop
for each of its nodes/vertices, in addition to all the edges in the input tree.

<!-- ======================================================================= -->
## transitive reduction

The transitive reduction of a tree `T` will return the input tree as-is.

That is because the removal of any edge from a tree will split the tree into a
graph that has one more connected component. Put differently, no tree has an
edge (e.g. `aEc`) for any pair of adjacent edges (e.g. `aEb` and `bEc`) in it.
After all, ..

* each tree has one and only one root
* each child (e.g. `b` and `c`) has one and only one parent

Note that a tree can be considered minimal in regards to transitive edges.
That is because it has no such edges. In contrary to that, a preorder can be
considered maximal in that regards.

<!-- ======================================================================= -->
## transitive closure

The transitive closure of a tree `T` will in general return a non-tree graph.

That is because the operation will add an edge (e.g. `aEc`) for any pair of
adjacent edges (e.g. `aEb` and `bEc`) in it. Consequently, a child (e.g. `c`)
will end up with multiple incoming edges and therefore with more than one
parent node.

* iteratively adds edge `aEc` for any pair of adjacent edges `aEb` and `bEc`
