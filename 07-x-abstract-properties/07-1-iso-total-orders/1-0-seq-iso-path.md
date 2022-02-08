
<!-- ======================================================================= -->
# ordered sequences <=> path graph

Given a non-empty ordered sequence `s`, ..

* `s := (n1, n2, n3, n4, n5, n6)`

.. one can easily form a path graph using the default edge-based semantics.

* `P := (N,E)` such that `N := E(s)` and
* `E := { (a,b) | (a next-presequent-to b) }`

One can then recreate `s` from `P` by a simple tree traversal.

* `( s == rp( s[#s] ) )`

Any non-empty ordered sequence therefore corresponds with a path graph.

Likewise, any path graph can be transformed into an ordered sequence of
nodes, which can then be transformed back into the intial path graph.

Consequently, any ordered sequence can be said to be **isomorphic**
to a path graph. That is, one can be transformed into the other.

* `s` is isomorphic to `P`

<!-- ======================================================================= -->
## ordered sequence => path graph

One can easily form a graph `G := (V,E)` such that the set of vertices `V`
is equal to the set of distinct elements `E(s)` of that sequence. All one
needs to do is to define the set of edges `E` based on the index order over
the components in `s`.

* `G := (V,E)` such that `V := E(s)`
* `E := { (a,b) | (idx(a) == idx(b)-1) for (a,b in V) }`
* `sem(G) := (a next-presequent-to b)`

One can then visualize the graph's endo-relation as below.

```
(a next-presequent-to b)
==============================
n1 - n2 - n3 - n4 - n5 - n6 ->
```

One can therefore conclude that this graph is a path graph `P := (N,E)` and as
such a node tree. Because of that, `n1` can be described as the root/source
node, and `n6` as the leaf/sink node of `G`.

* `s` => `G := (V,E)` => `P := (N,E)`

<!-- ======================================================================= -->
## path graph => ordered sequence

Since the path graph `P` is a tree and therefore has a single root `r` and a
single leaf `l`, the rooted path `rp(l)` of that leaf can be formed.

And since that rooted path of nodes `rp(l)` contains all of the nodes in `P`,
in the order as specified by the initial ordered sequence `s`, the ordered
sequence `s` can be recreated by a simple tree traversal of the path graph
that begins in the path graph's root node `r`.

* `( s == rp( s[#s] ) )`

Put differently, the initial sequence `s` is the trace of nodes that results
from traversing the path graph `P`.
