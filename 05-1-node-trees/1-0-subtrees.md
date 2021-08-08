
<!-- ======================================================================= -->
# subtrees (of a graph)

A **(simple) subtree** `S := (T,U)` is a subgraph of a graph `G := (V,E)`
such that `S` has the characteristics of a tree (i.e. `isTree(S)` is true).

* `(S subtree-of G) := (S subgraph-of G) and isTree(S)`

That is, the super-graph `G` is not required to be a tree, which is why `G`
may or may not be a tree `G := (N,E)`. Because of that, the focus of this
definition is on the subgraph. However, depending on a given context, `S`
and `G` may both be required to have additional characteristics.

Note that a subtree is commonly defined as: "A connected subgraph of a tree".
Since this definition requires the super-graph `G` to be a tree, the subgraph
`S` is as a consequence a tree. Because of that, this common definition is
more specific than the above.

A **strict/proper subtree** `S := (T,U)` is a subtree formed from a graph
`G := (V,E)` by removing at least one vertex and/or edge. Hence, any tree
is a (simple) subtree, but no proper subtree to itself.

* `(S proper-subtree-of G) := (S subtree-of G) and (S != G)`

Note that the graph-based definitions of "related-to", "properly-related-to"
and "unrelated-to" are still applicable in the context of (sub)trees.

Note that the graph-based descriptions **unrelated**, **related** and
**strictly/properly related** can be used in the context of subtrees.

* `(S related-to G) := (S subgraph-of G) or (G subgraph-of S)`
* `(S strictly-related-to G) := (S related-to G) and (S != G)`
* `(S unrelated-to G) := not (S related-to G)`

<!-- ======================================================================= -->
## induced subtree

An **induced subtree** `S := (T,U)` is an induced subgraph formed from another
graph `G := (V,E)` such that `S` is a tree.

Similar as before, this definition does also not require the super-graph `G`
to be a tree. In addition to that, and like any other graph, an induced subtree
may be induced by a subset of vertices (i.e. `S := G[T]`), or by a subset of
edges (i.e. `S := G[U]`).

An **induced strict/proper subtree** `S := (T,U)` is an induced subtree formed
from another graph `G := (V,E)` by removing at least one vertex and/or edge.
(Note that `S` may also be referred to as a "strict/proper induced subtree").

<!-- ======================================================================= -->
## remarks

(*) As can be seen by the following example, not even the super-graph of an
induced proper subtree is necessarily a tree. Because of that, and if needed
in a given context, there would have to be an explicit requirement that the
super-graph of a tree is itself required to be a tree.

Example: `G := (V,E)` is a forest of two trees: a tree that only has a single
node, and another disjoint tree with two or more nodes. `G[E]` is therefore an
induced proper subtree, even though all the edges in `G` are used to form the
subtree. In contrary to that, `G[V]` is equal to `G` and thus not a subtree.

(*) `S` must be the subtree of a component in `G` since `S` could otherwise
not satisfy the requirements of a tree. That condition is however met, if `G`
is itself connected (e.g. a tree).

<!-- ======================================================================= -->
# subtrees (of a tree)

A **(simple) subtree** `S := (T,U)` of tree `G := (N,E)` is formed by removing
nodes and/or edges such that `S` is a tree. As such, a subtree is a connected
subgraph of a tree.

* `(U intersects E) -> (T intersects N)`
* `(S subtree-of G) -> (S subgraph-of G)`
* `(S subtree-of G) -> (T subset-of N) and (U subset-of E)`
* `(S subtree-of G) -> (#T <= #N) and (#U <= #E)`

A **strict/proper subtree** `S := (T,U)` of tree `G := (N,E)` is formed by
removing at least one node and/or edge such that `S` is a tree.

* `(S proper-subtree-of G) -> (S proper-subgraph-of G)`
* `(S proper-subtree-of G) -> (S subtree-of G) and (S != G)`
* `(S proper-subtree-of G) -> (#T < #N) and (#U < #E)`, if `isTree(G)`

<!-- ======================================================================= -->
## remarks

(*) In the overall context of this discussion, the super-graph `G := (V,E)` of
a subtree `S := (T,U)` is in general expected to be a tree (i.e. `G := (N,E)`)
and any of its subtrees are assumed to be induced proper subtrees.

(*) In general, a tree `G := (N,E)` can be formed by adding child nodes to their
parent nodes. As such, a tree has one and only one edge that connects a child
with its parent. And because a tree must by definition have exactly one root,
any tree has `(#N-1)` edges and `(#E+1)` nodes. The number of elements in both
sets are as such coupled with each other.

* `isTree(G) -> (#E == #N-1)`, if `G := (N,E)` and `(#N > 1)`
* note - `(#E < #N)` is always true for any tree

(*) If both trees have the same root (i.e. `(RN(S) == RN(G))`), then any subtree
`S := (T,U)` of tree `G := (N,E)` can be formed by iteratively removing a leaf
and its incident edge from `G`.

(*) Any subtree `S := (T,U)` of tree `G := (N,E)` can be formed by successively
removing the root and/or a leaf. Note however that a root can only be removed,
if it has one child only since otherwise one would end up with a forest.

Note that the removal of a leaf and its incident edge will always yield a
subtree. In contrary to that, the removal of a parent and its incident edges
does not necessarily yield a tree since the result will in egeneral be a
sub-forest (i.e. a multi-component non-tree subgraph) if the parent is itself
a child, or if the parent has more than one child.
