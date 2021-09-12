
<!-- ======================================================================= -->
# the pre-order doctree traversal

```
//- the default pre-order tree traversal
traverseInPreOrder(node) begin
  //- visit the node and enter its scope
  //- write("<%s %s>", name, attributes)
  visit(node)

  //- recursively visit all child nodes
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end

  //- exit the node's scope - not a visit
  //- write("</%s>", name)
end
```

As was shown in the discussion of the pre-order tree traversal algorithm,
the pree-order traversal can be used to form a trace of nodes, if each node
is appended to a sequence of nodes while it is being visited. Formed this way,
the resulting trace of nodes is an ordered sequence of nodes and as such can
be understood to define **the total pre-order node order**.

Note that no node will be visited while another node is still in the process
of being visted. Because of that, **the visit of a node** must be understood
as **an indivisible atomic operation**.

Since the enter-order of a document traversal coincides with the pre-order
visit-order, one can conclude that **the visit-order** of a pre-order document
traversal is equivalent to the the enter-order of a document traversal.
Because of that, a node is visited during the corresponding enter-event only.

Note that, if the tag soup of a document is broken apart into a sequence of
tags, and if all the end-tags are dropped, then the resulting sequence of
start-tags is equivalent to the pre-order trace of the document tree. That is
because each node can be understood to be pushed into its start-tag, which
is why **a start-tag corresponds with the visit of a node** and can therefore
be understood such that it **defines the absolute position** of a node. In
addition to that, **a start-tag also denotes the start of the node's scope**.

* start-tag <=> visit the node and enter its scope

Note that, since each start-tag can be understood to define a unique node
in the document tree, a document tree can be described as **an ordered tree**
in the sense of "a tree of unique/distinct elements", which must be understood
to be in the sense of "an ordered sequence of distinct elements".

Note that, in contrary to the above, the subsequence of all end-tags reflects
**the exit-order**. That is, an end-tag does not correspond with the visit of
any node. Consequently, **an end-tag only marks the end of a scope**.

* end-tag <=> only exit the node's scope
