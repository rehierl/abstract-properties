
<!-- ======================================================================= -->
# the document order

Recall the prologue and chapter 05-2 (the definition of document trees), which
introduced **the document order** as a reference to the total node order over
the nodes in a document tree, and as **a processing order** that is required
in order to guarantee consistent results across all implementations.

Recall that **the above-of node order** and **the below-of node order**, as
outlined in the prologue, were introduced as additional references to the
document order. Hence, all of these references can be understood to be more
or less synonymous.

- the "document order" is an entirely generic description
- the "above-of order" can be used with regards to exclusion/context
- the "below-of order" can be used with regards to inclusion/scope

<!-- ======================================================================= -->
## based on the tree traversal algorithms

Recall that **the pre-order and the level-order tree traversal algorithms**
are the only **overall order preserving** algorithms discussed. That is, both
algorithms visit the nodes in tree order and also in child order.

Since the level-order trace of a tree can be described as a sequence of disjoint
child orders, and since that trace is as such non-hierarchical, one can conclude
that the document order can not be in level order. Because of that, and since
only one alternative option remains, the document order can be concluded to
be **the document tree's pre-order node order**.

Recall that the pre-order trace of a tree is a hierarchical ordered sequence
of nodes. After all, **the scope of each node appears a substring** such that
all the scopes are either disjoint ex-or related (**DI-RE**).

Recall that the pre-order trace of a node is a substring to the traces of its
ancestors, including the trace of a document tree. Based on that, the trace of
a document tree can be described as a sequence of **interleaved child orders**.

<!-- ======================================================================= -->
## based on the tag soup of a document tree

```
rotated clockwise | in regards    |
by 90 degrees     | to node <n>   | scopes
------------------|---------------|-------
<p>               | presequent-to |  + s(p)
  fs ..           | above-of      |  |
  <n>             |---------------|  +-+ s(n)
    fc .. lc      | subsequent-to |  | |
  </n>            | below-of      |  | |
  ns ..           |               |  |
</p>              |               |  |
```

Since each node in a document tree is defined by its start-tag, and since the
subsequence of start-tags in the tag soup of a document tree corresponds with
the document tree's pre-order trace, one can conclude that the document order
is **the document tree's pre-order node order**.

As a matter of consequence, **the above-of and the below-of node orders** can
be **defined based on the pre-order trace of a document tree**.

* `(a above-of b) := (a presequent-to b)`
* `(b below-of a) := (b subsequent-to a)`

Note that the node order of a document tree is a proper partial suborder to
its document order. That is, the total document order and the document tree's
partial node order are not equivalent.
