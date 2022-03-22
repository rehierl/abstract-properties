
<!-- ======================================================================= -->
# the meaning of placing start- and end-tags

The previous discussion can be understood to describe how computers encode
(aka. serialize) document trees using the tag-based syntax in such a way that
a computer can decode (aka. deserialize) the exact same document tree. With
that in mind, the following must be understood to point out how we humans
must look at the tag soup of a document such that the document tree we want
to define will be decoded as intended.

Recall that each start-tag is understood to define a node and its absolute
position. Because of that, the subsequence of start-tags will be read as
defining a total node order (i.e. the document tree's pre-order trace).

```
<root> ... <n> ......................... </root>
           |-all-of--------------------------->|
```

In addition to that, a parser perceives a start-tag as the definition of the
beginning of the node's scope, which is understood to begin with the CE of
that scope and to extend over all-of the nodes subsequent to it. That is,
the node's scope is initially understood to end with the document's last node.
After all, when reaching the start-tag of a node, a parser has no means to
tell when, or even if at all, it will reach a matching end-tag at some point
in the future.

Recall that a parser sees a tag soup as a strict sequence of tags (i.e. one
after another), which is why a parser must follow the past-present-future
principle, based upon which the scope of an abstract property `s(p)` is
defined as an open interval that begins with the property's defining node
`n` and ends with the last node subsequent to it (i.e. `s(p) := [n,*]`).

```
<root> ... <n> ................. </n> ... </root>
           |-all-of-s(n)----------->|-none-of-->|
           |-some-of--------------------------->|
```

Since an end-tag is understood to mark the end of a scope, the placement of
an end-tag can be understood as a method to restrict the default scope such
that it ends before the last node of the pre-order trace is reached.

Note that an end-tag can therefore be seen as a method to reduce the default
unrestricted **all-of** quantifier to a well-defined **some-of** quantifier.
Put differently, a some-of quantifier can be defined by combining the all-of
quantifier with a none-of quantifier.
