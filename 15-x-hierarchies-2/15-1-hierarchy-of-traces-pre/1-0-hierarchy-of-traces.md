
<!-- ======================================================================= -->
# Forest/Hierarchy of traces

Forests and hierarchies of pre-order traces can be defined as follows.

<!-- ======================================================================= -->
## a forest of traces (F)

A set of strings `S` may be referred to as **a forest**,
if the following requirements are met.

* (R0) `S` is a forest of strings.
* (R1) Each `(s in S)` is the pre-order trace of a node.

Recall that a forest of strings is defined as a partial setup of strings that
is based on the **superstring-of** operator. Furthermore, any two strings in
such a forest must either be disjoint ex-or related with each other (i.e. the
**DI-RE** case).

<!-- ======================================================================= -->
## a hierarchy of traces (H)

A set of strings `S` may be referred to as **a hierarchy**,
if the following requirements are met.

* (R0) `S` is a forest of traces.
* (R1) `S` has one and only one root.

Note that a hierarchy of strings is a rooted setup of strings such that all the
other strings in it are substrings to the root. Despite that, the traces in a
hierarchy still satisfy the DI-RE case.

<!-- ======================================================================= -->
## remarks

Note that a forest of traces `F` requires each string `(s in F)` to have `#s`
substrings in `F`, including `s` itself. In addition to that, the substrings
of each string are such that they begin in a unique node. That is, there are
no two strings in `S` that have the exact same first node.

* `(s[1] != t[1])` for all `(s,t in S)` and `(s != t)`

Note that, since there must be `#s` substrings for each trace `s` in a forest
of traces `F`, the length of the root trace `r` in a hierarchy of traces `H`
must be equal to the total amount of traces in `H`.

* `(#H == #r)` for `(r == RT(H))`

Note that, since each pre-order trace has a unique first node, and since there
must be `(#s-1)` proper sub-traces, the first node of a trace is its one and
only characteristic element **CE**.
