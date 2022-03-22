
- bound to the default pre-order tree traversal

the scope of a node is a substring to the tree's pre-order trace
- where explained?

Note that the **start-tag** of a node corresponds with **the visit of a node**.
That is, the subsequence of all start-tags (i.e. if all of the end-tags are
dropped) corresponds with the tree's pre-order trace.

Note that, since a node is pushed into its start-tag, an **end-tag** does not
correspond with the visit of any node. An end-tag remains to be nothing more
than an **end-marker** of the corresponding scope.

Note that, from an input-based point of view, the tag soup of a document
can be understood to define the document tree's pre-order trace - with the
additional feature that there is an end-marker for the scope of each node.

Note that the pre-order trace of a node strongly corresponds with the
**tag-based syntax**. Because of that, a node can be understood to be
**pushed into its start-tag**, which is why the visit of a node corresponds
with its start-tag. In contrary to that, the end-tag of a node must only
be understood as an end-marker that marks the end of the node's scope.

* `(n × <tag> × c × </tag> × s)` => `(<n> × c × </n> × s)`
