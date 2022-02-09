
# hierarchy of edges (He)

```
T <-> He
```

A tree (T) of **two or more nodes** can be used to form a hierarchy of edges
(He) - in essence, a tree's set of edges E(T) - such that the source tree
can be recreated based on the relationships between the edges in it. That is,
each tree is isomorphic to a hierarchy of edges, which will be referred to as
**the T-He isomorphism**.

Note that a hierarchy of edges (He) is defined as a setup of 2-element strings
such that the related-to operator is defined based on **being able to form a path**
over the edges in it. Two edges are thus related, if a path can be formed that
has the source node of one edge as its own source, and the sink node of the
other edge as its own sink.

Note that two edges in a hierarchy are either related (RE), disjoint (DI)
ex-or overlap each other (OV). That is, a hierarchy of edges is a specialized
**RE-DI-OV** based setup since the "unrelated" case may be one of the other
two cases (i.e. not just one).

Note that this type of hierarchy is **unlike any previous hierarchy** since
the elements in it are considered to be related with each other, even though
none is embedded into the other. This is in contrary to a scope being a subset
to an ancestor, a tree being a subtree to an ancestor, and a rooted path being
a superstring to an ancestor.

Note that the T-He isomorphism is inteded to underline that a hierarchy of
elements is itself **not required to be hierarchical**. That is because, a
hierarchy is only intended to be such that it can be formed from a tree in
such a way that it allows to recreate the source tree. That is, hierarchies
are intended to denote an equivalence relationship between trees and sets
of more or less complex elements.

## the He-Hrp isomorphism

```
T <-> He <-> Hrp
|<------------>|
```

A hierarchy of edges (He) is isomorphic to a hierarchy of rooted paths (Hrp) of
two or more paths. After all, the set of rooted paths over a tree (T) cover all
the edges in it.
