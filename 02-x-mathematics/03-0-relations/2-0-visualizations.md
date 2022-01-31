
<!-- ======================================================================= -->
# graph-based visualizations

The following is a barebone introduction to graph-based visualizations,
intended to allow to read/understand subsequent visualizations of relations.

A (directed) graph `G := (V,E)` is an endo-relation that consists of a set of
vertices/nodes `V` and a set of 2-element sequences as its set of edges `E`.

The drawing of a graph consists of nodes (one for each vertex) and arrows (one
for each edge in the relation). As such, a visualization can be understood to
define the relation it visualizes in a more human-friendly way.

Despite that, one must always keep in mind that in principle
**each (visualized) graph is a mere visual representation**
of a strict formal definition in terms of vertices and edges.

<!-- ======================================================================= -->

```
horizontal    horizontal    vertical
(explicit)    (implicit)    (implicit)
==========    ==========    ==========
 a -> b        a - b         a
                             |
                             b
```

* `E := { (a,b) }`

A horizontal visualization will in general denote the orientation of each
edge by displaying an arrow with its head on the side of the 2nd vertex -
i.e. `a -> b` corresponds with edge `(a,b)`.

However, and since the drawing-order is by default from left-to-right, an
arrow head may be omitted. In such a case, the arrows need to be understood
to be oriented such that the 1st vertex of a node appears left of the arrow's
line `-`, and the 2nd vertex right of it. This may be referred to as the
default orientation of a headless arrow.

Similar to that, arrows in a vertical top-down visualization always need to
be understood to be oriented with the 1st vertex being above the arrow's line
`|`, and the 2nd vertex beneath of it.

Based on the above, each arrow always must be understood to represents a
directed edge. Put differently: There are **no undirected edges/arrows**
in the context of this discussion!

<!-- ======================================================================= -->
## semantics

```
(x,y) := (x presequent-to y)    (a presequent-to b)
============================    ===================
a -> b                          a -> b
```

In cases that are not clear enough, the semantical expression that is by default
associated with each edge/arrow may be explicitly specified. In addition to
that, and as a matter of clarity, the differing semantics of a particular
edge/arrow may be specified in a similar fashion.

Note that, since each edge is a sequence of nodes, and since an arrow points
from the edge's 1st to the edge's 2nd node, the "next-presequent-to" semantics
can be understood as **the default semantics**. That is, and unless specified
otherwise, each arrow can be "read" with the **next-presequent-to semantics**
in mind.

* by default, read `(a -> b)` as "(a next-presequent-to b)"
* by default, read `(a -> b)` as "(b next-subsequent-to a)"

<!-- ======================================================================= -->
## splitting

```
horizontal    horizontal    vertical      vertical      vertical
(explicit)    (implicit)    (implicit)    (implicit)    (reduced)
==========    ==========    ==========    ==========    =========
 a -|-> b      a -|- b         a              a             a
    |-> c         |- c         |             / \          -----
                             -----          b   c         b   c
                             |   |
                             b   c
```

* `E := { (a,b), (a,c) }`

Since only horizontal and vertial lines will be used to visualize the arrows,
some combination (as shown above) is required in order to denote two arrows
that originate from the same node (split).

As before, and since characters tend to enlarge a visual representation,
vertical visualizations may be reduced by dropping vertical lines.

<!-- ======================================================================= -->
## merging

```
a -|-> b -> c -|-> d
   |---------->|
```

* `E := { (a,b), (a,d), (b,c), (c,d) }`

As shown above, vertical lines may also be used to rejoin (merge) several
arrows that end in the same node.

```
(less clear)            (more clear)
====================    ====================
a -|-> b -> c -|-> d    a -> b -> c -> d
   |<----------|             |<---|
```

* `E := { (a,b), (b,c), (c,d), (c,b) }`

More intricate visualizations should be sufficiently clear enough for the
reader to determine the corresponding nodes of an arrow. As a matter of
clarity, reduced sets of edges may be specified that denote those edges
that may be difficult to unambiguously identifiy.

* `E := {.. (c,b) ..}`
