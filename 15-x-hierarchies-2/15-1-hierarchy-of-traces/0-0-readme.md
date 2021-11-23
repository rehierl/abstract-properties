
# hierarchy of traces

```
T <-> Hpre
```

An ordered document tree (T) allows to form a hierarchy of pre-order traces
(Hpre) such that the source tree can be recreated based on the relationships
between its traces. In addition to that, the document tree's child order can
be recreated using the doctree's pre-order trace. That is, each document tree
is isomorphic to a hierarchy of traces. Because of that, this isomorphism will
be referred to as **the T-Hpre isomorphism**.

Note that, since the pre-order traces are the traces of the induced subtrees
of the source tree (T), the set of nodes of each trace is equal to the set of
nodes of the corresponding induced subtree over the unordered doctree (DTU).
And since the Hpre allows to recreate DTU, one can determine the set of child
nodes `c(p)` of each parent node in DTU.

Recall that the child order of each parent `p` is a suborder to the parent's
pre-order trace `pre(p)`. Because of that, the child order `co(p)` of a parent
can be recreated by restricting the parent's trace using its set of child nodes.
And since the doctree's child order is the union of the child orders of all the
parent nodes in it, the doctree's child order can be recreated from Hpre.

* `co(p) := t[c(p)]` where `t := pre(p)`

Note that the equivalent hierarchies of traces can be formed using the reversed
pre-order traversal (Hncr), the default post-order traversal (Hcin), and even
the reversed post-order traversal (Hcrn). Despite that, the focus will be on
the default pre-order traversal (Hpre -or- Hnci).

* Hcrn := the (reversed) child order follwed by the node
* (n) denotes the node, (c) denotes the child order
* (i) the child order in order, (r) the child order in reverse

# no Hs-Hpre isomophism - (Hpre -> Hs) only

A hierarchy of scopes Hs can be formed from a hierarchy of traces Hpre by
substituting each trace with its set of nodes. Because of that, a hierarchy
of traces allows to directly form the doctree's hierarchy of scopes.

On its own, Hs can however not be used to form Hpre since it does not embed
the doctree's child order. Furthermore, and even though a doctree's child order
is embedded into the ordered doctree, one can not form Hpre using the scopes
over DTO. That is because the ordered doctree itself has no child order, which
is why one can not distinguish the scope of its former next subsequent sibling
from the scope of its former first child.
