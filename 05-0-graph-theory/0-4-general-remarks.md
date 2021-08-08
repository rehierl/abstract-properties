
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
