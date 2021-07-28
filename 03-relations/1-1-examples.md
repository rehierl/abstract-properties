
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
