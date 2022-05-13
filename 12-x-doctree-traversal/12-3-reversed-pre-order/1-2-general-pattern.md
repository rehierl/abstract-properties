
<!-- ======================================================================= -->
# the reversed pre-order pattern

* the reversed pre-order rule := `(n × cR × sR)`

Since the reversed child order of `n` will be appended to `n`, the reversed
pre-order trace will be expanded right of node `n`. Because of that, a reversed
pre-order trace begins with the tree's root `r`, continues with the root's last
child `lc` and ends in leaf `l`, which is the last subsequent descendant leaf
of the root's first child.

* `trace(T) := (r, lc, .., l)`

Note that the last child `lc` of a parent `p` will always become and remain
its next subsequent sibling. That is, any parent always has its former last
child as its next subsequent sibling in the resulting reversed pre-order trace.

* `trace(T) := (.., p, lc, ..)`

<!-- ======================================================================= -->
## node levels

The pattern of the node levels, in the reversed pre-order trace is the same
(i.e. x=n, n+1, n-x) as that of the default pre-order trace. That is, the
reversed child order has no effect on that pattern.

Note that the order of the actual level values are obviously not the same.
That is because, (e.g.) the child of a parent may be a leaf whereas its next
subsequent sibling (i.e. its former next presequent sibling) may not be a leaf.

<!-- ======================================================================= -->
## a recursive, upwards-oriented point of view

```
trace(T) := (.., n, lc, .., .., fc, .., ..)
                 |-scope-n------------|
                    |-lc--| ... |-fc--|
```

Note that recursive characteristic remains the same. That is, the scope of a
node is still a substring to the reversed pre-order trace of its ancestors.

* `t(n), trace(n) := n × trace(lc) × ... × trace(fc)`
* `trace(T) := trace(r)`

<!-- ======================================================================= -->
## interleaved child orders

```
trace(T) := (.., n, lc, .., fc, .., ..)
                 |-s(n)-----------|
```

Note that even a reversed pre-order trace can be described a sequence of
interleaved child orders.

<!-- ======================================================================= -->
## a tag-based syntax

```
tags(n) := (<n attrib*>, lc, .., fc, .., </n>)
```

Note that, except for the reversed inner child order, the tag-based syntax
of the reversed pre-order trace corresponds with the syntax of the pre-order
trace. That is, a node can still be understood to be pushed into its start-tag.
