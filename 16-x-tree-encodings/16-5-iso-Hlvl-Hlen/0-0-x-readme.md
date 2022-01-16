
# the isomorphism between level and length values

As was shown in previous sections, several different encodings are possible.
Furthermore, the implementation of each encoding greatly depends on the tree
traversal algorithm that was used to produce a specific encoding. And finally,
variations are in general possible when implementing an encoding.

Due to the plethora of available options, which can not all be covered, it is
essential to understand the core concept behind each encoding. The following
section will therefore **focus on** the pre-order versions of the level- and
length-based encodings in order to recap the core aspects of both encodings.

Note that the intent behind this restricition is to simplify discussions by
reducing the amount of variations one needs to keep in mind.

Note that, from this point forward, the **pre-order** traversal will be assumed
as the default traversal algorithm. Hence, this particular tree traversal will
be mentioned explicitly only for clarification purposes.

## Hlvl - a hierarchy of level values

```
Hrs <-> Hrp <-> Hlvl
|<------Tree------>|
```

Recall that a document tree (DT) is isomorphic to a hierarchy of rscopes (Hrs,
reversed scopes), if the doctree's child order is embedded into the sequence
of rscopes (e.g. Hrs serialized in pre-order). In addition to that, a hierarchy
of rscopes (Hrs) is isomorphic to a hierarchy of rooted paths (Hrp).

Since a hierarchy of rooted paths (Hrp), as a sequence of rooted paths in
pre-order, can be transformed into a sequence of level values by replacing
each rooted path by the number of nodes in it, the resulting sequence of
level values will be referred to as the hierarchy of level values **Hlvl**,
even though Hlvl is itself not hierarchical. Likewise, Hrp can be formed
from Hlvl, which is why one can speak of **the Hrp-Hlvl isomorphism**.

## Hlen - a hierarchy of length values

```
Hs <-> Hpre <-> Hlen
|<------Tree------>|
```

Recall that a document tree (DT) is isomorphic to a hierarchy of scopes (Hs),
if the doctree's child order is embedded into the sequence of scopes (e.g. Hs
serialized in pre-order). In addition to that, a hierarchy of scopes (Hs) is
isomorphic to a hierarchy of pre-order traces (Hpre).

Since a hierarchy of pre-order traces (Hpre), as a sequence of traces in
pre-order, can be transformed into a sequence of length values by replacing
each trace by the number of nodes in it, the resulting sequence of length
values will be referred to as the hierarchy of length values **Hlen**, even
though Hlen is itself not hierarchical. Likewise, Hpre can be formed from
Hlen, which is why one can speak of **the Hpre-Hlen isomorphism**.

## the Hlvl-Hlen isomorphism, TODO

```
Hlvl <-> Hlen
```

Note that the DT-Hrs and DT-Hs isomophisms suggest that both hierarchies are
isomorphic to each other, which suggests that both can be transformed into one
another.
