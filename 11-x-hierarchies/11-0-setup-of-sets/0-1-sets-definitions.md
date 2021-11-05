
<!-- ======================================================================= -->
## a recap on set-based definitions

Note that the following definitions are intended to shift ones focus away from
the elements the sets contain, towards the relationships that exist between
sets of elements.

<!-- ======================================================================= -->
## remarks

Note that the empty set `Ø` is disjoint-to and related-to every other set. Also,
the empty set is the only set that is disjoint-to and as such also not coupled
with (i.e. no shared element) itself. In contrary to that, every other set is
coupled-with itself.

Note that common elements can be understood to act as a "link" between two sets.
Because of that, coupled sets can be said to be "connected" with each other via
some "point of contact" which may consist of one or more elements. That is, the
link between two coupled sets is a set of elements which is a subset to both
sets (i.e. the intersection).

Note that the set difference `css(A) := (A \ B)` of sets A and B contains all
of those elements in A that are unique to it in regards to B. Because of that,
the set difference can be described as **the characteristic subset css()** of
A in regards to B.

Note that the set difference `(A \ B)` of sets A and B is also known as
**the relative complement** of B in regards to A.

Note that any two subsets of two disjoint sets are themselves disjoint. Similar
to that, two descendants of two incomparable nodes in a tree are incomparable.

* Given two sets such that `(A disjoint-to B)` is true, ...
* and two subsets `a` and `b` such that ...
* `(a subset-of A)` and `(b subset-of B)` are both true, then ...
* `(a disjoint-to b)` is a consequence also true.

<!-- ======================================================================= -->
## set-based operations

Set C is the **union** of sets A and B,
if it consists of all the elements in A and B.

* `(A + B), (A or B), (A union B) := { x | (x in A) or (x in B) }`

Set C is the **intersection** of sets A and B, if it only consists of all
the elements in A and B that are common to both. Based on that, two sets
that have a non-empty intersection are said to **intersect each other**.

* `(A & B), (A and B), (A isect B) := { x | (x in A) and (x in B) }`

Set C is the **set-difference** between sets A and B,
if it consists of all the elements in A, but none of the element in B.

* `(A \ B), (A not B), (A sub B) := { x | (x in A) and (x !in B) }`
* `css(A) := (A \ B)`

Set C is the **symmetric difference** between sets A and B,
if it consists of all the elements that are elements of one set only.

* `(A ^ B), (A xor B) := (A + B) \ (A & B)`
* alternatively - `(A xor B) := (A \ B) + (B \ A)`

<!-- ======================================================================= -->
## set-based definitions

Set A is **empty**, if it has no elements at all.
The empty set `Ø` is the only set that has no elements.

* `isEmpty(A) := (#A == 0)`

Set A is **disjoint** (DI) to set B,
if no element in A is also an element in B.

* `(A disjoint-to B) := (a !in B) for all (a in A)`
* alternatively - `(A disjoint-to B) := ((A & B) == Ø)`

Set A is **coupled-with** (CW) set B,
if both sets have one or more elements in common.

* `(A coupled-with B) := (a in B) for some (a in A)`
* alternatively - `(A coupled-with B) := ((A & B) != Ø)`

Set A is a **(simple) subset** (SUB) of set B,
if every element in A is also an element in B.

* `(A subset-of B) := (a in B) for all (a in A)`
* alternatively - `(A subset-of B) := ((A & B) == A)`

Set A is a **(simple) superset** (SUP) of set B,
if B is a subset of A.

* `(B superset-of A) := (A subset-of B)`

Set A is **equal** (EQ) to set B,
if both are subsets to each other.

* `(A == B), (A equal-to B) := (A subset-of B) and (B subset-of A)`
* alternatively - `(A == B) := ((A xor B) == Ø)`

Set A is **distinct** (NEQ) to set B,
if both are unequal.

* `(A != B), (A distinct-to B) := not (A == B)`

Set A **overlaps** (OV) set B, if both are coupled-with but not
related-to each other. That is, none is a subset of the other.

* `(A overlaps B) := (A & B != Ø) and (A \ B != Ø) and (B \ A != Ø)`
* alternatively - `(A overlaps B) := (A coupled-with B) and (A unrelated-to B)`

<!-- ======================================================================= -->
## related

Set A is **related** (RE) to set B,
if one is a subset of the other.

* `(A related-to B) := (A subset-of B) or (B subset-of A)`

Set A is **unrelated** to set B,
if none is a subset of the other.

* `(A unrelated-to B) := not (A related-to B)`

Set A is a **strict/proper subset** of set B,
if both are distinct, and if A is a subset of B.

* `(A proper-subset-of B) := (A subset-of B) and (A != B)`

Set A is a **strict/proper superset** of set B,
if both are distinct, and if A is a superset of B.

* `(A proper-superset-of B) := (A superset-of B) and (A != B)`

Set A is **strictly/properly related** to set B,
if one is a proper subset of the other.

* `(A properly-related-to B) := (A proper-subset-of B) or (B proper-subset-of A)`
