
<!-- ======================================================================= -->
# the pre-order trace over DTU

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

Recall that, unless specified otherwise, descriptions are by default
in regards to an unordered document tree and its tree order.

```
t(T), trace(T), pre(T):  r .. -> n -> fc .. lc .. -> ns .. ls ..
t(n), trace(n), pre(n):       -> n -> fc .. lc ..
```

Recall that the pre-order trace `t(n)` of any node `n` is a substring to the
trace of its tree `T(N,E)` - i.e. the trace `t(r)` of the tree's root `r`.
Also, each trace `t(n)` is an ordered sequence of nodes such that its set of
nodes is equal to the set of nodes in the induced subtree `T[n]`. Because of
that, `t(n)` can also be described as the trace of that induced subtree.

* `t(n) := n × t(fc) × .. × t(lc)`
* `( t(n) substring-of t(a) )` is true for any `(a in A(n))`
* the trace of a node is a substring to the traces of its ancestors

Recall that the descendants of a node `n` will be inserted in between `n`
and its next subsequent sibling `ns`. Hence, it is possible to enclose all
of the nodes in the scope of a node`scope(n) := [n,*]` with a pair of tags.
The tag-based syntax can therefore be described as being bound to the node
order of an unordered doctree.

* `tags(n) := ( <n> tags(fc) .. tags(lc) </n> )`
