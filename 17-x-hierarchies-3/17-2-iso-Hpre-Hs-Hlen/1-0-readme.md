
# Hlen - a hierarchy of length values

```
Hpre <-> Hs <-> Hlen
|<-------DT------->|
```

Recall that a document tree (DT) is isomorphic to a hierarchy of scopes (Hs),
if the doctree's child order is embedded into the sequence of scopes (e.g. Hs
serialized in pre-order). In addition to that, a hierarchy of scopes (Hs) is
isomorphic to a hierarchy of pre-order traces (Hpre).

Since a hierarchy of pre-order traces (Hpre), as a sequence of traces, can
be transformed into a sequence of length values by replacing each trace by
the number of nodes in it, the resulting sequence of length values will be
referred to as the hierarchy of length values **Hlen**, despite Hlen not
being hierarchical itself. Since Hpre can be formed from Hlen, one can speak
of **the Hpre-Hlen isomorphism**, or **the Hs-Hlen isomorphism**.

Note that scopes can be described as being **forwards-oriented** since each
scope relies upon the scopes of its descendants in order to determine the
characteristic element (CE) of a given scope. Hence the semantical orientation
of scopes can be described to be against the processing order. After all,
the knowledge that is available at a certain point in time is defined by
past events.
