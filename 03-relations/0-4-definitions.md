
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
