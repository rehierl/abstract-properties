
<!-- ======================================================================= -->
# strictly bound

* the tag-based syntax is strictly bound to the scope of a node
* placing a pair of tags defines such a scope
* that is the reason why a sequence of tags must be "well formed"

```
.., <div>, .., <n>, .., </div>, .., </n>, ..
    |-scope(div)--------------|
               |-scope(n)---------------|
```

* scopes can not overlap each other
* that is against the nature of the tag-based syntax
* there is just no way that that kind of nonsense will ever work
