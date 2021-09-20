
<!-- ======================================================================= -->
# howto implement exit events?

As mentioned before, any implementation must explicitly create and maintain
objects, each of which can, from an implementation's point of view, be said to
represent one piece of its knowledge base. Because of that, an implementation
must explicitly mark the object it associates with a particular scope as being
closed, as soon as it has exited the corresponding scope.

```
<r> ... <p> ... <n> c(n) </n> s(n) </p> s(p) ... </r>
|-t(T)--------------------------------------------->|
scope-t3(n)     |-t3------------------------------->|
scope-t2(n)     |-t2----------------->|
scope-t1(n)     |-t1------->|
scope-t0(n)     |-| t0
```

Since each scope begins with the start-tag of its defining node, and may end
with the end-tag of another node (i.e. both tags may belong to distinct nodes),
implementations must map the type-2 and type-3 exit events onto the type-1
exit event of the corresponding node.

```
  type-0                             type-1/2/3
.. <n> ................................ </x> ..
    |-> enter node n, detect all scopes   | onEnter(n)
    |-> plan the closure of all scopes    |
    |         close all relevant scopes ->| onExitT1(x)
```

Because of that, implementations must in general **plan the closure of a scope**
(i.e. "initialize and postpone") when it reaches the scope's defining node.
After that, the close operation can be executed when the corresponding type-1
exit event was triggered.

Put differently, an implementation must keep track of which scopes count as
being open. An implementation is therefore required to maintain some memory
it can use in order to determine which scopes to close whenever it reaches
an end-tag.

Note that each of these end-tags belongs to a node in the rooted path of the
scope's defining node - i.e. the current node, its parent, the tree's root.
Because of that, the object of each node in a rooted path can in principle
be used to plan the closure of a scope. However, one should in general use a
separate storage location for that purpose. This in order to ensure that the
temporary information will be dropped once the overall process has finished.

Note that the node whose type-1 exit-event will be used to close the scope,
will be described as **the scope's surrounding (parent) container**, which
can be described to be analogous to a numeric upper/outer boundary.

Recall that, strictly speaking each scope ends with the last subsequent leaf
node in it. That is because that leaf node has no further node subsequent to
it in the scope's base order. However, since one can not define which node
will be that last node, any definition has no other means but to work with
upper/outer boundaries. Because of that, and even though a scope in general
ends with the exit-event of the last subsequent leaf, definitions can only
work with the next subsequent end-tag of one of the leaf's ancestors.

<!-- ======================================================================= -->
## the visit of a node

```js
traverseInDocOrder(node) begin
  //- determine the properties defined by "node"
  onEnterT0123(node)

  //- run all operations related to "node"
  //  and apply all open properties
  onVisit(node)

  //- close all type-0 scopes
  //- plan the closure of every other scope
  //  of those properties defined by "node"
  onExitT0(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInDocOrder(child)
  end

  //- close all scopes to which "node"
  //  is the surrounding container
  onExitT1(node)
end
```

Note that the separation into onEnterT0123(), onVisit() and onExitT0() is
merely fictional and intended to express the internal stages of onEnter().

Note that there are no onExitT2() and no onExitT3() events since these
correspond with the onExitT1() event of one of the defining node's ancestors.

Note that, except for type-0 scopes, and regardless of any future extensions,
no scope, other than the node's type-0 scopes end while a node is in the
process of being visited.

<!-- ======================================================================= -->
## remarks

Note that a scope is **forwards oriented** (i.e. along the edges). In contrary
to that, the decision to close a scope is **backwards oriented** (i.e. against
the orientation of the document order).

Note that **each end-tag is located in between two nodes** and may mark the end
of more than one scope. After all, the end-tag of a tree's root marks the end
of the root's type-1 scope, the end of all type-2 scopes of its child nodes,
and also the end of all type-3 scopes of all its descendant nodes. In addition
to that, the end-tag of every other node marks the end of the node's type-1
scope and also the end of all type-2 scopes of its child nodes.

Note that implementations will have to take into account that a **root** could
be associated with type-2/3 properties. For obvious reasons, the scopes of
these properties must be closed with the root's end-tag.

Note that implementations will have to take into account that the **child**
nodes of a root could be associated with type-3 properties. As before, the
scopes of these properties must be closed with the root's end-tag.

Note that extensions, such as rank values, may in principle close a scope
before the corresponding end-tag is reached. Because of that, one can speak
of **default scopes**. Close operations must therefore be **idempotent**.

Note the relationship between the end of a type-3 scope and its defining node
is **in general unclear**. That is, from the point of view of a root's end-tag,
one can only tell that the defining node is one of the non-root nodes in the
document tree. That is as clear as it can cet. Compared to that, the defining
node of a type-2 scope is one of the container's child nodes.

<!-- ======================================================================= -->
## closing order

Note that, depending on property definitions, a particular closing order may
be required. That is because a descendant scope (i.e. a subset) must in general
be closed before its ancestor scopes (i.e. in the case of a hierarchy).

TODO
- what if the exit-events of multiple scopes match the same end-tag?
- default? - in reversed order of appearance of the defining nodes
