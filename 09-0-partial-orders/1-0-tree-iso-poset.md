
<!-- ======================================================================= -->
# node tree <=> node order

<!-- ======================================================================= -->
## node tree => node order

One can easily form an explicit node order `Q := (N,<)` from a given node tree
`T := (N,E)` by the following simple definition.

* `Q := (N,<)` such that `N := V(T)`
* `(a < b) := (p := [a,..b] in P over T) and (#p > 1)`

That is, the set of vertices in `Q` is equal to the set of nodes in `T`. In
addition to that, two nodes are connected in `Q` iff a path of node length
2 or more can be formed between both nodes.

Formed as such, the following applies ..

* `Q` may have pairs of incomparable nodes
* `<` is directional - a node tree is a digraph
* `Q` is transitive - based on paths over `T`

One can therefore conclude, that the node order
`Q` is **a strict partial order** of nodes.
