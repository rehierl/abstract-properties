
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
(CO) of a document tree (DT) into the noder order of its unordered document tree
(DTU). The node order which results from that **partial order embedding** will
be referred to as the ordered document tree (DTO). Since the ordered document
tree is in general still a tree order, even more node orders can be embedded.

Hence, this meta-chapter continues to discuss the tree traversal algorithms
in terms of one or more **additional order embeddings**, each of which results
in a path graph - i.e. the trace of nodes according to the corresponding tree
traversal.

For example, the embedding of the node order that is defined by
**the pre-order rule** will result in the pre-order trace (PRE)
of a document tree.

* `n -> (fc .. lc) -> (ns .. ls)` - in short `(n × c × s)`
