
<!-- ======================================================================= -->
# child order

Any node tree `T := (N,E)` is defined to have a simple set of nodes `N` and a
simple set of edges `E`. Also, any parent node `p` in a tree can be said to be
associated with a simple set of child nodes `c(p)` that can be dreived from
the tree's set of edges `E`.

Defined as such, node trees do not support the notion of an order over child
nodes. That is because the endo-relation of a node tree does not provide the
means to define such a child order. Consequently, each child node appears to
be equally relevant to its parent node since there is no means to tell which
child node is first and which is last.

<!-- ======================================================================= -->
## binary trees

A binary tree is such that each node has no more than two child nodes. As such,
binary trees can be used to test if a particular mathematical expression like
`(1 : 2) = 3` evaluates to true or not.

```
(=) --|-> (:) --|-> 1
      |         |-> 2
      |-> 3
```

One can therefore tell that a binary tree must allow to distninguish between
both child nodes. After all, the order of operands is relevant since the
division of numbers (:) is not commutative - the 1st operand must be divided
by the 2nd operand, not vice versa.

Each node within a binary tree is therefore defined such that each node in it
may have a left child and a right child. As such, a binary tree is a tree that
has a child order associated with it. That is, one can tell which of the child
nodes is the 1st/left child and which is the 2nd/right child.

<!-- ======================================================================= -->
## plane trees

Similar to binary trees, generic trees can be used to hold content of some sort.
These trees allow each node to have any number of child nodes. And since each
node is used to hold some portion of the content in question, an order over the
child nodes within a generic tree is in general required. Because of that, each
parent node is understood to have a first child `cF` and a last child `cL`.

```
     p
     |
-----------
|   ...   |
cF        cL
```

Such trees are therefore in general drawn onto a 2-dimenensional plane with its
root at the top and any other parent node above its child nodes. In addition
to that, the child nodes of a parent node are drawn in a left-to-right order,
beginning with the 1st child `cF` (leftmost) and ending with the last child
`cL` (rightmost). As such, the child order of each parent is embedded into the
2-dimensional plane.

<!-- ======================================================================= -->
## serialized trees

Similar to the above, the process of writing a node tree to some memory must,
one way or another, write the tree's elements (i.e. the nodes and edges) in
some particular order. Because of that, even a tree that is serialized into
memory can always be understood to be associated with some child order.

Note however that it depends on a given context, if that order is considered
relevant or not. Put differently, if a tree that has no child order associated
with is read from memory, then the child order used to serialize the tree can
and sometimes even must be discarded.

<!-- ======================================================================= -->
## implicit vs. explicit child order

In cases where a child order is defined based upon dedicated child nodes (such
as in binary trees), or based upon a plane tree (such as a document tree),
the corresponding child order can be described as being **explicit**.

If, in contrary to that, the child order is a mere consequence of our inability
to truly read/write trees that have no such child order, then the corresponding
child order can be described as being **implicit** or **temporary**.

Note that the latter includes those orders that result from randomly iterating
over the child nodes of a tree that has no such child order. That is because
such a temporary order must be understood to have no further meaning.
