
<!-- ======================================================================= -->
## A total setup of sets

A set of sets `S` will be referred to as **a total setup**,
if the following requirements are met.

* (R0) `S` is a partial setup of sets.
* (R1) Any two sets in `S` are related with each other.

Note that, since any two sets in a total setup are required to be related, a
total setup does not allow pairs of disjoint and also no pairs of overlapping
sets. That is, a total setup covers the **RE only** case.

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
## least/most significant (super)set

Given a partial setup `S` and a non-root set `(s in S)`,
then `s` is a subset to one or more other sets in `S`.
Because of that, the set of all ancestors `A(s)` is non-empty.

Since `s` is a subset to each set in `A(s)`, and since no set in `S` can be
disjoint to, or overlap another set, all the sets in `A` are related with each
other. Consequently, `A` is **a total sub-setup** of `S`.

`A` therefore has a set `l` such that it is a subset to all the other sets in
`A` - i.e. `(l == p(s))` is true. Consequently, `l` has the least amount of
elements in `A`. As such, `l` can be described as **the least significant set**
in `A` that is **sub-ordinate** to all the other sets in `A`.

* `min(A) := l` such that `(#l < #t)` for all `(t in A\l)`
* `(l subset-of t)` for all `(t in A\l)`

Likewise, `A` has a set `m` such that it is a superset to all the other sets in
`A` - i.e. `(m == r(s))` is true. Consequently, `m` has the most amount of
elements in `A`. As such, `m` can be described as **the most significant set**
in `A` that is **super-ordinate** to all the other sets in `A`.

* `max(A) := m` such that `(#t < #m)` for all `(t in A\m)`
* `(m superset-of t)` for all `(t in A\m)`

Note that any non-empty subset of a total setup is a total sub-setup and
therefore has a least and a most significant set. (Hence the more generic
specifiers `l` and `m`).

Note that, due to the above, `S` can be described as being **downward-total**.

<!-- ======================================================================= -->
## unique numbers of elements

```
                              |0     |
                    C -> ...  |      |
                 > /          |      |- (#x < #t)       for (x in C)
           A -> {t}           |#t    |
          /      < \          |      |- (#t < #x < #s)  for (x in D)
         /          D -> ...  |      |
      > /                     |      |- D(s) - subsets
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
that, `s` can not have the same amount of elements as `t`. That is, `s` has
either more ex-or fewer elements than `t`.

* for `(s,t in S)` and `(s != t)` ..
* `(s subset-of t) <-> (#s < #t)`

The sets in `(S\s)` can therefore be split up into a set `A` that contains all
the sets which have fewer elements than `s` (i.e. `D(s)`), and a set `B` that
contains all the sets which have more elements than `s` (i.e. `A(s)`). Setup
`S` can therefore be described as a union of three pairwise disjoint sets.

* `S := (A + {s} + B)` where ..
* `A := { t | (t in S\s) and (#t < #s) }`
* `B := { t | (t in S\s) and (#t > #s) }`

Since subsets `A` and `B` are themselves total sub-setups of `S`, the process
can be repeated recursively on subsets `A` and `B` until there is no more set
that remains in `S`.

Distinct sets in a total setup have therefore **distinct amounts of elements**.
That is, the number of elements in each set is **unique** to that set.

* `(#S == #N)` is true for `N := { #s | (s in S) }`

Since each set in a total setup has a unique number of elements, a total setup
can be used to form a total order of sets `P(S,<)` such that the order over
the sets in it corresponds with the number of elements in each set.

* `(a < b) := (a superset-of b)`, alternatively `(a < b) := (#a > #b)`
* `(a < b) := (a subset-of b)`, alternatively `(a < b) := (#a < #b)`

Note that, with a visualization of nested sets in mind, one can describe a total
setup as **an onion of sets** such that the least significant set is at its core
and also such that the most significant set encloses all the other sets. Based
on that, the setup can be described to grow outwards by one or more elements
with each next larger set.

<!-- ======================================================================= -->
## remarks

Note that a total setup is a set of pairwise related sets. That is, each set
in a total setup is related to every other set in it. Because of that, and for
any pair of distinct sets `(s,t in S)` it can be determined which is the subset
and which the superset.

Note that in a total setup any parent has **one and only one child**. That is
because if a parent had more than one child, then the setup would have a pair
of unrelated/disjoint subsets. As such, the setup would not be total. A total
setup therefore is **downward- and upward-total**.

Note that, since each parent in a total setup has **one child only**, each
parent in a total setup always has a least and a most significant subset.
Any non-empty total setup therefore has **one root and one leaf**.
