
<!-- ======================================================================= -->
# example - remove a node from a tree

Since the trivial suborder is a base order that can be used to define the
scope of an operation, the element-based removal is just as applicable in
the context of a node tree:

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 4 ) \ ( 2 ) = ( 1 -|-> 3 )
     |-> 3  |-> 5                  |-> 4
                                   |-> 5
```

As before, the operation can be understood from an order-based perspective.
That is, the operation can be said to form the resulting suborder `S*(U,<)`
by removing a suborder `R(T,<)` from the input order `S(V,<)`.

* `S* := (S \ R)` where `S := (V,G)`, `R := ({2},<)` and ..
* `G := (a < b) := aPb := { (1,2), (1,3), (1,4), (1,5), (2,4), (2,5) }`

As before, one begins by removing the to-be-removed elements in `T`, and
continues to re-establish the consistency be dropping all those edges in `S`
that have one of their endpoints in `T`. (Note that the relationships between
the remaining elements will not be changed).

* `S* := (U,G*)` where `U := (V \ T) := {1,3,4,5}` and ...
* `G* := (a < b) := aPb := { (1,3), (1,4), (1,5) }`

Note that the child nodes of the removed node (i.e. `2`) will become child
nodes of the node's parent (i.e. node `1`). Furthermore, all the child nodes
of the node's parent are equally relevant to it after the removal. (Recall
that a node tree has no child order).

Note that the result is formed similar to the element-based removal in the
context of an ordered sequence. After all, a path graph also satisfies the
requirements of a node tree. That is, the removal of node `2` from sequence
`(1,2,3)` can thus be said to turn node `3` (a child of `2`) into a child of
its parent node `1`.

Note that an alternative type of removal of a single node from a tree is to
return the subtrees that are adjacent to the corresponding node (i.e. the tree
falls apart into subtrees). That is, in the above example the operation would
return a path graph `(1 -> 3)`, and the two 1-node subtrees `(4)` and `(5)`.
In the context of this discussion, this type of removal is however not
considered relevant.
