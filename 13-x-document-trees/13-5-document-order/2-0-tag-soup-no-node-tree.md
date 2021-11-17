
<!-- ======================================================================= -->
# a tag soup ain't no node tree

```
   |-s(n)------------------|-------|
.. |  <n>  | fc .. lc .. l | </n>  | ..
   |-ce(n)-|-iss(n)--------|-empty-|
```

As mentioned earlier, a hierarchy of scopes corresponds with a node tree. In
addition to that, each scope is the union of two disjoint subsets, an inner
subset of nodes `iss(n)`, which connects the scope of a node `s(n)` with the
scopes of its descendants, and a characteristic subset `css(n)`, which allows
to identify the scope amongst the scopes of a node's ancestors.

Furthermore, a hierarchy of scopes that corresponds with a node tree is such
that the CSS of each scope consists of one characteristic element `ce(n)` only.
Based on that one can conclude that **each start-tag denotes the CE of a scope**.

```
   |-s(n)---------------------|-------|
.. |  <n>  | fc .. lc .. <l/> | </n>  | ..
   |-ce(n)-|-iss(n)-----------|-empty-|
```

Recall that each scope ends with the last subsequent leaf `l` of the node's
last child `lc`, if it exists. And since `l` is a leaf, the inner subset of
that leaf is empty, which is why there is no further tag in between the tags
of `l`.

Note that, as a matter of simplification, a pair of tags which is such that
its start tag is next presequent to its matching end tag (i.e. `<l></l>`) may
be merged into a self-closing start-tag (i.e. `<l/>`).

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-s(n)----------------------------------------|
```

Since `l` is the last subsequent leaf of `lc`, end-tag `</lc>` is located just
after end-tag `</l>`. Similar to that, and since `fc` and `lc` are both child
nodes to `n`, end-tag `</fc>` precedes start-tag `<lc>`.

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n-------------------------------------------|
       |-fc--------|    |-lc----------------|
                                |-l---|
```

As can be seen above, the scopes defined by the pairs of tags of a document,
written while traversing a document tree in pre-order, are either disjoint
exor related (**DI-RE**). That is, there is no pair of tags such that the
corresponding scopes overlap each other.

Note that the tag soup of a document does not define any of the edges of the
document tree. These are encoded in the relationships between the scopes of
each node.

Due to the above, **the tag soup of a document encodes a hierarchy of scopes**,
defined based on a sequence of start-tags and end-tags. Because of that, the
tag soup of a document does not define a document tree.

Instead, a tag soup defines a hierarchy of scopes that corresponds with a
document tree. One must therefore keep in mind that a tag soup effectively
defines **a partial containment order** that is embedded as a partial suborder
into the total document order, the document tree's pre-order trace of nodes.

Because of that, and from a strict point of view, **parsers** read a hierarchy
of scopes from a tag soup. However, and due to the order of nodes (i.e. the
CE of each scope appears first), parsers do not have to explicitly instanciate
a hierarchy of scopes since the edges of the document tree can be decoded on
the fly.
