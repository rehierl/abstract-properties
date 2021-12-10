
<!-- ======================================================================= -->
# A partial setup

<!-- ======================================================================= -->
## a simple setup (of rscopes)

A set of sets `S` will be referred to as **a (simple) setup**,
if the following requirements are met.

* (R0) `S` is a set/family of sets.
* (R1) `S` is expected to be non-empty.
* (R2) Each `(s in S)` must be a simple set.
* (R3) Each `(s in S)` is non-empty.

Note that, unless specified otherwise, all set-based definitions made in the
context of setups of (default) scopes still apply.

<!-- ======================================================================= -->
## a partial setup (of rscopes)

Assuming the **subset-of** operator as the basis of the related-to operator,
a set of sets `S` will be referred to as **a partial setup**, if the following
requirements are met.

* (R0) `S` is a simple setup of rscopes.
* (R1) The scopes in `S` are expected to
  be related with, or to overlap each other.
* (R2) `S` must be downward-total.

Note that, due to requirement R1, any two scopes are expected to be related
with (i.e. one is a subset of the other) ex-or to overlap each other (i.e. the
**RE-OV** case). However, in order to allow for a partial setup to correspond
with a forest, such scopes must be allowed to be disjoint (i.e. the **DI-RE-OV**
case). That is, the disjoint case (DI) is allowed in the context of scopes that
belong to distinct rees.

Recall that any set may in general have disjoint subsets and also subsets that
overlap each other. In the context of a setup of reversed scopes, overlapping
subsets result in scopes having more than one parent. Because of that, a setup
of reversed scopes must be required to be such that scopes, which are subsets
to another scope, are related with each other. The set of all subsets of a
scope must therefore be required to be a total sub-setup of scopes. Hence, a
partial setup of reversed scopes must be required to be **downward-total**.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that, similar to a partial setup of default scopes, hierarchy-based terms
can be defined. The most notable definitions are as follows.

A **root scope** is such that it is **no superset** to another scope. As such,
a root may or may not have a superscope in `S`. That is, a root may or may not
be a source to another scope.

A **rooted setup** is such that it has one and only one root scope. That is,
the set of root scopes `RS(S)` of setup `S` consists of one scope only.

An **ancestor** `a` is a subset to another scope.
Likewise, a **descendant** `d` is a superset to another scope.

* `(a ancestor-of d), (d descendant-of a) := (a subset-of d)`
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
parent of `c`. (Note that, in a partial setup, a scope may have any number
of overlapping child scopes).

* `c(p) := { c | (p(c) == p) for (c in D(s)) }`

Two scopes `(s,t in S)` may be described as **siblings**, if both have the same
parent. (Note that, unlike in a hierarchy of default scopes, reversed scopes
that have the same parent overlap each other. Also, there is no child order
over siblings).

* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`
* `(s sibling-of t) <-> (A(s) == A(t))`

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

<!-- ======================================================================= -->
## extended definitions

TODO
