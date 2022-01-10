
<!-- ======================================================================= -->
# the level-based encoding (LVL)

The following focusses on howto implement a level-based encoding such that the
traversal algorithms output the node level of the current node being visited.

Note that this encoding scheme will be referred to as
**the level-based implicit encoding scheme**.

Note that the pre-order and the post-order tree traversal encoding algorithms
allow to **maintain the rooted path** of the node being visited, and by that
the node's node level. Because of that, and unlike with parent references,
one does not have to distinguish between root nodes and non-root nodes. These
algorithms can even be reduced to **maintain a primitive level value**.

Note that the decoding algorithms must maintain a rooted path in order to be
able to determine the parent node of the next node being decoded.

Note that this level-based encoding can not be used to define cycles. That is,
this encoding only allows to define **acyclic graphs** since the edges derived
from it will all be oriented from a current node towards the tree's root.
