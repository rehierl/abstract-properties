
<!-- ======================================================================= -->
# Unary operations on graphs

The following operations `(op: G -> X)` take a single input graph `G`
in order to produce a result:

* a single graph `G := (V,E)` is used to create some result
* e.g. a new graph `op(G) -> (V',E')`

<!-- ======================================================================= -->
## topological sorting/ordering

The "topological sort(ing)" or "topological ordering" of a DAG `G := (V,E)`
refers to the process of "serializing" the vertices of a graph into an ordered
sequence of vertices `s` such that the relative order of the endpoints of all
paths over `G` is preserved in `s`.

* `aPb -> (a presequent-to b)`
* for `(s in ×V)` and `(#s == #V)`

Note that the topological ordering of a graph is closely related to the linear
extension of partial orders.

<!-- ======================================================================= -->
## converse/transpose graph

The converse (or transpose) `G° := (V,F)` of a graph `G := (V,E)` is formed,
if each edge in it is reversed.

* `conv(G) -> G° := (V,F)`
* `F := { (b,a) | aEb }`

Note that the converse edge `bFa` of an edge `aEb` can be described as having
converse semantics.

<!-- ======================================================================= -->
## reflexive reduction

The reflexive recution of a general graph `G := (V,E)` will return a new graph
`S := (V,E*)` such that `S` has no loops at all.

* `E* := E \ { (a,a) | aEa }`
* `E*` may be distinct from `E`
* see - relations

Note that the resulting graph can be considered minimal in regards to loops.
That is because it has no loop at all. In contrary to that, a preorder can be
considered maximal in that regards. That is because a preorder is required to
have a loop for each of its vertices.

<!-- ======================================================================= -->
## reflexive closure

The reflexive closure of a general graph `G := (V,E)` will return a new graph
`S := (V,E*)` such that it has a loop for each vertex in it.

* `E* := E + { (a,a) | (a in V) }`
* `E*` may be distinct from `E`
* see - relations

<!-- ======================================================================= -->
## transitive reduction

The transitive reduction of a general graph `G := (V,E)` will return a new graph
`S := (V,E*)` such that it does not contain an edge `aE*c` for any pair of
adjacent edges `aEb` and `bEc`.

* `E*` may be distinct from `E`
* see - relations

Note that the resulting graph can be considered minimal in regards to transitive
edges. That is because it has no such edges. In contrary to that, a preorder can
be considered maximal in that regards. That is because a preorder is required to
be closed under transitivity.

<!-- ======================================================================= -->
## transitive closure

The transitive closure of a general graph `G := (V,E)` will return a new graph
`S := (V,E*)` such that it iteratively adds an edge `aE*c` for any pair of
adjacent edges `aEb` and `bEc`.

Note that the iterative process begins with cloning the input graph `G`. Each
next step will then add any missing edge `aEc` for any pairs of adjacent edges
`aEb` and `bEc`. For obvious reasons, each addition may introduce a new pair
of adjacent edges.

* `E*` may be distinct from `E`
* see - relations
