
<!-- ======================================================================= -->
# Unary operations on graphs

The following operations `(op: G -> X)` take a single input graph `G`
in order to produce a result:

* a single graph `G := (V,E)` is used to create some result
* e.g. a new graph `op(G) -> (V',E')`

<!-- ======================================================================= -->
## converse/transpose graph

The converse (or transpose) `G° := (V,F)` of a graph `G := (V,E)` is formed,
if each edge in it is reversed.

* `conv(G) -> G° := (V,F)`
* `F := { (b,a) | aEb }`

Note that the converse edge `bFa` of an edge `aEb` can be described as having
converse semantics.

<!-- ======================================================================= -->
## topological sorting

The "topological sort(ing)" or "topological ordering" of a DAG `G := (V,E)`
refers to the process of "serializing" the vertices of a graph into an ordered
sequence of vertices `s` such that the relative order of the endpoints of all
paths over `G` is preserved within `s`.

* `aPb -> (a presequent-to b)`
* for `(s in ×V)` and `(#s == #V)`

Note that the topological ordering of a graph is closely related to the linear
extension of partial orders.

<!-- ======================================================================= -->
## reflexive closure/reduction - TODO

* see - relations

<!-- ======================================================================= -->
## transitive closure/reduction - TODO

* see - relations
