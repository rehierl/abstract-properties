
<!-- ======================================================================= -->
# hierarchy of trees

Similar to a hierarchy of sets, a partial setup of trees `S` can only correspond
with a tree that has one node for each tree `T(N,E)` in `S` (i.e. `(#N == #s)`).
That is, the amount of nodes in `T` is independent of the amount of nodes in
each tree in `S`. Also, the relationships of the nodes in `T` is embedded into
the relationships between the trees in `S`.

In contrary to a hierarchy of sets, the elements in a partial setup of trees
are actual node trees, each of which has one and only one dedicated element,
its root node. Because of that, definitions that are analogous to those of
characteristic subsets (CSS) and characteristic elements (CE) are not required.

Note however, that the removal of all the proper subtrees of a tree from that
tree will result in a 1-node tree that only consists of the supertree's root.
Because of that, the root node of a tree can be described as the tree's
characteristic element (CE).
