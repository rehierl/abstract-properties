
# node trees (NT)
- node trees, specialized graphs

Like any other graph, a node tree T := (N,E) is an endo-relation that has
edges (E) which connect its nodes (N). In addition to that, a node tree is
such that the following requirements are met:

1. One and only one node has no incoming edge (aka. the root).
2. Each non-root node has one and only one rooted path.

Note that the overall discussion is on directed rooted node trees,
each of which can be described as an **arborescence**, or as an out-tree.

Note that both requirements must be met, a node tree (unlike general graphs)
can not be understood to have **no arbitrary set of edges**.

Note that the above requirements are based on the edges in a graph and as such
of structural nature. That is, if the vertices in a graph are connected such
that the requirements are met, then that graph is a node tree. Hence, the
semantical reason as to why two nodes in a graph are connected is as such
secondary. That is, the focus is on the resulting structure and as such on
"visuals", not on the semantics that led to it.
