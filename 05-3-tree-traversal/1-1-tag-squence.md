
<!-- ======================================================================= -->
## the tag sequence of a document tree

A document tree can be serialized in to a character-based sequence of tags,
if the enter- and exit-events are used to produce start- and end-tags as
roughly outlined below.

```
tagSequenceOf(root) being
  sequence = ()

  onEnterScope(node) begin
    name = node.tagName.toLowerCase
    attribtues = node.attributes.toString
    sequence.add("<%s %s>", name, attributes)
  end

  onExitScope(node begin
    name = node.tagName.toLowerCase
    sequence.add("</%s>", name)
  end

  traverseDocTree(node) begin
    onEnterScope(node)

    for(child in node.childNodes) begin
      traverseDocTree(child)
    end

    onExitScope(node)
  end

  traverseDocTree(root)
  return sequence
end
```

Note that, if all tags within the produced trace of tags are concatenated in
order of appearance, then the result can informally be described as **tag soup**.

Note that any tag produced will reflect the corresponding enter-/exit-event.
Also, only the enter-event is being used to enrich the start-tag with the
attributes of a node. As such, the start-tag can be understood to provide the
definitions that are required to reproduce the node while recreating the node
tree from the tag sequence.

Note that this does seem to suggest, that an enter-event corresponds with the
visit of a node. Consequently, one can assume that even a tag sequence is first
and foremost in pre-order.

Note that, since a tag sequence seems to be in pre-order, this can also be
understood to suggest that no operation may be executed that is in regards
to that particular node. After all, that node has then already been
visited/processed.
