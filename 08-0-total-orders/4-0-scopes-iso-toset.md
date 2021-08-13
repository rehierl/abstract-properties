
<!-- ======================================================================= -->
# order of scopes <=> order of nodes

Given a total containment order of scopes `P := (S,<)`, which was formed from
a path graph `s`, ..

* `P := (S,<)` such that
* `S := { s1, s2, s3, s4, s5, s6 }`
* `(si < sj) := (si superset-of sj)`

one can derive a strict total order of nodes `Q := (N,<)` by replacing each
scope in `P` with its characteristic element `ce(si)`.

* `Q := (N,<)` such that
* `N := { ce(si) | (si in V(P)) }`
* `(ce(si) < ce(sj)) := ((si,sj) in P)`

From this node order `Q` one can recreate `P` by replacing each node `ni` in `Q`
by a set of nodes that contains all those nodes which are equal or subsequent
to `ni` in `Q`.

* `P* := (S,<)` such that
* `S := { s(ni) | (ni in N) }`
* `(s(ni) < s(nj)) := ((ni,nj) in Q)`
* where `s(ni) := [ni,*]` - i.e. intervals over Q

Consequently, any such containment order of scopes can be said to be
**isomorphic** to an actual node order.

* `P*` is equal to `P`
* `P` is isomorphic to `Q`

<!-- ======================================================================= -->
## order of scopes => order of nodes

```
S := { s1, s2, s3, s4, s5, s6 }
aEb := (a superset-of b)
--------------------------------------
s1 := { n1,  n2,  n3,  n4,  n5,  n6 }
s2 := {      n2,  n3,  n4,  n5,  n6 }
s3 := {           n3,  n4,  n5,  n6 }
s4 := {                n4,  n5,  n6 }
s5 := {                     n5,  n6 }
s6 := {                          n6 }
```

Each set `si` contains a subset of elements that are no elements in any of the
proper subsets of `si`. As such, these subsets can be said to distinguish `si`
from its subsets. Because of that, the subset of these unique elements can be
referred to as **the characteristic subset css(si)** of `si`.

* `css(si) := si \ { (nj in sj) | (sj proper-subset-of si) }`

Since each element in `css(si)` is unique to `si` in regards to all the
subsets `sj` of `si` in `S`, each element can be referred to as
**a characteristic element** of `si`.

As can be seen above, each characteristic subset `css(si)` consists of one
and only one characteristic element. Each such element can therefore be
referred to as **the characteristic element ce(si)** of `si`.

* `ce(si) := oneOf(css(si))`, iff `(#css(si) == 1)`

Based on that, an order of nodes `Q := (N,<)` can be defined as follows.

* `Q := (N,<)` such that
* `N := { ce(si) | (si in V(P)) }`
* `(ce(si) < ce(sj)) := ((si,sj) in P)`

Since one only replaces each scope `si` by its chracteristic element `ce(si)`,
and since one only updates the order operator according to that replacement,
the new order `Q` preserves all other characteristics of `P`.

* `Q` is **a strict total order** of nodes
* `Q` is order preserving

<!-- ======================================================================= -->
## order of nodes => order of scopes

Similar as before, the order of nodes `Q := (N,<)` can be used to recreate an
order of scopes `P* := (S,<)` by replacing each node `ni` in `Q` with a set of
nodes that contains all those nodes which are equal or subsequent to `ni` in `Q`.

* `P* := (S,<)` such that
* `S := { s(ni) | (ni in N) }`
* `(s(ni) < s(nj)) := ((ni,nj) in Q)`
* where `s(ni) := [ni,*]` - i.e. intervals over Q

Due to how `Q` and `P*` were constructed,
one can conclude that `P*` is equal to `P`.
