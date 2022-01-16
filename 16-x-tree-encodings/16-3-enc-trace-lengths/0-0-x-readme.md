
# the length-based encoding (LEN)

The following focusses on howto implement a length-based encoding such that the
traversal algorithms output the node count of the current node being visited.
This node count includes the node itself and all its descendants in DTU.

Note that this encoding scheme will be referred to as
**the length-based implicit encoding scheme**.

Note that the pre- and post-order tree traversal encoding algorithms allow to
**maintain the rooted path** of the node being visited. Unlike with node levels,
the rooted path must this time be used to store intermediate node counts. That
is, until one recalls that the trace of a node is a substring to the traces of
its ancestors, which is why the length of a trace can simply be determined by
the index of the first and the index of the last node in a trace.

Note that the decoding algorithms must maintain a rooted path in order to be
able to determine the parent node of the next node being decoded. This is done
by iteratively reducing the corresponding node counts associated with each node,
which effectively results in a stack of remaining node counts.

Note that this length-based encoding can also not be used to define cycles.
That is this encoding also only allows to define **acyclic graphs** since the
edges derived from it will also be oriented from a current node towards the
tree's root.
