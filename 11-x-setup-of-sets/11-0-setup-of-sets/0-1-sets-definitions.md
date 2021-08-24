
<!-- ======================================================================= -->
## a recap on set-based definitions

Note that the main intention of the following definitions is to shift ones
focus away from the specific elements the sets contain. That is, the intention
is to shift ones focus towards the relationships between two or more sets.

<!-- ======================================================================= -->
## remarks

Note that the empty set `Ø` is disjoint-to and related-to every other set.
Also, the empty set is the only set that is disjoint-to and thus also not
coupled-with itself. In contrary to that, every other set is coupled-with
itself.

Note that common elements can be understood to act as a "link" between two
sets. Because of that, coupled sets can be said to be "connected" with each
other via some "point of contact". Such a point of contact may consist of
one or more elements. That is, the link between two coupled sets is itself
a set of elements that is a subset (i.e. intersection) to both coupled sets.

Note that the set difference `(A \ B)` between sets A and B is in general also
known as **the relative complement** of set B in regards to set A.

Note that the set difference `css(A) := (A \ B)` between sets A and B contains
all those elements in A that are unique to it in regards to B. As such, it can
be described as **the characteristic subset CSS()** of A in regards to B.

Note that two non-empty subsets of two disjoint sets are themselves disjoint.
Likewise, two descendants of two incomparable nodes in a tree are themselves
incomparable.

* Given two sets such that `(A disjoint-to B)`, ...
* and two subsets `a` and `b` such that ...
* `(a subset-of A)` and `(b subset-of B)`, ...
* and provided that `(a != Ø)` and `(b != Ø)`, then ...
* `(a disjoint-to b)` is a consequence.

<!-- ======================================================================= -->
## set-based operations

Set C is the **union** of sets A and B,
if it contains all the elements of A and B.

* `(A + B), (A or B), (A union B) := { x | (x in A) or (x in B) }`

Set C is the **intersection** of sets A and B,
if it contains all the elements of A and B that are common to both.

* `(A & B), (A and B), (A isect B) := { x | (x in A) and (x in B) }`

Set C is the **set-difference** between sets A and B,
if it contains all the elements of A, but no element of B.

* `(A \ B), (A not B), (A sub B) := { x | (x in A) and (x !in B) }`
* `css(A) := (A \ B)`

Set C is the **symmetric difference** between sets A and B,
if it contains all the elements that are elements of only one set.

* `(A ^ B), (A xor B) := (A + B) \ (A & B)`
* alt - `(A xor B) := (A \ B) + (B \ A)`

<!-- ======================================================================= -->
## set-based definitions

Set A is **empty** (Ø),
if it has no elements at all.

* `isEmpty(A) := (#A == 0)`

Set A is **disjoint** (DI) to set B,
if no element in A is also an element in B.

* `(A disjoint-to B) := (a !in B) for all (a in A)`
* alt - `(A disjoint-to B) := ((A & B) == Ø)`

Set A is **coupled-with** (C) set B,
if both sets have one or more elements in common.

* `(A coupled-with B) := (a in B) for some (a in A)`
* alt - `(A coupled-with B) := ((A & B) != Ø)`

Set A is a **(simple) subset** of set B,
if every element in A is also an element in B.

* `(A subset-of B) := (a in B) for all (a in A)`
* alt - `(A subset-of B) := ((A & B) == A)`

Set A is a **(simple) superset** of set B,
if B is a subset of A.

* `(B superset-of A) := (A subset-of B)`

Set A is **equal** (EQ) to set B,
if both are subsets to each other.

* `(A == B), (A equal-to B) := (A subset-of B) and (B subset-of A)`
* alt - `(A == B) := ((A xor B) == Ø)`

Set A is **distinct** from set B,
if both are unequal.

* `(A != B), (A distinct-from B) := not (A == B)`

Set A **overlaps** set B,
if both are coupled-with but not related-to each other.

* `(A overlaps B) := (A coupled-with B) and (A unrelated-to B)`

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

Set A is **strictly related** to set B,
if one is a proper subset of the other.

* `(A related-to B) := (A proper-subset-of B) or (B proper-subset-of A)`
