
<!-- ======================================================================= -->
# the pre-order tree traversal

```
//- the default pre-order tree traversal
traverseInPreOrder(node) begin
  visit(node)
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end
end
```

Note that the pre-order traversal trace will contain the nodes in tree order
(i.e. ancestors before descendants) and also in child order (if one exists).
Because of that, the pre-order traversal trace is **order-preserving**.

```
n -|-> (ns .. ls)     =>     n -> (fc .. lc) -> (ns .. ls)
   |-> (fc .. lc)            n -> c -> s
```

Due to the above, **the pre-order rule** requires to first embed a child order
(even if only temporary), and then to append the sequence of subsequent siblings
`s(n)` to the sequence of child nodes `c(n)`. Because of that, and unlike the
embedding of a child order, the pre-order rule does not build upon pre-existing
edges.

* the pre-order rule := `n -> (c × s)`

Note that, since a (P)arent appears before its (D)escendants, and they before
any of its subsequent (S)iblings, the pre-order rule may also be referred to
as **the PDS rule/pattern** (aka. `p -> d -> s`).

Note that **no particular order of execution** is required (see below).

<!-- ======================================================================= -->
## applied to one node only

Since the resulting sequence, can be described as a new sequence of siblings,
the resulting sequence can be understood to replace a node's former sequence
of subsequent siblings.

```
n.s = (n.c × n.s)
n.c = null
```

With that in mind, the corresponding node can be treated as having no more
child nodes, which is why the pre-order rule can be understood to remove all
child nodes by turning them into siblings of their former parent. Because of
that, the pre-order rule can be said to push the child nodes of a node one,
including all of their descendants, one level closer towards the root.

Note that, if a node is a leaf, then the pre-order rule will have no effect
on it. Likewise, a node that had subsequent siblings will remain unchanged.
In contrary to that, a node that had child nodes will have its sequence of
(former) child nodes as ist new sequence of subsequent siblings.

Note that, in this context, a missing sequence of siblings can be treated as
being equivalent to an empty sequence (i.e. no null-reference error).

<!-- ======================================================================= -->
## applied to all the nodes (=> path graph)

```
n -> (fc .. lc) -> (ns .. ls)
      |..   |?      |..   |..
```

Since the former last child `lc` of node `n` is prepended to the former next
sibling `ns` of node `n`, node `lc` is set as the new previous sibling of
node `ns`. Because of that, `ns` becomes the next sibling of `lc`.

If `lc` has no child in the unordered doctree (i.e. a leaf), then `lc` is also
a leaf in the ordered doctree (i.e. it has no subsequent sibling and no child).
The pre-order rule then has the effect of turning a leaf node into one that is
no longer a last sibling to any node and therefore also **no longer a leaf**.

If `lc` has a child in the unordered doctree (i.e. if `lc` is a parent), then
it remains to be a parent that has `ns` as its next sibling. The pre-order rule
therefore also applies to `lc`, which will insert its child nodes as siblings
in between `lc` and `ns`.

The pre-order rule has in general the effect of turning nodes into siblings
that, apart from their next subsequent sibling, have **no child nodes**.

```
root -> (fc .. lc)
```

Since an unordered doctree is in general assumed to have two or more nodes,
the pre-order rule will turn the root's first child `fc` into its next, and
the root's last child `lc` into its last sibling `ls`. After that, the root
and its child nodes can be understood to represent a sequence of siblings.

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
an ordered tree into **a path graph** that has its **last subsequent leaf**
as its one and only leaf.

* tree-order + child-order + pre-order => pre-order trace

<!-- ======================================================================= -->
## no order of execution

Since the pre-order rule is such that it is required to apply to each parent
in a tree (i.e. a generic rule), and since a node and all of its descendants
form a substring to the trace of a tree, no particular order of execution is
required. That is, even though the root of a tree will in general be used as
a starting point, one can apply the rule to the nodes in any order and still
end up with the exact same trace of nodes.

(Think in terms of linked lists, not in terms of actual sequences/arrays).

**TODO** - align with the level-order section
