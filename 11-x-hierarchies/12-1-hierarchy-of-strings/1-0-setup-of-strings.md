
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

Note that, since each `(s in S)` is required to be an ordered sequence nodes
(R2), and also required to be non-empty (R3), each such string can be said to
correspond with a path graph and therefore also with a (specialized) tree. A
setup of strings is therefore equivalent to a (specialized) setup of trees.

Note that a setup can be understood to be accompanied by **a universal set**
of nodes `U`, which can be described as the union of all the sets of nodes of
each string in the setup. Likewise, a setup can be understood to be accompanied
by **a universal graph** `G`, which can be described as the union graph of all
the strings in it, which is not necessarily a tree.

Note that the **well formedness** requirement (R4) is intended to ensure that
any two strings in a setup are disjoint, related (i.e. one is a substring of
the other) ex-or overlap each other (i.e. **DI-RE-OV**). Based on that, all
strings are required to represent node orders that do not contradict each
other - e.g. the ancestor of a node in the path graph of a string is no
descendant of that node in another string.

* the intersection between any two strings must be empty or a substring to both
* the union of two strings must be a forest, a tree or a path graph

Note that, in the case of overlapping strings, the first node of one string
must be a node in the other string. That is because the union of both strings
might otherwise not be a path graph or even a tree.

<!-- ======================================================================= -->
## a partial setup of strings

Assuming the **superstring-of** operator as the basis of the related-to
operator, a set of strings `S` may be referred to as **a partial setup**,
if the following requirements are met.

* (R0) `S` is a simple setup of strings.
* (R1) Any two strings are either disjoint ex-or related.

Note that, due to requirement R1, no string in such a setup may overlap
another string in it - i.e. the default **DI-RE** case.

Recall that a setup of strings, as a setup of specialized trees, supports
"a notion of offset". That is, the root of a subtree can be said to have a
placement in regards to the root of its supertree.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that the hierarchy-based terms defined for setups of trees still apply.

* root string, rooted setup
* ancestor string, descendant string
* no cycles, (A(s) disjoint-to D(s))
* root string of, parent string of
* child string of, sibling strings

Note that, `A(s)` in the context of a partial setup is a total subsetup of
strings. As such, a partial setup can be described as being downward-total.

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

Assuming the superstring-of operator as the basis of the related-to operator,
**an induced subsetup** `S[r]` is such that it contains `r` as its root, and
also all the substrings of `r` in `S`:

* `S[r], S[r,*] := { t | (t substring-of r) or (t == r) }`

<!-- ======================================================================= -->
## subsetups A() and D()

As with setups of trees, `A(s)` is always a total subsetup. In contrary to that,
`D(s)` is a total subsetup only if the overall setup is total. Because of that,
any partial setup is always downward-, but not necessarily also upward-total.

Furthermore, both subsetups can be extended to include the input string `s` as
the leaf in `A*(s)` and as the root in `D*(s)`. This ensures that both are
always non-empty.

* `A*(s) := A(s) + {s}` and `D*(s) := D(s) + {s}`

<!-- ======================================================================= -->
## paths of strings

Since each string in `A*(s)` has a unique amount of nodes, the strings in it
can be used to define the **rooted path** `rp(s)` of string `s` as an ordered
sequence of strings, ordered in decreasing order of significance.

Based on that, **a path** can be formed from string `a` to string `b`,
if string `a` is an ancestor of `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` is true if `p(a,b)` can be formed

Since paths can be formed in the context of a partial setup of strings, all
other path-based definitions can be assumed to be available.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(s) := #rp(s)` - the level of string `s`
