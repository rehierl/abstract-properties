
<!-- ======================================================================= -->
# A pre-order length-based encoding

The purpose of the following content is to proof that the pre-order rule is
more than a mere theoretical discussion. It suggests that node trees can be
encoded as sequences of length values.

<!-- ======================================================================= -->
## a setup of traces

Instead of recursively beginning with a tree's root, one can begin with the
leaf nodes and iteratively "push" the traces of descendant nodes upwards to
the root.

```
tree of nodes =>       ...       => tree/setup of traces
========================================================
 A           |  A           |  A           |  ABDEFC
-----------  | -----------  | -----------  | -----------
 B       C   |  B       C   |  BDEF    C   |  BDEF    C
------       | ------       | ------       | ------
 D  E        |  D  EF       |  D  EF       |  D  EF
   ---       |    ---       |    ---       |    ---
    F        |     F        |     F        |     F
```

Each pre-order trace of an induced sub-tree is a **substring** to its induced
super-trees. Because of that, each trace has a least and a most significant
super-trace (i.e. in terms of the length of a trace).

Together the traces of all induced sub-trees can be understood to define a
**setup of pre-order traces** `S := { ABDEFC, BDEF, C, D, EF, F }` that has
the following characteristics:

1. no trace is empty
2. all traces are either pairwise disjoint ex-or pairwise related

Note that "related" in this context is based upon the definition of "substring".

* `(s related-to t) := (s substring-of t) or (t substring-of s)`

Note that, due to characteristic-2 (i.e. **disjoint ex-or related**), such a
setup has no traces that overlap each other.

<!-- ======================================================================= -->
## correspondence

As can be seen above, a setup of traces can be formed from an ordered
tree. In addition to that, the ordered tree can be formed from its
setup of traces:

* The first node of a trace, i.e. its characteristic
  element (CE), is the node a trace represents.
* parent := the least significant (i.e. shortest) super-string
* The relationship a trace has with the other traces in a
  setup defines the parent of the node a trace represents.
* The offset of a trace within its parent trace defines
  the child order of the corresponding parent node.

An ordered tree therefore **corresponds** with its setup of traces:

* ordered tree <=> setup of traces

<!-- ======================================================================= -->
## setups of sets

Recall that each trace is an ordered sequence and therefore defines an
ordered set of nodes. Setups of traces can therefore be generalized into
setups of sets.

1. A setup of sets that satisfies similar requirements (i.e. (1) non-empty,
   and (2) disjoint ex-or related) defines the structure of a tree.
2. If, in addition to that, each set has one and only one characteristic
   element, a setup of sets uniquely defines an unordered tree.
3. If, in addition to that, all sets are totally ordered sets and as such
   sub-orders to a common total super-order, then the super-order can be
   used to define the child order of a parent.

Note that, if all of these requirements are met, then a setup of sets can
be understood to correspond with an ordered tree of nodes.

<!-- ======================================================================= -->
## a length-based encoding

Since a pre-order trace is an ordered sequence of nodes, a node in such a
trace is associated with a unique index. That is, the index of a node can
be used as an identifier that represents the corresponding node.

```
pre-order trace | hierarchy of traces | # | length encoding   
==============================================================
( A,B,D,E,F,C ) | A: (1,2,3,4,5,6)    | 6 | n := (A,B,D,E,F,C)
( 1,2,3,4,5,6 ) | B: (  2,3,4,5  )    | 4 | l := (6,4,1,2,1,1)
 |-----------|  | D: (    3      )    | 1 |                   
   |-------|-|  | E: (      4,5  )    | 2 |                   
     |-|---|    | F: (        5  )    | 1 |                   
         |-|    | C: (          6)    | 1 |                   
```

In addition to the above, a setup of traces can be used to encode an ordered
tree as a sequence of nodes `n` that is accompanied by a sequence of length
values `l`, both of which combined represent the **pre-order, length-based
encoding** of an ordered tree.

* ordered tree <=> length-based encoding

<!-- ======================================================================= -->
## characteristics of l[]

The index of a length value, combined with its actual length value, defines
an interval of indexes: `int(i) := [i, i+l[i]-1]`. As such, each interval
can be treated as a 2-element sequence of integers `i := (min,max)`.

Note that ...

* Each interval must define be a sub-set to the root-interval `int(1)`.
* Each interval represents a trace of nodes: `substr(n,i[1],i[2])`.
* If `(l[i] == 1)`, then `n[i]` is a leaf node.
* If `(l[i] > 1)`, then `n[i]` is a parent node.
* The descendants of a parent can be easily determined
  by its index and its length value in `l`.

Note that `l` always ends in a value of `1` since a pre-order trace ends in
a leaf (i.e. `(l[#l] == 1)`). Also, and if the tree's root is no leaf, then
`l` begins in a value that is greater than `1` (i.e. `(l[1] > 1)`).

* `l := (#l,...,1)`
* note - `l := (1)` if `(#l == 1)`

<!-- ======================================================================= -->
## general patterns

```
    A       | l := (#N,1,..,1)
---------   | 
 B C D E    | A: (A,B,C,D,E)
```

If a tree is such that only the root has child nodes,
then only the first length value is greater than one.

```
    A     | l := (#N,#N-1,..,2,1)
   ---    | 
    B     | A: (A,B,C)
   ---    | B: (  B,C)
    C     | C: (    C)
```

If a tree is a rooted path (i.e. a path graph), then `l` is
a strictly monotone decreasing sequence of length values.

<!-- ======================================================================= -->
## forests of trees

Sequences of length values can also be used to encode forests of trees:

* `l := ()` - an empty forest
* `l := (1,1)` - a forest of two 1-node trees
