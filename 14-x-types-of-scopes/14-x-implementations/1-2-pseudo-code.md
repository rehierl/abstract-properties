
<!-- ======================================================================= -->
# a pseudo-code example

Note that the code below is intended to merely showcase a basic approach.
Because of that, there are no specific checks. That is, `n.getParentNode()`
and `n.getRootNode()` must be understood to return a self-reference, if the
current node is the doctree's root. That is, both methods are understood to
always return a node instance, never a null reference.

Note that specific kinds of properties (i.e. restricted type systems) may allow
for more efficient implementations. Sections for example will never be defined
as having a type-0 scope since they could then never have any content nodes.

Note that "the root node" of an HTML document tree is at this point assumed to
be "the body element". That is because that element is the doctree's topmost
content node.

<!-- ======================================================================= -->

```js
Node {
  //- the doctree's root or $this
  Node getRootNode()

  //- the node's parent or $this
  Node getParentNode()

  //- initialize a set of those
  //  properties the node declares
  Set<Property> getDeclaredProperties()

  //- a set of those properties the
  //  node instance is associated with
  Set<Property> properties
}//- Node
```

Assuming that the definition of a node is extended as above, ...

```js
Property {
  //- used to indiciate the default scope of
  //  this property instance - i.e. "type-0",
  //  "type-1", "type-2" or "type-3"
  string getTypeOfScope()

  //- the node that declared this property instance
  Node definingNode

  //- the node whose type-1 exit event must
  //  be used to close the property's scope
  //- null, if the property's scope ends with
  //  the start-tag of its defining node
  Node parentContainer

  //- used to mark the property's scope
  //  as being open for associations
  void open()

  //- used to mark the property's scope
  //  as being closed for associations
  //- should be idempotent
  void close()
}//- Property

//- a set of all those properties whose
//  scopes are still open for associations
Set<Property> openProperties
```

... and assuming the above basic property definition, an implementation can
plan the closure of all scopes as shown next.

<!-- ======================================================================= -->

```js
onEnterT0123(n) {
  //- initialize and open all declared properties
  foreach(p in n.getDeclaredProperties()) {
    p.definingNode = n

    //- determine the property's default scope
    //  and set its parent container accordingly
    switch(p.getTypeOfScope()) {
    case "type-0":
      p.parentContainer = null
    case "type-1"://- scope of a node
      p.parentContainer = n
    case "type-2"://- extended scope
      p.parentContainer = n.getParentNode()
    case "type-3"://- unrestricted scope
      p.parentContainer = n.getRootNode()
    }//- swtich

    p.open()
    openProperties.add(p)
  }
}//- onEnterT0123
```

With "a set of all open properties" being maintained, the visit-event of a
node can be used to associate a node with these properties. (Recall that an
extension may in principle close one or more open properties).

```js
onVisit(n) {
  //- choose to close one or more open properties
  //- associate with all remaining open properties
  foreach(p in openProperties) {
    n.properties.add(p)
  }
}//- onVisit
```

Just after the node's visit-event has been processed, all type-0 properties
must be closed.

```js
onExitT0(n) {
  //- close all type-0 properties
  foreach(p in openProperties) {
    if(p.parentContainer === null) {
      openProperties.remove(p)
      p.close()
    }
  }
}//- onExitT0
```

Once all the descendants of a node have been visited and its type-1 exit-event
is triggered, all open properties to which the node is a parent container must
be closed.

```js
onExitT1(n) {
  //- close relevant type-1/2/3 properties
  foreach(p in openProperties) {
    if(p.parentContainer === n) {
      openProperties.remove(p)
      p.close()
    }
  }
}
```
