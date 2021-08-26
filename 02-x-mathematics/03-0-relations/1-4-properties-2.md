
<!-- ======================================================================= -->
## serial

* for any `a`, there is a `b` such that aRb
* e.g. intervals (open or closed) equipped with (<) or (<=)
* e.g. R := ([1,*],<) - serial - there always is a greater element
* e.g. R := ([1,*],>) - not serial - there is no `n` such that (n < 1)

clarification

* note - does not state how many `b`s there must be, one is sufficient

<!-- ======================================================================= -->
## set-like/local relation

* relation R over set X
* for every (x in X), the class of all (y in X) such that yRx is a set
* e.g. the lower-than ordering (<) on the class of ordinal numbers is set-like
* the elements less than a given element form a set

<!-- ======================================================================= -->
## well-founded relation

* a relation R over set X is well-founded,
  if every non-empty subset S has a minimal element in R
* i.e. an element m unrelated by sRm

remarks

* a poset is well-founded, if the strict order is well-founded
* if the order is total, then it is called a well-order

induction and recursion

* given a well-founded relation (X,R) and some property P(x)
* goal is to - prove that P(x) holds for all (x in X)
* show that - P(y) is true for all yRx, then P(x) holds for all (x in X)
* aka. well-founded or Noetherian induction

<!-- ======================================================================= -->
## remarks - quasi-transitive

* a weaker version of transitivity
* a relation that is symmetric for some elements, and transitive elsewhere

definition

* aRb and !bRa and bRc and !cRb => aRc and !cRa
* R is transitive, if R is anti-symmetric

example

* person p indifferent between 7 and 8
* and indifferent between 8 and 9
* but prefers 9 over 7

remarks

* R must be a disjoint union of
* a symmetric relation J and
* a transitive relation P

<!-- ======================================================================= -->
## euclidean relation

* magnitudes which are equal to the same are equal to each other
* note - not to be confused with "transitive"
* note - the definitions are quite unclear (!)

```
right-euclidean   left-euclidean
---------------   --------
  c               a
 /                 \
a |               | c
 \                 /
  d               b
```

right-euclidean, euclidean

* for all a,b,c in R
* if aRc and aRd, then also cRd
* note - aRd and aRc -> dRc (so also ?)
* note - aRa and aRd -> bRa

left-euclidean

* for all a,b,c in R
* if aRc and bRc, then also aRb
* note - bRc and aRc -> bRa (so also ?)
* note - aRa and bRa -> aRb

remarks

* the requirements must apply everywhere
* right-euclidean, reflexive => equivalence
* left-euclidean, reflexive => equivalence
* so a downward-total order is left-euclidean?
