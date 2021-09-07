
<!-- ======================================================================= -->
# tag-based borders

Since a node's start-tag holds the definition of a node (in terms of a name
and a set of attributes), it is a node's start-tag that corresponds with the
pre-order visit of that node. In contrary to that, a node's end-tag does not
correspond with the visit of any node. The end-tag of a node must therefore
be understood to only mark the end of the node's scope. Based on that, the
node's pair of tags can be understood to enclose all of the nodes within its
scope, including the node itself.

```
    |-border-|-scope(n)----------------|-border-|
.., | empty  | <n>, fc, .., lc, .., l, |  </n>, | ..
    |-border-|<-open------------close->|-border-|
```

Since the **start-tag** of a node can be understood to define the corresponding
node and therefore its absolute position, it must be understood to be located
just behind the border and as such to be located inside of the node's scope.
Based on that, the scope of a node can be understood to begin with the node's
start-tag.

Since the last subsequent leaf `l` of the node's last child is the last node
next presequent to the node's **end-tag**, one can state that the node's scope
ends with `l`. Consequently, and since an end-tag does not correspond with any
node, the node's end-tag must be treated as being located on top of the border
of the node's scope.

Note that the difficulty with locating the end-tag of a scope is similar to
locating **the empty set** in regards to a non-empty set: (1) Since the empty
set is a subset to every non-empty set, the empty set can be understood to
be located inside of a non-empty set. (2) Since the empty set is disjoint to
any non-empty set, the empty set can be understood to be located outside of
a non-empty set.

```
.., <n>, fc, .., lc, .., l, </n>, ..
   |-scope(n)-------------------|
```

As a matter of simplification and consistency (a start-tag is inside a scope)
the end-tag of a node will be visualized **by convention** as the last element
within a scope. However, one must always keep in mind that an end-tag does not
correspond with any node.
