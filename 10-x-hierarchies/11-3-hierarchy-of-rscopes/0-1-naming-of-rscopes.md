
<!-- ======================================================================= -->
# about the description "reversed scopes"

Note that the description of "reversed scopes" is in regards to upward-closed
open intervals (i.e. `[*,n]`), in contrary to the definiton of default scopes
as downward-closed open intervals (i.e. `[n,*]`). However, that description
needs some getting used to since the actual scopes are "not reversed".

<!-- ======================================================================= -->
## (default) scopes vs. reversed scopes

Recall that the (default) scope of a node `Hs(n)` is equal to the set of nodes
in the induced subtree that has the defining node as its root. That is, the
scope of a node contains the node and its descendants in the corresponding
tree.

* `Hs(n) := D*(n)`

The reversed scope of a node `Hrs(n)` is dual to that since it is equal to the
set of nodes in the rooted path of its defining node. That is, the reversed
scope of a node contains the node and its ancestors in the corresponding tree.

* `Hrs(n) := A*(n)`

Note that future discussions will eventually define the **reversed scope** of
a node as the node's **context**. After all, each such scope contains all the
nodes that may be the defining nodes of one or more abstract properties such
that the defining node `n` is within the scopes of these properties. At this
point, such a definition is however not required since the current focus is
on structure, not on semantics.

<!-- ======================================================================= -->
## reversing an ordered sequence

```
an ordered sequence S         the reversed sequence T
=====================   <=>   =======================
1 -> 2 -> 3 -> 4 -> 5         5 -> 4 -> 3 -> 2 -> 1
```

Recall that reversing a sequence is understood to form a new sequence (T) by
adding the elements of a source sequence (S) to the new sequence in reversed
order (i.e. from last to first).

Note that the process of reversing a sequence effectively turns each edge in
the path graph of a sequence upside down. That is, each edge in that such a
path graph is reversed - e.g. edge (1,2) is turned into edge (2,1).

<!-- ======================================================================= -->
## reversing a node tree

With the process of reversing a path graph in mind, one can reverse a node tree
by reversing each edge in it.

```
a node tree T           the reversed graph G
===============   <=>   ====================
      0                      5   6
      |                      |   |
-------------                -----
|   |       |                  |
1   2       7              3   4   8   9
    |       |              |   |   |   |
  -----   -----            -----   -----
  |   |   |   |              |       |
  3   4   8   9          1   2       7
      |                  |   |       |
    -----                -------------
    |   |                      |
    5   6                      0
```

Recall that visualizations orient the edges from "top to bottom" and "left to
right". That is tree (T) has an edge (0,2) whereas graph (G) has an edge (2,0).

Note that tree reversed graph (G) of a tree (T) is in general no node tree.
That is because each node in (G) may in general have more than one parent.
For example, node (4) has parent nodes (5) and (6). Furthermore, each leaf
node in (T) acts as a root in (G). Because of that, node (4) has two rooted
paths in (G) - i.e. (5,4) and (6,4).

Note that the set of ancestors of a node `A(n,T)` in tree (T) corresponds with
the set of descendants `D(n,G)` in graph (G). Because of that, the description
**reversed scope** can be understood to refer to the scope of the defining
node in the reversed graph.

* `A(n,T) <-> D(n,G)`
