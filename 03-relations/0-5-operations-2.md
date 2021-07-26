
<!-- ======================================================================= -->
## union (+, or, add)

A union of (endo-)relations is formed by merging the corresponding sets of
elements.

* `R := (D,G)`, `S := (T,U)`
* `X := (Y,Z)` where `Y := (D + T)` and `Z := (G + U)`

However, since the overall focus in the context of this discussion is on
"related things", disconnected vertices will be **silently dropped**. Based
on that, the union of two endo-relations can be loosely defined as follows:

* `(R + S) := { (a,b) : aRb or aSb }`

Note that with this simplification, an implicit operation is associated. That
is, first the resulting set of edges is formed, then all the endpoints of
these edges are used to create the set of vertices of the resulting relation.

<!-- ======================================================================= -->
## intersection (&, and)

The intersection of two relations is formed by holding on to the edges that
are common to both relations.

* `(R & S) := { (a,b) : aRb and aSb }`

<!-- ======================================================================= -->
## disjoint

Two (endo-)relations can be described as being disjoint, if the correspondings
sets of edges are disjoint.

* `(R disjoint-to S) := (G disjoint-to U)`

Note that `aRb` and `bSa` may still be true.

<!-- ======================================================================= -->
## difference (\, sub)

The difference operation removes all the edges in `S` from `R`.

* `(R \ S) := { (a,b) : aRb and !aSb }`

<!-- ======================================================================= -->
## overlap

Two relations can be said to overlap each other, if the corresponding sets of
edges overlap each other.

* `(R overlaps S) := (G overlaps U)`
* `(R overlaps S) := ((G & U) != Ø) and ((G \ U) != Ø) and ((U \ G) != Ø)`

<!-- ======================================================================= -->
## symmetric difference (^, xor, ex-or)

The symmetric difference between two relations is formed by removing the
intersection from the union over both relations.

* `(R ^ S) := (R + S) \ (R & S)`
