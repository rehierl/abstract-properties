
<!-- ======================================================================= -->
# reference-based encodings

In the following kind of encodings, the index-order of a sequence of node
definitions is used to provide references, which will be used to define the
edges in a doctree and to lookup additional data.

Because of that, such reference-based encodings can be understood to separate
the structure definition of a document tree (as connected references) from the
actual content it holds.

<!-- ======================================================================= -->
## transitioning towards node references

```
s := (a,b,c,b,d)   =>   r := (1,2,3,4,5)   =>   r := (1,2,3,2,4)
                        n := (a,b,c,b,d)        n := (a,b,c,d)
```

With complex node definitions in mind, one can clone the node definitions in
`s` into a sequence of node definitions `n`. This sequence will then be used
to provide access to all definitions. By replacing each occurrence of a node
in `s` by the index the corresponding definition has in `n`, one transforms
the former sequence of nodes `s` into **a sequence of (node) references** `r`.
Similar to that, the sequence of definitions `n` can in general be described
as **a data sequence**.

* `(s[i] == n[r[i]])` is true for any `(i in [1,#s])`

Note that the sequence of node definitions `n` may in general still contain
each definition more than once. In such a case, sequence `n` can be reduced
to the first occurrence of each definition while adjusting the references
in `r` accordingly.

<!-- ======================================================================= -->
## general remarks

Note that for each sequence of node references there must be one or more data
sequences which allow to "decode" the node references. However, and since the
focus of this discussion is on the definition of structure, the actual node
definitions are considered non-relevant in the context of this discussion.
Because of that, a data sequence is only assumed to exist as an associated
data sequence, which subsequent discussions will in general ignore.

```
s := (a,b,c,b,d)   =>   r := (3,4,1,4,2)
                        n := (c,d,a,b)
```

Note that, unless otherwise specified, neither the node references nor the
node definitions are required to appear in any particular order. That is, for
as long as the node references in `r` match the corresponding definition in
`n`. However, since a document tree must in general be processed in a specifc
order, one will in general encounter sequences which contain their elements
in some particular order.

```
r := (1,2,3,2,4)
================
     |<-----|
1 -> 2 -|-> 3
        |-> 4
```

Note that the transition towards references has no substantial effect on the
difficulties a path-based encoding has with repeating elements. That is, even
repeating references will add cycles to a graph.

<!-- ======================================================================= -->
## basic constraints

```
s := (a,b,c,d,e)   =>   r := (1,2,3,4,5)
                        n := (a,b,c,d,e)
```

Even though there is no requirement in regards to the length of a sequence of
references `r`, it is in general expected that each node definition in `n` is
referenced at least once, which is why sequence `r` is expected to hold at
least `#n` references.

* `(#n == #N)` is expected to be true
* for `N := { n[r[i]] | (i in [1,#r]) }`
* `(#r >= #n)` is expected to be true.

Note that set `N` is the set of node definitions in `n` for which there is at
least one reference in `r`.

Despite `r` not being upward-restricted in length, any reference in `r` must
be a valid reference to a definition in `n`.

* `(r[i] in [1,#n])` must be true for any `(i in [1,#r])`

<!-- ======================================================================= -->
## the general case

The following discussions will focus on the traversal of document trees which
are assumed to write node references (r), node definitions (n) and additional
data values (d) to sequences in the order in which the nodes will be visited.

```
r := (1,2,3,4,5)   =>   n := (a,b,c,d,e)
n := (a,b,c,d,e)        d := (x,x,x,x,x)
d := (x,x,x,x,x)
```

Because of that, all sequences produced will always have the exact same length.
Furthermore, the sequence of node references will be such that the indexes in
it always appear in strict ascending order.

* `r := (1,...,#N)` and `(#r == #N)`

Consequently, the sequence of node references `r` can in general be omitted.
After all, it will then always be identical to the index-order of `n` and `d`.

Since the actual node definitions in `n` are of no particular interest in the
context of this discussion, the sole focus of the following content will be
on data sequences `d` that hold one data value per node, each of which can
be identified by the index of the corresponding node definition in `n`.

* node `n[i]` must be understood to be associated with data value `d[i]`

<!-- ======================================================================= -->
## explicit vs. implicit encodings

Note that, since a path more or less directly defines the edges in a path
graph, that kind of encoding will be described as a **direct encoding**, or
as an **explicit encoding**. That is because the edges in such an encoding
do not first have to be derived - e.g. from an implicit/embedded encoding
such as compressed data.
