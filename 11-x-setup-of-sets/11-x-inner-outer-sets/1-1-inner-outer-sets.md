
<!-- ======================================================================= -->
## The inner/outer set of a node

Each node within a tree can be understood to represent the root of a subtree.
Any node can therefore be understood to define two sets of nodes: (1) The outer
set of a node (i.e. S1) contains the node and all of its descendants, and (2)
the inner set of a node (i.e. S2) only contains the descendants of that node.

* A tree's set of nodes is identical to the outer set of its root.
* An outer set always contains its defining node (i.e. never empty).
* An inner set is empty `Ø`, if its defining node is a leaf.
* An inner set is non-empty, if its defining node is a parent.

The relationship between both sets:

* `S1 := ({ node } union S2)`
* S1 is a strict super-set of S2.
* S1 is super-ordinate to S2, and S2 sub-ordinate to S1.
* S1 is the parent (i.e. an ancestor) set of S2.
* S2 is the only child (i.e. a descendant) set of S1.
* note - `(CE(S1) == node)` and `(CSS(S2) == Ø)`

Note that each set can be transformed into the other,
if its defining node is added to (or removed from) the corresponding set.

**CLARIFICATION**
Each node can be understood to contain itself and its descendants.
Put differently, node `n1` contains node `n2`, if ...

1. `n2` is a node in the subtree that has `n1` as its root, or
2. `n1`'s outer set contains `n2` as an element.

<!-- ======================================================================= -->
# relationship between the sets of different nodes

* The inner set of a parent is the union of the outer sets of its child nodes.
* The inner set of a parent is a superset to the outer set of a child.
* The outer set of a child is sub-ordinate to the inner set of its parent.
* Both sets of a descendant are subsets to both sets of an ancestor.
* No set of a descendant contains a node that an ancestor set does not contain.

The above statements should be fairly obvious because any descendant of a node
is also a descendant of the node's ancestors. As such, a descendant is also an
element of both sets of any of the node's ancestors.

* If a parent has one child only, then the parent's inner set is equal to the
  child's outer set. Both sets are strict subsets to the parent's outer set.
* If a parent has more than one child, then the parent's inner set has more
  nodes than any of the outer sets of its child nodes. That is, the outer set
  of any child is a strict subset of the parents's inner set.
* It is the outer sets of its siblings that distinguishes the outer set of a
  child from the inner set of its parent.

Note that the outer set of a node is the set of nodes of the subtree that has
the node as its root (i.e. a tree). In contrary to that, the inner set of a
node is the union of the outer sets of those subtrees that have the node's
child nodes as their root (i.e. a forest).
