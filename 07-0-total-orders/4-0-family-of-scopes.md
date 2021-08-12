
<!-- ======================================================================= -->
# a family of scopes

It should be obvious at this point, that not any family of sets can be said to
correspond with an actual order of elements and thus to also correspond with an
ordered sequence.

```
S  := { s1, s2, s3, s4, s5, s6 }
--------------------------------
s1 := { n1, n2, n3, n4, n5, n6 }
s2 := {     n2, n3, n4, n5, n6 }
s3 := {         n3, n4, n5, n6 }
s4 := {             n4, n5, n6 }
s5 := {                 n5, n6 }
s6 := {                     n6 }
```

<!-- ======================================================================= -->
## css(si), ce(si)

If any set `si` is related to every other set `sj` in `S`, one can say that
`si` contains a subset of those elements `css(si)` that are no elements in
any of the subsets of `si`. Because of that, these subsets can be referred
to as **the characteristic subset css(si)** of `si`.

* `css(si) := si \ { (nj in sj) | (sj proper-subset-of si) }`

Since no element in `css(si)` is also an element in any of the subsets of `si`,
any element in `css(si)` is unique to `si` in regards to its subsets. Because
of that, each of these elements can be referred to as
**a characteristic element** of `si`.

Note that any characteristic element of set `si` allows to distinguish `si`
from all the other sets in `Si`. That is because, no subset of `si` contains
any element in `css(si)`. In contrary to that, and even though the supersets
of `si` also contain these elements, `si` is the smallest set (in terms of
the number of elements) that still contains these elements.

In case `css(si)` has one and only one characteristic element, that element
can be referred to as **the chracteristic element ce(si)** of `si`.

* `ce(si) := oneOf(css(si))`, iff `(#css(si) == 1)`

<!-- ======================================================================= -->
## requirements

For an arbitrary set of sets of elements `S` to correspond with an ordered
sequence of elements, the following requirements must be met:

(**1**) Since the intention of such a family of sets is to ultimately form an
order of elements, any set must be required to be non-empty. That is because
(1) the empty set is a subset to every other set, and (2) each set needs to
contain at least the element it is supposed to represent.

(**2**) Any two distinct sets `si` and `sj` in `S` must be related under the
subset-of comparison operator. Otherwise it would not be possible to
determine the relationship between the sets.

Since all sets are required to be non-empty, and since all pairs of distinct
sets are required to be properly related, one can conclude that no set in `S`
has a characteristic subset `css(si)` that is empty.

(**3**) Even though it is not an absolute necessity, each set in `S` is expected
to have a chracteristic element `ce(si)`. That is, all characteristic subsets
are expected to be 1-element subsets.

Since each `css(si)` has one element only, one can determine the `ce(si)` of
each set in `S`. Because of that, one can use these elements to represent the
corresponding set `si`.

Any family of sets that satisfies all of the above requirements can be referred
to as **a family of scopes**. As such, each family of scopes is **isomorphic**
to a strict total order of characteristic elements.
