
<!-- ======================================================================= -->
# reference-based encodings

In the following kind of encodings, the index-order of a sequence of node
definitions is used to provide anchor points for node references, which will
be used to define the edges in a document tree, and to lookup additional data.
Because of that, such reference-based encodings can be understood to separate
the structure definition of a document tree (as interconnected references)
from the actual content it holds.

<!-- ======================================================================= -->
## transitioning towards node references

```
s := (a,b,c,b,d)   =>   r := (1,2,3,4,5)   =>   r := (1,2,3,2,4)
                        n := (a,b,c,b,d)        n := (a,b,c,d)
```

With complex node definitions in mind, one can clone the nodes in `s` into a
sequence of node definitions `n`, which will then be used to provide access
to all of these nodes. By replacing each occurrence of a node in `s` by the
index that node has in `n`, one transforms the former sequence of nodes `s`
into **a sequence of (node) references** `r`. Similar to that, the sequence
of nodes `n` can in general be described as **a data sequence**.

* `(s[i] == n[j])` is true for any `(i in [1,#s])` and `(j := r[i])`

Note that the sequence of nodes `n` may in general still contain each node
more than once. In such a case, sequence `n` can be reduced to an ordered
sequence of nodes while adjusting the references in `r` accordingly.

<!-- ======================================================================= -->
## general remarks

Note that for each sequence of node references there must be one or more data
sequences which allow to "decode" the references in it. However, and since the
focus of this discussion is on the definition of structure, the actual node
definitions are considered non-relevant in the context of this discussion.
Hence, an actual node sequence is only assumed to exist as an associated data
sequence, which subsequent discussions will in general ignore.

```
s := (a,b,c,b,d)   =>   r := (3,4,1,4,2)
                        n := (c,d,a,b)
```

Note that, unless specified otherwise, neither the node references nor the
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

Note the **backwards-oriented** edge `(3,2)` which finalizes the cycle. In
contrary to that, all the other edges (e.g. `(2,3)`) are **forwards-oriented**
towards the last reference in `r`. Consequently, there are certain advantages
in having a specific order of references, since cycles can then be detected
by simply comparing the values of node references.

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

* for `N := { n[r[i]] | (i in [1,#r]) }`
* `(#N == #n)` and `(#n <= #r)` are both expected to be true

Note that set `N` is the set of node in `n` for which there is at least one
reference in `r`. Simply put, `N` is the set of all referenced nodes.

Despite `r` not being upward-restricted in length, any reference in `r` must
be a valid reference to some node in `n`. Exceptions may be defined such that
some invalid references are allowed, which may denote a root or a leaf.

* `(r[i] in [1,#n])` must be true for any `(i in [1,#r])`

<!-- ======================================================================= -->
## the general case

The following discussions will focus on the traversals of document trees which
are assumed to write node references (r), node definitions (n) and additional
data values (d) to sequences in the order in which the nodes are visited.

```
r := (1,2,3,4,5)   =>   n := (a,b,c,d,e)
n := (a,b,c,d,e)        d := (x,x,x,x,x)
d := (x,x,x,x,x)
```

Because of that, all sequences produced will always have the exact same length.
Furthermore, the sequence of references `r` will be such that the indexes in
it always appear in strict ascending order. That is, the ordered sequence of
references `r` reflects the trace of nodes `n`.

* `r := (1,...,#N)` and `(#r == #N)`

Consequently, the sequence of node references `r` can in general be omitted.
After all, it will then match the identical index-orders of `n` and `d`.

Since the actual nodes in `n` are of no particular interest in the context
of this discussion, the sole focus of the following content will be on data
sequences `d` that hold one value per node, each of which can be identified
by the index of the corresponding node in `n`.

* node `n[i]` must be understood to be associated with data value `d[i]`

<!-- ======================================================================= -->
## explicit vs. implicit encodings

Note that, since a path more or less directly defines the edges in a path
graph, that kind of encoding may be described as a **direct encoding**, or
as an **explicit encoding**. That is because the edges in such an encoding
do not first have to be derived - e.g. from an implicit/embedded encoding
such as compressed data.
