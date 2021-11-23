
<!-- ======================================================================= -->
# hierarchy of traces <=> document tree

Recall that a child order is required in order to form the pre-order trace of
a document tree. Because of that, the isomorphism between a document tree and
a hierarchy of traces must allow to recreate the document tree and its child
order. In other words, a hierarchy of traces must allow to recreate the
unordered doctree `DTU` and also the ordered doctree `DTO`.

<!-- ======================================================================= -->
## doctree => hierarchy of traces

Given a document tree `T(N,E)`, one can form a hierarchy of traces `S` by first
collecting all of the induced subtrees over the unordered doctree (DTU) - i.e.
one for each node in `N`. After that, one needs to replace each induced subtree
by its pre-order trace.

* `S := { pre(t) | (t := T[n]) for (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of traces => node tree

Recall that the pre-order trace of each induced subtree `T[n]` begins with the
subtree's root `n`, which is followed by its first child, and then followed by
all the other descendants of `n`. Also, the trace of a descendant is a substring
to the traces of its ancestors.

* `(pre(n) substring-of pre(a))` for all `(a in A(n))`

Since the pre-order trace `s := pre(n)` begins in node `n` and only contains
the descendants of that node in the unordered document tree (DTU), each trace
of a node has root node `n` as its one and only characteristic element (CE).
The trace of each node therefore begins in its characteristic element.

* `(ce(s) == n)` and `(ce(s) == s[1])` are both true if `(s := pre(n))`

Since each pre-order trace has one and only one CE, and since the set of nodes
in each trace is equal to the scope of the root of the corresponding induced
subtree, the unordered document tree can be recreated given the document tree's
hierarchy of pre-order traces. After all, each tree `T` is isomorphic to a
hierarchy of scopes `Hs` - i.e. `(t <-> Hs)`.

<!-- ======================================================================= -->
## hierarchy of traces => child order

Since the unordered doctree `DTU` can be recreated from a given hierarchy of
traces `Hpre`, one can determine the set of child nodes `c(p)` of each parent
`p`. Because of that, the child order of each parent `p` can be determined by
inducing a suborder `co(p)` from the parent's trace of nodes `t := pre(p)`
using the parent's set of child nodes `c(p)`.

* `co(p) := t[c(p)]`

Note that, since the trace of a node is a substring to the traces of its
ancestors, the child order of a parent can be determined using the parent's
pre-order trace and also the traces of any of its ancestors. Because of that,
the child order of any parent can be determined using the hierarchy's root
trace since that trace contains all of the nodes.

Note that, while reading a document tree from a tag soup, the document tree's
child order is not recreated one child order per parent node. That is because
current nodes will be appended to the list of child nodes of the corresponding
parent. That is, the child orders of multiple parent nodes (i.e. those in the
current rooted path) will be formed simultaneously one child node at a time.
