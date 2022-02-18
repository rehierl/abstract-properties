
<!-- ======================================================================= -->
# tag-based borders

Since a node's start-tag holds the definition of a node (in terms of a name
and a set of attributes), it is a node's start-tag that corresponds with the
pre-order visit of that node. In contrary to that, a node's end-tag does not
correspond with the visit of any node. The end-tag of a node must therefore
be understood to only mark the end of a scope. Because of that, the pair of
tags associated with a node can be understood to enclose all of the nodes
within its scope, including the node itself.

```
    |-scope(n)----------------|-border-|
.., | <n>, fc, .., lc, .., l, | </n>,  | ..
    |->-open->------>-closed->|-empty--|
```

Since the **start-tag** of a node can be understood to define the corresponding
node and also its absolute position in the document order, it must be understood
to be located just behind the border and as such to be located inside of the
node's scope. Based on that, the scope of a node can be said to begin with the
node's start-tag.

Since the last subsequent leaf `l` of the node's last child is the last node
next presequent to the node's **end-tag**, one can state that the node's scope
ends with leaf `l`. Consequently, and since an end-tag does not correspond with
any node, the node's end-tag must be treated as being located on top of the
border of the node's scope.

Note that the difficulty with pinpointing the position of an end-tag is similar
to locating **the empty set** in regards to another set: (1) Since the empty
set is a subset to any other set, the empty set can be said to be located inside
of another set. (2) Since the empty set is disjoint to any set, the empty set
can also be said to be located outside of the same set.

```
.., <n>, fc, .., lc, .., l, </n>, ..
    |-scope(n)------------------|
```

As a matter of simplification, and since a start-tag is located inside of a
node's scope, the end-tag of a node will be visualized as the last element
within a scope. However, one must keep in mind that an end-tag does not
correspond with any node.
