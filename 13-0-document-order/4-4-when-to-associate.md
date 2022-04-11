
- TODO - needs to be fleshed out

<!-- ======================================================================= -->
# when (not) to associate a node

The following examines if some node `n` can be associated with some property
`x` that is defined by node `x`. In addition to that, and since the tags of a
node trigger enter- and exit-events in a parser (i.e. enter and exit the scope
of a node), the following clarifies which event must be used when a node has
to be associated.

Recall that some property `x` which has node `x` as its defining node can only
apply to the nodes in its scope `s(x)`. Furthermore, the scope of a node can
only include its defining node `x` and those nodes subsequent to it. However,
not all the nodes subsequent to a defining node are guaranteed to be nodes in
`s(x)`. After all, a scope may be reduced by the defining node's end-tag.

Recall that the document order (i.e. the document tree's pre-order node order)
is order-preserving in regards to the document tree's tree order and also in
regards to the document tree's child order.

Recall that it is the start-tag of a node that defines a node and its position
within the document order. Based on that, the start-tag of a node can be said
to define if that node is subsequent to a defining node or not.

<!-- ======================================================================= -->
## (n presequent-to x) in the document order

```
.. <n> .. <x> ..
          |-s(x)->
```

- `n` is presequent to `x` in the document order
- property `x` is undefined when `n` is reached
- not if a node is presequent to the defining node of a porperty

<!-- ======================================================================= -->
## (n subsequent-to x) in the document order

```
.. <x> .. <n> ..
   |-s(x)------>
```

- thus far no issue, if `n` is subsequent to `x` in the document order
- property `x` is known when the start-tag of `n` is reached
- a node can only be associated with a property, if and only if
  that node is subsequent to the property's defining node

<!-- ======================================================================= -->
## introducing end-tags

- recall that an end-tag restricts the scope of a node
- a scope can not be assumed to always end with the document order
- the core difference between the document order and the tree order
- an end-tag states that there is no further subsequent node
  which still counts towards the corresponding scope
- an end-tag triggers the exit-event of a scope

<!-- ======================================================================= -->
## n presequent-to s(x)

```
.. <n> .. <x> .. </x> ..
          |-s(x)--->|
```

- `n` can not be associated with `x` since `n` is presequent to `x`
- property `x` is undefined when `n` is reached

<!-- ======================================================================= -->
## n subsequent-to s(x)

```
.. <x> .. </x> .. <n> ..
   |-s(x)--->|
```

- `n` can not be associated with `x` since `s(x)`
  has ended with `</x>` when `n` is reached
- in other words, `n` is no node in `s(x)`

<!-- ======================================================================= -->
## malformed markup - ignored

```
.., <x>, .., <n>, .., </x>, .., </n>, ..
    |-s(x)---------------|
             |-s(n)----------------|
     reduced |-s(n)-->|<-ignored-->|
```

- recall that markup is required to be well-formed
- implementations may reject to process malformed markup
- implementations may instead choose to reduce the scope
  of a node and dismiss/ignore its end-tag
- malformed markup is no basis for discussion

Note that an artificial restriction will produce a document tree that can not
accurately represent the input, it can only provide an approximation of such
a malformed input document. That is, the document and the resulting tree can
not be considered equivalent.

<!-- ======================================================================= -->
## s(n) subset-of s(x)

```
.. <x> .. <n> .. </n> .. </x> ..
   |-s(x)------------------>|
          |-s(n)--->|
```

- it is the start-tag of a node that defines **the order of a node**
- `n` can be associated while processing its start-tag and its end-tag
- because scope `s(x)` is still valid during both events

```
.. <x> .. <n> .. </n> .. </x> ..
   |-s(x)------------------>|
           |<------| associate? - no!
```

- even though, in this case, the exit-event of node `n` could be used to
  associate `n` with property `x`, one can state that such an association
  is in conflict with the document order
- after all, knowledge is applied to a node that is presequent to the event,
  which is in conflict with the orientation of the document order

in regards to the processing order

- can be understood to introduce a backwards-oriented dependency
- can be understood as an attempt to undo/redo a past event
- the scope of a node is strictly forwards-oriented

<!-- ======================================================================= -->
## s(n) superset-of s(x)

```
.. <n> .. <x> .. </x> .. </n> ..
          |-s(x)--->|
```

- `n` is defined by its start-tag and thus no node in `s(x)`
- at the time start-tag `<n>` is processed, property `x` is undefined
- at the time end-tag `</n>` is processed, scope `s(x)` has already ended

```
.. <n> .. <x> .. </x> .. </n> ..
    |<-----| associate? - no!
```

- `n` is presequent to `x` - the association is against the document order
- it is an error to associate a node with the property of a descendant
- regardless of when exactly one would want to establish the association
- e.g. while processing `<x>` or `</x>`

<!-- ======================================================================= -->
## conclusion - only while entering a scope

Note that it is the start-tag of a node that defines **the order of a node**.
Put differently, the start-tag of a node defines if a node is subsequent to
the defining node of a property.

- each node must be associated while entering its scope
- a node must be subsequent to the defining node of a scope

Recall that the document tree's tree order and also the document tree's
child order are embedded suborders to the document order. That is, the
document order is order preserving in regards to these suborders.

- it is against the document order to associate a node in any other way
- it is against the tree order and the child order to associate a node
  while not processing the node's start-tag

Note that a node can only be associated with a property, if and only if the
property's scope still **counts as being open**.  A node subsequent to a
defining node is no node in the property's scope, if that scope has already
ended once the node's start-tag is reached.

- a node is no node in a scope, if that scope has already ended

Note that **implementations create and finalize node objects** as soon as they
reach the start-tag of a node. After that, node objects may only be extended
by references to their child nodes, while remaining done/visited/finalized
in every other aspect.
