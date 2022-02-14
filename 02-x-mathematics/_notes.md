
# fundamental concepts

container types are based upon components
- interconnected components
- an order over the components of a container
- the order of a simple set is ... total!

point out the similarties between the operators
- defined for sets and sequences
- i.e. subset-of, substring-of
- lost thought - the quantififers ?!?

# graph theory (GT)

semantics of an edge
- if an edge has semantics, then these semantics
  usually also apply to any pair of matching edges
- that is, if semantics are transitive, then the
  resulting graph is itself transitive
- e.g. parent-of vs. ancestor-of

graph property
- describes the general characteristic of a graph
- e.g. each node has a unique rooted path
- should probably have an explanation

hereditary (graph) properties
- applies to any subgraph

bipartite graph
- the set of vertices is a union of two disjoint subsets
- the edges lead from one subset to the other
- all the edges begin in the same subset
- bends the definition of an endo-relation
- i.e. more of a binary relation

graph theory seems to focus on edges
- disconnected vertices (seem) to get (mostly) ignored
- e.g. the (standard) definition of a complement graph

# tree order

Note that the DOM specification treats the "tree order" description as being
synonymous to the "pre-order node order" (i.e. the doctree's pre-order trace
of nodes). That is, the DOM spec uses that description to refer to a total
node order, which is more than just misleading.
