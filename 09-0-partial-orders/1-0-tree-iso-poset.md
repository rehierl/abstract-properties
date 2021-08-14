
<!-- ======================================================================= -->
# node tree <=> node order

Give a node tree `T := (N,E)` one can easily form a node order `Q := (N,<)`
by defining the order operator based on the paths that can be formed over `T`.

* `Q := (N,<)` such that `N := V(T)`
* `(a < b) := (p := [a,..,b] in P over T) and (#p > 1)`

One can then recreate `T` from `Q` by forming the transitive reduction
over the edges in the order relation of node order `Q`.

* `T* := (N,E)` such that `N := V(Q)`
* `E` := the transitively reduced `E(Q)`
* note - `(T* == T)` is true

Consequently, any node tree can be said to be **isomorphic** to a strict partial
node order (as described). That is, one can be transformed into the other.

Note that a node order `Q` formed from a node tree `T` as described here may
have any number of total suborders. These result from the edges over the source
tree `T`, and from the paths (which correspond with path graphs) that can be
formed over the edges in `T`.

Note that any tree `T` can be described as **a union of path graphs**,
and its node order `Q` as **a union of total suborders**.

<!-- ======================================================================= -->
## node tree => node order

One can easily form an explicit node order `Q := (N,<)` from a given node tree
`T := (N,E)` by the following simple definition.

* `Q := (N,<)` such that `N := V(T)`
* `(a < b) := (p := [a,..b] in P over T) and (#p > 1)`

That is, the set of vertices in `Q` is equal to the set of nodes in `T`. In
addition to that, two nodes are connected in `Q` iff a path of node length
2 or more can be formed between both nodes.

Formed as such, the following applies ..

* `Q` may have pairs of incomparable nodes
* `<` is directional - `T` is an acyclic digraph
* `Q` is not reflexive - `(#p > 1)` is required
* `Q` is transitive - based on paths over `T`
* `Q` is not trichotomous - e.g. siblings
* even though `(r < n)` holds for any non-root `n`
* `Q` is a-symmetric - unique rooted paths, acyclic

One can therefore conclude, that the node order
`Q` is **a strict partial order** of nodes.

<!-- ======================================================================= -->
## node order => node tree

One can recreate `T` from `Q` by forming the transitive reduction
over the edges in the order relation of node order `Q`.

* `T* := (N,E)` such that `N := V(Q)`
* `E` := the transitively reduced `E(Q)`

Note that defining the order operator of `Q` based on the paths that can be
formed over `T` ensures that `Q` is transitive. In addition to that, a node
tree is such that it has no transitive edge. Because of that, `T*` is equal
to `T` since the transitive reduction can, based on the above construction,
be guaranteed to reproduce `E(T)`.
