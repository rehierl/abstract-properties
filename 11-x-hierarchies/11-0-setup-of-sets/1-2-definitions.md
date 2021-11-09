
<!-- ======================================================================= -->
# Definition of hierarchy-based terms

The following will define graph-/hierarchy-based terms in the context of some
hypothetical partial setup `S`.

<!-- ======================================================================= -->
## special subsets

* `SI := { s | (s subset-of x) for some (x in S) }`
* `SI` is the set of sets that have a superset in `S`
* note - those that have an "incoming" relationship
* `SO := { s | (s superset-of x) for some (x in S) }`
* `SO` is the set of sets that have a subset in `S`
* note - those that have an "outgoing" relationship

Based on that, the following subsets can be defined:

* `SC := { s | (s in SI) or (s in SO) } := (S \ SD)`
* `SC` is the set of sets that are related to some other set
* note - those that are "connected" with another set
* `SD := { s | (s !in SI) and (s !in SO) }`
* `SD` is the set of sets that are unrelated to every other set
* note - those that are "disconnected" sets

In regards to the overall setup, the following subsets can be defined:

* `SRC := { s | (s !in SI) and (s in SO) }`
* `SRC` is the set of all "source" sets
* `SNK := { s | (s in SI) and (s !in SO) }`
* `SNK` is the set of all "sink" sets
* `INT := { s | (s in SI) and (s in SO) }`
* `INT` is the set of all "internal" sets

Note that a disconnected set is no element in any of these sets. After all,
a disconnected set is neither a superset nor a subset to another set.

<!-- ======================================================================= -->
## roots, leafs (of S/s)

A **root set** is such that (except for the universal set `U`) it is no subset
to another set. As such, a root set may or may not have a subset in `S`. That
is, a root set may or may not be a source set.

* `RS := { r | (r !in SI) }`
* `RS` is the set of all root sets
* note - these have no superset in S

Conversely, a **leaf set** is such that it is no superset to another set. As
such, a leaf set may or may not have a superset in `S`. That is, a leaf set
may or may not be a sink set.

* `LS := { l | (l !in SO) }`
* `LS` is the set of all leaf sets
* note - these have no subset in S

Note that a source set must have a subset, and that a sink set must have a
superset. In contrary to that, root sets and leaf sets may be disconnected.

A **rooted setup** is such that it has one and only one root set. That is,
the set of root sets contains one root set only (i.e. `(#RS == 1)`).

Note that the root set `r` of a rooted setup is equal to its universal set.
Because of that, all other sets in a rooted setup are subsets to the root set.

* `(r == U(S))` is true for a rooted setup

Note that a partial setup always has **one or more root sets**. That is because
(1) a setup that has only a single set, has that set as its only root. Also,
(2) the addition of a new set to the setup, in such a way that it continues to
satisfy all the requirements of a partial setup, will (2.1) add a new root (if
that new set is disjoint to all pre-existing sets), (2.2) turn one or more root
sets into non-root sets (if these root sets are subsets to the new set), or
(2.3) add the new set as a new subset to a pre-existing root set.

<!-- ======================================================================= -->
## ancestors, descendants (of S/s)

An **ancestor set** `a` is such that it is a superset to another set `s`.
As such, `a` may be described as **an ancestor set of** `s`.

* `(a ancestor-of s) := (a superset-of s) and (a != s)`

A **descendant set** `d` is such that it is a subset to another set `s`.
As such, `d` may be described as **a descendant set of** `s`.

* `(d descendant-of s) := (d subset-of s) and (d != s)`

Note that a set is no ancestor set and no descendant set to itself (i.e.
no loops and no cycles). Likewise, disjoint sets are neither ancestors
nor descendants to each other.

subsets of sets

* `AS := { a | (a ancestor-of s) for some (s in S) }`
* `AS` is the set of all ancestor sets in `S`
* `DS := { d | (d descendant-of s) for some (s in S) }`
* `DS` is the set of all descendant sets in `S`

helper functions

* `A(s) := { a | (a ancestor-of s) }`
* `A(s)` is the set of all ancestor sets of `s`
* note - all the supersets of `s` in `S`
* `D(s) := { d | (d descendant-of s) }`
* `D(s)` is the set of all descendant sets of `s`
* note - all the subsets of `s` in `S`

Note that a partial setup has **no cycles**. That is because no set can be a
subset and also a superset to another set. It would need to have fewer and also
more elements than the other set. Because of that, the set of ancestor and
descendant sets are disjoint.

* `(A(s) disjoint-to D(s))` is true for all `(s in S)`

Note that any set has more elements than any of its descendant sets. Likewise,
any set is guaranteed to have fewer elements than any of its ancestor sets.

* `(#s < #a)` for `(a in A(s))` and `(s in S)`
* `(#s > #d)` for `(d in D(s))` and `(s in S)`

Note that there is no requirement as to how many more elements an ancestor set
must have in regards to any of its descendant sets. That is, an ancestor set
may have one or more elements in addition to those of any of its descendant
sets. Put differently, the set difference between an ancestor set and one of
its descendant sets may in general have any number of elements.

* assumed that `(a ancestor-of d)` is true, then ..
* `(#a == (#d+n))` is true for some `(n in [1,*])`

<!-- ======================================================================= -->
## root, parent, child, leaf (of s)

The **root set of** set `s` is the most significant ancestor of `s`.

* `r(s) := r` such that `#r` is maximal for `(r in A(s))`
* `(r root-of s) := (r == r(s))`

The **parent set of** set `c` is the least significant ancestor of `c`.

* `p(c) := p` such that `#p` is minimal for `(p in A(c))`
* `(p parent-of c) := (p == p(c))`

Note that a set can have noe more than one parent set and no more than one root
set. Furthermore, if a set has a parent set, then it also has a root set, both
of which may be identical.

Note that any descendant set has **a unique parent set**. That is because `S`
has no overlapping sets and because no set can be a superset and also a subset
to another set (i.e. no cycles). Put differently, the non-empty set of ancestors
`A(s)` is always "a total set of sets" and as such guaranteed to have a least
and also a most significant superset.

A descendant set `c` of set `p` is **a child set of** `p`,
if `p` is the parent set of `c`.

* `c(p) := { c | (p(c) == p) }`
* `(c child-of p) := (c in c(p))`
* `(#c(p) >= 0)` is true

Note that any ancestor set may have **any number of (disjoint) child sets**.
That is, `c(p)` is a set of pairwise disjoint subsets.

Note that one or more sets may have the same parent set. That is, the
**parent-child relationship** is in general **a 1:N relationship**.

A descendant set `l` of set `p` is **a leaf set of** `p`,
if `l` is no ancestor to another set.

* `l(p) := { l | (l in D(p)) and (l in LS) }`
* `(l leaf-of s) := (l in D(p))`
* `(#l(p) >= #c(p))` is true

A set that is no root has a parent and may therefore be described as
**a non-root**, or as **a child set** (i.e. an upward oriented definition).

A set that is no parent has no child and may therefore be described as
**a non-parent**, or as **a leaf set** (i.e. a downward oriented defintition).

<!-- ======================================================================= -->
## siblings, no child order

Two sets `s` and `t` can be described as **sibling sets**,
if and only if both sets have the same parent set `p`.

* for `(s,t in DS)` and `(p in AS)`
* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`

Note that sibling sets may in principle have different amounts of elements.
That is, there is no relationship between the sizes of sibling sets.

* `(#s != #t)` may be true for `(s sibling-of t)`

Note that, since siblings have the same parent set,
two siblings have the **exact same set of ancestors**.

* `(s sibling-of t) <-> (A(s) == A(t))`

Note that, since siblings have the same parent set, they can not be related
with each other. As such, two sibling sets are **unrelated** with each other
(under the superset-of operator). Because of that, any two sibling sets are
**disjoint** (under DI-RE).

* `(s sibling-of t) -> (s disjoint-to t)`

Note that, since sibling sets are unrelated with each other, any two child
sets of a parent set appear to be **equally relevant** to their parent set.
Because of that, there is no first child set and no last child set, and
therefore also **no child order** in the context of a partial setup.

<!-- ======================================================================= -->
## universal set, roots, leafs

Recall that each setup `S` can be understood to be accompanied by a universal
set `U(S)`, which can be described as a superset to each set in `S`. Because
of that, `U(S)` can be referred to as the parent set of each root set. Based
on that, root sets can be described as siblings to each other.

* `(U parent-of r)` is understood to be true for each `(r in RS)`
* `(s sibling-of t)` is understood to be true for all `(s,t in RS)`

Note that leaf sets can not be described as sibling sets. That is because leaf
sets have in general distinct parent sets.
