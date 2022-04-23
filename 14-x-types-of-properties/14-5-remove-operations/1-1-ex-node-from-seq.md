
<!-- ======================================================================= -->
# example - remove a node from a sequence

```
s* := remove(s,2)
==============================================
s := (1,2,3)   =>   s \ (2)   =>   s* := (1,3)
```

In the context of an odered sequence we usually remove one element at a time.
The scope of that operation can therefore be understood as having the trivial
suborder of the ordered sequence as its base order. Because of that, the
operation may be described as **an element-based removal**.

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 3 ) \ ( 2 ) = ( 1 -> 3 )
     |----->|
```

Since the focus of this discussion is on ordered sequences, and since such
sequences correspond with ordered sets of elements, one can look at this type
of removal from **an order-based perspective**. That is, this operation can
be described to return a suborder `S*(U,<)` by removing an induced suborder
`R(T,<)` from an input order `S(V,<)`.

* `S := (V,G)` where `V := E(s)` and ...
* `G := (a < b) := aPb := { (1,2), (1,3), (2,3) }`
* `R := (T,<)` where `T := {2}`

Recall that each ordered set (defined by an order operator) can be understood
to be associated with an order relation (defined as an endo-relation). Because
of that, the removal of an element from an ordered set can be described in
regards to the order's order relation.

* `S* := (U,G*)` where `U := (V \ T) := {1,3}` and ...
* `G* := (a < b) := aPb := { (1,3) }` for `(a,b in U)`

The to-be-removed elements in `T` can be understood to first be removed from
the set of elements `V`. After that, those edges that have an endpoint in `T`
need to be removed from `G(S)`. That is because the remaining elements in `U`
can not remain related to any element in `T`.
