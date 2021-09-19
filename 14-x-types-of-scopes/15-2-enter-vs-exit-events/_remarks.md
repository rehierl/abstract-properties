
<!-- ======================================================================= -->
- how an implementation needs to react to certain events

```
    |<- enter node n, declares property 'p' |
    |<- the scope of property 'p'         ->|
.. <n> .................................. </x> ..
    |-> link property with end-tag '</x>'   | onVisit(n)
    |          close the property's scope <-| onExitT1(x)
```

Since the exit event of a scope does in general not correspond with the event
of a node, and since the pre-order tree traversal algorithm focuses on a node
and its descendants in the un-ordered tree, implementations must map the exit
event of a type-2 and a type-3 scope onto the type-1 exit event of an ancestor.

Note that the node whose type-1 exit event is used to close the property's
(default) scope, will be referred to as the property's **parent container**.

Implementations must therefore **plan a scope's closure** when it reaches
the defining node of such a property. After that, the close operation can be
triggered when the type-1 exit event of the property's parent container is
executed. As such, the initialize-and-postpone approach may in general be
referred to as **a planned closure**.

<!-- ======================================================================= -->
