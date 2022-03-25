
<!-- ======================================================================= -->
# a tag soup ain't no node tree

Recall that, if it exists, each scope ends with some last subsequent leaf `l`,
a descendant of the node's last child `lc`. And since `l` is a leaf, the inner
subset of that leaf is empty, which is why there is no further tag in between
the pair of tags of `l`.

```
   |-s(n)---------------------|-------|
.. |  <n>  | fc .. lc .. <l/> | </n>  | ..
   |-ce(n)-|-iss(n)-----------|-empty-|
```

Note that, as a matter of simplification, the pair of tags of any leaf, which
is such that its start-tag is next presequent to its matching end-tag (i.e.
`<l></l>`), may be merged into a self-closing tag (i.e. `<l/>`).

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-s(n)----------------------------------------|
```

Since `l` is the last subsequent leaf of `lc`, end-tag `</lc>` is located just
after end-tag `</l>`. Similar to that, and since `fc` and `lc` are both child
nodes of `n`, end-tag `</fc>` precedes start-tag `<lc>`.

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n-------------------------------------------|
       |-fc--------|    |-lc----------------|
                                |-l---|
```

As visualized above, the scopes defined by the pairs of tags of a document,
serialized while traversing a document tree, are either disjoint ex-or related
(**DI-RE**). That is, there is no pair of tags such that the corresponding
scopes overlap each other.

Due to the above, **the tag soup of a document encodes a hierarchy of scopes**,
based on a sequence of start- and end-tags. That is because none of the edges
of a document tree are actual elements in a tag soup, which is because these
edges are encoded into the relationships between the scopes. Consequently,
the tag soup of a document tree **does not define a document tree**.

Instead, a tag soup defines a hierarchy of scopes that corresponds with a
document tree. One must therefore keep in mind that a tag soup effectively
defines **a partial containment order** that is embedded as a partial suborder
into the total document order, the document tree's pre-order trace of nodes.

Because of that, and from a strict point of view, **parsers** read a hierarchy
of scopes from a tag soup. However, and due to the order of nodes (i.e. the
CE of each scope appears first in its scope), parsers do not have to explicitly
instanciate a hierarchy of scopes since the edges of a document tree can be
**decoded on the fly**.