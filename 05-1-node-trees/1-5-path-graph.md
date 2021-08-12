
<!-- ======================================================================= -->
# (directed) path graph

* `p := n1 -> n2 -> n3 -> n4`

A path graph `p` is a digraph `P := (N,E)` such that ..

* `N` is the non-empty set of nodes
* `E` is the possibly empty set of edges
* `(E(e) subset-of N)` for each `(e in E)`
* `(E subsetof N×N)`

In addition to that, the following requirements must be met.

* `E` has `(#N-1)` edges
* `N` has one and only one source node `r`
* `N` has one and only one sink node `l`

Also, the connections between the nodes must be such that a path `p := (r,..,l)`
can be formed that begins in `r` and ends in `l` such that it contains all the
nodes in `N`.

Based on the above, the following is true:

* `P` is a (special) node tree
* no node has more than one parent
* no node has more than one child
* the degree of each node is no more than 2
* `r` is a root and `l` a leaf to `P`
* `(p == rp(l))` and `(#p == #N)` and `(E(p) == N)`
* `p` is the rooted path `rp(l)` of `l`
* `p` is an ordered sequence over `N`
