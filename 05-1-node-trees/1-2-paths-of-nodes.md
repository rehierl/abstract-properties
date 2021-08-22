
<!-- ======================================================================= -->
# paths of nodes (over a tree)

Recall that, in the context of this discussion, and unless specified otherwise,
all paths are required to be uni-directional and oriented according to the edges
of a tree. Because of that, each path over a node tree is downward-oriented in
the direction of leaf nodes.

<!-- ======================================================================= -->
## set of paths P

Like any other graph, a tree `T := (N,E)` can be understood to be accompanied
by the set of all the paths `P` that can be formed over its set of edges `E`.

Given a path `p=(a,..,b) in ×N{k}` such that `(p[i] parent-of p[i+1])`
is true for all `(i in [1,#p-1])`, then `aPb` is defined to be true.

* path `p` is uni-directional, top-down/downward oriented
* `TD, P := { p=(a,..,b) | aPb for (a,b in N) }`
* `TD` is the set of all possible downward-oriented paths
* `RD := { p=(r,..,b) | (p in P) and (r in RN) }`
* `RD` is the set of all paths that begin a root node
* `TL := { p=(a,..,l) | (p in P) and (l in LN) }`
* `TL` is the set of all paths that end in a leaf node
* `RL := { p=(r,..,l) | (p in P), (r in RN), (l in LN) }`
* `RL` is the set of all paths that begin in a root and end in a leaf

Note that no `(p in TD)` has a pair of consecutive nodes `(p[i],p[i+1])` such
that `(p[i] child-of p[i+1])` is true. Consequently, `aPb` is (always) false
for any pair of siblings `(a,b in s(n))` for `(n in PN)`.

Note that the set of all paths `RD` that being in a root node will be referred
to as **the set of rooted paths** `RP := RD`.

Note that the set of all paths `RP(n) := p(r,n)` that begin in a root node
`(r in RN)` and end in the specified node `n` will in general be referred
to as **the set of rooted paths of node** `n`.

<!-- ======================================================================= -->
## acyclic, no cycles

Note that there is no `(p in P)` such that it contains a node `(n in N)` more
than once. That is because each child in a tree has one parent only. Thus, no
node can be a node in a path more than once. Consequently, ..

* each tree is an acyclic graph
* `(#E(p) == #p)` is true for any `(p in P)`
* each path `(p in P)` is an **ordered sequence of nodes**

<!-- ======================================================================= -->
## rp(n) - unique rooted paths

Since each tree is required to have one root `r` node only, `rp(n)` can be
understood to the return the set of all paths that begin in `r` and end in `n`.

Any node `(n in N\RN)` in a tree `T := (N,E)`, that is not the tree's root,
is connected to the tree's root `r` by a rooted path that is unique to it.
That is because ..

* each tree as one root node only
* each non-root node `(n in CN)` has a parent, and one parent only
* any tree consists of a single connected component
* each edge `(e in E)` is oriented away from the root
* a tree has no loops and no cycles
* one and only one path `rp(n)` can be formed

Consequently, `(#RP == #N)` is true for any node tree.
Because of that, `(#rp(n) == 1)` is true for all `(n in N)`.

Based on that, `rp(n)` can be understood to be redefined to return
**the (unique) rooted path of node** `n`.

* `rp(n) := p := (r,..,n)` for `(p in TD)`
* `rPn` is true for any `(n in N)`
* note - `nPn` is considered a valid path

<!-- ======================================================================= -->
## p(a,b) - no more than one path

Since each node `(b in N)` has one and only one rooted path, it can be connected
with node `(a in N)` if and only if `a` is a node in `rp(b)`. Consequently, no
more than one path can exist in `TD` that connects node `a` with node `b`.

* `#p(a,b) in [0,1]` is true for any pair of nodes `(a,b in N)`
* `(rp(a) prefix-of rp(b))` if `aPb`
* `(p(a,b) suffix-of rp(b))` if `aPb`

Based on that, `p(a,b)` can be understood to be redefined to return
**the (unique) path between both nodes** `a` and `b`.

* `p(a,b) := p := (a,..,b)` for `(p in TD)`
* note - `nPn` is considered a valid path

<!-- ======================================================================= -->
## filesystem-based notation

Note that there are several, less formal notations possible that can be used
to denote the rooted path of a node, and also the path between two nodes. The
notation that may be used here is:

* `/r` - the rooted path of root node `r`
* `/r/../n` - the rooted path of a non-root node `n`
* `a/../b` - the path between non-root nodes `a` and `b`
