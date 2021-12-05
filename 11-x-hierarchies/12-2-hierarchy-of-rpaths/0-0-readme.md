
# hierarchy of rpaths

```
T <-> Hrp
```

A tree (T) can be used to form a hierarchy of rooted paths (Hrp) such that the
source tree can be recreated based on the relationships between its paths. That
is, each tree is isomorphic to a hierarchy of rooted paths. Because of that,
this isomorphism will be referred to as **the T-Hrp isomorphism**.

Note that there is no order over the rooted paths in such a hierarchy. That is,
a hierarchy would need to have additional characteristics which allow to embed
a child order over the rooted paths of siblings - e.g. an ordered sequence of
rooted paths.

Note that a hierarchy of rooted paths (Hrp) can be described as a partial setup
of strings such that the related-to operator is based on the **prefix-of**
operator, and such that its strings are either related ex-or overlap each other
(i.e. the **RE-OV** case). Finally, the CE in each string is its last element.

## the Hs-Hr isomorphism

```
T <-> Hrp <-> Hs
|<------------>|
```

A hierarchy of rooted paths (Hr) is isomorphic to a hierarchy of scopes (Hs).
After all, each rooted path in Hr corresponds with the rooted path of a scope
in Hs.
