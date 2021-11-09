
# hierarchy of trees

```
T <-> Ht
```

A tree (T) allows to form a hierarchy of induced subtrees (Ht) such that the
source tree can be recreated from the relationships between these trees. That
is, each tree is isomorphic to a hierarchy of subtrees. Because of that, this
isomorphism may be referred to as **the T-Ht isomorphism**.

Note that, since the set of nodes of an induced subtree is equal to the scope
of the subtree's root, the T-Ht isomorphism can be understood to already be
covered by the T-Hs isomorphism. That is because the definition of the input
tree and all of its induced subtrees is embedded into the scopes and the
relationships between them in Hs.

Note that the induced subtree that has the source tree's root as its root is
an element in the hierarchy of induced subtrees. That is, the source tree is
itself an element in Ht. Because of that, this hierarchy is far from minimal
in regards to the amount of information that is embedded into it.

Note that the T-Ht isomorphism is intended to showcase that a tree can be
isomorphic to a hierarchy of complex elements. That is, the elements in a
hierarchy are in general not required to be a atomic values, or simple sets
of elements.

## the Hs-Ht isomorphism

```
T <-> Ht <-> Hs
|<----------->|
```

Since a tree is isomorphic to a hierarchy of scopes (T-Hs) and also isomorphic
to a hierarchy of subtrees (T-Ht), one can conclude that a hierarchy of scopes
(Hs) is itself isomorphic to a hierarchy of subtrees (Ht). After all, a scope
and all of its subsets in Hs can be described as a sub-hierarchy of scopes,
and therefore to hold the definition of the corresponding induced subtree.

Note that the Hs-Ht isomorphism is inteded to underline that the hierarchy of
scopes Hs can itself be understood to be hierarchical.
