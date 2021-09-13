
<!-- ======================================================================= -->
## enter/exit events

So, how can an implementation determine when to close a property's scope?

```
n1, n2, n3, n4, n5, ..., n6, n7, n8, n9, n10 | - a pre-order trace
   enter ->|--|<- exit                       | - enter/exit/visit node n4
   enter ->|-------------------|<- exit      | - enter/exit the scope of n4
```

Due to the stream-based perspective on a property, a property and its scope
can both be said to be associated with an open/enter and a close/exit event,
which will in general be referred to as the **enter/exit events** of a scope,
or as the scope's **open/close events**.

Note that, similar to the tags of a node, the enter/exit events of a scope
enclose all the nodes within a property's scope. That is, in regards to the
pre-order trace of a tree, there may in general be more than one node in
between both events.

Likewise, a node is said to be entered and exited while being **visited**.
That is, a node can also be said to be associated with enter/exit events.
However, the events of a node only enclose the corresponding node. Because
of that, the "visit" of a node needs to be seen as an indivisible composite
atomic operation. That is, no node will be visited while another node is
still in the process of being visited.

Based on that, the enter event of a defining node corresponds with the enter
event of a property's scope. However, the exit event of a property's scope
does not necessarily correspond with the exit event of the scope's defining
node.

Note that, only in the case of a type-0 property, the property's exit event
corresponds with the exit event of its defining node.

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

Implementations must therefore initialize a scope's closure when it reaches
the defining node of such a property. After that, the close operation can be
triggered when the type-1 exit event of the property's parent container is
executed. As such, the initialize-and-postpone approach may in general be
referred to as **the planned closure** of a property's scope.
