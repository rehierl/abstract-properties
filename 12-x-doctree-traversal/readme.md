
# document order

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

This chapter begins to describe the effects of **embedding the child order**
(CO) of a document tree (DT) into the noder order of an unordered document tree
(DTU). The node order that results from such **a partial order embedding** will
be referred to as the ordered document tree (DTO). Since the ordered document
tree (DTO) is in general still a tree order, even more node orders can be
embedded into document tree.

This chapter discusses the tree traversal algorithms in terms of an additional
order embedding, each of which results in a path graph - i.e. the trace of
nodes according to the corresponding tree traversal.

The embedding of a node order that is defined by **the pre-order rule** for
example will result in the pre-order trace of a document tree. The node order
that results from embedding the edges defined by the pre-order rule will be
referred to as **the document order**.

* `n -> (fc .. lc) -> (ns .. ls)` - in short `(n × c × s)`
