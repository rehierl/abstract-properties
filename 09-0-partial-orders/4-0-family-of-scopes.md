
<!-- ======================================================================= -->
# a family of scopes

It should be obvious at this point, that not any family of sets corresponds
with a partial order of elements and also with a node tree.

```
s1 := s(p1) := { n1, n2, n4, n5, n3 } = E(T)
s2 := s(p2) := {     n2, n4, n5     } = [ni,*]
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

Note that the following content must be understood as an introduction to the
concept of "families of scopes". More details on that topic will follow.

<!-- ======================================================================= -->
## css(si), ce(si)

In a family of sets `S`, which is assumed to have no pair of overlapping sets,
any set `si` contains a subset of those elements `css(si)` that are no elements
in any of the subsets of `si`. Because of that, such a subset can be referred
to as **the characteristic subset css(si)** of `si`.

* `css(si) := si \ { (nj in sj) | (sj proper-subset-of si) }`

Since no element in `css(si)` is also an element in any of the subsets of `si`,
any element in `css(si)` is unique to `si` in regards to its subsets. Because
of that, each of these elements can be referred to as
**a characteristic element** of `si`.

Note that any characteristic element of set `si` allows to distinguish `si`
from all the other sets in `S`. That is because, no subset of `si` contains
any element in `css(si)`. In contrary to that, and even though the supersets
of `si` also contain these elements, `si` is the least significant set (in
terms of the number of elements) that still contains these elements.

In case `css(si)` has one and only one characteristic element, that element
can be referred to as **the chracteristic element ce(si)** of `si`.

* `ce(si) := oneOf(css(si))`, iff `(#css(si) == 1)`

In case there is a set `si` that has more than one characteristic element,
one can assume that these subsets are replaced by some unique identifier.
Hence, a mapping can be defined that allows to resolve that id. Because of
that, any characteristic subset can be **normalized** to one element only.

<!-- ======================================================================= -->
## requirements

For an arbitrary family of sets `S` to correspond with a poset,
all of the following requirements must be met:

(**0**) `S` must be non-empty.

(**1**) Since such a set of sets must allow to form an order of elements, each
set in it must be required to be **non-empty**. That is because (1) the empty
set is a subset to every other set, and (2) each set needs to contain at least
the element it is supposed to represent.

(**2**) Any pair of distinct sets `si` and `sj` in `S` must be such that both
sets are **either disjoint ex-or related** (in short **DI ex-or RE**) under
the proper-superset-of comparison operator.

Note that, even though all sets are required to be non-empty, and since all
pairs of sets are required to be DI ex-or RE, *one can not conclude* that
every set in `S` has a non-empty characteristic subset `css(si)`. That is
because a set `si` may still exist that is equal to the union of pairwise
disjoint subsets.

* `(#css(si) == 0)` could be true for some `(si in S)`

(**3**) Since characteristic subsets may still exist that could be empty, each
set must be required to have one and only one characteristic element. That is,
all characteristic subsets are required to be 1-element subsets.

* `(#css(si) == 1)` is required

Since each `css(si)` is now required to have one and only one element, one can
determine the `ce(si)` of each set `si` in `S`. Because of that, one can use
these elements as an identifier of the corresponding set.

* `ce(si)` is required to be defined for all `(si in S)`

Any family of sets that satisfies the above requirements can be referred
to as **a (partial) family of scopes**. As such, each family of scopes is
**isomorphic** to a strict partial order of characteristic elements.

(**4, optional**) A family of scopes may be required to have a "root" set `si`
such that every other set `sj` is a subset to it. If that requirement is met
in addition to the above requirements, then the family corresponds with
**a single node tree**. Otherwise, the family of scopes corresponds with
**a forest of node trees**.

A set `si` in a family of sets `S` may be described as **a root set**,
if it is no subset to another set `sj` in `S`.

Note that, defined as such, a root set corresponds with the order-based
defintion of a minimal element: "is no subset" is equivalent to "is not greater
than". Based on that, a family of sets is required to have a least element, if
it is to correspond with a single node tree.
