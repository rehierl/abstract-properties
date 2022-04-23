
<!-- ======================================================================= -->
# suffix over DTU

The following will examine the effects of the removal of a suffix over the
unorderd doctree DTU in regards to the trivial order DTR, the ordered doctree
DTO, and the doctree's pre-order trace DPR.

<!-- ======================================================================= -->
## suffix over DTU in DTR

Since the trivial order DTR is such that it contains all the nodes, but none
of the edges, the effects of this suffix-based removal corresponds with the
removal of a simple subset of nodes from the order relation's set of nodes.

<!-- ======================================================================= -->
## suffix over DTU in DPR

```
before the removal                     after the removal
===============================   =>   ==========================
.. ps .. n fc .. lc .. /n ns ..        .. ps .. fc .. lc .. ns ..
         |-s1-----------|
```

The effects of this suffix-based removal in regards to a general tree have been
examined in "remove a suffix from a tree". This case covers the effects of the
removal in regards to the doctree's pre-order trace.

As explained before, a pair of tags encloses a node and the node's descendants
in DTU (i.e. the nodes in its type-1 scope). Furthermore, all of these nodes
appear as consecutive nodes in the doctree's pre-order trace (i.e. a substring).
Because of that, the above suffix-based removal corresponds with the removal
of an infix from the doctree's pre-order trace.

<!-- ======================================================================= -->
## suffix over DTU in DTO

```
before the removal                      after the removal
================================   =>   =========================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps -> ns .. ls
                    |-> fc .. lc
```

The suffix over DTU contains all the child nodes of node `n`. Because of that,
node `n` and its child order will be removed as well as all all the descendants
and their child orders. In regards to the child order of parent `p`, the above
suffix based removal appears as a simple element based removal of node `n`.

* `c1 := c(p) := (fs,..,ps,n,ns,..,ls)`
* `c1` changes into `c2 := (fs,..,ps,ns,..,ls)`

Note that the node's former next subsequent sibling `ns` will become the next
subsequent sibling of the node's former next presequent sibling `ps`. That is,
there will no longer be another node in between.
