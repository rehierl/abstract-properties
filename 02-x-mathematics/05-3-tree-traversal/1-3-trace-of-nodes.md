
<!-- ======================================================================= -->
# trace of nodes

Any tree traversal can be used to produce an ordered squence of nodes that is
commonly described as **a trace of nodes**, if the node that is being visited,
is appended to the sequence at the time it is being visited. Because of that,
such a trace of nodes reflects the path the traversal algorithm took through
the tree when visiting each node one after another.

```js
preOrderTraceOf(root) {
  trace = ();

  traverseInPreOrder(node) {
    //- visit the current node
    trace.append(node);

    //- visit the node's child nodes
    for(child in node.childNodes) {
        traverseInPreOrder(child);
    }
  }

  traverseInPreOrder(root);
  return trace;
}
```

Even though any tree traversal can be used to produce a trace of nodes, the
traversal algorithm most commonly used will produce a trace of nodes that
can be described as **the pre-order trace of nodes** (or simply as the
**trace (of nodes)**) of the corresponding tree.

Similar to that, and due to the recursive nature of the traversal algorithms,
the resulting trace of nodes can even be described as the trace of the root
(or input node).

Note that, like any other ordered sequence, a trace of nodes corresponds with
a total order over the nodes in it. The process of creating a trace of nodes
therefore corresponds with **a linear extension** of the tree's node order.
