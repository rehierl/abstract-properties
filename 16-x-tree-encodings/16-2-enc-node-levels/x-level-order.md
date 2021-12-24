
the node level of a node is monotone increasing
- increasing with each subsequent node/order
- i.e. `(t[i].level <= t[i+j].level)`

The last node of a level-order trace is not necessarily a descendant of the
root's last child. That node can even be a descendant of the root's first child.

The former child nodes of node `n` (i.e. `fc` and `ns`) are ordered in
ascending order (i.e. `(ns.level < fc.level)`).
