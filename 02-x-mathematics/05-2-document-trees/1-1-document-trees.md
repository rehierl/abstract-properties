
<!-- ======================================================================= -->
# document tree

A node tree that is used to hold content of some sort, may be clarified as
**a document tree** (in short **a doctree**). That is because the nodes in
it are not used to represent elements such as numeric values, which can be
considered globally unique.

In contrary to general trees, each node in a document tree can be understood
to hold a certain portion of the document tree's overall content. That is,
one can describe the content of a document tree as what results from
combining the bits and pieces of content each node in it holds.

Since one can describe the piece of content in each node as **unique** to the
overall content of a document, one can always associate each bit of content
with its unique placement, regardless of the actual content a node holds.
Based on the placement of each node, each document tree can be understood to
have **a child order** asociated with it.

Defined as such, a document tree is distinct from other trees such as binary
search trees (e.g. AVL trees), which are used as searchable collections of
elements that have no overall placement (i.e. no child order) associated with
them.

<!-- ======================================================================= -->
## tree order

**The node order of a tree** is commonly referred to as its **tree order**.
This description is in general used to refer to the top-down order between
the nodes in it (i.e. ancestors are presequent to their descendants). As such,
one can treat that description as referring to the partial order `P(N,<)` of
a tree, and thus as being synonymous to the underlying order relation.

* `P(N,<)` for `T(N,E)`
* `(a < d) := (a ancestor-of d) := aPd`

Note that, since a child is neither an ancestor nor a descendant to any of its
siblings, a tree order **has no child order**. The description "tree order"
must therefore always be understood as if the corresponding tree had no child
order associated with it.

Note that the **class of tree orders** can be described as a class of partial
orders such that all the orders in it are **downward-total**. That is, any
tree order is a specialized partial order.

<!-- ======================================================================= -->
## unordered document tree

Since the child order of a document tree is by default not understood to be
embedded into its tree order (i.e. not a suborder to the tree's node order,
i.e. still considered to be **external**), a document tree may in general
be referred to as **an undordered document tree**.

Note that any document tree is always associated with a child order. Hence,
the distinction between "ordered" and "unordered" in the sense that a child
order is or is not associated with a given tree (see below) is not required.
Because of that, this distinction can be used to clarify if the child order
must be understood to be embedded into the corresponding tree/node order.

<!-- ======================================================================= -->
## ordered document tree

Since embedding the child order of a document tree into its tree order is
**a partial extension** of the unordered document tree, the resulting tree
will be referred to as **the ordered document tree**.

Note that the child order of a document tree is **embedded** into the node
order of its ordered document tree. That is, a document tree's child order
is a suborder to its tree/node order. As such, the child order of a document
tree can be considered **internal** to the ordered document tree.

Note that, since any tree can be described as the union of one or more rooted
paths, each of which is an ordered sequence of nodes, embedding a child order
into a tree order will modify the node order of that tree. That is because the
edges of a child order will establish paths between siblings that can not be
formed over an unordered document tree.

<!-- ======================================================================= -->
## document tree (2)

In cases where it is considered secondary, if the child order of a document
tree is embedded into its node order, one may use **document tree** as a means
to refer to the document tree or its node order in a more generic way.

Note that this notion is similar to **tree order**. That is, this description
can also be understood as a generic way to refer to some known node order.

Note that neither a document tree (ordered or unordered), nor a general tree
has a child order. That is, the corresponding endo-relations must always be
understood to have no child order.

<!-- ======================================================================= -->
## document order

Recall that a document order is understood as **a total node order**. One
should therefore neither confuse that description with the node order of the
"unordered doctree", nor with the node order of the "ordered doctree". That
is because the node order of a document tree is in general still a partial
node order.

Furthermore, the document order of a document tree can be understood as a
**processing order** that defines the order in which the nodes of a document
tree must be visited. This in order to ensure that different implementations
will produce the same results.

Note that, in regards to providing a complete consistent "picture", there
is **an explanatory gap** between "ordered doctree" and "document order".
Subsequent chapters on the pre-order tree traversal will close this gap.

<!-- ======================================================================= -->
## "ordered tree" vs. "unordered" tree - meh (!)

A tree that is associated with an external child order is in general referred
to as an ordered tree In contrary to that, a tree that has no such child order
associated with it, is commonly described as an unordered tree.

* "ordered tree" => "unordered document tree"
* "unordered tree" => "a (simple) tree"

However, even though one can in general associate some child order with a tree,
one needs to keep in mind that, from a mathematical perspective, a tree still
has no child order. That is because the underlying endo-relation does not embed
such an order since its simple set of edges does not support such a notion.

With that in mind one should be able to understand the meaning of the following
statement: **Even an "ordered tree" is just another "unordered tree".**

Due to the above, the current use of the prefixes "ordered" and "unordered"
makes no sense in the context of a tree. That is because the endo-relation
of a tree has no child order either way.
