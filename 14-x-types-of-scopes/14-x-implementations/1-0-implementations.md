
<!-- ======================================================================= -->
# an implementation-based point of view

Note that the following definitions and restrictions are in regards to the
definition of default scopes (i.e. **upper boundaries**). That is, future
definitions may introduce even further restrictions that can not be covered
at this point.

<!-- ======================================================================= -->
## implementation-based restrictions

```
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
general explicitly react to the end of each scope. That is because a scope
would otherwise remain open for associations until the very end of a document.
As such, an implementation would then exceed the base order of that scope and
thus be in conflict with the scope's definition. The definition of a scope
must consequently be such that an implementation has well defined points it
can use to mark the scope as being closed.

* implementations must have the means to react to the end of any scope

Recall that any node in a document tree may in general have any number of
child nodes. In addition to that, no node can be guaranteed to have a certain
number of child nodes. Consequently, the pre-order traversal of a doctree does
not provide the means to reliably define that a scope ends at a certain point
in between a parent's first child and its last child.

No generic (i.e. doctree independent) definition can therefore be provided
such that a scope ends by default with some n-th child of a parent. Such
restrictions, if they can even be supported, must be provided externally
by some dedicated child node (e.g. a rank-based heading).

* no scope can by default end in between a parent's first and last child
* by default, each scope either includes all child nodes exor none at all

```
... <node> ... </node> ...
    |1  |2     |3   |3
```

As a matter of consequence, a scope may be such that it ends with a parent and
therefore just before its first child. In addition to that, a scope may be such
that it ends just after a parent's last child, while including all of the child
nodes and all of their descendants.

* any scope must (by default) end with an enter- exor an exit-event
* any scope must **end with a start-tag (1/2) exor an end-tag (3)**

Note that "ends with a start-tag" is by itself ambiguous since each start-tag
corresponds with a node. As such, this description can mean two things: (1)
ends just before the visit of the corresponding node (i.e. excluding the node),
exor (2) just after the visit of that node (i.e. including the node but still
before its first child). Definitions, which build upon a start-tag in that
regards, must be clear about which case does apply.

Note that, since the last node of a suborder is always defined by the last
node's start-tag, and since that last node must be a leaf to the corresponding
base order (otherwise there would be another node subsequent to it), any scope
can always be said to end with a start-tag. The difficulty with that description
is however that one can not provide a generic definition that can be used to
identify such a node as the last node. That is because any assumption, which
would allow to identify a node as that last node effectively introduces
requirements that can not be relied upon (hint - input errors).

Note that the above is intended to point out that the enter- and exit-events
of a node can be guaranteed to exist in the context of that node. Because of
that, the following will focus on these events since both represent well
defined processing steps that can be relied upon.

<!-- ======================================================================= -->
## trivial vs. non-trivial base orders

Recall that the trivial base order is the only order such that one can state
that no node has another node subsequent to it. Because of that, every scope
defined over a trivial base order is such that it begins and ends with the
start-tag of its defining node. (Obviously including the node itself).

* any scope over a trivial base order begins and ends with a **start-tag**

Note that every other base order is such that the scopes over it begin with
their defining node and end in another node (i.e. a node subsequent to it -
i.e. a descendant in that base order). Consequently, any scope over a
non-trivial base order ends with the end-tag of its last subsequent leaf.

* any scope over a non-trivial base order ends with an **end-tag**

<!-- ======================================================================= -->
## non-trivial base orders

The following will point out which end-tags can be guaranteed to exist in the
context of a scope over a non-trivial base order.

Note that, if the defining node of a scope is reached by an implementation,
then that node is guaranteed to exist. Consequently, definitions can be made
in regards to that defining node. The corresponding end-tag must, for obvious
reasons, be subsequent to the start-tag of that defining node.

(0) The first end-tag that could be used to define the default end of a scope
over a non-trivial suborder is the end-tag of last subsequent descendant leaf
of the scope's defining node. However, since a definition can not rely upon
the existence of such a leaf, and since the same applies to any of the
descendants of the defining node, the end-tag of the defining node is the
very first end-tag a definition can rely upon to exist.

* the end-tag of the defining node

(1) If the defining node is **the doctree's root**, then the one and only
end-tag that can be guaranteed to exist is the root's end-tag. Because of
that, the default scope over a non-trivial base order of the root must end
in the root's end-tag.

* the end-tag of the doctree's root

(2) If the defining node is **a child to the doctree's root**, then its
end-tag and the end-tag of the doctree's root are guaranteed to exist.

* the end-tag of the defining node
* the end-tag of the doctree's root

(3) If the defining node is **a distant descendant to the doctree's root**,
then its end-tag, the end-tag of its parent, and the end-tag of the doctree's
root is guaranteed to exist.

* the end-tag of the defining node
* the end-tag of its parent
* the end-tag of the doctree's root

Note that the defining node's parent may be the doctree's root. Despite that,
and similar to the existence of a child of the defining node, a definition
can not rely upon the existence of any other end-tag.

<!-- ======================================================================= -->
## remarks

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Note that the above considerations are consistent with the amount of base
orders in the linear extension that begins in DTR and ends in DPR. Based on
that, it will be assumed that there simply is no other base order available.

Because of that, and in the context of a tag-based syntax,
**no more than four distinct types of (default) scopes can be used**.
