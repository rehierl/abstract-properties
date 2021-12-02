
<!-- ======================================================================= -->
# setups of trees

As before with simple sets of elements, and with tree-based definitions in mind,
setups of trees can be defined as follows.

<!-- ======================================================================= -->
## (simple) setups of trees

A set of trees will be referred to as **a (simple) setup of trees** `S`,
if the following requirements are met.

* (R0) `S` is a set/family of trees.
* (R1) `S` is expected to be non-empty.
* (R2) `S` is **well formed**.

Note that there is no explicit requirement that the trees in `S` must be
non-empty. That is because each tree is required to have at least a root,
which is why such a requirement is not needed.

Note that, similiar to the universal set of elements `U` in the context of
a setup of sets, a setup of trees can be understood to be associated with
a graph that can be described as the union of all the trees in `S`. Note
however that in the context of a setup of trees, `U` is not necessarily a
tree - i.e. a possibly empty non-tree graph.

Note that, analogous to the powerset `P(U)` over a simple set of elements,
the expression `P(U)` in the context of a setup of trees can be understood
as the set of all possible subtrees of `U`.

Note that the **well formedness** requirement (R2) is intended to ensure that
any two trees in a setup of trees are either disjoint, related (i.e. one is a
subtree of the other) ex-or overlap each other (i.e. **DI-RE-OV**). Based on
that, all trees are required to represent node orders that do not contradict
each other - e.g. the ancestor of a node in a tree is no descendant of that
node in another tree.

* the intersection between any two trees must be empty or a tree
* the union of two trees must be a forest or a tree

Note that, in the case of overlapping trees, the root of one tree must be a
node in the other tree. That is because the union of both trees might otherwise
not be a tree.

Note that the well formedness requirement (R2) has the effect of turning the
relationship between the nodes of a tree into a secondary characterisitc. After
all, if all trees must share the same order between the nodes they contain, the
relationship between the nodes is overall less significant. Because of that,
the focus shifts towards the sets of nodes and the relationships between them.
That is, a setup of trees essentially acts as a setup of sets.

Note that such a requirement is not needed in the context of setups of simple
sets. That is because simple sets have no inner order associated with them.
Two sets in a setup can therefore not be in conflict with each other since no
such order does exist. (Note that this description is not overly accurate since
the inner order of simple sets is total - see simple sets).

<!-- ======================================================================= -->
## a partial setup of trees

Assuming the **supertree-of** operator as the basis of the related-to operator,
a set of trees `S` may be referred to as **a partial setup (of trees)**, if the
following requirements are met.

* (R0) `S` is a simple setup of trees.
* (R1) Any two trees in `S` are either disjoint ex-or related.

Note that, due to requirement R1, no tree in such a setup may overlap another
tree - i.e. the default **DI-RE** case.

Note that, provided a setup is a partial setup, in order to determine if two
trees are related with each other, one only needs to determine if both trees
have **one node in common**. Consequently, and in order to determine the
orientation between two related trees, one only needs to compare the number
of nodes in each tree.

* if `(#s < #t)`, then `t` is the super-tree
* if `(#s == #t)`, then both trees are equal
* if `(#s > #t)`, then `s` is the super-tree
* `#s` denotes the number of nodes in tree `s`

Note that the **intersection** between two trees in a partial setup is either
the empty graph ex-or equal to one of the trees. In the latter case, the
intersection is equal to the smaller tree (less significant). Likewise, the
**union** of two trees in a partial setup is either a forest ex-or one of
the trees. In the latter case, the union is equal to the larger tree (more
significant).

* if `(s,t in S)` and `(#s < #t)`, then ...
* `((s & t) == s)` and `((s + t) == t)` are both true

Note that, in contrary to a partial setup of sets, a subtree can be understood
to support "a notion of placement". That is, a subtree's root can be said to
have a placement in regards to the root of its supertree. However, thus far
there is no requirement in regards to the placement of a subtree. That is, a
subtree may or may not have the supertree's root as its own root. Likewise, a
subtree may or may not contain one or more leaf nodes of its supertree.

<!-- ======================================================================= -->
## definitions of hierarchy-based terms

Note that, similar to a partial setup of sets, hierarchy-based terms can be
defined. The most notable definitions are as follows.

A **root tree** is such that it is **no subtree** to another tree. As such, a
root tree may or may not have a subtree in `S`. That is, a root tree may or may
not be a source tree to another tree.

A **rooted setup** is such that it has one and only root tree. That is, the set
of root trees `RT(S)` of `S` consists of one tree only - i.e. `(#RT == 1)`.

Note that, since the union of two trees must either be a forest or a tree,
the union graph `U` of a rooted setup of trees is a tree and as such equal
to the setup's root tree.

An **ancestor tree** `a` is a supertree to another tree.
Likewise, a **descendant tree** `d` is a subtree to another tree.

* `A(t) := { a | (a ancestor-of t) }`
* `D(t) := { d | (d descendant-of t) }`

Note that a partial setup has **no cycles**. That is because no tree can be
a subtree and also a supertree to another tree. Because of that, the sets of
ancestor and descendant trees are disjoint.

* `(A(t) disjoint-to D(t))` is true

The **root tree** `r(t)` of tree `(t in S)` is the most significant ancestor
of `t`. The **parent tree** `p(t)` of tree `t` is the least significant ancestor
of `t`. (Recall that "most significant" and "least significant" is in regards
to the amount of nodes in the corresponding trees).

A descendant tree `(c in D(p))` is **a child tree of** `p`, if `p` is the
parent tree of `c`. (Note that, in a partial setup, a tree may have any number
of disjoint child trees).

* `c(p) := { c | (p(c) == p) for (c in D(p)) }`

Two trees `(s,t in S)` may be described as **sibling trees**, if both trees
have the same parent tree. (Note that, like sibling sets, sibling trees are
disjoint from one another. Also, there is no child order over sibling trees).

* `(s sibling-of t) := (p parent-of s) and (p parent-of t)`
* `(s sibling-of t) <-> (A(s) == A(t))`

Note that, similar to setups of sets, `A(t)` in the context of a partial setup
of trees is always a total subsetup of trees. As such, each partial setup of
trees can be described as being **downward-total**.

<!-- ======================================================================= -->
## a total setup of trees

A set of trees `S` will be referred to as **a total setup (of trees)**, if the
following requirements are met.

* (R0) `S` is a partial setup of trees.
* (R1) Any two trees in `S` are related with each other.

Note that a total setup does not allow pairs of disjoint trees (R1), and also
no pairs of overlapping trees (R0) - i.e. the **RE only** case.

Note that in a total setup any parent tree has **one and only one child tree**.
Consequently, a total setup is **downward- and upward-total**. Any non-empty
total setup therefore has **one root and one leaf tree only**.

Note that the root tree of `A(t)` is the root tree of `t`,
and that the leaf tree of `A(t)` is the parent of `t`.