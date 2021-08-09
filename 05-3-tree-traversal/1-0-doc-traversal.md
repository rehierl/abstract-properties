
<!-- ======================================================================= -->
# document traversal

When writing a document as a character-based sequence of start- and end-tags,
the document tree must be traversed in document order. That traversal order
is, as can be seen below, a combination of the default pre-order and post-order
tree traversal.

```
traversInDocOrder(node) begin
  onEnterScope(node)

  for(child in node.childNodes) begin
    traverseInDocOrder(child)
  end

  onExitScope(node)
end
```

Even though the exact meaning of `onEnterScope()` and `onExitScope()` will be
defined in the course of subsequent discussions, one can already describe these
function calls as **enter-** and **exit-events**, which is why the traversal of
a document tree can be described as **an event-driven process**.

However, one must keep in mind that these enter- and exit-events are
**a source of confusion** since these do not reflect the visit of that node.
Instead, both events reflect when a certain scope, which must be understood
in regards to that particular node, will be entered and exited.

Note that, if the enter-event is used to append the node to the current trace
of nodes, the trace can be described as being in **enter-order**. Conversely,
if the exit-event is used, the trace can be described as being in **exit-order**.

Note that these events can be understood from **a stream-based perspective**.
That is, the corresponding scope can be described as being open when it is
entered, and closed when it is exited.

Note that the scope can be understood counts as being open for as long as the
node and all of its descendants in the unordered document tree are being
visited. Because of that, the scope corresponds with the set of nodes of the
corresponding induced subtree.
