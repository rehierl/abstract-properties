
<!-- ======================================================================= -->
# a recap on tree-based definitions

Note that the following recap is intended to shift ones focus away from the
nodes the trees contain, towards the relationships that exist between node
trees. That is, a tree T(N,E) needs to be seen as a whole.

Recall that, if two graphs have a shared edge, then both graphs must also have
both of the endpoints of that edge in common. Because of that, if two graphs
have a shared edge, then both graphs also have intersecting sets of vertices.
Consequently, two graphs can not have an edge in common, if their sets of
vertices are disjoint.

<!-- ======================================================================= -->
## tree-based definitions

Tree A is **disjoint** (DI) to tree B,
if both sets of nodes are disjoint.

* `(A disjoint-to B) := (N(A) disjoint-to N(B)) and (E(A) disjoint-to E(B))`
* note - this is the more strict/verbose graph-based definition

Tree A is **equal** (EQ) to tree B,
if both have equal sets of nodes and equal sets of edges.

* `(A == B), (A equal-to B) := (N(A) == N(B) and (E(A) == E(B))`

Tree A is **distinct** (NEQ) to tree B,
if both are un-equal.

* `(A != B), (A distinct-to B) := not (A == B)`

Note that, since each tree must have a root node, an **empty** tree can not
exist since the graph of a tree will always have at least one vertex (i.e.
its root node).

Note that a less strict order-based definition of **disjoint** is possible,
if the definition only requires both trees to have disjoints sets of nodes.
With such a definition, one would treat both trees more like ordered sets
of nodes.

<!-- ======================================================================= -->
## related trees

Tree A is **coupled-with** (CW) tree B,
if both trees have one or more nodes and/or edges in common.

* `(A coupled-with B) := not (A disjoint-to B)`

Tree A is a **(simple) subtree** (SUB) of tree B,
if B contains all the nodes and all the edges in A.

* `(A subtree-of B) := (N(A) subset-of N(B)) and (E(A) subset-of E(B))`

Tree A is a **(simple) supertree** (SUP) of tree B,
if A contains all the nodes and all the edges in B.

* `(A supertree-of B) := (B subtree-of A)`

Tree A is **related** (RE) to tree B,
if one is a subtree of the other.

* `(A related-to B) := (A subtree-of B) or (B subtree-of A)`
* note - both trees may be qual

Tree A is **unrelated** to tree B,
if none is a subtree of the other.

* `(A unrelated-to B) := not (A related-to B)`

Tree A is a **porper subtree** (PSUB) of tree B,
if both are distinct, and if A is a subtree of B.

* `(A proper-subtree-of B) := (A subtree-of B) and (A != B)`

Tree A is a **proper supertree** (PSUP) of tree B,
if both are distinct, and if A is a supertree of B.

* `(A proper-supertree-of B) := (B subtree-of A) and (A != B)`

Tree A is **properly related** (PRE) to tree B,
if one is a poper subtree of the other.

* `(A properly-related-to B) := (A PSUB B) ex-or (A PSUP B)`

Tree A **overlaps** (OV) tree B,
if both are coupled-with, but not related-to each other.

* `(A overlaps B) := (A coupled-with B) and (A unrelated-to B)`
* note - both trees may differ in their sets of edges only
* note - none is a subtree of the other

<!-- ======================================================================= -->
## tree-based operations

Graph C is the **union** of trees A and B,
if it contains all of the nodes and all of the nodes in A and B.

* `(A + B), (A or B), (A union B) := (N(A) + N(B), E(A) + E(B))`

Graph C is the **intersection** of trees A and B,
if its set of nodes and its set of edges are the
intersections of the corresponding set of both trees.

* `(A & B), (A and B), (A isect B) := (N(A) & N(B), E(A) & E(B))`

Graph C is the **difference** of trees A and B,
if all the nodes and edges in B are removed from A.

* `(A \ B), (A diff B) := (N(A) \ N(B), E(A) \ E(B))`

Graph C is the **symmetric difference** of trees A and B,
if its set of vertices and its set of edges are formed as the
symmetric difference of the corresponding sets in A and B.

* `(A ^ B), (A xor B) := (N(A) xor N(B), E(A) xor E(B))`

Note that the removal of a vertex from a graph will trigger the implicit
removal of all the edges to which that vertex is an endpoint.

Note that the resulting graph of the above operations is not necessarily a
node tree. That is because the input trees have no requirements whatsoever.
That is, the ancestor of a node in one tree may (e.g.) be a descendant of the
node in the other tree. Despite that, and in the context of this discussion,
the input trees will in general be related in some way (e.g. tree B will in
general be an incudes subtree of tree A).
