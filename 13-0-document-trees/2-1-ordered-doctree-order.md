
<!-- ======================================================================= -->
## the node order of an ordered doctree

```
edges        graph T      \(n,lc)      cover graph T*
======   =>  =======  =>  =======  =>  ==============
 (n,fc)         n            n         n -> fc -> lc
 (n,lc)         |            |
+(fc,lc)     -------      -------
             |     |      |
            fc --> lc    fc --> lc
```

In general, embedding the child order of a doctree into its node order will
first turn the node tree into a non-tree graph such that each non-first child
has two parent nodes. A subsequent transitive reduction will then drop the
edges between a former non-first child and its former parent node.

```
         p           | tree-order:
         |           | top-to-bottom oriented
 -----------------   | "ancestor-of"
 | .. |  |  | .. |   |
 fs  ps  n  ns  ls   | child-order:
         |           | left-to-right oriented
      -------        | "presequent-sibling-of"
      | ... |        |
      fc   lc        |
```

That is, node `n` has `ps` as its previous sibling, `ns` as its next sibling,
`fc` as its first child and `lc` as its last child. Similar to that, node `p`
has `fs` as its first child (i.e. the "first sibling" of `n`) and `ls` as its
last child (i.e. the "last sibling" of `n`).

With the above in mind, one can then perform the same steps in regards to the
child order of the parent `p` of node `n`. What remains is a cover graph whose
general structure is as follows:

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Depending on the relationship between node `n` and its neighbors, the resulting
graph, after the explicit addition of a child order, has the following patterns.

```
root       1-st child of p    n-th child of p  |  in short
=======    ===============    ===============  |  ==========
n -> fc    p -> n -|-> ns     ps -> n -|-> ns  |  n -|-> s
                   |-> fc              |-> fc  |     |-> c
```

Consequently, a child in the cover graph of an unordered doctree has one
incoming edge in the ordered doctree whose source is either the node's
former parent `p` exor the node's former previous sibling `ps`.

* Each node in the resulting graph has **no more than one parent**.

In addition to that, a parent in the ordered doctree has two outgoing edges
such that one sink is its former next sibling `ns` and the other its former
first child `fs`, regardless of how many child nodes that parent had in the
unordered doctree.

* Each node in the resulting graph has **no more than two child nodes**.

Note that for each parent in the cover graph, one or both of its child nodes
may not exist. That is, a node may be a leaf, a parent that is missing `ns`,
a parent that is missing `fc`, or a parent that has both of these nodes as
its child nodes.

<!-- ======================================================================= -->
## an ordered doctree is a node tree

Since the root of the unordered doctree has no parent and no presequent
sibling, the former root has no incoming edge in the resulting graph. That
is, the root of the unordered doctree will be a root in the resulting graph.

* The root of the unordered doctree is a root in the resulting graph.
* The resulting graph **has a root**.

And since that root also has no subsequent sibling in the unordered doctree,
that root will have **one child only** in the resulting graph. That is, the
root's former first child is the root's only child in the resulting graph.

Since the transitive reduction will only replace the parent of a non-first
child with its former presequent sibling, the resulting graph has no further
root. That is, no child in the unordered doctree will become a root in the
resulting graph.

That is, each child in the unordered doctree remains to be a child in
the resulting graph. No child in the unordered doctree therefore become a
root in the resulting graph.

* The resulting graph has the root of the unordered doctree as its only root.
* The resulting graph has **one root only**.

The transitive reduction performed after adding the child order ensures that
each node has no more than one incoming edge. In addition to that, and as
stated before, no child node will become a root node.

* Each node in the resulting graph has **no more than one parent**.
* Each former child node remains to be a child node in the resulting graph.

Recall that each node in a node tree has a unique, strictly downward oriented
rooted path which connects a tree's root with one of its descendants. Because
of that, the the node levels of the nodes in a rooted path is strictly monotone
increasing with each subsequent node.

With that in mind, the embedding of a child order can be understood to add
horizontal, strictly left-to-right oriented edges that are neither downwards-
nor upwards oriented. The resulting graph will therefore have **no cycles**.
(Recall that loops can be understood as 1-node cycles).

* Each node in the resulting graph as a **unique rooted path**.

Due to the above, the transitive reduction performed after the addition of
a child order ensures that the resulting graph is once again a proper node
tree.

* The cover graph of an ordered doctree **is a node tree**.

Note that, since there is no edge that connects the former next sibling of
a node with its former first child, the tree order of an ordered doctree
has once again **no child order**.

Note that, due to the above, the old definition of the description as
**ordered tree** (i.e. a tree that has some external child order associated
with it) is misleading. After all, no node tree will ever be such that it has
a child order. Because of that, **this old definition must be deprecated**.
