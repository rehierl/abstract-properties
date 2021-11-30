
<!-- ======================================================================= -->
# hierarchy of trees (Ht) <=> hierarchy of scopes (Hs)

Even though one can first transform a hierarchy of trees `Ht` into a node tree
`T(N,E)`, and then that tree into a hierarchy of scopes `Hs`, one can also
directly transform `Ht` into `Hs`. Likewise, a direct transformation of `Hs`
into `Ht` is possible.

<!-- ======================================================================= -->
## Ht => Hs

A hierarchy of scopes Hs can be formed by collecting all of the sets of nodes
of each tree in Ht.

* `Hs := { N(t) | (t in Ht) }`

<!-- ======================================================================= -->
## Hs => Ht

Similar to the above, a hierarchy of scopes Hs allows to form a hierarchy of
trees Ht.

Recall that a hierarchy of scopes Hs corresponds with a node tree `T(N,E)`.
Furthermore each scope `(s in Hs)` is such that it has one characteristic
element only (i.e. the node definition `n(s)` of the node represented by `s`).
Because of that, scope `(s in Hs)` and all of its subsets in Hs form a
sub-hierarchy that corresponds with the induced subtree `T[n(s)]`.

In order to form Ht from Hs, one first needs to replace each set `s` with a
hierarchy of scopes, each of which is isomorphic to the corresponding induced
subtree in `T`.

* `Hs1 := { Hs[s] | (s in Hs) }`

Note that `Hs[s]` denotes an interval of scopes that has `s` as its root set
and that contains all the subsets of `s` in `Hs`. That is, `Hs[s]` denotes an
induced subsetup of `Hs`.

One can then use `Hs1` to from the hierarchy of trees `Ht` by replacing each
hierarchy of scopes in `Hs1` by the tree to which it is isomorphic. That is,
each scope in `Hs1` is replaced by the corresponding induced subtree over `T`.

* `Ht := { T(s) | (s in Hs1) }`

Note that `T(s)` denotes the process of forming tree `t` from the corresponding
sub-hierarchy in `Hs1`.
