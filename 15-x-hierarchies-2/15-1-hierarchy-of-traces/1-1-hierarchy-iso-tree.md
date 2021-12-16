
<!-- ======================================================================= -->
# document tree (DT) <=> hierarchy of traces (Hpre)

Recall that a child order is associated with each document tree (DT). Because
of that, the isomorphism between a document tree and a hierarchy of traces
must allow to recreate the document tree and also its child order. In other
words, a hierarchy of traces must allow to recreate the unordered doctree
(DTU) and also the ordered doctree (DTO).

<!-- ======================================================================= -->
## (DTU => Hpre)

Given a document tree `T(N,E)`, one can form a hierarchy of traces `S` by first
collecting all of the induced subtrees over the unordered doctree (DTU) - i.e.
one for each node in `N`. After that, one needs to replace each tree `(t in S)`
by its pre-order trace `pre(t)`.

* `S := { pre(t) | (t := T[n]) for (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## (Hpre => DTU)

Recall that the pre-order trace `pre(t)` of each induced subtree `T[n]` begins
with the subtree's root `n`, which is followed by its first child, and then
followed by all the other descendants of `n` in DTU. Also, the trace of each
descendant is a substring to the traces of its ancestors.

* `(pre(n) substring-of pre(a))` for all `(a in A(n))`

Since the pre-order trace `s := pre(n)` begins in node `n` and only contains
the descendants of that node in DTU, trace `s` has root node `n` as its one
and only characteristic element (CE). The trace of each node/tree therefore
begins in its characteristic element.

* `(ce(s) == n)` and `(ce(s) == s[1])` are both true if `(s := pre(n))`

Since each pre-order trace has one and only one CE, and since the set of nodes
in each trace is equal to the scope of the root of the corresponding induced
subtree, the unordered document tree (DTU) can be derived from its hierarchy
of pre-order traces. After all, each tree `T` is isomorphic to a hierarchy of
scopes `Hs` - i.e. the T-Hs isomorphism.

<!-- ======================================================================= -->
## decoding the doctree's child order

Recall that the child order of a doctree is embedded into the pre-order trace
of its root, and also partially into the pre-order traces of every other node.
That is, the child order of a doctree is a suborder to its pre-order trace.

Since the set of nodes of the pre-order trace `pre(n)` of each node `n` is
equal to its induced subtree `T[n]`, one can derive the unordered doctree DTU
from its hierarchy of traces `H` - i.e. the T-Hs isomorphism. Because of that,
one can determine the set of child nodes `c(p)` of each parent `p` in DTU.

Since the child order `co(p)` of a parent `p` is a suborder to its pre-order
trace `pre(p)`, the parent's child order can be derived from its trace by
restricting that trace to the subset of child nodes.

`co(p) := s[c(p)]` where `s := pre(p)` for `(p in PN(T))`

Note that, since the trace of a node is a substring to the traces of its
ancestors, the child order of a parent can also be derived from the traces of
any of the parent's ancestors. Because of that, the child order of any parent
can be determined using the hierarchy's root trace since that trace contains
all of the nodes.

Since the doctree's child order is the union of child orders of all the parent
nodes in it, the doctree's child order can be derived from its hierarchy of
traces.

`co(T) := { co(p) | (p in PN(T)) }`

Note that, while reading a document tree **from a tag soup**, the document
tree's child order is not recreated one child order per parent node. That is
because current nodes will be appended to the list of those child nodes of a
parent that have been encountered up to a certain point. That is, the child
orders of multiple parent nodes (i.e. those in the current rooted path) will
be **formed simultaneously one child at a time**.
