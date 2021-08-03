
<!-- ======================================================================= -->
# total order

A ordered set `P := (V,R)` which is a (simple) partial order and, in addition
to that also **connex** can be described as an ordered set that is associated
with a **(simple) total order** relation. Based on that, the ordered
set can itself be described as a (simple) total order, or as a
**(simple) toset** (i.e. a (simple) totally ordered set).

* a (simple) total order is a connex simple partial order

A ordered set `P := (V,R)` which is a strict partial order and, in addition
to that also **trichotomous** can be described as an ordered set that is
associated with a **strict total order** relation. Based on that,
the ordered set can itself be described as a strict total order, or as a
**strict toset** (i.e. a strict totally ordered set).

* a strict total order is a connex strict partial order
* a strict total order is a trichotomous partial order

<!-- ======================================================================= -->
## remarks

* Any total order consists of one connected component.
* Any total order has one and only one source vertex.
* Any total order has one and only one sink vertex.
* Any total order is acyclic (i.e. no cycles at all).

Note that, since any total order has one and only one source vertex, and since
a total order is required to directional/oriented, the transitive reduction of
any total order is a path graph. Because of that, and since a path graph is
considered "linear" (as in one continuous line), any total order can be
described as a **linear order**, or simply as a **loset**.

<!-- ======================================================================= -->
## connex, trichotomous

A **connex** order relation is such that, for any pair of
vertices `(a,b in V)` either the edge `aRb` and/or the edge `bRa` does exist.

* connex := `aRb` and/or `bRa` is true for any `(a,b in V)`

Note that any connex order relation is reflexive. Also any vertex is connected
to every other vertex. (Recall that an order relation is required to be
transitive). Put differently, a connex order relation has no disconnected
vertices.

A **semi-connex** order relation is such that, for any pair of *distinct*
vertices `(a,b in V)` either the edge `aRb` and/or the edge `bRa` does exist.

* semi-connex := `aRb` and/or `bRa` is true for any `(a != b)`

Note that a semi-connex order relation may or may not be reflexive. That is,
loops are allowed, but not required.

A **trichotomous** order relation is such that, for any pair of vertices one,
and only one of the following must be true: `aRb`, `bRa`, `(a == b)`.

* semi-connex := `aRb` ex-or `bRa` ex-or `(a == b)`

Note that a trichotomous order relation is required to be irreflexive. That
is, an trichotomous order relation is not allowed to have any loops at all.
Other than that, each vertex is still required to be connected.

<!-- ======================================================================= -->
## lower-than (<), lower-than-or-equal (<=)

```
s := (1, 2, 3, 4, 5, 6)
```

Given the above (ordered) sequence of natural numbers, a toset `P := (S,<=)` can
be formed, if the oder operator is defined based upon the lower-than-or-equal
comparison operation between numbers:

```
1° -> 2° -> 3° -> 4° -> 5° -> 6°
```

Similar to that, a strict toset can `P := (S,<)` can be formed, if the order
operator is defined based upon the lower-than comparison opertion between
numbers:

```
1 -> 2 -> 3 -> 4 -> 5 -> 6
```

Note that the definition of the above operators build upon the values of the
natural numbers, not on the index-order that is defined by the sequence.

<!-- ======================================================================= -->
## cyclic, acyclic

Recall that any strict/irreflexive preorder is acyclic. In contrary to that,
a simple preorder may contain one or more cycles.

Since a total order, simple or strict, is now required to have no pairs of
"flipped" edges, cycles are effectively required to not exist. That is because
the transitivity would otherwise result in such pairs of "flipped" edges.

Consequently, **any total order is acyclic**.

Note that a cycle graph (i.e. a path graph whose endpoints are connected with
each other), be it directed or not, does not represent a total order.
