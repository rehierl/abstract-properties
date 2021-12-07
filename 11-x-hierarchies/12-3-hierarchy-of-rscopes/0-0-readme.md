
# hierarchy of reversed scopes (rscopes)

```
T <-> Hrs
```

A tree (T) allows to form a hierarchy of reversed scopes (Hrs) such that the
source tree can be recreated based on the relationships between the reversed
scopes in it. That is, each tree is isomorphic to a hierarchy of reversed
scopes. Because of that, this isomorphism will be referred to as
**the T-Hrs isomorphism**.

Note that the reversed scope of a node, which is equal to the set of nodes
in the rooted path of its defining node, can be described as the defining
node's context.

## the Hrs-Hrp isomorphism

```
T <-> Hrs <-> Hrp
|<------------->|
```

A hierarchy of reversed scopes (Hrs) is isomorphic to a hierarchy of rooted
paths (Hrp). After all, each reversed scope is equal to the set of nodes in
the rooted path of its defining node.

Recall that, based on the Hs-Ht isomorphism, one can treat a hierarchy of
(default) scopes (Hs) as being equivalent to a hierarchy of trees (Ht). Similar
to that, and based on the Hrs-Hrp isomorphism, a hierarchy of reversed scopes
(Hrs) will be treated as being equivalent to a hierarchy of rooted paths (Hrp).
