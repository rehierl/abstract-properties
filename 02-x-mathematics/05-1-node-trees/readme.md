
# mathematics / node trees (NT)

A node tree `T(N,E)` is a graph such that the following requirements are met:

* One and only one node has no incoming edge - i.e. the root.
* Each node in a tree has one and only one rooted path.

Note that a node tree, unlike a general graph, can not be understood to have
**an arbitrary set of edges**. After all the above requirements must be met.

Note that these requirements are based on the edges in a graph and are as such
**structural requirements**. That is, if the vertices in a graph are connected
such that the requirements are met, then that graph can be described as a node
tree. Hence, the semantical reason as to why two nodes in a graph are connected
is more or less secondary. That is, the focus is on the resulting structure and
therefore on "visuals", not on the actual semantics that led to it.

Note that the overall discussion is on directed rooted trees, each of which
can be described as an **arborescence**, or as an out-tree. To be more clear,
the root of a tree may have any number of outgoing edges, but not even one
incoming edge.

Note that the definitions of **level**, **ancestor** and **descendant** are
path-based definitions. In addition to that, the definitions of **A(n)** and
**D(n)** can be described as an abstraction, which can be described in terms
of **open intervals** over the node order of a tree.

* `A(n) := (*,n)` and `D(n) := (n,*)`

Note that the perception of **up/down** in the context of trees is by default
in regards to top-to-bottom based drawings. It is therefore important to point
out that this perspective will change in the course of this discussion. That
is, the description of up/down will slowly shift bo be in regards to an
order-based point of view - i.e. in regards to the path-based definitions of
presequent (down) and subsequent (up). Insofar one should begin to think in
terms of left-to-right based drawings instead.
