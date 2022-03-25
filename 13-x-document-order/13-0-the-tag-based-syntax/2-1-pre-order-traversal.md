
<!-- ======================================================================= -->
# the pre-order tree traversal

As was shown in the discussion of the pre-order tree traversal (see - chapter
05-3), the pre-order tree traversal of a document tree can be used to form
a trace of nodes, if each node is appended to a sequence while it is being
visited. Formed this way, the resulting trace of nodes is an ordered sequence
of nodes and as such can be understood to represent the document tree's
**total pre-order node order**.

Note that each node will be visted once, and once only. Furthermore, no node
will be visited while another node is still in the process of being visted.
Because of that, **the visit of a node** must be understood as
**an indivisible atomic operation**.

```js
//- the default pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  visit(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInPreOrder(child);
  }

  //- exit the node's scope
  //- write("</%s>", name)
}
```

Since the enter-order of a pre-order tree traversal coincides with
**the (pre-order) visit of a node**, one can conclude that the pre-order
visit-order of a document tree corresponds with the **enter-order** of
a pre-order tree traversal. After all, each node can be understood to
be pushed into its start-tag.

Note that, in contrary to the above, **the post-order visit of a node**
corresponds with the document tree's **exit-order**.

However, one needs to be aware that the enter- and the visit-event of a node
are still not identical. That is because one marks the beginning of a scope,
while the other marks when a node is being **processed**.

Note that, if the tag soup of a document is broken apart into a sequence of
tags, and if all the end-tags are dropped, then the resulting sequence of
start-tags corresponds with the pre-order trace of a document tree.

Since each node can be understood to be pushed into its start-tag, a start-tag
can be said to correspond with the visit of a node. The start-tag of a node
can therefore be understood such that it **defines the absolute position**
of a node and therefore to **denote the start of the node's scope**.

* start-tag => enter the scope of a node and visit that node

Note that, since each start-tag can be understood to correspond with a
node in the document tree that has a unique position associated with it,
a document tree can be described as **an ordered tree** in the sense of
**a tree of unique/distinct elements** which is associated with a tree order.
That is, the description of "an ordered treee" should be understood in the
sense of "an ordered sequence of distinct elements", not in the sense that
it has a child order!

Note that, in contrary to the above, the subsequence of all end-tags reflects
**the exit-order**. That is, an end-tag does not correspond with the visit
of any node since **an end-tag only marks the end of a scope**.

* end-tag => only exit the node's scope
