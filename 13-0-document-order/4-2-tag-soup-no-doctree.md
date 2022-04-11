
<!-- ======================================================================= -->
# a tag soup ain't no node tree

As mentioned earlier, a hierarchy of scopes corresponds with a node tree. In
addition to that, each scope is the union of two disjoint subsets, an inner
subset `iss(n)` which binds the scope of a node `s(n)` to the scopes of its
descendants, and a characteristic subset `css(n)` which allows to identify a
scope amongst the scopes of its ancestors.

Furthermore, a hierarchy of scopes is such that the characteristic subset of
each scope has one and only one characteristic element `ce(n)`, an element
that is no element in any of the scopes defined by the descendants of a node.
With that in mind one can state that **a start-tag denotes the CE of a scope**.

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
       |-fc------->|    |-lc--------------->|
                                |-l-->|
```

Since `l` is the last subsequent descendant leaf of `lc`, start-tag `<lc>`
is presequent to start-tag `<l>` and end-tag `</l>` is presequent to end-tag
`</lc>`, which is why the scope of `lc` is **related** to the scope of `l`.
Similar to that, and since `fc` and `lc` are both child nodes of `n`, end-tag
`</fc>` is presequent to start-tag `<lc>`, which is why the scope of `fc` is
**disjoint** to the scope of `lc`.

As visualized above, the scopes defined by the pairs of tags of the nodes in a
document tree are, when serialized while traversing that tree, either disjoint
ex-or related (**DI-RE**). That is, there is no pair of tags such that the
defined scopes overlap each other.

Based on the above one can state that none of the edges of a document tree are
defined by its tag soup. Instead, the pairs of tags are used to define all of
the scopes in a document tree. That is, the edges of the document tree are
embedded into the relationships between its scopes. Consequently, a tag soup
does **not (directly) define a document tree**. Instead, a tag soup defines
**a hierarchy of scopes**. One must therefore keep in mind that a tag soup
corresponds with **a partial containment order** that is embedded as a partial
suborder into the document tree's pre-order trace.

<!-- ======================================================================= -->
## remarks

Note that the tag soup of a hand-written document must be **well-formed**.
That is because, in the context of a document tree, a tag soup must always
correspond with a partial containment order.

Note that, from a strict point of view, **parsers** read a hierarchy of scopes
from a tag soup. However, and due to the order of nodes (i.e. the CE of each
scope appears first), parsers do not have to explicitly instanciate a hierarchy
of scopes. That is because the edges of a document tree, which in a tag soup
always lead from one start-tag to another start-tag subsequent to it, can be
**decoded on the fly**.

Note that the tag-based syntax **does in principle support overlapping scopes**.
However, such scopes can not be used to define a document tree since the
containment order defined by such a tag soup is **no hierarchy of scopes**.
