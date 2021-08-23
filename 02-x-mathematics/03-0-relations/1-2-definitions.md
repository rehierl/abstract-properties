
<!-- ======================================================================= -->
## degenerated, empty

An endo-Relation `R` can be described as being empty (in the sense that it
does not define any relationships between its vertices), if its set of edges
is empty. Based on that, such a relation will be denoted by using the symbol
of an empty set (i.e. `Ø`).

* `(is-empty R) := (#G == 0)`

<!-- ======================================================================= -->
## contains

An endo-relation `R` is said to contain the endo-relation `S`, if all the
elements in both sets of `S` are elements in the corresponding set in `R`:

* `R := (D,G)`, `S := (T,U)`
* `(R contains S) := (T subset-of D) and (U subset-of G)`

Note that either of the sets in `S` may be equal to the corresponding set in
`R`. If only a disconnected vertex was removed from `R`, then `(G == U)` is
true. If however only one or more edges were removed, then `(T == D)` is true.
That is, if an edge is to be removed along with its endpoints, then its
endpoints need to be removed explicitly in `T`.

<!-- ======================================================================= -->
## restriction

A relation `S := (T,U)` is said to be a restriction of relation `R := (D,G)`,
if its set of vertices `T` is a (strict) subset to the set of vertices `D` in
`R`, and if `S` contains all the edges from `R` whose endpoints are both in `T`.

* `U := { (a,b) | aRb and (a,b in T) }`

Note that `(T subset-of D)` and `(U subset-of G)` are both true. However, `T`
is in general a strict subset of `D` since one would otherwise end up with `S`
being equal to `R`. In contrary to that, `U` is not necessarily a strict subset
to `G` (e.g. if only disconnected vertices were removed from `D`).

<!-- ======================================================================= -->
## (sub)sets of vertices

As a matter of simplification, the following sets of vertices can be assumed:

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

In regards to the overal relation, the following subsets can be defined:

* `SRC := { (v in V) | (v !in VI) and (v in VO) }`
* `SRC` is the set of source vertices
* `SNK := { (v in V) | (v in VI) and (v !in VO) }`
* `SNK` is the set of sink vertices
* `INT := { (v in V) | (v in VI) and (v in VO) }`
* `INT` is the set of internal vertices

<!-- ======================================================================= -->
## (helper) functions

Similar to the above subsets, a function `(src: V -> P(V))` can be defined which
returns the set of those vertices to which the input vertex `v` is a sink. Put
differently, `src(v)` returns all those vertices that are a source vertex to `v`.

* `src(v) := { (x in V) | xEv }`

Likewise, a function `(snk: V -> P(V))` can be defined which returns a set of
vertices to which the input vertex `v` is a source. Put differently, `snk(v)`
returns all those vertices that are a sink vertex to `v`.

* `snk(v) := { (x in V) | vEx }`

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
