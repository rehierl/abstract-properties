
<!-- ======================================================================= -->
# the general pre-order pattern

The overall pattern of a pre-order trace is such that it begins with a tree's
root `r`, immediately followed by the root's first child `c1`, and ending in
the last subsequent leaf `l` of the ordered doctree.

* `trace(T) := (r, c1, ..., l)`

Note that, if it exists, the first child `c1` of a parent `p` will always
become and remain its next subsequent sibling. That is, any parent always
has its former first child as its next subsequent sibling in the resulting
pre-order trace.

* `trace(T) := (..., p, c1, ...)`

<!-- ======================================================================= -->
## node levels

Note that, the node level of a next subsequent node may be equal to the level
of its predecessor (a sibling), one greater (a first child), or less than that
(a sibling to an ancestor).

<!-- ======================================================================= -->
## a recursive, upwards-oriented point of view

```
trace(T) := (r, .. n, fc, .., lc, .., ns, .., ls, .., l)
                   |-scope-n--------|
                      |-fc-|...|-lc-|
```

Note that the following assumes each node to define an abstract property
whose scope `s(n) := [n,*]` is in regards to the node order of the unordered
doctree. Based on that one can speak of **the scope of a node s(n)**.

The scope `s(n)` is restricted to its defining node `n` and all of its
descendants. As such, the scope is **a substring** to the pre-order trace
that begins in `n`, continues with scope `s(fc)`, and has scope `s(lc)` as
its suffix.

The pre-order rule can therefore be understood to form the traces of each
scope **recursively** in an upwards-oriented fashion. Because of that, the
scope of each node is a substring to the scope of its ancestors.

Note that, since scope of a node is a substring in the tree's pre-order
trace, it can be described as **the (pre-order) trace of that node t(n)**.

Due to the above, the trace of each node begins with the corresponding node
and contains the traces of its (former) child nodes in sequence one after
another. Because of that, the trace of each node is a substring to the
traces of its ancestors.

* `t(n), trace(n) := n × trace(fc) × ... × trace(lc)`
* `(a ancestor-of d) -> (trace(d) substring-of trace(a))`

Note that the traces of siblings can be formed **concurrently** before
concatenating them into the traces of their ancestors. That is because
these traces are disjoint ordered sequences.

Note that the trace of a tree `T` is equal to the trace of its root `r`.

* `trace(T) := trace(r)`

<!-- ======================================================================= -->
## interleaved child orders

```
trace(T) := (r, .., n, fc, .., lc, .., ns, ..)
                    |-s(n)-----------|
```

The first child `fc` of a node `n` will appear as the next sibling in the node's
pre-order trace `trace(n)`. That is because each node in a trace is presequent
to all of its descendants.

Further applications of the pre-order rule will then insert the child nodes of
the node's last child `lc` in between `lc` and the former next sibling `ns`.
That is, `ns` will in general not be the next sibling to `lc` since there is
in general a possibly infinite number of nodes in between.

The last child of a tree's root is therefore in general not the last node in
the tree's trace. That is because the last node of such a trace is in general
a descendant to the last child of the tree's root.

However, the pre-order rule guarantees that all of the descendants of node `n`
will be located in between `n` and `ns`. In other words, no node which is not
a descendant of `n`, will appear in between `n` and `ns`, or the next sibling
of an ancestor of `n` (whichever next sibling is available).

The pre-order trace of a tree can therefore be described as a sequence of
interleaved sub-sequences, each of which is a child order in the doctree. Put
differently, the child order of a node is interleaved by the child orders of
its descendants. Based on that, a tree's pre-order trace can be described as
**a sequence of interleaved child orders**.

Note that the child orders of a doctree are still sub-sequences to the tree's
pre-order trace. However, a child order is, unlike the pre-order trace of a
descendant, in general no substring to the trace of an ancestor. That is
because the pre-order rule will in general inject any number of nodes in
between any two adjacent siblings. In other words: In between any two former
siblings in the pre-order trace of a tree there may in general be any number
of nodes that are descendant to the next presequent sibling.
