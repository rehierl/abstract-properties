
# hierarchy of reversed scopes (rscopes, Hrs)

```
T <-> Hrs
```

A tree (T) can be used to form a hierarchy of reversed scopes (Hrs) such that
the source tree can be recreated based on the relationships between the scopes
in it. That is, each tree is isomorphic to a hierarchy of reversed scopes,
which will be referred to as **the T-Hrs isomorphism**.

Note that a hierarchy of reversed scopes (Hrs) is defined as a setup of sets
such that the related-to operator is based on the **subset-of** operator,
and such that the sets in it are either related with ex-or overlap each other
(i.e. the **RE-OV** case). Furthermore, each set in Hrs is required to have
one and only one characteristic element **CE**.

Note that, based on the definition of a hierarchy of (default) scopes (Hs),
one can state that a hierarchy of reversed scopes (Hrs) is **dual to** Hs
and vice versa.

## the Hrs-Hrp isomorphism

```
T <-> Hrs <-> Hrp
|<------------->|
```

A hierarchy of reversed scopes (Hrs) is isomorphic to a hierarchy of rooted
paths (Hrp). After all, each reversed scope is equal to the set of nodes in
the rooted path of its defining node. Because of that, Hrs can be described
to embed total suborders, one for each rooted path in Hrp.

## the Hrs-Hs isomorphism

```
T <-> Hrs <-> Hs
|<------------>|
```

Recall that, based on the T-Hs isomorphism, one can treat a hierarchy of scopes
(Hs) as being equivalent to a tree (T). Similar to that, and based on the T-Hrs
isomorphism, one can treat a hierarchy of reversed scopes (Hrs) as being
equivalent to a tree (T).

As a matter of consequence, each hierarchy of scopes (Hs) can be treated as
being equivalent to a hierarchy of reversed scopes (Hrs). That is, one can be
transformed directly into the other.
