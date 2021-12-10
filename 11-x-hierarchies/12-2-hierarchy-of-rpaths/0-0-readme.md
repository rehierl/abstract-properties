
# hierarchy of rooted paths (rpaths, Hrp)

```
T <-> Hrp
```

A tree (T) can be used to form a hierarchy of rooted paths (Hrp) such that
the source ree can be recreated based on the relationships between its paths.
That is, each tree is isomorphic to a hierarchy of rooted paths, which will
be referred to as **the T-Hrp isomorphism**.

Note that a hierarchy of rooted paths (Hrp) is defined as a setup of strings
such that the related-to operator is based on the **prefix-of** operator, and
such that its strings are either related ex-or overlap each other (i.e. the
**RE-OV** case). Finally, the characteristic element **CE** in each rooted
path is its last element.

## the Hs-Hrp isomorphism

```
T <-> Hrp <-> Hs
|<------------>|
```

A hierarchy of rooted paths (Hrp) is isomorphic to a hierarchy of (default)
scopes (Hs). After all, each rooted path in Hrp corresponds with the rooted
path of a scope in Hs.
