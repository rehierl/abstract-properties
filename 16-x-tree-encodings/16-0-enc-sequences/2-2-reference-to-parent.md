
<!-- ======================================================================= -->
# a parent-based encoding

```
s := (a,b,c,d)   =>   n := (a,b,c,d)   =>   n := (a,b,c,d) - node definitions
                      r := (1,2,3,4)        r := (1,2,3,4) - child nodes
                                            d := (x,1,2,3) - parent nodes
```

As before, a sequence of nodes `s` allows to form a sequence of nodes `n` and a
sequence of references `r`. In addition to that, a second sequence of references
`d` can be defined such that it holds the index of a parent of the corresponding
node in `r`.  Combined, sequences `r` and `d` can be understood to define a set
of edges `E` and therefore to define a graph `G(N,E)`.

* `N := { r[i] | (i in [1,#r] }`
* `E := { (d[i],r[i]) | (d[i] in [1,#r]) and (i in [1,#r]) }`
* `sem(G) := (a parent-of b)`

Note that `d[i]` defines the parent of `r[i]`.
Furthermore, `(#r == #N)` is at this point not (yet) required to be true.

<!-- ======================================================================= -->
## remarks

Note that, due to its versatility (as discussed below), this encoding scheme
can be understood as **the default explicit encoding scheme**.

Recall that "a parent" (not "the") is defined as the source of an incoming edge.
Because of that, any node may in general be associated with any number of such
edges, which is why one can by default not speak of "the parent" of a node
since in general, more than one such node may exist for any given node.

Recall that an index value (x) is used to denote an invalid index such that it
does not map to any node in `n`. In regards to this encoding scheme, such an
index is used to denote that the corresponding node has no parent, which is
why only root nodes may have such an invalid parent reference.

Note that the index values in `d` are lower than the corresponding values in
`r`. Because of that, this scheme may be described as being **backward-oriented**.
An index value of `0`, as the only invalid index allowed, would therefore be
appropriate for the invalid reference (x), which would then overall be a
constant reference.

Note that, as before, the orientation greatly **depends on the tree traversal**
algorithm that was used to form the above sequences, which will in general be
a "root to leaf" oriented traversal (i.e. in tree order).

<!-- ======================================================================= -->
## pro - one parent only

Since each node in a tree must have no more than one parent, this encoding
scheme can be used to encode forests of trees and even embed the child order
of a document tree.

```
s := (a,b,c,d)   =>   n := (a,b,c,d)
                      r := (1,2,3,4)
                      d := (x,1,2,3)
```

Even though this encoding scheme would also allow `r` to deviate from the
index-order of `n`, e.g. in order to not having to specify root nodes, one
will usually choose not to do so. That is because, compared to leaf nodes,
root nodes are few, which is why sticking with the index-order of `n`
allows to not explicitly specify `r` - i.e. sequence `r` can be omitted.

```
a -|-> b      d -|-> e      =>   n := (a,b,c,d,e,f)
   |-> c         |-> f           r := (1,2,3,4,5,6)
                                 d := (x,1,1,x,4,4)
```

Note that, in the context of this discussion (i.e. downward-total orders),
sequence `r` can not grow past the length of `n`. That is because no node
can have more than one parent. Hence, there is no actual reason to deviate
from the index-order of `n`.

<!-- ======================================================================= -->
## con - allows to define cyclic graphs

Note that this feature is considered negative in the context of this discussion
since, because of it, implementations must always take the possibility of cyclic
input into account and must therefore always define error handling procedures
that need to be triggered in case a cyclic definition is encountered.

```
component-1   component-2
===========   ===========
a -|-> b      d -|-> e      =>   n := (a,b,c,d,e,f)
   |-> c      |  |-> f           r := (1,2,3,4,5,6)
              |<-----|           d := (x,1,1,6,4,4)
                                             |<- a cycle (!)
```

As can be seen two components are defined, one of which is cyclic since path
`p := (4,6,4)` connects node `d` with itself. Despite not being a tree, this
encoding scheme can be used to encode all of the edges while sicking to the
index-order of `n`.

However, and since this encoding scheme is by default backwards-oriented, such
cycles can be detected. That is because there must then be an edge that is
oriented against the default orientation - i.e. `(4,6)` is forward-oriented.
Hence, verifying that each parent index in `d` is lower than the current index
in `r` allows to detect cycles.

* `(d[i] < r[i])` must be true for any `(i in [1,#n])`

<!-- ======================================================================= -->
## pro - allows to encode a child order

```
s := (a,b)   =>   n := (a,b,c,d)
t := (c,d)        r := (1,2,3,4)
                  d := (x,1,x,3)
```

Obviously, and since the child order of a document tree can be described as
a forest of specialized trees (i.e. path graphs), this encoding scheme allows
to explicitly encode a child order.

Recall that, due to its order-preserving nature of (e.g.) a pre-order tree
traversal, the child order of a document tree is a suborder to its pre-order
trace. Because of that, one will in general explicit encode a child order.

Note that this encoding can not be used to encode the rooted paths of a tree
since these paths are all coupled with each other via some non-empty prefix.

<!-- ======================================================================= -->
## pro - backward-oriented references

```
s := (a,b,c,d)   =>   n := (a,b,c,d)
                      r := (1,2,3,4)
                      d := (2,3,4,x)
```

**implementations - writer code**

Assuming that `s` is the trace of some order-preserving tree traversal, the
code of a writer will always have to ensure that the current node being visited
has an index in `n`. This is done by simply appending the node to `n` and its
index to `r`.

However, and in contrary to before, it is guaranteed that the parent of a child
already has an index in `n`. That is because no child will appear presequent
to its ancestors.

**implementations - reader code**

A reader will be able to create node objects on the fly. That is because once
some current node is being visited, it can use the the parent's index to lookup
its node object since that object must have been created by a previous visit.

Recall the past-present-future principle of abstract properties, to which this
order of node references is consistent.
