
<!-- ======================================================================= -->
# dom/html remarks

<!-- ======================================================================= -->
## dom's perception of tree order

* whatwg.org in 2021-10 - https://dom.spec.whatwg.org/#concept-tree
* "A tree is a finite hierarchical tree strurcture."
* "In tree order is preorder, depth-first traversal of a tree."

Based on that, the "tree order" description is treated as being synonymous to
the "pre-order node order" (i.e. the doctree's trace of nodes). That is, this
description is declared to refer to a total rather than a partial node order.
Needless to state that **this perception is more than just misleading** since
"a tree order" is in general no total order.

Note that the HTML specification builds upon this perception of "tree order".

<!-- ======================================================================= -->
## html's perception of "element"

* whatwg.org in 2021-09 - https://html.spec.whatwg.org/#elements-2
* "Tags are used to delimit the start and end of elements in the markup."

Based on that, a HTML element is such that it is understood to begin with
its start-tag and to end with its end-tag. It should be clear that each such
element still corresponds with a single node in the document tree.

The above statement is therefore **misleading** because the visit of the
element's node in the document tree still corresponds with its type-0 scope,
*not* with its entire type-1 scope. Naming the pair of tags "an element",
while implicitly including all the descendant elements in between, does not
change that.
