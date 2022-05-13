
# document traversal / order embeddings

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

Further order embeddings can be defined. These will however be in conflict
with the overall node order. That is, the resulting node order will no longer
be order-preserving the tree order and/or the child order.

**The post-order rule** is such that each node `n` is prefixed by its sequence
of former child nodes `c`. Since the embedded edges are in conflict with the
tree order, this order embedding is overall not order-preserving.

* `(fc .. lc) -> n -> (ns .. ls)` - in short `(c × n × s)`

Note that, based on the tree order, one can state that "a node is presequent
to its former first child" (i.e. `(n -> fc)`). In contrary to that, the
post-order rule can be understood to state that "a former first child is
presequent to its parent" (i.e. `(fc -> n)`). Obviously, both statements can
not be true at the same time, which is why the post-order rule can be said
to be in conflict with the document tree's node order.

* `(fc -> n)` is in conflict with `(n -> fc)`

<!-- ======================================================================= -->
## remarks

Note that, in a different context, both expressions may be allowed to be true
at the same time, which is then understood to state that both nodes involved
must be treated as being equivalent. However, such circumstances are not
allowed in the context of partial orders such as a tree order. After all,
a partial order is not allowed to have any symmetric edges (i.e.
**neither loops nor cycles**).

Note that the pre-order and the level-order rules can both be understood to
define how to form new sequences of sbilings, based on a node and two input
sequences, by embedding one additional edge in between the last node of one
sequence and the first node of the other. Based on that, one can describe
the embedding of an additional edge as an **ordering rule** which may or
may not require an **order of execution**.

Note that the ordering rules (in combination with an order of execution),
will result in a path graph that can be described as **a trace of nodes**.
Because of that, these rules can be understood to cover the underlying formal
aspects of the corresponding **tree traversal** algorithms. Hence the names
of the rules discussed in this chapter.

Note that the pre-order and the level-order tree traversals are the only
**order-preserving** algorithms in the context of this discussion. In
addition to that, the pre-order traversal corresponds with a hierarchy
of scopes, whereas the level-order trace is overall a sequence of disjoint
child orders and therefore not hierarchical.

Note that an **in-order** tree traversal will not be discussed here. That
is because such a traversal will in general visit each node more than once.
