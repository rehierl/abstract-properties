
<!-- ======================================================================= -->
## sub-orders to a pre-order trace

```
n1 -> n2 -> n3 -> n4 -> n5 -> n6 -> n7 -> n8 -> n9 -> n10   | pre-order trace
=========================================================   | =====
                  n4 -> n5 -> n6 -> n7                      | scope(p)
```

Recall that each pre-order trace is an ordered sequence of nodes. Because of
that, the pre-order trace of a tree corresponds with a total order of nodes.
And since each scope is a substring to a tree's pre-order trace, the total
order of a scope is a total suborder to (i.e. embedded into) a trace.

Likewise, and since the pre-order trace of a node is a substring to the traces
of its ancestors, the pre-order traces of each node is a total sub-order to
the trace of a tree (i.e. the pre-order trace of the tree's root).

Note that a pre-order trace is a substring and therefore a total sub-order to
itself. Based on that, the first node of a trace can in general be selected
as the defining node of a property whose scope includes all the nodes in the
corresponding trace.

```
unordered tree        n1 -> n2 -> n4 -> n5 -> n3 -> n6   | pre-order trace                    |
==============   =>   ================================   | =====
       n1             n1 -> n2 -> n4                     | tree-order of the
   ----------               n2 -------> n5               | unordered tree
   n2      n3         n1 -------------------> n3 -> n6   |
 ------   ----   =>   ================================   | =====
 n4  n5    n6               n2 -------------> n3         | a child order
```

Similar to that, the partial order of an unordered tree is embedded into the
total order of its pre-order trace. (Recall that a visualization is the cover
graph of a tree's node order - i.e. only its transitive reduction is shown).

Likewise, and because the child order of each parent node is embedded into
a pre-order trace, the partial order of the ordered tree is also a sub-order
to a pre-order trace. Because of that, each rooted path in both trees is a
total sub-order to a pre-order trace.

Due to the above, each pre-order trace can be understood to have several
**total and/or partial sub-orders** embedded into it. That is, each edge
of these sub-orders is an edge in the underlying total pre-order. All the
edges of all these sub-orders are therefore **consistently oriented**
(i.e. oriented towards the last node of a tree's pre-order trace).

The pre-order trace of a tree therefore has the following sub-orders:

* the scope of each property
* the pre-order trace of each node
* the partial order of the un-ordered tree
* all the child orders
* the partial order of the ordered tree
* all the rooted paths
* all the edges in each sub-order
