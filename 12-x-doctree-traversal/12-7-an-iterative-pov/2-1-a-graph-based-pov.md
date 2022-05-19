
<!-- ======================================================================= -->
# an order-based point-of-view

Recall that the additional child orders embedded will not produce a conflict
with the tree order of the ordered document tree. That is, the resulting
trace will be overall order-preserving - i.e. in regards to the document
tree's tree order and its child order.

The question is therefore, if the resulting trace of the iterative process
(defined by option-1) can in general produce the pre-order traversal of the
source tree.

<!-- ======================================================================= -->
## arbitrary, binary*, unary

```
  step-0        step-1   step-2   step-3
| =========== | ====== | ====== | ====== |
| n           | n      | n      | n      |
| |----->|    | c1     | c1     | c1     |
| c1    c2    | |-->|  | d1     | d1     |
| |-->| |-->| | d1 c2  | |-->|  | d2     |
| d1 d2 d3 d4 | d2 d3  | d2 c2  | c2     |
|             |    d4  |    d3  | d3     |
|             |        |    d4  | d4     |
|             |        |        |        |
|-arbitrary---|-binary-|-binary-|-unary--|
```

Recall that the ordered document tree is formed by embedding the document
tree's child order into the unordered document tree (an **arbitrary tree**).
Furthermore, this order embedding is guaranteed to produce a node tree such
that each node in it has no more than two child nodes (a **binary tree**),
its former first child, and its former next sibling.

* arbitrary tree => binary tree

Since the iterative process formes a child order based on the tree of the
previous step, and since that child order is embedded into that tree, the
overall process can be described to transform one ordered document tree
into another, until each node in the resulting tree has no more than one
child (an **unary tree** - i.e. a path graph).

* arbitrary tree => binary tree => .. => binary tree => unary tree

Note that the overall process is guaranteed to end since the embedding of
a child order will produce a tree whose root has no more than one child.

Note that the embedding of a child order is such that **a parent** in the
source tree is **guaranteed to have a first/left child** in the resulting
tree. In contrary to that, such a parent may or may not end up with a
second/right child. That is, the left/right descriptions have no additional
meaning as in a binary search tree.

<!-- ======================================================================= -->
## binary*, unary

The following will focus on the effects of embedding a child order into the
node order of a binary tree, which is the result of a pervious child order
embedding.

parent nodes
- a first child parent will be a parent of two - if there is a second child
- a first child parent will be a parent of one -

leaf nodes
- a first child leaf will become a parent
- a second child leaf will remain a leaf - a point of no return
- a second child will may eventually become a first child leaf

<!-- ======================================================================= -->

- in between any node and its next subsequent
  sibling will be its descendants

a matter of recursion
- the pre-order traversal of each intermediate tree
