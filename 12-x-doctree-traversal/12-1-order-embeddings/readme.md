
# document trees / order embeddings

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
order-preserving order embeddings can be defined such that one branch of each
node is appended to the other:

**The pre-order rule** is such that the sequence of former subsequent siblings
`s` of some node `n` is prefixed by its sequence of former child nodes `c`.

* `n -> (fc .. lc) -> (ns .. ls)` - in short `(n × c × s)`

**The level-order rule** is such that the sequence of former subsequent siblings
`s` of some node `n` is suffixed by its sequence of former child nodes `c`.

* `n -> (ns .. ls) -> (fc .. lc)` - in short `(n × s × c)`

Further order embeddings can be defined, which will however be in conflict with
the overall node order (i.e. the tree order and/or the child order).

**The post-order rule** is such that each sequence of former child nodes `c`
is pushed in front of node `n`. Since the embedded edges are in conflict with
the tree order, this order embedding is overall not order-preserving.

* `(fc .. lc) -> n -> (ns .. ls)` - in short `(c × n × s)`

Note that based on the tree order one can state that "n is presequent to fc".
In contrary to that, the post-order rule can be understood to state that "fc
is presequent to n". Strictly speaking, both statements can not be true at the
same time, which is why the post-order rule can be said to be in conflict with
the document tree's node order.

<!-- ======================================================================= -->
## remarks

Note that the pre-order and the level-order rules can both be understood to
define how to form new sequences of sbilings, based on a node and two input
sequences, by embedding one additional edge in between the last node of one
sequence and the first node of the other. Based on that, one may describe
the embedding of an additional edge as an **ordering rule** which may or
may not require an **order of execution**.

Note that the ordering rules (in combination with an order of execution)
discussed here, will result in a path graph that can be described as
**a trace of nodes**. Because of that, these rules can be understood to
describe the underlying formal aspects of the **tree traversal** algorithms.
Hence the names of the rules discussed in this chapter.

Note that the pre-order and the level-order tree traversals are the only
**order-preserving** algorithms in the context of this discussion. In
addition to that, the pre-order traversal corresponds with a hierarchy of
scopes, whereas the level-order traversal is overall a sequence of disjoint
child orders and therefore not hierarchical.

Note that an **in-order** tree traversal will not be discussed here. That is
because such a traversal will in general visit each node more than once.
