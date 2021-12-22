
<!-- ======================================================================= -->
# the (default) level-order tree traversal

```js
//- the default level-order traversal
traverseInLevelOrder(root) begin
  queue = new Queue()
  queue.enqueue(root)

  while (not queue.isEmpty) begin
    node = queue.dequeue()
    visit(node)

    for (child in node.childNodes) begin
      queue.enqueue(child)
    end
  end
end
```

Note that the level-order trace begins with the tree's root, continues with the
root's child nodes, followed by the child nodes of these child nodes, and so on.
As such, the (default) level-order trace contains the nodes in tree order (i.e.
ancestors before descendants) and also in child order (if a child order does
exist). Because of that, the level-order trace is **order-preserving**.

```
      presequent           subsequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> (ns .. ls)      |  n -|-> s
                       |-> (fc .. lc)   |     |-> (fc .. lc)      |     |-> c
                                        |                         |
                           child nodes  |                         |
```

Based on the above algorithm, the level-order rule requires to first embed a
child order (even if only temporary), and then to append the sequence of child
nodes `c(n)` to the sequence of subsequent siblings `s(n)`.

```
n -|-> (ns .. ls)     =>     -> n × (ns .. ls) × (fc .. lc)
   |-> (fc .. lc)            -> (n × s × c)
```

* the (default) level-order rule := `(n × s × c)`

Note that the level-order tree traversal is included as a dual counterpart to
the pre-order rule. However, even though it is order-preserving, it is not in
the focus of this discussion. That is because it does not keep a node and its
descendants in close proximity. Because of that, it does not contain a hierarchy
of substrings.

<!-- ======================================================================= -->
## order of execution

As pointed out above, the (default) level-order trace is **order preserving**
since it is effectively a sequence of concatenated child orders. However,
and since the child order of a node will be appended to the end of the node's
current sequence of subsequent siblings, the order in which the level-order
rule is applied, is relevant. That is because different orders of execution
result in different sequences of child orders and, because of that, in distinct
level-order traces. Consequently, a default order of execution must be defined.

Note that the child orders on a node level may be ordered in random order
without producing a conflict with tree's node order and even without producing
a conflict with the tree's child order. After all, the child orders will be
appended as whole units. Becuase of that, the level-order trace of a tree can
be described as **a sequence of child orders**.

Note that this seems to suggest that the level-order rule is **incomplete**
to some extent. That is, the rule does by itself not turn all the nodes of an
ordered doctree into comparable nodes. After all, incomparable nodes can be
ordered arbitrarily without contradiction.

**An open issue** - What exactly does the level-order rule not cover? The
question is therefore which means a doctree does provide that can be used
for a more generic definition of the order of execution?

**The default order of execution** is as follows:

The level-order rule must first be applied to the tree's root, which will
append the root's child order as the next child order to be processed. After
that, the level-order rule must be applied to the next child order, the first
of which consists of the child nodes of the tree's root, in the order as
specified by the corresponding child order.

Note that, defined as such, the order of execution can be described as being
defined **in order of appearance of the nodes in each child order**. Because
of that, the default order of execution builds upon the total order of each
child order which is why a tree's child order can be said to carry over to
the order of child orders in its level-order trace.

Note that, due to this default order of execution, the level-order rule
**can not be applied concurrently**. The question is therefore, if there
could be an order of exectuion which whould allow concurrency (e.g. by
dropping the requirement of a well defined order of child orders).
