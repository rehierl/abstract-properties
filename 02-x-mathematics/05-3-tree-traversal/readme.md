
# mathematics / tree traversal

In order to process the nodes in a document tree, implementations must visit
each node in a specific order. This chapter will therefore introduce the tree
traversal algorithms that can be used for that purpose.

Note that **the visit of a node** is in principle **an atomic operation** which
reflects a point in time that refers to processing the corresponding node. That
is, no other node can be understood to be visited while another node is still
in the process of being visited. That is because a design must ensure that
implementations can be guaranteed to produce identical results.

Note that the visit of a node **must not be confused with the scope of a node**
over the tree's node order. Subsequent discussions will point out that the
pre-order traversal of a tree visits a node just after entering its scope,
and before entering the scopes of its child nodes. Also the scope of a node
will be exited just after all the scopes of its child nodes have been exited.

Since a document tree has a child order associated with it, the traversal of
a document tree is in general required to visit each node while respecting the
tree's tree order, and also its child order. That is because each node in such
a tree can be understood to define properties whose scopes are defined based
on the suborders that are embedded into the document order.

Note that only the default level-order and the default pre-order tree traversal
algorithms can be described as **order preserving** in regards to the tree order
and also the child order of a document tree.
