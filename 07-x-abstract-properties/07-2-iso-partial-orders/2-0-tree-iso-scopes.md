
<!-- ======================================================================= -->
# node tree <=> order of scopes

Given a node tree `T := (N,E)` ..

```
(a next-presequent-to b)
========================
n1 --|-> n2 --|-> n4
     |-> n3   |-> n5
```

 **a family of scopes** `S` can be formed
based on the concept of abstract properties.

```
s1 := s(p1) := { n1, n2, n4, n5, n3 } = E(T)
s2 := s(p2) := {     n2, n4, n5     } = [ni,*]
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

* `S := { si | (si = [ni,*]) such that (i in [1,#V(T)]) }`

Based on `S` **a strict partial containment order of scopes** `P` can be formed,
which may also be described as **a scope order**, or as **an order of scopes**.

* `P := (S,<)` such that
* `(a < b) := (a proper-superset-of b)`

Like any other ordered set, the containment order can be visualized as a graph.
As can be seen below, the graph of such an order is itself **a node tree** such
that each node `si` in it is a scope `[ni,*]` over the intial node tree `T`.

```
sem(P) := (a proper-superset-of b)
==================================
s1 --|-> s2 --|-> s4
     |-> s3   |-> s5
```

One can therefore form a graph `G := (S,E)` as the transitive reduction of
the order relation of `P`. A node tree `T*` can then be formed, if each scope
`si` in `G` is replaced by its **characteristic element ce(si)**, while also
updating all the edges in `G` according to each replacement. Based on that,
one can determine, that the newly formed node tree `T*` is equal to `T`.

* `T* := (N,E)` such that
* `N := { ce(si) | (si in S) }`
* `E := { (ce(si),ce(sj)) | ((si,sj) in E(G)) }`
* note - `(T* == T)` is true

Consequently, any node tree can be said to be **isomorphic** to a strict
partial containment order. That is, a containment order can be formed from
the initial node tree, which can then be used to recreate that node tree.

<!-- ======================================================================= -->
## remarks

Note that each strict total containment order `P`, as formed above, corresponds
with a (total) family of scopes. One only has to either extract the set of
vertices from `P`, or attach the corresponding order operator to `S`.

Note that this is simlar to how we see the set of natural numbers `Nat`. That
is, even though we perceive Nat as a simple set of elements, we intuitively
associate a natural order with it.

Note that the scope `s(p1)` of property `p1` is equal to the set of nodes in
the **induced subtree** `T[n1]`. Generalized, the scope `s(pi)` of property
`pi` is equal to the set of nodes in the induced subtree `T[ni]`. Because of
that, the family of scopes `S` is a set that contains the set of nodes of
each induced subtree in `T`.

Note that one can not simply underline the set of nodes in the scopes of an
arbitrary induced subtree. That is because there is no total order over the
nodes in tree `T`. Because of that, drawing lines under the visualization
of a tree is in general ambiguous. However, since the sets of nodes of the
induced subtrees are **either disjoint ex-or related**, one can still draw
boxes around the nodes in the scope of a property.
