
<!-- ======================================================================= -->
# document tree

A node tree that is used to hold content of some sort, will be described
as **a document tree** (or simply as **doctree**).

That is because the nodes within a document tree are not mainly used to represent
globally unique elements such as numeric values. Instead, each node within a
document tree is used to hold a specific portion of some content.

Despite that, one can describe each portion of content as unique to the overall
content since it can always be associated with its placement within the content,
regardless of the actual portion of content each node holds. Due to the placement
of each node, a document tree is in general associated with a child order.

Defined as such, a document tree is distinct from other trees such as binary
search trees (e.g. AVL trees), which are used as searchable collections of
elements that have no particular placement associated with them.

<!-- ======================================================================= -->
## tree order

Note that the node order of a tree is commonly referred to as **the tree order**
of some known tree and used to denote the top-down order between the nodes in
it (i.e. descendants are subsequent to ancestors). Because of that, this
description is more or less one that that focuses on the visual representation
of a tree, and not so much on the underlying partial order.

Also, the description of "tree order" seems a bit misleading since the
corresponding order is no order of trees, but an order of nodes. That is,
referring to some "tree order" is like referring to "an ordered set of trees".

<!-- ======================================================================= -->
## unordered document tree

One can refer to the abstract endo-relation of a document tree as
**the unordered document tree** for reasons that should be obvious by now:
it has no child order. As such, this description can also be used to refer
to the node order of the (unordered) node tree that is associated with a
document tree.

Note that the description as "unordered document tree" in regards to the
document tree's node order is synonymous to "tree order".

<!-- ======================================================================= -->
## ordered document tree

For reasons that will become obvious in the course of subsequent discussions,
the child order of a document tree can and must be explicitly embedded into
the document tree's abstract node order.

Since this embedding is a partial extension of the unordered document tree's
node order, the resulting modified node tree and therefore also the resulting
modified node order can be referred to as **the ordered document tree**.

That is, the description "ordered document tree" will be used to refer to the
node tree/order that results from explicitly embedding a child order into a
document tree.

Note that any document tree is in general always associated with a child order.
From that point of view, no distinction between "ordered" and "unordered" is
required. Because of that, this distinction can and should be used to denote
whether or not the child order has been embedded into the corresponding node
tree/order. With that in mine, one can see the modified description to provide
the means to be more clear.

<!-- ======================================================================= -->
## "ordered tree" vs. "unordered" tree - meh (!)

A node tree that is associated with a child order is commonly described as
an **ordered tree**. That is, an "ordered tree" is in general understood to
consists of an endo-relation for which an external child order is provided.

In contrary to that, a node tree that is only defined by an endo-relation,
is commonly described as an **unordered tree**. That is, no child order
(hence "unordered") is associated with it.

However, even though one can in general associate some child order with a node
tree, one always needs to keep in mind that, from a mathematical perspective,
a node tree still has no child order since the underlying endo-relation does
not embed that order. Because of that, even an "ordered tree" still is just
another "unordered tree".

Consequently, the distinction between "ordered tree" and "unordered tree" makes
no difference in the context of an abstract node tree. That is because it has
no child order either way.