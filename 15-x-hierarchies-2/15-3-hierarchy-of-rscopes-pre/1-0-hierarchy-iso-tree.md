
<!-- ======================================================================= -->
# a (serialized) forest/hierarchy of rscopes

A sequence of reversed scopes `S` may be referred to as **a forest (F)**,
if the following requirements are met.

* (R0) `S` is an ordered sequence of sets.
* (R1) The sets of elements in `S` is a forest of reversed scopes.

A sequnce of reversed scopes `S` may be referred to as **a hierarchy (H)**,
if the following requirments are met.

* (R0) `S` is a serialized forest of scopes.
* (R1) `S` has one and only one root.

<!-- ======================================================================= -->
## document tree (DT) <=> hierarchy of rscopes (HrsPre)

Recall that, in the context of this dicsussion, the pre-order traversal and
its trace of nodes, is the default. That is because it is order-preserving
in regards to the tree order and also the child order of a document tree.

<!-- ======================================================================= -->
## (DTU => HrsPre)

Given a document tree `T(N,E)`, one can form a hierarchy of scopes `S` by
appending the sets of nodes of each rooted path `rp(n)` to a sequence of sets
while (e.g.) traversing a document tree in pre-order.

In other words, and beginning with the pre-order trace `pre(r)` of a document
tree, one first replaces each node `n` in that trace by the corresponding
rooted path `rp(n)` over DTU, which will yield a sequence `s` of all rooted
paths in pre-order. After that, one needs to replace each path in `s` by the
set of nodes, which will yield the serialized hierarchy of reversed scopes
(HrsPre).

* `t := pre(r)` for `(r == RN(DTU))`
* `s := ( rp(t[i]) | (i in [1,#t]) )`
* `H := ( N(s[i]) | (i in [1,#s]) )`

Note the set-builder like sequence-based notation.

<!-- ======================================================================= -->
## (HrsPre => DTU)

Since a serialized hierarchy of reversed scopes `S`, if formed as described
above, is an ordered sequence of scopes, one can derive the unordered document
tree DTU from it.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-of b) }`
* note - see the (Hrs => T) transformation for more

<!-- ======================================================================= -->
## decoding the doctree's child order

Recall that a hierarchy of reversed scopes `S` allows to identify a scopes `s`
as a parent scope (a superset) and also to determine its set of child scopes
`c(s)` (i.e. the least significant subsets). Because of that, one can reduce
the ordered sequence of scopes of a serialized hierarchy `S` to the child
scopes of a parent.

* `co[], co(s) := S[c(s)]` for `(s in S)`

Recall that each reversed scope in `H` contains a unique node reference of
the node it represents - its one and only characteristic element `ce(s)`.
Because of that, one can derive the child order of a node `co(n)` as an
ordered sequence of child nodes.

* `co(n) := ( ce(co[i]) | (i in [1,#co]), (n == ce(s)), (co := co(s)) )`

One can therefore derive the child order of a document tree from a hierarchy
of reversed scopes `H` as a set of ordered sequences of child nodes, which
is why one can recreate the ordered document tree DTO as well.

* `co(DT) := { co(p) | (p in PN(DTU)) }`
