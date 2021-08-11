
<!-- ======================================================================= -->
# ordered sequences

Assume that there is an ordered sequence `s` of six distinct nodes/cells:
`s := (n1, n2, n3, n4, n5, n6)`.

```
ordered sequence s:
(a next-presequent-to b)
===============================
n1 - n2 - n3 - n4 - n5 - n6 ->|
```

Now assume that the first node `n1` declares property `p1` (i.e. `d(p1) = n1`).
According to the introduction of abstract properties, `p1` extends over all
the nodes in `s` (i.e. `s(p1) = [n1,*] = {n1,..,n6}`). Put differently, the
scope of `p1` contains all the nodes in `s`:

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
```

As before, one can then assume that `n2` declares another property `p2` such
that `d(p2) = n2` and `s(p2) = [n2,*] = {n2,..,n6}`.

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
     -p2-----------------------
```

One can then assume, that each and every node `ni` in `s` declares its very
own property `pi`.

```
n1 - n2 - n3 - n4 - n5 - n6 ->|
-p1----------------------------
     -p2-----------------------
          -p3------------------
               -p4-------------
                    -p5--------
                         -p6---
```

<!-- ======================================================================= -->
## summary : ordered sequence => total order

Based on the scopes of each property, the above system of properties can be
described to define six subsets over the ordered sequence `s`.

```
s     := ( n1, n2, n3, n4, n5, n6 )
------------------------------------------
s(p1) := { n1, n2, n3, n4, n5, n6 } = E(s)
s(p2) := {     n2, n3, n4, n5, n6 } =: s2
s(p3) := {         n3, n4, n5, n6 } =: s3
s(p4) := {             n4, n5, n6 } =: s4
s(p5) := {                 n5, n6 } =: s5
s(p6) := {                     n6 } =: s6
```

Based on this **family of scopes**, a containment order can be defined,
which can be described as **a strict total (containment) order**.

* `P := (V,<)` such that
* `V := { s1, s2, s3, s4, s5, s6 }` and
* `(<) := (a superset-of b)`

<!-- ======================================================================= -->
## summary : total order => ordered sequence

Like any other order relation, the transitive reduction of that order can be
visualized as a graph of nodes and edges. As can be seen, the graph of a total
order satisifies the requirements of a tree. To be more accurate, the tree is
**a path graph**.

```
(a superset-of b)
================================
s1 -> s2 -> s3 -> s4 -> s5 -> s6
```

One can therefore serialize all the nodes within the path graph as the rooted
path `rp`. Based on that, the initial ordered sequence `s` can be recreated,
if each scope in `rp` is replaced by its **characteristic element (CE)**.

* `rp := rp(s6) := (s1,s2,s3,s4,s5,s6)`
* `s(i) = oneOf(rp(i) \ rp(i+1))` for `(i in [1,#rp])`

<!-- ======================================================================= -->
## summary - ordered sequence <=> total order

Due to the above, each ordered sequence can be understood to correspond with
a strict total containment order as described above. Consequently, the same
applies to any substring and even any subsequence that can be formed from an
ordered sequence.

Furthermore, and since intervals over ordered sequences can be used to form
substrings, one can state that any interval over an ordered sequence can be
used to form an induced total suborder.
