
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

Similar to simple sets of elements, two graphs `S := (T,U)` and `G := (V,E)`
are said to be **disjoint** (from one another), if both have neither vertices
nor edges in common:

* `(S disjoint-to G) := (T disjoint-to V) and (U disjoint-to E)`

Graph `S` can be described to **intersect** graph `G`, if both are not disjoint.
As such, both graphs can be understood to be **coupled** with each other via
the elements they share:

* `(S intersects G), (S coupled-with G) := not (S disjoint-to G)`

Like the common elements in coupled simple sets of elements, common vertices
and/or edges act as a "link" between both graphs. These links can be understood
to bind both graphs together, which is why two such graphs can be said to be
"connected" or "coupled" by some "point of contact".

Two graphs `S` and `G` are said to **overlap** (each other), if both are coupled
with each other, and if both have one or more vertices and/or edges the other
graph does not have.

* `(S overlaps G) := (S coupled-with G) and (S unrelated-to G)`

<!-- ======================================================================= -->
## intersecting graphs

In general, if graphs `S := (T,U)` and `G := (V,E)` have an edge in common,
then both graphs must also share both of the endpoints of that edge. Because
of that, two graphs that have intersecting sets of edges also have intersecting
sets of vertices. However, two graphs that have intersecting sets of vertices,
do not necessarily also have intersecting sets of edges since all of the shared
vertices may be disconnected.

* `(U intersects E) -> (T intersects V)`

If `(U subset-of E)` is true (i.e. all the edges in `U` are edges in `E`),
then a vertex `(v in T)` may still exist that is no vertex in `V`. Vertex `v`
must however be disconnected since an edge incident to `v` would then have to
be an edge in `E`, which in turn would require `v` to also be a vertex in `V`.
Because of that, `(U subset-of E)` does not imply that `(T subset-of V)` is
also true.

Likewise, if `(T subset-of V)` is true, then an edge in `U` may still exist
that is no edge in `E`. Because of that, `(T subset-of V)` does not imply
that `(U subset-of V)` is also true.

Put differently, if `(U subset-of E)` is true, then both graphs may still have
overlapping sets of vertices. Likewise, if `(T subset-of V)` is true, then both
graphs may still have overlapping sets of edges. That is, both graphs need to
have further characteristics for both pairs of sets to be related in some way.

* `(U subset-of E) <=!=> (T subset-of V)`

If `(U subset-of E)` is true, in addition to `S` having no disconnected vertex,
then `(T subset-of V)` is also true. That is because every vertex in `T` then
is an endpoint to one or more edges in `U` and as such also a vertex in `V`.
(Note however that `G` may still have disconnected vertices). In contrary to
that, if `(T subset-of V)` is true in addition to `S` having no disconnected
vertices, then `(U subset-of E)` is still not necessarily true. That is because
`U` may still have an edge not in `E`.

* `(U subset-of E) -> (T subset-of V)`

Note that an empty subgraph `S` of a graph `G` is disjoint to its supergraph,
regardless of whether the supergraph is itself empty or not.

* `(S == Ø)` => `(S subgraph-of G)` and `(S disjoint-to G)`

Note that a non-empty subgraph is coupled with its (non-empty) supergraph.
That is, a non-empty subgraph is never disjoint to its supergraph.

* `(S != Ø)` and `(S subgraph-of G)` => `(S coupled-with G)`
* `(S related-to G) -> (S coupled-with G)` if `(S != Ø)`
