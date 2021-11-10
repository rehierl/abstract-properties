
<!-- ======================================================================= -->
# remarks about the embedding of node definitions

Note that the following is in regards to forming a node tree `T(N,E)`
from a partial setup of trees `S`.

```
S: a hierarchy of trees               T: node tree
================================  =>  ============
{ A: 1 ,  B: 1 ,  C: 3 ,  D: 4 }           A
    / \      |       |                    / \
   2   3     2       6                   B   C
   |  / \    |                           |
   4 5   6   4                           D
```

Note that ...

* labels `A` to `D` are not part of setup `S`.
* the resulting tree `T` has 4 nodes, not 6.
* the trees in `S` are arbitrary subtrees to their ancestors.

Similar to a hierarchy of sets, a partial setup of trees `S` corresponds with
a tree `T(N,E)` that has one node for each tree in `S` (i.e. `(#N == #S)`).
That is, the amount of nodes in `T` is independent of the amount of nodes in
each tree in `S`.

Also, the relationships of the nodes in `T` is defined by the relationships
between the trees in `S`. The nodes of each tree in `S` is therefore secondary.
Because of that, a setup `S` does not contain any characteristics which could
be relied upon in order to recreate the nodes in `T`.

<!-- ======================================================================= -->
## missing characteristics

Further requirements are therefore required, which allow to determine the
definition of a node that corresponds with a particular tree in `S`.

Since it must be possible to reliably determine which node tree `t` represents,
each node `n` in `T` must be a node in `t`. Because of that, `n` must also be
a node in all of the supertrees `A(t)` of that tree. - Note that this does not
state that `n` can not also be a node in any of the subtrees in `D(t)`.

Since the structure of the resulting tree `T` is such that it has `#S` nodes,
one for each tree in `S`, `#S` node definitions must be embedded into `S`.
Furthermore, the node definitions must be embedded such that each definition
can be determined from the corresponding tree.

<!-- ======================================================================= -->
## missing requirements

In contrary to a hierarchy of sets, the elements in `S` are actual node trees,
each of which has one and only one dedicated element, its root node. Because of
that, definitions that are analogous to those of characteristic subsets (CSS)
and characteristic elements (CE) are not required.

Note that the removal of all the proper subtrees of a tree `(t in S)` from `t`
results in a 1-node tree, which only consists of the tree's root node. Because
of that, the root node of a tree can be seen as a characteristic element (CE).

Since each tree is guaranteed to have a root node, the root node of each tree
`t` in `S` can and must be used in order to provide the definition (i.e. a
node reference) of the corresponding node in `T`.

Note that a node tree in setup `S` has no other characteristics that could be
relied upon in order to embed the definition of the nodes in `T`. Because of
that, each tree can only hold one such definition in its root.

<!-- ======================================================================= -->
## types of subtrees

As can be seen above, there is no explicit requirement in regards to the
relationships between the trees in `S`. That is, the subtree `s` of a tree
`t` is strictly speaking not required to be an induced subtree of `t`.

However, since subtree `s` of tree `t` must be a subtree to each tree in
`A(t)`, it seems to be an implicit necessity that the trees in `S` must be
induced subtrees to their ancestors. That is because one could otherwise
not determine all of the ancestors of each tree in `S`.

Note that, in order to form an actual order relation from a setup of trees,
one must be able to determine the relationship of a tree with each tree in
`A(t)`. That is because an order relation must by definition be transitive.
