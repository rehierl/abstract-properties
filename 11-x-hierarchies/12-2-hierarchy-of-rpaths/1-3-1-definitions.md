
<!-- ======================================================================= -->
# Definition of hierarchy-based terms

The following will define graph-/hierarchy-based terms in the context of some
hypothetical setup of rooted paths `S`.

Note that, from a strict point of view, and since the **subset-of** operator
is now the basis of the "related-to" operator, the defintions made in the
context of setups of sets no longer apply. Despite that, the "general gist"
of these definitions does not change. The following will therefore focus on
**the most notable definitions**.

* `(A related-to B) := (A subset-of B) or (B subset-of A)`

<!-- ======================================================================= -->
## special subsets

* `SI := { s | (s superset-of x) for some (x in S) }`
* `SI` is the set of paths that are a prefix to some path in `S`
* note - those that have an "incoming" relationship
* `SO := { s | (s subset-of x) for some (x in S) }`
* `SO` is the set of paths that have a prefix in `S`
* note - those that have an "outgoing" relationship

Note that, except for these two modified definitions, the defintitions
of the subsets `SC`, `SD`, `SRC`, `SNK` and `INT` remain the same.

<!-- ======================================================================= -->
## roots, leafs (of S/s)

* `RS := { r | (r !in SI) }`
* `RS` is the set of all roots
* note - these have no prefix in `S`
* note - `(#r == 1)` for each `(r in RS)`
* `LS := { l | (l !in SO) }`
* `LS` is the set of all leaf sets
* note - these are no prefix to another path

A **rooted setup** is such that it has **one and only one root**.
That is, the set of root sets contains one set only (i.e. `(#RS == 1)`).

<!-- ======================================================================= -->
## ancestors, descendants (of S/s)

An **ancestor path** `a` is such that
`a` is a prefix to another path `s`.

* `(a ancestor-of s) := (a prefix-of s) and (a != s)`
* note - `(#a < #s)` is true

A **descendant path** `d` of another path `s` is such that
`s` is a prefix to `d`.

* `(d descendant-of s) := (s prefix-of d) and (d != s)`
* note - `(#s < #d)` is true

As before, the set of all ancestors `AS` and the set of all descendants `DS`,
and base on that the set of ancestors `A(s)` and the set of descendants `D(s)`
of path `s` can be defined.

Note that, in contrary to before, the amount of elements an ancestor has in
addition to the elements of one of its descendants is not arbitrary. That is
because a setup of rooted paths contains `#s` sequences for each `(s in S)`.

<!-- ======================================================================= -->
## root, parent, child, leaf (of s)

The **root of** path `s` is the least significant ancestor of `s`.

* `r(s) := r` such that `#r` is minimal for `(r in A(s))`
* note - `(#r == 1)` is true for any such root

The **parent of** path `s` is the most significant ancestor of `c`.

* `p(c) := p` such that `#p` is maximal for `(p in A(c))`
* note - `(#p == #c-1)` is true for any parent

A descendant `c` of path `p` is **a child of** `p`,
if `p` is the parent of `c`.

* `c(p) := { c | (p(c) == p) }`

A descendant `l` of path `p` is **a leaf of** `p`,
if `l` is no ancestor to another path.

* `l(p) := { l | (l in D(p)) and (l in LS) }`

<!-- ======================================================================= -->
## siblings, no child order

Two paths `s` and `t` can be described as **siblings**,
if and only if both paths have the same parent path `p`.

* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`

As before, two siblings have the **exact same set of ancestors**.

* `(s sibling-of t) <-> (A(s) == A(t))`

As before, since siblings have the same parent, they can not be related
with each other. That is, none is a prefix to the other. Because of that,
two siblings a required to **overlap** each other (under RE-OV).

* `(s sibling-of t) -> (s overlaps t)`

As before, since siblings are unrelated with each other, any two children
of a rooted path appear to be **equally relevant** to their parent. Because
of that, there is no first child and no last child, and therefore also
**no child order** in the context of a setup.

<!-- ======================================================================= -->
## universal set, roots, leafs

Recall that each setup `S` can be understood to be accompanied by a universal
graph `G(S)`, which is effectively a supergraph to each path in `S`.

In contrary to a setup of sets, each root in a setup of rooted paths can be
described as a child to the empty path `()`. That is, the empty path can be
understood as a theoretical super-root.

Furthermore, and with the extended definition of "prefix" in mind, each leaf
in `S` can be described as a prefix to the universal graph `G(S)`. Because of
that, the universal set can be described as a "theoretical" super-leaf.
