
# a (serialized) hierarchy of scopes (HsPre)

```
DT <-> HsPre
```

An ordered document tree (DT) allows to form a hierarchy of scopes (HsPre)
such that the source tree can be recreated based on the relationships between
its scopes. However, in order to encode the doctree's child order, the scopes
of HsPre must be provided as an **ordered sequence of scopes** such that the
child order can be derived from it. Based on that, each document tree is
isomorphic to a (serialized) hierarchy of scopes, which will be referred to
as **the DT-HsPre isomorphism**, or simply as **the DT-Hs isomorphism**.

Recall that a hierarchy of scopes (Hs) is defined as a setup of sets such that
the related-to operator is based on the **superset-of** operator, and such that
the sets in it are either disjoint ex-or related with each other (i.e. the
**DI-RE** case). Furthermore, each set in Hs is required to have one and only
one characteristic element **CE**, which is expected to be a reference to the
node a set represents.

## the HsPre-Hpre isomorphism

```
DT <-> HsPre <-> Hpre
|<----------------->|
```

A hierarchy of scopes (HsPre) is isomorphic to a hierarchy of pre-order traces
(Hpre). After all, the child order embedded into the ordered sequence of scopes
can be used recreate the document tree, which is isomorphic to a hierarchy of
traces.

Note that the HsPre-Hpre isomorphism suggests that there are also isomorphisms
between HsPre and hierarchies of other traces (i.e. post-order, level-order).
After all, a hierarchy of scopes can be used to derive a document tree, which
can be traversed in any order.
