
# abstract properties / total orders

This chapter describes transformations that transform one construct `ci` into
another construct `cj` such that the resulting construct `cj` can be transformed
back into `ci`.

Note that such a pair of transformations is understood to describe an
**isomorphism** between `ci` and `cj`. Based on that, constructs `ci` and `cj`
will be understood to be **isomorphic to** and also to **correspond with** each
other.

<!-- ======================================================================= -->
## isomorphisms

The isomorphisms described in this chapter can be visualized as follows.

```
s <-> p <-> Q <-> P <-> S
      |<--------->|
```

* `s` - **ordered sequences**
* `p` - path graphs of (distinct) nodes
* `Q` - total orders of nodes
* `P` - total orders of scopes
* `S` - (total) families of scopes

Note that, since `p` is isomorphic to `Q`, and since `Q` is isomorphic to `P`,
one can conclude that the existence of an isomorphism between `p` and `P` is
**a matter of consequence**. Because of that, future discussions may focus
on significant isomorphisms and may skip those that are less important to the
overall discussion.

Note that this chapter is excessive in the amount of transformations being
described, and intentionally inaccurate in regards to many explanations.
Because of that, this chapter is intended to introduce basic concepts of
what will be clarified in regards to partial orders.

<!-- ======================================================================= -->
## order of scopes <=> path graph, node order

When reading about the above correspondence between a path graph `s(N,E)` and
a strict total containment order of scopes `P(S,<)`, one might notice a core
aspect, which is to be highlighted below.

(1.1) From the containment order `P` a graph `G` can be formed by performing
a transitive reduction on the order relation of `P`.

(1.2) Since the set of vertices in `V(G)` is then still equal to the family of
scopes `V(P)`, each scope has to be replaced by its characteristic element
`ce(si)` such that the final graph `t` can be formed.

Since there is no real reason, as to why the transitive reduction has to be
performed first, one can in general flip the order of operations. That is, ..

(2.1) Beginning with the containment order `P`, an order of nodes `Q` can be
formed from the order relation of `P`, if each scope `(s in S)` is replaced by
its characteristic element `ce(s)`.

(2.2) From the node order `Q` a graph `u` can be formed by performing the
transitive reduction on the order relation of `Q`.

Since `t` and `u` are both equal to the initial path graph `s`, one can
conclude, that each path graph (of distinct nodes) `s` is **isomorphic to**
a containment order `P` and also to an actual node order `Q`. Consequently,
each path graph can be seen as the visual representation of a node order.
