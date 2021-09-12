
<!-- ======================================================================= -->
# The removal of a node (2)

The following exemplifies the element-based and the suffix-based removal
in the context of an ordered tree. The result is on the node order of the
resulting tree since an ordered tree is itself just another un-ordered tree.

<!-- ======================================================================= -->
## recall the node order of an ordered tree

```
unordered tree (UT)        ordered tree (OT)            general pattern
===================   =>   =====================   =>   ===============
         p                 p -> fs .. ps -> n             n -|-> s(n)
         |                                  |                |-> c(n)
 -----------------                       -------
 | .. |  |  | .. |                       |     |
 fs  ps  n  ns  ls                       fc   ns
         |                               ..   ..
     ---------                           lc   ls
     fc ... lc
```

Recall that the addition of a child order to an unordered tree `UT` results
in an unordered tree such that each node in it has no more than two child
nodes (i.e. its former first child and its former next sibling).

On top of that, the former next sibling `ns` (i.e. the first node in `s(n)`)
and the former first child `fc` of node `n` (i.e. the first node in `c(n)`)
are equally significant in `OT`. That is because both nodes are incomparable
with each other (i.e. one can not determine which of these is presequent or
subsequent to the other).

One can therefore in general not distinguish between both nodes since the
information that would be required to tell them apart is not embedded into
the definition of an ordered tree (i.e. neither in its set of nodes, nor in
its set of edges). Because of that, an ordered tree is an unordered tree.

Also, the sequence of former subsequent siblings `s(n)` and the sequence of
former subsequent siblings `s(ps)` are related with each other (i.e. `s(n)`
is a suffix to `s(ps)`). That is, both are in general not disjoint from one
another (i.e. `s(ps) = (n × s(n))`). After all, since node `n` is the next
subsequent sibling of `ps` in `UT`, both share those siblings that are
subsequent to node `n`.

And finally, the last sibling of a node (i.e. `ls` to `n` and `lc` to `fc`)
are the only candidates for leaf nodes in `OT`. That is because these nodes
have no former subsequent sibling as an additional child in `OT`. From a
path-based perspective, `ls` and `lc` can in general both be understood to
represent dead ends from which no further nodes can be reached. (That is
for as long as their own former child nodes can be ignored).

However, since each ordered tree is an unordered tree, the element-based and
the suffix-based removals are both applicable.

<!-- ======================================================================= -->
## (Ex-5) a suffix-based removal from an ordered tree

As stated before, and in regards to unordered trees, we in general choose to
remove entire induced subtrees (e.g. `t[n]`, i.e. node `n` and all of its
descendants) rather than restrict the removal to a single node.

Since an ordered tree is itself an unordered tree, the definition of an induced
subtree remains as is: An induced subtree begins at its root, includes all of
its descendants and all the edges in between these nodes. As such, the induced
subtree `t[n]` in an ordered tree includes the sequence of former child nodes
`c(n)`, the sequence of former subsequent siblings `s(n)` and the descendants
of these nodes.

If an induced subtree is to be removed from an ordered tree, then the following
two cases can be distinguished: (1) node `n` is the first child of `p` in `UT`,
and (2) node `n` has a presequent sibling `ps` in `UT` (i.e. `n` is in `UT` a
non-first child to its parent `p`).

```
S                      \ R               = S*
==========================================================
( p -|-> s(p)        ) \ ( n -|-> s(n) ) = ( p -|-> s(p) )
     |-> n -|-> s(n)          |-> c(n)          |-> X
            |-> c(n)
```

In case-1, `n` is the former first child of its parent `p`. As such, `p` may
or may not have a former next sibling `ns` as its second child in `OT`. After
the removal of `t[n]`, `p` therefore has in general no more than one child:
its former next subsequent sibling `s(p)` (i.e. `X` indicates that `c(p)` no
longer exist).

Note that removing `t[n]` from `OT` in such a case corresponds with removing
all the descendants of `p` in `UT`. That is, parent `p` will be a leaf in
`UT`, regardless of how many siblings `n` might have had.

Note that, since parent `p` is not required to have a former next sibling,
`p` will be a leaf in `OT`, if `p` had no subsequent sibling in `UT`.

```
S                       \ R               = S*
=============================================================
( ps -|-> n -|-> s(n) ) \ ( n -|-> s(n) ) = ( ps -|-> X     )
      |      |-> c(n)          |-> c(n)           |-> c(ps)
      |-> c(ps)
```

In case-2, `n` is a non-first child of its former parent `p` in `UT`. Because
of that, `n` has its former presequent sibling `ps` as its parent in `OT`.
After the removal of `t[n]`, `ps` has in general no more than one child: its
former first child `c(ps)` (i.e. `X` indicates that `s(ps)` no longer exists).

Note that removing `t[n]` from `OT` in such a case corresponds with turning
`ps` into the last child of parent `p` in `UT`.

Note that, since `ps` is not required to have a former first child, `ps`
will be a leaf in `OT`, if `ps` had no child in `UT` (i.e. a leaf in `UT`).

<!-- ======================================================================= -->
## (Ex-6) an element-based removal from an ordered tree

Since an ordered tree is an unordered tree, the element-based removal of a
node from an ordered tree is effectively the same as in example Ex-4. That is,
the child nodes of the to-be-removed node `n` will become child nodes of the
node's parent. Because of that, this example will focus on the resulting node
order after an element-based removal.

As before, two cases can distinguished: (1) node `n` is the first child of `p`
in `UT`, and (2) node `n` has a presequent sibling `ps` in `UT` (i.e. `n` is
in `UT` a non-first child to parent `p`).

```
S                      \ R     = S*
================================================
( p -|-> s(p)        ) \ ( n ) = ( p -|-> s(p) )
     |-> n -|-> s(n)                  |-> s(n)
            |-> c(n)                  |-> c(n)
```

In case-1, `n` is the first child of `p` in `UT`. As such, `p` may or may not
have a next sibling `ns` in `UT` as its second child in `OT`. Because of that,
`p` will in general have three child nodes after the removal of node `n`: (1)
the former next sibling `s(p)`, (2) the former next sibling `s(n)`, and (3)
the former first child `c(n)`.

However, since parent `p` is not required to have a former next sibling, and
since node `n` is also not required to have a former first child, or even a
former next sibling, `p` may be a leaf in `OT` after the removal of node `n`.

To be more accurate, `p` will be a leaf in `OT`, if `n` is the only child of
`p` and itself a leaf in `UT`, and if `p` is the last child of its own former
parent in `UT`. That is, the removal of a node will in general result in `p`
having up to three child nodes (i.e. `(#CN(p) == [0,3])`).

```
S                       \ R     = S*
==================================================
( ps -|-> n -|-> s(n) ) \ ( n ) = ( ps -|-> s(n) )
      |      |-> c(n)                   |-> c(n)
      |-> c(ps)                         |-> c(ps)
```

In case-2, `n` is a non-first child of `p` in `UT`. Because of that, `n` has its
former presequent sibling `ps` as its parent in `OT`. After the removal of `n`,
`ps` will in general have three child nodes: (1) the former next sibling `s(n)`,
(2) the former first child `c(n)`, and (3) the former first child `c(ps)`.

Similar to before, `ps` will be a leaf in `OT`, if `n` is the last subsequent
sibling of `ps` and a leaf in `UT`, and if `ps` is itself a leaf in `UT`. That
is, the element-based removal of a node will in general result in `ps` having
up to three child nodes (i.e. `(#CN(ps) == [0,3])`).

<!-- ======================================================================= -->
## remarks

As can be seen above, the suffix-based removal of a node from an ordered tree
does not change the general structure of an ordered tree. That is, after such
a removal the ordered tree will still be such that "each node has up to two
child nodes" (i.e. `(#CN(n) == [0,2])`). Because of that, the tree's pre-order
trace can still be formed.

In contrary to that, the element-based removal of a node from an ordered tree
has in general the effect of changing the characteristic of an ordered tree to
"each node may have up to three child nodes" (i.e. `(#CN(n) == [0,3])`). This
however invalidates the pre-order rule since it is defined based upon the
concatenation of two sequences.
