
<!-- ======================================================================= -->
# subgraph

A (simple) **subgraph** `S := (T,U)` is a graph formed from its super-graph
`G := (V,E)` by removing vertices and/or edges from `G`.

* `(S subgraph-of G) := (T subset-of V) and (U subset-of E)`
* `(S subgraph-of G) -> (#T <= #V) and (#U <= #E)`

Similar to simple sets, a **strict/proper subgraph** `S := (T,U)` is formed by
removing at least one vertex and/or edge from its super-graph `G := (V,E)`. Any
graph `G` is therefore a (simple) subgraph, but no proper subgraph to itself.

* `(S proper-subgraph-of G) := (S subgraph-of G) and (S != G)`
* `(S proper-subgraph-of G) -> (#T < #V) and/or (#U < #E)`

In this context, `(S != G)` is equivalent to `(#T != #V) and/or (#U != #E)`.
In addition to that, the sets of vertices and/or edges in `S` must have fewer
elements (i.e. `<` instead of `!=`) than the corresponding set in `G`.

<!-- ======================================================================= -->
## related

Two graphs `S := (T,U)` and `G := (V,E)` are said to be **related**
with each other, if one is a subgraph of the other.

* `(S related-to G) := (S subgraph-of G) or (G subgraph-of S)`

Two graphs `S` and `G` are said to be **strictly/properly related**
with each other, if both are related but not equal to each other.
That is, one graph is a proper subgraph of the other.

* `(S strictly-related-to G) := (S related-to G) and (S != G)`

Two graphs `S` and `G` are said to be **unrelated** with each other,
if neither of them is a subgraph of the other.

* `(S unrelated-to G) := not (S related-to G)`
* i.e. `(S no-subgraph-of G) and (G no-subgraph-of S)`

Note that no definition is possible for "strictly unrelated".

<!-- ======================================================================= -->
## remarks - removal

Note that, if vertex `(v in V)` is removed from a graph, then all the edges
`(e in E)`, to which `v` is an endpoint, must also be removed. That is because
a subgraph must still satisfy the definition of a graph in which the endpoints
of its edges must all be vertices in its set of vertices. Hence, edges may be
removed without further consequence, but the removal of a vertex may trigger
the (implicit) removal of one or more incident edges.

* `T` must include both endpoints of each edge in `U`
* `(E(e) subset-of T)` must be true for any edge `(e in U)`
* no edge in `U` can lead in-to and/or out-of `T`

Note that in the context of general graphs, a subgraph may still have the same
amount of vertices and/or edges. In contrary to that, a proper subgraph may
still have at most one set (i.e. vertices ex-or edges) that is equal to the
corresponding set in its super-graph. Put differently, for a subgraph to be a
proper subgraph, at least one of these sets are required to have fewer elements.

<!-- ======================================================================= -->
## remarks - semantics

Note that the semantics of a subgraph is assumed to be identical to the
semantics of its super-graph. The same applies to an empty subgraph formed
from another graph by removing all of its vertices and edges. And because the
empty graph `??` can be formed from any graph (even the empty graph itself),
the semantics of the empty graph needs to be understood to correspond with
the semantics of any (non-empty) graph.

Note that that is not necessarily true if a sub-graph is formed from a graph
that has heterogenous semantics. That is because the subgraph formed may have
homogenous semantics.
