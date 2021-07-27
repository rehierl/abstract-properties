
<!-- ======================================================================= -->
## reflexive relations

```
R (reflexive)    S (not reflexive)    T (?)
=============    =================    ======
a° -> b°         a° -> b              a -> b
```

Note that, if edges of the form `(a,a)` (aka. loops or "reflexive edges") are
visualized as `a°`, then relation `R` is reflexive, whereas `S` is not. That
is because `R` has a loop for each vertex in it. In contrary to that, `S` is
missing a loop for `b`.

However, since `(b,b)` is a loop in `R`, relation `R` can be said to be the
reflexive closure of `S` - i.e. `(R == RC(S))` is true.

In contrary to that, `S` is no reflexive reduction of `R` since `(a,a)` is
an edge in `S` - i.e. `(S != RR(R))` is true.

Note that, from a less strict perspective, relation `T` can be said to be
reflexive, iff one is aware that an implicit reflexive closure can and would
have to be performed first. Likewise, relation `R` can be considered
irreflexive, iff one keeps in mind that a reflexive reduction can and would
have to be performed first. In contrary to that, relation `S` can neither be
considered reflexive nor irreflexive due to its "mixed" definition.

<!-- ======================================================================= -->
## transitive relations

Recall that a relation is said to be transitive, if it
has an edge `aRc` for each pair of edges `aRb` and `aRb`.

```
R (transitive)     S (not transitive)
===============    ==================
a -|-> b -|-> c    a -> b -> c
   |----->|
```

Note that relation `R` is transitive whereas `S` is not. That is because `(a,c)`
is no edge in `S` even though `(a,b)` and `(b,c)` are both edges in `S`.

However, since `(a,c)` is an edge in `R`, relation `R` can be said to be the
transitive closure of `S` - i.e. `(R == TC(S))` is true.

Likewise, and since `(a,c)` is no edge in `S`, relation `S` can be said to be
the transitive reduction of `R` - i.e. `(S == TR(R))` is true.

Note that `(R == (TR ¤ TC)(R))` is not true in general since R may already
have some of the "transitive" edges. Likewise, and for the same reason,
`(R == (TC ¤ TR)(R))` is not in general true.

Note that, from a less strict perspective, relation `S` can be considered
transitive, iff one keeps in mind that a transitive closure can and would
have to be performed first.

<!-- ======================================================================= -->
## (ordered) sequences

```
- s := (a, b, c, d, e)
- (a next-presequent-to b)
========================
a -> b -> c -> d -> e
```

Ordered sequences can be visualized, if an arrow is drawn to denote the next
subsequent element of each element.

```
          |--------->|
          |-------------->|
a -|-> b -|-> c -|-> d -> e
   |             |------->|
   |--------->|
   |---------------->|
   |--------------------->|
```

As can be seen, the transitive closure of a relation is difficult, if not
impossible to visualize and clearly understand. That is because the amount of
edges tends to blow up the more nodes and initial edges there are. Because of
that, if not clear from a given context, and if applicable, one should always
point out that what is visualized is the transitive reduction of the actual
relation.

```
- (a presequent-to b)
=====================
a -> b -> c -> d -> e
```

If the transitive closure of the next-presequent-to relation of an ordered
sequence is formed, then the edges of that closure have **changed semantics**
in regards to the initial relation. That is, the next-presequent-to semantics
no longer applies. Instead, the edges in the transitive closure express that,
in the initial relation, a path exists which connects both of the endpoints of
each edge in the closure. Because of that, the next-presequent-to semantics
morphes into the more generic presequent-to semantics.

* `(a next-presequent-to b) => (a presequent-to b)`

Based on the semantical expression associated with a particluar visualization
one can determine that the visualization is supposed to represent the transitive
reduction of the actual relation. One should therefore use the semantical
expression specified **as a hint** towards what is being visualized.

* "presequent-to" does not add up with only next items being connected
* the visualization can be assumed to visualize a transitive reduction
* one needs to think in regards to the transitive closure

Note that the (default/generic) next-presequent-to semantics suggests to read
a visualization "as is".

The issue: Most of the times, the semantical expression of an edge is considered
to be "known from its context" and therefore neglected. Needless to state that
that is a source of confusion on both sides (i.e. on the side of an author, and
on the side of the reader audience).

<!-- ======================================================================= -->
## (simple) sequences
