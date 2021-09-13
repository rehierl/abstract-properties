
<!-- ======================================================================= -->
# There are more pre-order traces

The pre-order trace of a node (i.e. `trace(n)`) is a substring to the traces
of its ancestors and therefore also a substring to the trace of its tree (i.e.
the pre-order trace of the tree's root). That is because the pre-order rule
(i.e. `n -> c × s`) states that the former child nodes `c(n)` will be inserted
in between node `n` and its former subsequent siblings `s(n)`.

* `trace(n) := n × trace(fc) × ... × trace(lc)`

Because of that, a document tree can be defined as a pure sequence of tags.
That is, all the descendants of a node are prefixed by a start- and suffixed
by an end-tag. Such a pair of tags can therefore be understood to enclose the
descendants of a node. And since a node is always the previous sibling of its
former first child, each node can be "pushed" into its start-tag.

```
pre-order rule                                       tag-based syntax
===============   =>   ======================   =>   ================
n -> ( c × s )         ( n <tag> c </tag> s )        ( <n> c </n> s )
```

The following content will shift the focus from a node and its descendants
(i.e. `( n × c )`) towards a node and its subsequent siblings, including all
of their descendants (i.e. `( n × c × s )`). As such, the following discussion
will extend one's view on pre-order traces.

<!-- ======================================================================= -->
## the pre-order traces of induced subtrees

```
             p
             |
 =========================
 | .. |      |      | .. |
 fs  ps |---------| ns  ls
        |    n    |
        |    |    |
        | ======= | <- the induced
        | | ... | | <- subtree tU[n]
        | fc   lc |
        |---------|
```

The focus of this discussion is that the pre-order trace of a node contains a
node and all of its descendants. As such, the trace of a node corresponds with
an induced subtree `t[n]` in the underlying un-ordered tree. Because of that,
the pre-order trace of a node can in general be described as **the pre-order
trace of an induced subtree**.

It is therefore more accurate to describe the trace of a node `trace(n)` (as
discussed so far) as the trace `traceU(n)` of the induced subtree `tU[n]` in
the (U)n-ordered tree `tU`.

* `traceU(n) := n × traceU(fc) × ... × traceU(lc)`

This perspective does obviously not include all the descendants of a node in
the ordered tree. After all, the subsequent siblings and their descendants,
also count towards the descendants of a node in an ordered tree. Because of
that, a node can be understood to define an induced subtree `tO[n]` in the
(O)rdered tree `tO`.

```
                the induced subtree tO[n]
                 |---------------------|
p => (fs .. ps) =|=> n =|=> (fc .. lc) |
                 |      |=> (ns .. ls) |
                 |---------------------|
```

A node can therefore in general be understood to define two induced subtrees:
(1) an induced subtree in the un-ordered tree `tU[n]`, and (2) an induced
subtree in the ordered tree `tO[n]`. Based on that, a node can be said to
be associated with two distinct pre-order traces: (1) a pre-order trace in
regards to the un-ordered tree `traceU(n)`, and (2) a pre-order trace in
regards to the ordered tree `traceO(n)`.

* (1) `tU[n] <=> traceU(n)`, and (2) `tO[n] <=> traceO(n)`

<!-- ======================================================================= -->
## the pre-order trace of a node in an ordered tree

```
<r> ..                  <n> ..        </n> ..      </p> .. </r>
-|-----------------------|--------------|------------|-------|-
 r × .. p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) × ..
-----------------------|----------------|------------|-------|-
                       |<- traceU(n)  ->|            |
                       |<- prefix     ->|<- suffix ->|
                       |<- traceO(n)               ->|
```

Since applying the pre-order rule to node `n` results in prefixing the sequence
of subsequent siblings by the sequence of its child nodes, the pre-order trace
`traceU(n)` is a prefix to `traceO(n)`. That is, the pre-order trace `traceO(n)`
of a node results from appending some suffix to a node's pre-order trace
`traceU(n)` in the un-ordered tree.

* `traceO(n) := (prefix × suffix)`, where `(prefix == traceU(n))`
* `(traceU(n) prefix-of traceO(n))` is true

One might now notice that the pre-order trace of a node `traceU(n)` is followed
by the pre-order trace of its next sibling subsequent `traceU(ns)`. After all,
node `n` is the previous sibling `ps` to its next sibling `ns`. The pre-order
trace of a node `traceO(n)` in regards to an ordered tree is therefore a string
of pre-order traces in regards to the un-ordered tree. In other words, the
pre-order trace `traceO(n)` begins with its pre-order trace `traceU(n)`,
followed by the traces of its subsequent siblings, until that sequence ends
with the trace of its last subsequent sibling `traceU(ls)`.

Because of that, the pre-order trace of a node `traceO(n)` can in general be
described as **a string/sequence of pre-order traces**.

* `traceO(n) := traceU(n) × traceU(ns) × ... × traceU(ls)`

As such, the pre-order trace `traceO(n)` can be understood to be formed based
on generic units. Since these **building blocks** of a tree's pre-order trace
`traceO(n)` are traces in regards to the un-ordered tree, this seems to suggest
that a section has some level of granularity. These sub-traces could therefore
be seen as the atoms (i.e. as smallest indivisible units) of a section.

Note that the hidden attribute/property will turn this intuition into a fact.

<!-- ======================================================================= -->
## relationships: traceU() => traceO()

In order to summarize the above ...

```
.. × p × (fs .. ps ..) × n × (fc .. lc ..) × (ns .. ls ..) × ..
                       |-traceU(n)/prefix--|-suffix--------|
                       |-traceO(n)-------------------------|
```

The pre-order trace of a node `traceU(n)` is formed by prefixing the sequence
of pre-order traces of its child nodes by itself (i.e. prefixed by node `n`).

* `traceU(n) := n × ( traceU(fc) × ... × traceU(lc) )`

The pre-order trace of a node `traceO(n)` is formed from one or more pre-order
traces in regards to the un-ordered tree.

* `traceO(n) := traceU(n) × ( traceU(ns) × ... × traceU(ls) )`

At this point, one might already observe the following ...

* `traceU(n) := n × traceO(fc)`
* `traceO(n) := traceU(n) × traceO(ns)`

<!-- ======================================================================= -->
## relationships: a recursive definition

```
.. × p × (fs .. ps ..) × n × (fc .. lc ..) × (ns .. ls ..) × ..
                       |-traceU(n)---------|-traceO(ns)----|
                       |-traceO(n)-------------------------|
```

Since the pre-order trace of a node `traceU(n)` is followed by the pre-order
traces of its former subsequent siblings, the same applies to every other node.
This allows for a recursive description of the pre-order trace `traceO(n)`.

* `traceO(n) := traceU(n) × traceO(ns)`
* `traceO(ns) := traceU(ns) × ... × traceU(ls)`

Based on that, the pre-order trace of a subsequent sibling (e.g. `traceO(ns)`)
can be described as **a suffix** to the pre-order trace of a presequent sibling
(e.g. `traceO(ps)`). And since these traces are ordered sequences of nodes,
each of which can be seen as simple sets of nodes, the trace of a subsequent
sibling can be understood as **a (proper) subset** to the trace of a presequent
sibling.

* given an ordered sequence of siblings `s := (n1, ..., nk)`, then ...
* `(traceO(ni) suffix-of traceO(nj))` is true if `(i > j)`
* `(traceO(ni) subset-of traceO(nj))` is true if `(i > j)`

Note that this corresponds with a set-based definition of an ordered sequence.
That is, a sequence `s` can be understood to be defined based on a family of
sets `S` such that each set of nodes in it is related to every other set (i.e.
a total order of sets of nodes).

```
       s  := ( n1, n2, ..., nk )
==================================
S := { s1 := { n1, n2, ..., nk },
       s2 := {     n2, ..., nk },
       .. :=           ...      ,
       sk := {              nk } }
==================================
S := { s1, s2, ..., sk }
```

<!-- ======================================================================= -->
## relationships: traceO() => traceU()

```
.. × p × (fs .. ps ..) × n × (fc .. lc ..) × (ns .. ls ..) × ..
                       |-traceO(n)-------------------------|
                       |-traceU(n)---------|-traceO(ns)----|
```

Since the pre-order trace `traceO(ns)` is a suffix to `traceO(n)`, trace
`traceU(n)` can be formed from `traceO(n)` by removing `traceO(ns)` as a
suffix.

* `traceU(n) := traceO(n) \ traceO(ns)`

Note that this can be understood to allow a removal-based definition of the
section of a heading. That is, if rank values are taken into account. With
that in mind, the pre-order trace `traceO(n)` of heading `n` can be seen as
the default scope of heading `n`, whereas the rank value of heading `ns`, or
some other subsequent sibling heading, can be understood to prematurely end
that scope by removing its own pre-order trace `traceO(ns)` (i.e. a suffix)
from `traceO(n)`.

Note that, based on the above, a scope can be understood to be forwards
oriented (i.e. along the edges), whereas rank values need to be understood
to be backwards oriented (i.e. against the edges). Both perspectives can
also be understood to be in regards to the corresponding areas of effect.

<!-- ======================================================================= -->
## relationships: ancestor-descendants

```
.. × p × (fs .. ps ..) × n × (fc .. lc ..) × (ns .. ls ..) × ..
                       |-traceU(n)---------|
                           |-traceO(fc)----|
```

Similar to the above, the pre-order trace of a node `traceU(n)` can be formed
from the pre-order trace of its first child `traceO(fc)`.

* `traceU(n) := n × traceO(fc)`
* `traceO(fc) := traceU(fc) × ... × traceU(lc)`

Note that one could take this to suggest that the section of a section element
`n` could prematurely end just like the default scope of a heading. The issue
here is that a hidden attribute set on node `n`, in order to fold its section,
is defined to affect each and every node in `traceU(n)`.

<!-- ======================================================================= -->
## general observations

```
 un-ordered trees            ordered trees
===================         ===================
         p             |     n -|-> (fc .. lc)
         |             |        |-> (ns .. ls)
 -----------------     | 
 | .. |  |  | .. |     | 
 fs  ps  n  ns  ls     | 
         |             | 
      -------          | 
      | ... |          | 
      fc   lc          | 
```

Due to the above, the pre-order trace of a node is in general still
**a substring to the pre-order traces of its ancestors**.

* if `(a ancestor-of n)` is true, then ...
* `traceU(n) substring-of traceU(a)` - in the un-ordered tree
* `traceU(n) substring-of traceO(a)` - in both trees
* `traceO(n) substring-of traceU(a)` - in the un-ordered tree
* `traceO(n) substring-of traceO(a)` - in both trees

Note that, in regards to `traceU(a)`, node `n` needs to be a child, or the
descendant of a child of its ancestor `a`. In the above patterns, imagine
that node `n` is represented `fc` (or `ns`), and that node `n` represents
one of its ancestors `a`.

Note that one might assume that the section of a heading `hi`, which has a
subsequent sibling heading `hj`, can be expressed as the result of removing
a suffix (e.g. `traceO(hj)`) from the heading's pre-order trace `traceO(hi)`.
That is, assumed that the rank of heading `hj` is greater or equal to the
rank of heading `hi`.

* `section(hi) := (traceO(hi) \ traceO(hj))` if `(rank(hi) <= rank(hj))`

Note that, since `traceO(fc)` is a suffix to `traceU(n)`, and since `traceO(n)`
is a suffix to `traceO(ps)`, the above can be seen as the formal basis which
allows to define a hierarchy of traces, which could then be used to define
the outline of a document tree (i.e. its hierarchy of sections).

Note that one might see `traceU(n)` as the "Characteristic Element (CE)", or
as the "Characteristic Subset (CSS)" of `traceO(n)`. (See the correspondence
between node trees and partial orders).
