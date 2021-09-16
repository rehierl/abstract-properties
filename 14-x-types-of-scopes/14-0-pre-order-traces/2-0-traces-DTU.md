
<!-- ======================================================================= -->
# recap: the pre-order trace over DTU

The following content will shift the focus from a node and its descendants (i.e.
`(n × c)`) towards a node and its subsequent siblings, including all of their
descendants (i.e. `(n × c × s)`). The following must therefore be understood
as an attempt to widen one's view on pre-order traces.

```
         p           | tree-order:
         |           | top-to-bottom oriented
 -----------------   | "ancestor-of"
 | .. |  |  | .. |   |
 fs  ps  n  ns  ls   | child-order:
         |           | left-to-right oriented
      -------        | "presequent-sibling-of"
      | ... |        |
      fc   lc        |
```

Recall that, unless specified otherwise, descriptions are by default in regards
to the node order of an unordered doctree.

```
pattern:        -> n -> (fc .. lc ..) -> (ns .. ls ..)
t(n), trace(n): -> n -> (fc .. lc ..)
```

Recall that the pre-order trace `t(n)` over a tree `T(N,E)` is a substring to
the trace of a tree (i.e. the trace over its root node). Also, `t(n)` is an
ordered sequence of nodes such that its set of nodes is equal to the set of
nodes in the induced subtree `T[n]`. Because of that, one can describe `t(n)`
as the trace of an induced subtree.

* `t(n) := n × t(fc) × .. × t(lc)`
* `(t(n) substring-of t(a))` is true for any `(a in A(n))`
* the trace of a node is a substring to the traces of its ancestors

Recall that the descendants of a node `n` will be inserted in between `n` and
its next subsequent sibling `ns`. Because of that it is possible to enclose
all of the nodes within a node's scope `scope(n) := [n,*]` in a pair of tags.
The tag-based syntax can therefore be described as being bound to the node
order of an unordered doctree.

* `tags(n) := <n> tags(fc) .. tags(lc) </n>`
* `tags(T) := tags(r)` for `(r in RN(T))`
