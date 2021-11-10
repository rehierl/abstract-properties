
<!-- ======================================================================= -->
# Forest/Hierarchy of trees

Note that a family of trees `S`, if it is formed from a tree `T(N,E)` by
collecting the induced subtrees of all the nodes in `N`, is a hierarchy of
trees `H`. As such, hierarchy `H` holds the complete definition of tree `T`,
which is why any tree is isomorphic to a hierarchy of trees.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## a forest of trees (F)

A partial setup of trees `S` may be referred to as **a forest of trees**,
if the following requirements are met:

* (R0) `S` is a partial setup of trees.
* (R1) There are `#N` subtrees for each tree `t(N,E)` in `S`.
* (R2) Each tree `(t in S)` is an induced subtree to each tree in `A(t)`.

Recall that a partial setup `S` covers the **DI-RE** case. Furthermore, such a
setup may have any number of root trees, which is why a forest for trees may
even be empty.

Note that requirements R1 and R2 intend to state that for each tree `t(N,E)`
in `S`, all the induced subtrees of that tree must also be trees in that setup.
As can be seen below, these requirements are essential in order to ensure that
an order relation can be formed from such a setup.

<!-- ======================================================================= -->
## a hierarchy of trees (H)

A partial setup `S` may be referred to as **a hierarchy of trees**,
if the following requirements are met:

* (R0) `S` is a forest of trees.
* (R1) `S` has one and only one root tree `r`.

Note that a hierarchy of trees `H` has the following properties:

* `(#S > 0)` - A hierarchy is always non-empty.
* All the trees in a hierarchy are disjoint ex-or related.
* Each tree has no ex-or one parent tree - a supertree.
* Each tree may have any number of child trees - subtrees.
* Any ancestor has more nodes than all of its descendants.
* Each tree has a unique rooted path of trees.
* The root tree `r` is equal to `U(H)`.

<!-- ======================================================================= -->
## set of all hierarchies and forests

Similar to hierarchies and forests of sets, a theoretical set of all possible
hierarchies **UH** and a theoretical set of all possible forests **UF** can be
assumed to exist.

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`
* `(UH proper-subset-of UF)`

Note that the expression `(h in UH)` can be used to state that `h` is expected
to be a hierarchy. Likewise, `(f in UF)` can be used to express that `f` is
expected to be a forest of trees.
