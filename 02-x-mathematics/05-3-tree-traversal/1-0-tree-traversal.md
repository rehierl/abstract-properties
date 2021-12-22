
<!-- ======================================================================= -->
# tree traversal, document traversal

In order to process the nodes in a node tree, implementations must visit each
node in it one after another. The following will therefore introduce the main
traversal algorithms that can be used.

Since a document tree can in general be described as an ordered tree that has
a child order associated with it, the traversal of a document tree is in general
required to visit each node while repsecting the tree's tree order and also the
tree's child order. That is because each node in such a tree can be understood
to define properties whose scopes are in regards to the suborders embedded into
it.

Note that only the default level-order (BFS) and only the default pre-order
(DFS) tree traversal algorithms are **order preserving**.

<!-- ======================================================================= -->
## classification of algorithms

In general, the traversal of a tree can be classified depending on the order
in which the nodes in a tree are visited. Even though there are variations
possible, the following main categories can be distinguished:

(1) Traversal algorithms can be distinguished in regards to when a node is
visited in relation to its child nodes. In that regards, there are two main
types of traversal algorithms:

(1.1) The siblings of a node will be visited before any of its descendants.
Because of that, this type of traversal is in general referred to as
**a breadth-first search (BFS)**.

(1.2) The descendants of a node will be visited before any further sibling
of that node will be visited. Because of that, this type of traversal is in
general referred to as **a depth-first search (DFS)**.

(2) Traversal algorithms can also be distinguished in regards to the order
in which its child nodes will be visited. In that regards, there are two
main types of traversal algorithms:

(2.1) The child nodes of a parent will be visited in **left-to-right (LTR)**
order, which can also be described as in **first-to-last (FTL)** order.

(2.2) The child nodes of a parent will be visited **in reverse**. That is,
they will be visited in **right-to-left (RTL)** order, which can also be
described as in **last-to-first (LTF)** order.

<!-- ======================================================================= -->
## visiting a node

The description of **visiting a node**, in the context of this discussion,
must be understood to correspond with a point in time that is used to process
a particular node. This processing step must however be performed in such a
way, that no operation executed while traversing a tree may end up producing
conflicting result. Because of that, the **visit order** must correspond with
the node order of the document tree, which is why a document tree must be
traversed in an order-preserving fashion.

In addition to that, one must keep in mind that no node is being visited,
while another node is still in the process of being visited. As such, and
in regards to the visit of every other node, "visiting a node" must be
understood as **an atomic operation**.

Note that, in the context of this discussion, the traversal of a tree will
visit each node within a tree once and only once. Such a tree traversal can
in general be described as **a strict tree traversal**. In contrary to that,
variations are possible (e.g. in-order tree traversals) in which nodes will
be visited serveral times. These non-strict traversal algorithms are however
not in the focus of this discussion.

<!-- ======================================================================= -->
## child order

Even though the focus in the context of this discussion is on document trees,
the traversal algorithms introduced in this chapter can be understood to also
cover node trees that have an implicit/temporary child order associated with
them. After all, any tree can be understood to be associated with a child
order, even if that child order can be discarded afterwards. Because of that,
the following for-loops must be understood as described below.

```js
for (child in parent.childNodes) begin
  //- do something
end
```

This for-loop provides the child nodes of a parent in random order (see below),
if no particular child order is present. However, if such a child order is
available, then the child nodes are provided **in (first-to-last) order**.

Note that alternative property names may be used for purposes of
clarification - e.g. `.childNodesFTL`.

```js
for (child in parent.childNodesRev) begin
  //- do something
end
```

This for-loop provides the child nodes of a parent in random order (see below),
if no particular child order is present. However, if such a child order is
available, then the child nodes will be provided **in last-to-first order**.
Because of that, a tree traversal that uses the reversed child order may be
described as a "**X (reversed/rev)**", where "X" stands for the name of the
default variant (e.g. "a reversed pre-order traversal").

Note that alternative property names may be used for purposes of
clarification - e.g. `.childNodesLTF`.

```js
for (child in parent.childNodesRnd) begin
  //- do something
end
```

Note that even a random iteration over the child nodes is understood to provide
each child once only. Because of that, this for-loop must be understood such
that the child nodes are provided **in random order**, even if an actual child
order would be present. Consequently, this for-loop must be understood to denote
that the child nodes are provided in some temporary order such that repeated
iterations will yield different results.

Note that such a random visit order takes additional effort to implement. That
is because child nodes are most often maintained as lists of nodes, which can
easily be traversed in a first-to-last, or in a last-to-first order. Hence,
an implementation would have to ensure that subsequent iterations will yield
different results while also ensuring that each node will be visited once and
once only.

Note that, since a random visit order takes additional effor to implement, one
will usually visit the child nodes from first-to-last, or from last-to-first,
even if no particular order would be required.
