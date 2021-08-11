
<!-- ======================================================================= -->
## ordered sequence => total order

The scopes of abstract porperties can be used to define a family of scopes.

```
s  := ( n1, n2, n3, n4, n5, n6 )
--------------------------------
s1 := { n1, n2, n3, n4, n5, n6 }
s2 := {     n2, n3, n4, n5, n6 }
s3 := {         n3, n4, n5, n6 }
s4 := {             n4, n5, n6 }
s5 := {                 n5, n6 }
s6 := {                     n6 }
```

Based on these sets of elements, a containment order can be defined as follows.

* `P := (V,<)` such that
* `V := { s1, s2, s3, s4, s5, s6 }` and
* `(<) := (a superset-of b)`

Obviously, the set of vertices `V` of the above order is a set of sets, which
can be described as a set/family of sets. Based on the nature of these elements,
the set of vertices can be described as **a family of scopes**.

Based on that, the set of vertices `V` is such that each pair of distinct scopes
is properly related. That is, one scope in such a pair is a proper subset to the
other. Consequently, any two scopes within the containment order is comparable
under the order operator. Because of that, the containment order has
**no pair of incomparable (distinct) vertices**.

Furthermore, the oder operator is such that one can tell for any pair of scopes
which is super-ordinate to the other. That is, as far as distinct scopes are
concerned, the order operator is directional. Consequently, the underlying order
relation has one and only one edge for each pair of distinct vertices. The order
relation is therefore **trichotomous**.

Finally, if a set `a` has a proper subset `b`, and if that set has itself a
proper subset `c`, then set `c` is also a proper subset of superset `a`.
Because of that, the above containment order is also **transitive** and as
such an actual ordered set of elements.

Note that the above containment order `P` is **a strict total order**.
