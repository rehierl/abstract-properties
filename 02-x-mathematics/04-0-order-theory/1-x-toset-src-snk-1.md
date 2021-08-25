
<!-- ======================================================================= -->
# total order (toset)

* a toset is a trichotomous/connex poset
* trichotonous - aRb xor bRa xor (a == b)
* connex - aRb and/or bRa must be true for any (a,b in V)
* all possible pairs must be connected by an edge

loops/cycles

* a toset is a poset - a poset is acyclic
* transitivity would force symmetric pairs of edges
* cycles are symmetric sub-orders
* loops are allowed, cycles are not

source/sink vertices

* if more than two vertices, then ..
* has no disconnected vertices
* must be a single connected component
* must have one and only one source vertex
* must have one and only one sink vertex

<!-- ======================================================================= -->
## the transitive reduction of a toset

The trantsitive reduction of a total order relation must correspond with a
path graph. That is because otherwise the transitive closure could not
establish an edge between all pairs of vertices. In other words, a path
must exist between any two vertices.

```
not a toset (!)
====================
     |-> v2 ->|
v1 ->|        |-> v4
     |-> v3 ->|
```

No vertex in a toset can have more than one outgoing edge. That is because,
since a toset is acyclic, no path could be established between both target
vertices. No vertex can have more than one incoming edge for the same reason.

* no more than one outgoing edge
* no more than one incoming edge
* no more than one root
* no more than one leaf

A toset must have a leaf since it would otherwise be cyclic.
A toset must have a root for the same reason.

* must have one and only one root
* must have one and only one leaf
* (#ideg == 1) must be true for any non-root
* (#odeg == 1) must be true for any non-leaf

Any path in a toset is unique.

* one and only one path is possible between any two vertices
