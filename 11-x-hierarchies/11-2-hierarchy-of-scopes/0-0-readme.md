
# hierarchy of scopes (Hs)

```
T <-> Hs
```

A tree (T) allows to from a hierarchy of scopes (Hs) such that the source tree
can be recreated based on the relationships between its scopes. That is, each
tree is isomorphic to a hierarchy of scopes, which will referred to as
**the T-Hs isomorphism**.

Note that a hierarchy of scopes (Hs) is defined as a setup of sets such that
the related-to operator is based on the **superset-of** operator, and such
that the sets in it are either disjoint ex-or related with each other (i.e.
the **DI-RE** case). Furthermore, each set in Hs is required have one and only
one characteristic element **CE**, which is expected to be a reference to the
node a set represents.

Note that, based on the Ht-Hs isomorphism, one can treat a hierarchy of scopes
(Hs) as being equivalent to a hierarchy of trees (Ht). Both constructs can
therefore be understood to express the same thing using different syntactic
rules.
