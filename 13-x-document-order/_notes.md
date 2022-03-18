
Note that the pre-order trace of a node strongly corresponds with the
**tag-based syntax**. Because of that, a node can be understood to be
**pushed into its start-tag**, which is why the visit of a node corresponds
with its start-tag. In contrary to that, the end-tag of a node must only
be understood as an end-marker that marks the end of the node's scope.

* `(n × <tag> × c × </tag> × s)` => `(<n> × c × </n> × s)`
