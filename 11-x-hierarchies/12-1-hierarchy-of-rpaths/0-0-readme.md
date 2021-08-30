
# hierarchy of rpaths
- the (rpaths <-> trees) correspondence

```
T <-> HR <-> HS
```

* T - node trees
* HR - a hierarchy of rooted paths
* HS - a hierarchy of scopes

A tree (T) can be used to form a hierarchy of rooted paths (HR) such that the
source tree can be recreated from it. Likewise, a hierarchy of rooted paths
allows to form a tree, which in turn allows to recreate the source hierarchy.
That is, each tree is isomorphic to a hierarchy of rooted paths. And since a
forest of trees is the disjoint union of trees, each such forest corresponds
with a forest of rooted paths.

Note that there is no order amongst the child paths in a hierarchy. That is,
a hierarchy would need to have additional characteristics which could then be
used to define a child order over the rooted paths in that hierarchy - e.g.
an ordered sequence of rooted paths.

A hierarchy of rooted paths (HR) also allows to directly form a hierarchy
of scopes (HS) from it. Conversely, a hierarchy of scopes allows to form
a hierarchy of rooted paths. That is, a hierarchy of rooted paths is also
isomorphic to a hierarchy of scopes.
