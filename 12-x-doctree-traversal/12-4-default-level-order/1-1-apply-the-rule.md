
<!-- ======================================================================= -->
## applied to one node only

```
n.s = (n.s × n.c)
n.c = null
```

The effect of the level-order rule is such that a node can be treated as
having no more child nodes after the rule has been applied, which is why the
level-order rule can also be understood to remove all child nodes by turning
them into subsequent siblings of their parent. Because of that, the level-order
rule can also be said to push  the child nodes of a node, including all of
their descendants, one level closer towards the root.

Note that, if a node is a leaf, then even the level-order rule will have no
effect on it. Likewise, a node that had subsequent siblings, but no child nodes
will remain unchanged. In contrary to that, a node that had child nodes, but
no subsequent siblings will have its sequence of (former) child nodes as its
new sequence of subsequent siblings.

<!-- ======================================================================= -->
## applied to all the nodes => a path graph

Since the former first child `fc` of node `n` is appended to its former last
sibling `ls`, node `fc` is set as the new next sibling of `ls`. Because of
that, `ls` becomes the previous sibling of `fc`.

```
n -> (ns .. ls) -> (fc .. lc)
      |..   |?      |..   |..
```

If `ls` has no child in the unordered doctree (i.e. a leaf), then `ls` is also
a leaf in the ordered doctree (i.e. no subsequent sibling and no child). The
level-order rule has therefore the effect of turning a leaf node into one that
is no last sibling to any node and therefore also **no longer a leaf**.

If `ls` has a child in the unordered doctree (i.e. a parent), then it remains
to be a parent that has `fc` as its next sibling. The level-order rule therefore
also applies to `ls`, which will append its child nodes to `ls`.

The level-order rule has in general the effect of turning nodes into siblings
that, apart from their next subsequent sibling, have **no child nodes**.

```
root -> (fc .. lc)
```

Since an unordered doctree is in general assumed to have two or more nodes,
the level-order rule will turn the root's first child `fc` into its next, and
the root's last child `lc` into its last sibling `ls`.

```
root -> (ns .. ls) -> (fc .. lc)?
```

Similar to before, if `ls` (i.e. the root's former last child) has no child
in the unordered doctree (i.e. there is no `c := (fc .. lc)`), then it also
won't have a child in the ordered doctree. In that case, the last subsequent
sibling of the root **remains to be a leaf**.

If `ls` has a child in the unordered doctree, then the level-order rule also
applies to `ls`, which will turn `ls` into a node that has its former first
child `fc` as its next and its former last child `lc` as its last sibling.
Because of that, the former last child `lc` of `ls` becomes the root's new
last sibling `ls`. (Rinse and repeat until `ls` is a leaf).

Note that, after applying the level-order rule to the root, the rule may be
applied to any number of different nodes, before applying it to the root's
last sibling `ls`. In such a case, `ls` is no longer the root's last child,
but may be the former last child of another node instead. Because of that,
an order of execution must be defined.

Applying the level-order rule to all the nodes in an ordered tree will turn
an ordered doctree into **a path graph** that has the last child node of a
child order as its one and only leaf.

* tree-order + child-order + level-order => level-order trace
