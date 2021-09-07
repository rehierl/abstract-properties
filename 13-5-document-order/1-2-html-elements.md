
<!-- ======================================================================= -->
# html elements

```
.., <n>, fc, .., lc, .., l, </n>, ..
   |-scope(n)-------------------|
```

- an individual component of a document
- one of several types of html nodes - text, comments, ...
- spans from a start-tag, may have child content,
  terminated by an end-tag
- can be nested - contain other elements
- however - elements are not tags

```
.., <n>, </n>, .., <n/>, ..
    |-s(n)---|     |---|
```

- empty elements - have no content
- `<n/>` or `<n />` are mere syntactic shortcuts

html's point of view
- the start-/end-tag of some elements may be "implied" - not so here
- as a matter of clarity - all tags are always required
- the only exception - empty elements may be compacted as shown above

remark
- that combined view is misleading
- because a tag soup is still parsed into the nodes of a tree
- the reason why some think one can associate while exiting - which you can not
- the more reason why a property must apply to all the descendants
- the more reason to title it "a tag soup ain't no (fucking) node tree"
