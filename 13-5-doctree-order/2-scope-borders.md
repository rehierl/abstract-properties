
<!-- ======================================================================= -->
# scope borders

Since a document order corresponds with the doctree's pre-order trace, the
tag-based syntax developed for the pre-order tree traveral can be used to
visualize the structure of a document.

```
    |-scope(n)----------------------------------|
.., | <n attrib*>, | fc, .., lc, .., l, | </n>, | ..
    |--------------|--------------------|-------|
```

Since a node's start-tag holds the definition of a node in terms of attributes,
it corresponds with the pre-order visit of that node. In contrary to that, a
node's end-tag does not correspond with the visit of any node. Because of that,
an end-tag must be understood to only mark the end of the node's scope. Based
on that, the node's pair of tags can be understood to enclose all of the nodes
within its scope, including the node itself.

Since the **start-tag** of a node can be understood to define the corresponding
node, it must be understood to be located just behind the border and therefore
inside of the node's scope. That is, the node's scope must be understood to
begin with the start-tag of that node.

Since the last subsequent leaf `l` of the node's last child is the last node
next presequent to the node's **end-tag**, one can state that the node's scope
ends with `l`. Consequently, and since an end-tag does not correspond with any
node, the node's end-tag must be understood to be treated as being located just
behind the scope's border.

Note that, once an implementation reaches the end-tag of a node, the scope of
that node must be understood to no longer be open for associations. Because
of that, an implementation can only change its state such that the state is
consistent with that fact - i.e. the implementation's state must reflect that
fact.

Note that, if a node is subsequent to the end-tag of another node, then that
subsequent node can not belong to the end-tag's scope since that scope has
ended just before that end-tag was reached.
