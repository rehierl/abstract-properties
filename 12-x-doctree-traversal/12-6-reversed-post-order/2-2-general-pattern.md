
<!-- ======================================================================= -->
# the general reversed post-order pattern

* the reversed post-order rule := `(cR × n × sR)`

Since the reversed child order of `n` will be prepended to `n`, the reversed
post-order trace will be expanded left of `n`. Because of that, a reversed
post-order trace begins with a leaf `l` (a descendant of the root's last child)
and ends with the tree's root `r`, which is preceeded by its first child `fc`.

* `trace(T) := (l, .., fc, r)`

Note that, if it exists, the first child `fc` of a parent `p` will always
become and remain its next presequent sibling. That is, any parent always
has its former first child as its next presequent sibling in the resulting
reversed post-order trace.

* `trace(T) := (.., fc, p, ..)`

<!-- ======================================================================= -->
## node levels

Note that the overall pattern of the node levels in the reversed post-order
trace is the same as that of the default post-order trace. That is because
the reversed child order has no effect on that pattern.

<!-- ======================================================================= -->
## a recursive, upwards-oriented point of view

```
trace(T) := (.., .., lc, .., .., fc, n, ..)
                 |-scope-n------------|
                 |-lc--| ... |-fc--|
```

Note that the recursive characteristic remains.

* `t(n), trace(n) := trace(lc) × ... × trace(fc) × n`
* `trace(T) := trace(r)`

<!-- ======================================================================= -->
## interleaved child orders

```
trace(T) := (.., .., lc, .., fc, n, ..)
                 |-s(n)-----------|
```

Note that even a reversed post-order trace can be described as a sequence of
interleaved child orders.

<!-- ======================================================================= -->
## a tag-based syntax

```
tags(n) := (<n>, .., lc, .., fc, </n attrib*>)
```

Note that, except for the reversed inner child order, the tag-based syntax
of the reversed post-order corresponds with the syntax of the post-order
trace. That is, the attributes of a node must be added to its end-tag.

* the end-tags define the nodes
