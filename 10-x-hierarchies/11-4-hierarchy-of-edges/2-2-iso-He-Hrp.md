
<!-- ======================================================================= -->
# hierarchy of edges (He) <=> hierarchy of rpaths (Hrp)

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
