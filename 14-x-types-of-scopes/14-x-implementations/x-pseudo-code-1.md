
* the following is based on the concept of "parent containers"

<!-- ======================================================================= -->

Note that the following pseudo-code example is in regards to regular properties,
each of which is associated with one of the previously defined types of scopes.

```
Node {
  //- initialize a set of those
  //  properties the node declares
  getDeclaredProperties()

  //- the node is understood to be in
  //  the scopes of these properties
  Set<Property> properties

  //- the scopes of these properties
  //  end with the node's t1-exit event
  Set<Property> parentContainerOf
}
```

<!-- ======================================================================= -->

Assumed that the definition of a node is extended as above, an implementation
may plan the closure as follows.

```
//- used to maintain all those properties
//  whose scopes still count as being open
Set<Property> openProperties.

//- triggered when node n is reached
onVisit(n) {
  //- process the declared properties
  foreach(p in n.getDeclaredProperties()) {
    p.open()

    switch(p.getTypeOfScope()) {
    case "type-0":
      //- (n inside-of p) is true
      n.properties.add(p)
      p.close()
    case "type-1"://- un-ordered tree
      container = n
    case "type-2"://- ordered tree
      //- the parent in the un-ordered tree
      container = n.getParentNode()
    case "type-3"://- pre-order trace
      container = n.getRootNode()
    default:
      throw "invalid type"
    }

    if(p.isOpen() == true) {//- a non-null scope
      //- maintain the property as an open property
      openProperties.add(p)
      //- plan the property's closure
      container.parentContainerOf.add(p)
    }
  }

  //- associate the node with all open properties
  foreach(p in openProperties) {
    //- (n inside-of p) is true
    n.properties.add(p)
  }
}
```

<!-- ======================================================================= -->

Once the above steps have been executed, an implementation can close the scopes
of those properties to which the node is a parent container.

```
//- triggered when node n and all its
//  descendants have been visited
onExitT1(n) {
  //- close all scopes/properties
  foreach(p in n.parentContainerOf) {
    openProperties.remove(p)
    p.close()
  }
}
```
