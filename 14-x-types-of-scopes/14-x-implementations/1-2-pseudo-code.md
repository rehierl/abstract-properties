
<!-- ======================================================================= -->
# a pseudo-code example

```js
Node {
  //- initialize a set of those
  //  properties the node declares
  getDeclaredProperties()

  //- a set of those properties the
  //  node instance is associated with
  Set<Property> properties

  //- a set of properties whose scopes must
  //  be closed with the type-1 exit-event
  //  of this node instance
  Set<Property> parentContainerOf
}//- Node

//- used to maintain all those properties
//  whose scopes still count as being open
Set<Property> openProperties
```

Assumed that the definition of a node is as above, and assuming the existence
of "a set of all open properties", an implementation could plan the closure of
all scopes as follows.

```js
//- triggered when node n is being visited
onVisit(n) {

  //- process the declared properties
  foreach(p in n.getDeclaredProperties()) {

    //- determine the property's type of scope
    switch(p.getTypeOfScope()) {
    case "type-0":
      container = null
    case "type-1"://- scope of node
      container = n
    case "type-2"://- extended scope
      container = n.getParentNode()
    case "type-3"://- unrestricted scope
      container = n.getRootNode()
    }//- switch

    if(container == null) {
      p.open()
      n.properties.add(p)
      p.close()
    } else {//- type-1/2/3
      p.open()
      openProperties.add(p)
      container.parentContainerOf.add(p)
    }
  }

  //- associate the node with all open properties
  foreach(p in openProperties) {
    n.properties.add(p)
  }
}
```

Once the above steps have been executed, an implementation can close the scopes
of those properties to which the node is a parent container.

```js
//- triggered when node n and all of
//  its descendants have been visited
onExitT1(n) {
  //- close all scopes/properties
  foreach(p in n.parentContainerOf) {
    openProperties.remove(p)
    p.close()
  }
}
```

<!-- ======================================================================= -->
## remarks

Note that specific kinds of properties (i.e. restricted type systems) may allow
for more efficient implementations. Sections for example will never be defined
as having a type-0 scope since they could then have no content nodes.

Note that the above pseudo-code is merely intended to showcase a basic approach.
Because of that, there are no specific checks. That is, `n.getParentNode()` and
`n.getRootNode()` must be assumed to return the root (i.e. node `n`) if `n` is
the doctree's root.

Note that "the root node" of an HTML document tree is at this point assumed to
be "the body element". That is because that element is the doctree's topmost
content node.
