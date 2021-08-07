
<!-- ======================================================================= -->
# (finite directed) graphs

A graph `G := (V,E)` is an endo-relation that consists of
a set of vertices `V` and a set of edges `E` such that ..

* `V` is the possibly empty set of vertices
* `E` is the possibly empty set of directed edges
* `V` and `E` are both finite sets of elements
* `(E(e) subset-of V)` for each `(e in E)`
* `(E subset of (V × V))`

A graph `G := (V,E)` is referred to as ...

* a/the null/empty graph `Ø`, if `(G == ({},{}))`
* an "edge-less graph", if `(#E == 0)`
* a "trivial graph", if `(#V == 1)` and `(#E == 0)`
* an "edge graph", if `(#V == 2)` and `(#E == 1)` and no loop
* **G is oriented**, if `xEy` then `!yEx` (i.e. one direction only)
* **symmetric**, if `xEy` then also `yEx` for all `(x,y in V)`

The following can be said about the vertices of any edge `((x,y) in E)`:

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
## (sub)sets of vertices

As a matter of simplification, the following sets of vertices can be assumed
to be defined as follows:

* `VI := { (v in V) | xEv for some (x in V) }`
* `VI` is the set of vertices that have an incoming edge
* `VO := { (v in V) | vEx for some (x in V) }`
* `VO` is the set of vertices that have an outgoing edge

Based on these subsets, the following dedicated subsets can be defined:

* `DV := { (v in V) | (v !in VI) and (v !in VO) }`
* `DV` is the set of disconnected/isolated vertices
* `CV := { (v in V) | (v in VI) or (v in VO) } := (V \ DV)`
* `CV` is the set of connected vertices
* `LV := { (v in V) | vEv }`
* `LV` is the set of vertices that have a loop

In regards to the overal graph, the following subsets can be defined:

* `SRC := { (v in V) | (v !in VI) and (v in VO) }`
* `SRC` is the set of source vertices
* `SNK := { (v in V) | (v in VI) and (v !in VO) }`
* `SNK` is the set of sink vertices
* `INT := { (v in V) | (v in VI) and (v in VO) }`
* `INT` is the set of internal vertices

<!-- ======================================================================= -->
## helper functions

Similar to the above subsets, a function `(src: V -> P(V))` can be defined which
returns the set of those vertices to which the input vertex `v` is a sink. Put
differently, `src(v)` returns all those vertices that are a source vertex to `v`.

* `src(v) := { x | xEv }`

Likewise, a function `(snk: V -> P(V))` can be defined which returns a set of
vertices to which the input vertex `v` is a source. Put differently, `snk(v)`
returns all those vertices that are a sink vertex to `v`.

* `snk(v) := { x | vEx }`

Based on these functions, the following definitions can be provided:

* `ideg(v), in-degree(v) := #(src(v))`
* `odeg(v), out-degree(v) := #(snk(v))`
* `deg(v), degree(v) := (ideg(v) + odeg(v))`

In words: `ideg(v)` counts the number of incoming edges whereas `odeg(v)` counts
tne number of outgoing edges. Consequently, `deg(v)` counts the total number of
edges to which the given vertex `v` is an endpoint. (Note that loops are counted
twice).

* `v` is disconnected, if `(deg(v) == 0)`, otherwise `v` is connected
* `v` is a source vertex, if `(ideg(v) == 0)` and `(odeg(v) > 0)`
* `v` is a sink vertex, if `(odeg(v) == 0)` and `(ideg(v) > 0)`

Similar to that, a function `order(G)` can be defined which returns the number
of vertices in it. In contrary to that, the size of a graph `size(G)` is defined
as the number of edges in it.

* `order(G) := #V`
* `size(G) := #E`
