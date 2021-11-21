
<!-- ======================================================================= -->
# Forest/Hierarchy of trees

Note that a family of trees `S`, if formed from a tree `T(N,E)` by collecting
the induced subtrees of each node in `N`, is a hierarchy of trees `H`. As such,
hierarchy `H` holds the complete definition of tree `T`, which is why any tree
is isomorphic to a hierarchy of trees.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## a forest of trees (F)

A partial setup of trees `S` may be referred to as **a forest of trees**,
if the following requirements are met.

* (R0) `S` is a partial setup of trees.
* (R1) There are `#N` subtrees for each tree `t(N,E)` in `S`.
* (R2) Each tree `(t in S)` is an induced subtree to every tree in `A(t)`.

Recall that a partial setup `S` covers the **DI-RE** case. Because of that,
a forest of trees `F` may only contain disjoint ex-or related trees.

Note that requirements R1 and R2 intend to state that for each tree `t(N,E)`
in `S`, all the proper induced subtrees of that tree must also be trees in
that setup. That is, for each tree `(t in S)` there are `#N` trees in `S`.
Both requirements can therefore be understood to be analogous to "Each set
in a setup of sets must have one any only one CE".

Note that a forest of trees may have any number of root trees,
including none at all.

* `(#RS(F) in [0,*])` is true

<!-- ======================================================================= -->
## a hierarchy of trees (H)

A partial setup `S` may be referred to as **a hierarchy of trees**,
if the following requirements are met.

* (R0) `S` is a forest of trees.
* (R1) `S` has one and only one root.

Note that a hierarchy of trees `H` has the following properties:

* `(#RS(H) == 1)` must be true
* The root tree `r` is equal to `U(H)`.
* `(#S > 0)` - A hierarchy is always non-empty.
* All the trees in a hierarchy are "DI ex-or RE".
* Each tree has no ex-or one parent - a supertree.
* Each tree may have any number of child trees - subtrees.
* Any ancestor has more nodes than all of its descendants.
* Each tree has a unique rooted path.

<!-- ======================================================================= -->
## set of all hierarchies and forests

Similar to hierarchies and forests of sets, a theoretical set of all possible
hierarchies **UH** and a theoretical set of all possible forests **UF** can
be assumed to exist.

* `UH := { h | "h is a hierarchy" }`
* `UF := { f | "f is a forest of hierarchies" }`

Because of that, the expression `(h in UH)` states that `h` is expected to be
a hierarchy. Likewise, `(f in UF)` states that `f` is expected to be a forest
of trees.

* `(UH proper-subset-of UF)`
