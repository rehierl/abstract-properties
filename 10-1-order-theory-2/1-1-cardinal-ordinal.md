
<!-- ======================================================================= -->
# transfinite, cardinal, ordinal numbers

Even though the overall context of this discussion is on finite sets, one
will inevitably stumble upon the topic of ordinal numbers when reading about
well-ordered sets. The following is intended to provide a brief overview such
that one can grasp the meaning of certain order-related statements.

Note that the order type of a well-order is expressed as an ordinal number,
which can be loosely described as being vastly more general, but still similar
to index values.

Needless to state ... not my forte ...

<!-- ======================================================================= -->
## transfinite numbers

Natural numbers can be used as an ordinal (to denote the position of an element)
and as a cardinal (to denote the size of a finite set). Because of that, things
are "as usual" when dealing with finite sets.

Things are however different when dealing with infinite sets (of numbers). After
all, how does one tell, if one infinite set is larger (in terms of the number of
elements contained within them) than another infinte set?

A system of transfinite numbers is thus needed which allows to count beyond the
natural numbers. That is, numbers are required which are "infinite", but not
necessarily absolutely so. These kind of numbers can be described as "transfinite
cardinals" and as "transfinite ordinals".

<!-- ======================================================================= -->
## cardinal numbers, aleph number

The cardinality of the set of natural numbers (Nat) is `N0` (read as aleph-zero,
aleph-nought, aleph-null - the Hebrew letter alpeh). The next larger cardinality
then is `N1` (aleph-one), and so on. (Note that there is no cardinal number
between N0 and N1).

* `0,1,2,3, .., N0,N1,N2,N3, ..`

A set is said to be **a finite set**, if its cardinality is less than the
cardinality of Nat. In contrary to that, a set is said to be
**countably infinite**, if it has the same as cardinality as Nat.
Any set with a cardinality greater than that is said to be **uncountable**.

* X is finite, if `(|X| < N0)` is true
* X is countably infinite, if `(|X| == N0)` is true
* X is uncountable, if `(|X| > N0)` is true

<!-- ======================================================================= -->
## ordinal numbers, order type

The lowest transfinite ordinal is `omega` (alt. `om` - read as Omega), which
is also the **order type** of the natural numbers. (Hence the reason for this
chapter). As such, `omega` can be described to mark/label the first ordinal
(position) that is past the set of natural numbers. The next ordinal after
that is `omega+1`, and so on.

* `Ord := 0,1,2,3, .., om,om+1,om+2, .., om*2,om*2+1, .., om^2, .., om^om, ..`
* `(Nat prefix-of Ord)` is by definition true

Note that the infinite ordered sequence of ordinals `Ord` can be loosely
described as a sequence of infinitely many ordered sequences of countably
infinite size. To some extent one can imagine `Ord` as being formed by
concatenating the sequence of natural numbers infinitely many times. Because
of that, each such subsequence can be said to have an `offset` of `om*N`
for some number `N`.

Two ordered sets X and Y are said to have the same **order type**, if they are
order-isomorphic. That is, if there is a bijective mapping from X to Y. As such,
both sets have the same cardinality, which is then referred to as "the order
type" of both sets, and expressed as an ordinal number.

Note that `Ord` is such that any ordinal `ord` corresponds with the number
of ordinals that are presequent to it. Furthermore, the set of these ordinals
(i.e. `i := (*,ord)`) is such that it has a least element.

* for some `Ord[i]` and some possibly transfinite index `i` (an ordinal)
* `(#Pref[i] == Ord[i])` where `Pref[i] := (*,i) := { ord | (ord < s[i]) }`
* `Ord` corresponds with a well-ordered set

A **well-order** (aka. a well-ordered set) is a total order such that each
subset has a least element (i.e. a unique minimal element). Hence, the set
of ordinal numbers `Ord`, the set of natural numbers `Nat` and every other
prefix of `Ord` are all well ordered sets.

By definition, every well-ordered set is order-equivalent to exactly one ordinal
number. Hence, `Ord` can be understood to consist of canonical representatives
for a particular order types. Put differently, the order type of any well ordered
set can be expressed as an ordinal number.

* `ord(P), OrderTypeOf(P) := Ord[i]`
* for some poset `P` that is order-isomorphic to `Pref[i]`
