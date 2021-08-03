
<!-- ======================================================================= -->
## properties

Since relations are in widespread use throughout Mathematics (e.g. to describe
functions, ordered sets, node trees), many properties have been defined in
order to describe the characteristics of the graph of a relation. Because of
that, the following will only mention those that appear to be of some use to
the discussion, or that can be understood to provide more insight on those
that can be considered relevant.

Note that, as a matter of clarity, the following definitions are kept in terms
of bullet points. Detailed explanations on specific properties may follow.

Note that, even though the definitions are abstract and difficult to understand,
the following definitions can be described as providing a foundation for the
overall discussion. Luckily, only few are essential in the context of this
discussion: e.g. transitive, reflexive, irreflexive, a-symmetric

Note that properties may be associated with a quoted "memory hook". These are
not overly accurate, but should help to memorize the gist of the corresponding
definitions.

<!-- ======================================================================= -->
## "functional" properties

* `R := (A,B,G)`
* `a,b in A` and `c,d in B`
* not necessarily heterogenous

```
not           not            not          not
left-unique   right-unique   left-total   right-total
-----------   ------------   ----------   -----------
 a               c            a -- c       a -- c
  \             /
   c           a              b                 d
  /             \
 b               d
```

**left-unique, injective**

* if aRc and bRc, then (a == b)
* there is no `c` such that aRc and bRc for (a != b)
* no two distinct elements have the same outcome

**right-unique, functional**

* if aRc and aRd, then (c == d)
* there is no `a` such that aRc and aRd for (c != d)
* no two distinct elements have the same income

**left-total**

* for any `a`, there is a `c` such that `aRc`
* each `a` has an outcome

**right-total, surjective, onto**

* for any `c`, there is an `a` such that `aRc`
* each `c` has an income, each `c` can be reached

combinations of uniqueness and totality

* **(overall) unique, one-to-one** := left-unique and right-unique
* **total** := left-total and right-total
* **bijective** := unique and total

<!-- ======================================================================= -->
## endo-relations

* `R := (A,A,G)`
* `(a,b,c,d in A)`

miscellaneous

* **endo-relation** := binary and homogeneous
* universal relation **U** := (A × A) or { aRb | (a,b in A) }
* identity relation **I** := { aRa | (a in A) }

<!-- ======================================================================= -->
## endo-relations, transitive

**transitive**

* if aRb and bRc, then also aRc
* e.g. "is ancestor of"

clarification

* all three edges are required
* bRa, cRb, cRa may also exist

**quasi-transitive**

* if (aRb & !bRa & bRc & !cRb), then also (aRc & !cRa)
* not required to be a-symmetric
* not quite transitive

unclear

* due to !bRa, !cRb, !cRa
* seems more strict than "transitive"
* then why "quasi"?

<!-- ======================================================================= -->
## endo-relations, loops

**reflexive**

* "all possible loops"
* aRa is true for all (a in A)
* there is no `a` such that aRa is not true
* any `a` is strictly related to itself
* e.g. (<=) - "lower than or equal"

**irreflexive, strict**

* "no loops at all"
* no aRa for any (a in A)
* there is no `a` such that aRa is true
* e.g. (>) - "greater than"

clarification

* if aRa or !aRa for some (a in A),
  then neither reflexive nor irreflexive

**coreflexive**

* "loops only"
* if aRb, then (a == b)
* there is no aRb such that (a != b)
* (R subset-of I) if `R` is coreflexive
* e.g. (==) - "identical to"

**quasi-reflexive**

* "related, some loops"
* if aRb, then aRa and bRb
* not quite reflexive

<!-- ======================================================================= -->
## endo-relations, symmetry

**symmetric**

* "undirectional, non-strict, possible loops"
* if aRb, then also bRa
* no strict/overall orientation
* e.g. "equal to"

clarification

* symmetric => (inv(R) == R) => palindromic

**a-symmetric**

* "strictly directional, no loops"
* if aRb, then !bRa
* aRa no longer allowed
* e.g. "greater than"

**anti-symmetric**

* "directional, non-strict, possible loops"
* if aRb and bRa, then (a == b)
* aRa is allowed, but not required
* e.g. "greater or equal"

clarification

* if aRb and (a != b), then !bRa

<!-- ======================================================================= -->
## endo-relations, connectivity

**connex**

* "all related, all loops"
* for any pair aRb and/or bRa is true

clarification

* any connex relation is reflexive
* any node is related to every other node, including itself
* has no disconnected nodes

**semi-connex**

* "all related, non-strict - possible loops"
* for any pair (a != b) it holds that aRb and/or bRa

clarification

* aRa is allowed, but not required

**trichotomous**

* "all related, strict, no loops"
* aRb xor bRa xor (a == b) must be true
* e.g. "greater than"

clarification

* !aRa for any `a` => irreflexive
* any node is related to every other node
