
<!-- ======================================================================= -->
# example: reversed post-order

```
unordered doctree    unordered doctree     ordered doctree
(top-to-bottom)      (left-to-right)       (left-to-right)
===============  =>  ================  =>  ================================
     n0              n0 -|-> n3            n0 -|-> X
 ----------              |-> n2 -> n5          |-> n3 -> n2 -|-> n1 -|-> X
 n3  n2  n1              |-> n1 -> n4                        |-> n5  |-> n4
     --  --
     n5  n4
```

Recall that the root of a tree has no siblings and, because of that, only a
single child in the ordered doctree. Applying the post-order rule to the root
will therefore set the root's child nodes as its subsequent siblings. Because
of that, root `n0` will be ignored by the following considerations.

```
ordered doctree            first n2, then n1             post-order trace
=====================  =>  ========================  =>  ===================
n3 - n2 -|- n1 -|- X       n3 - n5 - n2 - n1 -|- X       (n3,n5,n2,n4,n1,n0)
         |- n5  |- n4                         |- n4
```

If the pre-order rule is first applied to `n2`, then `n5` becomes the next
sibling of `n3`. After that, applying the rule to `n1` will set `n1` as
the next sibling of `n4`.

```
ordered doctree            first n1, then n2             post-order trace
=====================  =>  ========================  =>  ===================
n3 - n2 -|- n1 -|- X       n3 - n2 -|- n4 - n1           (n3,n5,n2,n4,n1,n0)
         |- n5  |- n4               |- n5
```

Since the resulting pre-order traces are the same, regardless to which node
the rule is applied first, these two examples can be understood to suggest
that the pre-order rule does not require a specific order of execution.

Note that the reversed post-order trace corresponds with the default pre-order
trace. That is because both traces are reversed to each other.

* `postR(n3,n5,n2,n4,n1,n0)` is reversed to `preD(n0,n1,n4,n2,n5,n3)`
