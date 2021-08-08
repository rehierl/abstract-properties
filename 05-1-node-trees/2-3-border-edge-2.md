
<!-- ======================================================================= -->
# the border graphs of (induced) subtrees

Note that the overall focus is on subtrees of trees. The considerations below
are therefore non-substantial to the overall discussion. The following must
therefore be understood as an attempt to provide a more general perspective.

* possibly not complete, possibly outdated

<!-- ======================================================================= -->
## subtree S of super-graph G

The following assumes the super-graph `G := (V,E)` of subtree `S := (M,F)`
to be a connected, non-tree graph.

Note that the semantics of a subgraph is by definition equivalent to the
semantics of its super-graph. Because of that, the question arises how the
semantics of `S` could result in `S` being a tree, but the very same semantics
allowing `G` to be a non-tree graph? As the content below will not attempt
to answer that question, the following needs to be understood from a purely
theoretical (i.e. structural/syntactical) perspective.

**main considerations**

Recall that the focus is on the component in `G` to which `S` is a subtree.
That is because the edges of any other component in `G` can not be edges in
`S` or in the border graphs between the two. Hence, these edges are outside
of the scope of the following discussion and will therefore be ignored.

Another consequence of the that case (i.e. `G` is a non-tree graph) is that
`G` needs to satisfy one or more of the following conditions. That is because
`G` would otherwise be a tree.

1. All vertices in `G` have at least one incoming edge (i.e. no root)
2. `G` has several vertices with no incoming edge (i.e. more than one root)
3. `G` has vertices with more than one incoming edge (i.e. more than one parent)

Note that (3) does not necessarily result in (directed) cycles. That is because
a root vertex may have an alternative downward oriented path to one of its
descendants. However, `UG(G)` (i.e. the underlying undirected graph of `G`)
will have (undirected) cycles, if even one such vertex exists in `G`.

Note that, due to the above conditions, `S` can not be equal to `G` since `G`
is required to be a non-tree graph. That is, `S` and `G` are distinct graphs,
which is why `S` has to be a proper subtree of `G`.

**overview of case-1 and case-2**

In regards to a non-tree graph `G`, two cases may be distinguished:
(1) `S` is equal to the subgraph `I`, induced in `G` by the set
of vertices in `S` (i.e. `(S == I)` where `I := G[V(S)]`), and
(2) `S` is a proper subtree of `I`.

In case-1, the inner border graph between `S` and `G` is empty (i.e.
`(IBG == Ø)`). That is because `S` will, due to being induced by its set
of vertices `V(S)`, contain all the edges in `I`. The focus of case-1 is
therefore on the set of edges in `B`, which contains those edges in `G`
that are not in `S` (i.e. `B := ((G \ S) + OBG)`).

Note that `(G \ S)` contains all those edges that are not incident to a node
in `S`. In contrary to that, `OBG` contains those edges that are incident to
a node in `S`. And because `G` is connected and `S` a proper subtree of `G`,
the outer border graph between the two is non-empty (i.e. `(OBG != Ø)`).

In case-2, the inner border graph is non-empty (i.e. `(IBG != Ø)`). In contrary
to that, the outer border graph between the two is not necessarily empty (i.e.
`(OBG <=!=> Ø)`). The focus of case-2 is therefore on the edges in `I` that
are no edges in `S`.

**in regards to "generic subtrees"**

The generic method used to define subtrees (i.e. `subtreeOf(T,r,LS)`) requires
`T` to be a tree. That is because, in a connected non-tree graph, several paths
may in general be formed that allow to reach a leaf in `LS` beginning with the
subtree's root `r`. Because of that, there is no means to decide which path to
take in order to reach a given leaf in `LS`. Consequently, this generic method
does not allow to uniquely define a subtree in a non-tree graph.

<!-- ======================================================================= -->
## subtree S of super-graph G: case-1, (OBG != Ø)

Graph `G := (V,E)` is the connected non-tree super-graph of the proper subtree
`S := (M,F)` such that `(S == G[V(S)])` is true. Hence, the reason for `G` not
being a tree is due to the edges in `B := ((G \ S) + OBG)`.

Note that `(IBG == Ø)` and `(OBG != Ø)`. The focus of this case is therefore
on the edges in `OBG` (i.e. those in `G` but not in `S` and incident to a node
in `S`).

Note that, because `S` must be a proper subtree of `G`, `S` can not be induced
by all the elements of the corresponding set in `G`. That is, `S` is distinct
from `G[V]` and `G[E]`.

Note that `(S == G[M])` and `(S == G[F])` are due to`(IBG == Ø)` both true.
Hence, `S` may be induced by its set of nodes, or its set of edges. Because of
that, a distinction between those two is in that particular case not required.

**edges in OBG**

Every node in `S`, including its leaf nodes, may be adjacent to a vertex in
`(G \ S)` such that the corresponding edge `e` is incoming in regards to the
node in `S` (i.e. the node in `S` is the sink of `e`).

Likewise, every node in `S`, including its root node, may be adjacent to
a vertex in `(G \ S)` such that the corresponding edge `e` is outgoing in
regards to the node in `S` (i.e. the node in `S` is the source of `e`).

Consequently, `S` may be a source, a sink or even internal in regards to `G`.
As such, the edges in `B` do in general not allow to uniquely determine the
relationship between `G` and `S`.

<!-- ======================================================================= -->
## subtree S of super-graph G: case-2, (IBG != Ø)

Graph `G := (V,E)` is the connected non-tree super-graph of the proper subtree
`S := (M,F)` such that `(S != G[V(S)])` is true. Hence, the reason for `G` not
being a tree is due to the edges in `I`, and possibly also due to those edges
in `B := ((G \ S) + OBG)`.

Note that `(IBG != Ø)` and `(OBG <=!=> Ø)`. The focus of this case is therefore
on the edges in `I := G[V(S)]` that are no edge in `S`.

**induced by a subset of vertices - i.e. G(M)**

In this particular case, `S` can not be a subtree that is induced by a set of
vertices (i.e. `(S != G[M])`). That is because `S` would then also contain all
the edges in `IBG`, which would turn `S` into a non-tree graph.

Consequently, `S` must be induced by its set of edges (i.e. `(S == G[F])`).

**induced by a subset of edges - i.e. G(F)**

As mentioned before, the edges in `IBG` do not allow to clarify the relationship
between `G` and `S` because each edge can be understood to be oriented from one
graph to the other. Because of that, these edges need to be avoided.

In addition to `(IBG != Ø)`, the outer border graph may aso be non-empty
(i.e. `(OBG != Ø)` may be true). Therefore, case-1 still in regards to
those edges in `OBG`.
