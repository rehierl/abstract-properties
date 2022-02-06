
<!-- ======================================================================= -->
# downward-/upward-total orders

Given a subset of integers `I:[a,b]`, and from a value-based point of view,
one can state that, in order to move one step towards (b) from some current
element (i) one needs to **increase/up** the value of (i) by one. One can
therefore state that the orientation of the edges is **upwards**.

Conversely, one can state that, in order to move one step towards (a) from
some current element (i) one needs to **decrease/down** the value of (i) by
one. Based on that one can state that moving against the orientation fo the
edges is **downwards**.

* `(a related-to b) := (a < b) or (b < a)`
* `(a downwards-to b), (b upwards-to a) := (a < b)`

Note that "down/up" is thus analogous to "presequent/subsequent".

* `(a downwards-to b) <=> (a presequent-to b)`
* `(b upwards-to a) <=> (b subsequent-to a)`

<!-- ======================================================================= -->
## parallel sub-components

```
(a presequent-to b)
====================
s1 ->|-> s2 ->|-> s4
     |-> s3 ->|
```

Recall that the transitive reduction of a partial order may in general contain
subcomponents which can be considered "parallel".

* (see/ order theory / poset-src-snk)

<!-- ======================================================================= -->
## downward total poset (non-standard)

```
                             |-D(s)-partial--|
|-A(s)-total---------|       | |-> .. -> ..  |
| r(s) -> .. -> p(s) |-> s ->|-|->           |
|--------------------|       | |-> .. -> ..  |
                             |---------------|
                                   c(s)  l(s)
```

A partial order P(V,<) is **downward-total**, if the following condition is
met for all possible combinations of elements (a,b,c in V).

* if (a < c) and (b < c), then also (a related-to b)

In words: A partial order is described as downward-total, if the subset of
all those elements that are **presequent** to a given element (i.e. `A(s)`)
is a total suborder of elements.

* total against the edges, towards a root
* each node has one root node only

Note that, in the above parallel sub-component, s2 and s3 are both presequent
to s4. Because of that, the above partial order is not downward-total.

* disallows "parallel subcomponents"

<!-- ======================================================================= -->
## upward total poset (non-standard)

```
|-A(s)-partial-|
| .. -> .. ->| |       |-D(s)-total----------|
|          ->|-|-> s ->| c(s) -> .. -> ls(s) |
| .. -> .. ->| |       |---------------------|
|--------------|
```

A partial order P(V,<) is **upward-total**, if the following condition is met
for all possible combinations of elements (a,b,c in V).

* if (a < b) and (a < c), then also (b related-to c)

In words: A partial order can be described as upward-total, if the subset of
all those elements that are **subsequent** to a given element (i.e. `D(s)`)
is a total suborder of elements.

* total with the edges, towards a leaf
* each node has one leaf node only

Note that, in the above parallel sub-component, s2 and s3 ar both subsequent
to s1. Because of that, the above partial order is not upward-total.

* disallows "parallel subcomponents"

<!-- ======================================================================= -->
## total orders

```
|-A(s)-total---------|       |-D(s)-total----------|
| r(s) -> .. -> p(s) |-> s ->| c(s) -> .. -> ls(s) |
|--------------------|       |---------------------|
```

A total order P(V,<) is both downward- and upward-total. However, the
description as "downward- and upward-total" is insufficient to force
all pairs to be connected.

```
a partial, but not a total order
==================================
(r1 -> .. -> l1), (r2 -> .. -> l2)
```

Note that a collection of ordered sequences is both downward- and upward-total.
Despite that, the collection is not overal total since it does contain nodes
that are incomparable with each other (e.g. neither `(r1 < l2)` nor `(l2 < r1)`
is true).
