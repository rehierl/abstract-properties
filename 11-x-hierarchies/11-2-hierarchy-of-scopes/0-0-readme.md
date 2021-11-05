
# hierarchy of scopes
- the (scopes <-> trees) correspondence

```
T <-> Hs
```

* T - node trees
* Hs - a hierarchy of scopes

A tree (T) allows to from a hierarchy of scopes (Hs) such that the source tree
can be recreated from it. Likewise, a hierarchy of scopes allows to form a tree,
which allows to recreate the source hierarchy. That is, each tree is isomorphic
to a hierarchy of scopes. And since a forest of trees is the disjoint union of
trees, each such forest is isomorphic to a forest of scopes.

Note that a hierarchy of scopes has no child order over the childs sets in it.
