
# tree traversal (2)
- forming traces of nodes from an ordered doctree

Note that the **pre-order** and the **level-order** tree traversals are the
only order-preserving algorithms. In addition to that, the pre-order traversal
corresponds with a hierarchy of scopes, whereas the level-order traversal is
overall a sequence of disjoint child orders and thus non-hierarchical.

Note that **in-order** tree traversal algorithms are not in the focus of this
discussion. That is because these visit a node after its first child, which
is why they are not order-preserving. In addition to that, in-order algorithms
will in general visit a node more than once, which is why the corresponding
traces of nodes are no ordered sequences of nodes.
