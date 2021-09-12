
<!-- ======================================================================= -->
# The removal of a node (3)

Ex-1 shows the element-based removal in regards to ordered sequences, and
Ex-2 the suffix-based removal in regards to unordered trees. In addition
to that, the suffix-based removal is applied to ordered sequences in Ex-3,
and the element-based removal to unordered trees in Ex-4.

Even though an ordered tree is just another unordered tree, Ex-5 displays
the effect of a suffix-based removal from an ordered tree. That is, after a
suffix-based removal from an ordered tree, the ordered tree remains such that
each node has no more than two child nodes. As such, the pre-order rule (i.e.
`n -> (c × s)`) remains applicable.

In contrary to that, Ex-6 shows that after an element-based removal from an
ordered tree, the parent node of the removed node may have up to three child
nodes. As such, the pre-order rule can not be applied since it is defined for
no more than two node sequences. One would therefore have to further modify
the node order of the resulting tree after the removal in order to still be
able to traverse the tree in pre-order.

There is however a special case in which node `n` does not have a former first
child `c(n)` (i.e. `n` is a leaf in `UT`) but possibly a former next sibling
`s(n)`. This case is of particular interest since, it guarantees that each
node in the resulting tree remains to have no more than two child nodes.

Note that this seems to suggest that a hidden attribute *must* at least apply
to a node and all of its descendants in `UT`. That is because it effectively
guarantees to maintain the general characteristic of an ordered tree.

<!-- ======================================================================= -->
## (Ex-7) a removal from an ordered tree: keep s(n)

In this particular case, the child sequence `c(n)` is assumed to be removed
with node `n`. That is, one effectively holds on to the sequence of former
subsequent siblings `s(n)`. As such, this removal effectively corresponds
with a "some, but not all" qualifier.

```
S               =>                        => S*
============================================================
( p -|-> s(p) ) => ( p -|-> s(p)        ) => ( p -|-> s(p) )
     |-> c(p)           |-> n -|-> s(n)           |-> s(n)
                               |-> c(n)
```

If node `n` is the first child of its parent `p` in `UT`, then the sequence
of former child nodes `c(p)` can be understood to be replaced by the general
pattern of a node in an ordered tree. And since `c(n)` is to be removed along
with node `n`, this removal operation effectively replaces `c(p)` with `s(n)`.

```
S                 =>                         => S*
=================================================================
( ps -|-> s(ps) ) => ( ps -|-> n -|-> s(n) ) => ( ps -|-> s(n)  )
      |-> c(ps)            |      |-> c(n)            |-> c(ps)
                           |-> c(ps)
```

If node `n` is however a former non-first child of its parent `p` in `UT`,
then `n` has its former presequent sibling `ps` as its parent in `OT`. And
since the sequence of former child nodes `c(n)` is removed along with node
`n`, the removal operation effectively replaces `s(ps)` by `s(n)`.

In general, the element-based removal in Ex-6 can be said to be extended to
also remove `c(n)`. Likewise, the suffix-based removal in Ex-5 can be said to
be restricted to `n` and `c(n)` (i.e. keep `s(n)`). Since in this case `c(n)`
will no longer exist after the removal, it can not invalidate the pre-order
rule. Because of that, we would like to be able to define to also drop `c(n)`
while still holding on to `s(n)`.

If only it were not for the following issue: From a strict point of view, an
ordered tree is an un-ordered tree. Because of that, one can in general not
distinguish between `s(n)` and `c(n)`. We therefore need further information
that can be used to distinguish one sub-sequence from another.

<!-- ======================================================================= -->
## (Ex-8) a removal from an ordered tree: keep c(n) instead

In theory, one could drop `s(n)` instead and hold on to `c(n)`. However, since
the focus of this discussion is on the pre-order traversal of an ordered tree,
this case will not be taken into further consideration. That is because it
seems to require even more changes (e.g. a different type of traversal, i.e.
level-order?).

```
S               =>                        => S*
============================================================
( p -|-> s(p) ) => ( p -|-> s(p)        ) => ( p -|-> s(p) )
     |-> c(p)           |-> n -|-> s(n)           |-> c(n)
                               |-> c(n)
```

* `p` will have `c(n)` as its new sequence of former child nodes

```
S                 =>                         => S*
=================================================================
( ps -|-> s(ps) ) => ( ps -|-> n -|-> s(n) ) => ( ps -|-> c(n)  )
      |-> c(ps)            |      |-> c(n)            |-> c(ps)
                           |-> c(ps)
```

* can `c(n)` act as a sequence of subsequent siblings to `ps`?
* that is quite odd ...

<!-- ======================================================================= -->
## we don't implement trees, we implement non-tree graphs

Since we implement trees as ordered sequences of child nodes that are embedded
into parent nodes, we neither implement trees as unordered nor as ordered trees.

```
common practice             ordered trees             unordered trees
=======================     =====================     =============
Node {                      Node {                    Node {
  Object item;                Object item;              Object item;
  Node parentNode;            Node parentNode;          Node parentNode;
  Node firstChild;            Node childNodes{2};       Node childNodes{*};
  Node lastChild;           }                         }
  Node nextSibling;
  Node previousSibling;
  Node childNodes[*];
}
```

We don't strictly implement trees as unordered trees since we can traverse
from one sibling to another (e.g. `.nextSibling` and `.previousSibling`),
while ignoring that these nodes are incomparable in an unordered tree. That
is, the formal definition of an unordered tree does not have these edges.

Likewise, we don't implement trees as ordered trees since we can traverse
from one node to its parent in the unordered tree (e.g. `.parentNode` and
`.lastChild`), while ignoring that there is in general (i.e. except for
the former first child of a parent) no such edge that connects these nodes
in an ordered tree.

And since it is common practice to add such shortcut properties, each of
which represents a simple edge, we neither implement unordered nor ordered
trees. After all, each node can in general be said to have more than one
incoming edge and can therefore in general be understood to have more than
one parent (i.e. in conflict with the requirements of a node tree).

Based on the above, we implement non-tree graphs instead.

Note that, if one ignores the orientation of the properties (i.e. `.parentNode`
in particular, i.e. treat as an undirected graph), then the trees we intend
to implement are subtrees to the non-tree graphs we do implement. That is,
the objects we implement embed an ordered tree and its unordered tree, both
of which can be understood to be subgraphs to the graphs we do implement.

<!-- ======================================================================= -->
## (Ex-7) a removal from an ordered tree, keep s(n), continued ...

```
general pattern     S* (case-1)         S* (case-2)      
===============     ===============     =================
  n -|-> s(n)       ( p -|-> s(p) )     ( ps -|-> s(n)  ) 
     |-> c(n)            |-> s(n)             |-> c(ps)
```

Since each node object holds a reference to its first child (i.e. `.firstChild`
, i.e. `c(n)`) and also a reference to its next sibling (i.e. `.nextSibling`,
i.e. `s(n)`), both of which are in regards to `UT`, we can distinguish between
both child nodes in `OT` and therefore restrict the removal of a node in an
ordered tree to a node and its descendants in the unordered tree.

Note that this type of removal could be referred to as a type-1 removal of a
node from an ordered tree.

<!-- ======================================================================= -->
## remarks

The additional information provided by the above shortcut properties allows to
derive a generic definition of a "some, but not all" qualifier. That is because
the set of descendants of a node in an ordered tree can be said to be formed
as the union of two disjoint subsets of nodes. One is defined by the sequence
of former subsequent siblings `s(n)` and the other by the sequence of former
child nodes `c(n)`. Because of that, the "some, but not all" qualifier can be
understood as being defined as "include all the nodes in one branch, but none
of the nodes in the other".

Note that it is inherently difficult to implement simple sets of elements. That
is because there always is an order of sorts based upon the in-memory address
of an object (i.e. object references refer to distinct units in memory, each
of which has a unique address) and/or based upon the order of creation (i.e.
in the context of a single document tree, we commonly create one object after
another in a particular order).
