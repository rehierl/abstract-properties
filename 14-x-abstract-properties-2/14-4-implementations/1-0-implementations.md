
<!-- ======================================================================= -->
# an implementation-based point of view

Note that the following restrictions are in regards to the definition of default
scopes, which can be seen as **upper boundaries**. Also, the following is in
regards to the traversal of a document tree, which is why possible input errors
will be ignored.

Note that future extensions may or may not **restrict a scope to a prefix** of
its default scope. Despite that, extensions remain subject to the restrictions
layed out below.

<!-- ======================================================================= -->
## implementation-based restrictions

```js
//- the basic document tree traversal
traverseInDocOrder(node) begin
  //- used to write start-tags
  //- write("<%s %s>", name, attributes)
  onEnter(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInDocOrder(child)
  end

  //- used to write end-tags
  //- write("</%s>", name)
  onExit(node)
end
```

In regards to the end of a scope one can state that an implementation must react
to the end of each scope. That is because a scope would otherwise remain open
for associations until the end of a document, which might exceed the base order
(i.e. an upper boundary) of that scope. The definition of a scope must therefore
be such that an implementation has well defined points it can use to explicitly
mark a scope as being closed.

* implementations must have the means to react to the end of each scope

Recall that any node in a document tree may in general have any number of child
nodes. In addition to that, no node can be guaranteed to have a certain types
of, or a certain number of child nodes. Consequently, the pre-order traversal
of a doctree does not provide the means to reliably define that a scope ends
at a certain point in between a parent's first child and its last child.

Because of that, no generic definition (i.e. doctree independent definition)
can be provided such that a scope ends with some n-th child of a parent. Such
restrictions, if they can even be supported, must be provided externally by
some specific descendant node (e.g. a rank-based heading).

* no scope can by default end in between a parent's first and last child
* each scope either includes all child nodes exor none at all

```
.. <node> .. </node> ..
   |1  |2    |3
```

A scope can consequently only be defined such that it ends with a parent and
therefore just before its first child, or such that it ends just after its last
child, while including all of the child nodes and their descendants.

* any scope ends by default with an enter- exor an exit-event
* any scope must **end with a start-tag (1/2) exor an end-tag (3)**

Note that "ends with a start-tag" is ambiguous since each start-tag corresponds
with a node. As such, this description can be understood to mean two different
things: (1) the scope ends just before the visit of the start-tag's node while
excluding that node, exor (2) the scope ends just after the visit of that node
while including that node. Definitions, which build upon a start-tag in that
regards, must therefore be clear about which case applies.

Note that, since the last node of a suborder is always defined by the last
node's start-tag, and since that last node must be a leaf to the underlying
base order, any scope can always be said to end with a start-tag (case-2).
The difficulty with that description is however that one can not provide a
generic definition that can be used to identify a node as such a last node.
That is because any assumption, which would allow to identify a node as that
last node would effectively introduce requirements that can not be relied
upon (e.g. due to possible input errors).

Note that the above is intended to point out that the enter- and exit-events
of a node can be guaranteed to exist in the context of that node. Because of
that, the following will focus on these events since both represent well
defined processing steps that can be guaranteed to exist.

<!-- ======================================================================= -->
## trivial vs. non-trivial base orders

Recall that the trivial base order is the only order such that one can state
that no node has another node subsequent to it. Because of that, every scope
defined over a trivial base order is such that it begins and ends with the
start-tag of its defining node, while including the node itself (case-2).

* t0 - any scope over a trivial base order begins and ends with a **start-tag**

Every other base order is such that the scopes over it begins with a defining
node and includes all the nodes up to and including the last node subsequent to
it (i.e. a descendant to the defining node in that base order). Any scope over
a non-trivial base order therefore ends with the end-tag of its last subsequent
leaf (case-3).

* any scope over a non-trivial base order ends with an **end-tag**

Note that, extensions such as subsequent rank-based headings may be such that
the section of a presequent heading ends with the start-tag of a subsequent
heading, while excluding the subsequent heading (case-1).

<!-- ======================================================================= -->
## non-trivial base orders

The following will point out which end-tags can be guaranteed to exist in the
context of a scope over a non-trivial base order.

Note that, if the defining node of a scope is reached by an implementation,
then that node is guaranteed to exist. Consequently, definitions can be made
in regards to that node since its end-tag (i.e. a then future exit event) can
then be guaranteed to be reached eventually.

(0) The first end-tag that could be used to define the default end of a scope
over a non-trivial suborder is the end-tag of the last subsequent descendant
leaf of the scope's defining node. However, since a definition can not rely
on the existence any descendant, the end-tag of the defining node is the first
end-tag a definition can build upon.

* t1 - the end-tag of the defining node

(1) If the defining node is **the doctree's root**, then only the root's
end-tag can be guaranteed to exist. Because of that, the default scope over
a non-trivial base order, that has the doctree's root as its defining node,
must end in the root's end-tag.

* t1 - the end-tag of the doctree's root
* note - the root's t1 scope is equal to its t2 and t3 scopes

(2) If the defining node is **a child to the doctree's root**, then only
its end-tag and the end-tag of the doctree's root are guaranteed to exist.

* t1 - the end-tag of the defining node
* t2 - the end-tag of the doctree's root
* note - the node's t2 scope is equal to its t3 scope

(3) If the defining node is **a distant descendant to the doctree's root**,
then only its end-tag, the end-tag of its parent, and the end-tag of the
doctree's root is guaranteed to exist.

* t1 - the end-tag of the defining node
* t2 - the end-tag of its parent
* t3 - the end-tag of the doctree's root

Note that, similar to the existence of child nodes (i.e. any node may have any
number of child nodes), the existence of any other ancestor can not be relied
upon.

Note that the above end-tags all belong to nodes that are nodes in the rooted
path of a defining node. That is because all the nodes in that rooted path are
guaranteed to exist since they have been visited already. A rooted path can
therefore be understood to maintain a certain amout of knowledge of past nodes.

<!-- ======================================================================= -->
## four types of scopes only

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Note that the above considerations are consistent with the amount of orders in
the linear extension, which begins in the trivial suborder DTR and ends in the
processing order DPR. Based on that, it will be assumed that there simply is no
other base order available.

* no more than four distinct types of (default) scopes are available
