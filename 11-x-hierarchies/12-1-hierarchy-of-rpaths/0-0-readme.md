
# hierarchy of rpaths

```
T <-> Hr
```

A tree (T) can be used to form a hierarchy of rooted paths (Hr) such that the
source tree can be recreated based on the relationships between its paths.
That is, each tree is isomorphic to a hierarchy of rooted paths. Because of
that, this isomorphism will be referred to as **the T-Hr isomorphism**.

Note that there is no order amongst sibling paths in a hierarchy. That is,
a hierarchy would need to have additional characteristics which could then
be used to define a child order over the rooted paths of siblings - e.g. an
ordered sequence of rooted paths.

Note that since a forest of trees is a union of disjoint trees, each forest
is isomorphic to a forest of rooted paths.

## the Hs-Hr isomorphism

```
T <-> Hr <-> Hs
|<----------->|
```

A hierarchy of rooted paths (Hr) is also isomorphic to a hierarchy of scopes
(Hs).
