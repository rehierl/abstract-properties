
<!-- ======================================================================= -->
# the (pre-order) visit of a node

Recall that chapter 05-3 (the pre-order tree traversal) explained that the
pre-order tree traversal can be used to form the pre-order trace of a tree,
if each node is appended to a sequence of nodes while it is in the process
of being visited (i.e. visited in pre-order). Formed this way, the resulting
trace is an ordered sequence of nodes that can be understood to reflect
**the pre-order node order** of the source tree.

```
---> | slice n-1 | slice n | slice n+1 | ---> processing time
               ->| visit n |<-
```

**The (pre-order) visit of a node** can be understood as **a slice of time**
that is used during the (pre-order) traversal of a tree to process some of
the data that is associated with the current node. That silce of time can
for example be used to append the current node to the tree's pre-order trace.

Note that the entire processing time of a tree traversal can be described
to fall apart into a sequence of disjoint slices. Furthermore, each node in
a tree corresponds with one such slice only. As a matter of consequence, no
node will be visited while another node is still in the process of being
visted and each node will be visited once only. Because of that, the visit
of a node can be described as **an indivisible atomic operation**.

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

In contrary to the pre-order visit of a node, **the post-order visit of a node**
refers to a different slice of time that is used during the post-order tree
traversal to process a node in post-order. As before, that slice of time can
for example be used to append the current node to the tree's post-order trace.

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

As can be seen, **the traversal of a document tree** is a combination of the
pre-order and the post-order tree traversal algorithms. After all, start-tags
must be written while the scope of a node is being entered, and end-tags must
be written while the scope of a node is being exited.

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

<!-- ======================================================================= -->
## remarks

Note that discussions tend to get confusing since, depending on one's current
point of view, one can refer to the pre-order visit and the post-order visit
of a node as **the visit of a node**. Hence, one should **avoid** descriptions
that refer to the visit of a node. Instead, one should use descriptions that
are in regards to the corresponding enter- and exit-events.

Note that, since it is the start-tags that can be understood to define all of
the nodes in a document tree, one can **by default assume** that descriptions
are in regards to **the pre-order visit of a node**.

Note that **the pre-order enter-order is identical to the post-order enter-order**.
That is because both tree traversal algorithms enter the scope of a node in the
exact same order. Likewise, one can state that the pre-order exit-order is
identical to the post-order exit order.

Note that the pre-order and the post-order tree traversal algorithms
**differ in their visit-order**. That is because a pre-order tree traversal
visits the nodes in enter-order whereas a post-order tree traversal visits
the nodes in exit-order.

Note that one needs to be aware that the enter-event and the (pre-order)
visit-event of a node are not identical. After all, one marks the beginning
of a scope whereas the other marks the visit of corresponding node.
