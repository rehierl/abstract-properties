
<!-- ======================================================================= -->
## relationships

```
multiset-of-trees = <
A: 1 , B: 4 , C: 4 , D: 2 , E: 2, F: 2
  ===    ===    ===    ===          ===
  2 3     2      2      5           1 3
>
```

Elements/Trees B and C represent trees that are equal. The relationship between
both trees is therefore neither "disjoint" nor "properly related". Because of
that, there is no **distinct order** (i.e. inside vs. outside -or- subtree vs.
super-tree) between the two.

Consequently, and in order to avoid these kind of circumstances, each element
must represent a unique tree. Put differently, all trees **must be distinct**,
which is why a set-of-trees, rather than a multiset-of-trees is required.

Similar to that, there is no distinct relationship between trees A and B. That
is because both trees have some nodes in common (i.e. coupled with each other)
and nodes the other tree does not have (i.e. not related). As such, both trees
can be understood to **overlap** each other and therefore to represent another
type of relationship between two trees.

Likewise, trees A and D overlap each other. However, the root of D is a node
in A, which is why the union of both trees is, in contrary to (A + B), a tree.
As before, there is no clear relationship between A and D.

Note that, due to the overall intent of forming sets of trees that are related
in some way, a setup of trees will have to be required to be **well formed**.
That is, the trees in such a setup must be such that the node orders they
represent do not contradict each other - e.g. the ancestor of a node in a tree
can not be the descendant of that node in another tree as is the case with
trees A and F.
