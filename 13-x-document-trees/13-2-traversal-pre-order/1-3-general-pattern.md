
<!-- ======================================================================= -->
# the (default) pre-order pattern

* the pre-order rule := `(n × c × s)`

Since the child order of `n` will be appended to `n`, the pre-order trace will
be expanded to the right-hand side of node `n`. Because of that, a pre-order
trace begins with the tree's root `r`, continues with the root's first child
`fc` and ends in leaf `l`, which is the last subsequent descendant leaf of the
root's last child.

* `trace(T) := (r, fc, .., l)`

Note that the first child `fc` of a parent `p` will always become and remain
its next subsequent sibling. That is, any parent always has its former first
child as its next subsequent sibling in the resulting pre-order trace.

* `trace(T) := (.., p, fc, ..)`

<!-- ======================================================================= -->
## node levels

The node level of a next subsequent node in the pre-order trace may be equal
to the level of its predecessor (x=n, a sibling), one greater (n+1, a first
child), or less than that (n-x, a sibling to an ancestor).

Recall that descriptions such as "node level" and "first child" always are by
default in regards to the node order of the unordered document tree. Because
of that, clarifications such as "former node level" may be omitted.

<!-- ======================================================================= -->
## a recursive, upwards-oriented point of view

```
trace(T) := (.., n, fc, .., .., lc, .., ..)
                 |-scope-n------------|
                    |-fc--| ... |-lc--|
```

Note that the following assumes that each node defines an abstract property
whose scope `s(n) := [n,*]` is in regards to the node order of the unordered
doctree. Based on that one can speak of **the scope of a node s(n)**.

The scope `s(n)` is restricted to its defining node `n` and all of its
descendants. As such, the scope of a node is **a substring** to the pre-order
trace that begins in `n`, continues with scope `s(fc)`, and has scope `s(lc)`
as a suffix.

Note that, since the scope of a node is a substring in the tree's pre-order
trace, it can be described as **the (pre-order) trace of that node t(n)**.
More accurately, the description may be used to refer to the substring of
a doctree's pre-order trace that is induced by the scope of a given node.

The pre-order rule can therefore be understood to form the trace of a scope
**recursively** in an upwards-oriented fashion. That is because the trace of
each node begins with the corresponding node and contains the traces of its
(former) child nodes in sequence one after another.

* `t(n), trace(n) := n × trace(fc) × ... × trace(lc)`

Note that the trace of each node is a substring to the traces of its ancestors.
Because of that, the trace of a tree `T` is the trace of its root `r`.

* `trace(T) := trace(r)`

Note that the traces of siblings can be formed **concurrently** before joining
them into the traces of their ancestors. That is because these traces are
disjoint ordered sequences.

<!-- ======================================================================= -->
## interleaved child orders

```
trace(T) := (.., n, fc, .., lc, .., ..)
                 |-s(n)-----------|
```

The first child `fc` of a node `n` will appear as the next sibling in a node's
pre-order trace `trace(n)`. That is because each node in a trace is presequent
to its descendants.

Further applications of the pre-order rule will then insert the child nodes
of a node's last child `lc` in between `lc` and its former next sibling `ns`.
That is, `ns` will in general not be the next sibling to `lc` since there is
a possibly infinite number of nodes in between.

The last child of a tree's root is therefore in general not the last node in
the pre-order trace of a tree. That is because the last node of such a trace
is the last subsequent leaf and as such in general a descendant to the root's
last child.

However, the pre-order rule guarantees that all of the descendants of node `n`
will be located in between `n` and `ns`. In other words, no node that is not
a descendant of `n`, will appear in between `n` and `ns`, or the next sibling
of an ancestor of `n` - whichever next sibling is available.

Based on the above, the pre-order trace of a tree can therefore be described
as **a sequence of interleaved child orders**. That is, the child order of a
node is interleaved by the child orders of its descendants.

Note that the child orders of a doctree are still sub-sequences to the tree's
pre-order trace. However, a child order is, unlike the pre-order trace of a
descendant, in general no substring to the trace of an ancestor. That is
because the pre-order rule will in general inject any number of nodes in
between any two adjacent siblings. In other words: In between any two former
siblings in the pre-order trace of a tree there may be any number of nodes
that are descendant to the next presequent sibling.
