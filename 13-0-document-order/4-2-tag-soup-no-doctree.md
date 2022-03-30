
<!-- ======================================================================= -->
# a tag soup ain't no node tree

```
   |-s(n)---------------------|-------|
.. |  <n>  | fc .. lc .. <l/> | </n>  | ..
   |-ce(n)-|-iss(n)-----------|-empty-|
```

Each scope ends with some last subsequent leaf `l`, in general a descendant of
the node's last child `lc`. And since the inner subset of that leaf is empty,
there is no further tag/node in between the pair of tags of leaf `l`.

Note that, as a matter of simplification, the pair of tags of any leaf, which
is such that its start-tag is next presequent to its end-tag (i.e. `<l></l>`),
may be merged into **a self-closing tag** (i.e. `<l/>`).

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-s(n)--------------------------------------->|
```

Since `l` is the last subsequent descendant leaf of `lc`, start-tag `<lc>`
is subsequent to start-tag `<l>` and end-tag `</l>` is presequent to end-tag
`</lc>`, which is why the scope of `lc` is **related** to the scope of `l`.
Similar to that, and since `fc` and `lc` are both child nodes of `n`, end-tag
`</fc>` is presequent to start-tag `<lc>`, which is why the scope of `fc` is
**disjoint** to the scope of `lc`.

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n------------------------------------------>|
       |-fc------->|    |-lc--------------->|
                                |-l-->|
```

As visualized above, the scopes defined by the pairs of tags of the nodes in a
document tree are, when serialized while traversing that tree, either disjoint
ex-or related (**DI-RE**). That is, there is no pair of tags such that the
defined scopes overlap each other.

As a matter of consequence, none of the edges in a document tree are defined by
its tag soup. Instead, these edges are encoded by the relationships between the
scopes the pairs of tags define. Hence, tag soup does **not define a doctree**.
Instead, a tag soup defines **a hierarchy of scopes**. One must therefore keep
in mind that a tag soup defines **a partial containment order** that is embedded
as a partial suborder into the document tree's total pre-order trace.

Note that a hand-written document must therefore be **well-formed**. That is
because, in the context of a document tree, a tag soup must always correspond
with such a partial containment order.

Note that, from a strict point of view, **parsers** read a hierarchy of scopes
from a tag soup. However, and due to the order of nodes (i.e. the CE of each
scope appears first), parsers do not have to explicitly instanciate a hierarchy
of scopes. That is because the edges of a document tree, which in a tag soup
lead from one start-tag to another, can be **decoded on the fly**.
