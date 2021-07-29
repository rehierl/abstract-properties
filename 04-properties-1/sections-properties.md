
<!-- ======================================================================= -->
# Sections as shared properties

This content defines sections based on properties which implement the connection
between a node and a section. And since a section may in general contain more
than one node, the property that represents a section in regards to a node is
in general shared across several nodes. Because of that, a section can be seen
as a property which is shared between a sectioning node and the nodes that are
subsequent to it.

Note that these properties can be considered to be references which point from
a node to the section to which it belongs. As such these properties implement
the connections between the nodes of a tree and its sections. On top of that,
the properties represent stored results that can be used to determine to which
section, or multiples thereof each node belongs.

Note that this can be said to be an argument for associating a sectioning node
with the section it declares.

Note that, from a graph-based perspective, each section property represents
an edge `e := (s,n)` that begins in a section `s` and ends in a node `n` (i.e.
a perspective that is turned upside-down). Based on that, a bipartite graph
`G := (V,E)` can be defined whose set of vertices `V` is the union of the set
of nodes `N` and the set of those sections `S`  that are defined by the tree's
sectioning nodes (i.e. `V := (N + S)`, i.e. vertex set `V` contains two
disjoint subsets/types of nodes).

- can visualize as elevated layers on top of a 2d plane that holds the node tree
