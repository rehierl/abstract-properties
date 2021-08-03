
<!-- ======================================================================= -->
## partial/linear extension

Since following visualization has no edges at all, it can be said to denote
a **degenerated order**. That is, the order relation consists of a set of
vertices and an empty set of edges (i.e. `R := (V,{})`).

```
R0 := (a presequent-to b)    =>    R6 := (a presequent-to b)
=========================    =>    ==========================
a      b      c              =>    a -> b -> c -> d -> e -> f
              d
              e
       f
```

Note that all the vertices in R0 are incomparable with each other.

<!-- ======================================================================= -->

Starting off with R0, one can add an entire set of edges in order to form
a strict poset, which can be visualized as shown below:

```
R1 := (a presequent-to b)
=========================
a -|-> b -|-> c
   |      |-> d
   |      |-> e
   |-> f
```

In contrary to R0, R1 contains fewer vertices that are still incomparable.
Because of that, the addition of a set of edges that results in fewer
incomparable vertices can be described as **a partial extension**.

Based on that, R1 can be described as a partial extension to R0,
just as R5 is a partial extension to R1 and even R0.

If after the addition of even more edges the resulting order has no more
incomparable vertices left, the order extension can be described as
**a linear extension**.

Similar to before, R6 can be described as a linear extension to R5,
and even to R1 and R0.

<!-- ======================================================================= -->

If one would now add the edge `cRd` to the above strict poset, then the
resulting order relation would still be transitive. That is because it
would then contain the edges `bRc` and `cRd`, as well as `bRd`.

```
R2 := (a presequent-to b)
=========================
a -|-> b -|-> c -->|
   |      |-> d <--|
   |      |-> e
   |-> f
```

However, the visual representation as a graph-based relation, that is based
upon the transitive reduction of an order relation, would no longer have the
edge `bRd`. That is because `bRd` can now be considered the transitive edge
that can be formed from the edges `bRc` and `cRd`.

```
R3 := (a presequent-to b)
=========================
a -|-> b -|-> c -> d
   |      |-> e
   |-> f
```

Note that the edge `bRd` is however still an edge in the underlying order
relation. It simply is no longer an edge in the visual transitive reduction
that is being visualized.

<!-- ======================================================================= -->

Similar as before, and if now the edge `dRe` would be added to the changed
poset, the visual representation would have to be updated as follows:

```
R4 := (a presequent-to b)
=========================
a -|-> b -> c -> d -> e
   |-> f
```

<!-- ======================================================================= -->

If one now adds the edge `bRf` to the updated relation, one would end up
with the following representation that has the same amount of incomparable
vertices.

```
R5 := (a presequent-to b)
=========================
a -> b -|-> c -> d -> e
        |-> f
```

That is because `bRf` does not state anything in regards to the relationship
of the vertices `f` and `c`, or any of those vertices that are subsequent to
it. Because of that, these vertices remain incomparable with each other.

<!-- ======================================================================= -->

If one now adds the edge `eRf`, then one would end up with the visual
representation that has no more incomparable vertices. Because of that the
addition of this last edge can be described as a linear extension.

```
R6 := (a presequent-to b)
==========================
a -> b -> c -> d -> e -> f
```

<!-- ======================================================================= -->
## set of nodes => ... => "pre-order" trace

The overall transition from R1 to R5 can be understood to describe the addition
of a "child order" to an unordered tree. That is R5 can be said to visualize
the true node order of an "ordered tree".

The transition after that, from R5 to R6, can be understood to describe the
addition of "pre-order" edges, which is why R6 can be understood to represent
the pre-order trace of the "ordered tree" R1.

Note that the above transitions (from R0, over R1 and R5, to R6) represent the
very epicenter of this discussion. Because of that, the linear extension of an
"ordered tree" into its "pre-order trace" will still be discussed in greater
detail.
