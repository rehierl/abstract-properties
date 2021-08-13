
<!-- ======================================================================= -->
# path graph <=> node order

Given a non-empty path graph `s := (N,E)` ..

* `s := n1 -> n2 -> n3 -> n4 -> n5 -> n6`

one can easily form a node order by defining
the order operator based on the paths over `s`.

* `Q := (N,<)` such that `N := V(s)`
* `(a < b) := (p := [a,..,b] in P over s) and (#p > 1)`

One can then recreate `s` from `Q` by forming the transitive
reduction over the edges in the order relation of node order `Q`.

* `s* := (N,E)` such that `N := V(Q)`
* `E` := the transitively reduced edges of order relation `Q`.
* note - `(s* == s)`

Consequently, any path graph can be said to be **isomorphic** to a
strict total node order. That is, one can be transformed into the other.

<!-- ======================================================================= -->
## path graph => node order

One can easily form an explicit node order `Q := (N,<)` from a given path graph
`s := (N,E)` by the following simple definition.

* `Q := (N,<)` such that `N := V(s)`
* `(a < b) := (p := [a,..,b] in P over s) and (#p > 1)`

That is, the set of vertices in `Q` is equal to the set of nodes in `s`. In
addition to that, two nodes are connected in `Q` iff a path of node length
2 or more can be formed between both nodes.

Formed as such, the following applies ..

* `Q` has no pair of distinct incomparable nodes
* `<` is directional - a path graph is a digraph
* `Q` is transitive - based on paths over `s`
* `Q` is trichotomous - all nodes in `s` are nodes in `rp(l)`

One can therefore conclude, that the node order
`Q` is **a strict total order** of nodes.

<!-- ======================================================================= -->
## node order => path graph

One can then recreate `s` from `Q` by forming the transitive
reduction over the edges in the order relation of node order `Q`.

* `s* := (N,E)` such that `N := V(Q)`
* `E` := the transitively reduced edges of order relation `Q`.

Note that defining the order operator of `Q` based on the paths that can be
formed over `s` ensures that `Q` is transitive. In addition to that, a path
graph is such that it has no transitive edge. Because of that, `s*` is equal
to `s` since the transitive reduction is can, due to the above, be guaranteed
to reproduce the same set of edges.
