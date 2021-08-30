
<!-- ======================================================================= -->
# Definition of hierarchy-based terms

The following will define graph-/hierarchy-based terms in the context of
some hypothetical setup of sets `S`.

Note that the following definitions assume the **superset-of** operator as the
basis of the related-to operator. That is, a root/source set must be considered
to contain all of its subsets (i.e. is most significant in terms of the number
of elements in it).

* `(A related-to B) := (A superset-of B) or (B superset-of A)`

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
* `SC` is the set of connected sets
* note - related to some other set
* `SD := { s | (s !in SI) and (s !in SO) }`
* `SD` is the set of disconnected/isolated sets
* note - not related to any other set

In regards to the overall setup, the following subsets can be defined:

* `SRC := { s | (s !in SI) and (s in SO) }`
* `SRC` is the set of all "source" sets
* `SNK := { s | (s in SI) and (s !in SO) }`
* `SNK` is the set of all "sink" sets
* `INT := { s | (s in SI) and (s in SO) }`
* `INT` is the set of all "internal" sets

Note that a disconnected set is no element in any of these sets.

<!-- ======================================================================= -->
## roots, leafs (of S/s)

A **root set** is such that (except for the universal set `U`) it is no subset
to another set. Conversely, a **leaf set** is such that it is no superset to
another set.

* `RS := { r | (r !in SI) }`
* `RS` is the set of all root sets
* note - these have no superset in S
* `LS := { l | (l !in SO) }`
* `LS` is the set of all leaf sets
* note - these have no subset in S

A **rooted setup** is such that it has **one and only one root set**.
That is, the set of root sets contains one set only (i.e. `(#RS == 1)`).

Note that a root set may or may not be a source set. Likewise, a leaf set may
or may not be a sink set. That is because root sets and leaf sets may both be
disconnected. A disconnected set may therefore be described as a root and a
leaf set.

Note that any partial setup always has **one or more root sets**. That is
because (1) a setup that has only a single set, has that set as its only root.
Furthermore, (2) the addition of a new set to the setup, in such a way that it
still satisfies all the requirements, will (2.1) add a new root (if that new
set is disjoint to all pre-existing sets), (2.2) turn one or more root sets
into non-root sets (if these root sets are subsets to the new set), or (2.3)
add the new set as a new descendant to a pre-existing root.

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
* `D(s) := { d | (d descendant-of s) }`
* `D(s)` is the set of all descendant sets of `s`

Note that `A(s)` and `D(s)` are always disjoint.

* `(A(s) disjoint-to D(s))` is true for all `(s in S)`

Note that any set is guaranteed to have more elements than any of its
descendant sets. Likewise, any set is guaranteed to have fewer elements
than any of its ancestor sets.

* `(#s < #a)` for `(a in A(s))` and `(s in S)`
* `(#s > #d)` for `(d in D(s))` and `(s in S)`

Note however that there is no requirement as to how many more elements an
ancestor set must have in regards to any of its descendant sets. That is,
an ancestor set may have one or more elements in addition to all of its
descendant sets.

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

A descendant set `c` of set `p` is **a child set of** `p`,
if `p` is the parent set of `c`.

* `c(p) := { c | (p(c) == p) }`
* `(c child-of p) := (c in c(p))`
* `(#c(p) >= 0)` is true

A descendant set `l` of set `p` is **a leaf set of** `p`,
if `l` is no ancestor to another set.

* `l(p) := { l | (l in D(p)) and (l in LS) }`
* `(l leaf-of s) := (l in D(p))`
* `(#l(p) >= #c(p))` is true

Note that a set has either no parent at all (i.e. a root), or one and only one
parent set (i.e. a child). However, another set may still exist that has the
same set as its parent set. That is, the **parent-child relationship** is in
general **a 1:N relationship**.

A set that is no root has a parent and may as such be described as
**a non-root**, or as **a child set** (i.e. an upward oriented definition).

A set that is no parent has no child and may as such be described as
**a non-parent**, or as **a leaf set** (i.e. a downward oriented defintition).

Note that any descendant set has **a unique parent set**. That is because `S`
has no overlapping sets and because no set can be a superset and also a subset
to another set (i.e. no cycles). Put differently, the set of ancestors `A(s)`
is always "a total set of sets" and as such guaranteed to have a least and also
a most significant superset.

Note that any ancestor set may have **any number of (disjoint) child sets**.
That is, `c(p)` is a set of pairwise disjoint subsets.

<!-- ======================================================================= -->
## siblings, no child order

Two sets `s` and `t` can be described as **sibling sets**,
if and only if both sets have the same parent set `p`.

* for `(s,t in DS)` and `(p in AS)`
* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`

Note that, since siblings have the same parent set,
two siblings have the **exact same set of ancestors**.

* `(s sibling-of t) <-> (A(s) == A(t))`

Note that, since siblings have the same parent set, they can not be related
with each other. As such, two sibling sets are **unrelated** with each other
(under the superset-of operator). Because of that, two sibling sets are
required to be **disjoint** (under DI-RE).

* `(s sibling-of t) -> (s disjoint-to t)`

Note that, since sibling sets are unrelated with each other, any two child
sets of a parent set appear to be **equally relevant** to their parent set.
Because of that, there is no first child set and no last child set, and
therefore also **no child order** in the context of a setup.

<!-- ======================================================================= -->
## universal set, roots, leafs

Recall that each setup `S` can be understood to be accompanied by a universal
set `U(S)`, which is effectively a superset to each set in `S`. Because of
that, `U(S)` can be referred to as the parent set of each root set. Based on
that, root sets can be described as **siblings** to each other.

* `(U parent-of r)` is understood to be true for each `(r in RS)`
* `(s sibling-of t)` is understood to be true for all `(s,t in RS)`

Note that leaf sets can not be described as sibling sets. That is because leaf
sets have in general distinct parent sets.
