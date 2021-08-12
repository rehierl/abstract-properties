
<!-- ======================================================================= -->
# Turing machines

```
a - b - c - d - e ->  |-> input tape
       -p-----------  |-> output tape
```

Visualized as above, one can think of such a line to represent the output tape
of a **multi-tape/track turing machine** such that the tape, which is otherwise
empty, holds a symbol (unique to the property) in each cell that corresponds
with one of the nodes that is contained within the corresponding scope.

Alternatively, and in the (future) context of multiple shared properties, one
can associate a unique output tape with each property. This allows to use a
shared symbol which is then used to indicate that the node above a marked cell
is within the scope of the tape's property.
