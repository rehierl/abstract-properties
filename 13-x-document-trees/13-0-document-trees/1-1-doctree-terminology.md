
<!-- ======================================================================= -->
# terminology

Note that the following highlights standard (e.g. tree order) and
non-standard definitions (i.e. unordered/ordered document tree).

<!-- ======================================================================= -->
## tree order

The node order of a tree is commonly referred to as its **tree order**. That is,
the description "tree order" refers to the top-down order between the nodes in
a tree (i.e. ancestors are presequent to descendants). As such, one can treat
that description as referring to the partial order `P(N,<)` of a tree, and thus
as being synonymous to **the node order** of the corresponding tree.

* `P(N,<)` for `T(N,E)`
* `(a < d) := (a ancestor-of d) := aPd`

Note that, since a child is neither an ancestor nor a descendant to any of its
siblings, a "tree order" does not include a child order. Because of that, this
description always treats the corresponding tree as if it had no child order
associated with it.

<!-- ======================================================================= -->
## external vs. embedded/internal child order

Since a tree order does not include a child order, the child order of a tree
(if one exists) must be understood to be **external** to that node order.

Note that one can still embed the child order of a tree into its node order.
After all, any tree can be described as the union of one or more rooted paths,
each of which is an ordered sequence of nodes. However, embedding a child order
into the tree order will obviously modify its node order.

Note that the tree order before embedding the tree's child order will be
described as **the unordered tree/node order**. That is, describing a tree
order as "unordered" denotes that one does associate an child order with it.
In addition to that one clarifies that the child order has not yet been
embedded into the tree's node order. As such, that child order must still be
understood to be **external** to the tree's node order.

In contrary to that, once a child order has been embedded into a tree order,
one can describe the resulting node order as **the ordered tree/node order**.
That is, describing a tree order as "ordered" denotes that one does associate
a particular child order with it. In addition to that one clarifies that the
child order has already been embedded into the node order. As such, that child
order can be understood to be **internal** to the corresponding tree.

Note that, as pointed out above, the node tree that results from embedding a
child order is still such that the resulting node order has itself no child
order. That is, even **an "ordered tree" is still an "unordered tree"**.

<!-- ======================================================================= -->
## document tree

One can define **a document tree** (in short **doctree**) as a tree such that
each node in it can be understood to represent some particular part of some
content. Based on that, one can describe the content of a document tree as
what results from combining the unique bits and pieces each node in it holds.

Furthermore, a document order is associated with some processing order that
defines the order in which the nodes in the document tree must be visited in
order to ensure that different implementations will produce the same results.
Due to that processing order, any document tree can be understood to have a
**child order** associated with it.

Due to the above, one can use the description **unordered doctree** to refer
to the tree order before embedding the doctree's child order. Likewise, one
can use the description **ordered doctree** to refer to the tree order that
results from embedding the child order into it.

<!-- ======================================================================= -->
## document order

Note that the **document order** is a total node order and as such corresponds
with a doctree's trace of nodes. One should neither confuse that description
with the node order of the "unordered doctree", nor with the node order of
the "ordered doctree". The latter two are still partial node orders.

<!-- ======================================================================= -->
## ordered vs. unordered/simple tree

Similar to the description "ordered sequence", one can and should perceive any
tree as **an ordered tree**, if each of its nodes can be understood to refer
to distinct entitites. The focus of that description will therefore be on the
partial order that is associated with any such tree.

As a matter of completeness, and similar to "simple sequence"), one can then
use the description as **an unordered/simple tree** to denote that a tree has
no requriement of "uniqueness" associated with it. That is, the nodes in such
a tree are allowed to represent the same element. Consequently, such a tree
can, strictly speaking, not be understood to correspond with an ordered set.

Note that a binary search tree may in principle hold an item multiple times.
Because of that, a search tree can be understood to have more in common with
a multiset than with an ordered set. Hence the distinction between "unordered"
and "ordered".