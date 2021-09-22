
<!-- ======================================================================= -->
# the document traversal

Recall that the document order of a document is understood as a total order
over the nodes in it. In addition to that, the content of a document tree
is serialized into a document using a tag-based syntax, which is generated
using the following base algorithm.

```js
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

Note that start-tags can be described to represent an **enter-order** (i.e. a
sequence of enter events) and the end-tags an **exit-order** (i.e. a sequence
of exit events). Based on that, the tag soup of a document can be understood
to describe as a sequence of enter- and exit events.

Note that, since each enter-event is paired with an exit-event, the tag-based
syntax can be understood to support **a stream-based point of view**.

Since an implementation must be able to determine whether or not a given node
is located within the scope of a property (e.g. within the scope of a section),
a clear understanding of the meaning of the start-tags and the end-tags is
critical. After all, how is one to tell the context of a node, if one can not
pinpoint its exact location?

Note that, as a matter of simplification, subsequent discussions will assume
that any node and its scope can be expressed in terms of a pair of tags. Based
on that, any document can be understood to consist of paired start- and end-tags
and can therefore be described as a pure sequence of tags.
