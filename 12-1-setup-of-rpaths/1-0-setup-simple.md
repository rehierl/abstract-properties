
<!-- ======================================================================= -->
# A (simple) setup of rooted paths (rpaths)

A set of rooted paths will be referred to as **a (simple) setup of rpaths**
`S`, if and only if the following requirements are met.

* (R0) `S` is expected to be non-empty.
* (R1) Each `(s in S)` is required to be an ordered sequence.
* (R2) `(#s > 0)` is required to be true for all `(s in S)`.
* (R3) If `(s in S)`, then so are all prefixes of `s`.

Note that the paths in such a setup are understood correspond with the rooted
paths of a single tree, or with all the rooted paths in a forest of trees.
Because of that, `S` is expected to be a set of **ordered sequences of nodes**.
That is, no path in it contains a node more than once (i.e. acyclic).

Note that each setup can be understood to be accompanied by **a universal set**
`U`, which can be described as the union of all the elements in each sequence.
Because of that, `S` can be described as a set in the powerset `P(×U)` over
the set of all possible sequences over `U`.

* `(S in P(×U))` is true
* `(E(s) subset-of U(S))` is true for each `(s in S)`

Note that `S` must contain all non-empty prefixes of every path in it. Based
on that, `S` can be described as being **downward closed**. (hint - similar
to the reflexive/transitive closure - i.e. there is no element missing that
can be derived from existing ones).

* `(S(s) subset-of S)` is true for all `(s in S)` where ..
* `S(s) := { t | (t prefix-of s) and (#t > 0) }`

<!-- ======================================================================= -->
## RE-OV, by default

Recall that each ordered sequence corresponds with a totally ordered set of
elements. Because of that, a setup of rooted paths can be described as a set
of totally ordered sets. Consequently, a setup of rooted paths can be treated
as a specialized setup of sets - i.e. a particular variation of the general
case (a setup of sets).

Recall that two non-empty sets can either be disjoint (DI), related (RE), or
both sets overlap each other (OV) - in short **DI-RE-OV**. Because of that,
and without further restriction (i.e. the default case), the relationships
between two rooted paths in a setup is one of these relationships.

In the context of a setup of rooted paths, the **related-to** operator (RE)
must be understood to be defined based on the **prefix-of** operator, which
can be described as a specialization of the **subset-of** operator. After all,
each ordered sequence corresponds with a totally ordered set. That is, the
default operator in the context of a setup of rooted paths is the subset-of
operator, not the superset-of operator.

* `(s related-to t) <=> (s prefix-of t) <=> (s subset-of t)`

Since a setup of rooted paths can be understood to represent a set of all the
rooted paths in a single tree, any two paths in `S` share a common prefix and
(possibly empty) disjoint suffixes. Because of that, two paths `(s,t in S)`
are either related ex-or overlap each other - i.e. the **RE-OV** variation.

* `(p1 == p2)` and `(s1 disjoint-to s2)` are both true, where ..
* `s := (p1 × s1)` and `t := (p2 × s2)` and `(s,t in S)`

Note that the RE-OV case (trees) will be the focus of this discussion,
whereas the DI-RE-OV case, as described next, will be considered secondary.

<!-- ======================================================================= -->
## DI-RE-OV, union of setups

When forming a union of two such setups one can in general not expect that the
universal sets of both setups are disjoint. That is, two distinct setups may
in principle contain paths that share any number of nodes in any order. (hint
- the union of two paths, each of which belongs to a different setup, may form
an "X").

Because of that, the union of setups is in general expected to be a union of
setups that have **disjoint universal sets**. Based on that expectation, the
union of setups can be described as **a union of disjoint setups**.

* `(S1 + S2) := { s | (s in S1) or (s in S2) }`
* if and only if `(U(S1) disjoint-to U(S2))`

Note that, even though general operations on setups of rooted paths are not
the focus of this discussion, the union of non-disjoint setups could be
performed in order to add one or more nodes to a tree. However, care must
be taken in order for the resulting union to not break the requirements of
a setup of rooted paths.

Since a union is by default expected to be a union of disjoint setups, the
relationships that are allowed in the resulting union must be extended such
that rooted paths in a setup may be disjoint in addition to being related
ex-or overlapping - i.e. **a specialized DI-RE-OV case**.

Note however that such a setup must still correspond with the disjoint union
of proper setups. That is, the set of all valid setups remains to be a proper
subset to the completely unrestricted case.
