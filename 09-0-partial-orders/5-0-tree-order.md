
<!-- ======================================================================= -->
# tree order, node order

The node order of a tree is commonly referred to as **the tree order** of some
known tree and used to denote the top-down order between the nodes in it (i.e.
descendants are subsequent to ancestors). Because of that, this description is
more or less one that that focuses on the visual representation of a tree, and
not so much on the underlying partial order.

Also, the description of "tree order" seems misleading since the corresponding
order is no order of trees, but an order of nodes. That is, referring to some
"tree order" is like referring to "an ordered set of trees". Because of that,
it seems better to not use that description, but to use descriptions such as
"the tree's **node order**" instead.

<!-- ======================================================================= -->
## "presequent-to/ancestor-of" semantics

Since the node order of a tree is transitive, one needs to keep in mind
that the "parent-of" semantics of the edges in a tree is morphed into the
"ancestor-of" semantics.

Conesquently, if one had to describe the semantics of such a node order,
one should either describe it as "presequent-to", or as "ancestor-of".
