
<!-- ======================================================================= -->
# general remarks

Note that **a directed multigraph** is a graph such that the set of edges `E` is
a possibly empty multiset of edges. However, in the context of this discussion,
`E` is always a simple set of edges. That is, excluding loops, each edge may
appear no more than once.

Note that a directed graph that is **symmetric** has a "flipped" counterpart
for each of its edges. Despite that, a symmetric graph is strictly speaking
still no undirected graph. However, depending on a particular context, one
can treat a pair of "flipped" edges a being equivalent to an undirected edge.

Note that `xEx` may be true for any vertex in a graph. That is, edges may in
general exist that begin and end in the same vertex `x`. These kind of edges
are in general referred to as "loops", or as "reflexive edges". Because of
that, a graph with no such edges may be referred to as being **loop-less**,
or as being "irreflexive".

Note that for each directed graph `G := (V,E)`, an undirected graph `UG := (V,A)`
can be formed such that `({x,y} in A)` if `xEy`. That is, for each edge
`((x,y) in G)`, `A` contains an arc `{x,y}`. (Note that two distinct edges may
correspond with the same arc - i.e. `xEy` and `yEx`). An undirected graph formed
this way will be referred to as the **underlying undirected/simple graph** `UG(G)`
of the corresponding directed graph `G`.

Note that for each undirected graph `G := (V,A)`, a directed graph `DG := (V,E)`
can be formed such that `((x,y) in E)` if `xAy`. That is, for each arc
`({x,y} in A)`, `E` may contain `(x,y)` and/or `(y,x)`. If each arc corresponds
with one edge only, then the directed graph may be described to as an
**orientation** of the undirected graph. In contrary to "UG(G)", an undirected
graph may in general have several distinct orientations.

<!-- ======================================================================= -->
## components

A graph `G := (V,E)` can be described as being **connected**, any pair of
vertices are connected with each other in the graph's underlying undirected
graph. That is, an undirected path `(p in UP)` exists for any pair of vertices
`(a,b in V)` such that `aUPb` is true.

A graph that is connected consists one **component** only.

Note that a graph that has no disconnected vertex is not necessarily connected
since such a graph may consist of more than one component. However, such a
graph can not have any trivial component (i.e. every component in it has two
or more vertices).

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
