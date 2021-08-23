
<!-- ======================================================================= -->
# (finite directed) graphs

A graph `G := (V,E)` is an endo-relation that consists of
a set of vertices `V` and a set of edges `E` such that ..

* `V` is the possibly empty set of vertices
* `E` is the possibly empty set of directed edges
* `V` and `E` are both finite sets of elements
* `(E(e) subset-of V)` for each `(e in E)`
* `(E subset of V×V)`

A graph `G := (V,E)` is referred to as ...

* a/the null/empty graph `Ø`, if `(G == ({},{}))`
* an "edge-less graph", if `(#E == 0)`
* a "trivial graph", if `(#V == 1)` and `(#E == 0)`
* an "edge graph", if `(#V == 2)` and `(#E == 1)` and no loop
* **G is oriented**, if `xEy` then `!yEx` (i.e. one direction only)
* **symmetric**, if `xEy` then also `yEx` for all `(x,y in V)`

The following can be said about the vertices of any edge `(e in E)`:

* `e := (x -> y) := (x,y)`
* `x` and `y` are both endpoints of `e`
* `x` and `y` are adjacent to each other
* `x` is covered by `y`, and `y` is covered by `x`
* `x` is a source to `y`, and `y` a sink to `x`

The following can be said about any edge `(e in E)`
and the relationship it has with both of its vertices:

* `e` is an ordered pair of vertices
* `e` begins in `x` and ends in `y`
* each edge is oriented from `x` to `y`
* the endpoints of an edge are considered un-equal
* `e` is an outgoing edge to `x`, and an incoming edge to `y`
* `e` has `x` as its source and `y` as its sink
* `e` is incident to `x` and `y`
* `e` is a loop if `(x == y)`
* `e` is a link if `(x != y)`
* a graph is loop-less, if there is no loop in `E`

In regards to the visual representation of an edge
as an arrow, the following can be clarified:

* `(x -> y) := (x,y)`
* an arrow that has its head pointing at `y`
* sink `y` can therefore be described as a head
* an arrow that has its tail at `x`
* source `x` can therefore be described as a tail

Each graph can be understood to be accompanied by an
indicator function `E()` such that ..

* `(E: V×V -> Bool)` or `E(x,y) := ((x,y) in E)`
* `E(x,y)` returns true if `x` is a source to `y`
* `E(x,y)` returns true if `(x,y)` is an element in `E`
* a notational simplification - `xEy := E(x,y)`

Each graph can be understood to be accompanied by an
indicator function `A()` such that ..

* `(A: V×V -> Bool` or `A(x,y) := (xEy or yEx)`
* `A(x,y)` returns true if `x` is a source or a sink to `y`
* `A(x,y)` returns true if `x` is adjacent to `y`
* a notational simplification `xAy := A(x,y)`

For purposes of clarification, the following operators may be used
in the context of multiple graphs:

* `(V: Graph -> Set)` or `V(G) := V` where `G := (V,E)`
* `V(G)` returns the set of vertices in graph `G`
* `(E: Graph -> Set)` or `E(G) := E` where `G := (V,E)`
* `E(G)` returns the set of edges in graph `G`
* `(A: Graph -> Set)` or `A(G) := { {x,y} | xAy } `
* `A(G)` returns the set of undirected edges/arcs of graph `G`

<!-- ======================================================================= -->
## isomorphic

Two graphs are **isomorphic** (to each other), if an isomorphism exists that
maps one graph onto the other.

Note that two isomorphic graphs may have different semantics. Because of that,
and in the context of this discussion, "isomorphic" is understood in the sense
of "both graphs have isomorphic structure", whereas "equal" is understood in
the sense of "both represent the exact same graph".
