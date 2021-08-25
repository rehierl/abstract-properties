
<!-- ======================================================================= -->
# (Simple) setups of sets

A set of sets will be referred to as **a (simple) setup of sets** `S`,
if and only if no set in it is empty.

* (R0) `S` is in general expected to be non-empty
* (R1) `(#s > 0)` - is required to be true for all `(s in S)`

Note that, since a setup is not defined as a multiset, each set in `S` is
distinct to every other set in it. Furthermore, each set in a setup may in
principle hold elements of any kind (i.e. heterogenous). However, depending
on a given context, a setup is in general required to hold elements of a
certain kind (e.g. primitive numeric values only, i.e. **homogenous**).

Note that set-based operators can be used in the context of a simple setup.
This includes, but is not limited to the following operators ..

* `(T equal-to S) := (T == S)`
* `(T sub-setup-of S) := (T subset-of S)`
* `(s in S)` := true, iff set `s` is an element in `S`

Note that each setup can be understood to be accompanied by a **universal set**
`U`, which is referred to as the union of all sets in `S`.

* `U, U(S)` is the universal set of setup `S`
* `U := { x | (x in s) for some (s in S) }`
* `(S subset-of P(U))` - `S` is a subset to the powerset of `U`

Note that the expression `(e in S)` may be used to test if `e` is an element
in one or more sets of `S`. Since setups are in general such that `U` is a
set of primitive values, one can in general distinguish both cases in a given
context. After all, `e` must then either be a primitive value ex-or a set of
such values.

Note that a setup was formerly defined as a tuple `S(P,U)` such that `P` is
the set of sets, and `U` the universal set of elements. This more complete
definition however seemed to make explanations needlessly verbose and thus
more difficult to understand.

<!-- ======================================================================= -->
## options for refinment

Recall that two non-empty sets can either be disjoint (DI), related (RE), or
both sets overlap each other (OV) - in short **DI ex-or RE ex-or OV**.

Setups will be used to define partial orders based on the relationships between
two non-empty sets in it. And since partial orders are defined to have directed
edges, an order operator must be available that has a notion of **orientation**.

For obvious reasons, neither "disjoint-to" (DI) nor "overlaps-with" (OV) have
such a notion of orientation. This only leaves the "related-to" (RE) operator
as an option. Even though "related-to" is itself also without orientation, one
can recall that it is defined based upon the **superset-of** operator (default),
or alternatively the subset-of operator.

* `(A related-to B) := (A superset-of B) or (B superset-of A)`

An option for refinement is therefore to choose to redefine "related-to" (RE)
such that it is based upon a different operator such that it still implicitly
supports a notion of orientation.

* `(A related-to B) := (A prefix-of B) or (B prefix-of A)`

Since an order operator will be based upon the "related-to" operator, one may
still choose to restrict the types of relationships two sets in such a setup
may have. That is a setup may be defined such that sets are not allowed to
overlap each other (**DI ex-or RE**). Likewise, a setup may be defined such
that no disjoint sets are allowed (**RE ex-or OV**). And finally, one may
even completely disallow both of these alternatives such that any two sets
are required to related (**RE only** - i.e. total) with each other.

Note that the "unrelated" (i.e. not related) aspect reflects the case that
there is no edge/path between two elements. Further restricting the available
alternative relationships to only-disjoint or only-overlapping is therefore
beneficial. That is because knowing that two elements are unrelated will then
allow to conclude what "kind of unrelatedness" resulted in both elements being
disconnected from each other.

<!-- ======================================================================= -->
## remarks

Since the empty set has characteristics that are unique to it, and "in conflict"
with those of non-empty sets, **the empty set is as an element not allowed**.

Note that the "in conflict" description refers to the following aspect:
"The empty set is disjoint and related to every other set, including itself",
compared to "Each non-empty set is coupled with and related to itself". Because
of that, and if the empty set were allowed, one could not simply conclude:
"If two sets are disjoint, then both sets are related." - One would therefore
always have to distinguish between empty and non-empty sets.

Note that, except for the exclusion of the empty set, a simple setup is in
essence the vertex set of a **containment/inclusion order**.
