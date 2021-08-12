
<!-- ======================================================================= -->
## connected, disconnected

**A pair of vertices** is said to be connected, if there is an edge within an
order relation that has both vertices as its endpoints. Conversely, a pair of
vertices can be described as being disconnected from each other, if such an
edge does not exist.

* `(a connected-with b) := aRb or bRa`
* `(a disconnected-from b) := not (a connected-with b)`

Similar to that, **a vertex** can be described as being connected, if an edge
exists that has the vertex as one of its endpoints. That is, a connected vertex
is an endpoint to one or more edges within an oder relation. Conversely, a
vertex can be described as being disconnected, if such an edge does not exist.

* `(is-connected a) := "some (b in V) exists such that aRb or bRa is true"`
* `(is-disconnected a) := not (is-connected a)`

<!-- ======================================================================= -->
## comparable, incomparable

Since an ordered set `P := (V,×)` is in general understood to be associated
with an order operator `×`, the set of edges in the underlying order relation
of an ordered set is **not arbitrary**. One can therefore not freely choose
which pair of vertices are connected and which ones are not. Put differently,
there is a strict definition for the pairs of vertices an order relation must
contain.

Based on that, two vertices are said to be **comparable** over an order, if an
edge exists within the underlying order relation that has both vertices as its
endpoints. If no such pair exists, then both vertices are understood to be
**incomparable** under the corresponding ordered set.

* `(a comparable-to b) := (a connected-with b)`
* `(a incomparable-with b) := (a disconnected-from b)`

Defined as such, the terms comparable/incomparable are synonymous to connected/
disconnected in regards to pairs of vertices. Based on that, the former pair of
terms can be said to reflect an order-based perspective whereas the latter pair
can be said to reflect a graph/relation-based perspective.

Since the order relation is considered to contain all of the pairs of vertices
for which the order operator is defined to be true, the oder relation of an
ordered set must be treated as being **complete** (i.e. "as is").
