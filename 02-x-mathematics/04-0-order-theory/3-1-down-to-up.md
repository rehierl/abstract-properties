
<!-- ======================================================================= -->
# the meaning of "down" and "up"

In mathematics the focus is on sets of numbers, which is why orders are in
general ordered sets of numbers `P(V,<)`. Furthermore, the edges of such
number-based ordered sets are such that they are oriented from numbers whose
values are smaller towards numbers that are larger. That is, an edge exists
between numbers `a` and `b` if, and only if the value of `a` is smaller (<)
than the value of `b`:

* `(a < b), aEb` := "the value of (a) is smaller than the value of (b)"

Because of that, definitions in mathematics are in general based on the
values of numbers, rather than based on the abstract relationship between
these numbers.

For example, given the subset of integers `I:[a,b]`, then (a) is the least
element (i.e. the number with the smallest value) and (b) the greatest element
(i.e. the number with the largest value).

However, provided that the edges are always always oriented towards those
elements whose values are greater than the value of some current element, then
one can describe the edges as being oriented towards those elements that are
subsequent to the current element.

* `(a < b), (a -> b) := (b subsequent-to a)`
* `(a related-to b) := (a < b) or (b < a)`

Given a subset of integers `I:[a,b]`, and from a value-based point of view,
one can state that, in order to move one step towards (b) from some current
element (i) one needs to **increase/up** the value of (i) by one. Consequently,
one can state that the orientation of the edges is **upwards**.

Conversely, one can state that, in order to move one step towards (a) from
some current element (i) one needs to **decrease/down** the value of (i) by
one. Based on that one can state that moving against the orientation fo the
edges is **downwards**.

* `(a downwards-to b), (b upwards-to a) := (a < b)`

Note that "down/up" is thus analogous to "presequent/subsequent".

* `(a downwards-to b) <=> (a presequent-to b)`
* `(b upwards-to a) <=> (b subsequent-to a)`
