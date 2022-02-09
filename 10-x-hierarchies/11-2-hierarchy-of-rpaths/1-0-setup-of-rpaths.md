
<!-- ======================================================================= -->
# setups of rooted paths

Recall that each rooted path is an ordered sequence of nodes. Because of that,
it is possible to either focus on the path graph of a rooted path, or on its
set of nodes.

<!-- ======================================================================= -->
## a partial setup of rpaths

A set of rooted paths `S` will be referred to as **a partial setup**,
if the following requirements are met.

* (R0) `S` is a simple setup of strings.
* (R1) A descendant is a prefix to its ancestor.
* (R2) The rooted paths in `S` are expected to
       be related with, or to overlap each other.
* (R3) If two paths in `S` are coupled with each
       other, then both must have a common prefix.
* (R4) `S` must be downward-total.

Note that two rooted paths are **related**, if one is a prefix to the other.

* `(a ancestor-of d), (d descendant-of a) := (d prefix-of a)`
* `(s related-to t) := (s prefix-of t) or (t prefix-of s)`

Note that, since the elements in such a setup are rooted paths and as such
ordered sequences of nodes, the prefix-of operator can be described as a
specialized subset-of operator.

* `(s related-to t) <=> (s prefix-of t) <=> (s subset-of t)`

Note that, due to requirement R2, any two rooted paths are expected to be
related with (i.e. one is a prefix of the other) ex-or to overlap each other
(i.e. the **RE-OV** case). However, in order to allow for a partial setup to
correspond with a forest of trees, rooted paths must be allowed to be disjoint
(i.e. the **DI-RE-OV** case). That is, the disjoint case (DI) is allowed in
the context of rooted paths that belong to distinct trees.

Note that a setup of rooted paths is different to a partial setup of scopes.
That is because such setups only need two types of relationships (DI-RE) in
order to support forests of trees. In contrary to that, a setup of rooted
paths must support three types of relationships (DI-RE-OV).

Recall that each partial setup of rooted paths is a setup of strings and as
such required to be **well formed**. Based on that, requirement R3 is to ensure
that overlapping rooted paths only have disjoint suffixes. Despite that, there
is no requirement in regards to the amounts of nodes in a shared prefix and
thus also not in regards to disjoint suffixes. That is, overlapping paths are
only required to share some common non-empty prefix (all-of) and consequently
to be disjoint their last nodes (none-of).

Note that two distinct prefixes of the same rooted path can not overlap each
other since both will always be related with each other. Because of that, a
rooted path in a partial setup can not end up having two parent paths. It is
thus not necessary to require that a partial setup must be **downward-total**
since that is a consequence of the prefix-of operator.

<!-- ======================================================================= -->
## coupled paths

Recall that two non-disjoint paths are required to share a common prefix (R3).
Because of that, two such paths always have the same first node.

* `(s coupled-with t) <-> (s[1] == t[1])` must be true for `(s,t in S)`

As a matter of consequence, overlapping paths have disjoint non-empty suffixes.

* if `(s overlaps t)` is true for `(s,t in S)`, then also ..
* `s := (p × s1)`, `t := (p × s2)` for `(#p > 0)` and ..
* `(#s1 > 0)`, `(#s2 > 0)`, `(s1 disjoint-to s2)`

Note that a shared prefix is at this point not required to be a path in `S`.

* `(p in S)` may or may not be true

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that hierarchy-based terms can be defined.

* root path, rooted setup
* ancestor path, descendant path
* no cycles, (A(s) disjoint-to D(s))
* root path of, parent path of
* child path of, sibling paths

Note that, since the prefix-of operator is the basis of the related-to operator,
ancestors hold **fewer nodes** than any of their descendants.  Despite that,
ancestors are still considered **more significant** than their descendants.

Note that each root in a setup of rooted paths can be described as a child to
the empty path `()`. That is, the empty path can be described as a theoretical
super-root.

Note that, `A(s)` is a total subsetup of rooted paths. Because of that, each
rooted path in such a setup has a unique rooted path (of rooted paths).

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
* rooted paths of rooted paths ..
* `level(s) := #rp(s)`

Note that an induced subsetup still **grows with its orientation**, not against
it. That is because the subsetup grows with the orientation of the prefix-of
operator.

Note that, as before, `A(s)` is always **a total subsetup**, whereas `D(s)`
is in general only **a partial subsetup**. That is, the overall setup must
itself be total for `D(s)` to always be a total subsetup.
