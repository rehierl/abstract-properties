
<!-- ======================================================================= -->
# path graph <=> order of scopes

Given a non-empty path graph `s := (N,E)` ..

```
s := n1 -> n2 -> n3 -> n4 -> n5 -> n6`
```

**a family of scopes** `S` can be formed
based on the concept of abstract properties.

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

* `S := { si | (si := [ni,*]) where (i in [1,#V(s)]) }`

Based on `S` **a strict total containment order of scopes** `P` can be formed,
which can also be described as **a scope order**, or as **an order of scopes**.

* `P := (S,<)` such that
* `(a < b) := (a proper-superset-of b)`

Like any other ordered set, the containment order can be visualized as a graph.
As can be seen below, the graph of such an order is itself **a path graph** such
that each node `si` in it is a scope `[ni,*]` over the intial path graph `s`.

```
sem(P) := (a proper-superset-of b)
==================================
s1 -> s2 -> s3 -> s4 -> s5 -> s6
```

One can therefore form a graph `G := (S,E)` as the transitive reduction of
the order relation of `P`. A path graph `s*` can then be formed, if each scope
`si` in `G` is replaced by its **characteristic element ce(si)**, while also
updating all the edges in `G` according to each replacement. Based on that,
one can determine, that the newly formed graph `s*` is equal to `s`.

* `s* := (N,E)` such that
* `N := { ce(si) | (si in S) }`
* `E := { (ce(si),ce(sj)) | ((si,sj) in E(G)) }`
* note - `(s* == s)` is true

Consequently, any path graph can be said to be **isomorphic** to a strict total
containment order. That is, a containment order can be formed from the path
graph, which can then be used to recreate the initial path graph.

<!-- ======================================================================= -->
## remarks

Note that each strict total containment order `P`, as formed above, corresponds
with a (total) family of scopes. One only has to either extract the set of
vertices from `P`, or attach the corresponding order operator to `S`.

Note that this is simlar to how we see the set of natural numbers `Nat`. That
is, even though we perceive Nat as a simple set of elements, we intuitively
associate a natural order with it.
