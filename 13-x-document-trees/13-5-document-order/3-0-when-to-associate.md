
<!-- ======================================================================= -->
# when to associate a node

```
    |-scope(n)------------|---------|
.., | <n>,      | ..,     | </n>,   | ..
    |-start-tag-|-content-|-end-tag-|
```

Recall that each start-tag corresponds with a node. Because of that, one must
keep in mind that, when the node's **start-tag** is being processed, one has
already entered the node's scope. In contrary to that, and since an end-tag
does not translate into any node, one must keep in mind that, when the node's
**end-tag** is being processed, one has already exited the node's scope.

<!-- ======================================================================= -->
## disjoint - no, not at all

```
    |-s(x)-----------|     |-s(n)-----------|
.., | <x>, .., </x>, | .., | <n>, .., </n>, | ..
    |----------------|     |----------------|
```

For obvious reasons, if node `n` is not located within the scope of `x` (i.e.
both scopes are disjoint), then `n` can not be associated with `x`. That is
because no such association would be valid since `s(x)` ends with `</x>`.

<!-- ======================================================================= -->
## malformed - no basis for discussion

```
    |-s(x)----------------|
.., <x>, .., <n>, .., </x>, .., </n>, ..
             |-s(n)-?-|
```

In the case of malformed content such that `s(n)` reaches out of `s(x)`, an
implementation may choose to restrict `s(n)` to a subset of `s(x)`. Despite
that, and due to its ambiguous nature, such malformed content can not be
used as the basis of clear definitions.

Note that there are two ways to look at malformed content such as the above:
(1) it does not correspond with a proper hierarchy of scopes, or (2) reducing
the scope of `n` to the scope of `x` can not accurately represent the input.

Note that, as can be seen above, a parser has no means to "fix" malformed
content. That is, broken content is guaranteed to yield broken results.

<!-- ======================================================================= -->
## related - while entering - ok

```
.., <x>, .., <n>, .., </n>, .., </x>, ..
    |-s(x)-------------------------|
             |-s(n)-------|
```

Since node `n` is an element in scope `s(x)` node `n` can be associated with
`x` **while that node is being visited**. That is, `n` can be associated while
the **enter-event** of `n` is being processed. There is no issue with that
since the visit-event corresponds with the node's absolute position.

<!-- ======================================================================= -->
## related - while exiting - no (!)

```
.., <x>, .., <n>, .., </n>, .., </x>, ..
    |-s(x)-------------------------|
             |<-associate-|
```

Due to the above one might be tempted to associate node `n` while processing
the **exit-event** of its scope. Although, in this particular example, it will
yield the same result, one must keep in mind that `n` has already been visited.

Note that associating a node while processing the exit-event of its scope is
**in conflict with the past-present-future principle**. That is, such an
association must be understood to establish **a backward-oriented dependency**
and, because of that, in principle as an attempt to undo/redo a past event.

Recall that the scope of a property/node is strictly forwards-oriented. It
begins with the defining node and contains every node that is subsequent to
it. (In that regards, the end-tag of a scope can be understood to state that
there will be no further subsequent node).

<!-- ======================================================================= -->
## summary - only while visting/entering

Node `n` must be associated with the scope of another node `x`, during the
**visit-event** of `n` (i.e. during the **enter-event** of `s(n)`), if -
and only if - `(n in s(x))` is true.

In other words: Any operation that builds upon the node order of a document
must be executed while a node is being visited.
