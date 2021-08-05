
<!-- ======================================================================= -->
# order embedding

The following can be understood to formalize the notion of a suborder that
is embedded into a super-order.

Recall the the overall focus of this discussion is on embedded suborders.

<!-- ======================================================================= -->
## history-, future-, order-preserving

A mapping between two orders `(f: P -> Q)` is said to be **history-preserving**,
if the following requirement is met:

* `(f(b*) == f(b)*)` where `b* := { a | aRb }`
* `b*` is said to be the "history" of `b`

Note that the rooted path of a `b` in a node tree can thus be described as
the node's "history" (or as its "context").

A mapping between two orders `(f: P -> Q)` is said to be **future-preserving**,
if the following requirement is met:

* `(f(a*) == f(a)*)` where `a* := { b | aRb }`
* `a*` is said to be the "future" of `a`

Note that the induced subtree `T[a]` can be described as the node's "future".

A mapping between two orders `(f: P -> Q)` is said to be **order-preserving**,
if the following requirement is met:

* `(a × b) <-> (f(a) × f(b))` for all `(a,b in P)`
* `(×)` represents the order-operator

Note that `f` must be injective. Also, any history-/future-preserving mapping
is order-preserving.

* `history-/future-preserving -> order-preserving`

<!-- ======================================================================= -->
## order-embedding

With the formalized definition of the order-preserving characteristic in mind,
one can describe a mapping between two orders as **an order-embedding**, if it
is order preserving.

Note that, in contrary to an order isomorphism, a mapping that is order-embedding
is not required to be right-total. After all, an induced subtree that is embedded
into a super-tree may be a proper subtree (i.e. smaller-than) to its supertree.
Based on that, the notion of order-embedding is weaker than that of an
order-isomorphism.

Based on the above, an **order-isomorphism** can be described as a surjective
(i.e. right-total) order-embedding.
