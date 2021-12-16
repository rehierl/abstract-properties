
<!-- ======================================================================= -->
# a (serialized) forest/hierarchy of scopes

A sequence of scopes `S` may be referred to as **a forest (F)**,
if the following requirements are met.

* (R0) `S` is an ordered sequence of sets.
* (R1) The sets of elements in `S` is a forest of scopes.

A sequence of scopes `S` may be referred to as **a hierarchy (H)**,
if the following requirements are met.

* (R0) `S` is a serialized forest of scopes.
* (R1) `S` has one and only one root.

<!-- ======================================================================= -->
## document tree (DT) <=> hierarchy of scopes (HsSer)

Recall that, in the context of this dicsussion, the pre-order traversal and
its trace of nodes, is the default. That is because it is order-preserving
in regards to the tree order and also the child order of a document tree.

<!-- ======================================================================= -->
## (DTU => HsSer)

Given a document tree `T(N,E)`, one can form a hierarchy of scopes `S` by
appending the sets of nodes of each induced subtree `T[n]` to a sequence
while (e.g.) traversing a document tree in pre-order.

In other words, and beginning with the pre-order trace `pre(r)` of a document
tree, one first replaces each node in that trace by the corresponding induced
subtree `T[n]` over DTU, which will yield a sequence `s` of all the induced
subtrees in pre-order. After that, one merely needs to replace each tree in
`s` by the tree's set of nodes, which will yield the serialized hierarchy
of scopes (HsSer).

* `t := pre(r)` for `(r == RN(DTU))`
* `s := ( DTU[i] | (i in [1,#t]) )`
* `H := ( N(s[i]) | (i in [1,#s]) )`
* note - `(#s == #N(DTU))` is true

Note the set-builder like sequence-based notation.

<!-- ======================================================================= -->
## (HsSer => DTU)

Since a serialized hierarchy of scopes `S`, if formed as described above, is
an ordered sequence of scopes, one can derive the unordered document tree DTU
from it.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-set-of b) for (a,b in S) }`
* note - see the (Hs => T) transformation for more

<!-- ======================================================================= -->
## decoding the doctree's child order

Recall that a hierarchy of scopes `S` allows to identify a scope `s` as a
parent scope (a subset) and also to determine its set of its child scopes
`c(s)` (i.e. the most significant sub-scopes). Because of that, one can
reduce the ordered sequence of scopes of a serialized hierarchy `S` to
the child scopes of a parent.

* `co[], co(s) := S[c(s)]` for `(s in S)`

Recall that each scope in `H` contains a unique node reference of the node
it represents - its one and only characteristic element `ce(s)`. Because
of that, one can derive the child order of a node `co(n)` as an ordered
sequence of child nodes.

* `co(n) := ( ce(co[i]) | (i in [1,#co]), (n == ce(s)), (co := co(s)) )`

One can therefore derive the child order of a document tree from a hierarchy
of scopes `H` as a set of ordered sequences of child nodes, which is why one
can recreate the ordered document tree DTO as well.

* `co(DT) := { co(p) | (p in PN(DTU)) }`
