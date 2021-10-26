
<!-- ======================================================================= -->
# an intermediate summary

The following examples will examine the effects of the removal of a suffix over
one base order in regards to the other base orders.

<!-- ======================================================================= -->
## a base order recap

```
unordered doctree (DTU)        ordered doctree (DTO)
=======================   =>   ================================
         p                     p -> fs .. ps -> n -|-> ns .. ls
         |                                         |-> fc .. lc
 -----------------
 | .. |  |  | .. |
 fs  ps  n  ns  ls
         |
     ---------
     fc ... lc
```

Recall that embedding the child order of a document tree into the doctree's
unordered node order (DTU) transforms the tree order into the doctree's
ordered node order (DTO) such that no node has more than two child nodes,
its former next sibling (ns) and its former first child (fc).

```
pre-order trace
========================================================
r .. p fs .. ps .. n fc .. lc .. /n ns .. ls .. /p .. /r
                   |-s1-----------|
                   |-s2--------------------------|
                   |-s3--------------------------------|
```

Furthermore, applying the pre-order rule to the ordered doctree (DTO) turns the
tree order into the total node order of the doctree's pre-order trace (DPR).

<!-- ======================================================================= -->
## remarks

Note that the element-based removal is from a generalized point of view also a
suffix-based removal. That is, a suffix over the trivial base order is removed
from the input order. It just so happens that each suffix over the trivial base
order only consists of a single element. The removal of a node is therefore
**always a suffix-based removal** over the corresponding base order.

Note that each **ordered sequence** corresponds with **a path graph**. And
since each path graph satisfies the requirements of a tree, it can be described
as **an unordered doctree** (type-1, DTU). Furthermore, and since a path graph
is such that each node has no more than one child, the path graph of an ordered
sequence can also described as **an ordered doctree** (type-2, DTO). That is,
the embedding of the child order has no effect. Finally, a path graph can be
described as **a doctree's preorder trace** (type-3, DPR). Consequently, all
base orders that are available in the context of a general doctree are available
as a base order. However, since all non-trivial base orders are equal, one can
state that an ordered sequence does not support any other base order than the
trivial order and the total node order of an ordered sequence.

Note that the removal of an element can not affect the relationships between
the remaining elements. That is because after removing an element from an
ordered set, all those edges in the order relation must be dropped that still
have the removed element as one of its endpoints. Based on that point of view,
the general description of how a subsequence is formed (i.e. "remove an element
**while maintaining the order** between the remaining elements") is somewhat
inaccurate. That is because the order relation must be updated in regards to
those elements that were removed (in order to re-establish consistency), not
in regards to those elements that still remain.
