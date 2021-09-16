
<!-- ======================================================================= -->
# induced subtrees over DTU and DTO

Note that, thus far, all considerations have been in regards to the node order
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
corresponding base order is.

* `tU(n) := n × tU(fc) × .. × tU(lc)`
* `(tU(n) substring-of tU(a))` is true for all `(a in A(n))`

As can be seen above, the current definition of a node's trace `tU(n)` does
not cover its induced subtree `TO[n]` in the ordered doctree. That is because
it does not include all the node's descendants in TO. Consequently, any node
can be understood to be associated with **two pre-order traces**, a trace
`tU(n)` in regards to TU and a trace `tO(n)` in regards to TO.

With the above in mind, the pre-order trace of a node can be described as a
subsequence (more accurately a substring) of the document tree's pre-order
trace (more accurately the trace of the document't trees root node) that is
**restricted to a node and its descendants** in the respective node order.
