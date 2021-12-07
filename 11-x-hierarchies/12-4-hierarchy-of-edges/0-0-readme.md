
# hierarchy of edges (He)

```
T <-> He
```

A tree (T) of **two or more nodes** can be used to form a hierarchy of edges
(He) - in essence, a tree's set of edges `E(T)` - such that the source tree
can be recreated based on the relationships between the edges in it. That is,
each tree is isomorphic to a hierarchy of edges. Because of that, this
isomorphism will be referred to as **the T-He isomorphism**.

Note that a hierarchy of edges (He) is defined as a setup of 2-element strings
such that the related-to operator is defined based **being able to form a path**
over the hierarchy's edges. Two edges are thus related, if a path can be formed
that has the source node of one edge as its own source, and the sink node of
the other edge as its own sink.

Note that two edges in a hierarchy are either related (RE), disjoint (DI)
ex-or overlap each other (OV). That is, a hierarchy of edges is a specialized
**RE-DI-OV** based setup since the case of two edges being unrealted may be
one of the other two cases (i.e. not just one).

Note that this hierarchy is **unlike any previous hierarchy** insofar as the
elements in it are considered to be related with each other, even though none
is required to be embedded into the other. This is in contrary to a scope being
a subset to an ancestor, a tree being a subtree to an ancestor, and a rooted
path being a superstring to an ancestor.

Note that the T-He isomorphism is inteded to underline that a hierarchy of
elements is itself **not required to be hierarchical**. That is because, a
hierarchy is only intended to be such that it can be formed from a tree in
such a way that it allows to recreate the source tree. That is, hierarchies
are intended to denote an equivalence between trees and sets of more or less
complex elements.

Note that the main intent of the T-He isomorphism is therefore to highlight that
there is no substantial difference between a tree (expressed as a graph) and its
tree order (expressed as an order relation). That is, one must learn to accept
that both "express the same thing using **different syntactic rules**".

## the He-Hrp isomorphism

```
T <-> He <-> Hrp
|<------------>|
```

A hierarchy of edges (He) is isomorphic to a hierarchy of rooted paths (Hrp) of
two or more paths. After all, the set of rooted paths over a tree (T) cover all
the edges in it.
