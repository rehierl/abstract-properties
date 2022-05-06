
<!-- ======================================================================= -->
# suffix over DTR

The following will examine the effects of the removal of a suffix over the
trivial base order DTR in regards to the unordered doctree DTU, the ordered
doctree DTO, and the doctree's pre-order trace DPR.

Recall that each suffix over the trivial base order DTR consists of one node
only. Because of that, this kind of removal is also referred to as an element
based removal.

<!-- ======================================================================= -->
## suffix over DTR in DPR

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 3 ) \ ( 2 ) = ( 1 -> 3 )
     |----->|
```

The effects of this element-based removal have already been examined in "remove
a node from a sequence". That is, the result can be seen as the concatenation
of a prefix and a suffix, both of which can be understood to be restricted
(i.e. `[1,2)` and `(2,3]`) by the removed node.

Note that, since each path graph satisfies the requirements of a node tree, the
effects of this element-based removal can be understood as a special case of the
effects on a general tree. That is, node `3` will become a child of node `1` in
the resulting node tree.

<!-- ======================================================================= -->
## suffix over DTR in DTU

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 4 ) \ ( 2 ) = ( 1 -|-> 3 )
     |-> 3  |-> 5                  |-> 4
                                   |-> 5
```

The effects of this element-based removal have already been examined in "remove
a node from a tree". That is, the child nodes of the removed node will become
additional child nodes of the node's parent.

Recall that a general tree, including the unordered doctree DTU has no child
order. Because of that, nodes `3`, `4` and `5` are equally relevant to `1`.

<!-- ======================================================================= -->
## suffix over DTR in DTO

Since an ordered doctree is itself also a node tree with no child order, one
might assume that the effects of this element-based removal is effectively
the same as shown in regards to the unordered doctree.

Two cases can be distinguished: (1) the to-be-removed node `n` is the first
child of its former parent `p`, and (2) node `n` has a presequent sibling
`ps` in DTU (i.e. `n` is a non-first child to `p`).

```
S                      \ R     = S*
================================================
( p -|-> s(p)        ) \ ( n ) = ( p -|-> s(p) )
     |-> n -|-> s(n)                  |-> s(n)
            |-> c(n)                  |-> c(n)
```

Recall that `s(x)` is used to denote the sequence of subsequent siblings of `x`,
and that `c(x)` is used to denote sequence of child nodes (i.e. its child order)
of `x`. In addition to that, each of these sequences may in general be empty.
That is, node `n` is in general not required to have a next sibling or even a
first child.

```
S                       \ R     = S*
==================================================
( ps -|-> n -|-> s(n) ) \ ( n ) = ( ps -|-> s(n) )
      |      |-> c(n)                   |-> c(n)
      |-> c(ps)                         |-> c(ps)
```

As can be seen, the element-based removal of a node from DTO has the effect of
changing the general characteristic of an ordered doctree from "each node has
no more than two child nodes" to "each node may have up to three child nodes".

Because of that, and since the pre-order rule is defined for two particular
child nodes only (i.e. the former first child and the former next subsequent
sibling), this rule can strictly speaking no longer be understood to apply.

<!-- ======================================================================= -->
## suffix over DTR in DPR (2)

Since the element-based removal of a node from the ordered doctree DTO will
in general result in a tree such that the pre-order rule no longer applies,
one needs take the effect of the element-based removal on the doctree's child
order into account. After all, the to-be-removed node is also an element in
the child order of its parent.

```
before the removal        after the removal         |
==================   =>   =======================   |
         p                           p              |
         |                           |              |
 -----------------        -----------------------   |
 | .. |  |  | .. |        | .. |  | ... |  | .. |   |
 fs  ps  n  ns  ls        fs  ps  fc   lc  ns  ls   | <- c(p)
         |                                          |
     ---------                                      |
     fc ... lc                                      | <- c(n)
```

As can be seen, the above planar tree (has a child order associated with it)
is changed such that the child nodes `fc` to `lc` of the removed node `n` will
become additional child nodes of the node's parent `p`, while maintaining the
child order of `n`. That is, the child order of a node will not be removed with
it. Instead, the child order of the node's parent changes such that the node
in it is replaced by the node's child order.

* `c1 := c(p) := (fs,..,ps,n,ns,..,ls)` and `c2 := c(n) := (fc,..,lc)`
* `c1` changes into `c3 := (fs,..,ps,ns,..,ls)`
*  and then into `c4 := (fs,..,ps,fc,..,lc,ns,..,ls)`

Note that this change is reflected in the tree's pre-order trace:

* `t1 := t(p) := (fs,..,ps,..,n,fc,..,lc,..,ns,..,ls,..)`
* changes into `t2 := (fs,..,ps,..,fc,..,lc,..,ns,..,ls,..)`

Note that all of the above child orders (i.e. `c1` to `c4`) are suborders to
the initial pre-order trace `t1`. However, `c1` is no suborder to the resulting
pre-order trace `t2`, which is consistent with effects of the element-based
removal on DPR.

Note that the child order `c(p)` must be changed since an element in it (i.e.
node `n`) will be removed. Also, the child order `c(n)` must be integrated into
`c(p)` since its point of reference (i.e. node `n`) will be removed.

* `c4 := (fs,..,ps,fc,..,lc,ns,..,ls)`

<!-- ======================================================================= -->
## suffix over DTR in DTO (2)

Since the child order of the node's parent changes with the node's removal, the
doctree's child order can not simply be ignored. The node order of the ordered
doctree DTO must therefore be changed accordingly.

```
before the removal                      after the removal
================================   =>   =====================================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps -> fc .. lc -> ns .. ls
                    |-> fc .. lc
```

Due to the above, the element-based removal of node `n` from an ordered doctree
DTO changes the node order as shown above such that the node's parent in DTO
(i.e. `p` or `ps`) will have one child only, not up to 3 child nodes. That is
because the removal must also affect the doctree's child order, which, adds to
the transformation of DTO.
