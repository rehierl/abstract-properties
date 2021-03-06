
<!-- ======================================================================= -->
## definitions

As in the context of a graph, one can in principle define **paths of vertices**
over the edges of a relation `R`. Based on that, `aPb` can be understood to be
true, if a path can be formed over the edges of the corresponding relation such
that `a` is a source, and `b` a sink to that path.

In regards to transitivity, an edge `e := (a,b)` can be said to be **missing**,
if a path `aPb` can be formed such that `(e in R)` is not true. Based on that,
such an edge may also be described as an **implicit** edge, if ones focus of
consideration is on the transitive closure `TC(R)`. Similar to that, an edge
that exists in the current relation `R` may be described as an **explicit**
edge since it will also exist in `TC(R)`.

<!-- ======================================================================= -->
## reflexive transitive closure - RTC(R)

If a relation `R` is to be "closed" under reflexivity and transitivity, then
one should first form the transitive closure.

* `S := RTC(R) := RC(TC(R)) := (RC ¤ TC)(R)`
* note - (¤) denotes a functional composition

One aspect is that the transitive closure will potentially add one new edge
for each vertex. Because of that, a subsequent transitive closure would then
have to also test these additional edges. Hence, a matter of computational
complexity.

Note that, as a precursor to order theory, a non-strict order relation is
reflexive and transitive. That is, in order to form an order relation based
on a given relation, one needs to form the reflexive transitive closure from
that relation.

<!-- ======================================================================= -->
## reflexive closure - RC(R)

The reflexive closure `S` is formed from relation `R` by adding all of those
loops that are still missing.

* `S := RC(R) := R + { (a,a) | (a in D) }`

Note that `S` is then guaranteed to be reflexive.

<!-- ======================================================================= -->
## transitive closure - TC(R)

Relation `S := (T,U)` is the transitive closure, or the transitive extension
of relation `R := (D,G)`, if `S` contains `R` and also one edge `(a,b)` for
each path `aPb` that can be formed over the edges of `R`.

* `S := TC(R)`

Note that `S` is then guaranteed to be transitive. (Hence the name).

In order to form the transitive closure `S` of relation `R` one first creates
`S` as a clone of `R`. After that, one adds all the missing edges `aSc` based
on the pair of existing edges `aSb` and `bSc`. The latter step is iteratively
repeated until no more edges can be added.

In some sense, the transitive closure of a relation allows to "directly" answer
if a vertex can be reached from an initial vertex by traversing over existing
edges. That is, while respecting the direction/orientation of these edges!

Given the below relation `R(N,E)`, then `S(N,E2)` can be formed as follows:

```
R(N,E) where N := [1..5]
E := {(1,2),(2,3),(3,4),(4,5)}
==============================
E0 := {(1,2),(2,3),(3,4),(4,5)}
add   {(1,3),(2,4),(3,5)}
E1 := {(1,2),(1,3),(2,3),(2,4),(3,4),(3,5),(4,5)}
add   {(1,4),(1,5),(2,5)}
E2 := {(1,2),(1,3),(1,4),(1,5),(2,3),(2,4),(2,5),(3,4),(3,5),(4,5)}
```

<!-- ======================================================================= -->
## reflexive transitive reduction - RTR(R)

If a relation `R` is to be "reduced" under reflexivity and transitivity, then
one should first from the reflexive reduction.

* `S := RTR(R) := TR(RR(R)) := (TR ¤ RR)(R)`
* note - (¤) denotes a functional composition

Since a reflexive relation has one loop per vertex, an initial transitive
reduction would also have to test these additional edges. Hence, and as before,
the suggested processing order is a matter of computational complexity.

<!-- ======================================================================= -->
## reflexive reduction - RR(R)

The reflexive reduction `S` is formed from a relation `R` by removing all the
edges that being in a vertex and end in the same vertex.

* `S := RR(R) := R \ { (a,a) | (a in D) }`

<!-- ======================================================================= -->
## transitive reduction - TR(R)

As with the above transitive closure, the transitive reduction `S` of a relation
`R` can be understood to be formed based upon an iterative process: First, `S`
needs to be created as the clone of the source realtion `R`. Then, each edge
`aSb` is removed if there is a pair of edges such that `aSx` and `xSb` is true.

Note that a vertex, which is the endpoint of one or more edges, remains to be
the endpoint of one or more edges. That is because the transitive reduction
does not break the relation's connectivity. Because of that, no disconnected
vertices will be formed.

Given the above transitive closure `S(N,E2)`, then `R(N,E)` can be recreated
as follows:

```
TR(S) = R(N,E1)
==============================
E0 := {(1,2),(1,3),(1,4),(1,5),(2,3),(2,4),(2,5),(3,4),(3,5),(4,5)}
drop  {(1,3),(1,4),(1,5),(2,4),(2,5),(2,5),(3,5)}
E1 := {(1,2),(2,3),(3,4),(4,5)}
```
