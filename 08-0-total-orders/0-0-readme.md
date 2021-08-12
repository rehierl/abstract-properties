
<!-- ======================================================================= -->
# total orders

This chapter describes transformations that transform one type of construct `ci`
into another construct `cj` such that the formed construct `cj` can be reversed
back into `ci`. Because of that, `ci` can be said to be **isomorphic** to `cj`.

<!-- ======================================================================= -->
## order of scopes <=> path graph, node order

When reading about the above correspondence between a path graph `s := (N,E)`
and a strict total containment order of scopes `P := (S,<)`, one might notice
a fundamental aspect, which is to be highlighted here.

(1.1) From the containment order `P` a graph `G` can be formed by performing
a transitive reduction on the order relation of `P`.

(1.2) Since the set of vertices in `V(G)` is then still equal to the family
of scopes `V(P)`, each scope has to be replaced by its characteristic element
`ce(si)` such that the final graph `s*` can be formed.

Since there is no real reason, as to why the transitive reduction has to be
performed first, one can in general flip the order of operations.

(2.1) From the containment order `P` an order of nodes `Q` can be formed from
the order relation of `P` such that each scope in `P` is replaced by its
characteristic element `ce(s)`.

(2.2) From the node order `Q` a graph `s*` can be formed by performing the
transitive reduction on the order relation of `Q`.

Since `s*` is in both cases equal to the initial path graph `s`, one can
conclude, that each path graph (of distinct nodes) `s` is **isomorphic**
to a containment order `P` and also to an actual node order `Q`.

As a consequence of that, any path graph is isomorphic to an actual node order.
Because of that, each path graph can be seen as the visual representation of
an actual node order.
