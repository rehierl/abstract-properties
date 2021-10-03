
<!-- ======================================================================= -->
# html elements

* whatwg.org in 2021-09 - https://html.spec.whatwg.org/#elements-2
* "Tags are used to delimit the start and end of elements in the markup."

A HTML element is therefore such that it is understood to begin with its
start-tag and to end with its end-tag. It should be clear that each such
element still corresponds with a single node in the document tree.

The above statement is therefore **misleading** because the visit of the
element's node in the document tree still only corresponds with its type-0
scope, *not* with its type-1 scope. Naming the pair of tags "an element",
while implicitly including all the descendant elements in between, does not
change that.
