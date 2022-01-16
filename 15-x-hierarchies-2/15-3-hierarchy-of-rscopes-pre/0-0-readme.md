
# a (serialized) hierarchy of rscopes (HrsPre)

```
DT <-> HrsPre
```

Analogous to a serialized hierarchy of scopes, a document tree (DT) allows to
form a serialized hierarchy of reversed scopes (HrsSer) such that the source
tree can be recreated based on the relationships between its scopes. However,
in order to encode the doctree's child order, the reversed scopes of HrsSer
must be provided as **an ordered sequence of rscopes** such that the child
order can be derived from it. Based on that, each document tree is isomorphic
to a (serialized) hierarchy of reversed scopes, which will be referred to as
**the DT-HrsPre isomorphism**, or simply as **the DT-Hrs isomorphism**.

Recall that a hierarchy of reversed scopes (Hrs) is defined as a setup of
sets such that the related-to operator is based on the **subset-of** operator,
and such that the sets in it are either related with ex-or overlap each other
(i.e. the **RE-OV** case). Furthermore, each set in Hrs is required to have
one and only one characteristic element **CE**.

## the HrsPre-Hpre isomorphism

```
DT <-> HrsPre <-> Hpre
|<------------------>|
```

A hierarchy of reversed scopes (HrsPre) is isomorphic to a hierarchy of traces
(Hpre). After all, the child order embedded into the ordered sequence of scopes
HrsPre can be used recreate the document tree (DT), which is isomorphic to a
hierarchy of traces Hpre.

## the HrsPre-HsPre isomorphism

```
DT <-> HrsPre <-> HsPre
|<------------------->|
```

Note that, since a hierarchy of scopes (HsPre) is isomorphic to a document tree
(DT), and since a serialized hierarchy of reversed scopes (HrsPre) is isomorphic
to a document tree (DT), the above suggests that both are isomorphic to each
other. That is, depending on a specific encoding, one will be able to transform
one representation into the other more or less efficiently.
