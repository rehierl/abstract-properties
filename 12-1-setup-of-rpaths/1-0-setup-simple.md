
<!-- ======================================================================= -->
# A (simple) setup of rooted paths (rpaths)

A set of rooted paths will be referred to as **a (simple) setup of rpaths**
`S`, if and only if the following requirements are met.

* (R0) `S` is expected to be non-empty.
* (R1) Each `(s in S)` is required to be an ordered sequence.
* (R2) If `(s in S)`, then so are all prefixes of `s`.
* (R3) `(#s > 0)` - is required to be true for all `(s in S)`

Note that the paths in such a setup are understood correspond with the rooted
paths of a single tree or a forest of trees. Because of that, `S` is expected
to be a set of **ordered sequences of nodes**. That is, no path in it contains
a node more than once (i.e. acyclic).

Note that `S` must be **complete** (aka. **downward total**) insofar, as it
must contain all non-empty prefixes of every path in it. That is, the following
is required to be true.

* `(S(s) subset-of S)` where ..
* `S(s) := { t | (t prefix-of s) and (#t > 0) }` for `(s in S)`

Note that each setup can be understood to be accompanied by **a universal set**
`U`, which can be described as the union of all the elements in each rooted
path `S`.

* `(E(s) subset-of U(S))` for all `(s in S)`

<!-- ======================================================================= -->
## no (further) variations

Recall that each ordered sequence corresponds with a totally ordered set of
elements. Because of that, a setup of rooted paths can be described as a set
of totally ordered sets. Consequently, a setup of rooted paths can be treated
as a specialized setup of sets - i.e. a particular variation of the general
case (a setup of sets).

Note that two non-empty sets can either be disjoint (DI), related (RE), or
both sets overlap each other (OV) - in short **DI ex-or RE ex-or OV**. Hence,
without further restriction, the relationships between two rooted paths in a
setup is one of these relationships (i.e. the default case).

In the context of a setup of rooted paths, the **related-to** operator must
be understood to be based on the **prefix-of** operator, which is, since
rooted paths are ordered sequences, based on the **subset-of** operator.
That is, the default operator in the context of a setup of rooted paths is
thus the subset-of operator, not the superset-of operator.

* `(s related-to t)` <=> `(s prefix-of t)` <=> `(s subset-of t)`

Since a setup of rooted paths is based on the rooted paths of a single node
tree, including any possible prefix of such a path, any two paths in `S`
share a common prefix and (possibly empty) disjoint suffixes. Because of that,
two paths `(s,t in S)` are either related ex-or overlap each other - i.e. the
**RE ex-or OV** variation.

* `(p1 == p2)` and `(s1 disjoint-to s2)`
* for `s := (p1 × s1)` and `t := (p2 × s2)` and `(s,t in S)`

When forming a union of setups each of which is supposed to correspond with
a single tree, one can in general not expect that the universal sets of two
setups are disjoint. That is, two distinct setups may in principle contain
paths that share one or more nodes. Because of that, and unless specified
otherwise, the union of setups must be expected to be a union of setups that
have **disjoint universal sets**. With that in mind, the union of setups can
be described as **a union of disjoint setups**.

* `(S1 + S2) := { s | (s in S1) or (s in S2) }`
* if and only if `(U(S1) disjoint-to U(S2))`

Note that, even though general operations on setups of rooted paths are not the
focus of this discussion, the union of non-disjoint setups could be performed
in order to add one or more nodes to a tree. However, care must be taken in
order for the resulting union to not break the requirements of a setup of rooted
paths (hint - two rooted paths that form an "X").

Since a union is expected to be a union of disjoint setups, the relationships
between the rooted paths in the resulting union must be extended such that
rooted paths in a setup may be disjoint in addition to being related ex-or
overlapping - i.e. an "unrestricted" **DI ex-or RE ex-or OV** variation.

Note however that such a setup must still correspond with the disjoint union
of proper setups. That is, the set of all valid setups remains to be a proper
subset to the completely unrestricted case.

For obvious reasons, the RE-OV case (trees) will be the focus of this
discussion, whereas the DI-RE-OV case (forests) will be considered secondary.
