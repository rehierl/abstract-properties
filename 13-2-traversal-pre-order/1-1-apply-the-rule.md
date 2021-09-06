
<!-- ======================================================================= -->
## applied to one node only

```
n.s = (n.c × n.s)
n.c = null
```

Since the pre-order rule will effectively prefix a node's current sequence
of subsequent siblings with its child order, a node can be treated afterwards
as having no more child nodes, which is why the pre-order rule can be said to
remove all child nodes by turning them into subsequent siblings of their former
parent. Because of that, the pre-order rule can be said to push the child nodes
of a node, including all of their descendants, one level upwards closer the
tree's root.

Note that, in this context, a missing sequence can be treated as being
equivalent to an empty sequence (i.e. no null-reference error).

Note that, if a node is a leaf, then the pre-order rule will have no effect
on it. Likewise, a node that had subsequent siblings but no child nodes will
remain unchanged. In contrary to that, a node that had child nodes but no
subsequent siblings will have its sequence of (former) child nodes as its
new sequence of subsequent siblings.

<!-- ======================================================================= -->
## applied to all the nodes => a path graph

Note that the following is in regards to applying the pre-order rule to all
the nodes with no particular order of execution in mind. Also recall that the
focus is ultimately on reducing the number of leaf nodes to one leaf only.

Since the former last child `lc` of `n` is prepended to the next sibling `ns`
of node `n`, node `lc` is set as the previous sibling of `ns`. Because of that,
`ns` becomes the new next sibling of `lc`.

```
n -> (fc .. lc) -> (ns .. ls)
      |..   |?      |..   |..
```

If `lc` has no child in the unordered doctree (i.e. a leaf), then `lc` is also
a leaf in the ordered doctree (i.e. no subsequent sibling and no child). The
pre-order rule therefore has the effect of turning a leaf node into one that
is no longer a last sibling to any node and therefore also **no longer a leaf**.

If `lc` has a child in the unordered doctree (i.e. a parent), then it remains
to be a parent that has `ns` as its next sibling. The pre-order rule therefore
also applies to `lc`, which will insert its child nodes as siblings in between
`lc` and `ns`. Because of that, the first child of `lc` will become the node's
new next subsequent sibling.

The pre-order rule has in general the effect of turning nodes into siblings
that, apart from their next subsequent sibling, have **no child nodes**.

```
root -> (fc .. lc)
```

Since an unordered doctree is in general assumed to have two or more nodes,
the pre-order rule will turn the root's first child `fc` into its next, and
the root's last child `lc` into its last sibling `ls`.

```
root -> (ns .. ls) -> (fc .. lc)?
```

Similar to before, if `ls` (i.e. the root's former last child) has no child
in the unordered doctree (i.e. there is no `c := (fc .. lc)`), then it also
won't have a child in the ordered doctree. In that case, the last subsequent
sibling `ls` of the root **remains to be a leaf**.

If `ls` has a child in the unordered doctree, then the pre-order rule also
applies to `ls`, which will turn `ls` into a node that has its former first
child `fc` as its next and its former last child `lc` as its last sibling.
Because of that, the former last child `lc` of `ls` becomes the root's new
last sibling `ls`. (Rinse and repeat until `ls` is a leaf).

Applying the pre-order rule to all the nodes in an ordered doctree will turn
an ordered doctree into **a path graph** that has its **last subsequent leaf**
as its one and only leaf.

* tree-order + child-order + pre-order => pre-order trace
