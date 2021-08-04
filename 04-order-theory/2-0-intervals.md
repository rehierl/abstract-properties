
a generalized perspective on intervals
- point out that an interval defines
  a subset of elements
- a subset that can be used to induce
  a suborder
- i.e. an interval can be understood
  to define an induced suborder
- i.e. intervals can be used to efficiently
  describe suborders

intervals (2)
- any interval requires an known set of elements
- with that set, a known order must be associated, since
  otherwise one would not know what is in between both
  of the endpoints and therefore not which elements to
  include in the set an interval defines/describes
- similar to intervals based upon total orders/numbers,
  intervals can be defined based upon partial orders
- i.e. based upon the order's order operator
- what about sub-intervals of equal/incomparable elements?

generalization
- each interval specifies a subset of elements
- based upon an ordered set of elements
- each interval specifies an ordered subset

intervals (3)
- "hierarchy of nested intervals/sets" - somehow redundant
  not quite - if "nested" applies to all, then total
  hierarchy of (possibly nested) intervals, then partial
  must be the default

Note that each interval can be understood to correspond with an ordered subset
of elements. Because of that, any scope can be understood to correspond with
**an ordered (sub)set of nodes**.

Note that each an interval of the form `[a,*]` can be understood to correspond
with a **suffix** in regards to the underlying node order, regardless of whether
the node order is total or not. Likewise, an interval of the form `[*,b]` can
be described as a **prefix**.
