
<!-- ======================================================================= -->
# the document tree traversal

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

```js
//- the recursive document tree traversal
traverseInDocOrder(node) {
  //- enter the node's scope
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
## remarks

Note that, if the tag soup of a document is broken apart into a sequence of
tags, and if all the end-tags are dropped, then the resulting sequence of
start-tags corresponds with the pre-order trace of a document tree.

Note that **the post-order visit-order** of the nodes in a document tree
corresponds with the document tree's **exit-order**. That is, the pre-order
exit-order and also the post-order exit-order.

Note that the **the pre-order enter-order** corresponds with the (pre-order)
visit of a node. Because of that one can state that the pre-order visit-order
corresponds with **the tree's pre-order trace**.

However, one needs to be aware that the enter- and the visit-event of a node
are still not identical. After all, one marks the beginning of the node's
scope, while the other marks when that node is being processed.
