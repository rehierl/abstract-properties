
<!-- ======================================================================= -->
# total order

An ordered set `P := (V,R)`, which is a (simple) partial order and also
**connex**, can be said to be associated with a **(simple) total order**
relation. Because of that, the ordered set can itself be described as a
(simple) total order, or as a **(simple) toset** (i.e. a (simple) totally
ordered set).

* any (simple) total order is a connex simple partial order

An ordered set `P := (V,R)`, which is a strict partial order and also
**trichotomous**, can be said to be associated with a **strict total order**
relation. Because of that, the ordered set can itself be described as a strict
total order, or as a **strict toset** (i.e. a strict totally ordered set).

* any strict total order is a strict connex partial order
* any strict total order is a trichotomous partial order

Note that any total order is, as a specialized partial order, **acyclic**.

<!-- ======================================================================= -->
## remarks

Any non-empty total order has ..

* one and only one connected component.
* one and only one source vertex.
* one and only one sink vertex.

Note that, since any total order has one and only one source vertex, and since
a total order is required to be directional/oriented, the transitive reduction
of any total order can be visualized as a path graph. Because of that, and
since a path graph is considered "linear" (as in one continuous line), any
total order can be described as a **linear order**, or simply as a **loset**.

<!-- ======================================================================= -->
## connex, trichotomous

A **connex** order relation is such that, for any pair of vertices `(a,b in V)`
either the edge `aRb` and/or the edge `bRa` does exist.

* connex := `aRb` and/or `bRa` is true for any `(a,b in V)`

Note that any connex order relation is reflexive. Also any vertex is connected
to every other vertex. (Recall that an order relation is required to be
transitive). Put differently, a connex order relation has no disconnected
vertices.

Note that "and/or" in the definition of "connex", and in the context of a
(simple) total order, is **in effect an "ex-or"**. After all, even a (simple)
total order is still required to be a (simple) partial order, which must be
anti-symmetric, which is why "and" does not apply in regards to total orders.

A **semi-connex** order relation is such that, for any pair of *distinct*
vertices `(a,b in V)` either the edge `aRb` and/or the edge `bRa` does exist.

* semi-connex := `aRb` and/or `bRa` is true for any `(a != b)`

Note that a semi-connex order relation may or may not be reflexive. That is,
loops are allowed, but not required.

A **trichotomous** order relation is such that, for any pair of vertices one,
and only one of the following must be true: `aRb`, `bRa`, `(a == b)`.

* trichotomous := `aRb` ex-or `bRa` ex-or `(a == b)`

Note that a trichotomous order relation is required to be irreflexive. That
is, an trichotomous order relation is not allowed to have any loops at all.
Other than that, each vertex is still required to be connected.

<!-- ======================================================================= -->
## lower-than (<), lower-than-or-equal (<=)

```
s := (1, 2, 3, 4, 5, 6)
```

Given the above (ordered) sequence of natural numbers (or ordinal numbers
such as index numbers), a toset `P := (S,<=)` can be formed, if the oder
operator is defined based upon the lower-than-or-equal comparison operation
between numbers:

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
