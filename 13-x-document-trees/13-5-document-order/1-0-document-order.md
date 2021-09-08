
<!-- ======================================================================= -->
# the document order

Recall that the document order of a document is understood as a total order
over the nodes in it. In addition to that, the content of a document tree
is serialized into a document using a tag-based syntax, which is generated
using the following base algorithm.

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

When trying to parse the tag-based syntax (aka. **tag soup**) of a document,
questions arise about the exact meaning of a start-tag and an end-tag. That
is because both can be understood to represent events of some kind:

* (1) a **start-tag** can be said to trigger an **enter-event**
* (2) an **end-tag** can be said to trigger an **exit-event**

Based on that, the process of parsing a document can be described as an
event-driven process.

Note that start-tags can be said to represent an **enter-order** (i.e. a
sequence of enter events) and the end-tags an **exit-order** (i.e. a sequence
of exit events). Based on that, the tag-based syntax can be understood to
support **a stream-based point of view**.

Since an implementation must be able to determine whether or not a given node
is located within the scope of a property, a clear understanding of the meaning
of the start-tags and the end-tags is critical. After all, how is one to tell
the context of a node, if one can not pinpoint its exact location?

Note that, as a matter of simplification, subsequent discussions will assume
that any node and its scope can be expressed in terms of a pair of tags. Based
on that, any document can be understood to consist of start-tags and end-tags
only and can therefore be described as a pure sequence of tags.

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

As was shown in the discussion of the pre-order tree traversal algorithm,
the pree-order traversal can be used to form a trace of nodes, if each node
is appended to a sequence of nodes while being visited. Formed this way, the
resulting trace of nodes is an ordered sequence of nodes and as such can be
understood to define **the total pre-order node order**.

Note that no node will be visited while another node is still in the process
of being visted. Because of that, **the visit of a node** must be understood
as **an indivisible atomic operation**.

Since the enter-order of a document traversal coincides with the pre-order
visit-order, one can state that **the visit-order** of a pre-order document
traversal is equivalent to the the enter-order of a document traversal.
Because of that, a node can be said to be visited during the corresponding
enter-event only.

Note that, if a the tag soup of a document is broken apart into a sequence
of tags, and if all end-tags are dropped, then the resulting sequence of
start-tags is equivalent to the pre-order trace of the document tree. That
is because each node can be understood to be pushed into its start-tag, which
is why **a start-tag corresponds with the visit of a node** and can thus be
understood to define the absolute position of a node. In addition to that,
**a start-tag also denotes the start of the node's scope**.

* start-tag <=> visit the node and enter its scope

Note that, in contrary to the above, the subsequence of all end-tags reflects
**the exit-order**. That is, an end-tag does not correspond with the visit of
any node. Consequently, **an end-tag only marks the end of a scope**.

* end-tag <=> only exit the node's scope

<!-- ======================================================================= -->
## the doc-order is a total pre-order

Recall that the pre-order and the level-order tree traversal algorithms are the
only **order preserving** tree traversal algorithms. That is, both algorithms
visit the nodes in tree order and also in child order.

However, since the level-order trace of a tree can be described as a sequence
of disjoint child orders, and is as such non-hierarchical, one can conclude
that the document order is not in level order.

Despite the fact that the only order-preserving tree traversal algorithm left
is the pre-order tree traversal, one can point out that the pre-order trace
of a tree is a hierarchical ordered sequence of nodes. That is because
**the scope of each node is a substring** to the pre-order trace. Furthermore,
due to the order-preserving nature of the pre-order trace, the hierarchy of
scopes embedded into it is such that two scopes are either disjoint exor
related (**DI-RE**). Apart from that, a pre-order trace can be described as a
sequence of interleaved child orders.

**The tag soup of a document is in pre-order.**

And there is not even the slightest shred of doubt about that!
