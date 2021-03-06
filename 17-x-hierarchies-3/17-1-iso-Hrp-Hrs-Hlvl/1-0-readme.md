
# Hlvl - a hierarchy of level values

```
Hrp <-> Hrs <-> DT
|<---- Hlvl ---->|
```

Recall that a document tree (DT) is isomorphic to a hierarchy of rooted paths
(Hrp), if the doctree's child order is embedded into the sequence of rooted
paths (e.g. if serialized in pre-order). In addition to that, a hierarchy of
rooted paths (Hrp) is isomorphic to a hierarchy of reversed scopes (Hrs).

Since a hierarchy of rooted paths (Hrp), as a sequence of rooted paths, can
be transformed into a sequence of level values by replacing each rooted path
by the number of nodes in it, the resulting sequence of level values will be
referred to as the hierarchy of level values **Hlvl**, even though Hlvl is
itself not hierarchical. Since Hrp can also be formed from Hlvl, one can
speak of **the Hrp-Hlvl isomorphism**, or **the Hrs-Hlvl isomorphism**.

Note that forming a document tree (DT) from a hierarchy of rooted paths (Hrp),
or from a hierarchy of reversed scopes (Hrs), or from a hierarchy of level
values (Hlvl) is a **backwards-oriented** process. That is because one must
compare the current information with previous information (i.e. the knowledge
base) in order to determine the parent of the current node.
