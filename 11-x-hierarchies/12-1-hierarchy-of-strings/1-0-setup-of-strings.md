
<!-- ======================================================================= -->
# setups of strings

As before with setups of trees, and with string-based definitions in mind,
setups of strings can be defined as follows.

<!-- ======================================================================= -->
## a (simple) setup of strings

A set of strings will be referred to as **a (simple) setup** `S`,
if the following requirements are met.

* (R0) `S` is a set/family of strings.
* (R1) `S` is expected to be non-empty.
* (R2) Each `(s in S)` must be an ordered sequence.
* (R3) Each `(s in S)` must be non-empty.
* (R4) `S` must be **well formed**.

Note that, since each string `(s in S)` is required to be an ordered sequence
nodes (R2), and also required to be non-empty (R3), each such string can be
said to correspond with a path graph and therefore also with a (specialized)
tree. A setup of strings is therefore equivalent to a (specialized) setup of
trees.

Note that a setup can be understood to be accompanied by **a universal set**
of nodes `U`, which can be described as the union of all the sets of nodes
of each string in it. Likewise, a setup can be understood to be accompanied
by **a universal graph** `G`, which can be described as the union of all the
strings in it, which is not necessarily a tree.

Note that the **well formedness** requirement (R4) is intended to ensure that
any two strings in such a setup are disjoint (DI), related (RE - i.e. one is
a substring of the other) ex-or overlap (OV) each other (i.e. **DI-RE-OV**).
Because on that, all strings are required to represent node orders that do
not contradict each other - e.g. the ancestor of a node in the path graph of
a string is no descendant of that node in another string.

* the intersection between any two strings must be empty or a substring to both
* the union of two strings must be a forest, a tree or a path graph

Note that, in the case of coupled strings, **the first node of one** string
(aka. its root node) must be a node in the other. Because of that requirement,
the intersection of two coupled strings is always a prefix to one. This to
ensure that the union graph of two coupled strings does not have a node that
has two incoming parent nodes.

Note that, in the case of coupled strings, the root of one string is not also
required to be the root of the other string. That is, the root of one string
may in general match any node in the other string.

Note that a setup of strings supports **a notion of offset**. That is, the root
of a substring can be said to have a placement in regards to the root of its
superstring. Likewise, and since overlapping strings must intersect in the
prefix of one string, two overlapping strings can be understood to have such
a notion of placement in regards to each other.

<!-- ======================================================================= -->
## a partial setup of strings

Assuming the **superstring-of** operator as the basis of the related-to
operator, a set of strings `S` may be referred to as **a partial setup**,
if the following requirements are met.

* (R0) `S` is a simple setup of strings.
* (R1) Any two strings are either disjoint ex-or related.

Note that, due to requirement R1, no string in such a setup may overlap
another string - i.e. the **DI-RE** case.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that the hierarchy-based terms can be defined.

* root string, rooted setup
* ancestor string, descendant string
* no cycles, (A(s) disjoint-to D(s))
* root string of, parent string of
* child string of, sibling strings

Note that, since the superstring-of operator is the basis of the related-to
operator, ancestors hold **more nodes** than any of their descendants. Despite
that, ancestors are still considered **more significant** than all of their
descendants.

Note that, `A(s)` is a total subsetup of strings. As such, a partial setup can
be described as being **downward-total**. Because of that, each string in such
a setup has a unique rooted path.

Note that substrings, which are **siblings** to each other, are not required
to hold the same amount of nodes. That is, sibling strings may in general
differ in their length. Despite that, siblings a guaranteed to hold fewer
nodes than their parent.

<!-- ======================================================================= -->
## a total setup of strings

A set of strings `S` will be referred to as **a total setup**,
if the following requirements are met.

* (R0) `S` is a partial setup of strings.
* (R1) Any two strings are related with each other.

Note that a total setup does not allow pairs of disjoint strings (R1),
and also no pairs of overlapping strings (R0) - i.e. the **RE only** case.

Note that, in a total setup, any parent has **one and only one child**. Because
of that, a total setup is **downward- and upward-total**. Any non-empty total
setup therefore has **one root and one leaf only**.

<!-- ======================================================================= -->
## (induced) subsetup

The subset of a setup may be described as **a sub-setup**.

* `(A subsetup-of B) := (A subset-of B)`

An **induced subsetup** `S[r]` is such that it contains `r` as its root,
and also all the substrings of `r` in `S`:

* `S[r], S[r,*] := { t | (t substring-of r) or (t == r) }`

<!-- ======================================================================= -->
## subsetups A() and D()

As with setups of trees, `A(s)` is always a total subsetup. In contrary to that,
`D(s)` is a total subsetup only if the overall setup is total. Because of that,
any partial setup is always downward-, but not necessarily upward-total.

Furthermore, the definition of both subsetups can be extended to include the
input string `s` as the leaf in `A*(s)` and as the root in `D*(s)`. This to
ensure that both subsetups are always non-empty.

* `A*(s) := A(s) + {s}` and `D*(s) := D(s) + {s}`

<!-- ======================================================================= -->
## paths of strings

Since each string in `A*(s)` has a unique length, the strings in it can be used
to define the **rooted path** `rp(s)` of string `s` as an ordered sequence of
strings, ordered in decreasing order of significance.

Based on that, **a path** of strings can be formed from string `a` to string
`b`, if string `a` is an ancestor of `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` is true if `p(a,b)` can be formed

Since paths can be formed in the context of a partial setup of strings,
all other path-based definitions can be assumed to be defined.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(s) := #rp(s)` - the level of string `s`
