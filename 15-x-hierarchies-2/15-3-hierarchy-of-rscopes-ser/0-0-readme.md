
# a (serialized) hierarchy of rscopes (HrsSer)

```
DT <-> HrsSer
```

Analogous to a serialized hierarchy of scopes, an ordered document tree (DT)
allows to form a serialized hierarchy of reversed scopes (HrSer) such that
the source tree can be recreated based on the relationships between its
scopes. However, in order to encode the doctree's child order, the reversed
scopes of HrSer must be provided as **an ordered sequence of rscopes** such
that the child order can be derived from it. Based on that, each document
tree is isomorphic to a (serialized) hierarchy of reversed scopes, which will
be referred to as **the DT-HrSer isomorphism**.

Note that, depending on a given context, the DT-HrSer isomorphism may simply
be **referred to as the T-Hrs isomorphism**. After all, in order to fully
recreate a document tree, its child order must be available.

Recall that a hierarchy of reversed scopes (Hrs) is defined as a setup of
sets such that the related-to operator is based on the **subset-of** operator,
and such that the sets in it are either related with ex-or overlap each other
(i.e. the **RE-OV** case). Furthermore, each set in Hrs is required to have
one and only one characteristic element **CE**.

## the HsSer-Hpre isomorphism

```
DT <-> HrsSer <-> Hpre
|<------------------>|
```

A hierarchy of reversed scopes (HrsSer) is isomorphic to a hierarchy of traces
(Hpre). After all, the child order embedded into the ordered sequence of scopes
can be used recreate the document tree, which is isomorphic to a hierarchy of
traces.

## the HrsSer-HsSer isomorphism

```
DT <-> HrsSer <-> HsSer
|<------------------->|
```

Note that, since a serialized hierarchy of scopes (HsSer) is isomorphic to a
document tree (DT), and since a serialized hierarchy of reversed scopes (HrsSer)
is also isomorphic to a document tree (DT), the above suggests that both are
isomorphic to each other. That is, depending on a specific encoding, one might
end up being able to transform one into the other more or less efficiently.
