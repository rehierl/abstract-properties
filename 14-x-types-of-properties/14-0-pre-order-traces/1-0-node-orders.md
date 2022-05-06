
<!-- ======================================================================= -->
# relevant node orders

```
         p          | tree-order:
         |          | top-to-bottom oriented
 -----------------  | "ancestor-of"
 | .. |  |  | .. |  |
 fs  ps  n  ns  ls  | child-order:
         |          | left-to-right oriented
      -------       | "presequent-sibling-of"
      | ... |       |
      fc   lc       |
```

Recall that the unordered document tree is such that no child order has been
embedded into it. Because of that, the unordered document tree must be treated
like any other node tree - i.e. as a tree that has no child order associated
with it.

```
      presequent           subsequent   | the resulting tree-order
      siblings             siblings     | in regards to node (n)
                                        |
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |
                       |-> (fc .. lc)   |
                                        |
                           child nodes  |
```

Recall that, embedding the document tree's child order into its tree order has
the effect of reducing the amount of child nodes to no more than two. That is,
each node in the ordered document tree has its former next subsequent sibling
and its former first child as its only child nodes.

```
 -> n -> fc .. lc .. -> ns .. ls ..
```

Recall that applying the pre-order rule to the ordered document tree has the
effect of turning its tree order into into the document tree's pre-order trace
that can be visualized as a path graph.
