
<!-- ======================================================================= -->
## power-set - P()

Given a set of elements `s`, then its power-set `P(s)` is defined as the set
of all possible subsets. Defined as such, a power-set contains the empty set
and the source set itself.

* `s := { a, b }`
* `P(s) := { Ø, {a}, {b}, {a,b} }`

Note that a power-set is defined as a homogenous nested set whose elements are
themselves sets of elements.

Note that a power-set may be used similar to a type of values (aka. domain) in
expressions of the form `(x in P(s))`. That way on can express that element `x`
is required to be one of the subsets of set `s`.

To form a power-set, one can imagine to start off with a random trace of
elements `t` fromed while iterating over the elements of the given set `s`.
In that trace, each element has a unique zero-based index raning from `0` to
`N-1`.

* `(#s == N)`, `t := traceof(s)`, `(#t == N)`

In addition to that, sequences `ti` are formed, each of which is of the same
length. However, instead of containing the elements of `s`, the components in
these sequences hold a numeric value of either zero/0 ex-or one/1. The each
element at an index corresponds within sequence `ti` corresponds with the
element in `t` at the same index (i.e. `( ti[j] <=> t[j] )`). As such, each
sequence `ti` corresponds with the binary representation of a numeric value.

Since there are `2^N` distinct values possible for a N-bit binary value, `2^N`
different sequences (`ti`) can be formed. Consequently, the power-set of a
set with size `N` is itself of size `2^N`. Hence, the name "power-set" is in
regards to their size (i.e. powers of two).

* `(#P(s) == 2^N)` if `(#s == N)`

<!-- ======================================================================= -->
## (cartesian) product - (×)

The cartesian product of two sets can be defined as a set of all possible
2-element sequences such that the first element of each sequence is taken
from the 1st set, and the 2nd element from the 2nd set.

* `s × t := { (a,b) | (a in s), (b in t) }`
* `#(s × t) == (#s * #t)`

Defined as such, the resulting set of the cartesian product is in principle
always a set of 2-element sequences. That is, even a cartesian product of three
or more sets will (aka. **multi cartesian product**) produce nested 2-element
sequences rather than flat sequences. As such, the cartesian product is neither
commutative nor associative.

* `s := {1}`, `t := {2}`, `u := {3}`
* `(s × t) = { (1,2) }`
* `(t × s) = { (2,1) }` - non-commutative
* `((s × t) × u) = { ((1,2), 3) }`
* `(s × (t × u)) = { (1,(2,3)) }` - non-associative

<!-- ======================================================================= -->
## (concatenation-based) product - (×)

In contrary to the strict definition of the cartesian product, and in the
context of this discussion, the product of 3 or more sets must be understood
to be evaluated from left to right and to append the elements of subsequent
sets to the sequences of the previous product. Based on that, parenthesis
can and will be omitted.

* `(s × t × u) := ((s × t) × u) = { (1,2,3) }`

Furthermore, sequences will be formed whose elements are taken from one common
set of elements `S` in order to represent paths of nodes/vertices. As such,
these sequences may in general be of any length, which is why the product
operator needs to be extended such that it can be used to refer to the set of
all paths that possible over a particular relation.

Here, `×Si` will be used to refer to all valid paths of length `i`. Based on
that, the set of all valid paths can be described as a union of all sets of
valid paths that have some specific length. Hence, `×S*` (or simply `×S`)
will be used to refer to that union of sets of sequences.

* `×Si := (S1 × ... × Si) := { (s1,...,si) | (si in S) }`
* `×S*, ×S := ×S0 + ×S1 + ×S2 + ...`

Note that `×S` contains sequences of any length, including the empty sequence
`()` (from `×S0`) and all possible 1-element sequences (from `×S1`).

If need be, the lengths of the paths in consideration may be restricted using
the following pattern-based definitions:

* `×S{i} := ×S0 + ×S1 + ... + ×Si`
* `×S{i,j} := ×Si + ... + ×Sj` where `(i <= j)`

Note that this style of notation is based upon the patterns used by regular
expressions. Futher extensions should therefore be understood in that regards.
