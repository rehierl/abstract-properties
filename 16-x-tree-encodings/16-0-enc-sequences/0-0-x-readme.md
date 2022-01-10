
<!-- ======================================================================= -->
# sequence-based tree encodings

Each path over a tree, as an ordered sequence of nodes, can be understood to
encode a path graph and thus a linear subtree of the source tree. After all,
any two adjacent nodes in a path can be understood to define an edge, which
is why any path can be described as a **path-based encoding** of a path graph.

Note that since the definition of each edge is more or less directly encoded,
each edge can be read as-is. That is, the definition of the edges do not first
have to be decoded from some implicit, or some embedded encoding. The latter
of which would be the case when (e.g.) reading a compressed data stream.

An alternative to a path-based encoding would be to associate a trace of nodes
with a sequence of index values such that each index points to the **child**
of the corresponding entry. This **reference-based encoding scheme** is however
of limited use since (by default) it only supports one child per node.

A different alternative would be to associate a trace of nodes with a sequence
of index values such that each index points to the **parent** of an entry.
Since this encoding can be used to encode any tree, including a child order,
it will be used as **the default explicit encoding scheme** of a tree.

Note that more explicit encodings are obviously possible. Amongst these are
adjacency matrices and lists of explicit edge definitions, each of which has
its particular advantages and disadvantages in regards to processing the data
stored within. With that in mind, the focus of the parent-based encoding scheme
is on serializing and deserializing the structure of a tree into and from a
sequence of numerical values.
