
<!-- ======================================================================= -->
## relationships

A possible multiset of trees may be as follows:

```
A: 1 , B: 4 , C: 4 , D: 2 , E: 2, F: 2
  ===    ===    ===    ===          ===
  2 3     2      2      5           1 3
```

Trees B and C are both equal, which is why the relationship between both tree
instances is neither "disjoint" nor "properly related". Because of that, there
is no **distinct order** (i.e. subtree vs. super-tree) between the two.

Consequently, and in order to avoid these kind of circumstances, each element
must represent a unique tree. In other words, all trees **must be distinct**,
which is why a set-of-trees, rather than a multiset-of-trees is required to
form a hierarchy of trees.

Similar to that, there is no distinct relationship between trees A and B. That
is because both trees have a node in common (i.e. coupled) and nodes the other
tree does not have (i.e. unrelated). As such, both trees can be understood to
**overlap** each other and therefore to represent a third type of relationship
between two trees (i.e. in addtion to disjoint and related).

Likewise, trees A and D overlap each other. However, the root of D is a node
in A, which is why the union of both trees is, in contrary to (A + B), a tree.
As before, there is no clear relationship between A and D.

Finally, trees A and F are also coupled with each other since both have all of
their nodes in common. However, both trees have none of their edges in common -
i.e. edges (1,2) and (1,3) in A are no edges in B, and edges (2,1) and (2,3)
in B are no edges in A. Because of that, the intersection graph (A & B) is a
trivial subgraph to both trees (i.e. all the nodes, but none of the edges) and
as such no tree.

Note that, due to the overall intent of forming sets of trees such that the
trees in them are either disjoint ex-or related in some way, a setup of trees
will have to be **well formed**. That is, the trees in a setup must be such
that the node orders they represent do not contradict each other - e.g. the
ancestor of a node in a tree must not be the descendant of that node in another
tree, as is the case with trees A and F.
