
# document traversal

```
DTU                 + CO          = DTO
========================================================================
         p          | embedding a |
         |          | child order | long pattern:
 -----------------  |             | p -> (fs .. ps) -> n -|-> (ns .. ls)
 | .. |  |  | .. |  |             |                       |-> (fc .. lc)
 fs  ps  n  ns  ls  |     =>      |
         |          |             | reduced pattern:      in short:
      -------       |             | n -|-> (ns .. ls)     n -|-> s
      | ... |       | a partial   |    |-> (fc .. lc)        |-> c
      fc   lc       | extension   |
```

This meta-chapter begins to describe the effects of **embedding the child order**
(CO) of a document tree (DT) into the noder order of the unordered document tree
(DTU). The node order which results from that **partial order embedding** will
be referred to as the ordered document tree (DTO). Since the ordered document
tree is still a tree order, but not necessarily also a linear order, even more
node orders can in general be embedded.

Hence, this meta-chapter continues to discuss the tree traversal algorithms in
terms of **one or more additional order embeddings**, each of which results in
a path graph - i.e. a trace of nodes that can be understood to describe the
corresponding tree traversal. Based on that, a tree traversal can be described
in terms of order embeddings - i.e. a linear extension.

For example, the **ordering rule** that is defined by the pre-order rule will
result in the pre-order trace (PRE) of a document tree.

* the pre-order rule - `(n × c × s)`
* the post-order rule - `(c × n × s)`
* the level-order rule - `(n × s × c)`

Note that an ordering rule may or may not require **an order of execution**.
For example, the pre-order rule does not have to be applied to the nodes in
any particular order. In contrary to that, the (default) level-order rule
must be applied "overall in child-order" - i.e. start with the tree's root,
continue with its child nodes in child order, and so on.

Note that the pre-order traversal can be described as an **iterative embedding**
of child orders. In contrary to that, the default level-order traversal can not
be described as such an iterative embedding.
