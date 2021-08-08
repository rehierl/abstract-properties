
<!-- ======================================================================= -->
# paths of vertices

Note that, in the context of this discussion, and unless specified otherwise,
all paths are required to be uni-directional and oriented according to the
edges of a graph.

<!-- ======================================================================= -->
## paths over a graph

An **undirected path** over a graph `G := (V,A)` is a sequence of vertices
`p := (v1,...,vk)` such that `(p in ×V{k})` - i.e. `(vi in V)`. In addition
to that, any pair of consecutive vertices in `p` represents an arc in `A`.
that is, `({vi,vi+1} in A)` is required to be true.

A **directed path** over a graph `G := (V,E)` is a sequence of vertices
`p := (v1,...,vk)` such that `(p in ×V{k})` - i.e. `(vi in V)`. In addition
to that, any pair of consecutive vertices in `p` represents an edge in `E`.
That is, `((vi,vi+1) in E)` is requried to be true.

Defined as such, a path can be described as **a sequence of adjacent vertices**.
Because of that, all definitions for sequences can be used in combination
with paths - e.g. subsequence-of, substring-of, prefix-of.

Note that, because a (directed) graph is defined as an endo-relation,
a (directed) path may also be referred to as "a path over a graph",
or as "a path over the relation of a graph".

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
## direction/orientation

( Note that the intention of the following subsection must be understood to
be in regards to consistently oriented semantics. )

With each edge `(e in E)` in a graph `G := (V,E)`, a statement (i.e. meaning,
aka. semantics) is associated. Since the vertices of an edge are understood
to be un-equal, the edges of a graph in general support a notion of
**direction** and/or **orientation**.

However, that sense of orientation is broken, if two vertices are connected
in both ways (i.e. `aPb` and `bPa`). Because of that, and in order for a graph
to have a strict orientation, a graph must be acyclic. (Note that each acyclic
graph is by definition an oriented graph, but not necessarily vice versa).

With that in mind, any directed path `p=(v1,v2,...)` over an (acyclic) graph
`G` can be described as **uni-directional**, if `((vi,vi+1) in E)` for all
pairs of consecutive vertices.

An uni-directional path may be referred to as **consistent with** (or as
**in the direction of**) `G`, if each pair `(vi,vi+1)` is an edge in `E`.
In contrary to that, a path may be referred to as being uni-directional but **inverted** (or **converse**), if each pair `(vi,vi+1)` represents an edge
in the inverted (aka. converse) graph - i.e. `(e in conv(G))`.

A path may be referred to as being **multi-directional**, if it contains pairs
of consecutive vertices such that `(vi,vi+1)` and/or `(vi+1,vi)` in `G`. Put
differently, if a path contains pairs in `G` and `conv(G)`.

Note that an uni-directional path (converse or not) may be said to have one
direction only. In contrary to that, a multi-directional path has no consistent
orientation.

In general: A multi-directional path `(p in ×V{k})` is a sequence of vertices
`p := (v1,...,vk)` such that `(vi covered-by vi+1)` for `(i in [1,#p-1])`.

Example: In a tree of nodes `T := (N,E)`, a multi-directional path of length
3 connects a child `c`, over its parent `n`, with one of its siblings `s`.
Hence, if such paths are allowed, then `c` and `s` are connected via a path
`p(c,s) := (c,n,s)` such that `((c,n) in conv(E))` and `((n,s) in E)`.

<!-- ======================================================================= -->
## set of paths P

The following is an inductive definition of **the set of all possible paths**
`P` that can be formed based on the edges of a graph `G := (V,E)`:

(1) `P1 := { (v in V) }`

That is, `P1` only contains all trivial paths `p := (v)` (i.e. `(#p == 1)`).

(2) `P2 := { (a × b) | (a in P1), (b in V), ((a[#a],b) in E) }`

That is, `P2` holds all paths of vertex-length 2.
Hence, `P2` is identical to the set of edges `E`.
Note that `a[#a]` denotes the last vertex in path `a`.

(i) `Pi := { (a × b) | (a in P(i-1)), (b in V), ((a[#a],b) in E) }`

That is, the next set of paths `Pi` for `(i > 1)` is formed from the previous
set of paths `P(i-1)` by concatenating all those vertices `b` to each path `a`
in `P(i-1)`, if there is an edge `( (a[#a],b) in E )`.

* `P := P1 + ... + P(i-1) + Pi` for `(i in [1,*])`
* `P := (union-of Pi)` for all `(i in [1,*])`
* note - `(E subset-of P)` since `(E == P2)`

Based on the above, each graph `G` can be understood to be associated with the
set of all possible paths `P` that can be formed over its edges. A graph can
thus be described as a triplet of sets: `G := (V,E,P)`.

Note that any path in `(P0 + P1)` may be referred to a **degenerated path**.
That is, because such a path does not contain any consecutive pair of vertices.

Note that, if a discussion is in regards to multiple graphs, a specific set
of paths `P` may be clarified as `P[E]` or `P[G]`, which needs to be read as
"the set of paths `P`, induced by the set of edges `E` in graph `G`".

Note that a finite graph, that has loops and/or cycles, allows to form an
infinite number of paths. That is, the graph's set of paths `P` has infinitely
many elements. The set of paths `P` therefore has finite size, if and only
if the corresponding graph is acyclic.

<!-- ======================================================================= -->
## in, contains

A sequence of vertices can be understood to represent a (valid) path `p` over
graph `G`, if `p` is an element of the graph's set of paths `P`. In such a case,
graph `G` is understood to contain path `p`.

* `(p in P), (p in G)` := `p` is a path over the edges in `G`

<!-- ======================================================================= -->
## p(a,b)

A selector function `p(a,b)` can be defined such that, for a given pair of
vertices `(a,b)` it returns the set of all paths that can be formed over the
edges `E` in regards to a particular graph `G`. That is, `p(a,b)` is understood
to return all the valid paths that begin in `a` and end in `b`.

* `(p: V×V -> P(P) )` where `P(P)` denotes the powerset over `P`
* `p(a,b) := { p | (p := (a,...,b)) and (p in G) }`

Note that, in cases where a graph has exactly one such path for any pair of
vertices `(a,b in V)`, `p(a,b)` can be understood to be defined to return a
single path `p := (a,...,b)` rather than a set of paths. That is, `p()` is
understood to be defined as `(p: V×V -> P)`.

The above selector function `p(a,b)` can be understood to be extended such
that a set of end-vertices is supported. That is, `p(a,B)` is understood to
return a set of paths such that any path in it begins in `a` and ends in any
of the vertices within the vertex set `B`.

* `(p: V×P(V) -> P(P) )`
* `p(a,B) := { p(a,b) | (p in G) for all (b in B) }`
