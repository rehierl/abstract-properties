
<!-- ======================================================================= -->
# (Simple) setups of sets

A set of sets will be referred to as **a (simple) setup** `S`,
if the following requirements are met.

* (R0) `S` is a set/family of sets.
* (R1) `S` is expected to be non-empty.
* (R2) Each `(s in S)` must be a simple set.
* (R3) Each `(s in S)` must be non-empty.

Note that `S` is itself expected, but not required to be non-empty.
That is, similar to an empty forest of trees, `S` may be empty.

Note that, since a setup is not defined as a multiset, each set in `S` is
distinct to every other set in it. Furthermore, each set in a setup may in
principle hold elements of any kind (i.e. heterogenous sets). Despite that,
a setup is in general expected to hold elements of a certain kind (e.g. only
primitive numeric values, i.e. **homogenous** sets).

Note that set-based operators can be used in the context of a simple setup.
This includes, but is not limited to the following operators.

* `(T equal-to S)`, `(T subset-of S)`, `(s in S)`, ...

Note that each setup can be understood to be accompanied by **a universal set**
of elements `U`, which can be described as the union of the all sets in `S`.
Based on that, `S` can be described as a subset to the powerset of `U`.

* `(S subset-of P(U))` is true
* `U(S) := { x | (x in s) for some (s in S) }`

<!-- ======================================================================= -->
## variations

Recall that two non-empty sets can either be disjoint (DI), related (RE),
or both sets overlap each other (OV) - in short **DI-RE-OV**.

Setups will be used to define partial orders (i.e. containment orders) based
on the relationships between two sets in it. And since partial orders are
defined to have directed edges, an order operator must be used that does
support a notion of **orientation**.

As mentioned before, neither "disjoint-to" (DI) nor "overlaps" (OV) support
such a notion. This only leaves the "related-to" (RE) operator as an option.
Even though "related-to" is itself also without orientation, one must recall
that "related-to" is by default defined based on the **superset-of** operator,
which does support a sense of orientation.

* `(A related-to B) := (A superset-of B) or (B superset-of A)`

A possible variation is therefore to redefine the "related-to" operator such
that it is based on a different operator.

* `(A related-to B) := (A subset-of B) or (B subset-of A)`
* `(A related-to B) := (A prefix-of B) or (B prefix-of A)`

Since the order operator of a to-be-defined ordered set will be defined based
on the "related-to" operator, one may also choose to restrict the types of
relationships two sets in such a setup may have. That is, a setup may be defined
such that sets are not allowed to overlap each other (**DI-RE**). Likewise, a
setup may be defined such that no disjoint sets are allowed (**RE-OV**). And
finally, one may even completely disallow both of these alternatives such that
any two sets are required to be related (**RE only**).

Note that the alternative "unrelated" relationship reflects the case that
there is no edge/path between two elements. Further restricting the available
alternative relationships to only-disjoint or only-overlapping is beneficial.
That is because knowing that two elements are unrelated will then allow to
conclude why both elements are disconnected from one another - i.e. "both are
disjoint", or "both overlap each other".

<!-- ======================================================================= -->
## remarks

Since the empty set has characteristics that are unique to it, and "in conflict"
with those of non-empty sets, **the empty set is as an element not allowed**.

Note that the "in conflict" description refers to the following aspect:
"The empty set is disjoint and related to any set, including itself".
Because of that, and if the empty set were allowed, one could not conclude:
"If two sets are disjoint, then both are related." - One would therefore
always have to distinguish between empty and non-empty sets.

Note that a simple setup will in essence be used as the vertex set of an
ordered set (i.e. a **containment/inclusion order**). Because of that, and
if the kind of relatedness (i.e. superset-of, prefix-of, ...) is known, one
can easily form an actual order relation from any given setup of sets.
