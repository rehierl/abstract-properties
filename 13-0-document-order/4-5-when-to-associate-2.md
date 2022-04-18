
<!-- ======================================================================= -->
## malformed markup - ignored

```
.., <x>, .., <n>, .., </x>, .., </n>, ..
    |-s(x)-------------->|
             |-s(n)--------------->| from the input
             |-s(n)-->|-ignored--->| reduced scope
```

As discussed before, the markup of a document must be well-formed, which is
why implementations may choose to (1) cancel processing malformed markup,
or (2) return an approximation of the input by reducing the scope of one or
more nodes via implicitly "repositioning" the corresponding end-tags.

Note that such an artificial restriction will produce a document tree that
can not accurately represent the input. It can only provide an approximation.
That is, the markup and the resulting document tree can not be equivalent.

In case of option (1), malformed markup can be treated to not exist at all.
In contrary to that, option (2) can be understood such that it transforms
the markup into a well-formed one. Hence, malformed markup can overall be
ignored, which leaves the cases discussed below.

<!-- ======================================================================= -->
## case 3.1: (s(n) disjoint-to s(x))

```
.. <n> .. </n> .. <x> .. </x> ..
   |-s(n)--->|    |-s(x)--->|
```

As before, start-tag `<n>` must be an element in scope `s(x)`, which
is not the case since end-tag `</n>` is presequent to start-tag `<x>`.
Because of that, node `n` **can not be associated** with node `x`.

```
.. <x> .. </x> .. <n> .. </n> ..
   |-s(x)--->|    |-s(n)--->|
```

For the same reason, node `n` **can not be associated** with node `x`,
if start-tag `<n>` is subsequent to end-tag `</x>`.

<!-- ======================================================================= -->
## case 3.2: (s(n) subset-of s(x))

Recall that node `x` is the defining node of property `x`, and that node `n`
is to be associated with that property, not vice versa.

```
.. <x> .. <n> .. </n> .. </x> ..
   |-s(x)------------------>|
          |-s(n)--->|
```

Since start-tag `<n>` and end-tag `</n>` are both elements in scope `s(x)`,
node `n` can technically be associated **while processing both tags**. After
all, scope `s(x)` is defined to be open during both events.

```
.. <x> .. <n> .. </n> .. </x> ..
   |-s(x)------------------>|
           |<------| associate? - no!
```

However, even though **the exit-event** of node `n` could be used to associate
node `n`, one can state that this particular association is in principle in
conflict with the document order. (Recall the past-present-future principle -
i.e. the PPF principle). After all, knowledge is then applied to a node that
is presequent to the corresponding event. In other words, knowledge is then
applied to a past event.

- can be understood as **an attempt to undo/redo past events**
- can be understood to be **against the orientation of the document order**
- in contrary to that, any scope is strictly forwards-oriented

Note that one will then have to ensure that the delayed association has no
implications on the associations of the contents in between both of tags.
That is, implementations will have to **revisit the contents** in between
in order to update the associations that were established until the end-tag
of that node was reached. This in order to guarantee consistent results.

Note that such a backwards-oriented association has shares characteristics
with **a temporal paradox**. One aspect is that a causal loop must be avoided
since this could trap/freeze an implementation in an endless loop.

- **no exit-event should be used to associate a node**

<!-- ======================================================================= -->
## case 3.3: (s(n) superset-of s(x))

Note that this time, start-tag `<n>` is presequent to start-tag `<x>`, and
that end-tag `</n>` is subsequent to end-tag `</x>`. None of the tags of
node `n` are therefore elements in scope `s(x)`.

```
.. <n> .. <x> .. </x> .. </n> ..
   |-s(n)------------------>|
          |-s(x)--->|
```

As before, if node `n` appears presequent to node `x`, then property `x` is
still unknown by the time start-tag `<n>` is reached. Because of that, node
`n` can not be associated with node `x`.

- `n` is defined by its start-tag and thus no node in `s(x)`
- node `x` and all of its properties are unknown when node `n` is reached
- node `n` **can not be associated** with node `x`

```
.. <n> .. <x> .. </x> .. </n> ..
    |<-----|-------|-------| associate? - NO!
```

Note that it is non-relevant when exactly one would want to associate node `n`
with node `x` - e.g. while processing start-tag `<n>`, start-tag `<x>`, end-tag
`</x>` or even end-tag `</n>`. That is because node `n` just isn't defined to
be a node in scope `s(x)`.

<!-- ======================================================================= -->
## conclusion - only while entering a scope

Recall that **the start-tag of a node defines a node and its order**. Put
differently, the start-tag of a node defines if a node is subsequent to
the defining node of a property.

- a node must be subsequent to the defining node of a scope

Furthermore, a node can only be associated with a property, if the property's
**scope still counts as being open**.  A node subsequent to a defining node
is however no node in the property's scope, if that scope has already ended
when the node's start-tag is reached.

- a node must be presequent to the end of a scope
- a node must be defined to be an element of a scope

Recall that the document tree's tree order and also the document tree's
child order are embedded suborders to the document order. That is, the
document order is order preserving in regards to these suborders. Hence,
to associate a node, any node, while processing its end-tag (i.e. while
exiting its scope) is in principle in conflict with the document order.

- any node must be **associated while entering its scope**

Note that **implementations create and finalize node objects** as soon as
they reach the start-tag of a node. After that, node objects will only be
extended by references to their child nodes, while remaining finalized in
every other aspect.
