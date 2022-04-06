
<!-- ======================================================================= -->
# the document tree traversal

Since the theoretical construction of the tag-based syntax is clear, the
question remains as to how an implementation can produce the tag soup of
a document tree.

```
     .. × n × (<tag> fc .. lc .. </tag>) × (ns .. ls ..) × ..
enter ->|-s(n)-------------------------->|-> exit
```

Since the tag-based syntax is formed by applying the pre-order rule to
the ordered document tree, a node appears presequent to its descendants
(in regards to the unordered document tree - DTU) in the document order.
Because of that, a document tree must be **traversed in tree order**,
which allows to write the start-tag of a node before the start-tags of
its descendants.

Since the tags of the descendants of a node must appear before the end-tag
of a node (i.e. before the scope of a node is exited), a document tree must
be **traversed depth-first**, which allows to write the end-tag of a node
just after the end-tags of its descendants, and also before the start-tags
of its subsequent siblings.

Since the pre-order rule is applied after embedding the document tree's
child order in order (i.e. not reversed), a document tree must be
**traversed in child order** such hat the start-tag of a node can be
written before the start-tags of its subsequent siblings.

Note that these orders require the start-tags to be written **in pre-order**
and the end-tags to be written **in post-order**. Because of that, the
(recursive) document tree traversal algorithm is a combination of the
pre-order and the post-order tree traversal algorithms.

```js
//- the recursive document tree traversal
traverseInDocOrder(node) {
  //- enter the node's scope
  //- write the node's start-tag before the
  //  start-tags of its descendants in DTU
  //- write the node's start-tag before the
  //  start-tags of its subsequent siblings
  //- write("<%s %s>", name, attributes)
  onEnter(node);

  //- recursively visit all child nodes
  //- write the pairs of tags of the node's
  //  descendants in DTU in between the
  //  pair of tags of the current node
  //- in child order - not in reverse
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- exit the node's scope
  //- write the node's end-tag after the
  //  end-tags of its descendants in DTU
  //- write the node's end-tag before the
  //  start-tags of its subsequent siblings
  //- write("</%s>", name)
  onExit(node);
}
```

Note that the document tree traversal is a combination of the pre-order and
the post-order tree traversal algorithms. However, it is still the start-tag
of a node that defines a node and marks the beginning of the node's scope.
Likewise, the end-tag of a node still only marks the end of the node's scope.

Since the above document tree traversal algorithm produces the tag-based
document of a document tree, it can be understood as *the* document tree
traversal. That is, a document tree must be processed this exact way, or
in a way that is equivalent to this processing order - e.g. non-recursively.

Recall that **the scope of a node is a superset** to the scopes of its
descendants. Because of that, the scope of a node will be entered before
the scopes of its descendants (i.e. in pre-order). In contrary to that,
the scope of a node will be exited after the scopes of its descendants
have been exited (i.e. in post-order).
