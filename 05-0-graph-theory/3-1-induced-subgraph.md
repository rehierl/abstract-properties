
<!-- ======================================================================= -->
# Induced subgraphs

There are two methods that can be used to form an induced subgraph: (V) based
on a given subset of vertices, and (E) based on a given subset of edges.

<!-- ======================================================================= -->
## induced subgraph (V)

By default, an **induced subgraph** `S := G[X] := (T,U)` is formed from another
graph `G := (V,E)` by removing some of its vertices. In addition to that, the
subset of edges `U` is formed from the set of edge `E` by removing all of those
edges that have one of their endpoints not in `T` (i.e. the implicit removal of
incident edges). As such, the induced subgraph `S` may be described as being
**induced by a subset of vertices**.

* `(T subset-of V)` where `T := (V & X)`
* `U := { (e in E) | (E(e) subset-of T) }`
* i.e. `U` contains all the edges in `E` whose endpoints are both in `T`

Note that there is no freedom when forming the subset of edges `U`. That is,
the subset of edges `U` can be understood as a consequence of the subset of
vertices `T`.

Note that **the term "induced"** can therefore be understood as: The resulting
graph is formed based on a given set of vertices and based on a rule that allows
to uniquely determine all the edges in the induced subgraph.

<!-- ======================================================================= -->
## induced subgraph (E)

Similar to that, an induced subgraph `S := (T,U)` of graph `G := (V,E)` may
be referred to as being **induced by a subset of edges** (i.e. `S := G[Y]`).
As such, the set of edges in `U` contains all those edges in `Y` that are also
edges in `E` (i.e. `U == (E & Y)`). Consequently, the rule used to form such
a subgraph is to remove all those vertices in `G` that are no endpoint to any
edge in `U`.

* `S := G[Y] := (T,U)` where `U := (E & Y)` and
* `T := { (v in V) | (v endpoint-of e) for some (e in U) }`
* note - `(G[Y] subgraph-of G)` is true

<!-- ======================================================================= -->
## induced proper subgraph

An **induced strict/proper subgraph** `S := (T,U)` is an induced subgraph of
graph `G := (V,E)`, if it was formed by removing at least one vertex and/or
edge. (Note that `S` may also be referred to as a "strict/proper induced
subgraph").

Note that the requirement of having fewer vertices and/or edges is in regards
to the resulting subgraph. That is, the subset of vertices or edges used to
form an induced subgraph is in principle not required to have fewer elements
than the corresponding set in the super-graph.

<!-- ======================================================================= -->
## remarks - (V)

Note that `(G[V] == G)` is (always) true.

Note that, in the context of (binary) relations, an induced subgraph is a
restriction of its super-relation. That is, the corresponding sub-relation
is restricted to the given subset of vertices.

* `(S == G[V]) -> (#U == #E)`
* `(S == G[T]) -> (#U <= #E)`, if `(#T < #V)`
* `(S subgraph-of G[V]) <-> (S subgraph-of G)`

<!-- ======================================================================= -->
## remarks - (E)

Note that `(G[E] == G)` may not be true.
That is because `G` may have disconnected vertices.

Note that `G[U]` can not have disconnected vertices. Despite that, `G[U]` is
still not necessarily connected since it may consist of components that all
have two or more vertices. Hence, `(G[E] == G)` may be used as a requirement
to only express that `G` must not have disconnected vertices.

Note that an induced proper subgraph `S := G[U]` (i.e. `(#U < #E)`) may have
the same set of vertices as `G` (i.e. `(T == V)`). That is because all vertices
in `G` may be incident to more than one edge.

* `(S == G[E]) -> (#T <= #V)`
* `(S == G[U]) -> (#T <= #V)`, if `(#U < #E)`
* `(S subgraph-of G[E]) -> (S subgraph-of G)`

<!-- ======================================================================= -->
## remarks - in general

Note that any induced subgraph `S := (T,U)` of a graph `G := (V,E)` is by the
definition of the "subgraph-of" operator also a subgraph of `G`. However, an
arbitrary subgraph of a graph is not necessarily also an induced subgraph
since an arbitrary subgraph may be formed by also removing vertices and edges.

* `(S induced-subgraph-of G) -> (S subgraph-of G)`

Note that an induced subgraph may be clarified as being "induced by a subset
of vertices" (i.e. `G[T]`, `G[V]` or `G[X]`), or as being "induced by a subset
of edges" (i.e. `G[U]`, `G[E]` or `G[Y]`). In addition to that, `G[T]` and
`G[U]` are used to express that the induced subgraph is formed by some subset,
which may or may not be equal to the corresponding set in `G`. In contrary to
that, `G[V]` and `G[E]` are used to express that the induced subgraph is formed
by the corresponding complete set in `G`.

Note that the set of vertices `X` in `G[X]` is not strictly required to be equal
to `T`. Likewise, the set of edges `Y` in `G[Y]` is not strictly required to be
equal to `U`. However, the input sets (i.e. `X` and `Y`) are in general expected
to be subsets of the corresponding set in `G` and therefore expected to be equal
to the corresponding set in `S`. That is, `(T == (V & X))` and `(U == (E & Y))`
are in general both expected to be true.

Note that there is in general no requirement or limitation as to how the input
set of vertices or edges is formed. That is, the empty graph `Ø` can be seen as
an induced subgraph of another graph (i.e. `Ø := G[{}]`), induced by an empty
set of vertices, or induced by an empty set of edges.
