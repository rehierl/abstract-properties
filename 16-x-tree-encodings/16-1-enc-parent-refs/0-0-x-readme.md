
<!-- ======================================================================= -->
# the parent-based encoding (PAR)

The following focusses on howto implement a parent-based encoding in the context
of different tree traversal algorithms. That is, different traversal algorithms
will be specified in code which output a sequence of parent references, one for
each node in the traversal's trace of nodes.

Note that this encoding scheme will be referred to as
**the parent-based explicit encoding scheme**.

Note that the level-order and the pre-order traversals allow straight-forward
implementations. That is because both of these are order-preserving in regards
to the document tree's tree order. In contrary to that, the post-order traversal
will always require additional computational complexity since the reference of
a parent is unavailable at the time a child is being visited.

Note that a root has no parent, which is why the parent-based encoding will
always have to define **an invalid parent reference** to cover the parent
reference of a root. In addition to that, one will always have to keep in
mind that this parent-based encoding can be used to define **cyclic graphs**.
