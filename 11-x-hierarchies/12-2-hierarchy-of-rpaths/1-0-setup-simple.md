
<!-- ======================================================================= -->
# A (simple) setup of rooted paths

A set of rooted paths will be referred to as **a (simple) setup** `S`,
if the following requirements are met.

* (R0) `S` is a set/family of sequences.
* (R1) `S` is expected to be non-empty.
* (R2) Each `(s in S)` must be an ordered sequence.
* (R3) Each `(s in S)` must be non-empty.
* (R4) If `(s in S)`, then so are all prefixes of `s`.

Note that each setup can be understood to be accompanied by **a universal set**
of nodes `U`, which can be described as the union of all the nodes in each
rooted path in the setup. Likewise, such a setup can be understood to be
accompanied by **a universal graph** `G`, which can be described as the union
graph of all the sequences in it, which is in general a possibly empty non-tree
graph.

Note that `S` must contain all non-empty prefixes of each path in it. Based on
that, `S` can be described as being **downward closed**. (Note - similar to a
reflexive/transitive closure - i.e. there is no element missing that could be
derived from existing ones).

* `(S(s) subset-of S)` is true for all `(s in S)` where ..
* `S(s) := { t | (t prefix-of s) and (#t > 0) }`

<!-- ======================================================================= -->
## RE-OV, by default

Recall that two non-empty sets can either be disjoint (DI), related (RE), or
both sets overlap each other (OV) - in short **DI-RE-OV**. Because of that,
and without further restriction (i.e. the default case), the relationships
between two paths in a setup is one of these relationships.

In the context of a setup of rooted paths, the related-to operator (RE) must
be understood to be defined based on the **prefix-of** operator, which can be
described as a specialization of the subset-of operator. After all, each rooted
path is an ordered sequence and therefore corresponds with a totally ordered
set of nodes. That is, the base operator in the context of a setup of rooted
paths is the subset-of operator, not the superset-of operator.

* `(s related-to t) <=> (s prefix-of t) <=> (s subset-of t)`

Since a setup of rooted paths is intended to represent a set of all the rooted
paths in a single tree, any two rooted paths in `S` must share a common prefix
and (possibly empty) disjoint suffixes. Because of that, two paths `(s,t in S)`
are either related ex-or overlap each other - i.e. the **RE-OV** case.

* `(p1 == p2)` and `(s1 disjoint-to s2)` are both true, where ..
* `s := (p1 × s1)` and `t := (p2 × s2)` and `(s,t in S)`

Note that the RE-OV case (trees) will be the focus of this discussion, whereas
the DI-RE-OV case (forests) will be considered secondary.

<!-- ======================================================================= -->
## DI-RE-OV, union of setups

When forming a union of two setups one can in general not expect that the
universal sets of both setups are disjoint. That is, two distinct setups
may in principle contain paths that share any number of nodes in any order.
(Note - the union of two paths, each of which belongs to a different setup,
may form an "X" - i.e. contains a node that has two parents and two child
nodes).

Because of that, the union of setups is in general expected to be a union of
setups that have **disjoint universal sets**. Based on that, the union of
setups can be described as **a union of pairwise disjoint setups**.

Note that, even though general operations on setups of rooted paths are not the
focus of this discussion, the union of non-disjoint setups could be performed
in order to add one or more nodes to a tree. However, care must be taken in
order for the resulting union to not break the above mentioned requirements.

Since a union is by default expected to be a union of disjoint setups, the
relationships that are allowed in the resulting union must be extended such
that rooted paths in a setup may be disjoint in addition to being related
ex-or overlapping - i.e. **a specialized DI-RE-OV case**.

Note however that such a setup must still correspond with the union of disjoint
setups. That is, the set of all valid setups is still a proper subset to the
unrestricted DI-RE-OV case.
