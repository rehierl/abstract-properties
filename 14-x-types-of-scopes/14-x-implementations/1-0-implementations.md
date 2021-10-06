
<!-- ======================================================================= -->
# an implementation-based point of view

Note that the following restrictions are in regards to the definition of default
scopes (i.e. **upper boundaries**).

Note that future extensions may be allowed to **restrict a scope to a prefix**
of its default scope. However, extensions remain subject to the restrictions
which will be layed out below.

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

In regards to the end of a scope one can state that an implementation must in
general explicitly react to the end of a scope. That is because a scope would
otherwise remain open for associations until the end of a document, which might
exceed the base order of that scope. The definition of a scope must therefore
be such that an implementation has well defined points it can use to explicitly
mark a scope as being closed.

* implementations must have the means to react to the end of any scope

Recall that any node in a document tree may in general have any number of child
nodes. In addition to that, no node can be guaranteed to have a certain number
of child nodes. Consequently, the pre-order traversal of a doctree does not
provide the means to reliably define that a scope ends at a certain point in
between a parent's first child and its last child.

Because of that, no generic (i.e. doctree independent) definition can be
provided such that a scope ends by default with some n-th child of a parent.
Such restrictions, if they can even be supported, must be provided externally
by some descendant node (e.g. a rank-based heading).

* no scope can by default end in between a parent's first and last child
* by default, each scope either includes all child nodes exor none at all

```
.. <node> .. </node> ..
   |1  |2    |3
```

As a matter of consequence, a scope can only be such that it ends with a parent
and therefore just before its first child, or it ends just after a parent's
last child, while including all of the child nodes and their descendants.

* any scope ends by default with an enter- exor an exit-event
* any scope must **end with a start-tag (1/2) exor an end-tag (3)**

Note that "ends with a start-tag" is by itself ambiguous since each start-tag
corresponds with a node. As such, this description can be understood to mean
two things: (case-1) ends just before the visit of the start-tag's node (i.e.
excluding that node), exor (case-2) just after the visit of that node (i.e.
including that node). Definitions, which build upon a start-tag in that
regards, must therefore be clear about which case applies.

Note that, since the last node of a suborder is always defined by the last
node's start-tag, and since that last node must be a leaf to the corresponding
base order (otherwise there would be another node subsequent to it), any scope
can always be said to end with a start-tag (case-2). The difficulty with that
description is however that one can not provide a generic definition that can
be used to identify such a node as the last node. That is because any assumption,
which would allow to identify a node as that last node effectively introduces
requirements that can not be relied upon (e.g. input errors).

Note that the above is intended to point out that the enter- and exit-events of
a node can be guaranteed to exist in the context of that node. Because of that,
the following will focus on these events since both represent well defined
processing steps that can be relied upon.

<!-- ======================================================================= -->
## trivial vs. non-trivial base orders

Recall that the trivial base order is the only order such that one can state
that no node has another node subsequent to it. Because of that, every scope
defined over a trivial base order is such that it begins and ends with the
start-tag of its defining node while including the node itself (case-2).

* t0 - any scope over a trivial base order begins and ends with a **start-tag**

Every other base order is such that the scopes over it begin with a defining
node and end in another node (i.e. a node subsequent to it - a descendant in
that base order). Consequently, any scope over a non-trivial base order ends
with the end-tag of its last subsequent leaf (case-3).

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
also be guaranteed to exist.

(0) The first end-tag that could be used to define the default end of a scope
over a non-trivial suborder is the end-tag of the last subsequent descendant
leaf of the scope's defining node. However, since a definition can not rely on
the existence any of the descendants of the defining node, the end-tag of the
defining node is the first end-tag a definition can rely upon.

* t1 - the end-tag of the defining node

(1) If the defining node is **the doctree's root**, then only the root's
end-tag that can be guaranteed to exist is the root's end-tag. Because of that,
the default scope over a non-trivial base order, that has the doctree's root
as its defining node, must end in the root's end-tag.

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

Note that, similar to the existence of child nodes of a node (i.e. any node
may have any number of child nodes), the existence of any other ancestor can
not be relied upon.

Note that the above end-tags all belong to nodes that are nodes in the rooted
path of the defining node that was reached. That is because all the nodes in
that rooted path are guaranteed to exist.

<!-- ======================================================================= -->
## four types of scopes only

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Note that the above considerations are consistent with the amount of base
orders in the linear extension, which begins in DTR and ends in DPR. Based on
that, it will be assumed that there simply is no other base order available.

* no more than four distinct types of (default) scopes are available
