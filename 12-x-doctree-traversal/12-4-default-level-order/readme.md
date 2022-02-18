
# document trees / (default) level-order (LevelD)

This chapter provides a brief discussion of the default level-order rule.

* the (default) level-order rule := `(n × s × c)`

Note that the resulting total node order is order-preserving.

* preserves the tree order
* preserves the child order

Note that the level-order rule does require **an order of execution**. Because
of that, one must define a default order of execution: By default, and beginning
with the root of the corresponding tree, the rule must be applied in the order
in which the nodes will be appended to the level-order trace. This order of
execution may be loosely described as **overall in child order**.