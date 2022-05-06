
<!-- ======================================================================= -->
# suffix over DPR

The following will examine the effects of the removal of a suffix over the
doctree's pre-order trace DPR in regards to the trivial order DTR, the unorderd
doctree DTU, and the ordered doctree DTO.

<!-- ======================================================================= -->
## suffix over DPR in DTR

As before, the trivial order DTR is such that it contains all the nodes, but
none of the edges. The effects of this suffix-based removal thus corresponds
with the removal of a simple subset of nodes from the order's set of nodes.

<!-- ======================================================================= -->
## suffix over DPR in DTU

```
before the removal        after the removal   |
==================   =>   =================   |
         p - ...             p                |
         |                   |                |
 -----------------        -------             |
 | .. |  |  | .. |        | ... |             |
 fs  ps  n  ns  ls        fs   ps             | <- c(p)
         |                                    |
     ---------                                |
     fc ... lc                                | <- c(n)
```

Recall that the type-2 scope of `n` (over DTO) is a subset of its type-3 scope
(over DPR). In addition to the type-2 nodes of `n`, the type-3 scope of `n`
contains all the subsequent siblings of all of its ancestors, including their
descendants (over DTU, DTO and DPR).

<!-- ======================================================================= -->
## suffix over DPR in DTO

The rooted path of node `n` over DTU can be said to split the unordered doctree
into two parts: (1) a part that contains all the nodes that have been visited
once node `n` is being visited, and (2) a part that contains all the nodes that
will be visited after `n` has been visited. Based on that, the rooted path of
a node can be described to mark "a border" over DTU.

```
before the removal
======================================================================
r -> fs .. ps -> a -|-> ns .. ls
                    |-> fs .. ps -> p -|-> ns .. ls
                                       |-> fs .. ps -> n -|-> ns .. ls
                                                          |-> fc .. lc
```

Similar to that, the rooted path of node `n` over DTO can be said to split the
ordered doctree DTO into two parts. However, the rooted path over DTO contains
a node, its presequent siblings, its ancestors and their presequent siblings.

```
after the removal                                 |
===============================================   |
r -> fs .. ps -> a -> fs .. ps -> p -> fs .. ps   | <- rp(n) \ (n)
      | .. |           | .. |           | .. |    |
```

Based on that, one can describe this suffix-based removal as dropping the node
and its descendants over DTO, as well as each `(ns .. ls)` branch of all the
ancestors of `n` over DTU. Because of that, all the ancestors of `n` over DTU
will have one child only after this suffix-based removal. What remains of the
ordered doctree can therefore be described as the remainder of the rooted path
of `n` - that is, if the descendants over DTU of the presequent siblings of `n`
and all of its ancestors are ignored.
