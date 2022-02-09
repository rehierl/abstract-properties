
<!-- ======================================================================= -->
# Forest/Hierarchy of trees

Note that a family of trees `S`, if formed from a tree `T(N,E)` by collecting
the induced subtrees of all the nodes in `N`, is a hierarchy of trees `H`. As
such, hierarchy `H` provides a complete definition of tree `T`, which is why
any tree is isomorphic to a hierarchy of trees.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## a forest of trees (F)

A partial setup of trees `S` may be referred to as **a forest**,
if the following requirements are met.

* (R0) `S` is a partial setup of trees.
* (R1) There are `#N` induced subtrees for each tree `t(N,E)` in `S`.

Recall that the related-to operator of a partial setup `S` is defined based
on the **supertree-of** operator and that such a setup covers the **DI-RE**
case. Because of that, a forest of trees `F` may only contain disjoint ex-or
related trees.

Note that requirement R1 is intended to state that for each tree `t(N,E)` in
`S`, all the proper induced subtrees of that tree must also be trees in `S`.
Because of that, this requirement can be understood to ensure that each tree
in `S` has one and only one characteristic element (CE), its root node.

Note that a forest of trees may have any number of root trees,
including none at all.

* `(#RS(F) in [0,*])` is true

<!-- ======================================================================= -->
## a hierarchy of trees (H)

A partial setup `S` may be referred to as **a hierarchy**,
if the following requirements are met.

* (R0) `S` is a forest of trees.
* (R1) `S` has one and only one root.

Note that a hierarchy of trees `H` has the following properties:

* `(#RS(H) == 1)` and `(#S > 0)` must be true
* Each tree has no ex-or one parent - a supertree.
* Each tree may have any number of child trees - subtrees.
* Any ancestor has more nodes than all of its descendants.
* Each tree has a unique rooted path of trees.
* The root tree `r` is equal to `G(H)`.

<!-- ======================================================================= -->
## set of all hierarchies and forests

Similar to hierarchies and forests of sets, a theoretical set of all possible
hierarchies (UH) and a theoretical set of all possible forests (UF) can be
assumed to exist.

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in UH)` states that `h` is expected to be
a hierarchy. Likewise, `(f in UF)` states that `f` is expected to be a forest
of trees.

* `(UH proper-subset-of UF)`
