
<!-- ======================================================================= -->
# html elements

The following is intended to point out that the definition of HTML elements
in the official specification can - one way or another - be easily misread.

One must always keep in mind that it is quite difficult to express a certain
point of view, while still ensuring that the reader will understand the written
statements as they were intended. Despite that, well established descriptions
(e.g. "ordered tree") can themselves also turn out to be quite misleading.

<!-- ======================================================================= -->
## the definition of an element

whatwg.org / 13.1.2 Elements / as of 2021-09-08

* Tags are used to delimit the start and end of elements in the markup.

Since tags are described to delimit the extent of an HTML element, one might
be mislead to conclude that an element in HTML consist of its start-tag, its
end-tag and also includes everything in between. This however is not true
since each HTML element corresponds with only one node in the document tree.

<!-- ======================================================================= -->
## the contents of an element

whatwg.org / 13.1.2 Elements / as of 2021-09-08

* The contents of the element must be placed between just after the start
  tag and just before the end tag. The exact allowed contents ... depend
  on the content model of that element ...

whatwg.org / 3.2.5 Content models / as of 2021-09-08

* The contents of an element are its children in the DOM.

Since the content of an element is described as being defined by its child
nodes in the DOM tree, one can conclude that HTML sees elements as being
recursive in nature.

Note that it does not state "its descendants", instead the statement only
refers to the top level elements (i.e. "its children") of a parent element,
which does quite explicitly exclude any distant descendant. As such, the
statement does suggest a recursive point of view on elements.

<!-- ======================================================================= -->
## a misleading point of view

```
    |-html-element------------------|
.., | <n>,      | ..,     | </n>,   | ..
    |-start-tag-|-content-|-end-tag-|
    |-scope(n)------------|-empty---|
```

As described above, the description of "HTML element" can be misunderstood
such that an element consists of its start-tag and its end-tag, while
including everything in between. That is, one might be mislead to believe
that an element in HTML is, similar to an induced subtree, a complex unit
of many elements. That point of view is however misleading.

That is because the tag soup of a document is read into a node tree, which
is why, regardless of ones current point of view, each HTML element directly
corresponds with one and only one node in the DOM tree. An HTML element can
therefore not be understood to be equivalent to an entire (induced) subtree,
which is what the official definition might seem to suggest.

**One must always distinguish between an element (a node) and its scope.**

Note that, as a matter of clarity, this discussion will continue to refer
to HTML elements as the nodes in a DOM tree.

Note that the scope of a node is not to be confused with the contents of an
element. That is because the scope of a node includes the node itself and
also all of its descendants in the unordered document tree. In addition to
that, the scope of a node does strictly speaking not contain the node's
end-tag since an end-tag does not correspond with any node. That is because
an end-tag is nothing more but an end marker.

Note that an element does not remain in the process of being visited while
the element's descendants are being visited. That is because there would
otherwise be no correlation between the nodes and the document's pre-order
trace. The visit of a node must still be understood as an atomic operation.