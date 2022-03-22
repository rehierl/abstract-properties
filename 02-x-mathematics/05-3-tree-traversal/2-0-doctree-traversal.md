
<!-- ======================================================================= -->
# document traversal

When serializing a document tree as a character-based sequence of start- and
end-tags, the document tree must be traversed in document order. That traversal
order is, as can be seen below, a combination of the default pre- and post-order
tree traversal.

```js
traverseInDocOrder(node) {
  //- enter the node's scope
  //- visit the node in pre-order
  //- e.g. used to write start-tags
  onEnter(node);

  //- visit the child nodes
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- exit the node's scope
  //- visit the node in post-order
  //- write("</%s>", name)
  onExit(node);
}
```

Even though the exact meaning of `onEnter()` and `onExit()` will be clarified
in the course of subsequent chapters, one can already refer to these function
calls as **enter-** and **exit-events**, which is why the traversal of a tree
can be described as **an event-driven process**.

One must however always keep in mind that these enter- and exit-events are
**a source of confusion** since both events combined do not reflect the visit
of a node. That is because, both events only reflect when **a certain scope**,
which must be understood in regards to that particular node, will be entered
and exited.

Note that, if the enter-event is used to append the node to the current trace
of nodes, the trace can be described as being in **enter-order**. Conversely,
if the exit-event is used, the trace can be described as being in **exit-order**.

Note that these events can be understood from **a stream-based perspective**.
That is, the corresponding scope can be described as being open when it is
entered, and closed when it is exited.

Note that the scope of a node counts as being open for as long as the node
and all of its descendants in the unordered document tree are being visited.
Because of that, the scope of a node corresponds with the set of nodes of
the underlying induced subtree.
