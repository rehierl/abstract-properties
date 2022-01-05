
<!-- ======================================================================= -->
# a child-based encoding

```
s := (a,b,c,d)   =>   n := (a,b,c,d)   =>   n := (a,b,c,d) - node definitions
                      r := (1,2,3,4)        r := (1,2,3,4) - parent nodes
                                            d := (2,3,4,x) - child nodes
```

As mentioned before, a sequence of nodes `s` allows to form a sequence of node
definitions `n` and a sequence of references `r`. In addition to that, a second
sequence of references `d` can be defined such that it holds the index of a
child of the corresponding node in `r`.

Note that ..

* `n` is expected to be an ordered sequence
* `(#r >= #n)` is expected to be true
* `(#r == #n)` is not (yet) required to be true
* `(#r == #d)` must be true
* `(r[i] in [1,#n])` and `(d[i] in [1,#n])` must be true
* `(r[i] != d[i]` must be true - i.e. no loops
* `r[i]` is defines the parent of `d[i]`

Combined, sequences `r` and `d` can be understood to define a set of edges `E`
and therefore to define a graph `G(N,E)`.

* `N := { r[i] | (i in [1,#r]) }`
* `E := { (r[i],d[i]) | (d[i] in [1,#n]) and (i in [1,#r]) }`
* `sem(G) := (a parent-of b)`

Note that `G` is strictly speaking a graph of index values such that each index
in it corresponds with a node in `n`. As a matter of simplification these index
values will in general be treated as actual nodes.

<!-- ======================================================================= -->
## remarks

Note that, due to its shortcomings (as discussed below), this encoding scheme
will not be discussed in detail. It needs to be understood as a transitional
encoding from the path-based to a parent-based encoding.

Note that each index value in `d` is greater than the corresponding index in
`r`. Because of that, this scheme may be described as being **forward-oriented**.
Hence, an index value of `#n+1` would be appropriate for the invalid reference
(x), which would then be an overall non-constant reference.

* `forward-oriented := (r[i] < d[i])` for all `(i in [1,#r])`

Note that the orientation **depends on the tree traversal** algorithm that was
used to form the sequences, which will in general be a "root to leaf" oriented
traversal (i.e. in tree order).

Note that, in this encoding scheme, sequence `r` can in general be described
as a sequence of parent nodes, even though one node (e.g. `r[4]` from above)
is not defined as a parent. After all, it is associated with an invalid child
reference (x).

Note that an index value (x) may be used to denote an invalid index such that
it does not map to any node in `n`. This value will usually point to before
the first (i.e. a constant value of `0`), or to after the last node (i.e. a
non-constant value of `#n+1`) in `n`.

<!-- ======================================================================= -->
## con - any number of child nodes

Since each node in a tree may in general have any number of child nodes, it
is quite obvious why this encoding scheme has significant drawbacks. After all,
it expects each node to have either no, or one child only. That is, if `r` is
required to correspond with the index-order of `n`.

```
s := (a,b,c,d)   =>   n := (a,b,c,d)
                      r := (1,2,3)
                      d := (2,3,4)
```

However, if it would be allowed for `r` to deviate from that index-order, at
the cost of always having to specify all the sequences, then sequence `r` may
even end up being shorter in length. That is because leaf nodes would no longer
have to be specified.

```
a                n := (a,b,c,d,e,f)
----------   =>  r := (1,1,1,1,4)
b  c  d  e       d := (2,3,4,5,6)
     ---
      f
```

On top of that, one would no longer be restricted to one child per parent since
one could then repeat references in `r` and, based on that, specify subsequent
siblings with each repeating parent reference.

<!-- ======================================================================= -->
## pro - allows to encode a child order

```
s := (a,b,c,d)   =>   n := (a,b,c,d)
                      d := (2,3,4,x)
```

If one assumes the general case (i.e. `r` corresponds with the index-order of
`n`), then `r` can be omitted. However, as discussed above, the sequence of
child references `d` can then only be used to define a path graph, or a forest
of paths.

```
s := (a,b)   =>   n := (a,b,c,d)
t := (c,d)        d := (2,x,4,x)
```

Despite that, this encoding scheme could still be used to explicitly encode the
child order of a document tree. After all, the sequences of child nodes of a
parent are disjoint.

Note that this encoding scheme could not be used to encode the rooted paths of
a tree since these paths are coupled with each other via some non-empty prefix.

<!-- ======================================================================= -->
## con - forward-oriented references

```
s := (a,b,c,d)   =>   n := (a,b,c,d)
                      r := (1,2,3,4)
                      d := (2,3,4,x)
```

**implementations - writer code**

Assuming that `s` is the trace of some tree traversal, the code of a writer
will always have to ensure that the current node being visited has an index
in `n`. This is done by simply appending the node to `n` and its index to
`r` while that node is being visited.

Likewise, and while iterating over the child nodes of a parent, a writer will
also have to ensure that each child has an index in `n` such that it can be
referenced in `d`. However, since the child of a parent has then not yet been
visited, implementations will have to delay writing the child references until
the child nodes are being visited.

**implementations - reader code**

A reader will have less of an issue, if the sequence of nodes `n` is first
processed in order to create a sequence of node objects. This however has
in general the same issue as having to display large image files - i.e.
the actual display must be delayed until all the data is available.

Note that it is however possible to pre-render large image files in low
resolution. This however makes definitions and implementations needlessly
complicated.
