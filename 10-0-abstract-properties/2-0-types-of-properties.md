
<!-- ======================================================================= -->
# types of (abstract) properties

Since there was thus far no assumption that abstract properties could have
anything in common, one can now assume that properties may exist which have
certain characteristics (e.g. a specific purpose, aka. semantics) in common.
Consequently, one can assume the existence of certain **types of properties**,
even without knowing what these "types" exactly are.

```
(height)
l3 |           =====|
l2 | ¤    ==========|
l1 |================| (width)
   | c1 - c2 - c3 ->|
```

For example, given the side scroller, and assuming that the properties that
are defined by each cell all are **properties of the same kind**, one can
simply **count** the number of those properties with which each cell is
associated.

Note that one doesn't usually count things that have nothing in common.

```
(height)     (cursor)
l3 |           =|==|
l2 | ¤    ======|==|
l1 |============|==| (width)
   | c1 - c2 - c3  |-> input tape
      1    2    3  |-> output tape
```

Based on that, one can imagine **a Turing machine** that has the ordered
sequence of cells as an input tape, and an output tape to which it can write
the number of those properties with which the corresponding cell is associated.

Note that since properties of the same kind are merely counted, it isn't even
essential to know which concrete properties they are. That is, it doesn't matter
if these properties represent colors, some weight, or some other characteristic.
(hence - **abstract properties**). One only needs to know that they have
something in common.

At this point one can notice that each path graph is a tree, and that each node
in it has **a node level**. With that in mind, one can conclude that the number
of properties counted for each cell reflects the cell's node level. That is,
if the sequence of cells were to be visualized as an actual path graph.

One can therefore conclude, that the node levels of the nodes in a path graph
are strictly monotone increasing. Consequently, there is one node (the root)
whose node level is minimal. In addition to that, there are no two nodes that
have the exact same node level.
