
<!-- ======================================================================= -->
# the (pre-order) visit of a node

Recall that chapter 05-3 (the pre-order tree traversal) explained that the
pre-order tree traversal can be used to form the pre-order trace of the
corresponding tree, if each node is appended to a sequence of nodes while
it is in the process of being visited (i.e. visited in pre-order). Formed
this way, the resulting trace is an ordered sequence of nodes that an be
said to reflect **the pre-order node order** of the source tree.

```js
//- the recursive pre-order tree traversal
traverseInPreOrder(node) {
  //- visit the node and enter its scope
  //- e.g. append to the pre-order trace
  visitInPreOrder(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInPreOrder(child);
  }

  //- exit the node's scope
}
```

**The (pre-order) visit of a node** can be understood as **a slice of time**
that is used during the (pre-order) traversal of a tree to process some of
the data that is associated with the current node. That silce of time can
for example be used to append the current node to the tree's pre-order trace.

```
---> | slice n-1 | slice n | slice n+1 | ---> processing time
               ->| visit n |<-
```

Note that the entire processing time of a tree traversal can be described to
fall apart into a sequence of disjoint slices. Furthermore, each node in a
tree corresponds with one such slice only. As a matter of consequence, no node
will be visited while another node is still in the process of being visted and
each node will be visited once only. Because of that, the visit of a node can
be described as **an indivisible atomic operation**.

```js
//- the default post-order tree traversal
traverseInPostOrder(node) {
  //- enter the node's scope

  //- visit the node's child nodes
  for(child in node.childNodes) {
    traverseInPostOrder(child);
  }

  //- visit the node and exit its scope
  //- e.g. append to the post-order trace
  visitInPostOrder(node);
}
```

In contrary to the pre-order visit of a node, **the post-order visit of a node**
refers to a different slice of time that is used during the post-order tree
traversal to process a node in post-order. As before, that slice of time can
for example be used to append the current node to the tree's post-order trace.

```js
//- the recursive document tree traversal
traverseInDocOrder(node) {
  //- visit the node in pre-order and enter its scope
  //- e.g. write("<%s %s>", name, attributes)
  visitInPreOrder(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- visit the node in post-order and exit its scope
  //- e.g. write("</%s>", name)
  visitInPostOrder(node);
}
```

As can be seen, **the traversal of a document tree** is a combination of the
pre-order and the post-order tree traversal algorithms. After all, start-tags
must be written while the scope of a node is being entered, and end-tags while
the scope of a node is being exited.

Note that discussions tend to get confusing since one can refer to the pre-order
and the post-order visit as "the visit of a node". Because of that, one should
**avoid using descriptions that refer to the visit of a node**. Instead, one
should use descriptions that are **in regards to the enter- and exit-events**
of the corresponding scope.
