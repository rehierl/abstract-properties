
# document order

```
//- the default pre-order traversal
traverseInPreOrderD(node) begin
  //- corresponds with the node's start-tag
  //- visit the node and enter its scope
  visit(node)

  //- visit all child nodes in order
  for(child in node.childNodes) begin
    traverseInPreOrderD(child)
  end

  //- corresponds with the node's end-tag
  //- no vitis, only exit the node's scope
end
```

```
traversInDocOrder(node) begin
  //- corresponds with the node's start-tag
  //- visit the node and enter its scope
  onEnterScope(node)

  //- visit all child nodes in order
  for(child in node.childNodes) begin
    traverseInDocOrder(child)
  end

  //- corresponds with the node's end-tag
  //- no vitis, only exit the node's scope
  onExitScope(node)
end
```

* the doctree's tag-based syntax is hierarchical, interleaved child orders
* no level-order - the doctree's tag-based syntax is hierarchical
* no post-order, no reversed pre-order - none is order-preserving
* the document order corresponds with the tree's pre-order trace
* there is no/zero/zip, not even one shred of doubt about that

visit-/enter-/exit-events

* a start-tag marks the beginning of the node's scope
* a start-tag corresponds with the scope's enter-event
* a start-tag corresponds the visit-event of a node
* an end-tag (only) marks the end of the node's scope
* an end-tag corresponds with the scope's exit-event
* an end-tag does not correspond with the visit-event of any node
