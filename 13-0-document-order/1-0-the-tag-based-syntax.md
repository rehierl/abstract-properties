
<!-- ======================================================================= -->
# the tag-based syntax, a theoretical point of view

```
reduced pattern       in short
=================     ========
n -|-> (ns .. ls)     n -|-> s
   |-> (fc .. lc)        |-> c
```

Since the scope of a node `s(n)` is a substring to a tree's pre-order trace,
it represents a unit of consecutive nodes which always begins in the specified
node. With that in mind, one can inject **tag-based markers** in order to denote
the beginning and the end of a node's inner subset `iss(n) := {fc,..,lc,..}`
by prefixing the node's child order `co(n)` with a start-tag `<tag>` and by
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
tags of a node can be extended such that both hold **the node's name**.

```
tags(n) := (<n attribute*>, fc, .., lc, .., </n>)
```

Next, the definition of a **start-tag** can be extended such that it may hold
**attributes** which define all the remaining characteristics of that node.
Based on that, a node can be said to be **pushed into its start-tag**.

Derived as described above, the resulting sequence is **a pure sequence of**
pairs of tags, which is why one does not need separate definitions for the
nodes themselves. This pure sequence of tags will be informally referred to
as **the tag soup of a document tree**.

Note that, since this tag-based syntax is intended to provide the complete
definition of a tree, which in one single pass allows to recreate that tree
as a structure of interconnected node objects, **the end-tag** of a node is
not changed any further (i.e. **has no attributes**). That is because a parser
could then, while parsing a tag soup from its first tag to its last tag, not
finalize the definition of a node object before its end-tag is reached.

Note that the start-tag of a node corresponds with the node it defines. In
contrary to that, the end-tag of a node does **not correspond with any node**
since, except for the node's name, it does not hold any attributes that define
the node.
