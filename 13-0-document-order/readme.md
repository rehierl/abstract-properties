
# document order

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

This meta-chapter begins with **embedding tag-based nodes** into a document
tree - i.e. the start-tag as a first child and the end-tag as a last child.
The pre-order trace of the modified document tree can thus be described as
a sequence of nodes and tags ..

```
n, <tag>, fc, .., lc, .., l, </tag>, ns, .., ls
|-s1-------|              |-s2--------|
```

.. such that each node `n` is followed by its start-tag `<tag>`, which is
followed by the node's first child `fc` - i.e. `s1 := (n, <tag>, fc)`.
Furthermore, the last subsequent descendant leaf `l` of the node's last
child `lc` is followed by the node's end-tag `</tag>`, which is followed
by the node's next subsequent sibling `ns` - i.e. `s2 := (l, </tag>, ns)`.
That is, there are no other nodes in between the tags of a node and the
nodes mentioned.

```
n, <tag>, fc, .., lc, .., l, </tag>, ns, .., ls
|->|----------------------------->|
```

After a pair of tags has been injected for all the nodes in the document tree,
the resulting mixed sequence of nodes and tags can then be turned into a pure
sequence of tags (i.e. the document's **tag soup**), if both tags reflect the
node's name, and if the node's start tag is redefined to hold attributes which
define all of the node's characteristics.

```
<n attribute*>, fc, .., lc, .., </n>, ns, .., ls
|-s(n)---------------------------->|
```

Since each node can now be understood to be **pushed into its start-tag**, the
**start-tag** of a node can be understood to denote the **absolute position**
of that node in the document tree's pre-order trace. As such, the start-tag
of a node denotes **the characterisitc element** (CE) of its scope.

In contrary to the start-tag of a node, the **end-tag** of a node does not
correspond with any node, which is why the end-tag of a node only marks the
end of the node's scope, which is why an end-tag is **a mere end-marker**.
Because of that, no attributes can be set on the end-tag of a node.

```js
//- the basic document tree traversal
traverseInDocOrder(node) {
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

As can be seen, a document tree is serialized into a tag soup by traversing
the document tree using a combination of the pre-order and post-order tree
traversal algorithms.

Note that **the (pre-order) visit of a node** in a document tree is used to
write the start-tag of that node. Because of that, and since the visit of each
node can be described as **an indivisible atomic operation**, the visit-order
of the nodes corresponds with the document tree's pre-order node-order. That
is, **the visit-order is in pre-order**.

```
        |-s(n)------------------------------------------------------->|
    .., | <n attribute*>, <fc>, .., </fc>, .., <lc>, .., </lc>,  </n> |, ..
enter ->|-ce(n)---------|-iss(n)------------------------------|-empty-|-> exit
 open ->|-a-substream-of-nodes--------------------------------------->|-> close
      ->|-visit---------|<-
```

Since each tag corresponds with the enter- or exit-event of the corresponding
scope, **parsing** the tag soup of a document tree can be described as
**an event-driven process**. Based on that, the subsequence of start-tags can
be understood to define an **enter-order**, and the sub-sequence of end-tags
to define an **exit-order**. Overall, the tag soup of a document tree can be
understood to define **an order of events**.

- start-tag => enter the node's scope and visit it
- end-tag => exit the node's scope

Note that a tag soup counts as being **well-formed**, if and only if it consists
of pairs of start- and end-tags such that the strings of nodes they define are
either disjoint ex-or related. Otherwise, an input document must be understood
to be **malformed**.

Note that an **implementation** may in general choose to return some best-effort
result or choose to return no result by throwing an error, as soon as it can
determine that the input document is malformed.

<!-- ======================================================================= -->
## conclusions

Based on the above, the following conclusions can be drawn:

- end-tags can be understood as a method to define some-of quantifiers
- a tag soup defines a containment order, not a document tree
- the document order is the document tree's pre-order node order
