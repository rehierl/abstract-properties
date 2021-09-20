
<!-- ======================================================================= -->
# a pseudo-code example

Note that the following pseudo-code example is in regards to regular
properties, each of which is associated with one of the previously
defined types of scopes.

```js
Node {
  //- initialize a set of those
  //  properties the node declares
  getDeclaredProperties()

  //- this node is associated
  //  with these properties
  Set<Property> properties

  //- the scopes of these properties
  //  end with the node's t1-exit event
  Set<Property> parentContainerOf
}
```

Assumed that the definition of a node is as above, an implementation
could plan the closure of all scopes as follows.

```js
//- used to maintain all those properties
//  whose scopes still count as being open
Set<Property> openProperties

//- triggered when node n is being visited
onVisit(n) {
  //- process the declared properties
  foreach(p in n.getDeclaredProperties()) {
    //- mark the property's scope as open
    p.open()

    switch(p.getTypeOfScope()) {
    case "type-0":
      n.properties.add(p)
      p.close()
    case "type-1"://- scope of node
      container = n
    case "type-2"://- extended scope
      container = n.getParentNode()
    case "type-3"://- unrestricted scope
      container = n.getRootNode()
    }//- switch

    if(p.isOpen()) {//- a non-null scope
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

Once the above steps have been executed, an implementation can close
the scopes of those properties to which the node is a parent container.

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

Note that specific kinds of properties may allow for far more efficient
implementations. Sections for example will certainly never be defined
as having a type-0 scope since they could then have no content at all.
Because of that, the type-0 case in onVisit() will not be required.
Also, any section will remain open when the visit of the current node
has been finished.
