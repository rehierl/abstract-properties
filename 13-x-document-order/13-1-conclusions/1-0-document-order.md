
<!-- ======================================================================= -->
# the doc-order is a total pre-order

Recall that the pre-order and the level-order tree traversal algorithms are the
only **order preserving** tree traversal algorithms. That is, both algorithms
visit the nodes in tree order and also in child order.

However, since the level-order trace of a tree can be described as a sequence
of disjoint child orders, and since it is as such non-hierarchical, one can
conclude that the document order can not be in level order.

Despite the fact that the only order-preserving tree traversal algorithm left
is the pre-order tree traversal, one can point out that the pre-order trace
of a tree is a hierarchical ordered sequence of nodes. That is because
**the scope of each node is a substring** to the pre-order trace.

Furthermore, and due to the order-preserving nature of a pre-order trace,
the hierarchy of scopes embedded into it is such that two scopes are either
disjoint ex-or related (**DI-RE**). Based on that, a pre-order trace can be
described as a sequence of interleaved child orders.

<!-- ======================================================================= -->
## a 90° clockwise rotation

In order to visualize the general pattern of the node order of a document, the
only transformation left is to clockwise rotate the tag soup of a document by
90 degrees and to indent the tags according to the node level of each node.

```
clockwise rotated | in regards    |
by 90 degrees     | to node <n>   | scopes
------------------|---------------|-------
<p>               | presequent-to |  + s(p)
  (fs ..)         | above-of      |  |
  <n>             |---------------|  +-+ s(n)
    (fc .. lc)    | subsequent-to |  | |
  </n>            | below-of      |  | |
  (ns ..)         |               |  |
</p>              |               |  |
```

By looking at the scopes that are drawn to the side, one can conclude that we
are already familiar with that node order. We see it each and every time we
open a file system browser (i.e. a tree of files and folders), or when opening
a the hierarchical listing of browser bookmarks (i.e. a tree of bookmarks
organized as nested folders).

Note that the overall difference is that such a hierarchical listing has in
general two types of nodes: (1) folders which may contain folders (by which
the hierarchy is established), and (2) items which may contain nothing (the
tree's leaf nodes). In addition to that, such a system affects the tree's
child order (e.g. folders first, then alphabetical by an entry's name - i.e.
a two-staged node order). In contrary to that, any node in a document tree
is such that it may in general have any number of descendants.

<!-- ======================================================================= -->
## the document order of a document

Recall that **the above-of node order** (as outlined in the prologue) was
introduced as a reference to the document order. With that in mind, the
following statements are true.

* The doctree's pre-order traversal defines the doctree's pre-order node order.
* The tag soup of a document encodes the doctree's pre-order node order.
* **The total document order is equivalent to the pre-order node order**.
* The tag soup of a document encodes a hierarchy of scopes.
* The tag soup of a document is isomorphic to the document tree.
* **The document tree is a partial suborder to the document order**.

In regards to the document tree's pre-order trace, the above-of node order
must be understood to be defined based on the doctree's pre-order trace.

* `(a above-of b) := (a presequent-to b)`

And there shouldn't even be the slightest shred of doubt about that!

<!-- ======================================================================= -->
## remarks

Recall that no node above-of a heading belongs to a heading's section. Because
of that, no node can count towards the section of a heading, if the heading is
subsequent to that node in the document tree's pre-order trace. That is, a node
can not be associated with the section of a heading, if the node is an ancestor
of that heading, a presequent sibling of that heading (or one of the descendants
of such a node), or a presequent sibling of one of the heading's ancestors (or
one of the descendants of such a sibling).

Conversely, the subsequent siblings of a heading (including their descendants),
the subsequent siblings of the heading's ancestors (including their descendants)
are subsequent to that heading in the document tree's pre-order trace. Because
of that, all of these nodes may in principle be content nodes in the section of
a heading.

Recall however that the document order does by itself not allow to conclude,
if specific nodes that are subsequent to a heading in the document order, are
indeed content nodes in the section if a heading. Further defintions are thus
required.