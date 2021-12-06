
<!-- ======================================================================= -->
# setups of rooted paths

Recall that each rooted path is an ordered sequence of nodes. Because of that,
it is possible to either focus on the path graph of a rooted path, or on its
set of. Also, any rooted path can be described as a string of distinct nodes.

<!-- ======================================================================= -->
## a partial setup of rpaths

Assuming the **prefix-of** operator as the basis of the related-to operator,
a set of rooted paths may be referred to as **a partial setup**, if the
following requirements are met.

* (R0) `S` is a simple setup of strings.
* (R1) The rooted paths in `S` are expected to
       be related with, or to overlap each other.
* (R2) If `(s in S)`, then so are all non-empty prefixes of `s`.

Note that, since the elements in such a setup are rooted paths and as such
ordered sequences of nodes, the prefix-of operator can be described as a
specialization of the **subset-of** operator.

* `(s related-to t) := (s prefix-of t) or (t prefix-of s)`
* `(s related-to t) <=> (s prefix-of t) <=> (s subset-of t)`

Note that, due to requirement R1, any two rooted paths are expected to be
related (i.e. one is a prefix of the other) ex-or to overlap each other as
described below (i.e. the **RE-OV** case). However, in order to allow for a
partial setup to correspond with a forest of trees, rooted paths must be
allowed to be disjoint (i.e. the **DI-RE-OV** case). That is, the disjoint
case (DI) is only allowed in the context of rooted paths that belong to
distinct trees.

Note that this is different to a partial setup of scopes. That is because such
setups only need two types of relationships (DI-RE) in order to support a forest
of trees. In contrary to that, a setup of rooted paths must allow three types
of relationships (DI-RE-OV) to support forests of trees.

Recall that a simple setup of strings must be **well formed**. Because of that,
if two paths have one or more nodes in common, then the intersection between
both paths must be a prefix to one path.

<!-- ======================================================================= -->
## remarks

Note that, since the related-to operator is defined based on the prefix-of
operator, two coupled paths **must have the same prefix**. That is because a
non-prefix substring does not satisfy the disjoint case (DI, since both share
one or more nodes), not the related case (RE, none is a prefix of the other),
and also not the overlaps case (OV, one is still a substring to the other).

* `(s coupled-with t) <-> (s[1] == t[1])` must be true for `(s,t in S)`

Note that, due to requirement R2, a partial setup of rooted paths may be
described as being **downward-closed** in the sense that there is no element
missing that could be derived from any pre-existing path. (Note - "closed"
in the sense of a "transitive closure").

* `(S(s) subset-of S)` is true for all `(s in S)` where ..
* `S(s) := { t | (t prefix-of s) and (#t > 0) }`

Note that, since any setup of rooted paths is required to be downward-closed,
any path in a setup of rooted paths has its last element as its one and only
characteristic element **CE**.

Note that, since two coupled paths in a setup of rooted paths must have equal
first nodes, two overlapping paths in such a setup must share a non-empty
prefix and must also differ in non-empty disjoint suffixes.

* if `(s overlaps t)` is true for `(s,t in S)`, then also ..
* `s := (p × s1)`, `t := (p × s2)`, `(p in S)` and `(s1 disjoint-to s2)`

Note that the intersection between any two paths in `S` is always equal to a
path that setup. However, the intersection may or may not also be equal to one
of the two paths.

Note that the union of two paths is either equal to one of the two paths (i.e.
both are related), or a union of paths that overlap each other.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that hierarchy-based terms can be defined.

* root path, rooted setup
* ancestor path, descendant path
* no cycles, (A(s) disjoint-to D(s))
* root path of, parent path of
* child path of, sibling paths

Note that, since the prefix-of operator is the basis of the related-to operator,
ancestors hold **fewer nodes** than any of their descendants. As a matter of
consequence, root paths are rooted paths of one node only. Despite that,
ancestors are still considered **more significant** than all of their
descendants.

Note that each root in a setup of rooted paths can be described as a child to
the empty path `()`. That is, the empty path can be described as a theoretical
super-root.

Note that, `A(s)` is a total subsetup of rooted paths. As such, a partial setup
can be described as being **downward-total**. Because of that, each rooted path
in such a setup has a unique rooted path (of rooted paths).

Note that the amount of rooted paths in `A(s)` is not arbitrary. After all, any
prefix of a path must also be a path in the corresponding setup (R2). In other
words, a setup of rooted paths must contain all `(#s-1)` proper prefixes of
each path `(s in S)` in the setup.

Note that rooted paths, which are **siblings** to each other, have the same
length, the same prefix, and only differ in their very last nodes. Because of
that, siblings are guaranteed to hold only one more node in addition to their
parent.

<!-- ======================================================================= -->
## a total setup of rpaths

A set of rooted paths `S` will be referred to as **a total setup**,
if the following requirements are met.

* (R0) `S` is a partial setup of rooted paths.
* (R1) Any two paths are related with each other.

Note that a total setup does not allow pairs of disjoint or overlapping paths.
Because of that, any parent has **one and only one child**, which is why any
total setup has **one root and one leaf only** - i.e. a total setup of rooted
paths is **downward- and upward-total**.

<!-- ======================================================================= -->
## extended definitions

Note that the extended definitions of setups of trees
can be defined in a similar fashion.

* induced subsetups ..
* `S[r] := { s | (r prefix-of s) or (s == r) }`
* extended sets of ancestors and descendants ..
* `A*(s) := A(s) + {s}` and `D*(s) := D(s) + {s}`
* `( #(A*(s)) == #s )` is true
* paths of rooted paths ..
* `level(s) := #rp(s)`

Note that an induced subsetup still **grows with its orientation**, not against
it. That is because the subsetup grows with the orientation of the prefix-of
relationship.

Note that, as before, `A(s)` is always **a total subsetup**, whereas `D(s)`
is in general only **a partial subsetup**. That is, the overall setup must
itself be total for `D(s)` to always be a total subsetup.

<!-- ======================================================================= -->
## howto distinguish the cases

Assumed that `S` is a valid partial setup of rooted paths, then ..

In order to determine if two paths `(s,t in S)` in `S` are **disjoint**,
one only needs to test if both paths have the same first node.

* `(s disjoint-to t) <-> (s[1] != t[1])`

In order to determine if two coupled paths in `S` are **related** with each
other, one only needs to determine if the last node of the shorter path is
a node in the other path.

* `(s related-to t) <-> (s[1] == t[1]) and (s[i] == t[i])`
* for `i := min(#s,#t)`

Furthermore, if two related paths in `S` are related, then one can determine
the ancestor and the descendant by simply comparing the lengths of both paths.
That is because the shorter path is the ancestor to the other path.

* `(s ancestor-of t) <-> (s related-to t) and (#s < #t)`

If that is not the case, then both paths **overlap** each other.

* `(s overlaps t) <-> (s[1] == t[1]) and (s[i] != t[i])`

<!-- ======================================================================= -->
## DI-RE-OV, union of setups

When forming a union of two setups, one can in general not guarantee that the
universal sets of both setups are disjoint. That is, two distinct setups may
contain paths that share any number of nodes in any order. (Note - the union
of two paths, each of which belongs to a different setup, may form an "X" -
i.e. contains a node that has two parents and two child nodes).

Note that, even though general operations on setups of rooted paths are not
the focus of this discussion, the union of non-disjoint setups could be used
in order to add one or more nodes to a tree. However, care must be taken in
order for the resulting union to not break the requirements of such a setup.
