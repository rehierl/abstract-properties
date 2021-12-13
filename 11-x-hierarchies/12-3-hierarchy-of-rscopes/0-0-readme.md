
# hierarchy of reversed scopes (rscopes, Hrs)

```
T <-> Hrs
```

A tree (T) can be used to form a hierarchy of reversed scopes (Hrs) such that
the source tree can be recreated based on the relationships between the scopes
in it. That is, each tree is isomorphic to a hierarchy of reversed scopes,
which will be referred to as **the T-Hrs isomorphism**.

Note that a hierarchy of reversed scopes (Hrs) is defined as a setup of sets
such that the related-to operator is based on the **subset-of** operator.
Furthermore, the inner subset of each reversed scope consist of all the nodes
in its ancestor scopes. Because of that, a reversed scope shares its **CEs**
with its descendant scopes, which is why a reversed scope is the most
significant scope that has its CE as an element.

Note that a hierarchy of reversed scopes is **dual to** a hierarchy of default
scopes (Hs). That is because a hierarchy of default scopes is defined based on
the superset-of operator. Furthermore, the inner subset of each default scope
contains all the nodes in its descendant scopes. Because of that, a default
scope shares its CEs with its ancestor scopes, which is why a default scope
is the least significant scope that has its CE as an element.

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
being equivalent to a tree (T).

As a matter of consequence, each hierarchy of scopes (Hs) is equivalent to a
hierarchy of reversed scopes (Hrs). That is, one can be transformed into the
other.
