
# mathematics / graph theory (GT)

A graph `G(V,E)` is defined as an endo-relation that consists of a set of
vertices `V` and a set of directed eges `E`. As such, and like an order
relation, a graph is a complex value/type.

* `G(V,E)` such that `(E subset-of (V × V))`

<!-- ======================================================================= -->
## paths of vertices

**Paths** over the edges in a graph are by definition **un-directional**.
That is, for each vertex in a path there must be an edge which has that
vertex as its source, and the next subsequent vertex as its sink vertex.
That is, all the edges in a path are oriented the same way.

Note that paths are fundamental to graph-based definitions. In addition to
that, it is essential to realize that paths, as the basis of transitivity,
can be understood to **bridge the gap between GT and OT**.

<!-- ======================================================================= -->
## no overall requirements

Unlike order relations, a graph has in general no overall requirement as to why
two of its nodes are connected. That is, a graph does by default not have to
satisfy any structural requirement. Because of that, a graph can be understood
as a relation that has a seemingly arbitrary set of edges. No conclusion can
therefore be drawn based upon shared characteristics, since none can be
guaranteed to exist.

Requirements therefore need to be introduced that define sub-groups of graphs
such that each graph in such a group can be expected to ave the required
characteristics (e.g. each graph must be a node tree). These characteristics
then allow to draw conclusions in regards to such a group.

<!-- ======================================================================= -->
## edge-based semantics

An expression of some sort is in general associated with each edge `(e in E)`
which is understood to provide an explanation as to why two vertices in a
graph are adjacent (aka. connected) to each other. This reason will be referred
to as the semantics of an edge.

* `sem(e) := (x divisible-by y)` for some edge `e := (x,y)`

The semantics of two edges `e1` and `e2` in a relation are in general not
required to be the same. That is, `(sem(e1) != sem(e2))` may in general be
true for some pair of edges. In such a case, the set of edges `E` is said to
be heterogenous. Because of that, a graph can in general be understood to be
associated with a set of tuples which provides a mapping between an edge and
its semantics.

* `R := (V,E,S)`, where `S` is defined as follows
* `S := { (e,s) | (e in E) and (s == sem(e)) }`

However, in the context of this discussion, the semantics of each edge is
expected to be equal to the semantics of all the other edges in a graph. In
such a case, the set of edges `E` can be said to have **homogenous semantics**.
Based on an homogenous set of edges, the semantics of a graph `sem(G)` can
be defined as the shared semantics of its edges.

* `(sem(G) == sem(e))` is expected to be true for all `(e in E)`

Note that all graphs in context of this this discussion are expected to be
endo-relations based on a homogenous set of vertices and a homogenous set
of edges. Furthermore, two graphs with equal semantics can be described to
be of the **same sort**.

Note that, to some extent, the structure of a graph could be described as its
"syntax", and the reason as to why two vertices are connected as its "semantics".

<!-- ======================================================================= -->
## operations on graphs

Some of the graph-related binary operations defined here create new graphs by
executing set-based operations on the corresponding sets of vertices and/or
their sets of edges. That is, these definitions build upon existing vertices
and/or edges rather than creating entirely new entities (e.g. via the Cartesian
product, e.g. tensor/strong product).

Note that these binary operations in general require the input graphs to be
of the same sort. That is, the graphs involved are expected to have similar,
if not identical semantics.

Note the difference between the definitions of **sub-graph** and **sub-order**:
A subgraph can be formed almost arbitrarily, whereas a suborder must be formed
as an induced suborder by following a fixed/defining rule: (1) a subset of
vertices, and (2) **all the edges between the input vertices**. That is, there
is no degree of freedom in which edges to hold on to when forming a suborder.
