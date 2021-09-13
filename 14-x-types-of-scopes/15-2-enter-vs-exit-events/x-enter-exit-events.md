
<!-- ======================================================================= -->
# The enter-/exit-event of a scope

Since the sought-after sub-orders need to begin with a property's first node
and end with a property's last node, and since these sub-orders need to be
continuous in regards to a tree's pre-order trace, these sub-orders need to
be substrings to a pre-order trace.

The pre-order traces of a property's defining node satisfies all of the above
requirements. Because of that, the pre-order traces of a defining node must
be used to define the scope of a property. Based on that, properties and
their scopes can be loosely described as the scopes of their defining nodes.

* the scope of a property <=> the scope of a node <=> a pre-order trace

Note that the term "pre-order trace" focuses in general on a node and all of
its descendants (i.e. an induced subtree/suffix). In other words, the focus
is on sets of nodes which, based on the pre-order rule, are serialized into
total orders, each of which have one leaf node only.

Note that, since a partial order has in general more than one last node (i.e.
its leaf nodes), a tree's pre-order traversal must be taken into account. After
all, one still needs to be able to distinguish the "last" leaf of a sub-order
from all the other leaf nodes.

<!-- ======================================================================= -->
## the scopes of a (defining) node

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-| type-0
t1-scope(n)            |-- type-1 -----|
t2-scope(n)            |-- type-2 ----------------------|
t3-scope(n)            |-- type-3 ------------------------------|
```

Recall that the t1 scope of node `n` ends with its end-tag (`</n>`), and
its t2 scope with the end-tag of its parent (`</p>`). In contrary to that,
the t3 scope of node `n` ends with the end-tag of the tree's root (`</r>`).

Unlike a start-tag, an end-tag does however not correspond with a node.
That is, an end-tag appears to be located in between two nodes, which is
why the end-tag of a node only marks the end of its pre-order trace in
regards to the un-ordered tree (i.e. one such trace).

In addition to that, the end-tag of a parent marks the end of one or more
pre-order traces in regards to the ordered tree (i.e. one such trace per
former child). That is, the pre-order trace of a node in the ordered tree
ends with the end-tag of its parent. Furthermore, the end-tag of a tree's
root marks the end of the t3 scopes of its descendants.

Since each end-tag in general corresponds with the scopes of more than one
node, implementations need to have the means to **determine which scopes
to close** when reaching a given end-tag. After all, an end-tag may in
general correspond with the end of any number of scopes.

* the t1 scope of the tag's defining node
* the t2 scopes of the node's child nodes
* the t3 scopes of the root's descendants

Note that a property's scope is **forwards oriented** (i.e. along the edges).
In contrary to that, the decision to close the scope of a property is
**backwards oriented** (i.e. against the edges). That is, an implementation
needs to maintain a memory of those events it encountered in the past to
determine which scopes to close with a given end-tag.

<!-- ======================================================================= -->
## entering and exiting a scope/node

```
|<- open/enter a scope       |<- enter a node
|----------------------|     |----------------|
|   scope of a node    |     |  visit a node  |
|----------------------|     |----------------|
  close/exit a scope ->|        exit a node ->|
```

Based on the above, the scope of a property can be understood to be entered
once the property's defining node is reached, and exited after reaching the
property's last node. That is, **a scope has an enter and an exit event** or,
depending on one's current point of view (e.g. the stream-based perspective),
**an open and a close event**.

Similar to the scope of a property, nodes can in general be said to be entered
and exited during their visit. Because of that, the terms "visit", "enter"
and "exit" need to be clarified in regards to processing the nodes of a tree:

When an implementation begins to visit a node, an implementation is said to
**enter** the node. At that point, an implementation begins to execute those
operations that are associated with the node's **visit**. That is, the visit
of a node corresponds with a set of those operations that have to be executed
during the node's visit. Once the last operation has been executed, an
implementation is understood to **exit** the corresponding node. That is, and
similar to the scope of a property, one can in general speak of a node as
having **an enter and an exit event**.

Note that from an extreme theoretical point of view one could state that there
are no such node events. That is because all of these events are effectively
the events of one or more scopes. As such, and similar to the existence of
ordered trees, it can be stated that the enter/exits events of a node don't
actually exist.

Note that the above point of view is strict since the term "visit" must be
understood to group together all those operations that are directly related
to a node. To be more accurate, no operation of a node can be executed while
the operations of another node are still being processed. That is, no node
is entered or exited while another node is still being visited. The visit
of a node must therefore be seen as **an indivisible atomic operation**.

```
visit(s) := <enter-s> "visit-s" </exit-s>         | - the general pattern
<enter-s> .. <enter-t> .. </exit-s> .. </exit-t>  | - no overlap allowed
<enter-s> .. </exit-s> <enter-t> .. </exit-t>     | - one after another
```

Recall that all the nodes are visited one after another, in a strict orderly
fashion. That is, in the node order of a tree's pre-order trace.

```
n1, n2, n3, n4, n5, ..., n6, n7, n8, n9, n10  | - a pre-order trace
   enter ->|--|<- exit                        | - enter/exit/visit node n4
   enter ->|-------------------|<- exit       | - enter/exit the scope of n4
```

Due to the above, and in contrary to the enter/exit events of a scope, the
enter/exit events of a node enclose one node only. That is, the enter/exit
events of a node correspond with the enter/exit events of the node's type-0
scope. However, even though the enter event of a node corresponds with the
enter event of all the node's scopes, the same does not in general apply to
the node's exit event.

<!-- ======================================================================= -->
## a sequence of triggered events

So which node event corresponds with the exit event of a given scope? Is it
the exit event of the scope's last node, the enter event of the next node
subsequent to it, or is it some other event?

Based on that, the difficulty of an implementation is to map the abstract
exit event of a given scope onto some concrete event. In order to answer
these questions, one therfore first has to take a closer look at the basic
pseudo code of a pre-order tree traversal:

```
traverseInPreOrder(n) {
  //- process "<n>"
  onEnter(n)
  onVisit(n)
  onExitT0(n)

  //- process the descendants
  child = n.firstChild
  while(child != null) {
    traverseInPreOrder(child)
    child = child.nextSibling
  }

  //- process "</n>"
  onExitT1(n)
}
```

Note that an `onExitTX(n)` call is intended to represent the exit event of
scope `tX` of node `n`. Also, `onExitT0(n)` corresponds with the exit event
`onExit(n)` of node `n`.

Note that `onEnter(n)` and `onExit(n)` can both be merged into `onVisit(n)`.
That is, the enter/exit events of a node can be understood as theoretical
events which are triggered when an implementation starts/stops to execute
`onVisit(n)`.

Note that there are no `onExitT2(n)` and also no `onExitT3(n)` calls. That
is because these events correspond with the `onExitT1(a)` call of an ancestor
`a` of node `n` (i.e. its parent, or the tree's root). Because of that, the
exit event of a type-2 and a type-3 scope still need to be mapped onto the
enter/exit events of a node, or the exit event of a type-1 scope.

Since the tree traversal algorithm can easily be used to produce the pre-order
trace of a tree, and even its tag-based serialization, the **tag-based syntax**
can be said to focus on a node and its descendants in the un-ordered tree. That
is, this syntax can be understood to focus on type-0 (i.e. `<n>`) and on type-1
scopes (i.e. `</n>`) only.

In addition to that, the pre-order trace of a tree can be understood as **a
sequence of triggered events**. In order to see that, one only needs to use
the `onX(n)` calls to output tokens which reflect the triggered events/calls.

```
.., visit-n, exitT0-n, visit-c1, .., exitT1-n, .., exitT1-p, .., exitT1-r
   |- type-0 scope -|
   |- type-1 scope -------------------------|
   |- type-2 scope ---------------------------------------|
   |- type-3 scope -----------------------------------------------------|
```

Note that the enter/visit event of a parent's first child directly follows
a parent's exit event. Also, the end-tag of a last child (i.e. the child's
t1-exit event) directly precedes the t1-exit event of its parent. That is,
the t1-exit event of a last subsequent descendant precedes the t1-exit
event of an ancestor with no enter/visit event in between (i.e. a substring
of end-tags).

<!-- ======================================================================= -->
## planned closure

As mentioned above, each t1-exit event may correspond with the exit event of
any number of scopes. Because of that, an implementation must maintain a memory
of past events which allow an implementation to determine the scopes that need
to be closed when exiting a node's type-1 scope.

```
    |<- enter node n, determine the scope's type ->|
.. <n> .......................................... </x> ..
    |-> and associate it with end-tag '</x>'       | onVisit(n)
    |                            close the scope <-| onExitT1(x)
```

As soon as an implementation enters/visits a node `n`, it is assumed to have
the means to determine that node `n` is the defining node of property `p` and
that the property's scope ends with the t1-exit event of node `x`.

Since `x` is either the node itself (i.e. `n`), its parent (i.e. `p`) or even
the tree's root (i.e. `r`), the corresponding node has already been entered.
In addition to that, the t1-exit events have not yet been triggered. Hence,
the t1-exit events of those nodes are guaranteed to be executed at some later
point in time (.. assumed that no input errors need to be taken into account).

Furthermore, and if `x` is not the node itself, `x` is guaranteed to be an
ancestor of `n`. Because of that, an implementation can access the object that
represents node `x` (i.e. via the rooted path of node `n`). An implementation
therefore has the means to attach information with said object. That is, an
implementation can link/associate node `x` with the property whose scope ends
with its t1-exit event. Consequently, and once the t1-exit event of node `x`
is triggered, the link that was established earlier can be used to close the
property's scope.

Note that the node whose type-1 exit event is used to close the property's
(default) scope, will be referred to as the property's **parent container**.

<!-- ======================================================================= -->
## a pseudo-code example

- pseudo code (2)

<!-- ======================================================================= -->
## remarks

Since it is not possible to generically pin point the last node of a scope
(i.e. a node may have any number of descendants) and since it is not even
guaranteed that a node has a subsequent sibling, the t1-exit event of a node
must be used to close the corresponding scopes. Because of that, one can not
define the scope of a property as a closed interval (i.e. `[first,last]`)
and not even as an open interval of nodes (i.e. `[first,next(`).

However, one can still loosely speak of a scope as "ends with its last node",
or as "ends with the visit of the next subsequent node". That is, for as long
as one keeps in mind that the accurate description would be that the scope of
a property in general **ends in between two such nodes**.

Note that scopes must be closed explicitly since leaving a scope open runs the
risk of associating a property with nodes that are not defined to be within
the corresponding scope. Because of that, associations past the end of a scope
represent implementation errors.

Note that, in addition to obvious input errors, production code will have to
take into account that a root could be misused to declare a type-2/3 property.
In these cases, such declarations must be ignored.

Note that extensions, such as rank values, may in principle close a scope
before the corresponding end-tag is reached. Based on that, one can speak of
**default scopes**. Implementations must therefore take into account that a
close operation may be triggered more than once.

Note that, depending on property definitions, a specific **closing order**
may be required. That is because a descendant scope will in general have to
be closed before its ancestor scopes (i.e. in case of a section hierarchy).
Obviously, the above algorithm does not take such a closing order into account.
