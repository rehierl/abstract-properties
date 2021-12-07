
<!-- ======================================================================= -->
# Forest/Hierarchy of edges

Forests and hierarchies of edges can be defined as follows.

<!-- ======================================================================= -->
## a forest of edges (F)

A set of edges `E` may be described as **a forest of edges**,
if the following requirements are met.

* (R0) `E` is a partial setup of edges.

Note that the edges in such a forest may be disjoint (DI), related (RE),
or even overlap (OV) each other - i.e. the **DI-RE-OV** case.

Recall that, despite the modified related-to operator (i.e. a path-based
definition) and the relationships allowed (i.e. DI-RE-OV), a forest of edges
can be described as a setup of strings.

<!-- ======================================================================= -->
## a hierarchy of edges (H)

A set of edges `E` may be described as **a hierarchy of edges**,
if the following requirements are met.

* (R0) `E` is a forest of edges.
* (R1) `E` has one and only one root node/edge.

Note that a hierarchy of edges `E` has the following properties.

* `(#RN(E) == 1)` must be true.
* `(#E > 0)` - A hierarchy is always non-empty.
* Each node has no ex-or one parent.
* Each node may have any number of child nodes.
* Each node has a unique rooted path (of nodes).

Note that there is a 1:1 relationship between the root edge of a hierarchy
of edges and the source node of that edge. Because of that, one can continue
to use the more common description "root node" rather than the more accurate
description "root edge".

Note that even the edges in a hierarchy may be disjoint (DI), related (RE),
or even overlap (OV) each other - i.e. still the DI-RE-OV case.
