
<!-- ======================================================================= -->
# dom/html remarks

<!-- ======================================================================= -->
## dom's perception of "ordered set"

* whatwg.org in 2022-02 - https://dom.spec.whatwg.org/#trees
* "An object that participates in a tree has a parent,
  ..., and has children, which is an ordered set."
* whatwg.org in 2022-02 - https://infra.spec.whatwg.org/#sets
* "An ordered set is a list ... must not contain the same item twice".

Based on that, the description "ordered set" is treated as being synonymous
to a simple set that is associated with a total order. This is obviously
an **over-simplification** since not all orders are linear/total orders.

<!-- ======================================================================= -->
## dom's perception of "tree order"

* whatwg.org in 2022-02 - https://dom.spec.whatwg.org/#trees
* "A tree is a finite hierarchical tree strurcture."
* "In tree order is preorder, depth-first traversal of a tree."

Based on that, the description "tree order" is treated as being synonymous to
the "pre-order node order". That is, the description "tree order" is declared
to be equivalent to a linear/total order rather than a partial order. This is
**misleading** since the node order of a document tree is embedded into the
pre-order node order. In other words: Not all tree orders are linear/total.

Recall that all tree orders are downward-total (i.e. each node has a unique
rooted path). However, not all tree orders are also upward-total.

Note that the HTML specification builds upon this misleading perception of
"tree order".

<!-- ======================================================================= -->
## html's perception of "element"

* whatwg.org in 2021-09 - https://html.spec.whatwg.org/#elements-2
* "Tags are used to delimit the start and end of elements in the markup."

Based on that, an HTML element is such that it is understood to begin with
its start-tag and to end with its end-tag. It should be clear at this point
that each element still corresponds with a single node in the document tree.
Because of that, this statement is **misleading** since the visit of the
element's node in the document tree still corresponds with its type-0 scope,
*not* with its type-1 scope. Treating an element as being equal to its
pre-order trace of nodes, which is enclosed by its pair of tags, does not
change that.
