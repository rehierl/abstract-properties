
<!-- ======================================================================= -->
# child order

A node tree `T(N,E)` is defined as a tuple of a simple set of nodes `N` and
a simple set of edges `E`. Based on that, any parent `p` can be said to be
associated with a simple set of child nodes `c(p)` that can be derived from
the tree's set of edges `E`.

* `c(p) := { c | pEc }`

Due to the above, the mathematical definition of a node tree does not support
the notion of a child order. That is because the endo-relation of a tree does
not provide the means to define such an order. Consequently, each child node
in a tree appears to be equally relevant to its parent since there is no means
to tell which is child first and which is last.

<!-- ======================================================================= -->
## expression trees

Expression trees can be used to represent arithmetic expressions such as. In
addition to that, an expression tree can be used to recreate (as a sequence
of characters) and to evaluate the expression it holds.

```
(a : b) = c
===================
(=) -|-> (:) -|-> a
     |-> c    |-> b
```

One can therefore tell that the implementation of an expression tree must
allow to distninguish between child nodes. After all, the order of operands
is relevant since the division of numbers (:) is not commutative. That is,
the 1-st operand must be divided by the 2-nd operand, not vice versa. Hence,
an expression tree is such that it has a child order associated with it.

Note that expression trees suggest that the concept of a child order, even
though not (directly) supported by the formal definition of a tree, is not
just required due to limited memory.

<!-- ======================================================================= -->
## plane trees

Similar to binary trees, generic trees (which allow a parent to have any number
of child nodes) can be used to hold content of some sort. And since a node is
used to hold some portion of the content in question, an order over the child
nodes can be concluded to exist. Because of that, each parent is understood
to have a first child `cF` and a last child `cL`.

```
    p       equiv      |-> cF
---------    <=>    p -|-> ..
cF ... cL              |-> cL
```

A plane tree is in general drawn onto a 2-dimenensional plane with its root at
the top, and any parent node above its child nodes. In addition to that, the
child nodes of a parent are drawn in a left-to-right order, beginning with
the 1st child `cF` (leftmost) and ending with the last child `cL` (rightmost).
As such, the child order of a tree is embedded into the 2-dimensional plane,
external to the tree's endo-relation.

<!-- ======================================================================= -->
## serialized trees

Similar to the above, the process of writing a node tree to memory must, one
way or another, write the elements in a tree (e.g. its nodes) in some order.
Because of that, even a tree that is serialized into memory can always be
understood to be associated with some child order.

However it depends on a given context, if that order is considered relevant
or not. That is, the child order embedded into a serialized tree may or may
not be relevant to the tree.

<!-- ======================================================================= -->
## implicit vs. explicit child order

In cases where a child order is defined based on dedicated child nodes (e.g.
the left child and the right child of a parent in a binary tree), or based on
a plane tree (e.g. a document tree), the corresponding child order can be
described as **explicit** or **persistent**.

If, in contrary to that, the child order is a mere consequence of our inability
to write/serialize trees with no child order whatsoever, then the corresponding
child order can be described as **implicit** or **temporary**.

Note that the latter also includes those orders which result from randomly
iterating over the nodes of a tree that has no explicit child order associated
with it. That is because such a temporary order can be said to not be relevant
past the corresponding iteration.
