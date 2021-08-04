
<!-- ======================================================================= -->
# partial order

An ordered set `P := (V,R)` which is a (simple) preorder and, in addition
to that also **anti-symmetric** can be described as an ordered set that is
associated with a **(simple) partial order** relation. Based on that, the
ordered set can itself be described as a (simple) partial order, or simply
as a **(simple) poset** (i.e. a (simple) partially ordered set).

* any (simple) partial order is an anti-symmetric pre-order

An ordered set `P := (V,R)` which is a strict preorder and, in addition
to that also **anti-symmetric** can be described as a set of elements that
is associated with a **strict partial order** relation. Based on that, the
ordered set can itself be described as a **strict poset** (i.e. a strict
partially ordered set).

* any strict partial order is an anti-symmetric strict pre-order
* any strict partial order is an a-symmetric (strict) pre-order

Note that any partial order is **acyclic**. That is because the order's
transitivity would otherwise force the existence of one or more pairs of
"flipped" edges, which are not allowed in any partial order.

Note that any partial order **may have one or more source vertices** (aka.
"root nodes" or "points of entry"). Also, any partial order relation may
consist of **one or more connected components** (e.g. "a forest of trees").

<!-- ======================================================================= -->
## symmetric, a-symmetric, anti-symmetric

An order relation that has a "flipped" counterpart for each edge in it, is
said to be **symmetric**. Note that, although not required, loops are allowed
in a symmetric order relation.

* symmetric := if `aRb`, then also `bRa`

An order relation that has no such "flipped" counterpart for any of its edges,
is said to be **a-symmetric**. Note that loops are not allowed in an a-symmetric
order relation. That is, an a-symmetric order relation is also irreflexive and
can as such be described as "strict".

* a-symmetric := if `aRb`, then `!bRa`

An order relation that allows "flipped" counterparts for an edge only in
regards to the same vertex, is said to be **anti-symmetric**. Note that loops
are allowed, but not required. That is, an anti-symmetric order relation may
be reflexive or irreflexive.

* anti-symmetric := if `aRb` and `bRa`, then `(a == b)` must be true

Note that the above terms focus on the **orientation** of a graph/relation. That
is, a relation can be considered **undirected** (i.e. symmetric), if each "edge"
represents a pair of "flipped" directed edges. In contrary to that, a relation
can be considered **directed** or **(strictly) oriented** (i.e. a-symmetric or
anti-symmetric), if any "edge" represents one directed edge only.

<!-- ======================================================================= -->
## superset/subset-of

```
V := {
  { 1, 2, 3, 4, 5, 6 }, //- s1
  {    2, 3, 4       }, //- s2
  {       3, 4       }, //- s3
  {       3, 4, 5    }, //- s4
  {             5, 6 }  //- s5
}
```

Given the above family of sets `V`, a poset `P := (V,<=)` can be formed, if the
oder operator is defined based upon the superset-of comparison operator (i.e.
`(a <= b) := (a superset-of b)`). The transitive reduction of that poset can
be visualized as follows:

```
s1° -|-> s2° -|-> s3°
     |-> s4° -|
     |-> s5°
```

Note that there is no edge/path that connects `s2` with `s5` since these sets
are disjoint. Likewise, there is no edge between `s2` and `s4` since these
sets overlap each other. Because of that, `s2` is **incomparable** with `s4`
and `s5` under the `superset-of` order operator. In contrary to that, each
set in the above family of sets is connected with itself since each set is
a subset and therefore also a superset to itself.

Given the above family of sets `V`, a strict poset `P := (V,<)` can be formed,
if the oder operator is defined based upon the strict-superset-of comparison
operation (i.e. `(a <= b) := (a strict-superset-of b)`). This strict poset
can be visualized as follows:

```
s1 -|-> s2 -|-> s3
    |-> s4 -|
    |-> s5
```

Note that there are no reflexive edges since no set is a strict/proper subset
and therefore also no strict/proper superset to itself.
