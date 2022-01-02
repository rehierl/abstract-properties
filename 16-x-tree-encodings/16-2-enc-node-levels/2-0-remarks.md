
<!-- ======================================================================= -->
# overall remarks

Note that the level-based encoding scheme is **an implicit encoding scheme**
since it doesn't directly encode the edges of a tree. Furthermore, no other
encoding is embedded as an "inner encoding" which would first have to be
decoded.

Recall that the **level of a node** is defined as the node-length of its rooted
path - i.e. `#rp(n)`. That is, the level of a node is the number of nodes in
its extended set of ancestors - i.e. `#A*(n)`. Consequently, the level of a
node can be understood to count the number of scopes to which a given node
is an element. In other words, the level of a node is equal to the number of
scopes that are open while a node is being visited.

* `level(n) := #rp(n)`, alternatively `level(n) := #A*(n)`

Note that the level-based encoding does not allow to define cycles. That is,
the structure of a graph that is defined using the level-based encoding is
guaranteed to be **acyclic**. That is because the parent-to-child edges derived
from such an encoding are all oriented the same way - i.e. backward-oriented
in the case of a pre-order encoding.

Note that level values are **independent of the index order** of a tree's trace
of nodes. Because of that, the PRE-POSTR and POST-PRER correspondences directly
apply - i.e. without having to transform index values.
