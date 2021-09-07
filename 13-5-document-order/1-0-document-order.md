
<!-- ======================================================================= -->
# the document order

Recall that the document order of a document tree is understood as a total
order over all the nodes in it. In addition to that, the contents of a
document tree are serialized into a document using a tag-based syntax which
is generated using the following base algorithm.

```
//- the basic document tree traversal
traverseInDocOrder(node) begin
  //- used to write start-tags
  //- write("<%s %s>", name, attributes)
  onEnter(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInDocOrder(child)
  end

  //- used to write end-tags
  //- write("</%s>", name)
  onExit(node)
end
```

When trying to parse this tag-based syntax (aka. **tag soup**), questions
arise about the exact meaning of a start- and an end-tag. That is because
both can be understood to represent events of some kind:

* (1) a **start-tag** can be said to represent an **enter-**, and
* (2) an **end-tag** can be said to represent an **exit-event**.

Based on that, parsing a tag soup can be described as an event-driven process.

Note that start-tags can be described as being in **enter-order** and the
end-tags as being in **exit-order**. In addition to that, the above tag-based
syntax can be said to support **a stream-based point of view**.

Since an implementation must be able to determine whether or not a given node
is located within the scope of a certain property, a clear understanding of
the meaning of these start- and end-tags is paramount. After all, how is one
to tell the association of a node, if one can not tell where exactly a node
is located within a document?

<!-- ======================================================================= -->
## the pre-order tree traversal

```
//- the default pre-order tree traversal
traverseInPreOrder(node) begin
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  visit(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end

  //- exit the node's scope - not a visit
  //- write("</%s>", name)
end
```

As was shown in the discussion of the pre-order tree traversal algorithm, the
pree-order tree traversal can be used to form a trace of nodes, if the current
node is appended to a sequence of nodes while it is being visited. Formed this
way, the resulting trace of nodes is an ordered sequence of nodes and as such
can be said to represent **the total pre-order node order**.

Note that no node will be visited while another node is still in the
process of being visted. In that regards, **the visit of a node** is
**an indivisible atomic operation**.

Since the enter-event of a document traversal corresponds with the pre-order
visit-event, one can state that **the pre-order visit-order** and therefore
also **the pre-order node order** is equivalent to **the enter-order** of a
document. A node is therefore being visited only during that enter event.

Note that, if a tag soup is broken apart into a sequence of tags, and if all
end-tags are removed from it, then the resulting sequence of all start-tags
is equivalent to the pre-order trace of the document tree. That is because
each node can be understood to be pushed into its start-tag, which is why the
visit of a node **corresponds with its start-tag**.

Note that, in addition to denoting the absolute position of a node,
a start-tag **also denotes the start of the node's scope**.

Note that, in contrary to the above, the subsequence of all end-tags reflects
**the exit-order**. That is, an end-tag does not correspond with the visit of
any node. Consequently, **an end-tag marks nothing but the end of a scope**.

* start-tag <=> visit the node and enter its scope
* end-tag <=> only exit the node's scope

<!-- ======================================================================= -->
## the doc-order is a pre-order

Recall that, the pre-order and the level-order tree traversals are the only
**order preserving** tree traversal algorithms. That is both algorithms visit
the nodes in tree order and also in child order.

However, since the level-order trace of a tree can be described as a sequence
of disjoint child orders, one can conclude that the document order is no level
order. That is because a level-order trace is non-hierarchical.

Despite the fact that the only order-preserving tree traversal algorithm left
is the pre-order tree traversal, one can point out that the pre-order trace
of a tree is a hierarchical ordered sequence of nodes. That is because
**the scope of each node is a substring** to the pre-order trace. Furthermore,
due to the order-preserving nature of the level-order traversal, such scopes
remain to be disjoint exor related. In addition to that, the pre-order trace
can be described as a sequence of interleaved child orders.

**The tag soup of a document is in pre-order.**

And there is not even the slightest shred of doubt about that!
