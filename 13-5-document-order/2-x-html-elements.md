
<!-- ======================================================================= -->
# html elements

```
    |-html-element------------------|
.., | <n>,      | ..,     | </n>,   | ..
    |-scope(n)----------------------|
    |-start-tag-|-content-|-end-tag-|
```

- an individual component of a document
- spans from a start-tag to an end-tag
- may have child content
- nested - contains other elements
- note - elements are not tags

html's point of view
- the start-/end-tag of some elements may be "implied" - not so here
- as a matter of clarity - all tags are always shown and required
- the only exception allowed - empty elements may be compacted

html's twisted perception of "element"
- a document is processed as a node tree
- a node tree does not consist of "elements"
- a node tree consists of nodes

remark
- that combined view is misleading
- because a tag soup is still parsed into the nodes of a tree
- the reason why some think one can associate while exiting - which you can not
- the more reason why a property must apply to all the descendants
- the more reason to title it "a tag soup ain't no (fucking) node tree"
