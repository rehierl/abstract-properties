
# document order / the tag-based syntax

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

This meta-chapter begins with **embedding tag-based nodes** into a document
tree - i.e. the start-tag as a first child and the end-tag as a last child.
The pre-order trace of the extended document tree can be described as a
sequence of nodes and tags ..

```
n, <tag>, fc, .., lc, .., l, </tag>, ns, .., ls
|-s1-------|              |-s2--------|
```

.. such that each node `n` is followed by its start-tag `<tag>`, which is
followed by the node's first child `fc` - i.e. `s1 := (n, <tag>, fc)`.
Furthermore, the last subsequent descendant leaf `l` of the node's last
child `lc` is followed by the node's end-tag `</tag>`, which is followed
by the node's next subsequent sibling `ns` - i.e. `s2 := (l, </tag>, ns)`.
That is, there are no other nodes in between the node's tags and these nodes.

```
n, <tag>, fc, .., lc, .., l, </tag>, ns, .., ls
|-->|------------------------->|
```

This mixed sequence of nodes and tags can then be turned into a pure sequence
of tags (i.e. the document's **tag soup**), if both tags reflect the node's
name, and if the node's start tag is redefined to hold attributes such that
the start-tag's attributes define all of the node's characteristics.

```
pre(n) := (<n attribute*>, fc, .., lc, .., </n>)
           |-s(n)---------------------------->|
```

Since each node can now be understood to be **pushed into its start-tag**,
the **start-tag** of a node corresponds with the absolute position of that
node in the document tree's pre-order trace. That is, the start-tag of a node
denotes **the (pre-order) visit of a node**. Furthermore, the start-tag of a
node can be understood to denote the characteristic element (CE) of the node's
scope (i.e. the node itself).

In contrary to that, the **end-tag** of a node does not correspond with any
node, which is why the end-tag of a node only marks the end of the node's
scope. Because of that, no attributes can be set on the end-tag of a node.
Hence, an end-tag is nothing more but **an end-marker**.

```js
//- the basic document tree traversal
traverseInDocOrder(node) {
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  onEnter(node);

  //- recursively visit the child nodes
  for(child in node.childNodes) {
    traverseInDocOrder(child);
  }

  //- exit the node's scope
  //- write("</%s>", name)
  onExit(node);
}
```

Note that the recursive document traversal algorithm is a combination of the
pre-order and the post-order tree traversal algorithm. And since each tag
corresponds with the enter- or exit-event of the corresponding scope, parsing
the tag soup of a document tree can be described as **an event-driven process**,
which is why the tag soup of a document tree can be understood to define
**an order of events** (i.e. the enter- and exit-order).

Note that a tag soup counts as being **well-formed**, if and only if it consists
of pairs of start- and end-tags such that the strings of nodes they define are
either disjoint ex-or related. Otherwise, an input document can be described
as being **malformed**.

Note that an **implementation** may in general choose to return some best-effort
result, or choose to not return a result by throwing an error, as soon as it
can determine that the input document is malformed.
