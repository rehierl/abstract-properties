
# hierarchy of rpaths
- the (rpaths <-> trees) correspondence

```
T <-> Hr
```

A tree (T) can be used to form a hierarchy of rooted paths (Hr) such that the
source tree can be recreated from it. Likewise, a hierarchy of rooted paths
allows to form a tree, which in turn allows to recreate the source hierarchy.
That is, each tree is isomorphic to a hierarchy of rooted paths. Because of
that, this isomorphism will be referred to as **the T-Hr isomorphism**.

Note that since a forest of trees is a union of disjoint trees, each forest
can be understood to correspond with a forest of rooted paths.

Note that there is no order amongst the child paths in a hierarchy. That is,
a hierarchy would need to have additional characteristics which could then
be used to define a child order over the rooted paths of siblings - e.g. an
ordered sequence of rooted paths.

## the Hs-Hr isomorphism

```
T <-> Hr <-> Hs
|<----------->|
```

A hierarchy of rooted paths (Hr) is also isomorphic to a hierarchy of scopes
(Hs).
