
<!-- ======================================================================= -->
# intervals over posets

As mentioned in the recap of basic mathematical concepts, intervals over (real)
numbers define subsets of numbers. Based on which strings over (simple) sequences
can be defined.

* `i := [a,b] := { x | (a <= x <= b) }`
* `i := { x | (a <= x) } & { x | (x <= b) }`
* `i := [a,*] & [*,b] := (A & B)`

More accurately, each interval defines two subsets of numbers: (1) a subset `A`
that consists of those numbers that are grater than (or equal) to the lower
endpoint `a`, and (2) a subset `B` that consists of those numbers that are
lower than (or equal) to the interval's upper endpoint `b`. The set of numbers
an interval represents is then formed as the intersection between those two
subsets - i.e. `(A & B)`. As such, the resulting subset of numbers an interval
represents consists of those numbers that are either equal to one or both of
the endpoints (if applicable), or any numbers in between.

Based on that, intervals can be used in the context of any ordered set which
supports a notion of "greater-than" and/or "lower-than". That is, an interval
can be defined in the context of simple `P := (V,<=)` and strict `Q := (V,<)`
posets. After all, the default sequence/edge-based semantics can be understood
to always apply.

* `(a < b) := (a presequent-to b) := aPb`
* `(a <= b) := (a presequent-to b) or (a equal-to b)`

This perspective on intervals over numbers can be generalized even futher since
the subset of numbers an interval represents isn't just understood to define
a simple unordered set of elements. That is because the relationships between
the numbers in an interval (i.e. in the subset of numbers it represents) can be
understood to be preserved.

An interval can therefore be understood to represent an induced suborder to the
ordered set from which its elements were taken. As such, an interval can be seen
as an order-embedding - i.e. a function that is order-preserving.

Because of that, an interval can more accurately be understood to correspond with
**an induced suborder** `Q(V,<=)` that was formed based upon a known superorder
`P(V,<=)`. That is, intervals can be defined as the restriction of a super-order
(i.e. restricted to those elements that are located in between the endpoints of
an interval). Consequently, an interval-based syntax can be used to efficiently
define (induced) suborders.

* `P[a,b] := P[T]` where `T := { x | (a <= x <= b) }`

Note that an induced subtree `T[r]` can be understood to be defined based upon
an interval. That is, an induced subtree denotes the induced suborder `T[r,*]`
in regards to a known node tree `T`. Based on that, the following syntactic
simplification can be defined:

* `P[a] := P[a,*]`
