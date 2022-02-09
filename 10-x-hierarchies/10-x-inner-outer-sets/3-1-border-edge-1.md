
<!-- ======================================================================= -->
# the border graphs of (induced) subtrees

In the following discussion, `S` is formed as a subtree of `G`. Because of that,
`S` must be the subtree of a component in `G` as `S` could otherwise not be a
tree since trees are by definition connected. Consequently, `G` can be thought
of as being reduced to the relevant maximal component in `G`, which is why `G`
can be treated as a connected graph. That is, the components in `G` that are not
connected with `S` will be ignored since they are non-essential to the following
discussion.

Note that the border graph of a proper induced subtree `S := T[r]` consists
of one edge only. That edge begins in the parent `p` of root `r` in `T` (i.e.
`e := (p,r)`) and ends in `r`. As such, that edge will be referred to as
**the border edge** (in short: `BE(T,S) := e`).

<!-- ======================================================================= -->
## subtree S of super-tree T

The following assumes the super-graph `G := (V,E)` of subtree `S := (M,F)` to
be a tree `T := (N,E)` (i.e. `G := T`). Because of that, `(S == T[M])` is true.
That is, `S` is equal to the subgraph, induced by the set nodes in `S`.

**generic subtrees**

The generic method used to define subtrees (i.e. `subtreeOf(T,r,LS)`) will
be covered by the following two cases in which the definition of the induced
subtrees is based upon subsets of elements.

The two aspects that need to be taken into account are, (1) whether or not the
root `r` of subtree `S` is identical to the root of the super-tree `T` (i.e.
`(RN(S) == RN(T))`), and (2) whether or not the subtree contains all the leaf
nodes that can be reached in `T` beginning with the subtree's root.

**induced by a subset of nodes - i.e. T(M)**

If `S` is induced by the entire set of nodes in `T` (i.e. `(M == N)`), then
both border graphs are empty (i.e. `(IBG == Ø)` and `(OBG == Ø)`). That is
because `S` is then identical to `T` (i.e. `(S == T)`).

If, in contrary to that, `S` is induced by a proper subset of nodes (i.e.
`(M proper-subset-of N)`), then the inner border graph is still empty (i.e.
`(IBG == Ø)`). That is because `T` is a tree and because `S` then contains
all the edges whose endpoints are both in `S`.

However, the outer border graph is never going to be empty (i.e. `(OBG != Ø)`,
i.e. `(OBGi != Ø)` and/or `(OBGo != Ø)`), if `S` is a proper subtree of `T`.
To be more accurate, `OBGi` is non-empty, if the root of `S` is unequal to
the root of `T`. Likewise, `OBGo` is non-empty, if not all of the leaf nodes
of `r` in `T` are also leaf nodes in `S`.

**induced by a subset of edges - i.e. T(F)**

If `S` is induced by the entire set of edges in `T` (i.e. `(F == E)`), then
both border graphs are empty (i.e. `(IBG == Ø)` and `(OBG == Ø)`). That is,
because `S` then is identical to `T` (i.e. `(S == T)`).

If, in contrary to that, `S` is induced by a proper subset of edges (i.e.
`(F proper-subset-of E)`), then the inner border graph is still empty (i.e.
`(IBG == Ø)`). That is because `T` is and `S` must be a tree. Put differently,
every edge in `T` in between the nodes of `S` must be included.

However, the outer border graph is never going to be empty (i.e. `(OBG != Ø)`,
i.e. `(OBGi != Ø)` and/or `(OBGo != Ø)`), if `S` is a proper subtree of `T`.
As before, `OBGi` is non-empty, if the root of `S` is unequal to the root of
`T`. Likewise, `OBGo` is non-empty, if not all of the leaf nodes of `r` in `T`
are also leaf nodes in `S`.

<!-- ======================================================================= -->
## summary

The inner border graph `IBG` in between `T` and `S` is (always) empty.

* `(IBG(T,S) == Ø)`

In contrary to that, the outer border graph `OBG` in between `T` and `S` is not
necessarily empty. That is because `OBGi` is not empty, if the root of `S` is
not identical to the root of `T`. Likewise, `OBGo` is not empty, if not all of
the leaf nodes of `r` in `T` are also leaf nodes in `S`. Put differently, `T`
may in general have a single edge that ends begins in `(T \ S` and ends in `S`,
and one or more edges that begin in `S` and end in `(T \ S)`.

* `(OBG(T,S) <=!=> Ø)`, where `OBG := (OBGi + OBGo)`
* i.e. `OBGi` and `OBGo` are both not necessarily empty
* `(OBG(T,S) == Ø)` if, and only if `(T == S)`

Note that the outer border `OBGi` in between `T` and `S` is non-empty, if `S`
is induced by a descendant `r` of the root in `T` (i.e. `S := T[r]`). That is
because `r` is then a child node in `T`.

* `r` is the root of `S` and `S := T[r]`
* `p` is the parent of `r` in `T` - i.e. `(r != t)`
* `(OBGi(T,S) == {e})` where `(e == (p,r))`

Note that the outer border `OBGo` in between `S` and `T` is empty, if `S` is
induced by some node `T` (i.e. `(S := T[r])`). That is because `S` then has
all the leaf nodes of `r` in `T`.

* `(OBGo(T,S) == Ø)`, if `S := T[r]`

Any proper induced subtree `S := T[r]` is connected to its super-tree `T` by
a single edge `(e in OBGi)`. That edge connects the subtree's root `r` with
its parent node in `T` and is incoming in regards to `r` (i.e. root `r` is
the sink of `e`). As such, `e` reflects the relationship between both trees.

Note that, due to the above, the single edge `e` in `OBGi` will simply be
referred to as the **border edge** (in short: `BE(T,S) := e`). This border
edge does however not exist iff `(S == T)`.

Due to the above, no other class of subtrees can be defined such that the
relationship between a super-tree and one of its subtrees can be uniquely
determined. That is, because in any other case, the additional edges in the
border graphs break the above unique relationship. The focus of the overall
discussion is therefore on subtrees that are induced by their root node.

<!-- ======================================================================= -->
## example

Given the following two trees, ...

```
super-tree T      sub-tree S
=============     ==========
1 -> 2 -|-> 3     2 -|-> 3
        |-> 4        |-> 4
```

* T: `V(T) := {1,2,3,4}` and `E(G) := {(1,2),(2,3),(2,4)}`
* S: `V(S) := {2,3,4}` and `E(S) := {(2,3),(2,4)}`
* i.e. `(S == T[2])`

... the border graphs between the two are as follows:

```
 |= T ===================|
 |        |= S ========| |
 | |= OBG ====|        | |
 | | 1 -> | 2 | -|-> 3 | |
 | |==========|  |-> 4 | |
 |        |============| |
 |=======================|
```

* `(IBG == Ø)`, `(OBGo == Ø)` and `(OBGi == ({1,2}, {(1,2)}) )`
* i.e. `(BE(T,S) == (1,2))`

Note that `(T supertree-of S)` because `(e in OBGi)` is oriented from a node
in `T` towards the root of `S`. That is, because `e` still has the parent-of
semantics (i.e. `(1 parent-of 2)`) and is therefore oriented from a super-
ordinate node towards a sub-ordinate node. The relationship between `T` and
`S` therefore corresponds with the relationship between both nodes. That is,
`T` is super-ordinate to `S`.
