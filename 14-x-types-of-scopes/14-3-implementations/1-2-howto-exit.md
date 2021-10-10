
<!-- ======================================================================= -->
# howto implement exit events?

As mentioned before, any implementation must explicitly create and maintain
objects, each of which can be said to represent some amount of knowledge. An
implementation must therefore explicitly mark the object it associates with a
particular scope as being closed. This to keep the implementation's knowledge
base in a consistent state.

```
<r> .. <p> .. <n> c(n) </n> s(n) </p> s(p) .. </r>
|-t(T)------------------------------------------>|
scope-t3(n)   |-t3------------------------------>|
scope-t2(n)   |-t2----------------->|
scope-t1(n)   |-t1------->|
scope-t0(n)   |-| t0
```

Since each scope begins with the start-tag of its defining node, and may end
with the end-tag of another node (i.e. both tags may belong to distinct nodes),
implementations must map its type-2 and type-3 exit events onto the type-1
exit-event of the corresponding node.

```
  type-0                          type-1/2/3
.. <n> ............................. </x> ..
   |-> enter node n, detect all scopes  | onEnter(n)
   |-> plan the closure of all scopes   |
   |        close all relevant scopes ->| onExitT1(x)
```

Because of that, implementations must in general **plan the closure of a scope**
(i.e. "initialize and postpone") when it reaches the scope's defining node.
After that, the close operation can be executed when the corresponding type-1
exit-event is triggered. An implementation must therefore maintain some memory
it can query in order to determine which scopes to close whenever an end-tag
is reached.

Note that each of these end-tags belongs to a node in the rooted path of the
scope's defining node - i.e. the current node, its parent, the tree's root.
Because of that, the objects associated with each node in a rooted path can
in principle be used to plan the closure of a scope. However, one should in
general maintain a separate storage location for that purpose since one needs
to ensure that this temporary knowledge will be dropped once the overall
process has finished.

Recall that, strictly speaking each scope ends with a last subsequent leaf.
That is because that leaf node has no further node subsequent to it in the
scope's base order. However, since one can not define which node that will
be, a definition has no other means but to work with upper/outer boundaries.
Because of that, and even though a scope in general ends with the exit-event
of the last subsequent leaf, definitions can only work with the next end-tag
of one of the leaf's ancestors that can be guaranteed to exist.

<!-- ======================================================================= -->
## the visit of a node

```js
traverseInDocOrder(node) begin
  {//- onEnter(node)
    //- determine the properties defined by "node"
    onEnterT0123(node)

    //- run all operations related to "node"
    //  and apply all open properties
    onVisit(node)

    //- close all type-0 scopes
    //- plan the closure of every other scope
    //  of the properties defined by "node"
    onExitT0(node)
  }//- onEnter(node)

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
merely fictional and intended to express the internal stages of processing
the more general onEnter() event.

Note that there are no onExitT2() and no onExitT3() events. That is because
these correspond with the onExitT1() event of one of the defining node's
ancestors.

<!-- ======================================================================= -->
## remarks

Recall that a scope is **forwards oriented** (i.e. along the edges). In contrary
to that, the decision to close a scope is **backwards oriented** (i.e. against
the orientation of the document order). That is because the closure of a scope
is effectively delayed until the next subsequent end-tag that can be guaranteed
to exist. Because of that, the actual closure of a scope can be understood to
"fix" an inconsistent intermediate state since the corresponding scope has
already ended.

Note that **each end-tag may mark the end of more than one scope**. After all,
the end-tag of a tree's root marks the end of the root's type-1 scope, the end
of all type-2 scopes of its child nodes, and also the end of all type-3 scopes
of all its descendants. Similar to that, the end-tag of every other node marks
the end of the node's type-1 scope and also the end of all type-2 scopes of its
child nodes.

Note that implementations will have to take into account that a **root** could
be associated with type-2/3 properties. For obvious reasons, the scopes of such
properties must be closed with the root's end-tag. The reason being is that a
doctree's root has no parent and therefore also no root as its ancestor.

Note that extensions, such as rank values, may in principle close a scope
before the corresponding end-tag is reached. Because of that, close operations
must be **idempotent** (i.e. have no effect if a scope was already closed).

Note the relationship between the end of a type-3 scope and its defining node
is **in general unclear**. That is, from the point of view of a root's end-tag,
one can only tell that the defining node is one of the non-root nodes in the
document tree. Compared to that, the defining node of a type-2 scope always is
one of the container's child nodes.

Note that **a certain closing order could be required**. That is because a
descendant scope (i.e. a subset of nodes) must in general be closed before
its ancestor scopes (i.e. a hierarchy of scopes).
