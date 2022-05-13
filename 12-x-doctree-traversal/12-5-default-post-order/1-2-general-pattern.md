
<!-- ======================================================================= -->
# the general post-order pattern

* the (default) post-order rule := `(c × n × s)`

Since the child order of `n` will be prepended to `n`, the post-order trace
will be expanded left of `n`. Because of that, a post-order trace begins with
a leaf `l` (a descendant of the root's first child) and ends with the tree's
root `r`, which is preceeded by its last child `lc`.

* `trace(T) := (l, .., lc, r)`

Note that, if it exists, the last child `lc` of a parent `p` will always
become and remain its next presequent sibling. That is, any parent always
has its former last child as its next presequent sibling in the resulting
post-order trace.

* `trace(T) := (.., lc, p, ..)`

<!-- ======================================================================= -->
## node levels

Note that the node levels of a post-order trace are reverse to that of a
pre-order trace. That is, the node level of a next presequent node may be
equal to the level of its successor (a sibling), one greater (a last child),
or less than that (a sibling to an ancestor).

<!-- ======================================================================= -->
## a recursive, upwards-oriented point of view

```
trace(T) := (.., .., fc, .., .., lc, n, ..)
                 |-scope-n------------|
                 |-fc--| ... |-lc--|
```

Note that the recursive characteristic remains the same as with the pre-order
traversal. That is, the scope of a node is still a sbustring to the document
tree's (default) post-order trace.

* `t(n), trace(n) := trace(fc) × ... × trace(lc) × n`
* `trace(T) := trace(r)`

<!-- ======================================================================= -->
## interleaved child orders

```
trace(T) := (.., .., fc, .., lc, n, ..)
                 |-s(n)-----------|
```

Note that even a post-order trace is a sequence of interleaved child orders.

<!-- ======================================================================= -->
## a tag-based syntax

```
tags(n) := (<n>, .., fc, .., lc, </n attrib*>)
```

Note that, since a node is next subsequent to its last child, the visit of
a node corresponds with its end-tag, instead of its start-tag. Because of
that, the attributes of a node must be added to its end-tag.

* the end-tags define the nodes
