
<!-- ======================================================================= -->
# miscellaneous definitions

<!-- ======================================================================= -->
## isomorphic

Two graphs are **isomorphic** (to each other), if an isomorphism exists that
maps one graph onto the other.

Note that two isomorphic graphs may have different semantics. Because of that,
and in the context of this discussion, "isomorphic" is understood in the sense
of "both graphs have isomorphic structure", whereas "equal" is understood in
the sense of "both represent the exact same graph".

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
* `a` and `b` are connected over `p`
* `p` begins in `a` and ends in `b`
* `p` has `a` as its source and `b` as its sink vertex

<!-- ======================================================================= -->
## distance between vertices

In a graph `G := (V,E)`, "the distance between two vertices" `a` and `b` is
the edge-length of the shortest possible path `(p in p(a,b))` over the set of
paths in the underlying undirected graph `UG`.

Note that a directed path does not necessarily have to exist.

<!-- ======================================================================= -->
## connectivity

A graph `G := (V,E)` can be described as being **connected**, if any pair of
distinct vertices are connected. That is, a path `(p in P)` exists for any
pair of vertices `(a,b in V)` such that `(aPb and/or bPa)` is true.

Note that a connected graph consists of one component only.

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

<!-- ======================================================================= -->
## orientation

Given an undirected graph `UG` an orientation (graph) `G` can be formed, if
each undirected edge is associated with a direction. Put differently, each
undirected edge is replaced by a directed edge. As such, the term "orientation"
refers to a directed graph that was formed based upon an undirected graph.

Note that not every directed graph is an orientation of its underlying
undirected graph (i.e. each directed edge is replaced with an undirected
edge). That is because the directed graph may have pairs of "flipped" edges.

Note that, due to the above definition, and in order to avoid unnecessary
confusion, one should not speak of the orientation of a directed graph (in
regards to the orientation of its edges).
