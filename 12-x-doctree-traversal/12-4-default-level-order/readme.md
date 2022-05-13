
# document traversal / (default) level-order (LevelD)

This chapter provides a brief discussion of the (default) level-order rule.

* the (default) level-order rule := `(n × s × c)`

Note that the resulting node order is (overall) order-preserving.

* it preserves the tree order
* it preserves the child order

Note that the level-order rule **requires an order of execution**:

By default, and beginning with the root of a tree, the rule must be applied
in the order in which the nodes will be appended to the level-order trace.
This order of execution may be described as **(overall) in child order**.

Note that, since an order of execution is required, the level-order rule
can not be understood to be well-defined.
