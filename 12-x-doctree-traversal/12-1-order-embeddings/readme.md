
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
order-preserving order embeddings can be defined such that one branch of a
node is appended to the other:

(1) **The pre-order rule** is such that the sequence of former subsequent
siblings `s` of some node `n` is prefixed by its sequence of former child
nodes `c`.

* `n -> (fc .. lc) -> (ns .. ls)` - in short `(n × c × s)`

(2) **The level-order rule** is such that the sequence of former subsequent
siblings `s` of some node `n` is suffixed by its sequence of former child
nodes `c`.

* `n -> (ns .. ls) -> (fc .. lc)` - in short `(n × s × c)`

(3) **The post-order rule** is such that a sequence of former child nodes
`c` is pushed in front of some node `n`. Since the embedded edges are in
conflict with the tree order, this order embedding is not order-preserving.

* `(fc .. lc) -> n -> (ns .. ls)` - in short `(c × n × s)`

<!-- ======================================================================= -->
## remarks

Note that pre-order and the level-order rules both effectively describe how
to form new sequences of sbilings, based on a node and two input sequences,
by adding only one additional edge in between the last node of one sequence
and the first node of the other. As such, one may describe the embedding of
an additional edge as an **ordering rule** which may or may not require an
**order of execution**.

Note that the **pre-order** and the **level-order** tree traversals are the
only order-preserving algorithms. In addition to that, the pre-order traversal
corresponds with a hierarchy of scopes, whereas the level-order traversal is
overall a sequence of disjoint child orders and therefore not hierarchical.

Note that an **in-order** tree traversal is not in the focus of this discussion.
That is because such a traversal is not order-preserving since it will visit a
node after its first child.
