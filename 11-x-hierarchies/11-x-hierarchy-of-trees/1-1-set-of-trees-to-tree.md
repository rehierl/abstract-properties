
<!-- ======================================================================= -->
# Hierarchy of trees => Unordered tree

The focus of this discussion is on how to form
a node tree `T := (N,E)` from a hierarchy of subtrees `H := (P,U,G)`.

<!-- ======================================================================= -->
## Simple hierarchy => Unordered tree

```
H: a hierarchy of subtrees            G: node tree
================================  =>  ============
{ A: 1 ,  B: 1 ,  C: 3 ,  D: 4 }           A
    / \      |      / \                   / \
   2   3     2     5   6                 B   C
   |  / \    |                           |
   4 5   6   4                           D
```

Note that labels `A` to `D` are not part of the hierarchy and therefore only
serve as a visual aid intended to support discussions.

Note that the only information available, which can be used to form a tree
based on a simple hierarchy, are the relationships between the trees. That is
because the definition of a simple hierarchy has no requirements in regards
to the elements in `U` (i.e. other than the non-requirement that no tree is
allowed to be empty). Consequently, the resulting tree has one node per tree
`(t in P)`, not one node per element in the union over the sets of nodes of
all trees in `P` (i.e. 4 nodes, not 6).

**CLARIFICATION**
Each (simple) hierarchy of trees `H := (P,U,G)` defines
the structure of a directed unordered tree `T := (N,E)`.

In order to form a tree from such a hierarchy,
the following steps must be executed:

1. Create a node `(ni in N)` for each tree `(ti in P)` (i.e. `(#N == #P)`)
   and associate each tree with the node it represents (i.e. `(ti -> ni)`).
2. If tree `ti` is the parent of `tj`, then node `ni` must be set as the
   parent of `nj` (i.e. `(ti,tj) in G => (ni,nj) in E`).

Even though the relationship of a tree (with all the other trees) is defined
by common elements, the creation of nodes and the association of a tree with a
node is unrelated to these. That is because a simple hierarchy does not allow
to reliably determine which node a tree represents. In general, a hierarchy
only states what relationship a tree has with all the other trees.

Note that ...

* The union graph `U` is unequal to the resulting tree `G`.
* The resulting graph will be a directed graph since the relationship
  a tree has with all the other trees is oriented from a super-ordinate
  tree towards a sub-ordinate tree.
* A tree is no ancestor to itself. That is, the resulting graph has
  one root, no loops and no cycles (i.e. a node tree).
* Each tree either has none ex-or no more than one parent.
* The addition of further nodes to the trees in `P`, without changing
  the relationship a tree has with all the other trees, will not change
  the structure of the resulting tree.

**Memory hook**
What counts is what relationship a tree has with all the other trees. Other
than that, any further characteristics of the trees in `P` need to be ignored
since these can not be relied upon. That is, the elements in `P` need to be
treated as abstract/transparent entities.

<!-- ======================================================================= -->
## missing characteristics

**CLARIFICATION**
Since a simple hierarchy `H := (P,U,G)` has no further characteristics that
could be relied upon when creating the nodes of a tree `T := (N,E)`, a simple
hierarchy only allows to define the structure of a tree. A hierarchy therefore
needs to have further characteristics, specified by the following requirements:

1. `(N subset-of V(U))`:
   Since it must be possible to determine which node a tree represents, the
   nodes of the resulting tree must all be vertices in the union graph `U`.
   That is, each node in `T` must be a node in one or more trees in `P`.
2. `(#P == #N)`:
   Since the structure of the resulting tree is defined by the relationships
   between the trees, there must be a unique tree in `P` for each node in `T`.
3. `node-of: P -> N`:
   Since it must be possible to determine the node of a tree, a method must
   exist that allows to reliably identify the node it represents.

Note that the trees in `P` may in general have any number of nodes
that are no node in `T`. (req-1 does not exclude such nodes).

Note that the above requirements do not strictly require that the node a tree
represents must be a node in that tree. However, if that node is a node in its
tree, then that will provide direct access it. Consequently, selecting the node
a tree represents is then reduced to finding that node within its own set of
nodes (i.e. within itself).

<!-- ======================================================================= -->

**CLARIFICATION**
A hierarchy satisfies all of these requirements,
if the node a tree represents is its own root.

1. `(N subset-of V(U))`:
   That requirement is satisfied since the nodes of each tree in `P`,
   their root nodes included, are all vertices in `U`.
2. `(#P == #N)`:
   `P` contains one tree for each node in `T` since all the nodes in the
   resulting tree are unique. That is because no tree can then have the
   exact same root.
3. `node-of(t) := root-of(t)`:
   That is because the root of a tree is unique to a tree since the root
   of a tree is guaranteed to exist and since that node is the only node
   which has no parent.

Note that the node a tree represents must be the root of that tree since there
is no other option available which can be used to guarantee that the node of
a tree can be reliably identified. That is because no tree is required to have
more than one node, and because every other node in a tree has one and only
one parent.

* each tree in a hierarchy is required to have a distinct root
* the relationships of each tree reflects the relationship of its root
* induced subtrees, induced by their root node
* a hierarchy of induced subtrees
