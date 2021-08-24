
<!-- ======================================================================= -->
## node tree => order of scopes

Given a node tree `T(N,E)`, **a family of scopes** `S` can be formed based on
the concept of abstract properties. That family of scopes can then be used to
form a strict partial containment order `P(S,<)` using the "strict-superset-of"
operator as the order operator.

Recall that with any digraph, one can always assume the default edge-based
"next-presequent-to" semantics, even though the semantics of a tree can in
general be denoted as the "parent-of" semantics.

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

Likewise, one can then assume that `n2` declares another property `p2` such
that `d(p2) = n2` and `s(p2) = [n2,*] = {n2, n4, n5}`. One can thus assume
that each and every node `ni` in `T` declares its very own property `pi`.

Based on these properties, one can define a set `S` such that it contains
the scope `si` of each property `pi` as an element. As such, set `S` can be
described as **a family of scopes**.

```
S  := +si   := { s1, s2, s3, s4, s5 }
s1 := s(p1) := { n1, n2, n4, n5, n3 } = E(T)
s2 := s(p2) := {     n2, n4, n5     } = [ni,*]
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

One can then define a containment order `P` using the family of scopes `S`.

* `P := (V,<)` such that `(V := S)` and
* `S := { si | (si := [ni,*]) such that (i in [1,#V(T)]) }`
* `(a < b) := (a strict-superset-of b)`
