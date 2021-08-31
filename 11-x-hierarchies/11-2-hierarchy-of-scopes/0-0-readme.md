
# hierarchy of scopes
- the (scopes <-> trees) correspondence

```
T <-> Hs
```

* T - node trees
* Hs - a hierarchy of scopes

A tree (T) can be used to from a hierarchy of scopes (Hs) such that the source
tree can be recreated from it. Likewise, a hierarchy of scopes allows to form
a tree, which in turn allows to form the source hierarchy. That is, each tree
is isomorphic to a hierarchy of scopes. And since a forest of trees is the
disjoint union of trees, each such forest corresponds with a forest of scopes.

Note that there is no order amongst the child sets in a hierarchy. That is,
a hierarchy would need to have additional characteristics which could then
be used to define a child order over the sets in that hierarchy - e.g. an
ordered sequence of sets.
