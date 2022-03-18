
<!-- ======================================================================= -->
# tag-based borders

Since a node's start-tag holds the definition of a node (in terms of a name
and a set of attributes), it is the node's start-tag that corresponds with
the pre-order visit of that node. In contrary to that, a node's end-tag
does not correspond with the visit of any node. The end-tag of a node must
therefore be understood to only mark the end of a scope. The pair of tags
of a node combined can be understood to enclose all of the nodes within its
scope, including the node itself.

```
    |-scope(n)----------------|-border-|
.., | <n>, fc, .., lc, .., l, | </n>,  | ..
    |-open->---------->-close-|-empty--|
```

Since the **start-tag** of a node can be understood to define the corresponding
node and also its absolute position within the document order, a start-tag must
be understood to be located just behind the border and as such to be located
inside of the node's scope. Based on that, the scope of a node can be said to
begin with the start-tag of a node.

Since the last subsequent descendant leaf `l` of a node's last child is the
last node next presequent to a node's **end-tag**, one can state that the scope
of a node ends with that leaf node. Consequently, and since an end-tag does not
correspond with any node, the end-tag of a node must be treated as being located
on top of the border of a node's scope.

Note that the difficulty with pinpointing the position of an end-tag is similar
to locating **the empty set** within another set: (1) Since the empty set is a
subset to any other set, the empty set can be said to be located inside of any
other set. (2) Since the empty set is disjoint to any set, the empty set can
however also be said to be located outside of any other set.

```
.., <n>, fc, .., lc, .., l, </n>, ..
    |-scope(n)-----------------|
```

As a matter of simplification, and since a start-tag is located inside of a
node's scope, the end-tag of a node will be visualized as the last element
of the corresponding scope (i.e. inside). However, one must still keep in
mind that an end-tag does not correspond with any node.
