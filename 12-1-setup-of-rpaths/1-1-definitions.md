
<!-- ======================================================================= -->
# Definition of hierarchy-based terms

Note that, since the "subset-of" operator is now the basis of the "related-to"
operator, the **defintions** that are available in the context of a setup of
sets no longer apply (from a strict point of view). However, one should easily
be able to determine the meaning of a term by the "general gist" of a definition.
The following will therefore only mention the most notable definitions.

<!-- ======================================================================= -->
## ancestors, descendants (of S/s)

An **ancestor path** `a` is such that
`a` is a prefix to another path `s`.

* `(a ancestor-of s) := (a subset-of/prefix-of s) and (a != s)`

A **descendant path** `d` of another path `s` is such that
`s` is a prefix to `d`.

* `(d descendant-of s) := (d superset-of s) and (d != s)`
* alternatively - `(s subset-of/prefix-of d)`

<!-- ======================================================================= -->
## root, parent, child, leaf (of s)

The **root path of** path `s` is the least significant ancestor path of `s`.

* `r(s) := r` such that `#r` is minimal for `(r in A(s))`
* note - `(#r == 1)` is true for any root path

The **parent path of** path `s` is the most significant ancestor of path `c`.

* `p(c) := p` such that `#p` is maximal for `(p in A(c))`

A descendant path `c` of path `p` is **a child path of** `p`,
if `p` is the parent path of `c`.

* `c(p) := { c | (p(c) == p) }`

A descendant path `l` of path `p` is **a leaf path of** `p`,
if `l` is no ancestor to another path.

<!-- ======================================================================= -->
## siblings, no child order

Two paths `s` and `t` can be described as **sibling paths**,
if and only if both paths have the same parent path `p`.

* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`
