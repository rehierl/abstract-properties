
<!-- ======================================================================= -->
## total order => ordered sequence

Given a family of scopes that was formed as described before, one can define
a strict total containment order `P := (V,<)` such that ..

* `V := { s1, s2, s3, s4, s5, s6 }` and
* `(<) := (a superset-of b)`

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

Like any other order relation, the transitive reduction of that order can be
visualized as a graph of nodes and edges.

```
(a superset-of b)
================================
s1 -> s2 -> s3 -> s4 -> s5 -> s6
```

For obvious reasons, that graph satisfies the requirements of a node tree.
However, that node tree is special insofar, as except for the single leaf
`s6`, each node has one and only one child node. Consequently, the entire
tree corresponds with a single rooted path `rp` such that contains every
other node within the graph. As such, the tree can be described as
**a path graph**.

* `rp := rp(s6) := (s1,s2,s3,s4,s5,s6)`

At this point one can make the following observation: Even though `rp` pretty
much resembles the initial sequence `s`, it is still such that each element
in `rp` is one of the scopes as defined by the abstract properties `p1` to
`p6`. One therefore still needs to be able to reliably determine the element
within a scope that corresponds with the element within the initial sequence
`s` at the corresponding position.

As can be seen above, and due to the top-to-bottom ordering of the scopes,
these elements can be determined using simple set-based operations:

* `s(i) = oneOf(rp(i) \ rp(i+1))` for `(i in [1,#rp])`
