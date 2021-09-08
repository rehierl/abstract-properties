
<!-- ======================================================================= -->
# a tag soup ain't no node tree

```
   |-s(n)--------------------------|
.. |  <n>  | fc .. lc .. l | </n>  | ..
   |-ce(n)-|-iss(n)--------|-empty-|
```

As mentioned earlier, a hierarchy of scopes corresponds with a node tree. In
addition to that, each scope is the union of two disjoint subsets, an inner
subset of nodes `iss(n)`, which connects a node's scope `s(n)` with the scopes
of its descendants, and a characteristic subset `css(n)`, which allows to
identify the scope amongst the scopes of the node's ancestors.

Furthermore, a hierarchy of scopes that corresponds with a node tree is such
that `css(n)` of each scope consists of one characteristic element `ce(n)`
only, which can be described as the scope's representative. Based on that,
one can conclude that **any start-tag denotes the CE of a scope**.

```
   |-s(n)-----------------------------|
.. |  <n>  | fc .. lc .. <l/> | </n>  | ..
   |-ce(n)-|-iss(n)-----------|-empty-|
```

Recall that each scope ends with the last subsequent leaf `l` of the node's
last child `lc`. And since `l` is a leaf, the inner subset `iss(l)` of that
leaf is empty, which is why there is no further node in between `<l>` and
`</l>`.

Note that, as a matter of simplification, a start-tag that is directly
followed by its end-tag (i.e. `<l></l>`) may be expressed as `<l/>`.

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-s(n)----------------------------------------|
```

Since `l` is the last subsequent descendant of `lc`, the end-tag `</lc>` will
be located just after end-tag `</l>`, or depending on the encoding just after
`<l/>`. Similar to that, and since `fc` and `lc` are both child nodes to `n`,
the end tag `</fc>` will precede the start tag `<lc>`.

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n-------------------------------------------|
       |-fc--------|    |-lc----------------|
                                |-l---|
```

As can be seen above, the scopes defined by the pairs of tags, written while
traversing a document tree in pre-order, are either disjoint exor related
(**DI-RE**). That is, there is no pair of tags such that the corresponding
scopes overlap each other.

Note that a tag soup does not define any of the edges of the document tree.
These are encoded in the relationships between the scopes of each node.

Due to the above, the tag soup of a document is the encoding of a hierarchy
of scopes, defined based on a sequence of start-tags and end-tags. Because
of that, **the tag soup of a document** does not define a document tree.

Instead, a tag soup defines a hierarchy of scopes that corresponds with a
document tree. One must therefore keep in mind that a tag soup effectively
defines **a partial containment order** that is embedded as a suborder into
the total document order, the document tree's pre-order trace of nodes.

Because of that, and from a strict point of view, **parsers** read a hierarchy
of scopes from a tag soup. However, and due to the order of nodes (i.e. the
CE of each scope appears first), parsers do not have to explicitly instanciate
a hierarchy of scopes since the edges of the document tree can be decoded on
the fly.
