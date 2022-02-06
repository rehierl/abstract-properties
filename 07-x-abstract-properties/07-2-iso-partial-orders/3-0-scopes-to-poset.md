
<!-- ======================================================================= -->
# order of scopes <=> order of nodes

Given a partial containment order of scopes `P := (S,<)`,
which was formed from a node tree `T`, ..

* `P := (S,<)` such that
* `S := { s1, s2, s3, s4, s5 }`
* `(si < sj) := (si proper-superset-of sj)`

one can derive a strict partial order of nodes `Q := (N,<)` by replacing each
scope in `P` with its characteristic element `ce(si)`.

* `Q := (N,<)` such that
* `N := { ce(si) | (si in V(P)) }`
* `(ce(si) < ce(sj)) := ((si,sj) in P)`

From this node order `Q` one can recreate `P` by replacing each node `ni` in `Q`
by a set of nodes that contains all those nodes that are equal or subsequent
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
aEb := (a proper-superset-of b)
-------------------------------------
s1 := s(p1) := { n1, n2, n4, n5, n3 }
s2 := s(p2) := {     n2, n4, n5     }
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

Each set `si` contains a subset of elements that are no elements in any of
the proper subsets of `si`. As such, these subsets can be said to distinguish
`si` from its subsets. Because of that, such a subset can be referred to
as **the characteristic subset css(si)** of `si`.

* `css(si) := si \ { (nj in sj) | (sj proper-subset-of si) }`

Since each element in `css(si)` is unique to `si` in regards to all its
subsets `sj`, each element in `css(si)` can be referred to
as **a characteristic element** of `si`.

As can be seen above, each `css(si)` consists of only one such element.
Each such element can therefore be referred to as
**the characteristic element ce(si)** of `si`.

* `ce(si) := oneOf(css(si))`, iff `(#css(si) == 1)`

Based on that, an order of nodes `Q := (N,<)` can be defined as follows.

* `Q := (N,<)` such that
* `N := { ce(si) | (si in V(P)) }`
* `(ce(si) < ce(sj)) := ((si,sj) in P)`

Since one only replaces each scope `si` by its chracteristic element `ce(si)`,
and since one only update the order operator according to that replacement,
the new order `Q` preserves all other characteristics of `P`.

* `Q` is order preserving
* `Q` is **a strict partial order** of nodes

<!-- ======================================================================= -->
## order of nodes => order of scopes

Similar as before, the order of nodes `Q := (N,<)` can be used to create an
order of scopes `P* := (S,<)` by replacing each node `ni` in `Q` with a set of
nodes that contains all those nodes that are equal or subsequent to `ni` in `Q`.

* `P* := (S,<)` such that
* `S := { s(ni) | (ni in N) }`
* `(s(ni) < s(nj)) := ((ni,nj) in Q)`
* where `s(ni) := [ni,*]` - i.e. intervals over Q

Due to how `Q` and `P*` were formed
one can conclude that `P*` is equal to `P`.
