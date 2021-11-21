
<!-- ======================================================================= -->
# a recap on tree-based definitions

Note that the following is intended to shift ones focus away from the nodes
the trees contain, towards the relationships that exist between entire trees.
That is, a tree T(N,E) needs to be perceived as a whole - i.e. not a s complex
construct of nodes and edges.

Recall that, if two graphs have a shared edge, then both graphs must also have
both of the endpoints of that edge in common. Because of that, if two graphs
have intersecting sets of edges, then both graphs also have intersecting sets
of vertices. However, two graphs with intersecting sets of vertices do not
necessarily also have intersecting sets of edges.

<!-- ======================================================================= -->
## tree-based definitions

Tree A is **disjoint** (DI) to tree B,
if both have disjoint sets of nodes and disjoint sets of edges.

* `(A disjoint-to B) := (N(A) disjoint-to N(B))`

Note that the requirement of having disjoint sets of nodes implicitly also
ensures that both graphs also have disjoint sets of edges.

Tree A is **equal** (EQ) to tree B,
if both have equal sets of nodes and equal sets of edges.

* `(A == B), (A equal-to B) := (N(A) == N(B)) and (E(A) == E(B))`

Tree A is **distinct** (NEQ) to tree B,
if both are un-equal.

* `(A != B), (A distinct-to B) := not (A == B)`

Note that, since each tree must have a root, **empty** trees do not exist.
That is because the graph of a tree will always have a root node as a vertex
(i.e. a non-empty set of nodes).

<!-- ======================================================================= -->
## related trees

Tree A is **coupled-with** (CW) tree B,
if both trees have one or more nodes and/or edges in common.

* `(A coupled-with B) := not (A disjoint-to B)`

Tree A is a **(simple) sub-tree** (SUB) of tree B,
if B contains all the nodes and all the edges in A.

* `(A subtree-of B) := (N(A) subset-of N(B)) and (E(A) subset-of E(B))`
* note - trees A and B may be equal

Tree A is a **(simple) super-tree** (SUP) of tree B,
if A contains all the nodes and all the edges in B.

* `(A supertree-of B) := (B subtree-of A)`

Tree A is **related** (RE) to tree B,
if one is a subtree of the other.

* `(A related-to B) := (A subtree-of B) or (B subtree-of A)`

Tree A is **un-related** to tree B,
if none is a subtree of the other.

* `(A unrelated-to B) := not (A related-to B)`

Tree A is a **proper subtree** (PSUB) of tree B,
if both trees are distinct, and if A is a subtree of B.

* `(A proper-subtree-of B) := (A SUB B) and (A != B)`

Tree A is a **proper supertree** (PSUP) of tree B,
if both trees are distinct, and if A is a supertree of B.

* `(A proper-supertree-of B) := (A SUP B) and (A != B)`

Tree A is **properly related** (PRE) to tree B,
if one is a poper subtree of the other.

* `(A properly-related-to B) := (A PSUB B) or (A PSUP B)`

Tree A **overlaps** (OV) tree B,
if both trees are coupled-with, but not related-to each other.

* `(A overlaps B) := (A coupled-with B) and (A unrelated-to B)`
* note - none is a subtree of the other

<!-- ======================================================================= -->
## tree-based operations

Graph C is the **union** of trees A and B,
if it contains all of the nodes and all of the edges in A and B.

* `(A + B), (A or B), (A union B) := (N(A) + N(B), E(A) + E(B))`

Graph C is the **intersection** of trees A and B,
if its set of nodes and its set of edges are the
intersections of the corresponding set in both trees.

* `(A & B), (A and B), := (N(A) & N(B), E(A) & E(B))`

Graph C is the **(simple) difference** of trees A and B,
if all the nodes and all the edges in B are removed from A.

* `(A \ B), (A diff B) := (N(A) \ N(B), E(A) \ E(B))`

Graph C is the **symmetric difference** of trees A and B,
if its set of vertices and its set of edges are formed as the
symmetric difference of the corresponding sets in both trees.

* `(A ^ B), (A xor B) := (N(A) xor N(B), E(A) xor E(B))`

Note that the removal of a vertex from a graph must implicit also remove all of
the edges to which that vertex is an endpoint. Because of that, the simple and
the symmetric difference graph may have fewer edges that what would directly
result from the removal of second input tree.

Note that the resulting graph of the above operations is not necessarily a
tree. That is because the input trees have thus far no requirements. That is,
the ancestor of a node in one tree may (e.g.) be a descendant of that node
in the other tree. Despite that, and in the context of this discussion, input
trees will in general be related in some way - e.g. tree B will in general
be an incuded subtree of tree A.
