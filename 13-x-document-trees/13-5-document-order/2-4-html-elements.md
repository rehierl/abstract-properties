
<!-- ======================================================================= -->
# html elements

The following is intended to point out that the definition of HTML elements
in the official specification can - one way or another - be easily misread.

What one must always keep in mind is that it is quite difficult to express
a certain point of view, while still ensuring that the reader audience will
understand the written statements as they were intended. Despite that, well
established descriptions (e.g. "ordered tree") can still turn out to be
quite misleading.

<!-- ======================================================================= -->
## the definition of an element

whatwg.org / 13.1.2 Elements / as of 2021-09-08

* Tags are used to delimit the start and end of elements in the markup.

Since tags are described to delimit the extent of an HTML element, one might
be mislead conclude that HTML sees elements as consisting of its start-tag
and its end-tag, and as containing everything in between.

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

Note that it does not state "its descendants", instead the statement refers
to the top level elements (i.e. "its children") of a parent element, which
does quite explicitly exclude any distant descendant. As such, the statement
does suggest a recursive point of view on elements.

<!-- ======================================================================= -->
## a misleading point of view

```
    |-html-element------------------|
.., | <n>,      | ..,     | </n>,   | ..
    |-start-tag-|-content-|-end-tag-|
    |-scope(n)------------|-empty---|
```

As described above, the description of "HTML element" can be misunderstood
such that an element consists of its start-tag, its end-tag and also includes
everything in between. That is, one might be mislead to believe that an element
in HTML is, similar to an induced subtree, a complex unit of elements. That
point of view is however misleading.

That is because the tag soup of a document is read into a node tree, which is
why, regardless of ones current point of view, each HTML element directly
corresponds with one and only one node in the DOM tree. An HTML element can
therefore not be understood to be equivalent to an entire (induced) subtree,
which is what the official definition might seem to suggest.

**One must always distinguish between an element (a node) and its scope.**

Note that, as a matter of clarity, this discussion will continue to describe
even HTML elements as the nodes in the corresponding DOM tree.

Note that the scope of a node is not to be confused with the contents of an
element. That is because the scope of a node also includes the node itself.
In addition to that, the scope of a node does strictly speaking not contain
the node's end-tag since an end-tag does not translate into any node.

Note that an element does not remain in the process of being visited while the
element's descendants are being visited. That is because there would otherwise
be no correlation between the nodes and the document's pre-order trace. The
visit of a node must be understood as an uninterruptable atomic operation.
