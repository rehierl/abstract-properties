
<!-- ======================================================================= -->
# sequence-based tree encodings

Each path over a tree, as an ordered sequence of nodes, can be understood to
encode a path graph and therefore a linear subtree of the source tree. After
all, any two adjacent nodes within a path can be understood to define an edge.

Note that such an encoding can be described as an **explicit encoding** since
the definition of the edges are more or less directly encoded. That is, these
definitions can be read as-is, which is why the definition of the edges do not
have to be derived from some other implicit/embedded encoding such as a
compressed data stream.

An alternative is to associate a trace of nodes with a sequence of index values
such that each index in it references the **child-of** the corresponding node.
Since this encoding can be described as a deflated version of the path-based
encoding, this **reference-based encoding** is of limited use. After all, it
only allows to define one child per parent.

Another alternative is to associate a trace of nodes with a sequence of index
values such that each index in it references the **parent-of** a node. Since
this encoding can be used to define any node tree, including an associated
child order, it will be assumed as the **default encoding** of a tree.

Note that many more explicit encodings are obviously possible.
Amongst these are adjacency matrices and explicit lists of edge definitions.
