
<!-- ======================================================================= -->
## a forest of trees

A forest (of trees) `F := (N,E)` is a union of pairwise disjoint trees:

* `N` is the possibly empty set of nodes
* `(E subset-of N×N)` is the possibly empty set of edges
* `N` may contain any number of root nodes
* each component in `F` is a tree

An alternative definition could be: A forest (of trees) is a graph such that
each (maximal) connected component in it is a tree (as defined above).

<!-- ======================================================================= -->
## siblings

* `x` is a child of `p`, if `pEx` is true
* `x` is a sibling of `y`, if `(pEx and pEy)` is true
* note - siblings have the same parent node
* `(x sibling-of y) := (p(x) == p(y))`

The following function `(s: N -> P(N))` can be defined:

* `s(n) := { (s in N) | pEs for (p in N), pEn, (s != n) }`
* `s(n)` returns the set of all silbings of node `n`
* alternatively - `s(n) := (c(p) \ {n})` where `pEn`

Note that, there is no edge `xEy` and no edge `yEx` if `(x sibling-of y)` true.
Also, the sibling-of operator has no orientation. Because of that, siblings can
be considered to be of equal significance.

<!-- ======================================================================= -->
## semantics of a tree T

Each edge `(e in E)` in a tree `T := (N,E)` is defined to connect a parent node
(source) with a child node (sink). Because of that, the semantics of each edge
within a tree `sem(e)` is the `parent-of` semantics. And since these semantics
apply to every edge within a tree (i.e. homogenous semantics), the semantics of
a tree `sem(T)` is the `parent-of` semantics.

* `sem(e) := (p parent-of c)` - i.e. `p` is a parent of `c`
* for any `e := (p,c)` such that `(e in E)`
* `(E subset-of PN×CN)` and `(PN×CN subset-of N×N)`

In contrary to that ..

* `sem(e) := (c child-of p)` - i.e. `c` is a child of `p`
* `pEc <-> (p parent-of c) <-> (c child-of p)`

Note that any edge in a tree is oriented from a super-ordinate entity (a parent)
downwards to a sub-ordinate entity (a child). Because of that, the `parent-of`
semantics is therefore **consistently oriented** with the orientation of each
edge. In contrary to that, the `child-of` semantics is oriented from a
sub-ordinate entity (a child) upwards to a super-ordinate entity (a parent).
As such, the child-of semantics is **converse** to the parent-of semantics.

<!-- ======================================================================= -->
## semantics of a converse T°

If all the edges in a tree `T` are inverted, i.e. if one forms the converse `T°`,
then the child-of semantics is consistently oriented with the resulting edges.

* for `T° := (N,E) := conv(T)`
* `sem(e) := (c child-of p)` - i.e. `c` is a child of `p`
* for any `e := (c,p)` such that `(e in E)`

Note however, that the resulting graph is in general no longer a tree. That is
because more than one (former) child node may have the same (former) parent
node. As such, and because a (former) parent node may then have more than one
incoming edge, the converse graph of a tree will in general not satisfy the
requirements of a tree. That is because each (former) parent will then act as
a child node in the converse graph.

Note that the endo-relation of a tree is not right-unique (more than one child).
Because of that, the relation of a tree is not functional. In contrary to that,
the converse graph of a tree is right-unique (one parent only). However, the
converse relation is not left-unique (more than one child - not injective),
not left-total (the root is no child) and not right-total (leaf nodes have
no child - not surjective).
