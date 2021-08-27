
<!-- ======================================================================= -->
# partial order (poset)

* a non-strict poset is reflexive and transitive
* a strict poset is non-reflexive and transitive
* a poset is transitive - if aPb and bPc, then also aPc
* a poset is anti-symmetric - if aRb and bRa, then (a == b)
* a strict poset is a-symmetric - if aPb, then !bPa

loops/cycles

* a poset is acyclic
* transitivity would force symmetric pairs of edges
* cycles are symmetric sub-orders
* loops are allowed, cycles are not

connected/disconnected

* may have any number of disconnected vertices
* not required to have even one edge/path
* may have more than one connected component

for each connected component ..

* must have a source and a sink vertex
* may have one or more source vertices
* may have one or more sink vertices

<!-- ======================================================================= -->
## the transitive reduction of a poset

The transitive reduction of a partial order relation is not required to have
a path between any two vertices. In other words, no edge is required in between
any two vertices in the transitive closure.

```
v1
v2 -> v3
```

* may have disconnected vertices
* not required to have even one edge/path
* may have more than one connected component

```
v1 -> v2 -> v3
```

* for each connected component ..
* must have a leaf vertex
* must have a root vertex
* reason - acyclic - no cycles

```
v1 ->|-> v3
v2 ->|
```

* may have more than one root vertex

```
v1 ->|-> v3
     |-> v4
```

* may have more than one leaf vertex

```
     |-> v2 ->|
v1 ->|        |-> v4
     |-> v3 ->|
```

* may have parallel sub-components
* any vertex may have any number of outgoing edges
* any vertex may have any number of incoming edges

non-unique paths

* without any restriction ...
* vertices may be connected over more than one path
* non-relevant in the transitive closure
