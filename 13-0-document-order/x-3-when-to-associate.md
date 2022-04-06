
<!-- ======================================================================= -->
# when to associate a node

The following examines if a node in some scope `s(n)` can be counted towards
an abstract property that is defined by some other node `x`.

Recall that a property that has node `x` as its defining node can only apply
to a node, if that node is a node in scope `s(x)`.

<!-- ======================================================================= -->
## disjoint - no, not at all

```
    |-s(x)-----------|     |-s(n)-----------|
.., | <x>, .., </x>, | .., | <n>, .., </n>, | ..
    |----------------|     |----------------|
```

For obvious reasons, if node `n` is not located within the scope of `x` (i.e.
both scopes are disjoint), then node `n` can not be associated with `x`. That
is because no such association would be valid since scope `s(x)` ends with
end-tag `</x>`.

<!-- ======================================================================= -->
## malformed - no basis for discussion

```
.., <x>, .., <n>, .., </x>, .., </n>, ..
    |-s(x)---------------|
             |-s(n)----------------|
```

In the case of a malformed input document such that some scope `s(n)` reaches
out of some other scope `s(x)`, an implementation might choose to restrict
scope `s(n)` to a subset of `s(x)`. However, such an artificial restriction
will produce a document tree that can not accurately represent the input, it
can merely provide an approximation of such an input document. That is, the
document and the resulting tree are not equivalent.

Note that the artificial restriction of `s(n)` to a subset of `s(x)` will
transform this case into the following *related case*.

<!-- ======================================================================= -->
## related - while entering - ok

```
.., <x>, .., <n>, .., </n>, .., </x>, ..
    |-s(x)-------------------------|
             |-s(n)------|
```

Since node `n` is an element in scope `s(x)` node `n` can be associated with
`x` **while that node and its scope is being processed**. That is, node `n`
can be associated while its **start-tag** is being processed.

<!-- ======================================================================= -->
## related - while exiting - no (!)

```
.., <x>, .., <n>, .., </n>, .., </x>, ..
    |-s(x)-------------------------|
             |<-associate-|
```

Due to the above one might be tempted to associate node `n` while processing
its **end-tag**. Although, in this particular example, it will yield the same
result, one must keep in mind that the start-tag of node `n` has already been
processed. That is, the corresponding node has been created and finalized.

Note that associating a node while processing its end-tag is in principle
**in conflict with the past-present-future principle** since such an
association must be understood to establish **a backward-oriented dependency**
and, because of that, must be understood as an attempt to undo/redo a past
event.

Recall that the scope of a property/node is strictly forwards-oriented. It
begins with the defining node and contains every node that is subsequent to
it. In that regards, the end-tag of a scope can be understood to state that
there will be no further subsequent node.

<!-- ======================================================================= -->
## conclusion - only while visting/entering

Node `n` must be associated with the scope of another node `x`, while processing
the **visit-event** of `n` (i.e. during the **enter-event** of `s(n)`), if and
only if `(n in s(x))` is true.

In other words: Any operation that builds upon the node order of a document
must be executed while a node is being visited.
