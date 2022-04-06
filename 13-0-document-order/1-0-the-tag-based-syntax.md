
<!-- ======================================================================= -->
# the tag-based syntax, a theoretical point of view

```
reduced pattern       in short
=================     ========
n -|-> (ns .. ls)     n -|-> s
   |-> (fc .. lc)        |-> c
```

Since the scope of a node `s(n)` is a substring to the pre-order trace of a
document tree, it represents a unit of consecutive nodes that always begins
in its defining node. With that in mind, one can inject **tag-based markers**
in order to denote the beginning and the end of the inner subset of the
corresponding node `iss(n) := {fc,..,lc,..}` by prefixing the node's child
order `co(n)` with a start-tag `<tag>`, and by suffixing it with an end-tag
`</tag>`.

```
           n
           |
------------------------
 |     |      |     |
<tag>  fc ... lc  </tag>
```

These tag-based markers can be thought of as being injected as additional
child nodes into the unordered document tree (DTU). The start-tag as the
node's new first child, and the end-tag as the node's new last child, both
of which can be described as specialized leaf nodes.

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

In the ordered document tree (DTO), the start-tag is a child to the defining
node and appears as a node that has one child only, the node's former first
child. In contrary to that, an end-tag appears as a leaf node next subsequent
to the node's former last child.

```
n × (<tag> fc .. lc .. </tag>) × (ns .. ls ..)
```

In the document tree's pre-order trace (PRE), the node's child order appears
enclosed in between the injected start-tag and the injected end-tag.

Note that, since the end-tag of a node is injected into DTU as the last child
of that node, each descendant of the former last child `lc` will appear in
between that former last child and the node's end-tag. Furthermore, and since
the end-tag of a node is injected as a specialized leaf, no descendant of a
node will be subsequent to the node's end-tag. That is, all the descendants
of a node will appear in between the start-tag and the end-tag of that node.

```
trace(n) := (n, <tag>, fc, .., lc, .., </tag>)
```

If the pairs of tags are injected for each node in a document tree,
then its pre-order trace will be a mixed sequence of nodes and tags.

```
trace(n) := (n, <n>, fc, .., lc, .., </n>)
             |-->|-------------------->|
```

Since the start-tag of a node always appears next subsequent to a node,
the definition of both tags node can be extended such that both denote
**the name** of the corresponding node as a tag attribute.

```
tags(n) := (<n attribute*>, fc, .., lc, .., </n>)
```

Next, the definition of a **start-tag** can be extended such that it may hold
further **attributes** which define all of the node's remaining characteristics.
Based on that, each node can be said to be **pushed into its start-tag**.

Derived as described above, the resulting sequence is **a pure sequence of**
**pairs of tags**, which is why one does not need separate definitions for
the nodes themselves. As such, this pure sequence of tags will be informally
described as **the tag soup of a document tree**.

Since a tag soup can now be understood to define all of the characteristics
of a document tree that can be recreated from its tag soup in a single pass
as a structure of interconnected node objects, the definition of **end-tags**
does not have to be changed any further. That is, end-tags remain to have
**no attributes** other than the node's name. After all, a parser could
otherwise not finalize the definition of a node object before its end-tag
has been reached.

Note that a tag soup, seen as a pure sequence of tags, can be understood
to associate a unique index with each and every tag in it. Based on that,
and since all start-tags can be understood to define all of the nodes in
a document tree, each node can be understood to have a **unique position**
associated with it - a position that reflects its index in the document
tree's pre-order trace.

Note that, since **end-tags** have no attributes associated with them, apart
from the node's name, end-tags **do not correspond with any node** in the
document tree. Hence, end-tags are mere **end-markers** that only mark the
end of a scope.
