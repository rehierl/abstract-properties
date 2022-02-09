
<!-- ======================================================================= -->
# node tree (T) <=> hierarchy of edges (He)

Any tree (T) of two or more nodes is isomorphic to a hierarchy of edges (He).

<!-- ======================================================================= -->
## (T => He)

Any node tree of two or more edges `T(N,E)` has a set of edges that satisfies
all the requirements of a hierarchy of edges `He`. Because of that, the process
of transforming a tree into a hierarchy of edges consists of extracting the
tree's set of edges.

* `He(T) := E(T)`

<!-- ======================================================================= -->
## (He => T)

Similar to before, the process of transforming a hierarchy of edges `H` into a
tree `T(N,E)` essentially consists of forming a set of nodes from the edges in
the hierarchy.

* `T(N,E) := T(U(He),He)`

Note that, since none of the sets of edges will be modified in any way,
transforming a tree `T` into a hierarchy `He`, and then back into a tree `T*`
will yield the source tree. That is, `(T == T*)` is true.
