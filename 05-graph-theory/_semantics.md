
An expression of some sort is in general associated with each edge `(e in E)`
which is understood to provide an explanation as to why the endpoints are
adjacent to each other - i.e. connected with each other. This reason will be
referred to as the semantics of an edge.

* e.g. `sem(e) := (x divisible-by y)` for some edge `e := (x,y)`

The semantics of two edges `e1` and `e2` in a relation are in general not
required to be the same. That is, `(sem(e1) != sem(e2))` may in general be
true for some pair of edges. In such a case, the set of edges `E` is said to
be heterogenous. Because of that, a relation can in general be understood to
also contain a set of tuples that provides a mapping between an edge and its
semantics.

* `R := (V,E,S)`, where `S` is defined as follows
* `S := { (e,s) | (e in E) and (s == sem(e)) }`

However, in the context of this discussion, the semantics of each edge is
expected to correspond with the semantics of all the other edges in a relation.
Because of that, the semantics of a relation `sem(R)` can be defined as the
common semantics of its edges.

* `(sem(R) == sem(e))` for all `(e in E)`

Put together, all relations in this discussion are seen as directed graphs and
are expected to be endo-relations based upon a homogenous set of vertices and
a homogenous set of edges.
