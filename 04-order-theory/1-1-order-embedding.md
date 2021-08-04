
<!-- ======================================================================= -->
# ordered embedding

<!-- ======================================================================= -->
## todo

functions
- surjective, injrective, bijective
- reversible - an inverse exists

order-preserving
- (f: P -> Q) is order-preserving, if ..
  (x × y) <-> (f(x) × f(y)) for all (x,y in S)
- (f) must be injective
- history/future-preserving -> order-preserving
- see prefix order

history-preserving
- history - p* := { q | q <= p) }
- (f: P -> Q) is history-preserving, if ..
  and only if (f(p*) == f(p)*)
- note - rooted paths

future-preserving
- future - p+ := { q | p <= q }
- (f: P -> Q) is future-preserving, if ..
  and only if (f(p+) == f(p)+)

order isomorphism
- for (P,<=) and (Q,<=) an (f: P -> Q) can be defined such that (f) has an inverse
- i.e. an bijective mapping can be defined
- i.e. is order-preserving
- (f) is an order isomorphism, (P) and (Q) are order-isomorphic
- orders have the same "order type", if they are "order isomorphic"
- (P) and (Q) can be said to "correspond" with each other

order-embedding
- an order embedding is order-preserving
- a notion that is weaker than "oder isomorphism"
- an order-isomorphism is a surjective order-embedding
