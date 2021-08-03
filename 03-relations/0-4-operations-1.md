
<!-- ======================================================================= -->
## empty

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
## restriction - R(T)

A relation `S` is said to be a restriction of relation `R`, if its set of
vertices `T` is a (strict) subset to the set of vertices `D` in `R`, and
if `S` contains all the edges from `R` whose endpoints are both in `T`.

* `S := R(T) := { (a,b) | aRb and (a,b in T) }`

Note that `(T subset-of D)` and `(U subset-of G)` are both true. However, `T`
is in general a strict subset of `D` since one would otherwise end up with `S`
being equal to `R`. In contrary to that, `U` is not necessarily a strict subset
to `G` (e.g. if only disconnected vertices were removed from `D`).

Note that this operation can be understood to be similar to the operation that
is used to form an **induced subtree**. That is, given an input node (as the
root node of the induced subtree `T[r]`) all the descendants of that node need
to be determined first. Hence, one first determines a subset of nodes and then
the edges that belong to the induced subtree. As such, the term **induced** can
be understood to be associated with well defined rules that need to be applied
based on the input available.

Note that this operation can be understood to be similar to the **subset-of**
operator in the context of sets of elements such that simple sets of elements
have no further information that could be added.

As such, a restriction can be said to form **an induced sub-relation** based
on a pre-determined subset of vertices. Hence, one could speak of an induced
sub-relation `R[v]`, if the subset of vertices were defined based on a given
single vertex - e.g. in terms of all those vertices that can be reached from
that initial vertex. (Recall that a relation is not necessarily transitive).

<!-- ======================================================================= -->
## sub-relation

Note that no direct counterpart to the subset-of operator will be provided
at this point. The reason is that specialized relations (such as trees and
order relations) should provide specialized definitions.

- TODO - It is at this point too unclear, if these specialized definitions
are similar to some extend, or if they differ substantially in some specific
way. Will have to spend some thought on that aspect once these definitions
have been fleshed out.
