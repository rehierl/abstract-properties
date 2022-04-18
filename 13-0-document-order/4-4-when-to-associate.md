
<!-- ======================================================================= -->
# when (not) to associate a node

The following examines, if some node `n` can be associated with some property
`x`, that has node `x` as its defining node. In addition to that, and since
the tags of a node can be understood to trigger enter- and exit-events (i.e.
enter and exit the scope of a node), the following will also examine which
events can be used to associate a node with a property.

Note that "associate some node with a property that has some other node as its
defining node" will be shortened to **associate a node with some other node**.
That is, the latter node needs to be understood as the defining node of some
property, which allows to treat that node as the property's representative.

Recall that the document order (i.e. the document tree's pre-order node order)
is order-preserving in regards to the document tree's tree order and also in
regards to its child order. Because of that, the edges of the corresponding
order relations are all oriented the exact same way.

Recall that it is the start-tag of a node which defines a node and its position
in the document order. Because of that, the start-tag of a node can be said to
define if a node is subsequent to some other node. This can be understood to
require that **each node must be associated while processing its start-tag** -
i.e. **while entering its scope**.

<!-- ======================================================================= -->
## case 1.1: (n presequent-to x)

```
-> document/processing order ->
.. <n> .. <x> ..
          |-s(x)->
```

Since node `n` appears presequent to node `x`, property `x` is still unknown by
the time an implementation reaches node `n`. Because of that, node `n` can not
be associated with property/node `x`.

- node `n` is presequent to node `x`
- property `x` is unknown by the time node `n` is reached
- node `n` **can not be associated** with node `x`

<!-- ======================================================================= -->
## case 1.2: (n subsequent-to x)

```
.. <x> .. <n> ..
   |-s(x)------>
```

Since node `n` appears subsequent to node `x`, property `x` is defined by the
time node `n` is reached. Because of that, node `n` can be associated with
property/node `x`.

- node `n` is subsequent to node `x`
- property `x` is defined by the time node `n` is reached
- node `n` **can be associated** with node `x`

<!-- ======================================================================= -->
## introducing end-tags

```
        .. <x> .. </x> ..
|-unknown->|-open--->|-closed->|
           |-s(x)--->|
```

Recall that a property only applies to the nodes in its scope `s(x)`, which
includes the property's defining node `x` and those nodes subsequent to it.
However, not all of the nodes that are subsequent to a defining node are
necessarily also defined to be nodes in that scope. After all, a scope may
be **restricted by the end-tag of its defining node**.

Note that an end-tag can be understood to state that no node subsequent to it
belongs to the scope that end-tag is defined to close. After all, the scope is
then defined to end with that end-tag, not with the last node in the document
order. Hence, an end-tag can be understood to state that no more node will
follow which still adds towards the corresponding scope.

<!-- ======================================================================= -->
## case 2.1: (n presequent-to s(x))

```
.. <n> .. <x> .. </x> ..
          |-s(x)--->|
```

As before, if node `n` appears presequent to node `x`, then property `x` is
still unknown by the time node `n` is reached. Because of that, node `n` can
not be associated with node `x`.

- node `n` is presequent to node `x`
- property `x` is undefined by the time node `n` is reached
- node `n` **can not be associated** with node `x`

<!-- ======================================================================= -->
## case 2.2: (n subsequent-to s(x))

```
.. <x> .. </x> .. <n> ..
   |-s(x)--->|
```

Similar to before, node `n` is subsequent to node `x`. However, node `n` is
also subsequent to the defining node's end-tag. Because of that, scope `s(x)`
is defined to **end before** node `n` is reached. Node `n` can therefore not
be associated with node `x`.

- node `n` is subsequent to node `x`
- node `n` is subsequent to end-tag `</x>`
- node `n` is subsequent to the exit-event of scope `s(x)`
- node `n` is *not* defined to be a node in scope `s(x)`
- node `n` **can not be associated** with node `x`

<!-- ======================================================================= -->
## case 2.3: (n subsequent-to s(x))

```
.. <x> .. <n> .. </x> ..
   |-s(x)---------->|
```

Similar to before, node `n` is subsequent to node `x`. However, node `n` is
still presequent to the defining node's end-tag. Because of that, scope `s(x)`
is defined to **end after** node `n` is reached. Node `n` can therefore be
associated with node `x`.

- node `n` is subsequent to node `x`
- node `n` is presequent to end-tag `</x>`
- node `n` is presequent to the exit-event of scope `s(x)`
- node `n` is defined to be a node in scope `s(x)`
- node `n` **can be associated** with node `x`
