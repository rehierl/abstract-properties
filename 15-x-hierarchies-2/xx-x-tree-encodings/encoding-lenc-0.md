
<!-- ======================================================================= -->
## pre-order

pre-order
- expand the distance between a node and its next sibling
- distance in terms of total number of descendants
- distance-encoding - not accurate - last child

pre-order length-encoding
- in regards to streaming large documents
- supports pre-order and level-order traversal?
- pre-order - already in that order - so yes
- level-order - most likely - a queue of intervals

<!-- ======================================================================= -->
## level-order

won't work
- a parent may have any number of child nodes
- you don't know how many child nodes a particular parent has

efficiently recreate an ordered tree
- i.e. the 2-child-per-node tree
- via a list of child orders

relationship between
- traces of ancestors and descendants
- substring?, prefix?, suffix?

concatenate child orders
- in the order of a tree's child order
- a child order is a set of child orders
- a child order is a forest of n rooted paths
- a child order is a partial order that has n roots

an ordered sequence of child orders
such that the former node level of each child is
monotone increasing (with each subsequent node/order)
i.e. `(t[i].level <= t[i+j].level)`

The last node of the trace is not necessarily
a descendant of the root's last child.

Note that the former child nodes of node `n` (i.e. `fc` and `ns`)
are ordered in ascending order (i.e. `(ns.level < fc.level)`).
