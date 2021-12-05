
<!-- ======================================================================= -->
# Definition of hierarchy-based terms

The following will define graph-/hierarchy-based terms in the context of some
hypothetical partial setup of sets `S`.

<!-- ======================================================================= -->
## special subsets

* `SI := { s | (x superset-of s) for some (x in S) }`
* `SI` is the set of sets that have some superset in `S`
* note - those that have an "incoming" relationship
* `SO := { s | (x subset-of s) for some (x in S) }`
* `SO` is the set of sets that have some subset in `S`
* note - those that have an "outgoing" relationship

The following subsets can be defined:

* `SD := { s | (s !in SI) and (s !in SO) }`
* `SD` is the set of sets that are unrelated to every other set
* note - those that are "disconnected" sets
* `SC := { s | (s in SI) or (s in SO) } := (S \ SD)`
* `SC` is the set of sets that are related to some other set
* note - those that are "connected" with another set

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
## roots, leafs, rooted setup

A **root** is such that, except for the universal set `U`, it is no subset to
another set. As such, a root set may or may not have a subset in `S`. That is,
a root set may or may not be a source set.

* `RS := { r | (r !in SI) }`
* `RS` is the set of all root sets
* note - root sets have no superset in S

Conversely, a **leaf** is such that it is no superset to another set. As such,
a leaf set may or may not have a superset in `S`. That is, a leaf set may or
may not be a sink set.

* `LS := { l | (l !in SO) }`
* `LS` is the set of all leaf sets
* note - root sets have no subset in S

Note that a source set must have a subset, and that a sink set must have a
superset. In contrary to that, root sets and leaf sets may be disconnected.

A **rooted setup** is such that it has one and only one root. That is, the set
of root sets has one and only one root set - i.e. `(#RS == 1)` is true.

Note that the root set `r` of a rooted setup is equal to its universal set.

* `(r == U(S))` is true for a rooted setup

Note that a non-empty partial setup always has **one or more root sets**.
That is because (1) a setup that has only one set, has that set as its only
root. Also, (2) adding a new set to the setup, in such a way that it continues
to satisfy all the requirements, will (2.1) add a new root (if that new set
is disjoint to all pre-existing sets), (2.2) turn one or more root sets into
non-root sets (if these root sets are subsets to the new set), or (2.3) add
the new set as a new subset to a pre-existing root set.

<!-- ======================================================================= -->
## ancestors, descendants

An **ancestor** `a` is such that it is a superset to another set `s`.
As such, `a` may be described as **an ancestor of** `s`.

* `(a ancestor-of s) := (a superset-of s) and (a != s)`

A **descendant** `d` is such that it is a subset to another set `s`.
As such, `d` may be described as **a descendant of** `s`.

* `(d descendant-of s) := (d subset-of s) and (d != s)`

Note that a set is no ancestor/superset and no descendant/subset to itself
(i.e. no loops and no cycles). Likewise, disjoint sets are neither ancestors
nor descendants to each other.

subsets of sets

* `AS := SO := { a | (a ancestor-of s) for some (s in S) }`
* `AS` is the set of all ancestors in `S`
* `DS := SI := { d | (d descendant-of s) for some (s in S) }`
* `DS` is the set of all descendants in `S`

helper functions

* `A(s) := { a | (a ancestor-of s) for some (a in S) }`
* `A(s)` is the set of all ancestor sets of `s`
* note - all the supersets of `s` in `S`
* `D(s) := { d | (d descendant-of s) for some (d in S) }`
* `D(s)` is the set of all descendant sets of `s`
* note - all the subsets of `s` in `S`

Note that a partial setup has **no cycles**. That is because no set can be
a subset and also a superset to another set. It would need to have fewer and
also more elements than the other set. Because of that, the set of ancestors
is disjoint to the set of descendants.

* `(A(s) disjoint-to D(s))` is true for all `(s in S)`

Note that any set has more elements than any of its descendants. Likewise,
any set is guaranteed to have fewer elements than any of its ancestors.

* `(#s < #a)` for `(a in A(s))` and `(s in S)`
* `(#s > #d)` for `(d in D(s))` and `(s in S)`

Note that there is no requirement as to how many more elements an ancestor must
have in regards to any of its descendants. That is, an ancestor may have one or
more elements in addition to those of any of its descendants. Put differently,
the set difference between an ancestor and one of its descendants may contain
any number of elements.

* assumed that `(a ancestor-of d)` is true, then ..
* `(#a == (#d+n))` is true for some `(n in [1,*])`

<!-- ======================================================================= -->
## root, parent, child, leaf

The **root of** set `s` is the most significant ancestor of `s`.

* `r(s) := r` such that `#r` is maximal for `(r in A(s))`
* `(r root-of s) := (r == r(s))`

The **parent of** set `c` is the least significant ancestor of `c`.

* `p(c) := p` such that `#p` is minimal for `(p in A(c))`
* `(p parent-of c) := (p == p(c))`

Note that any set in `SO` has at least one subset in `S`. Because of that,
any set `(p in SO)` may be described as **a parent** set. Likewise, any
set `(c in SI)` that has at least one superset in `S` may be described as
**a child** set.

* `PS := AS := SO` and `CS := DS := SI`

Note that a set can have no more than one parent and no more than one root.
Furthermore, if a set has a parent, then it also has a root, both of which
may even be identical.

Note that any descendant has **a unique parent**. That is because `S` has no
overlapping sets and because no set can be a superset and also a subset to
another set (i.e. no cycles). Put differently, the non-empty set of ancestors
`A(s)` is always "a total set of sets" and as such guaranteed to have a least
and also a most significant superset.

A descendant `c` of set `p` is **a child of** `p`,
if `p` is the parent of `c`.

* `c(p) := { c | (p(c) == p) for (c in D(p)) }`
* `(c child-of p) := (c in c(p))`
* `(#c(p) >= 0)` is true

Note that any ancestor may have **any number of (disjoint) child sets**.
That is, `c(p)` is a set of pairwise disjoint subsets.

Note that one or more sets may have the same parent set. That is, the
**parent-child relationship** is in general **a 1:N relationship**.

A descendant `l` of set `p` is **a leaf of** `p`,
if `l` is no ancestor to another set.

* `l(p) := { l | (l in D(p)) and (l in LS) }`
* `(l leaf-of s) := (l in D(p))`
* `(#l(p) >= #c(p))` is true

A set that is no root has a parent and may therefore be described as
**a non-root**, or as **a child** (i.e. an upward oriented definition).

A set that is no parent has no child and may therefore be described as
**a non-parent**, or as **a leaf** (i.e. a downward oriented defintition).

<!-- ======================================================================= -->
## siblings, no child order

Two sets `s` and `t` can be described as **siblings**,
if both sets have the same parent `p`.

* for `(s,t in CS)` and `(p in PS)`
* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`

Note that siblings may differ in the amounts of elements they hold.

* `(#s != #t)` may be true for `(s sibling-of t)`
* `(#s = #t+n)` may be true for any `(n in [0,*])`

Note that, since siblings must have the same parent,
two siblings have the **exact same set of ancestors**.

* `(s sibling-of t) <-> (A(s) == A(t))`

Note that, since siblings must have the same parent, they can not be related
with each other. Because of that, two siblings are **unrelated** with each
other (under the superset-of operator). Because of that, any two sibling sets
are **disjoint** (under DI-RE).

* `(s sibling-of t) -> (s disjoint-to t)`

Note that, since siblings are unrelated with each other, any two child sets of
a parent set appear to be **equally relevant** to their parent since there is
no meaningful way to compare siblings with each other. Because of that, there
is no first child and no last child, and therefore also **no child order** in
the context of a partial setup.

<!-- ======================================================================= -->
## universal set, root sets, leaf sets

Recall that each setup `S` can be understood to be accompanied by a universal
set `U(S)`, which can be described as a superset to each set in `S`. Because
of that, `U(S)` can be referred to as the parent of each root. Based on that,
root sets can be described as siblings to each other.

* `(U parent-of r)` can be understood to be true for each `(r in RS)`
* `(s sibling-of t)` can be understood to be true for all `(s,t in RS)`

Note that leaf sets can in general not be described as siblings to each other.
That is because leaf sets have in general distinct parents.
