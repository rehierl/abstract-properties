
<!-- ======================================================================= -->
## a tag-based syntax

```
n -|-> (ns .. ls)
   |-> (fc .. lc)
```

Since the scope of a node `s(n)` is a substring to a tree's pre-order trace,
it represents an enclosed unit of consecutive nodes that always begins in the
specified node. One can therefore inject tag-based markers in order to denote
the beginning and the end of the scope's inner subset `iss(n) := (fc,..,lc)`
by prefixing the node's sequence of former child nodes with a start-tag `<tag>`
and by suffixing it with an end-tag `</tag>`.

```
n -|-> (ns .. ls)
   |-> (<tag> fc .. lc </tag>)
```

If the pre-order rule is then applied to node `n`, its "current" sequence of
subsequent siblings will be prefixed by its modified sequence of child nodes.

```
n × (<tag> fc .. lc .. </tag>) × (ns .. ls ..)
```

Note that, at this point, each tag represents nothing more but the beginning
and the end of a scope. Because of that, applying the pre-order rule to a tag
will not have any effect since tags act as specialized leaf nodes (i.e. no
child nodes of their own).

<!-- ======================================================================= -->

```
tags(n) := (n, <tag>, fc, .., lc, .., </tag>)
```

Since the pre-order rule will also be applied to every other node in the tree's
trace, the tree's trace will be transformed into a bloated sequence of nodes
and tags.

Since the start-tag of a node always appears next subsequent to a node in the
tree's preorder trace, one can extend the definition of a start- and an end-tag
such that they both denote the name of the corresponding node.

In addition to that, the node's start-tag can be extended such that it may hold
attributes which can be understood to define all other characteristics of that
node. Based on that, a node can be described to be **pushed into its start-tag**.

```
tags(n) := (<n attrib*>, fc, .., lc, .., </n>)
```

Note that, since the tag-based syntax is intended to provide the definition
of a tree which allows to recreate a tree in one single pass, the end-tag of
a node is not extended any further. That is because a parser could then not
finalize the definition of a node before its end-tag has been reached.

Extended as above, the resulting sequence will then consist of pairs of tags
only. Consequently, one will no longer need separate definitions for the nodes
themselves since these are embedded into the corresponding start-tags. That is,
the tree's pre-order trace is thus completely defined in terms of a tag-based
syntax - with the additional feature that there is an end-marker for the scope
of each node.

Note that the **start-tag** of a node corresponds with **the visit of a node**.
That is, the subsequence of all start-tags (i.e. drop everything except for the
start-tags) corresponds with the tree's pre-order trace.

Note that, since a node is pushed into its start-tag, an **end-tag** does not
correspond with the visit of a node. An end-tag remains to be nothing more but
an **end-marker** for the scope of a node.
