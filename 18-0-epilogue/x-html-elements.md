
<!-- ======================================================================= -->
# html elements

```
    |?-html-element-----------------?|
    |-start-tag-|-contents-|-end-tag-|
.., | <n>,      | ...,     | </n>,   | ..
    |-scope(n)-----------------------|
    |-ce(n)-----|-iss(n)---|-empty---|
```

The following is based on the official HTML specification in order to clarify
the core semantics of "HTML Elements". To be more clear, the focus is on the
relationship between the nodes in a DOM tree and the tags in a markup. This
in order to clarify **the meaning of what an HTML element is**.

Note that the specification **remains unclear**, which is why this discussion
will continue to distinguish between the nodes and the scopes they define.

<!-- ======================================================================= -->
## introductory definitions

Note that chapter "3.2 Elements" does overall not clarify the relationship
between tags, elements and the nodes in the DOM tree. That is, it does not
state that (e.g.) each node in the tree is defined by its start-tag.

* whatwg / 3.2 Elements / as of 2022-04-10
* https://html.spec.whatwg.org/multipage/dom.html#elements

Section "3.2.2 Elements in the DOM" states that the nodes in a DOM tree
represent HTML elements. Insofar, **a correspondence** between these nodes
and the elements in the markup of a document is assumed to exist.

Section "3.2.5 Content models" describes a content model as "a description
of the element's expected contents". Furthermore it states that the "contents
of an element are **its children** in the DOM" tree.

Note that, since the content of an element is understood to be defined by
its child nodes, elements can be understood to be **recursively defined**.
After all, the specification refers to the "children" of a node and, because
of that, not directly to all of its descendants.

Note that both sections do suggests that there is a correspondence between
an element and a node in the DOM tree - i.e. the parent of those nodes that
define the content of an element. That is, the specification clearly assumes
some kind of **relationship between the elements and the nodes** in a DOM
tree. However, the specification does not clarify this relationship.

TODO - some other specification (e.g. DOM, XML, XHTML) might be more clear
about the relationship between the elements and the nodes in a DOM tree.

<!-- ======================================================================= -->
## start-tags, end-tags, attributes

* whatwg / 13.1.2.1 Start tags / as of 2022-04-10
* https://html.spec.whatwg.org/#start-tags

A listing of syntactic characteristics a start-tag must have.
That is, this section does not provide any explanation of the overall
purpose (aka. semantics) of a start-tag.

* whatwg / 13.1.2.2 End tags / as of 2022-04-10
* https://html.spec.whatwg.org/#end-tags

As before, a listing of syntactic characteristics an end-tag must have.
That is, the overall purpose of end-tags is not explained.

* whatwg / 13.1.2.3 Attributes / as of 2022-04-10
* https://html.spec.whatwg.org/#attributes-2

Once again, a mere definition of syntactic characteristics.
That is, the the overall purpose of attributes is not explained.

<!-- ======================================================================= -->
## syntactic definitions

* whatwg.org / 13.1.2 Elements / as of 2021-04-10
* https://html.spec.whatwg.org/#elements-2

""Tags are used to delimit the start and end of elements in the markup ...
Elements have a start-tag to indicate where they begin, and an end-tag to
indicate where they end.""

Since the pair of tags of an element is defined to delimit the extent of an
element, an element can be understood to include its start-tag, its end-tag
and everything in between.

* whatwg.org / 13.1.2 Elements / as of 2021-04-10
* https://html.spec.whatwg.org/#elements-2

""The contents of the element must be placed between just after the start
tag ... and just before the end tag ... The exact allowed contents ...
depend on the content model of that element ...""

Based on that, everything in between the tags of an element must be
understood to define the contents of an element.

<!-- ======================================================================= -->
## unclear definitions

Based on section 3.2, the specification quite clearly treats elements as
if they would **correspond with specific nodes** in the DOM tree - however,
without clarifying that relationship.

Based on section 13.1.2, the concept of elements can also be understood to
correspond with **the concept of scopes**. That is because, based on syntactic
rules, each element is defined to correspond with **a group of nodes** in
the DOM tree - i.e. not just with a single node.

Suffice to state that the specification remains **unclear and confusing**
since the relationship between the elements and the nodes in a DOM tree is
not explicitly addressed - e.g. by stating that the start-tags define the
nodes in the corresponding DOM tree.

Furthermore, the specification should **point out the duality of elements**.
That is, an element can be understood to correspond with a single node in
the DOM tree and also to correspond with all the nodes in the induced
subtree (i.e. a group of nodes) that has the node as its root.

<!-- ======================================================================= -->
## a misleading point of view

As described above, the definition of "HTML element" can be misunderstood such
that an element consists of its start-tag and its end-tag, while including
everything in between. That is, one is led to believe that an element in HTML
is, similar to an induced subtree, a complex unit of many elements.

That point of view is however misleading since tag soup of a document is read
into a node tree. Because of that, and regardless of ones current point of
view, each HTML element directly corresponds with one and only one node in the
DOM tree. An HTML element can therefore not be understood to be equivalent to
an entire (induced) subtree, which is what the official definition might seem
to suggest.

**One must clearly distinguish between an element (a node) and its scope.**

Note that the scope of a node is not to be confused with the contents of an
element. That is because the scope of a node includes the node itself and
all of its descendants in the DOM tree. In addition to that, the scope of
a node does strictly speaking not contain the end-tag of a node since an
end-tag does not correspond with any node. After all, an end-tag is nothing
more but an end marker.
