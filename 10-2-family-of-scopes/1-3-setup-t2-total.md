
<!-- ======================================================================= -->
## Strict/Proper setup (T2)

A set of sets `S` will be referred to as **a proper setup (of type-2)**,
if and only if the following requirements are met:

* (R1) `S` is a simple setup of sets
* (R2) Any two sets in `S` must be related.

Note that, since any two sets in such a setup are required to be related,
a total setup disallows any pairs of disjoint and any pairs of overlapping
sets. That is, a total setup covers the **RE only** case as described in
the remarks to simple setups. Because of that, such a setup may also be
described as **a total setup**.

Note that a total setup corresponds with a set of pairwise related sets.
That is, each set in a total setup is related to all the other sets.
Because of that, and for any pair of distinct sets `(s,t in S)` it can be
determined which is the subset and which the superset. That is, a total
setup is **a partial setup (T1)** which does not even have one pair of
disjoint sets.

<!-- ======================================================================= -->
## a visual impression

```
|-A-----------|       total-setup = {
| |-B-----|   |         A: { 1, 2, 3, 4 },
| | 1   2 |   |         B: { 1, 2, 3 },
| | |-C-| |   |         C: { 3 }
| | | 3 | | 4 |       }
| | |---| |   |
| |-------|   |
|-------------|
```

* Set A contains elements 1 to 4.
* Set B contains elements 1 to 3.
* Set C only contains element 3.

As before, elements may belong to more than one set:

* Elements 1 and 2 both belong to sets A and B.
* Element 3 belongs to sets A, B and C.
* Element 4 only belongs to set A.

<!-- ======================================================================= -->
## unique numbers of elements

```
                              |0     |
                    C -> ...  |      |
                 > /          |      |- (#x < #t)       for (x in C)
           A -> {t}           |#t    |
          /      < \          |      |- (#t < #x < #s)  for (x in D)
       > /          D -> ...  |      |
        /                     |      |- D(s) - subsets
S -> {s}                      |#s    |-----------------------------
      < \                     |      |- A(s) - supersets
         \          E -> ...  |      |
          \      > /          |      |- (#s < #x < #u)  for (x in E)
           B -> {u}           |#u    |
                 < \          |      |- (#u < #x)       for (x in F)
                    F -> ...  |      |
                              |+Inf  |
```

Given an arbitrary total setup `S` of two or more sets, then two distinct sets
`(s,t in S)` are required to be related with each other. That is, it can be
determined if `s` is a proper subset or a proper superset to `t`. Because of
that, `s` can not have the same amout of elements as `t`. Hence, `s` has either
more or fewer elements than `t`.

* for `(s,t in S)` and `(s != t)` ..
* `(s subset-of t) <-> (#s < #t)`

The sets in `(S\s)` can therefore be split up into a set `A` that contains all
the sets which have fewer elements than `s` (note - `D(s)`), and a set `B` that
contains all the sets which have  more elements than `s` (note - `A(s)`).
Consequently, `S` can be described as a union of three pairwise disjoint sets.

* `S := (A + {s} + B)` where ..
* `A := { t | (t in S\s) and (#t < #s) }`
* `B := { t | (t in S\s) and (#t > #s) }`

Since subsets `A` and `B` are themselves total sub-setups of `S`, the process
can be repeated recursively on subsets `A` and `B` until there is no more set
that remains in `S`.

Distinct sets in a total setup have therefore **distinct amounts of elements**.
That is, the number of elements in each set is **unique** to that set.

* `(#S == #N)` is true for `N := { #s | (s in S) }`

Since each set in a total setup has a unique number of elements, such a total
setup can be used to form a total order of sets `P(S,<)` such that the order
over the sets in it correpsponds with the number of elements in each set.

* `(a < b) := (a superset-of b)`, alt. `(a < b) := (#a > #b)`
* `(a < b) := (a subset-of b)`, alt. `(a < b) := (#a < #b)`

Note that one can describe a total setup as **an onion of sets** such that the
least significant set is at its core. Based on that, the onion can be described
to grow outwards by one or more elements with each next larger set.

<!-- ======================================================================= -->
## least/most significant (super)set

Given a partial setup `S` and a non-root set `(s in S)`,
then `s` is a subset to one or more other sets in `S`.
Because of that, **the set of all supersets** `A(s)` is non-empty.
One can thus form a sub-setup `T := (A(s) + {s})`.

Since `s` is a subset to each set in `A(s)`, and since no set in `S` is
allowed to overlap another set in `S`, all the sets in `T` are related
with each other. Consequently, `T` is **a total sub-setup** of `S`.

`T` therefore has a set `l` such that it is a subset to all the sets
in `(T\l)`. Consequently, `l` has the least amount of elements in `T`.
As such `l` can be described as **the least significant set** in `T`
that is **sub-ordinate** to all the other sets.

* `min(T) := l` such that `(#l < #t)` for all `(t in T\l)`
* `(l subset-of t)` for all `(t in T\l)`

Likewise, `T` has a set `m` such that it is a superset to all the sets
in `(T\m)`. Consequently, `m` has the most amount of elements in `T`.
As such, `m` can be described as **the most significant set** in `T`
that is **super-ordinate** to all the other sets.

* `max(T) := m` such that `(#t < #m)` for all `(t in T\m)`
* `(m superset-of t)` for all `(t in T\m)`

Note that any non-empty subset of a total setup is itself a total
sub-setup and therefore has a least and a most significant set.
