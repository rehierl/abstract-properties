
# tree traversal (2)
- forming traces of nodes from an ordered doctree

```
      presequent           subsequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> (ns .. ls)      |  n -|-> s
                       |-> (fc .. lc)   |     |-> (fc .. lc)      |     |-> c
                                        |                         |
                           child nodes  |                         |
```

Since each node in an ordered doctree has no more than two child nodes, two
order-preserving order embeddings can be defined. Both are such that one
branch of a node is appended to the other:

(1) **The pre-order rule** is such that the sequence of former subsequent
siblings `s` is prefixed by a node's sequence of former child nodes `c`.
Note that the pre-order rule does not require an order of execution since
the resulting total node order (i.e. the pre-order trace) will be the same,
regardless of the order in which the pre-order rule is applied.

* `n -> (fc .. lc) -> (ns .. ls)` - in short `(n × c × s)`

(2) **The level-order rule** is such that the sequence of former subsequent
siblings `s` is suffixed by a node's sequence of former child nodes `c`.
Note that the level-order rule does equire an order of execution. That is
because the resulting total node order (i.e. the level-order trace) depends
on the order in which the level-order rule is applied. That is, one must
define a default order of execution: By default, and beginning with the root
of the corresponding tree, the rule must be applied in the order in which the
nodes will be appended to the level-order trace. This order of execution may
loosely be described as "overall in child order".

* `n -> (ns .. ls) -> (fc .. lc)` - in short `(n × s × c)`

Note that both rules effectively describe how to form new sequences of
sbilings, based on a node and two input sequences, by adding an additional
edge in between the last node of one sequence and the first node of the
other. As such, one may describe the embedding of an additional edge as
an **ordering rule**. That may or may not be paired with a particular
**order of execution**.

Note that the **pre-order** and the **level-order** tree traversals are the
only order-preserving algorithms. In addition to that, the pre-order traversal
corresponds with a hierarchy of scopes, whereas the level-order traversal is
overall a sequence of disjoint child orders and thus non-hierarchical.

Note that **in-order** tree traversal algorithms are not in the focus of this
discussion. That is because these visit a node after its first child, which
is why they are not order-preserving. In addition to that, in-order algorithms
will in general visit a node more than once, which is why the corresponding
traces of nodes are no ordered sequences of nodes.
