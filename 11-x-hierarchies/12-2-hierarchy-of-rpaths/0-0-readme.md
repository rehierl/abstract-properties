
# hierarchy of rooted paths (rpaths, Hrp)

```
T <-> Hrp
```

A tree (T) can be used to form a hierarchy of rooted paths (Hrp) such that
the source ree can be recreated based on the relationships between its paths.
That is, each tree is isomorphic to a hierarchy of rooted paths, which will
be referred to as **the T-Hrp isomorphism**.

Note that a hierarchy of rooted paths (Hrp) is defined as a setup of strings
such that the related-to operator is based on the **prefix-of** operator,
and such that its strings are either related ex-or overlap each other (i.e.
the **RE-OV** case). Furthermore, the characteristic element **CE** of each
rooted path is required to be its last element.

Note that, since a forest of rooted paths must hold each prefix of every path
in it, a hierarchy of rooted paths (Hrp) can be said to embed total suborders,
one for each path in it, each of which can be derived from the longest path
in such a suborder. Because of that, and like a hierarchy of trees, a hierarchy
of rooted paths can be considered **anything but minimal** in regards to the
amount of information it holds.

## the Hs-Hrp isomorphism

```
T <-> Hrp <-> Hs
|<------------>|
```

A hierarchy of rooted paths (Hrp) is isomorphic to a hierarchy of (default)
scopes (Hs). After all, each rooted path in Hrp corresponds with the rooted
path of a scope in Hs.
