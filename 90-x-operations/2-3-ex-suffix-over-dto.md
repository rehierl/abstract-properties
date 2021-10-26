
<!-- ======================================================================= -->
# suffix over DTO

The following will examine the effects of the removal of a suffix over the
ordered doctree DTO in regards to the trival order DTR, the unordered doctree
DTU, and the doctree's pre-order trace DPR.

<!-- ======================================================================= -->
## suffix over DTO in DTR

As before, the trivial order DTR is such that it contains all the nodes, but
none of the edges. The effects of this suffix-based removal thus corresponds
with the removal of a simple subset of nodes from the order's set of nodes.

<!-- ======================================================================= -->
## suffix over DTO in DPR

```
before the removal                                   after the removal
=============================================   =>   =================
.. ps .. x n fc .. lc .. /n ns .. ls .. /p ..        .. ps .. x /p ..
           |-s1-----------|
           |-s2--------------------------|
```

Note that `x` can be understood to denote the last subsequent descendant leaf
of `ps`, which (if it exists) is next presequent to `n` in the doctree's
pre-order trace.

As before, the pair of tags of parent `p` encloses `p` and all its descendants
over DTU, including all the descendants of `n` over DTU. Furthermore, all the
nodes subsequent to `n` in the doctree's pre-order trace up until the end-tag
of `p` are descendants of `n` over DTO. The above suffix based removal therefore
also corresponds with the removal of an infix from the doctree's pre-order trace.

<!-- ======================================================================= -->
## suffix over DTO in DTU

```
before the removal        after the removal   |
==================   =>   =================   |
         p                   p                |
         |                   |                |
 -----------------        -------             |
 | .. |  |  | .. |        | ... |             |
 fs  ps  n  ns  ls        fs   ps             | <- c(p)
         |                                    |
     ---------                                |
     fc ... lc                                | <- c(n)
```

Recall that the suffix `[n,*]` over DTO is a substring to the doctree's
pre-order trace. Furthermore, that substring can be said to be formed by
concatenating the pre-order traces of `n` and all of its subsequent siblings.

* `tO(n) := tU(n) × tU(ns) × .. × tU(ls)`

<!-- ======================================================================= -->
## suffix over DTO in DTO

```
before the removal                      after the removal
================================   =>   =================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps
                    |-> fc .. lc
```

The suffix over DTO contains all the child nodes of `n` (in DTU and DTO). Node
`n` and its child order will therefore be removed as well as all of the child
orders of each parent node that is a descendant of `n` in DTO. In regards to
the child order of parent `p`, the above suffix-based removal appears as the
removal of the suffix `[n,*]` over `c(p)`.

* `c1 := c(p) := (fs,..,ps,n,ns,..,ls)`
* `c1` changes into `c2 := (fs,..,ps)`
