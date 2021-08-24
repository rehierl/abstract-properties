
<!-- ======================================================================= -->
# Strict/Proper setup (T1)

A set of sets `S` will be referred to as **a proper setup (of type-1)**,
if and only if the following requirements are met:

* (R1) `S` is a simple setup of sets.
* (R2) If two sets in `S` are coupled, then both must be related.

Note that, as can be seen below, R2 can be rephrased as follows:

* (R2*) Any two sets in `S` must either be disjoint ex-or related.

Note that, since two sets in a partial setup are either disjoint ex-or related
(i.e. **DI ex-or RE**) requirement R2 guarantees that two sets in a partial
setup do not overlap each other. Because of that, such a setup may also be
described as **a partial setup** (of type-1).

<!-- ======================================================================= -->
## a visual impression

```
|-A---------------------| |-F-|        set-of-sets := {
| |-B-----|   |-D-----| | | 7 |          A: { 1, 2, 3, 4, 5, 6 },
| | 1   2 |   | 3     | | |---|          B: { 1, 2, 4 },
| | |-C-| |   | |-E-| | |                C: { 4 },
| | | 4 | | 5 | | 6 | | |                D: { 3, 6 },
| | |---| |   | |---| | |                E: { 6 },
| |-------|   |-------| |                F: { 7 }
|-----------------------|              }
```

* Set A contains elements 1 to 6.
* Set B contains elements 1, 2 and 4.
* Set C only contains element 4.
* Set D contains elements 3 and 6.
* Set E only contains element 6.
* Set F only contains element 7.

Elements may belong to more than one set:

* Elements 1 and 2 belong to sets A and B.
* Element 4 belongs to sets A, B and D.
* Element 5 only belongs to set A.

Some of the relationships between those sets are:

* Set A contains set B as a subset.
* Sets A and B both contain set C.
* Set B is disjoint to set D.

<!-- ======================================================================= -->
## (coupled <-> related)

As a consequence of R2, any two related sets in such a setup are guaranteed
to be coupled with each other.

* `(s coupled-with t) <-> (s related-to t)` is true for all `(s,t in P)`

(1) `(s coupled-with t) <-> (s related-to t)` is true if `(s == t)` is true.
That is because, in the context of a setup, and by the definition of the
corresponding operators, that statement is true since any non-empty set
is by definition coupled-with and related-to itself.

(2) `(s coupled-with t) -> (s related-to t)` is true if `(s != t)` is true.
That is because that expression is, due to R2, required to be true.

Note that two disjoint sets in such a setup are unrelated with each other
(i.e. `(disjoint -> unrelated)` is true). That is because no set is allowed
to be empty.

(3) `(s coupled-with t) <- (s related-to t)` is true if `(s != t)` is true.
That is because two related sets are, by the definition of the "related-to"
operator, coupled with each other.

Note that two distinct unrelated sets are not necessarily disjoint since both
may overlap each other (i.e. `(unrelated -> disjoint)` is in general *not*
true). However, for an implication (i.e. `(a -> b) := (!a or b)`) to be true
`b` must only be true if `a` is true. In contrary to that, `b` may have any
value if `a` is false. Consequently, implication (3) is due to the definition
of the "related-to" operator, satisfied.

(4) `(s coupled-with t) <-> (s related-to t)` is true if `(s != t)` is true.
That is because `((a -> b) and (a <- b)) <-> (a <-> b)` (i.e. 2+3).

(5) `(s coupled-with t) <-> (s related-to t)` is true for all `(s,t in P)`.
That is because that expression is true regardless of whether both sets in
a given setup are equal or not (i.e. 1+4).

<!-- ======================================================================= -->
## (disjoint ex-or related)

Any two sets in a partial setup are either disjoint
ex-or one set is a subset of the other.

* `(s disjoint-to t) ex-or (s related-to t)` is true for all `(s,t in P)`

That expression is true since it results from basic transformations:

(1) `(s coupled-with t) <-> (s related-to t)` is true for all `(s,t in P)`.
That is because this expression is a consequence of R2.

(2) `not (s disjoint-to t) <-> (s related-to t)` is true for all `(s,t in P)`.
A valid transformation since `(coupled-with <-> not-disjoint)`.

(3) `(s disjoint-to t) ex-or (s related-to t)` is true for all `(s,t in P)`.
A valid transformation since `(!a <-> b) <-> (a ex-or b)`.

<!-- ======================================================================= -->
## remarks

Note that, in order to determine if two sets are related with each other in a
partial a setup, one only needs to determine if both sets have **one element**
in common. That is, having one element in common is sufficient to tell if two
sets are related with each other. Consequently, and in order to determine the
orientation between both sets, one only needs to compare the number of elements
(aka. their **size**) in both sets.

Note that the **intersection** between any two sets in a partial setup is
either empty ex-or a set in it. In the latter case, the intersection is equal
to the smaller set (i.e. less significant). Likewise, the **union** of any two
sets in a partial setup is either a union of disjoint sets ex-or a set it.
In the latter case, the union is equal to the larger set (i.e. more significant).

* if `(s,t in S)`, `((s & t) != Ø)` and `(#s < #t)`, then ...
* `((s & t) == s)` and `((s + t) == t)` are both true
