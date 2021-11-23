
<!-- ======================================================================= -->
# Forest/Hierarchy of traces

Note that a family of strings `S`, if formed from an unordered doctree (DTU)
`T(N,E)` by collecting the pre-order traces of the induced subtrees of all
the nodes in `N`, is a hierarchy of traces `Hpre`. As such, hierarchy `Hpre`
holds the definition of the document tree, including the doctree's child order,
which is why any document tree is isomorphic to such a hierarchy of traces.

* `S := { pre(t) | (t := T[n]) for (n in N) }`
* `(#S == #N)` is true

Recall that the child order of a document tree is a suborder to the doctree's
pre-order trace. That is, the child order is embedded into the trace of the
doctree's root, and partially also in the traces of every other node.

<!-- ======================================================================= -->
## a forest of traces (F)

A partial setup of strings `S` may be referred to as **a forest of traces**,
if the following requirements are met.

* (R0) `S` is a forest of strings.
* (R1) Each `(s in S)` is the pre-order trace of a node.

Note that the related-to operator is based on the **superstring-of** operator.
Also, a forest covers the default **DI-RE** case, which is why a forest of
traces `F` must only contain disjoint ex-or related strings.

<!-- ======================================================================= -->
## a hierarchy of traces (H)

A partial setup of strings `S` may be referred to as **a hierarchy of traces**,
if the following requirements are met.

* (R0) `S` is a forest of traces.
* (R1) `S` has one and only one root.

Note that a hierarchy of strings is a rooted setup of strings such that all
the other strings in it are substrings to the root.

<!-- ======================================================================= -->
## remarks

Note that a forest of traces `F` requires each string `(s in F)` to have `#s`
substrings in `F`, including `s` itself. In addition to that, the substrings
of each string are such that they begin in a unique node. That is, there are
no two strings in `S` that have the same first node.

* `(s[1] != t[1])` for all `(s,t in S)`
