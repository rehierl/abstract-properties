
<!-- ======================================================================= -->
## order of scopes => path graph

Like any other order relation, the transitive reduction of the order relation
`R` of the containment order `P := (S,<)`, which was formed from the initial
path graph `s` as described before, can be visualized as a graph of nodes and
edges `G := (S,E)`.

```
(a superset-of b)
================================
s1 -> s2 -> s3 -> s4 -> s5 -> s6
```

As can be seen, the graph of such a containment order is itself **a path graph**
such that each node `si` in it is a scope `[ni,*]` over the intial path graph.

Because of that, and in order to recreate the intial path graph `s`, one can
begin with defining a graph `G := (S,E)` as the transitive reduction of the
order relation of `P := (S,<)`.

* `G := (S,E)` such that `S := V(P)` and
* `E` := the transitive recution of `E(P)`

Defined as such, one now has a path graph over the scopes `si`, which is why
the vertices in `G` still need to be replaced such that the resulting graph
`s*` is equal to the initial path graph `s`.

```
s     :=   n1 - n2 - n3 - n4 - n5 - n6 ->
------------------------------------------
s(p1) := { n1,  n2,  n3,  n4,  n5,  n6 } =: s1 = E(s)
s(p2) := {      n2,  n3,  n4,  n5,  n6 } =: s2
s(p3) := {           n3,  n4,  n5,  n6 } =: s3
s(p4) := {                n4,  n5,  n6 } =: s4
s(p5) := {                     n5,  n6 } =: s5
s(p6) := {                          n6 } =: si = [ni,*]
```

Based on the elements in each scope `(si in S)` one can observe that node `ni`
is an element in scope `si`. Furthermore, a subset can be formed from each `si`
such that it only contains node `ni`, if all the elements in all the subsets
`sj` of `si` are removed.

* `css(si) := si \ { (nj in sj) | (sj proper-subset-of si) }`

One can therefore conclude, that the subsets `css(si)` contain all of the
elements that are unique to the corresponding superset `si` in regards to all
of its subsets `sj`. Because of that, each such subset will be referred to
as **the chracteristic subset css(si)** of `si`.

Since each element in `css(si)` is unique to `si` in regards to all the
subsets `sj` of `si` in `S`, each element in `css(si)` can be referred to
as **a characteristic element** of `si`.

As can be seen above, each characteristic subset `css(si)` consists of one
and only one characteristic element. Each such element can therefore be
referred to as **the characteristic element ce(si)** of `si`.

* `ce(si) := oneOf(css(si))`, iff `(#css(si) == 1)`

Based on that, a mapping `(f: si -> ce(si))` can be defined that allows to
replace each scope `si` by its characteristic element `ce(si)`.

This mapping can then be applied on `G := (S,E)` in order to derive a new
graph `s* := (N,E)` such that each scope `si` in `G` is replaced by its
characteristic element `ce(si)`.

* `s* := (N,E)` such that
* `N := { ce(si) | (si in S) }`
* `E := { (ce(si),ce(sj)) | ((si,sj) in E(G)) }`

One can then conclude that the resulting graph `s*`
is equal to the initial path graph `s`.

* `(s* == s)` is true
