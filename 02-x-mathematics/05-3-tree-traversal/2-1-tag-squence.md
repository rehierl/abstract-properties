
<!-- ======================================================================= -->
## the tag sequence of a document tree

A document tree can be serialized into a character-based sequence of strings,
if the enter- and exit-events are used to produce start- and end-tags as
outlined below.

```js
tagSequenceOf(root) {
  sequence = ();

  //- recursively traverse the given node
  traverseDocTree(node) {
    //- enter the node's scope
    onEnter(node);

    //- traverse the node's child nodes
    for(child in node.childNodes) {
      traverseDocTree(child);
    }

    //- exit the node's scope
    onExit(node);
  }

  //- process the node's enter-event
  //- used to write "<$name $attributes>"
  onEnter(node) {
    name = node.tagName;
    attribtues = node.attributes.toString();
    sequence.add("<%s %s>", name, attributes);
  }

  //- process the node's exit-event
  //- used to write "</$name>"
  onExit(node) {
    name = node.tagName;
    sequence.add("</%s>", name);
  }

  traverseDocTree(root);
  return sequence;
}
```

Note that, if all tags within the produced trace of tags are concatenated in
order of appearance, the result can informally be described as **tag soup**.

Note that any tag produced will reflect the corresponding event. Also, only
the enter-event is being used to enrich a tag with the attributes of a node.
As such, a start-tag can be understood to provide all the properties that
are required to reproduce a node while recreating the node tree from such
a tag sequence. Consequently, a tag soup can be assumed to be in enter-order
and, as such, to reflect a pre-order tree traversal.

Note that this does seem to suggest, that an enter-event corresponds with
the visit of a node. Consequently, one can assume that even a tag sequence
is first and foremost in pre-order.

Note that, since a tag sequence seems to be in pre-order, this can also be
understood to suggest that no operation may be executed in regards to a
node during the exit-event of that particular node. After all, that node
has then already been visited/processed.
