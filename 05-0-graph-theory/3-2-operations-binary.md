
<!-- ======================================================================= -->
# Binary operations on graphs

The following operations `(op: (G,H) -> X)` take two input graphs `G` and `H`
in order to produce a result:

* two graphs `S := (T,U)` and `X := (Y,Z)` are used to create some result
* e.g. a new graph `op(G,H) -> (V',E')`

<!-- ======================================================================= -->
## union (+, or, union)

Graph `G := (V,E)` is said to be the **union** graph `G := (S + X)` of two
graphs `S := (T,U)` and `X := (Y,Z)`, if its vertex-set is the union of `T`
and `Y`, and if its edge-set is the union of `U` and `Z`.

* `G := (S + X) := (V,E)`, where
* `V := (T + Y)` and `E := (U + Z)`
* associative - `(A + B + C) == ((A + B) + C) == (A + (B + C))`
* commutative - `(A + B) == (B + C)`

Note that `S` and `X` are not required to be disjoint.

<!-- ======================================================================= -->
## intersection (&, and, isect)

Graph `G := (V,E)` is said to be the **intersection** graph `G := (S & X)`
of two graphs `S := (T,U)` and `X := (Y,Z)`, if `G` was formed by taking all
vertices and edges that are common to both. Put differently, if its vertex-set
is the intersection between `T` and `Y`, and if its edge-set is the intersection
between `U` and `Z`.

* `G := (S & X) := (V,E)`, where
* `V := { (v in T) | (v in Y) }` and `E := { (e in U) | (e in Z) }`
* associative - `(A & B & C) == ((A & B) & C) == (A & (B & C))`
* commutative - `(A & B) == (B & C)`

Note that the intersection graph `G := (S & X)` is a subgraph of `S` and `X`.

* if `(G := (S & X))` => `(G subgraph-of S)` and `(G subgraph-of X)`

Two graphs `S` and `X` are said to **intersect** (each other), if their
intersection graph `(S & X)` is distinct from the empty graph `Ø`.

* `(S intersects X) := ((S & X) != Ø)`
* `(S intersects X) <-> (X intersects S)`
* `(S intersects X) <-> (S coupled-with X)`

Note that "intersects" is equivalent to "coupled-with".

<!-- ======================================================================= -->
## remarks on - intersection

As above, two intersecting graphs are not necessarily related to each other.
That is because two such graphs are either related ex-or overlap each other.

* `(S related-to G) -> (S intersects G)` (i.e. if `S` and `G` are non-empty)
* `(S intersects G) <-> (S related-to G) ex-or (S overlaps G)`

The set of vertices `V` in an intersection graph `G := (S & X)` does not allow
to determine the set of common edges `E` based on one of the input graphs. That
is, the intersection graph `G` is not (necessarily) an induced subgraph of one
or both of the input graphs (i.e. `(G == S[V])` and `(G == X[S])` are both not
necessarily true). Because of that, the set of common edges must be determined
by comparing the sets of edges in the input graphs.

Example 1: The intersection graph `G := (S & X)` of `S := ({1,2},{(1,2)})` and
`X := ({1,2},{(2,1)})` is `G := ({1,2},{})`. That is, `G` is not an induced
subgraph to any of them (i.e. `(G == S[V])` and `(G == X[V])` are both false).

Example 2/3: The intersection graph `G := (S & X)` of `S := ({1,2},{(1,2)})` and
`X := ({1,2},{})` is `G := ({1,2},{})`. That is, `G` is not an induced subgraph
of `S`, but an induced subgraph of `X` (i.e. in contrary to `(G == S[V])` being
false, `(G == X[V])` is true).

Example 4: The intersection graph `G := (S & X)` of `S := ({1,2},{(1,2)})` and
`X := ({1,2,3},{(1,2)})` is `G := ({1,2},{})`. That is, `G` is an induced
subgraph of `S` and an induced subgraph of `X` (i.e. `(G == S[V])` and
`(G == X[V])` are both true).

<!-- ======================================================================= -->
## options to define the graph difference (\)

The definition of the graph-difference operation `T := (G \ S)` needs to define
which elements in `S` to remove from `G`. That is because, in contrary to simple
sets of elements, graphs contain elements/vertices and their relationships/edges
rather than a single type of elements.

Note that the definition of the set-difference `C := (A \ B)` is based upon
the removal of elements. That is, `C` is formed by removing all the elements
in `B` from `A`. Because of that, `(A \ B)` is a subset of `A`.

### option-0, Remove nothing at all

Removing no vertices and no edges at all has obviously no effect on `G`. That
is because the operation will then have to return `G` as `T` (i.e. without any
modification). Obviously, that option does not cover the intention behind this
operation.

### option-1, Remove all the edges in S from G

This option is intended to remove all the edges in `S` from the edges in `G`,
while maintaining the vertices in `G`.

Recall that the endpoints of an edge in a graph must both be vertices in the
graph's set of vertices. Because of that, an edge in `S` can only be removed
from `G`, if `G` contains the corresponding edge and both of its endpoints.

Example 1: The graph difference `T := (G \ S)` of `G := ({1,2},{(1,2),(2,1)})`
and `S := ({1,2},{(1,2)})` under that option is `T := ({1,2},{(2,1)})`.

Example 2: The graph difference `T := (G \ S)` of `G := ({1,2},{(1,2)})` and
`S := ({1,2},{(1,2)})` under that option is `T := ({1,2},{})`. That is, the
resulting graph is a graph of disconnected vertices.

Note that the complement graph `G*` is defined based upon the removal of edges:
`G* := (K(G) \ G)`. That is, all edges in `G` need to be removed from its
induced complete graph `K(G)`. The disadvantage of this option is that the
complement graph of a complete graph is, in contrary to the empty complement of
the universal set of elements, an edgeless graph of vertices.

### option-2, Remove all the vertices in S from G

This option is intended to remove all the vertices in `S` from the set of
vertices in `G`, while maintaining the set of edges in `G`.

Recall that the endpoints of any edge `e` in a graph `G := (V,E)` must both
be elements in `V` (i.e. `(E(e) subset-of V)`). Because of that, and if a
vertex `(v in V)` would have to be removed, then any edge `(e in E)` incident
to `v`, must also be implicitly removed. That is, because the result of such
an operation would otherwise not be a graph. Consequently, the removal of all
vertices in `S` also results in the implicit removal of any edge that are
incident to a removed vertex.

Example: The graph difference `T := (G \ S)` of `G := ({1,2,3},{(1,2),(2,3)})`
and `S := ({1},{})` under that option is `T := ({2,3},{(2,3)})`.

Note that even edges, which are no edges in `S`, may have to be removed.

### option-3, Remove all the vertices and all the edges in S from G

Because once all the vertices in `S` have been removed from `G` (including the
implicit removal of any incident edge), no edge in `G` remains that could still
be an edge in `S`. Because of that, the subsequent removal of all the edges in
`S` from `G` will no longer have any effect. The removal of all the vertices in
`S` will therefore also implicitly remove all the edges in `S`. This option is
consequently equivalent to option-2.

Example: The graph difference `T := (G \ S)` of `G := ({1,2,3},{(1,2),(2,3)})`
and `S := ({1,2},{(1,2)})` under that option is `T := ({3},{})`.

<!-- ======================================================================= -->
## difference (\, sub, diff)

Due to the above, there are only two options available that allow to define
the difference between two graphs. Because of that, option-1 will be referred
to as the **edge-based**, and option-2 as the **vertex-based** definition.

The difference graph of the difference graph `(G \ G)` under the edge-based
definition is an edgeless graph of vertices (i.e. one component per vertex).
In contrary to that, the difference graph `(G \ G)` under the vertex-based
definition is the empty graph `Ø`. Because of that, the vertex-based definition
is more suited for the definition of the relationship between a graph and its
subgraphs as it is more consistent compared with the difference between simple
sets of elements.

* `(G diff S) := (V,E)` where
* `V := (V(G) \ V(S))` and `E := { (x,y) in E(G) | (x,y !in V(S)) }`
* `(G \ S), (G - S), (G sub S) := (G diff S)`
* i.e. **the vertex-based definition**

Note that ...

* `((G \ Ø) == G)` and `((G \ G) == Ø)`
* `((G \ S) disjoint-to S)`
* `((G \ S) subgraph-of G)`

Note that `(G \ S)` can be also defined as an induced subgraph of `G`:

* `(G diff S) := G[V(G) \ V(S)]`

In `T := (G \ S)`, `S` is not required to be a subgraph of `G`. Likewise, `S`
may not overlap `G`, or both graphs may even be disjoint from one another.
However, in the context of this discussion, the intersection between `S` and
`G` is assumed to be non-empty. Furthermore, `S` is assumed to be reduced to
that intersection, which is why `S` is assumed to have no elements (vertices
and/or edges) outside of `G`. That is, `S` is in general expected to be a
non-empty subgraph of `G`.

* `S` is stripped of any elements not in `G`
* i.e. `S := (G & S)`, i.e. `(S subgraph-of G)`

<!-- ======================================================================= -->
## symmetric difference (^, xor, ex-or)

With the above vertex-based definition, the symmetric difference between two
graphs can be defined "similar" to the symmetric difference between two simple
sets of elements.

* `(G ex-or S) := (G \ S) + (S \ G)`
* `(G ^ S), (G xor S) := (G ex-or S)`
