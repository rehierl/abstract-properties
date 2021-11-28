
# hierarchy of traces

```
T <-> Hpre
```

An ordered document tree (T) allows to form a hierarchy of pre-order traces
(Hpre) such that the source tree can be recreated based on the relationships
between these traces. In addition to that, the doctree's child order can be
recreated using the doctree's pre-order trace. That is, each document tree
is isomorphic to a hierarchy of traces. Because of that, this isomorphism
will be referred to as **the T-Hpre isomorphism**.

Note that, since the pre-order traces are the traces of the induced subtrees
over the unordered doctree (DTU), the set of nodes of each trace is equal to
the set of nodes of the corresponding induced subtree. And since the hierarchy
of traces Hpre allows to recreate DTU, one can determine the set of child nodes
`c(p)` of each parent in DTU.

Recall that the child order `co(p)` of a parent `p` is a suborder to the its
pre-order trace `pre(p)`. Because of that, the child order of a parent can be
induced from the parent's trace by restricting its trace to its set of child
nodes. And since the doctree's child order is the union of the child orders
of all the parent nodes, the doctree's child order can be recreated from Hpre.

* `co(p) := t[c(p)]` where `t := pre(p)`
* `co(T) := { co(p) | (p in PN(T)) }`

Note that equivalent hierarchies of traces can be formed using the reversed
pre-order traversal (Hncr), the default post-order traversal (Hcin), and
even the reversed post-order traversal (Hcrn). Despite that, the focus in
the context of this discussion will remain on the default pre-order traversal
(Hpre, aka. Hnci).

* Hcrn := the (reversed) child order follwed by its parent node
* (n) denotes the visit-order of each node, (c) denotes its child order
* (i) the child order in order, (r) the child order in reverse

# no Hs-Hpre isomophism - (Hpre -> Hs) only

A hierarchy of scopes Hs can be formed from a hierarchy of traces Hpre by
replacing each trace with its set of nodes. Because of that, a hierarchy of
traces allows to directly form the doctree's hierarchy of scopes. However,
a hierarchy of scopes does not allow to form a hierarchy of traces since it
does not embed the doctree's child order.

Note that one would have to form an ordered sequence of scopes (i.e. a
pre-order trace of scopes) from Hpre, in order to be able to recreate Hpre
from it. That is because the index-order over the scopes would then correspond
with the index-order over the nodes in the doctree's pre-order trace, which
would then allow to form the trace of each node.
