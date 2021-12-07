
<!-- ======================================================================= -->
# isomorphisms

Note that a hierarchy of edges must have at least a root edge. Because of that,
a hierarchy must always have two or more nodes. Consequently, each hierarchy
can only correspond with **a tree of two or more nodes**.

<!-- ======================================================================= -->
## node tree (T) <=> hierarchy of edges (He)

Any tree (T) of two or more nodes is isomorphic to a hierarchy of edges (He).

<!-- ======================================================================= -->
## (T => He)

Any node tree of two or more edges `T(N,E)` has a set of edges that satisfies
all the requirements of a hierarchy of edges `He`. Because of that, the process
of transforming a tree into a hierarchy of edges consists of extracting the
tree's set of edges.

* `He(T) := E(T)`

<!-- ======================================================================= -->
## (HE => T)

Similar to before, the process of transforming a hierarchy of edges `H` into a
tree `T(N,E)` essentially consists of forming a set of nodes from the edges in
the hierarchy.

* `T(N,E) := T(U(He),He)`

Note that, since none of the sets of edges will be modified in any way,
transforming a tree `T` into a hierarchy `He`, and then back into a tree `T*`
will yield the source tree. That is, `(T == T*)` is true.

<!-- ======================================================================= -->
## hierarchy of edges (He) <=> hierarchy of rpaths (Hrp)

A hierarchy of edges (He) is isomorphic to a hierarchy of rooted paths (Hrp)
of two or more rooted paths.

Note that a tree (T) that has two nodes only must have an edge `(r,n)` which
connects the tree's root `r` with its only child `n`. As such, the hierarchy
of rooted paths of that tree only consists of two rooted paths only:
`(r)` and `(r,n)`.

<!-- ======================================================================= -->
## (He => Hrp)

Any hierarchy of edges (He) can be transformed into a hierarchy of rooted
paths (Hrp) of two or more paths by collecting all those rooted paths that
can be formed over the edges in He.

* `Hrp(He) := { p(r,n) | (r := src(RE(He))), (n in U(He)) }`
* `RE(He)` denotes the root edge in He
* `src(e)` denotes the source node of the given edge

<!-- ======================================================================= -->
## (Hrp => He)

Any hierarchy of rooted paths (Hrp) of two or more paths can be transformed
into a hierarchy of edges (He) by collecting those edges that are embedded
into the rooted paths (Hrp).

`He(Hrp) := { e | (e in E(rp)), (rp in Hrp) }`

Recall that any rooted path is an ordered sequence of nodes and therefore
corresponds with a path graph. Because of that, graph-based operators (e.g.
`E()` - returns the set of edges in that path) can be used in a less strict
fashion.
