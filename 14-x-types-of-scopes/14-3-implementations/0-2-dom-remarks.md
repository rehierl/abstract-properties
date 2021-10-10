
<!-- ======================================================================= -->
# remarks related to the dom tree

The following will take a look at those orders that are suborders to the DOM
tree structure. These considerations can then be taken into account when having
to decide which base orders to support.

As explained below, the trivial suborder (DTR), the node order of the unordered
doctree (DTU) and the node order of the ordered doctree (DTO) can all be said
to be embedded suborders to the DOM tree. In contrary to that, and since a DOM
node is missing certain properties, the pre-order node order is no suborder to
the DOM tree.

* DTR, DTU, DTO are suborders to the DOM tree
* DPR is no suborder to the DOM tree

Note that, since the DPR order is no suborder to the DOM tree, the DPR order
is of limited use as a base order. Solid reasons must therefore be provided
such that the support of that base order can be justified.

<!-- ======================================================================= -->
## the doctree's child order

Each DOM node is such that it has a list of child nodes embedded into it (i.e.
`Node.childNodes`). Because of that, a DOM tree can be understood such that
the (overall) child order of the document tree is accessible.

<!-- ======================================================================= -->
## the trivial suborder (DTR)

Since the DOM tree has a node for each pair of tags, the trivial base order
is an actual suborder to the DOM tree. Because of that, this node order always
is a viable base order candidate.

<!-- ======================================================================= -->
## the unordered doctree (DTU)

```
         p          | tree-order:
         |          | top-to-bottom oriented
 -----------------  | "ancestor-of"
 | .. |  |  | .. |  |
 fs  ps  n  ns  ls  | child-order:
         |          | left-to-right oriented
      -------       | "presequent-sibling-of"
      | ... |       |
      fc   lc       |
```

A DOM node has a `Node.parentNode` property which can be understood to define
an edge that is oriented from a child to its parent (i.e. against the default
parent-to-child orientation. Despite this inverse orientation, one can assume
that there is an edge in between a child and its parent.

Note that, even though a list of child nodes does not represent a property in
between each child and its parent, the child list of a parent node can also
be said to represent all of the corresponding parent-to-child edges. That is
because, while iterating over a child list, one can in general tell to which
parent node the child list belongs.

One can therefore state that the node order of the unordered doctree
**DTU is a suborder to the DOM tree**.

<!-- ======================================================================= -->
## the ordered doctree (DTO)

```
     presequent           subsequent   | the tree-order of the
     siblings             siblings     | ordered document tree
                                       | in regards to node (n)
p -> (fs .. ps) -> n -|-> (ns .. ls)   |
                      |-> (fc .. lc)   |
                                       |
                          child nodes  |
```

Recall that the ordered doctree is such that its child order is embedded into
it. As such, a node has its former presequent siblings as ancestors in DTO.
Because of that, the parent of a node in DTO is either its former parent in
DTU (in case of a first child) exor its former next presequent sibling. Based
on the `Node.parentNode` and the `Node.previousSibling` properties, one can
therefore state that the parent-to-child edges do exist, which is why one can
always traverse to a node's parent.

```js
parentNodeDTO(node) begin
  if(node.previousSibling !== null) then
    return node.previousSibling
  else
    return node.parentNode
  end
end
```

Similar to the above, a node's former subsequent siblings and their descendants
form one branch of descendants in DTO, which is accessible over the node's
former next subsequent sibling `ns`. The second branch of descendants in DTO
consists of all the former child nodes and their descendants, which is accessible
over the node's former first child `fc`. Because of that, a node in DTO always
has no more than two child nodes: (1) Its former first child `Node.firstChild`
and (2) its former next subsequent sibling `Node.nextSibling`.

One can therefore state that the node order of the ordered doctree
**DTO is a suborder to the DOM tree**.

<!-- ======================================================================= -->
## the document order (DPR)

```
n -> (fc .. lc ..) -> (ns .. ls ..)
```

Recall that the description of "document order" refers to the total pre-order
trace of nodes, which is the document's processing order. That node order is
formed by prefixing a node's sequence of former child nodes `(fc .. lc)` to
its sequence of former subsequent siblings `(ns .. ls)`. Because of that,
there are three possibilities for a node's parent in DPR:

(1) If node `n` has a child in DTU,
then `n` will be the parent of `fc` in DPR.

(2) Otherwise (i.e. no child), if `n` has a next sibling in DTU,
then `n` will be the parent of `ns` in DPR.

(3) Otherwise (i.e. no child and no subsequent sibling), a node's child in
DPR will be the next subsequent sibling of one of its ancestors in DTU. Put
differently, a node's parent in DPR will be the last subsequent descendant
leaf of its next presequent sibling in DTU.

Note that case-1 is covered by the `.parentNode` property, and case-2 by the
`.previousSibling` and/or the `.nextSibling` properties. In contrary to that
a DOM node has no property that covers case-3. That is, there is no means to
directly traverse to the next subsequent sibling of an ancestor or to the last
subsequent descendant of a presequent sibling. A DOM tree does consequently
not always allow to transition from a DPR parent to its child and vice versa.

One can therefore state that the document order
**DPR is NO suborder to the DOM tree**.

Note that, even though it would in general be possible to extend the DOM
specification by properties (i.e. **missing edges**) which allow to directly
traverse the DPR node order, such a "solution" does however come with a caveat:
Such properties must always be updated to maintain "structural" consistency,
which is why such extensions will add additional complexity to implementations
that is in general difficult to justify and maintain.

Note that, despite a possible extension, the issue of being unable to reliably
use a pair of tags to consistently enclose a type-3 scope remains as is.
