
<!-- ======================================================================= -->
## level-order

- a parent may have any number of child nodes
- no child at all, one child only, ..

a child order is ..
- a set of child orders
- a set of disjoint ordered sequences
- a partial order that has n roots
- a forest of rooted paths

concatenate child orders
- in the order of a tree's child order,
  beginning with the tree's root node
- an ordered sequence of child orders

such that the node level of node is monotone increasing
- increasing with each subsequent node/order
- i.e. `(t[i].level <= t[i+j].level)`

The last node of the trace is not necessarily a descendant of the root's
last child. That node can be a descendant of the root's first child.

In a level-order trace, one does in general not know to which child order
a random node belongs.

The former child nodes of node `n` (i.e. `fc` and `ns`) are ordered in
ascending order (i.e. `(ns.level < fc.level)`).
