
<!-- ======================================================================= -->
# the document traversal

Recall that the document order is a total order over the nodes in a document
tree. In addition to that, the content of a document tree can be serialized
into a sequence of characters using the tag-based syntax, which is generated
based on the pre-order tree traversal.

```js
//- the basic document tree traversal
traverseInDocOrder(node) {
  //- used to write start-tags
  //- write("<%s %s>", name, attributes)
  onEnter(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- used to write end-tags
  //- write("</%s>", name)
  onExit(node);
}
```

When trying to parse the tag-based syntax (aka. **tag soup**) of a document,
questions arise about the semantics of a start-tag and an end-tag. That is
because while parsing a tag soup, both tags can be understood to trigger
events, which is why the process of parsing a document can be described as
an event-driven process.

* (1) a **start-tag** can be said to trigger an **enter-event**
* (2) an **end-tag** can be said to trigger an **exit-event**

Note that all start-tags combined can be said to represent an **enter-order**
(i.e. a sequence of enter events) and all the end-tags an **exit-order**
(i.e. a sequence of exit events). As a matter of consequence, the tag soup of
a document can be understood to define a sequence of enter- and exit events.

Note that, since each enter-event is paired with a subsequent exit-event, the
tag-based syntax can be understood to support **a stream-based point of view**.
Based on that, each pair of tags can be understood to define a sub-stream of
nodes.

Note that, as a matter of simplification, subsequent discussions will assume
that any node and its scope can be expressed in terms of a pair of tags. That
is, the tag soup of a document must be understood as a pure sequence of start-
and end-tags - i.e. with no other content in between any adjacent tags.
