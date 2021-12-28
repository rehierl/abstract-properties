
# hierarchy of traces

```
T <-> Hpre
```

An ordered document tree (T) allows to form a hierarchy of pre-order traces
(Hpre) such that the source tree, including its child order, can be recreated
based on the relationships between its traces. That is, each document tree is
isomorphic to a hierarchy of pre-order traces, which will be referred to as
**the T-Hpre isomorphism**.

## (Hpre -> Hs) only

```
DT <-> Hpre -> Hs <-> T
|<------->|    |<---->|
```

A hierarchy of scopes Hs can be formed from a hierarchy of traces (Hpre) by
replacing each trace with its set of nodes. Because of that, a hierarchy of
traces allows to directly form the doctree's hierarchy of scopes. However,
a hierarchy of scopes does not allow to form a hierarchy of traces since
there is no requirement as to how a doctree's child order must be embedded
into it.

## equivalent hierarchies

Note that equivalent hierarchies of traces can be formed using the reversed
pre-order traversal (Hncr), the default post-order traversal (Hcin), and
even the reversed post-order traversal (Hcrn). Despite that, the focus in
the context of this discussion will remain on the default pre-order doctree
traversal (Hpre, aka. Hnci).

* Hcrn := the (reversed) child order follwed by its parent node
* (n) denotes the visit-order of each node, (c) denotes its child order
* (i) the in-order child order, (r) the reversed child order
