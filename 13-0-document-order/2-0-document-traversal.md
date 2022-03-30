
<!-- ======================================================================= -->
# the document tree traversal

```js
//- the basic document tree traversal
traverseInDocOrder(node) {
  //- visit the node and enter its scope
  //- e.g. write("<%s %s>", name, attributes)
  onEnter(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- exit the node's scope
  //- e.g. write("</%s>", name)
  onExit(node);
}
```

A document tree traversal is for example used to serialize a document tree into
a tag soup. As can be seen, this serialization is done based on a combination
of the pre-order and the post-order tree traversal algorithms, which will be
referred to as **the document tree traversal algorithm**.

<!-- ======================================================================= -->
## about the semantics of start- and end-tags

When trying to parse the tag soup of a document, questions arise about the
semantics of start- and end-tags. That is because, while parsing a tag soup,
both kinds of tags can be understood to trigger events with regards to the
scopes of the corresponding scopes. Based on that point of view, the process
of parsing a document can be described as **an event-driven process**.

* (1) a **start-tag** can be said to trigger an **enter-event**
* (2) an **end-tag** can be said to trigger an **exit-event**

Note that all the start-tags combined can be said to represent an **enter-order**
(i.e. a sequence of enter events) and all the end-tags an **exit-order** (i.e.
a sequence of exit events). Combined, the tag soup of a document can be
understood to define a sequence of enter- and exit events.

```
        |-s(n)------------------------------------------------------->|
    .., | <n attribute*>, <fc>, .., </fc>, .., <lc>, .., </lc>,  </n> |, ..
enter ->|-ce(n)---------|-iss(n)------------------------------|-empty-|-> exit
 open ->|-a-substream-of-nodes--------------------------------------->|-> close
```

Note that, since each enter-event is paired with a subsequent exit-event, the
tag-based syntax can be understood to support **a stream-based point of view**.
Hence, each pair of tags can be said to denote a sub-stream of nodes.

<!-- ======================================================================= -->
## the (pre-order) visit of a node

As was shown in the discussion of the pre-order tree traversal in chapter 05,
the pre-order tree traversal of a document tree can be used to form a trace
of nodes, if each node is appended to a sequence while it is in the process
of being visited. Formed this way, the resulting trace is an ordered sequence
of nodes and as such can be understood to represent the document tree's
**pre-order node order**.

Note that **the (pre-order) visit of a node** must be understood as a slice
of processing time that is used during the pre-order traversal of a tree to
**process** some of the node's data. That is, the description is used to refer
to a group of actions that are in regards to a particular node - e.g. write
the node's start-tag. In contrary to that, the post-order visit of a node is
used to process a node in post-order - e.g. write the node's end-tag - i.e.
a different group of actions.

Note that each node is understood to be visited once only. Furthermore, no
node will be visited while another node is still in the process of being
visted. Because of that, the visit of a node must be understood as
**an indivisible atomic operation**.

```js
//- the default pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the node and enter its scope
  //- e.g. add to the pre-order trace
  //- e.g. write("<%s %s>", name, attributes)
  visitInPreOrder(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInPreOrder(child);
  }

  //- exit the node's scope
  //- e.g. add to the post-order trace
  //- e.g. write("</%s>", name)
  visitInPostOrder(node);
}
```

Since **the pre-order enter-order** corresponds with the (pre-order) visit of
a node, one can conclude that the pre-order visit-order also corresponds with
**the document tree's pre-order trace** of nodes.

Note that, if the tag soup of a document is broken apart into a sequence of
tags, and if all the end-tags are dropped, then the resulting sequence of
start-tags corresponds with the pre-order trace of a document tree.

Note that **the post-order visit-order** of the nodes in a document tree
corresponds with the document tree's **exit-order**. That is, the pre-order
exit-order and also the post-order exit-order.

However, one needs to be aware that the enter- and the visit-event of a node
are still not identical. After all, one marks the beginning of the node's
scope, while the other marks when that node is being processed.
