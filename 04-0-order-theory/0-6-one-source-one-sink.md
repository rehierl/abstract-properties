
<!-- ======================================================================= -->
## more than one source and/or sink vertex?

Recall that a total order is defined as a specialized partial order that has
additional requirements attached to it. That is, as a partial order, a total
order is required to be oriented/directed. That is, in between any pair of
distinct connected vertices, only one edge may exist.

Assumed that a total order had two source vertices (i.e. two vertices with
no incoming edge at all) `(a,b in V)`, then the transitive closure could not
establish an edge between these two vertices, since none can also be a sink.
That is, neither the edge `aRb`, nor the edge `bRa` could exist. As such, the
order relation could neither be connex nor trichotomous.

Assumed that a total order had two sink vertices (i.e. two vertices with no
outgoing edge at all) `(a,b in V)`, then the transitive closure could not
establish an edge between these two vertices, since none can also be a source.
That is, neither the edge `aRb` nor the edge `bRa` could exist. As such, the
order relation could neither be connex nor trichotomous.

Due to the above, an order relation can not be total if it has more than one
source and/or sink vertex. That is because it would then contain two or more
vertices that are incomparable. Consequently, any total order relation has ..

* **one and only one connected component**
* **no more than one source vertex**
* **no more than one sink vertex**

<!-- ======================================================================= -->
## one source/sink?

The remaining question is therefore, if a total order is required to even have
a sink and/or a source vertex?

Assumed that a total order relation had a source vertex, then the relation's
connex/trichotomous characteristic would force it to be a source vertex to
every other vertex. That is, any other vertex is then required to be directly
connected to it as a source vertex in the order relation. Based on that there
seems to be no conflict, which is why a total order relation may still have a
single source vertex.

Analogous to that, a total order relation may still have a single sink vertex.
That is because such a vertex can still be connected as a sink to every other
vertex in the order relation.

<!-- ======================================================================= -->
## no source/sink?

Assumed that a total order had **no source vertex**, while ignoring any
loops at this point, then each vertex would be required to have at least
one incoming edge since otherwise there would be a source. Because of
that, **each vertex must be a sink to one or more other vertices**.

At least one vertex must therefore exist that is a sink to some other vertex
and, in addition to that, a source to yet another vertex. Having no (overall)
source vertex therefore requires the relation to have an inner vertex. That
is, **at least one inner vertex must exist**.

Since at least one inner vertex is required, and since a total order must be
transitive (preorder) and strictly oriented (partial order), an edge must
exist that connects the source vertex of that required inner vertex with its
sink vertex, each of which must be distinct.

Consequently, the source vertex of the required (initial) inner vertex must
itself be an inner vertex. After all, it is a source to the initial inner
vertex and itself still required to be a sink to some other vertex.

Based on that, one can imagine an interative process that begins with the
required (initial) inner vertex, removes two distinct vertices from the
remaining vertices and connects one as its source and the other as its sink
vertex. And since that source vertex must itself be an inner vertex, the
focus of the iterative process shifts to that source vertex as the new
current inner vertex.

Note that the "next" current inner vertex has its sink vertex within those
vertices that have already been removed from the remaining vertices. In
contrary to that, the source vertex to the "next" current inner vertex can
not be one of these "known" vertices since this would trigger a conflict
with the strict orientation of the total order. That is because any of these
vertices can be reached as an immediate sink (due to transitivity), which
can not also be a source vertex to the new inner vertex. This "next" source
vertex must therefore be one of the remaining vertices.

One can then imagine to repeat the iteration by removing the next remaining
vertex as the next source to the current inner vertex, and by that to reduce
the amount of remaining vertices by one with each step of the iteration, until
there is no more remaining vertex left (hint - no infinite orders).

One can therefore conclude that the iteration is guaranteed to result in a
conflict since there will at some point be no further source vertex to the
current inner vertex.

* assumption - no source vertex
* each vertex must be a sink to one or more other vertices
* at least one inner vertex must exist
* an iteration in the direction of source vertices
* one will eventually run out of source vertices (!)

Loosely described, one is therefore guaranteed to end up with a source vertex,
even though the initial assumption was such that there is no overall source
at all. Based on an analogous initial assumption, one can derive an analogous
conclusion.

* assumption - no sink vertex
* each vertex must be a source to one or more other vertices
* at least one inner vertex must exist
* an iteration in the direction of sink vertices
* one will eventually run out of sink vertices (!)

One can therefore conclude that any total order relation must have ..

* **one and only one source vertex**
* **one and only one sink vertex**
