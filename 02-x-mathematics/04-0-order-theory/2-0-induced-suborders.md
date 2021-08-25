
<!-- ======================================================================= -->
## relations / restriction

The restriction `S := (T,U)` of a relation `R := (D,G)` can be described as
an induced result. After all, the source realtion `R` will be restricted
to the subset of elements `T` while preserving the relative order between
those elements that remain. The restriction of a relation can therefore be
described to return an **induced sub-relation** `R[T]`.

* `S := R[T] := (T,U)` such that
* `U := { (a,b) | aRb and (a,b in T) }`

Note that an **induced subtree** `T[r]` is defined such that it consists of
the given root node `r` and all of its descendants in `T`, while preserving
the relative order between the remaining nodes. That is, as an induced subtree
is, as described above, formed based on a specific input and a specific set
of operations.

<!-- ======================================================================= -->
## induced suborder

Due to the above, **an induced suborder** `S := (T,U)` can be defined as the
restriction of a super-order `R := (D,G)`.

* `S := R[T]`.

That is, the resulting suborder can be described is being induced by a set of
those vertices that need to remain in the suborder. Similar to induced subtrees,
this definition can be specialized as follows:

* `R[v] := R[T]`
* where `T := { x | (v <= x) for (x,v in D) }`
* and `(v <= x) := (v presequent-to x) or (x equal-to v)`

Recall that "presequent-to" denotes the default/generic sequence-based semantics
of an edge in regards to the source order. Also, each order relation is required
to be transitive.

Note that an induced suborder `R[v]` can be said to be **embedded as a suborder**
into the corresponding super-order `R`. Even though the word "embedded" isn't
strictly required, it can be understood to point out that the suborder is no
actual element within the super-order. That is, one mereley underlines the fact
that a suborder is "integrated" as a suborder. This clarification can be used
to keep others from misreading the word "contained" as "contained as an actual
element" until the word "suborder" is properly understood.
