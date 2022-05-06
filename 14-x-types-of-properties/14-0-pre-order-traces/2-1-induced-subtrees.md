
<!-- ======================================================================= -->
# induced subtrees over DTU and DTO

Note that the following will shift the focus from the unordered document
tree `TU(N,EU)` towards the ordered document tree `TO(N,EO)`.

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

If one's focus shifts towards to the node order of an ordered doctree,
one will eventually recall the definition of an **induced subtree** `T[n]`,
which includes a node and all of its descendants in regards to some current
**known tree order**. Based on that, each node can be understood to be
associated with more than one such tree - i.e. an induced subtree in the
unordered doctree `TU[n]`, and an induced subtree in the ordered doctree
`TO[n]`.

With that in mind, one might also notice that the induced subtree `TU[n]`
is, although not as an actual subtree of DTO, embedded into `TO[n]` as a
partial suborder. After all, the edge `(n,lc)` has been dropped while
embedding the document tree's child order.

* `TU[n]` is no subtree to `TO[n]`
* `TU[n]` is a partial suborder to `TO[n]`

<!-- ======================================================================= -->
## more than one trace per node

The trace of a node `t(n)` is an ordered sequence of nodes over its induced
subtree `TU[n]`. Due to now having to deal with multiple node trees, one
needs to indicate the corresponding tree order, if that order isn't obvious
in a given context.

* `tU(n) := n × tU(fc) × .. × tU(lc)`

Since a node can be understood to be associated with more than one induced
subtree, a node can also be understood to be associated with more than one
pre-order trace, a trace `tU(n)` over DTU, and a trace `tO(n)` over DTO.

Note that the document tree's root `r` has only one trace associated with it.
After all, a root has no subsequent siblings, which is why the root's trace
`tO(r)` has no additional descendants it could append to `tU(r)`. Because of
that, both of these traces are equal.

* `( tU(r) == tO(r) )` is true
