
<!-- ======================================================================= -->
# types of (abstract) properties

Since there was thus far no assumption that abstract properties could have
anything in common, one can now assume that properties may exist that share
certain characteristics (e.g. a specific purpose, aka. semantics). Based on
that, one can assume the existence of certain **types of properties**, even
without knowing what these "types" exactly are (hence **abstract properties**).

```
(height)     (cursor)
l3 |           =|=|
l2 |      ======|=|
l1 |============|=| (width)
   | c1 - c2 - c3 |
```

For example, given the side scroller, and assuming that the properties that
are defined by each cell all are **properties of the same kind**, one can
simply **count** the number of those properties with which each cell is
associated. Based on that, cell `c3` can be said to be associated with `3`
such properties.

Note that one doesn't usually count things that have nothing in common.

```
(height)     (cursor)
l3 |           =|=|
l2 |      ======|=|
l1 |============|=| (width)
   | c1 - c2 - c3 |-> input tape
      1    2    3 |-> output tape
```

Based on the above, one can imagine **a Turing machine** that has the ordered
sequence of cells as an input tape, and an output tape to which it can write
the number of those properties with which the corresponding cell is associated.

At this point one can recall that each path graph is a tree, and that each node
in it has **a node level**. With that in mind, one can conclude that the number
of properties counted for each cell reflects the cell's node level. That is, if
the sequence of cells were to be visualized as a path graph.

Furthermore, one can observe that the node levels of the nodes in a path graph
are strictly monotone increasing. Consequently, there is one node (the root)
whose node level is minimal. In addition to that, there are no two nodes that
have the same node level.
