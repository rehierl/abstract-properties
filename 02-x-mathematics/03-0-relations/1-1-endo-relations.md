
<!-- ======================================================================= -->
# endo-relations

A relation that can be described as binary and homogenous (i.e. both domains
are the same), can be described as an **endo-relation**. In addition to that,
the elements within the domain of an endo-relation will be referred to as
**vertices** and, based on that, the domain `D` as a set of vertices `V`.

* `R := (V,G) := (V,V,G)` such that `(G subset-of P(V×V))`

Note that, due overall focus on node trees, graph theoretical terms may in
general be used in the context of endo-relations.

The following syntactic "shortcuts" will be used:

* `(s in R) := (s in G)`
* `aRb := ((a,b) in G)`
* `!aRb := ((a,b) not in G)`

Note that the expression `aRb` is defined to denote a boolean value that is
true, if the corresponding edge is an element in `G` (i.e. `((a,b) in G)`).
However, the expression `aRb` may also be used to denote the corresponding
edge (i.e. `(a,b)`) itself.

All the sequences in `G` are 2-element sequences and will as such be referred
to as **edges**. Furthermore, the vertices of an edge will be referred to as
**endpoints** with the 1st endpoint being the **source** and the 2nd endpoint
as being the **sink** vertex of that edge. Furthermore, The source of an edge
can be described as a source to its sink vertex. Conversely, the sink of an
edge can be described as a sink to its source vertex.

Note that not every vertex is in general required to be the endpoint of an
edge. Such a vertex can be described as being **disconnected**, or as being
**unrelated** (to another vertex). However, since the overall discussion is
on connected "things", disconnected vertices will in general be ignored.

Note that an edge is in general assumed to have distinct vertices as its
endpoints. In cases where the endpoints are the same, an edge may be referred
to as **a loop (edge)**,  or as **a reflexive edge** (i.e. `aRa`). This in
regards to reflexive order relations.

Since each edge has a source and a sink vertex, any edge can be said to lead
from its source to its sink vertex. As such, an edge can be described as being
oriented. Because of that, an endo-relation can be understood to support
**a notion of orientation**, or **a notion of direction**.

A vertex that is a source vertex to one or more edges, but no sink vertex to
any edge, will be referred to as a **source vertex** to the relation. Likewise,
a vertex that is a sink vertex to one or more edges, but no source vertex to any
edge, will be referred to as a **sink vertex** to the relation. Any other vertex
that is an endpoint to one or more edges may be referred to as an **inner vertex**
to the relation.

Any edge to which a vertex is a source, may be described as **an outgoing edge**.
Conversely, any edge to which a vertex is a sink may be described as an
**incoming edge**. A vertex that has a loop can therefore be understood to have
an outgoing and an incoming edge. A vertex that has a loop is therefore neither
a source nor a sink vertex to the endo-relation. Consequently, a vertex that
has a loop will be treated as an inner vertex if loops can not be ignored in
a given context.
