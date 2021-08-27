
# graph theory (GT)
- an overview of graph theory

A graph `G := (V,E)` is defined as an endo-relation that consists of a set of
vertices `V` and a set of (directed) eges `E`. As such, and like an ordered
set, a graph is a complex value/type.

* `G(V,E)` such that `(E subset-of (V × V))`

<!-- ======================================================================= -->

Unlike order relations in Order Theory, a graph in Graph Theory has no overall
requirement as to why two of its nodes are connected. That is, a graph does by
default not have to satisfy any structural requirement. Because of that, a
graph can be understood as a relation that has a seemingly arbitrary set of
edges. As such, no conclusion can be drawn based upon shared characteristics,
since none can be guaranteed to even exist.

Because of that, requirements need to be introduced that define sub-groups of
graphs such that each graph in a group has the required characteristics (e.g.
each graph must be a node tree). These shared characteristics then allow to
draw conclusions in the context of such a group.

<!-- ======================================================================= -->

An expression of some sort is in general associated with each edge `(e in E)`
which is understood to provide an explanation as to why two vertices in a
graph are adjacent to each other - aka. connected with each other. This
reason will be referred to as the semantics of an edge.

* e.g. `sem(e) := (x divisible-by y)` for some edge `e := (x,y)`

The semantics of two edges `e1` and `e2` in a relation are in general not
required to be the same. That is, `(sem(e1) != sem(e2))` may in general be
true for some pair of edges. In such a case, the set of edges `E` is said to
be heterogenous. Because of that, a relation can in general be understood to
be associated with a set of tuples that provides a mapping between an edge
and its semantics.

* `R := (V,E,S)`, where `S` is defined as follows
* `S := { (e,s) | (e in E) and (s == sem(e)) }`

However, in the context of this discussion, the semantics of each edge is
expected to equal to the semantics of all the other edges in a graph.
Because of that, the semantics of a graph `sem(G)` can be defined as the
shared semantics of its edges.

* `(sem(G) == sem(e))` for all `(e in E)`

Note that all graphs in context of this this discussion are expected to be
endo-relations based upon a homogenous set of vertices and a homogenous set
of edges.

Note that the structure of a graph could be described as its "syntax",
and the reason as to why two vertices are connected as its "semantics".

<!-- ======================================================================= -->

The grah-related binary operations as defined here create new graphs by executing
set-based operations (e.g. union of sets) on the corresponding sets of vertices
and/or on the corresponding sets of edges. That is, the definitions build upon
existing vertices and/or edges rather than creating new entities (e.g. via the
Cartesian product, e.g. tensor/strong product).

Note that the focus of the binary operations defined here is on the description
of the relationship between a graph and its subgraphs.

Note that these binary operations require in general the input graphs to be of
the same sort. That is, the graphs involved are (implicitly) expected to have
similar, if not identical semantics.
