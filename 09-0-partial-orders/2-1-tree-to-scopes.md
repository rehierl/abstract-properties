
<!-- ======================================================================= -->
## node tree => order of scopes

Given a node tree `T := (N,E)`, **a family of scopes** `S` can be formed
based on the concept of abstract properties. That family of scopes can then
be used to form a strict partial containment order `P := (S,<)` using the
"strict-superset-of" operator as the order operator.

Recall that with any digraph, one can always assume the default edge-based
"next-presequent-to" semantics, even though the semantics of a tree is in
general referred to as the "parent-of" semantics.

```
(a next-presequent-to b)
========================
n1 --|-> n2 --|-> n4
     |-> n3   |-> n5
```

Assume that node `n1` declares property `p1` (i.e. `d(p1) = n1`). According
to the introduction of abstract properties, the scope of `p1` extends over
all the nodes in `T` (i.e. `s(p1) = [n1,*] = {n1,..,n5}`. Put differently,
the scope of `p1` contains every single node in `T`.

```
            |-p2------------|
n1 --|------|-> n2 --|-> n4 |
     |-> n3 |        |-> n5 |
            |---------------|
```

Likewise, one can then assume that `n2` declares another property `p2` such
that `d(p2) = n2` and `s(p2) = [n2,*] = {n2, n4, n5}`. One can therefore
assume in general that each and every node `ni` in `T` declares its very own
property `pi`.

Based on these properties, one can define a set `S` such that it contains
the scope `si` of each property `pi` as an element. As such, set `S` can be
described as **a family of scopes**.

```
s(p1) := { n1, n2, n4, n5, n3 } =: s1 = E(T)
s(p2) := {     n2, n4, n5     } =: s2
s(p4) := {         n4         } =: s4
s(p5) := {             n5     } =: s5
s(p3) := {                 n3 } =: s3
```

* `S := { s1, s2, s3, s4, s5 }` where
* `S := { si | (si = [ni,*]) such that (i in [1,#V(T)]) }`

One can then define a containment order `P` using the family of scopes `S`.

* `P := (V,<)` such that `(V := S)` and
* `(a < b) := (a proper-superset-of b)`

As can be seen above, the set of vertices `V(P)` is such that any pair of
distinct scopes is either disjoint ex-or related.

* `(si disjoint-to sj) or (si related-to sj)` is true
* for any `(i,j in [1,#V])` and `(i != j)`

Consequently, two distinct scopes within the containment order `P` might
be disjoint and therefore incomparable under the superset-of order operator.
The containment order **may therefore have pairs of incomparable vertices**.

Apart from that, the order operator is such that one can tell for any pair
of comparable scopes which is super-ordinate to the other. That is, as far
as related scopes are concerned, **the order operator is directional**. As
such, the operator can be understood to point from a super-ordinate entity
(i.e. in terms of the number of elements within a scope) towards a
sub-ordinate entity.

`(a < b) <=> (a super-ordinate-to b)`

Consequently, the underlying order relation of `P` has one and only one edge for
each pair of comparable scopes. Although not trichotomous, the order relation
of `P` can still be described as **a-symmetric**.

Finally, if a set `a` has a proper subset `b` (A), and if that set has itself
a proper subset `c` (B), then set `c` is also a proper subset of superset `a`
(C). Because of that, the above containment order is also **transitive** and
as such an actual ordered set of elements.

* `A := (a proper-superset-of b)`
* `B := (b proper-superset-of c)`
* `C := (a proper-superset-of c)`

One can therefore conclude that the above containment order
`P` is **a strict partial order** of scopes.
