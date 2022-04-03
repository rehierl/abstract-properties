
<!-- ======================================================================= -->
# tag-based borders

The pair of tags of a node can be understood to enclose all of the nodes within
the node's scope, including the node itself.

```
    |-scope(n)---------------------------|-empty--|
.., | <n attribute*>, fc, .., lc, .., l, | </n>,  | ..
    |-open->--------------------->-close-|-border-|
```

Since the **start-tag** of a node can be understood to define the corresponding
node and therefore also its **position** in the pre-order trace of a document
tree, a start-tag must be understood to be located just behind the border of
the node's scope and as such to be located inside that scope. Because of that,
the scope of a node can be said to begin with its start-tag.

Note that, since each start-tag can be understood to correspond with a node
in the document tree that has a unique position associated with it, a document
tree can be described as **an ordered tree** in the sense of "a set of distinct
elements" that is associated with a tree order.

Since the last subsequent descendant leaf `l` of a node's last child is the
last node next presequent to the node's **end-tag**, one can state that the
scope of a node ends with its last subsequent leaf. Consequently, and since
an end-tag does not correspond with any node, the end-tag of a node must be
treated as being located on top of the border of the node's scope.

Note that the difficulty with pinpointing "the location of an end-tag" is
similar to locating **the empty set** within another set: (1) Since the empty
set is a subset to any other set, the empty set can be said to be located
inside of every other set. In contrary to that, and (2) since the empty set
is disjoint to any set, the empty set can also be said to be located outside
of every other set.

```
.., <n>, fc, .., lc, .., l, </n>, ..
    |-scope(n)---------------->|
```

As a matter of simplification, and since a start-tag is located inside of a
node's scope, the end-tag of a node will be **visualized as the last element**
in a scope and therefore counted towards the corresponding scope.
