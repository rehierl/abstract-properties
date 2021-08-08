
<!-- ======================================================================= -->
# Binary operations on trees

Note that the binary operations defined for general graphs still apply in the
context of node trees. However, the induced subtrees of a tree do not overlap
each other. That is, a pair of distinct induced subtrees in the context of a
common super-tree are either disjoint ex-or (strictly) related.

<!-- ======================================================================= -->
## union (+, or, union)

The union of two trees `R := (S + T)` is in general not a tree. That is,
depending on both input trees `S` and `T`, the result may be a single tree,
a forest of two trees, or a non-tree graph. The focus in the context of this
discussion will obviously be on the requirement that the result of a union
of trees is either a single tree ex-or a forest.

A forest of trees is defined as the union of disjoint trees. Consequently,
and in order to for the union of two trees to return a single tree, both
input trees `S` and `T` must not be disjoint. That is, both trees must have
a non-empty intersection (i.e. a common subtree).

For two trees `S` and `T` with root nodes `s` and `t`, the following cases can
be distinguished: (Case-0) both are equal, (Case-1) both are disjoint, (Case-2)
both are related, and (Case-3) both overlap each other.

Case-0: If both trees are equal, then the result will be equal to both. Put
differently, the union will in essence return a tree that is a clone to both.

Case-1: The result will be a forest of trees. That is because a forest is
defined as the union of disjoint trees.

Case-2: The result will be one of the input trees. That is because a subtree
can not add any new element to the union since all of its nodes/edges are
already nodes/edges in its super-tree.

* `((S + T) == S)` if `(S == T)`
* `((S + T) == S)` if `(T subtree-of S)`
* `((S + T) == T)` if `(S subtree-of T)`

Case-3: If two trees overlap each other, then both trees must have a non-empty
intersection. The following cases can be distinguished: (Case-4) neither root
is a node in the other tree, (Case-5) one and only one root is a node in the
other tree.

Case-4: If `t` is no node in `S` and `s` no node in `T`, then a node in the
non-empty intersection between both trees exists that has two distinct parent
nodes (one in `S` and the other in `T` - i.e. the root of the common subtree).
Because of that, the union of such trees would result in a non-tree graph since
that node would then have two parent nodes in the resulting graph. Consequently,
**the root of one tree must be a node in the other** if the result is required
to be a tree.

Case-5: If `t` is a node in `S`, but `s` no node in `T`, then `T` must have
leaf nodes not in `S`. That is because `T` would otherwise be a subtree to `S`.
The result in such a case is guaranteed to be a single tree. That is because
`(s ancestor-of t)` is true in `S`. Because of that, and since `T` is a tree,
`T` can not add any edge to the result that would force it to become a non-tree
graph.

<!-- ======================================================================= -->
## intersection (&, and, isect)

The intersection `R := (S & T)` of two distinct induced subtrees `S` and `T`
of a common super-tree `U` (i.e. `S := U[s]`, `T := U[t]` and `(s != t)`) is
either empty ex-or one of the input trees.

To proof that, the following cases need to be distinguished: (Case-1) `s`
is an ancestor of `t`, (Case-2) `t` is an ancestor of `s`, or (Case-3) `s`
is not an ancestor of `t`, and `t` not an ancestor of `s`.

Case-1/2: If `s` is an ancestor of `t`, then subtree `S` includes all the
nodes in `T`. Because of that, `T` is a proper induced subtree of `S`.
The intersection between `S` and `T` is therefore equal to `T`.

* `((S & T) == T)` if `(s ancestor-of t)`
* `((S & T) == S)` if `(t ancestor-of s)`
* i.e. `(S & T)` is in both cases a subtree of `S` and `T`
* `((S & T) != Ø) <-> (S related-to T)`

Case-3: Since both trees are disjoint, and no root is an ancestor of the other,
both trees have disjoint sets of nodes. Because of that, both subtrees are
disjoint. That is, the intersection between `S` and `T` is empty.

* `((S & T) == Ø)` if `(s !ancestor-of t)` and `(t !ancestor-of s)`

Consequently, two distinct induced subtrees in a tree either disjoint ex-or one
is a proper induced subtree of the other. Hence, no tree has a pair of induced
subtrees that overlap each other.

* `(S disjoint-to T) ex-or (S related-to T)` if `(S != T)`
* if `R := (S & T)`, then `(R in {Ø,S,T})`

<!-- ======================================================================= -->
## difference (\, sub, diff)

Recall that the graph difference `R := (S \ T)` is defined based on the removal
of vertices (i.e. the **vertex-based** definition). That is, the difference is
formed by removing all the vertices in the 2nd operand from the 1st operand,
including the implicit removal of all the edges incident to the vertices being
removed.

Note that, due to its definition (i.e. remove the elements of the 2nd tree
from the 1st tree) this operation is **not commutative**. That is, the order
of operands is relevant.

The difference of two trees is in general no tree. That is, depending on both
input trees, the result may be empty, a single tree, or a forest of two or more
trees. Similar as before, the focus will be on the requirement that the result
of such an operation is either empty ex-or a single tree.

Obviously, if both input trees `S` and `T` are disjoint, then the result of
`(S \ T)` is equal to `S`. That is because `T` then has no vertices that could
be removed from `S`.

* `((S \ T) == S)` if `(T == Ø)`
* `((S \ T) == S)` if `(T disjoint-to S)`

Because of that, both trees are in general expected to be coupled with each
other. More accurately, `T` is expected to to be reduced to the intersection
between both trees (i.e. `(T == (S & T))`). The root of `T` is thus expected
to be a node in `S`.

For two distinct trees `S` and `T` with root nodes `s` and `t`, the following
cases can be distinguished: (Case-1) `T` is equal to `S`, (Case-2) `T` is not
an induced subtree of `S` (i.e. `(T != S[t])`), and (Case-3) `T` is an induced
subtree of `S` (i.e. `(T == S[t])`).

Case-1: If `T` is equal to `S`, then the result of `(S \ T)` will be empty.

* `((S \ T) == Ø)` if `(T == S[s] == S)`

Case-2: If `T` is not an induced subtree of `S` (i.e. `(T != S[t])`), then `T`
is guaranteed to have a leaf `l` that is a node, but no leaf in `S`. Because of
that, the result of `(S \ T)` will contain an induced subtree for each child of
`l` in `S` (i.e. `S[c]` where `(c child-of l)`). The result is therefore in
general a forest of trees.

However, (1) if `t` is equal to `s`, and (2) if `T` has only one leaf `l`
that is a parent (and therefore no leaf) in `S`, and (3) if `l` only has a
single child `c` in `S`, then the result of `(S \ T)` will be a single tree
(i.e. `R == S[c]`). That particular case however is outside of the scope of
this discussion since the focus is on conditions that are in general true,
rather than on conditions that are true in a very particular case.

Case-3: Because `T` is an induced subtree of `S` (i.e. `(T == S[t])`), `T`
is guaranteed to have all the descendants of `t` in `S`. Because of that, the
result of `(S \ T)` can not contain any tree that is induced by a descendant
of `t` in `S`. Hence, the result is guaranteed to be a single tree (i.e.
`(S \ S[t])` for `(s != t)`).

Note that, in the context of this discussion, the difference between two trees
is, due to the above, required to either be empty ex-or a single tree. Because
of that, and in `(S \ T)`, **T must be an induced subtree of S**.

<!-- ======================================================================= -->
## symmetric difference (^, xor, ex-or)

Note that, since the difference requires the 2nd operand to be an induced
subtree, the "symmetric difference" operation (i.e. `(G \ S) + (S \ G)`)
is not applicable in the context of node trees. That is because the only
way to satisfy that precondition is for both trees to be equal.

* not applicable
