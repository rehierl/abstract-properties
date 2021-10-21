
<!-- ======================================================================= -->
# operations on trees

Once an implementation has determined the relationships of each node with each
section in a doctree, one will usually want to use the information available
to (e.g.) fold the contents of a section. In general, such an operation is
implemented based on hiding the nodes of a section.

Note that hiding a node from a visual representation is in essence a decision
to not visualize that node. That is, one chooses to not display the node by
skipping/ignoring it (passive) while visualizing the rest of the tree (active).
Because of that, and since hiding a node from a tree is similar to removing
that node from the tree (active), the following will focus on the removal of
a node from a tree.

It would obviously be counter intuitive if the descendants of a removed node
would still have to be visualized. Because of that, one does in general
associate more than one node with an operation. Each operation can therefore
be said to be associated with a certain scope that extends over all the nodes
that will be affected.

Note that an operation, which is defined to affect all the nodes in the type-x
scope of its first/defining node, may be described as **a type-x operation**.
That is, a type-0 operation is restricted to a single node whereas a type-1
operation also affects all of its descendants in the DTU base order.
