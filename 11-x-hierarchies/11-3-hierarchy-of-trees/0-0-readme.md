
# hierarchy of trees (Ht)

```
T <-> Ht
```

A tree (T) allows to form a hierarchy of induced subtrees (Ht) such that the
source tree can be recreated based on the relationships between its trees.
That is, each tree is isomorphic to a hierarchy of induced subtrees, which
will be referred to as **the T-Ht isomorphism**.

Note that the induced subtree that has the source tree's root as its root is
an element in Ht. That is, the source tree T is itself a tree in Ht. Because
of that, a hierarchy of trees is anything but minimal in regards to the amount
of information it holds.

Note that the T-Ht isomorphism is intended to underline that a tree can be
isomorphic to a hierarchy of complex elements. That is, the elements in a
hierarchy are in general not required to be atomic values, or even simple
sets of elements.

## the Ht-Hs isomorphism

```
T <-> Ht <-> Hs
|<----------->|
```

A hierarchy of trees (Ht) is isomorphic to hierarchy of scopes (Hs). After all,
each induced subtree in Ht is isomorphic to a sub-hierarchy of scopes over Hs.

Note that the Ht-Hs isomorphism is intended to underline that the hierarchy of
scopes Hs is itself hierarchical.
