
<!-- ======================================================================= -->
# Binary operations on graphs

The following operations `(op: (G,H) -> X)` take two input graphs `G` and `H`
in order to produce a result:

* two graphs `S := (T,U)` and `X := (Y,Z)` are used to create some result
* e.g. a new graph `op(G,H) -> (V',E')`

Note that both graph arguments are implicitly expected to be graphs of the same
sort. That is, the smantics of both graphs are expected to be the same. Because
of that, operations may only be applicable after the execution of semantical
conversions.

<!-- ======================================================================= -->
## equal, unequal, distinct

Two directed graphs `S := (T,U)` and `G := (V,E)` are considered **equal**,
if both have equal sets of vertices, equal sets of edges, and equal semantics.

* `(S == G), (S equal-to G) := (T == V) and (U == E) and (sem(S) == sem(G))`

Note that the "equal semantics" aspect ensures that both graphs are of the
same "sort". In a given context, the graphs in question usually automatically
satisfy that requirement, which is why the semantics of a graph are in general
ignored/omitted.

In contrary to that, two directed graphs are **unequal**, if they differ
in their sets of vertices, their sets of edges, and/or in their semantics.
Based on that, two graphs that are unequal can be described as being
**distinct** from one another.

* `(S != G), (S unequal-to G) := (T != V) or (U != E) or (sem(S) != sem(G))`
* `(S != G) := not (S == G)`

<!-- ======================================================================= -->
## disjoint, coupled, overlap

Given two (simple) sets `A` and `B`, the following definitions apply:

* `(A disjoint-to B) := ((A & B) == {})`
* `(A coupled-with B) := not (A disjoint-to B)`

Two graphs `S := (T,U)` and `G := (V,E)` are said to be **disjoint**
(from one another), if both have neither vertices nor edges in common:

* `(S disjoint-to G)`, if `(T disjoint-to V)` and `(U disjoint-to E)`
* `(S disjoint-to G) <-> (G disjoint-to S)`

Two graphs `S` and `G` are said to be **coupled** (with each other),
if both have one or more vertices (and/or edges) in common:

* `(S coupled-with G) := not (S disjoint-to G)`
* `(S coupled-with G) <-> (G coupled-with S)`

Like the common elements in coupled simple sets of elements, the above common
vertices and/or edges act as a "link" between both graphs. These links can be
understood to bind both graphs together, which is why two such graphs can be
said to be "connected" or "coupled" by some "point of contact".

Two graphs `S` and `G` are said to **overlap** (each other), if both are coupled
with each other, and if both have one or more vertices and/or edges the other
graph does not have.

* `(S overlaps G) := (S coupled-with G) and (S unrelated-to G)`
* `(S overlaps G) <-> (G overlaps S)`

<!-- ======================================================================= -->
## remarks on - disjoint, coupled, overlap

Note that both endpoints of an edge `(e in E)` in a graph `G := (V,E)` must
be elements in the graph's set of vertices `V` (i.e. `(E(e) subset-of V)`).
If that would not be the case, then `G` would not even satisfy the definition
of a graph.

Two coupled graphs `S := (T,U)` and `G := (V,E)` always have coupled sets of
vertices. That is because the endpoints of a common edge are also elements
in both sets of vertices `T` and `V`. The converse is however not necessarily
true. That is, two graphs that are coupled via coupled sets of vertices, do
not necessarily also have coupled sets of edges (e.g. both graphs may be
coupled via isolated vertices).

* `(U coupled-with E) -> (T coupled-with V)`
* `(S coupled-with G) <-> (T coupled-with V)`
* (`S` and `G` may still have edges in common)

Note that an empty subgraph `S` of a graph `G` is disjoint to its supergraph,
regardless of whether the supergraph is itself empty or not.

* `(S == Ø)` => `(S subgraph-of G)` and `(S disjoint-to G)`

Note that a non-empty subgraph is coupled with its (non-empty) supergraph.
That is, a non-empty subgraph is never disjoint to its supergraph.

* `(S != Ø)` and `(S subgraph-of G)` => `(S coupled-with G)`
* `(S related-to G) -> (S coupled-with G)` if `(S != Ø)`
