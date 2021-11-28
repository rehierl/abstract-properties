
<!-- ======================================================================= -->
# hierarchy of traces <=> document tree

Recall that a child order is associated with each document tree. Because of
that, the isomorphism between a document tree and a hierarchy of traces must
allow to recreate the document tree and its child order. In other words, a
hierarchy of traces must allow to recreate the unordered doctree (DTU) and
also the ordered doctree (DTO).

<!-- ======================================================================= -->
## doctree => hierarchy of traces

Given a document tree `T(N,E)`, one can form a hierarchy of traces `S` by first
collecting all of the induced subtrees over the unordered doctree (DTU) - i.e.
one for each node in `N`. After that, one needs to replace each tree in `S` by
its pre-order trace.

* `S := { pre(t) | (t := T[n]) for (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of traces => node tree

Recall that the pre-order trace of each induced subtree `T[n]` begins with the
subtree's root `n`, which is followed by its first child, and then followed by
all the other descendants of `n` in DTU. Also, the trace of a descendant is a
substring to the traces of its ancestors.

* `(pre(n) substring-of pre(a))` for all `(a in A(n))`

Since the pre-order trace `s := pre(n)` begins in node `n` and only contains
the descendants of that node in DTU, trace `s` has root node `n` as its one
and only characteristic element (CE). The trace of each node therefore begins
in its characteristic element.

* `(ce(s) == n)` and `(ce(s) == s[1])` are both true if `(s := pre(n))`

Since each pre-order trace has one and only one CE, and since the set of nodes
in each trace is equal to the scope of the root of the corresponding induced
subtree, the unordered document tree (DTU) can be recreated given its hierarchy
of pre-order traces. After all, each tree `T` is isomorphic to a hierarchy of
scopes `Hs` - i.e. the T-Hs isomorphism.

<!-- ======================================================================= -->
## hierarchy of traces => child order

Since the unordered document tree (DTU) can be recreated from its hierarchy of
traces `Hpre`, one can determine the set of child nodes `c(p)` of each parent
node `p`. Because of that, the child order of each parent can be determined
by inducing a suborder `co(p)` from the parent's trace of nodes `t := pre(p)`
using the parent's set of child nodes `c(p)`.

* `co(p) := t[c(p)]`

Note that, since the trace of a node is a substring to the traces of its
ancestors, the child order of a parent can also be induced by the traces of
any of the parent's ancestors. Because of that, the child order of any parent
can be determined using the hierarchy's root trace since that trace contains
all of the nodes.

Note that, while reading a document tree from a tag soup, the document tree's
child order is not recreated one child order per parent node. That is because
current nodes will be appended to the list of those child nodes of a parent
that have been encountered up to a certain point. That is, the child orders of
multiple parent nodes (i.e. those in the current rooted path) will be formed
simultaneously one child at a time.
