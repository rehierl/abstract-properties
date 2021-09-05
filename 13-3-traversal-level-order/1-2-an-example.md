
<!-- ======================================================================= -->
# example: (default) level-order

```
unordered doctree    unordered doctree     ordered doctree
(top-to-bottom)      (left-to-right)       (left-to-right)
===============  =>  ================  =>  ==========================
     n0              n0 -|-> n1 -> n4      n0 -|-> X
 ----------              |-> n2 -> n5          |-> n1 -|-> n2 -|-> n3
 n1  n2  n3              |-> n3                        |-> n4  |-> n5
 --  --
 n4  n5
```

Recall that the root of a tree has no siblings and therefore only a single child
in the ordered doctree. Just like the pre-order rule, applying the level-order
rule to the root will set the root's child nodes as its subsequent siblings.
Because of that, root `n0` will be ignored by the following considereations.

```
ordered tree            first n1, then n2           level-order trace
==================  =>  ======================  =>  ================
n1 -|-> n2 -|-> n3      n1 -> n2 -|-> n3 -> n4      (n0,n1,n2,n3,n4,n5)
    |-> n4  |-> n5                |-> n5
```

If the level-order rule is first applied to `n1`, then `n4` becomes the last
sibling of `n1` and also of `n2` and `n3`. After that, applying the rule to
`n2` will set `n5` as the last sibling of and `n1`, `n2`, `n3` and `n4`.

Note that the node order of this level-order trace reflects the default
level-order trace of a tree. That is, the nodes of a tree appear one node
level at a time and in the order of all child orders.

```
ordered tree            first n2, then n1           level-order trace
==================  =>  ======================  =>  ================
n1 -|-> n2 -|-> n3      n1 -|-> n2 -> n3 -> n5      (n0,n1,n2,n3,n5,n4)
    |-> n4  |-> n5          |-> n4
```

If the level-order rule is first applied to `n2`, then `n5` becomes the last
sibling of `n2` and also of `n1` and `n3`. After that, applying the rule to
`n1` will set `n4` as last sibling of nodes `n1`, `n2`, `n3` and `n5`.

Since both traces are distinct, the result of the level-order rule depends on
the order in which the rule is applied. These examples therefore proof that
an ordered doctree may have several different valid level-order traces.
