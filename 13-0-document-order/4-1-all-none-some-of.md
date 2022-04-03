
<!-- ======================================================================= -->
# a method to define some-of quantifiers

Each start-tag can be understood to define a node and its absolute position in
the document tree's pre-order trace. The subsequence of start-tags can thus be
understood to define the document tree's total pre-order trace - i.e. the
document tree's total pre-order node order.

```
<root> ... <n> ......................... </root>
           |-s(n)----------------------------->|
```

A parser reads a start-tag as the definition of an abstract property `p` that
has the start-tag's node `n` as its defining node (i.e. `d(p) := n`). Since
each start-tag can be understood to define a unique property of some kind,
the scope of a node `s(n)` can be understood to be defined based on the scope
`s(p)` of some abstract property - i.e. `s(n) := s(p)`.

That scope must be understood to begin with its characteristic element CE (i.e.
node `n`) and to extend over **all-of** the nodes subsequent to it. That is,
the node's scope is initially understood to end with the document's last node.
After all, when reaching the start-tag of a node, a parser has no means to tell
when, or even if at all, a matching end-tag will eventually be reached while
processing the remaining input tags. Consequently, the node's scope can be
understood to be defined as an open interval that begins with the defining
node `n` and ends with the last node subsequent to it - i.e. `s(n) := [n,*]`.

```
<root> ... <n> ................. </n> ... </root>
           |-all-of---------------->|-none-of-->|
           |-some-of--------------------------->|
```

Since an end-tag is understood to mark the end of a scope, the placement of an
end-tag can be understood as a method to restrict the (default) scope of a node
such that the scope ends before the last tag has been reached.

```
s(n) := PRE[<n>,*] \ PRE[</n>,*]
```

An end-tag can therefore be said to reduce an unrestricted **all-of** quantifier
based on a well-defined **some-of** quantifier. That is, a some-of quantifier
can be defined by based on an all-of quantifier in combination with a
well-defined **none-of** quantifier.

- `some-of := all-of \ none-of`
