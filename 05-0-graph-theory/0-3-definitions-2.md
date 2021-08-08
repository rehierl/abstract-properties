
<!-- ======================================================================= -->
# miscellaneous definitions

<!-- ======================================================================= -->
## in, contains

A sequence of vertices can be understood to represent a (valid) path `p` over
graph `G`, if `p` is an element of the graph's set of paths `P`. In such a case,
graph `G` is understood to contain path `p`.

* `(p in P), (p in G)` := `p` is a path over the edges in `G`
* `(G contains p) := (p in G)`

<!-- ======================================================================= -->
## aPb

Similar to the indicator function `aEb` for a pair of adjacent vertices, an
indicator function `aPb` can be defined for a pair of vertices such that it
returns true, if a path can be formed over a particular graph that has both
vertices specified as its endpoints. That is, `aPb` is understood to be true,
if a path exists that begins in `a` and ends in `b`.

* `aPb := (p(a,b) != {})` - if multiple paths are possible
* `aPb := (p(a,b) in G)` - if only one such path is possible

notational simplifications

* `aPb` may be used to denote `p(a,b)`
* possible use - `(p in aPb)`

Note that edge-based terms can be used in the context of a path:

* given a path `p := (a,..,b)` such that `(p in P)`
* `a` and `b` are both endpoints of `p`
* `a` is a source vertext to `p`
* `b` is a sink vertex to `p`
* `p` begins in `a` and ends in `b`
* `p` has `a` as its source and `b` as its sink vertex

<!-- ======================================================================= -->
## connected, disconnected

A vertex can be described as being **connected**, if it is an endpoint to one
or more edges. Conversely, a vertex can be described as being **disconnected**
or **isolated**, if is no endpoint to any edge.

* `(is-connected v) := (v in VI) or (v in VO)`
* `(is-disconnected v), (is-isolated v) := not (is-connected)`

Two vertices in a graph can be described as being **connected with** each other,
if a path can be formed that has both vertices as its endpoints.

* `(a connected-with b) := aPb and/or bPa`

Note that different levels of connectivity can be defined based on whether the
corresponding path is a path over the directed graph, or a path over the graph's
underlying undriected graph. The focus of this discussion in that regards is on
vertices that are not disconnected.

<!-- ======================================================================= -->
## the length of a path

Given a path `p := (v1,..,vk)`, its length `#p` can be defined as below.

A hop/pair/edge-based view: `#p := (k-1)`

* `#p` is the number of consecutive pairs in `p`
* as such, `#p` will be referred to as the edge-length of `p`

A vertex-based view: `#p := k` (default)

* as such, `#p` is the number of components in `p`
* as such, `#p` will be referred to as the vertex-length of `p`

Note that the default point of view is on the vertex-length of a path. As such
`#p` corresponds with the cardinality of the path's sequence of vertices.

Note that a path may in general have any (even infinite) length. However, in
the context of this discussion, all paths are assumed to have finite length.

<!-- ======================================================================= -->
## distance between vertices

In a graph `G := (V,E)`, "the distance between two vertices" `a` and `b` is
the edge-length of the shortest possible path `(p in p(a,b))` over the set of
paths in the underlying undirected graph `UG`.

Note that a directed path does not necessarily have to exist.

<!-- ======================================================================= -->
## cyclic vs. acyclic

A directed loopless graph `G := (V,E)` is can be described as **cyclic**, if a
path can be formed that begins and ends in the same vertex.

* `G` is cyclic, if `aPa` is true for any `(a in V)`

A graph can be described as **acyclic**, if no such path exists. A directed
acyclic graph may be referred to as a **dag**.

* `G` is acyclic, if `aPa` is false for all `(a in V)`

A path `(p in P)` can be described as **cyclic**, if it contains any vertex
in it more than once.

* `p` is cyclic, if `(#E(p) < #p)` is true
* `G` is cyclic, if `P` contains a cyclic path

Note that an acyclic graph is also loop-less.
