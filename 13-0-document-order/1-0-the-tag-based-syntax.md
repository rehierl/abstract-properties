
<!-- ======================================================================= -->
# the tag-based syntax, a theoretical point of view

```
reduced pattern       in short
=================     ========
n -|-> (ns .. ls)     n -|-> s
   |-> (fc .. lc)        |-> c
```

Since the scope of a node `s(n)` is a substring to a tree's pre-order trace, it
represents a unit of consecutive nodes which always begins in the specified node.
With that in mind, one can inject **tag-based markers** in order to denote the
beginning and the end of a node's inner subset `iss(n) := {fc,..,lc,..}` by
prefixing the node's child order `co(n)` with a start-tag `<tag>` and by
suffixing it with an end-tag `</tag>`.

```
             n
             |
----------------------------
 |      |        |     |
<tag>   fc  ...  lc   </tag>
```

These tag-based markers can be thought of as being injected as additional child
nodes into the unordered document tree (DTU). The start-tag as the node's new
first child, and the end-tag as the node's new last child, both of which can
be described as specialized leaf nodes.

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

In the ordered document tree (DTO), the start-tag is a child to the node and
appears as a node that has one child only, the node's former first child. In
contrary to that, end-tag appears as a leaf node next subsequent to the node's
former last child.

```
n × (<tag> fc .. lc .. </tag>) × (ns .. ls ..)
```

In the document tree's pre-order trace (PRE), the node's child order is
enclosed in between the injected start-tag and the injected end-tag.

Note that, since the end-tag of a node is injected into DTU as the last child
of that node, each descendant of the former last child `lc` will appear in
between that former last child and the node's end-tag. Furthermore, and since
the end-tag of a node is injected as a specialized leaf, no descendant of a
node will be subsequent to the node's end-tag. That is, all the descendants
of a node will remain in between the start-tag and the end-tag of a node.

```
trace(n) := (n, <tag>, fc, .., lc, .., </tag>)
```

If the pairs of tags are injected for each node in a document tree, then its
pre-order trace will be a mixed sequence of nodes and tags.

```
trace(n) := (n, <n>, fc, .., lc, .., </n>)
             |-->|-------------------->|
```

Since the start-tag of a node always appears next subsequent to a node, both
tags of a node can be extended such that they hold **the node's name**.

```
tags(n) := (<n attribute*>, fc, .., lc, .., </n>)
```

Next, the definition of a **start-tag** can be extended such that it may hold
**attributes** which define all of the node's remaining characteristics. Each
node can therefore be said to be **pushed into its start-tag**.

Derived as described above, the resulting sequence is **a pure sequence of**
pairs of tags, which is why one does not need separate definitions for the
nodes themselves. This pure sequence of tags will be informally described as
**the tag soup of a document tree**.

Since a tag soup now completely defines a document tree that can be recreated
from it in a single pass as a structure of interconnected node objects, the
definition of **end-tags** does not have to be changed any further. That is,
end-tags remain to have **no attributes** other than the node's name. After
all, a parser could otherwise not finalize the definition of a node object
before the node's end-tag has been reached.

Note that, since a node can be understood to be pushed into its start-tag, it
is the **start-tags** that define the nodes in a doucment tree. Based on its
position within a sequence of tags, a start-tag can be said to denote the
**position** of the corresponding node in the document tree's pre-order trace.

Note that, since **end-tags** have no attributes (other than the name of a node),
end-tags **do not correspond with any node**. Consequently, end-tags are mere
**end-markers** - i.e. they only mark the end of a scope.
