
<!-- ======================================================================= -->
## a tag-based syntax

```
n -|-> (ns .. ls)
   |-> (fc .. lc)
```

Since the scope of a node `s(n)` is a substring to a tree's pre-order trace, it
represents an enclosed unit of consecutive nodes which always begins with the
defining node. One can therefore inject tag-based markers to denote the beginning
and the end of the scope's inner subset `iss(n) := (fc,..,lc)` by prefixing the
node's sequence of former child nodes with a start-tag `<tag>` and by suffixing
it with an end-tag `</tag>`.

```
n -|-> (ns .. ls)
   |-> <tag> (fc .. lc) </tag>
```

If the pre-order rule is then applied, to node `n`, its "current" sequence of
subsequent siblings will be prefixed with its modified sequence of former child
nodes.

```
n -> <tag> (fc .. lc) </tag> -> (ns .. ls)
```

Note that, at this point, each tag represents nothing more but the beinning and
the end of a scope. Because of that, applying the pre-order rule to a tag can
not have any effect. That is because these tags must be thought of as being
inserted as specialized leaf nodes (i.e. no child nodes of their own).

```
trace(T) := (r, .. n, <tag>, fc, .., lc, .., </tag>, ns, .., ls, .., l)
                   |-scope-n-----------------------|
```

Since the pre-order rule will also be applied to every other node in the tree,
the tree's pre-order trace will appear as a bloated sequence of nodes and tags.

Note that, the descendants of a node will always be inserted in between the
node and its next subsequent sibling. Because of that, there will be no other
node inserted into the subsequences `(n, <tag>, fc)` and `(</tag>, ns)`.

Since the start-tag of a node always appears next subsequent to a node in the
tree's preorder trace, one can extend the definition of a start- and an end-tag
such that they both denote the name of a node by renaming the corresponding
tags. In addition to that, the node's start-tag can be extended such that it
may also hold attributes `attrib*` such that a start-tag represents a complete
definition of the corresponding node. Because of that, a node can be understood
to be **pushed into its start-tag**.

Note that, since the tag-based syntax is intended to provide the definition of
a tree that allows to recreate a tree in one single pass over its pre-order
trace, the end-tag of a node is not extended such that it may hold attributes
which define even further characterisitics of the corresponding node. That is
because a parser could then not finalize the definition of a node before the
node's end-tag has been reached.

```
def(T) := (r, .. <n attrib*>, fc, .., lc, .., </n>, ns, .., ls, .., l)
                 |-scope-n------------------------|
```

Extended as such, the resulting sequence will then consist of start- and
end-tags only. Consequently, one will no longer need separate definitions for
the nodes themselves since these are embedded into the corresponding start-tags.
That is, the tree's pre-order trace is thus completely expressed in terms of a
tag-based syntax with - the additional feature that there is an end-marker for
the scope of each node.

Note that a pair of tags can thus be understood to completely enclose all of
the nodes within the scope of a node, including the node itself.

Note that the subsequence of all start-tags (i.e. drop all end-tags) almost
directly corresponds with the tree's pre-order trace and, because of that,
with the **pre-order visit order** of the nodes in a document tree. That is,
the visit of a node corresponds with its start-tag - and nothing else.
