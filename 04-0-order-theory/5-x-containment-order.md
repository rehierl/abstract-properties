
<!-- ======================================================================= -->
## containment order

An order that is defined based upon a family of sets (i.e. a set whose elements
are themselves sets of elements), and whose order relation is defined based
upon the containment of subsets (i.e. based upon the subset-of or superset-of
comparison operator) can be described as **a containment order**.

<!-- ======================================================================= -->
## containment order vs. cyclic/acyclic

Except for possible loops, a containment order is **inherently acyclic**.

For such a relation to have a cycle (note - of two or more sets), some set `a`
would have to be a subset to another set `b` (note - both are non-empty and
distinct), which is why `(a subset-of b)` and `(#a < #b)` is then true.

However, in order to establish a cycle, `b` would then also have to be a
subset to `a`. This can however never be true since `a` would then also
need to have one or more elements in addition to those elements in `b`.

The resulting conflict is therefore that a set can not have fewer and, at the
same time, more elements than another set. Because of that, a set can not be
a subset and a superset to another set.

Consequently, an order that is defined based upon the subset-of comparison
operator, or an order that corresponds with such an order, can not have any
cycles and is therefore "inherently" acyclic.

<!-- ======================================================================= -->
## poset <-> containment order

Since a containment order is oriented and may have elements that are
incomparable with each other (i.e. disjoint sets, overlapping sets), any
containment order is **a partial order**. However, depending on the specific
characteristics (i.e. all sets are related), the order relation of a porper
containment order **may still be total**.

Given a poset `P := (V,<=)`, a proper containment order `S := (T,<=)`
can be formed as follows.

* each vertex `(s in T)` is a subset of vertices in `P(V)` such that
* `s := { b | (a <= b) }`
* i.e. `a` and every other vertex subsequent to it in `P`
* `(s <= t) := (s superset-of t)` for `(s,t in T)`

Note that transitivity will ensure that this mapping is order-preserving. Also,
subsequent discussions will proof that this process can be reversed. That is,
the resulting containment order (aka. an order over a family of scopes) can be
used to reliably re-create the initial/source poset.

As a consequence, **any poset corresponds with a containment order**.

Based on that, any order that is order-isomorphic to a containment order,
can itself be (loosely) described as a containment order. If need be, one can
distinguish between an order that "corresponds with a containment order" and
one that is "an actual/proper containment order".
