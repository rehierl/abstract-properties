
<!-- ======================================================================= -->
# xml's well-formedness

```
.., <div>, .., <n>, .., </div>, .., </n>, ..
    |-scope(div)--------------|
               |-scope(n)---------------|
```

placing a pair of tags defines the scope of a node
- the reason why a document must be "well formed"

xml's well-formedness rules
- at its core it includes that ..
- a well-formed element is such that ..
- it is an empty element `<tag/>`,
  or opened and subsequently closed
- must be properly nested - no overlap
- a document is well formed, if all the
  elements in it are well formed

scopes can not overlap each other
- that is in conflict with the tag-based syntax
- there is just no way that that kind of nonsense will ever reliably work
