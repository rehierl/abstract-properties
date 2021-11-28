
# hierarchy of rpaths

```
T <-> Hr
```

A tree (T) can be used to form a hierarchy of rooted paths (Hr) such that the
source tree can be recreated based on the relationships between its paths.
That is, each tree is isomorphic to a hierarchy of rooted paths. Because of
that, this isomorphism will be referred to as **the T-Hr isomorphism**.

Note that there is no order over the rooted paths in such a hierarchy. That is,
a hierarchy would need to have additional characteristics which could then be
used to embed a child order over the rooted paths of siblings - e.g. an ordered
sequence of rooted paths.

## the Hs-Hr isomorphism

```
T <-> Hr <-> Hs
|<----------->|
```

A hierarchy of rooted paths (Hr) is isomorphic to a hierarchy of scopes (Hs).
After all, each rooted path in Hr corresponds with the rooted path of a scope
in Hs.
