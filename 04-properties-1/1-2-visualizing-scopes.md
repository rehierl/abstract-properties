
<!-- ======================================================================= -->
# Visualizing scopes

As shown below, the scope of a property can be visualized by simply underlining
all of the nodes to which it applies:

```
a - b - c - d - e ->
        ============ p
```

Assuming that node `c` is understood to define property `p`, the scope of
that property can be understood to contain all the nodes within the open
interval `[c,*)` over the corresponding node order.

* `s(p) := [c,*) = { c, d, ... }`

```
       |-p-------------|
a - b -|- c - d - e -> |
       |===============|
```

If need be, one can extend the line that is used to highlight the nodes within
a scope, by simply drawing a box that has the line as one of its edges. Based
on that, it is visually unambiguous which nodes are included, and which nodes
are not. That is, one can visually determine the (ordered) set of nodes the
scope contains.

<!-- ======================================================================= -->
## Turing machines

```
a - b - c - d - e ->  |- input tape
        =p==========  |- output tape
```

Visualized as above, one can think of such a line to represent the output tape
of a **multi-tape/track turing machine** such that the tape, which is otherwise
empty, holds a symbol (unique to the property) in each cell that corresponds
with one of the nodes that is contained within the corresponding scope.

Alternatively, and in the (future) context of multiple properties, one can
associate a unique output tape with each property. This would allow to use
a shared symbol which is then used to indicate that the node above a marked
cell is within the scope of the tape's property.
