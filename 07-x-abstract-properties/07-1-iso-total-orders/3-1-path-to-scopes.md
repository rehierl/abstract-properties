
<!-- ======================================================================= -->
## path graph => order of scopes

Given a non-empty path graph `s := (N,E)`, **a family of scopes** `S` can be
formed based on the concept of abstract properties. That family of scopes can
then be used to form a strict total containment order `P := (S,<)` using the
"strict-superset-of" operator as the order operator.

Recall that with any digraph, one can always assume the default edge-based
"next-presequent-to" semantics.

```
(a next-presequent-to b)
===============================
n1 - n2 - n3 - n4 - n5 - n6 ->|
```

Assume that the first node `n1` declares property `p1` (i.e. `d(p1) = n1`).
According to the introduction of abstract properties, the scope of `p1` extends
over all the nodes in `s` (i.e. `s(p1) = [n1,*] = {n1,..,n6}`). Put differently,
the scope of `p1` contains every single nodes in `s`:

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
```

Likewise, one can then assume that `n2` declares another property `p2` such
that `d(p2) = n2` and `s(p2) = [n2,*] = {n2,..,n6}`.

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
     -p2-----------------------
```

One can therefore assume, that each and every node `ni` in `s` declares
its very own property `pi`.

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
     -p2-----------------------
          -p3------------------
               -p4-------------
                    -p5--------
                         -p6---
```

Based on these properties, one can define a set `S` such that it contains
the scope `si` of each property `pi` as an element. As such, set `S` can be
described as **a family of scopes**.

```
s :=   n1 - n2 - n3 - n4 - n5 - n6 ->
------------------------------------------
s1 := s(p1) := { n1,  n2,  n3,  n4,  n5,  n6 } = E(s)
s2 := s(p2) := {      n2,  n3,  n4,  n5,  n6 } = [ni,*]
s3 := s(p3) := {           n3,  n4,  n5,  n6 }
s4 := s(p4) := {                n4,  n5,  n6 }
s5 := s(p5) := {                     n5,  n6 }
s6 := s(p6) := {                          n6 }
```

* `S := { s1, s2, s3, s4, s5, s6 }` where
* `S := { si | (si = [ni,*]) such that (i in [1,#V(s)]) }`

One can then define a containment order `P` using the family of scopes `S`.

* `P := (V,<)` such that `(V := S)` and
* `(a < b) := (a proper-superset-of b)`

Based on the above, the set of vertices `V(P)` is such that any pair of distinct
scopes is **properly related**. That is, one scope is a superset to the other.

* `(si related-to sj)` is true
* for any `(i,j in [1,#V])` and `(i != j)`

Consequently, any two scopes in the containment order is comparable
under the order operator. The containment order therefore has
**no pair of incomparable (distinct) vertices**.

Furthermore, the oder operator is such that one can tell for any pair of distinct
scopes which is super-ordinate to the other. That is, as far as distinct scopes
are concerned, **the order operator is directional**. As such, the operator can
be understood to point from a super-ordinate entity (i.e. in terms of the number
of elements within a scope) towards an entity that is sub-ordinate to it.

* `(a < b) <=> (a super-ordinate-to b)`

Consequently, the underlying order relation of `P` has one and only one edge for
each pair of distinct scopes. The order relation is therefore **trichotomous**.

Finally, if a set `a` has a proper subset `b` (A), and if that set has itself
a proper subset `c` (B), then set `c` is also a proper subset of superset `a`
(C). Because of that, the above containment order is **transitive** and as
such an actual ordered set of elements.

* `A := (a proper-superset-of b)`
* `B := (b proper-superset-of c)`
* `C := (a proper-superset-of c)`

One can therefore conclude that the above containment order
`P` is **a strict total order** of scopes.
