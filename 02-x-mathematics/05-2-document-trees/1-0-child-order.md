
<!-- ======================================================================= -->
# child order

Any node tree `T(N,E)` is defined as a tuple of a simple set of nodes `N` and
a simple set of edges `E`. Also, any parent node `p` in a tree can be described
as being associated with a simple set of child nodes `c(p)` which can be derived
from the tree's set of edges `E`.

* `c(p) := { c | pEc }`

Defined as such, node trees do not support the notion of a child order. That
is because the endo-relation of a tree does not provide the means to define
such an order. Consequently, each child node in a tree appears to be equally
relevant to its parent since there is no means to tell which is child first
and which is last.

<!-- ======================================================================= -->
## binary trees

A binary tree is such that each node has no more than two child nodes. As such,
binary trees can be used to test if a particular expression (e.g. `(1 : 2) = 3`)
evaluates to true or not.

```
(=) --|-> (:) --|-> 1
      |         |-> 2
      |-> 3
```

One can therefore tell that the implementation of a binary tree must allow
to distninguish between both child nodes. After all, the order of operands is
relevant since the division of numbers (:) is not commutative. That is, the
1st operand must be divided by the 2nd operand, not vice versa.

Each node in a binary tree is therefore defined such that each node in it may
have a left child and a right child. As such, a binary tree is a tree that has
a child order associated with it. That is, one can tell which of the child
nodes is the 1st/left child, and which is the 2nd/right child.

Note that the above can be understood to suggest that the concept of a child
order is not purely fictional. Furthermore it proofs that this concept is not
just required due to limited memory.

<!-- ======================================================================= -->
## plane trees

Similar to binary trees, generic trees can be used to hold content of some sort.
These trees allow each node to have any number of child nodes. And since each
node is used to hold some portion of the content in question, an order over
the child nodes in a generic tree is in general required. Because of that, each
parent node is understood to have a first child `cF` and a last child `cL`.

```
    p       equiv       |--> cF
---------    <=>    p --|--> ..
cF ... cL               |--> cL
```

Such trees are therefore in general drawn onto a 2-dimenensional plane with its
root at the top and any parent node above its child nodes. In addition to that,
the child nodes of a parent are drawn in a left-to-right order, beginning with
the 1st child `cF` (leftmost) and ending with the last child `cL` (rightmost).
As such, the child order of a tree is embedded into the 2-dimensional plane,
external to the tree's endo-relation.

<!-- ======================================================================= -->
## serialized trees

Similar to the above, the process of writing a node tree to some memory must,
one way or another, write the elements in a tree (its nodes and edges) in some
particular order. Because of that, even a tree that is serialized into memory
can always be understood to be associated with some child order.

Note however that it depends on a given context, if that order is considered
relevant or not. Put differently, if a tree, that has no child order associated
with it, is read from memory, then the child order read from its serialized
data can and should in general be discarded.

<!-- ======================================================================= -->
## implicit vs. explicit child order

In cases where a child order is defined based on dedicated child nodes (such
as in binary trees), or based on a plane tree (such as a document tree), the
corresponding child order can be described as **explicit** or **persistent**.

If, in contrary to that, the child order is a mere consequence of our inability
to write trees with no child order whatsoever, then the corresponding child
order can be described as **implicit** or **temporary**.

Note that the latter includes those orders that result from randomly iterating
over the nodes of a tree that has no explicit child order associated with it.
That is because such a temporary order must be understood to have no further
meaning.
