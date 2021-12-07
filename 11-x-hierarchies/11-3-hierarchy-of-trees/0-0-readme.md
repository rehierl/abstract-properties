
# hierarchy of trees (Ht)

```
T <-> Ht
```

A tree (T) allows to form a hierarchy of induced subtrees (Ht) such that the
source tree can be recreated based on the relationships between its trees.
That is, each tree is isomorphic to a hierarchy of induced subtrees. Because
of that, this isomorphism will be referred to as **the T-Ht isomorphism**.

Note that, since the set of nodes of each induced subtree is equal to the scope
of its root, the T-Ht isomorphism can be understood to be already covered by
the T-Hs isomorphism. That is because the definition of the source tree and
all of its induced subtrees is embedded into the sets of nodes of the induced
subtrees in Ht, and the relationships between them.

Note that the induced subtree that has the source tree's root as its root is
an element in Ht. That is, the source tree T is itself a tree in Ht. Because
of that, a hierarchy of trees is anything but minimal in regards to the amount
of information it holds.

Note that the T-Ht isomorphism is intended to underline that a tree can be
isomorphic to a hierarchy of complex elements. That is, the elements in a
hierarchy are in general not required to be atomic values, or even simple
sets of elements.

## the Hs-Ht isomorphism

```
T <-> Ht <-> Hs
|<----------->|
```

A hierarchy of trees (Ht) is isomorphic to hierarchy of scopes (Hs). After all,
each induced subtree in Ht is isomorphic to a sub-hierarchy of scopes over Hs.

Note that the Hs-Ht isomorphism is intended to underline that the hierarchy of
scopes Hs is itself hierarchical.
