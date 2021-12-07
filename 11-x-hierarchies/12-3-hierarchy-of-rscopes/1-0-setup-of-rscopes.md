
<!-- ======================================================================= -->
# A partial setup

<!-- ======================================================================= -->
## a simple setup (of rscopes)

A set of sets `S` will be referred to as **a (simple) setup**,
if the following requirements are met.

* (R0) `S` is a set/family of sets.
* (R1) `S` is expected to be non-empty.
* (R2) Each `(s in S)` is non-empty.

Note that, unless specified otherwise, all set-based definitions made in the
context of setups of default scopes still apply.

<!-- ======================================================================= -->
## a partial setup (of rscopes)

Assuming the **subset-of** operator as the basis of the related-to operator,
a set of sets `S` will be referred to as **a partial setup**, if the following
requirements are met.

* (R0) `S` is a simple setup of rscopes.
* (R1) Any two sets in `S` are either related ex-or overlap each other.
* (R2) `S` must be **downward-total**.

Note that, due to requirement R1, no set in such a setup may be disjoint to
another set - i.e. the **RE-OV** case.

Note that requirement R2 is a necessity since a scope could otherwise have
overlapping subsets as ancestor scopes, which could result in reversed scopes
having more than one parent scope.

Recall that in the context of default scopes (i.e. the DI-RE case), one only
needs to find a single shared element in order to conclude that two sets are
related. In contrary to that, and in the context of reversed scopes (i.e. the
RE-OV case), one must test all the elements in both sets in order to exclude
that both sets overlap each other.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that, similar to a partial setup of default scopes, hierarchy-based terms
can be defined. The most notable definitions are as follows.

A **root scope** is such that it is **no superset** to another scope. As such,
a root scope may or may not have a superscope in `S`. That is, a root scope
may or may not be a source scope to another scope.

A **rooted setup** is such that it has one and only one root scope. That is,
the set of root scopes `RS(S)` of setup `S` consists of one scope only.

An **ancestor scope** `a` is a subset to another scope.
Likewise, a **descendant scope** `d` is a superset to another scope.

* `A(s) := { a | (a ancestor-of s) }`
* `D(s) := { d | (d descendant-of s) }`

Note that a partial setup has **no cycles**. That is because no scope can be
a subset and also a superset to another scope. Because of that, the set of
ancestor scopes `A(s)` and descendant scopes `D(s)` are disjoint.

* `(A(s) disjoint-to D(s))` is true

The **root scope** `r(s)` is the least significant ancestor of `s`. The
**parent scope** `p(s)` is the most significant ancestor of `s`. (Recall
that "most significant" and "least significant" is in regards to the
amount of nodes in the each scope).

A descendant scope `(c in D(p))` is a **child scope** of `p`, if `p` is the
parent scope of `c`. (Note that, in a partial setup, a scope may have any
number of overlapping child scopes).

* `c(p) := { c | (p(c) == p) for (c in D(s)) }`

Two scopes `(s,t in S)` may be described as **siblings**, if both scopes have
the same parent. (Note that, unlike in a hierarchy of default scopes, reversed
scopes that have the same parent overlap each other. Also, there is no child
order over siblings).

* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`
* `(s sibling-of t) <-> (A(s) == A(t))`

Recall that a partial setup of reversed scopes is required to be downward-total.
Because of that, siblings have the same set of ancestors.

<!-- ======================================================================= -->
## a total setup (of rscopes)

A set of sets `S` will be referred to as **a total setup**, if the following
requirements are met.

* (R0) `S` is a partial setup of rscopes.
* (R1) Any two sets in `S` are related with each other.

Note that a total setup does not allow pairs of disjoint sets (R0), and also
no pairs of overlapping sets (R1) - i.e. the **RE only** case.

Note that in a total setup any parent has **one and only one child**. A total
setup is therefore **downward- and upward-total**, which is why any non-empty
total setup has **one root and one leaf only**.

Note that the root scope of `A(t)` is the root scope of `t`,
and that the leaf scope of `A(t)` is the parent of `t`.

<!-- ======================================================================= -->
## remarks

Note that sets may in principle have disjoint subsets and also subsets that
overlap each other. In the context of a setup of reversed scopes, overlapping
subsets results in parent scopes to have more than one parent scope. Because
of that, a setup of reversed scopes must be required to be such that the scopes
which are subsets to another scope are all related with each other - i.e. one
scope must be a subset to the other. The set of all subsets of a scope must
therefore be a total setup of sets - i.e. a partial setup of reversed scopes
must be required to be **downward-total**.

- the intersection of two sets must be a set in S
- the union of two sets may or may not be a set in S
- if related, then yes - if overlapping, then no
