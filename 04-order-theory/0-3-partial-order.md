
<!-- ======================================================================= -->
# partial order

An ordered set `P := (V,R)` which is a (simple) preorder and, in addition
to that also **anti-symmetric** can be described as an ordered set that is
associated with a **(simple) partial order** relation. Based on that, the
ordered set can itself be described as a (simple) partial order, or simply
as a **(simple) poset** (i.e. a (simple) partially ordered set).

* a (simple) partial order is an anti-symmetric pre-order

An ordered set `P := (V,R)` which is a strict preorder and, in addition
to that also **anti-symmetric** can be described as a set of elements that
is associated with a **strict partial order** relation. Based on that, the
ordered set can itself be described as a **strict poset** (i.e. a strict
partially ordered set).

* a strict partial order is an anti-symmetric strict pre-order
* a strict partial order is an a-symmetric (strict) pre-order

<!-- ======================================================================= -->
## symmetric, a-symmetric, anti-symmetric

An order relation that has a "flipped" counterpart for each edge in it, is
said to be **symmetric**. Note that, although not required, loops are allowed
in a symmetric order relation.

* symmetric := if `aRb`, then also `bRa`

An order relation that has no such "flipped" counterpart for any of its edges,
is said to be **a-symmetric**. Note that loops are not allowed in an a-symmetric
order relation. That is, an a-symmetric order relation is also irreflexive and
as such "strict".

* a-symmetric := if `aRb`, then `!bRa`

An order relation that allows "flipped" counterparts for an edge in only in
regards to the same vertex, is said to be **anti-symmetric**. Note that loops
are allowed, but not required. That is, an anti-symmetric order relation may
be reflexive or irreflexive.

* anti-symmetric := if `aRb` and `bRa`, then `(a == b)` must be true

Note that the above terms focus the **orientation** of a graph/relation.
That is, a graph is considered **undirected** (i.e. symmetric), if any edge
represents a pair of directed edges. In contrary to that, a graph is considered
**directed** (i.e. a-symmetric or anti-symmetric), if any edge represents one
directed edge only.

Note that any such relation may have **several source vertices**
(i.e. root nodes, e.g. forests of trees).

<!-- ======================================================================= -->
## superset-of, strict-superset-of

```
S := {
  { 1, 2, 3, 4, 5, 6 }, //- s1
  {    2, 3, 4       }, //- s2
  {       3, 4       }, //- s3
  {       3, 4, 5    }, //- s4
  {             5, 6 }  //- s5
}
```

Given the above family of sets, a poset `P := (S,<=)` can be formed, if the
oder operator is defined based upon the superset-of comparison operation (i.e.
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

Given the above family of sets, a strict poset `P := (S,<)` can be formed,
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

<!-- ======================================================================= -->
## superset/subset-of vs. cyclic/acyclic

Except for loops, an order relation that is defined based upon the subset-of
or the superset-of comparison operator is **inherently acyclic**.

For such a relation to have a cycle (note - of two or more sets), a set `a`
would have to be a subset to another set `b` (note - both are distinct), which
is why `(a subset-of b)` and `(#a < #b)` is then true.

However, in order to establish a cycle, `a` would also have to be a superset
to `b`. This can however never be true since `a` would then also need to have
one or more elements in addition to those in `b`.

The resulting conflict is therefore that a set can not have fewer and, at the
same time, more elements than another set. Because of that, a set can not be
a subset and a superset to another set.

Consequently, an order that is defined based upon the (strict-) subset-of
comparison operator, or an order that corresponds with such an order, can
not have any cycles and is as such acyclic.
