
<!-- ======================================================================= -->
# Setups of rooted paths

<!-- ======================================================================= -->
## A partial setup of rpaths

A set of rooted paths `S` will be referred to as **a partial setup**,
if and only if the following requirements are met:

* (R1) `S` is a simple setup of rooted paths.
* (R2) Any two paths in `S` are either related ex-or overlap each other.

Note that the above requirements define the default **RE-OV** case.

<!-- ======================================================================= -->
## remarks (1)

In order to determine if two paths are related with each other in a partial
setup, one only needs to determine if both paths have same last element.

* `(s related-to t)` is true for `(s,t in S)` if ...
* `(s(i) == t(i))` where `i := min(#s,#t)`

Furthermore, and in order to determine the orientation between two related
paths, one only needs to compare the number of elements (aka. their length).

* `(s prefix-of t)` is true if `(s related-to t) and (#s < #t)`

The intersection between any to paths in a partial setup always is equal to
a sequence in it. However, the intersection may or may not correspond with
one of the two paths. That is because both paths may overlap each other.

The union of two paths in a partial setup `(s,t in S)` is either equal to one
of the two paths (i.e. equal to `t` if `(s prefix-of t)`), or a union of paths
that overlap each other.

<!-- ======================================================================= -->
## A total setup of rpaths

A set of rooted paths `S` will be referred to as **a total setup**,
if and only if the following requirements are met:

* (R1) `S` is a simple setupf of rooted paths.
* (R2) Any two paths in `S` must be related with each other.

Note that the above requirements define the **RE only** case.

<!-- ======================================================================= -->
## least/most significant prefix

Given a partial setup `S` and a non-root path `(s in S)`,
then `s` is a prefix to one or more other paths in `S`.
Because of that, the set of all ancestors `A(s)` is non-empty.

Since each path in `A(s)` is a prefix to `s`, all the paths in `A` are related
with each other. Consequently, `A` is **a total sub-setup** of `S`.

`A` therefore has a path `l` such that it is a super-string to each path in
`(A\l)` (i.e. `(l == p(s))`). Consequently, `l` has the most amount of elements
in `A`. As such, `l` can be described as **the least significant path** in `A`
that is **sub-ordinate** to all the other paths.

* `min(A) := l` such that `(#t < #l)` for all `(t in A\l)`
* `(t prefix-of l)` for all `(t in A\l)`

Likewise, `A` has a path `m` such that it is a prefix to each path in `(A\n)`
(i.e. `(m == r(s))`). Consequently, `m` has the least amount of elements in
`A`. As such, `m` can be described as **the most significant path** in `A`
that is **super-ordinate** to all the other paths.

* `max(A) := m` such that `(#m < #t)` for all `(t in A\m)`
* `(m prefix-of t)` for all `(t in A\m)`

Note that any non-empty subset of a total setup is itself a total sub-setup
and therefore has a least and a most significant path. (Hence the more generic
specifiers `l` and `m`).

Note that, due to the above, `S` can be described as being **downward-total**.
