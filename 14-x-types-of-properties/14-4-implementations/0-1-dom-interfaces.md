
<!-- ======================================================================= -->
# the dom tree

Recall that a HTML document is accessible to an implementation in terms of a
DOM tree, which is why a document tree must be traversed as DOM nodes. The
following will therefore take a short look at those properties and methods of
the DOM interfaces that are relevant to implementing a traversal algorithm.

Note that an Element is understood as a base interface that extends the Node
interface and which itself is extended by interfaces that are more specialized.
That is, **an element must be understood to implement a certain type of node**,
not so much as being synonymous to the theoretical concept of a node. With that
in mind it can be pointed out that a DOM tree has more nodes than a tag soup
has pairs of tags.

Note that Mozilla's MDN Web Docs denotes deprecated properties and methods.
In contrary to that, WHATWG's specification does not seem to maintain such
information. Further inconsistencies between WHATWG and MDN can be found.

<!-- ======================================================================= -->
## the Node interface

```js
Node {
  //- e.g. Node.ELEMENT_NODE (1)
  //- e.g. Node.ATTRIBUTE_NODE (2)
  ushort nodeType

  //- depends on the implementing interface
  //- e.g. an utf-16 encoded string
  //- e.g. Element.tagName
  DOMString nodeName

  //- returns the value of the current node
  //- e.g. text, comments, cdata, attributes
  DOMString? nodeValue

  //- element - the descendant text content
  //- attributes - the attribute's value
  DOMString? textContent

  //- unclear descriptions ...
  //- options:false - to include the shadow root
  Node getRootNode(options?)

  //- the node's parent in DTU
  Node? parentNode

  //- unclear descriptions ...
  Element? parentElement

  //- a 0-based list of child nodes in DTU
  //- includes elements, text and comments
  NodeList childNodes

  //- the node's first child in DTU
  //- should be equal to childNodes.item(0)
  Node? firstChild

  //- the node's last child in DTU
  Node? lastChild

  //- the node's immediate predecessor
  //- i.e. its next presequent sibling in DTU
  Node? previousSibling

  //- the node's immediate successor
  //- i.e. its next subsequent sibling in DTU
  Node? nextSibling
}//- node
```

The `Node` interface provides object properties and methods that are common
to all node objects in the DOM tree. This includes elements and their content
attributes.

- https://dom.spec.whatwg.org/#interface-node
- https://developer.mozilla.org/en-US/docs/Web/API/Node

<!-- ======================================================================= -->
## the Element interface

```js
Element : Node {
  //- the HTML-uppercased qualified name
  //- e.g. "IMG" for an "<img>" element
  DOMString tagName

  //- the local part of the qualified name
  DOMString localName

  //- non-standard, declared by MDN
  //- get/set the markup of the element's descendants
  //- warning - security issues - use Node.textContent
  DOMString innerHTML

  //- non-standard, declared by MDN
  //- get/set the markup of the element and its descendants
  DOMString outerHTML

  //- a 0-based list of those attribute nodes
  //  that are defined for the current element
  //- has a .length property and an .item() method
  //- can use Node properties to iterate
  NamedNodeMap attributes

  //- returns the attribute's value if it exists
  DOMString? getAttribute(DOMString qualifiedName)

  //- a list of element nodes that matched qualifiedName
  //- if "*" - all the descendants of the current element
  //- has a .length property and an .item() method
  //- the elements are listed in pre-order node order
  //- "HTMLCollection" is considered a historical name
  HTMLCollection getElementsByTagName(DOMString qualifiedName)
}//- Element
```

The `Element` interface provides further object properties and methods in
addition to those of the `Node` interface.

- https://dom.spec.whatwg.org/#element
- https://developer.mozilla.org/en-US/docs/Web/API/element

<!-- ======================================================================= -->
## the Attr interface

```js
Attr : Node {
  //- the attribute's qualified name
  DOMString name

  //- the local part of the qualified name
  DOMString localName

  //- the attribute's value
  //- same as Node.nodeValue?
  DOMString value
}//- Attr
```

The `Attr` interface is used to represent one of the attributes of an element
as a node object, which allows to iterate over the attributes of an element.

- https://dom.spec.whatwg.org/#attr
- https://developer.mozilla.org/en-US/docs/Web/API/Attr

Note that, except for very few properties in addition to those displayed, the
`Attr` interface can be said to merely join an attribute's name with its value.

<!-- ======================================================================= -->
## the HTMLElement interface

```js
HTMLElement : Element {
  //- "" if empty
  //- the readable content of the element's descendants
  //- might depend on the element's render status
  //- the text content if highlighted by a user
  //- MDN - different to Node.textContent
  DOMString innerText

  //- "" if empty
  //- listed by WHATWG, declared non-standard by MDN
  DOMString outerText

  //- true if the element is not to be rendered
  //- reflects the element's "hidden" content attribute
  boolean hidden
}//- HTMLElement
```

The `HTMLElement` interface provides further properties and methods in addition
to those of the DOM's `Element` interface.

- https://html.spec.whatwg.org/multipage/dom.html#elements-in-the-dom
- https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement
