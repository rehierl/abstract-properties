
<!-- ======================================================================= -->
## containment order

An order that is defined based upon a family of sets (i.e. a set whose elements
are themselves sets), and whose order relation is defined based upon the subset
containment (i.e. based upon the subset-of or superset-of comparison operators)
can be described as **a containment order**.

<!-- ======================================================================= -->
## containment order vs. cyclic/acyclic

Except for possible loops, a containment order is **inherently acyclic**.

For such a relation to have a cycle (note - of two or more sets), a set `a`
would have to be a subset to another set `b` (note - both are distinct), which
is why `(a subset-of b)` and `(#a < #b)` is then true.

However, in order to establish a cycle, `a` would also have to be a superset
to `b`. This can however never be true since `a` would then also need to have
one or more elements in addition to those in `b`.

The resulting conflict is therefore that a set can not have fewer and, at the
same time, more elements than another set. Because of that, a set can not be
a subset and a superset to another set.

Consequently, an order that is defined based upon the (strict-) subset-of
comparison operator, or an order that corresponds with such an order, can
not have any cycles and is therefore acyclic.

<!-- ======================================================================= -->
## poset <-> containment order

Every poset is isomorphic to (aka. corresponds with) a containment order.

containment order
- given poset a P = (X,<=)
- associate to each (b in X) the set
- X(b) = { a | (a <= b) for (a in X) }
- transitivity ensures that
- (X(a) subset-of X(b)) if (a <= b)
