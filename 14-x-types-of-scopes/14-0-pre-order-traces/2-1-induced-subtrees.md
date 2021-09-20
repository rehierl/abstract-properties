
<!-- ======================================================================= -->
# induced subtrees over DTU and DTO

Note that all considerations have been thus far in regards to the node order
of the unordered doctree `TU(N,E)`. The following considerations will therefore
shift towards the node order of the ordered doctree `TO(N,E)`.

```
             p                      |-TO[n]---------------|
             |                      ||-------------TU[n]-||
 ==========================         || n =|=> (fc .. lc) ||
 | .. |       |      | .. |         ||----|--------------||
 |    | |-------------TO[n]-|       |     |=> (ns .. ls)  |
 fs  ps ||-TU[n]---| ns  ls |       |---------------------|
        ||    n    |        |
        ||    |    |        |
        || ======= |        |
        || | ... | |        |
        || fc   lc |        |
        ||---------|        |
        |-------------------|
```

If one shifts one's focus to the node order of the ordered doctree, one might
notice that the description "induced subtree", which is defined as containing
the node provided and all its descendants, is in regards to a particular base
order.

With that in mind one can then notice that the induced subtree `TU[n]` is,
although not as an actual subtree to TO, embedded into `TO[n]` as a partial
suborder. After all, the edge `(n,lc)` has been dropped while embedding the
doctree's child order.

* `TU[n]` is no subtree to `TO[n]`
* `TU[n]` is a partial suborder to `TO[n]`

The trace of a node `t(n)` is an ordered sequence of nodes over the induced
subtree `TU[n]`. Due to now having to deal with multiple base orders, one
needs to keep in mind that it must be clear in a given context what the
corresponding base order is. When in doubt, that base order must therefore
be indicated.

* `tU(n) := n × tU(fc) × .. × tU(lc)`
* `( tU(n) substring-of tU(a) )` is true for all `(a in A(n))`

As can be seen above, the current definition of a node's trace `tU(n)` does
not cover its induced subtree `TO[n]` in the ordered doctree. That is because
it does not include all the node's descendants in TO. Consequently, any node
can be understood to be associated with **two pre-order traces**, a trace
`tU(n)` in regards to TU and a trace `tO(n)` in regards to TO.

With the above in mind, the pre-order trace of a node can be described as a
subsequence (more accurately a substring) of the document tree's pre-order
trace (more accurately the trace of the document't trees root node) that is
**restricted to a node and its descendants** in the respective node order.

<!-- ======================================================================= -->
## a suffix/prefix-based point of view

Recall that each ordered sequence (including the pre-order trace of a tree)
corresponds with a path graph and as such with a specialized node tree. Because
of that, **each non-empty suffix** over an ordered sequence corresponds with
**an induced subtree**. Based on that one can describe `TU[n]`, `TO[n]` and
also `TO[ns]` as suffixes to the corresponding node orders.

Conversely, the **prefix** of an ordered sequence can be described as what
remains when a suffix is removed from a sequence. Based on that, and with
a less strict perspective in mind, one can describe `TU[n]` as a prefix of
`TO[n]` since `TU[n]` can be formed by removing `TO[ns]` from `TO[n]`.

* `( TO[n] \ TO[ns] ) => TU[n]`
* `( TU[n] prefix-of TO[n] )` can be understood to be true

Note that, since `TU[n]` is obviously strictly speaking no subtree to `TO`,
one needs to focus on the resulting subset of nodes that, if need be, can
be used to form an induced suborder/subgraph over the appropriate node order.
