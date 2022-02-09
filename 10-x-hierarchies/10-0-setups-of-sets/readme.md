
# hierarchies / setups of sets

This chapter begins with a recap of basic set-based definitions such as the
definition of the **superset-of** operator, which is by default used to define
the more generic related-to operator.

* `(A superset-of B) := (b in A) for all (b in B)`
* `(A related-to B) := (A superset-of B) or (B superset-of A)`

Note that the **related-to** operator is considered critical to a setup since
it allows to test if two sets in a setup/hierarchy are considered to be related
with each other in some way. This relationship can be described to indicate the
**existence of an edge** between the corresponding vertices in the resulting
order relation.

Note that the subset-of operator is considered to be **oriented** since it
allows to determine which set is super-ordinate (i.e. more significant) or
sub-ordinate (i.e. less significant) to the other. In contrary to that, the
related-to operator does not allow to distinguish both input sets in such
a way.

From the types of relationships that are possible between any two distinct
sets in a setup one can state that any two such sets are either disjoint (DI),
related (RE), ex-or both sets overlap (OV) each other - in short **DI-RE-OV**.
One core aspect when defining the characteristics of a setup therefore is to
state which types of relationships are allowed, and which ones are not.

For example, **a partial setup** is (by default) such that any two sets must
either be disjoint ex-or related with each other - the **DI-RE** case. In
contrary to that, **a total setup** is such that any two sets must be related
with each other - the **RE-only** case.

Note that **tree-based terms** such as "ancestor" (i.e. a superset), "parent"
(i.e. the least significant superset), "root" (i.e. the most significant
superset) and descendant" (i.e. a subset) can be defined based on the
superset-of operator. Likewise, a set of all ancestor sets `A(s)` and a set
of all descendant sets `D(s)` can be defined in regards to some set `s` in
the corresponding setup.

* `A(s) := { t | (t superset-of s) }` and `A*(s) := A(s) + {s}`
* `D(s) := { t | (s superset-of t) }` and `D*(s) := D(s) + {s}`

Note that, in a partial setup, `A(s)` can in general be described as
**a total subsetup** which may or may not have a root set, and which may or
may not have one and only one leaf set. In contrary to that, `D(s)` can in
general be described as **a partial subsetup** which may have any number of
root sets and also any number of leaf sets. Despite their differences, `A(s)`
and also `D(s)` can both be described as **downward-total setups**.

Note that, including the input sets `s` in `A*(s)` and `D*(s)`, guarantees
that both sets always have one and only one root set. However, even though
`A*(s)` is then also guaranteed to have set `s` as its one and only one leaf
set, `D*(s)` can still only be described to have one or more leaf sets.
