
# hierarchy of reversed scopes (rscopes, Hrs)

```
T <-> Hrs
```

A tree (T) can be used to form a hierarchy of reversed scopes (Hrs) such that
the source tree can be recreated based on the relationships between the scopes
in it. That is, each tree is isomorphic to a hierarchy of reversed scopes,
which will be referred to as **the T-Hrs isomorphism**.

Note that a hierarchy of reversed scopes (Hrs) is, unlike a hierarchy of
(default) scopes (Hs), defined as a setup of sets such that the related-to
operator is based on the **subset-of** operator. Furthermore, the inner subset
of each reversed scope consist of the nodes in its ancestors, not the nodes
in its descendants. Consequently, a reversed scope shares its characteristic
element **CE** with its descendants, not with its ancestors.

## the Hrs-Hrp isomorphism

```
T <-> Hrs <-> Hrp
|<------------->|
```

A hierarchy of reversed scopes (Hrs) is isomorphic to a hierarchy of rooted
paths (Hrp). After all, each reversed scope is equal to the set of nodes in
the rooted path of its defining node.

## the Hrs-Hs isomorphism

```
T <-> Hrs <-> Hs
|<------------>|
```

Recall that, based on the T-Hs isomorphism, one can treat a hierarchy of
scopes (Hs) as being equivalent to a tree (T). Similar to that, and based on
the T-Hrs isomorphism, one can treat a hierarchy of reversed scopes (Hrs) as
being equivalent to a tree (T) and also as being equivalent to a hierarchy
of scopes (Hs).
