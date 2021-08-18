
<!-- ======================================================================= -->
# trees in (axiomatic) set theory (AST)

A tree `T` in AST is a poset `P(T,<)` such that for each `(t in T)` the set
`ht(t,T)` is well-ordered. Frequently, such trees are required to have one
minimal element only (i.e. a least element, a root).

* `ht(t,T) := { (s in T) | (s < t) }`

Recall that a well-ordered set is a total set such that each subset has a least
element. With that in mind, `ht(t,T)` can be understood to correspond with the
rooted path of `t`, or more accurately with the rooted path of its parent.

* `ht(t,T) <=> ( E(rp(t)) \ {t} )`

Note that `ht()` decreases in size towards the root element. Because of that,
a family of scopes can be considered in some sense "similar" but "inverse" to
this set-based definition. That is because the scopes increase in size the
closer one gets to the root.

Note that `ht()` seems more intuitive to mathematicians. After all, the
absolute value of a number (and thus its level of significance) increases
with the distance from zero. In that regards `ht()` can be considered order
preserving.

Note that a family of scopes can be considered order reversing in that regards.
However, since a root node in a node tree can be considered most significant to
such a tree, the number of elements in the scope of a root can be understood to
reflect that level of significance. That is, a family of scopes is in that
regards order preserving.

<!-- ======================================================================= -->
## analogous definitions

There are specific definitions for this particular set-based context which have
a graph-based counterpart. These set-based definitions are however non-relevant
to this discussion. The following will therefore only mention a few in order to
give a general impression.

The **height** of an element `t` in a tree `T` is defined as the **order type**
of `ht(t,T)`. That is, the height of `t` is defined as the number of elements
that are less than `t`. Because of that, the height of a root `(r in T)` is 0.

Note that this definition is "inverse" to the height of a node in a node tree.
That is because the height of a node in such a tree is defined as the length
of the longest downlard path to a leaf. However, the above set-based definition
corresponds with the depth of a node. That is because the depth of a node is
the length of its rooted path minus one (alternatively, the edge-length of its
rooted path).

* `height(t,T) := ord( ht(t,T) )` for `P(T,<)`
* `depth(n,T) := #rp(n,T)` for `T(N,E)`

A **branch** of a tree is a maximal chain (a total suborder) in the tree,
and its **length** is the ordinal that is order-isomorphic to the branch.

Note that the construct of a branch corresponds with that of a rooted path
in a node tree.
