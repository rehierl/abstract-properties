
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

```
- s := (a, b, c, d, e)
- (a next-presequent-to b)
- R := { (a,b), (b,c), (c,d), (d,e) }
===================================
a -> b -> c -> d -> e
```

```
- s := (a, b, c, d, e)
- (a next-subsequent-to b)
- R := { (e,d), (d,c), (c,b), (b,a) }
===================================
e -> d -> c -> b -> a
```

As mentioned above, a sequence can be read using the next-presequent-to
semantics which is why an ordered sequence can be visualized using `(#s-1)`
edges/arrows.

However, if a sequence is "simple" insofar as multiple occurrences are allowed,
then the definition of "presequent" seems to make no more sense. That is because
an element, from a linguistic understanding, can not be properly presequent to
itself.

If one does recall, that the terms "presequent" and "subsequent" are both
defined based upon the index order of the corresponding sequence, and since
arrows are more strictly bound to the index of each component, one can still
derive a relation from a simple sequence that has repetitions. That is, if
each element is understood to correspond with all the indexes of each of its
occurrences. Derived as such, a graph can be drawn.

```
- s := (a, b, c, b, e)
- (a next-presequent-to b)
- R := { (a,b), (b,c), (c,b), (b,e) }
===================================
     |<-----|
a -> b -|-> c
        |-> e
```

Note that element `c` is indeed subsequent and presequent to `b`.
Because of that, the visualization contains a 2-element cycle.

```
- s := (a, b, c, b, e)
- (a next-subsequent-to b)
- R:= { (e,b), (b,c), (c,b), (b,a) }
===================================
     |<-----|
e -> b -|-> c
        |-> a
```

Drawn as such, the core issue with repetitions is apparent: With the terms
"presequent" and "subsequent" one usually associates an order of succession
that can in general be described as "linear". In contrary to that "expected
notion", the visualization is no longer linear. Instead, it "looks" like
a tree .. a tree that has a cycle .. just because of one single repetition.
Whatever that visualization is supposed to represent, it ain't linear!

Due to the above, one can state that a linear order of succession is
**broken by repetitions**.

On a side note: The visualization isn't just "not linear", it also isn't
hierarchical. After all, "a tree with a cycle" does not make sense either!

```
- s := (a, b, b, d, e)
- (a next-presequent-to b)
- R := { (a,b), (b,b), (b,d), (d,e) }
===================================
a -> b° -> d -> e
```

Note that one could in principle use a simple sequence to define a reflexive
linear relation. However, and since each element would have to be repeated
next subsequent to itself, it would be easier to just point out that the
intended relation is the reflexive closure of the corresponding ordered
sequence.

As a consequence, and except for special purposes (which are not part of this
discussion), repeating elements will by default not be allowed. That is, the
**default case** of sequences in the context of this discussion is that of
**ordered sequences of nodes**.

<!-- ======================================================================= -->
## visual variations

```
- s := (a, b, c, d, e)
- (a next-presequent-to b)
==========================
a - b - c - d - e ->
```

Recall that the overall focus of this discussion is on ordered sequences of
nodes. Also, the orientation of the arrows is by default from left-to-right.
Because of that, the arrow heads can in general be omitted if one keeps in
mind that all the arrows are always directed from left-to-right. An optional
trailing (`->`) can be used to make the default orientation more clear.

```
- s := (n1, n2, n3, n4, n5, n6)
- (n1 next-presequent-to n2)
==========================
n1 n2 n3 n4 n5 n6
```

Sometimes however, even the reduction to simple lines might still cause too
much visual clutter. In such a case, even these lines may be omitted, if the
element references (i.e. (a), (b), ...) are sufficiently distinct such that
one can easily tell them apart. If need be, additional spaces can be used to
help with that aspect.

```
- s := (a, b, c, d, e)
==========================
a, b, c, d, e
```

Alternatively, one can separate the element references from each other using
separator charachters (e.g. comma (,) or semikolon (;)) instead of actual
arrows. Hence, there isn't much of a visual difference between a path graph
and an actual sequence of elements, which is why a semantical expression can
be omitted.

```
(some descriptive title)
=============================
... n3 n4 ... x ... n5 n6 ...
```

In regards to shifting ones focus to specific parts within a squence, or if
only certain patterns are relevant within a sequence, elements that are to be
ignored can be omitted entirely in various different ways.
