
<!-- ======================================================================= -->
# cyclic vs. acyclic preorders

```
|---------->|
a --> b --> c
```

If one would add the edge `cRa` to the above strict preorder, then the resulting
relation can be said to contain the cycle `(c,a,b,c)`. The resulting relation
can therefore be described as being **cyclic**.

```
|---------->|
a --> b --> c
|<-- cycle -|
```

However, since the resulting relation is no longer transitive, one would have
to perform a transitive closure over the modified relation. This in order to
re-establish transitivity. In a first iteration one could add the following
edges:

* `cRb` since `cRa` and `aRb` both exist
* `bRa` since `bRc` and `cRa` both exist

```
|---------->|
a --> b --> c
|<-- cycle -|
|<----|<----|
```

Since the modified relation is still not transitive, one would have to continue
to add even more edges:

* `aRa` since `aRb` and `bRa` both exist
* `bRb` since `bRa` and `aRb` both exist
* `cRc` since `cRa` and `aRc` both exist

```
|---------->|
a° -> b° -> c°
|<-- cycle -|
|<----|<----|
```

Consequently, the addition of an edge that establishes a cycle will result in
having to add one or more loops in order to re-establish transitivity. This
would however be in conflict with the "irreflexive" characteristic of a strict
preorder. Because of that, **any strict preorder is acyclic**. An irreflexive
preorder has therefore no cycles.

In contrary to that, a simple preorder, may contain one or more cycles of two
or more distinct vertices (while ignoring loops). Put differently, a simple
preorder may be cyclic.

Note that a cyclic preorder is not required to have a pair of edges `aRb` and
`bRa` for each pair of connected vertices. That is, a cyclic preorder is neither
required to be symmetric nor anti-symmetric.
