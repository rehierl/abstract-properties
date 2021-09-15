
<!-- ======================================================================= -->
# restricting the end of a scope

Note that the following definitions and restrictions are in regards to the
definition of default scopes (i.e. **an upper boundary**). That is, future
definitions may provide even further restrictions.

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

In regards to the end of a scope one can state that an implementation must
in general explicitly react to the end of any scope. That is because a scope
would otherwise remain open for associations until the very end of a document.
As such an implementation would exceed the base order of that scope and thus
be in conflict with the scope's definition. Consequently, the definition of
a scope must be such that an implementation has certain well defined points
in its code that can be used to mark any scope as being closed.

* implementations must have the means to react to the end of any scope

Recall that any node in a document tree may in general have any number of child
nodes. In addition to that, no node can be guaranteed to have a certain number
of child nodes. Consequently, the pre-order traversal of a doctree does not
provide the means to reliably define that a scope ends at a certain point in
between a parent's first child and its last child.

No generic (doctree independent) definition can therefore be provided such that
a scope ends by default with some n-th child of a parent. Such restrictions, if
they can be supported by the default definitions, must be provided externally
by dedicated child nodes (e.g. rank-based headings).

* no suborder can (by default) end in between a parent's first and last child
* each suborder either includes all child nodes exor none at all

```
... <node> ... </node> ...
    |1   |2    |3
```

As a matter of consequence, a scope may be such that it ends with a parent and
therefore just before its first child. In addition to that, a scope may be such
that it ends just after a parent's last child, while including all of the nodes
that are descendant to that parent.

* any scope must end with an enter- exor an exit-event
* any scope must **end with a start-tag (1/2) exor an end-tag (3)**

Note that "ends with a start-tag" is by itself ambiguous since each start-tag
corresponds with a node. Because of that, this can mean two things: (1) ends
just before the visit of the corresponding node (i.e. excluding the node),
exor (2) just after the visit of that node (i.e. including the node but still
before its first child). Definitions, which build upon a start-tag in that
regards, must be clear about which case does apply.

Note that, since the last node of a suborder is defined by its start-tag, and
since that last node must be a leaf to the corresponding base order (otherwise
there would be another node subsequent to it), any scope can be said to end
with a start-tag. The difficulty with that statement is however that one can
not provide a generic definition which allows to identify such a last node.
That is because any assumption, which would allow to identify a node as the
last node effectively introduces requirements that can not be relied upon
(hint - input errors).

Note that the above is merely intended to state that these events are guaranteed
to exist. Because of that, the following will focus on these events since both
represent well defined processing steps.

<!-- ======================================================================= -->
## trivial vs. non-trivial base orders

Recall that the trivial base order is the only order such that one can state
that no node has another node subsequent to it. Because of that, every scope
defined over a trivial base order is such that it begins and ends with the
start-tag of its defining node. (Obviously including that node).

* all the scopes over a trivial base order end with a **start-tag**

Note that every other base order is such that the scopes defined over it begin
in their defining node and end in another node (i.e. some node subsequent to
it - i.e. some descendant). Consequently, any scope over a non-trivial order
ends with the end-tag of its last subsequent leaf.

* the scopes over non-trivial base orders all end with an **end-tag**

Note that, by default, the scope over a non-trivial base order must include
all the descendants of a scope's defining node. The end-tag in which such a
scope ends is however not required to be the end-tag of the scope's defining
node.

<!-- ======================================================================= -->
## non-trivial base orders

- some end-tag - must be subsequent to the start-tag of the defining node
- i.e. subsequent in the processing order
- can be the end-tag of a descendant - no guarantee
- can be the end-tag of the defining node - guaranteed
- can be the end-tag of some ancestor - no guarantee
- can be the end-tag of the root - guaranteed
