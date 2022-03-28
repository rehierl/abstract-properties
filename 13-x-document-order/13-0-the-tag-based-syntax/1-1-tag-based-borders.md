
<!-- ======================================================================= -->
# tag-based borders

The pair of tags of a node combined can be understood to enclose all of the
nodes within the node's scope, including the node itself. However, and since
the attributes of the node's start-tag defines all the characteristics of
that node, it is the node's start-tag that corresponds with that node. In
contrary to that, a node's end-tag does not correspond with any node. The
end-tag of a node can therefore only be understood to mark the end of a
scope.

```
    |-scope(n)---------------------------|-border-|
.., | <n attribute*>, fc, .., lc, .., l, | </n>,  | ..
    |-open->--------------------->-close-|-empty--|
```

Since the **start-tag** of a node can be understood to define the corresponding
node and therefore also its **absolute position** in the pre-order trace of a
document tree, a start-tag must be understood to be located just behind the
border of the node's scope and as such to be located inside of the node's scope.
Based on that, the scope of a node can be said to begin with the start-tag of
a node.

Since the last subsequent descendant leaf `l` of a node's last child is the
last node next presequent to the node's **end-tag**, one can state that the
scope of a node ends with that leaf. Consequently, and since an end-tag does
not correspond with any node, the end-tag of a node must be treated as being
located on top of the border of the node's scope.

Note that the difficulty with pinpointing the location of an end-tag is similar
to locating **the empty set** within another set: (1) Since the empty set is a
subset to any other set, the empty set can be said to be located inside of every
other set. In contrary to that, and (2) since the empty set is disjoint to any
set, the empty set can also be said to be located outside of every other set.

```
.., <n>, fc, .., lc, .., l, </n>, ..
    |-scope(n)---------------->|
```

As a matter of simplification, and since a start-tag is located inside of a
node's scope, the end-tag of a node will be **visualized as the last element**
and therefore counted towards a node's scope (i.e. visualized as being inside
of that scope).

```
   |-s(n)------------------|-------|
.. |  <n>  | fc .. lc .. l | </n>  | ..
   |-ce(n)-|-iss(n)--------|-empty-|
```

As mentioned earlier, a hierarchy of scopes corresponds with a node tree. In
addition to that, each scope is the union of two disjoint subsets, an inner
subset `iss(n)`, which binds the scope of a node `s(n)` to the scopes of its
descendants, and a characteristic subset `css(n)`, which allows to identify
the scope amongst the scopes of its ancestors.

Furthermore, a hierarchy of scopes is such that the CSS of each scope has one
and only one characteristic element `ce(n)`. With that in mind one can conclude
that **any start-tag denotes the CE of a scope**.
