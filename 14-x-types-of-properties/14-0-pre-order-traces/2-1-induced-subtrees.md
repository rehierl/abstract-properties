
<!-- ======================================================================= -->
# induced subtrees over DTU and DTO

Note that the following will shift the focus from the unordered document tree
`TU(N,E)` towards the ordered doctree `TO(N,E)`.

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

If one's focus shifts towards to the node order of the ordered doctree,
one will eventually notice the definition of an **induced subtree** `T[n]`,
which includes a node and all of its descendants in regards to some current
**known tree**. Based on that, each node can be understood to be associated
with more than one such tree - i.e. an induced subtree in the unordered
doctree `TU[n]` and an induced subtree in the ordered doctree `TO[n]`.

With that in mind, one might also notice that the induced subtree `TU[n]` is,
although not as an actual subtree of DTO, embedded into `TO[n]` as a partial
suborder. After all, the edge `(n,lc)` has been dropped while embedding the
document tree's child order.

* `TU[n]` is no subtree to `TO[n]`
* `TU[n]` is a partial suborder to `TO[n]`

The trace of a node `t(n)` is an ordered sequence of nodes over its induced
subtree `TU[n]`. Due to now having to deal with multiple node trees, one will
have to indicate the corresponding tree order.

* `tU(n) := n × tU(fc) × .. × tU(lc)`

Since a node can be understood to be associated with more than one induced
subtree, a node can also be understood to be associated with more than one
pre-order trace, a trace `tU(n)` over DTU, and a trace `tO(n)` over DTO.

With the above in mind, the pre-order trace of a node can in general be
described as a subsequence, or more accurately as substring of the document
tree's pre-order trace, which covers a node and its descendants in the
corresponding node order.
