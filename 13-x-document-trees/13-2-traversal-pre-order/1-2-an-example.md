
<!-- ======================================================================= -->
# example: pre-order (D)

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

Recall that the root of a tree has no siblings and, because of that, only a
single child in the ordered doctree. Applying the pre-order rule to the root
will therefore set the root's child nodes as its next subsequent siblings.
Because of that, root `n0` will be ignored by the following considerations.

```
ordered doctree       first n1, then n2        pre-order trace
================  =>  ===================  =>  ===================
n1 -|- n2 -|- n3      n1 - n4 - n2 -|- n3      (n0,n1,n4,n2,n5,n3)
    |- n4  |- n5                    |- n5
```

If the pre-order rule is first applied to `n1`, then `n4` becomes the next
sibling of `n1`. After that, applying the rule to `n2` will turn `n5` into
the next sibling of `n2`.

```
ordered doctree       first n2, then n1        pre-order trace
================  =>  ===================  =>  ===================
n1 -|- n2 -|- n3      n1 -|- n2 - n5 - n3      (n0,n1,n4,n2,n5,n3)
    |- n4  |- n5          |- n4
```

Since the resulting pre-order traces are the same, regardless to which node
the rule is applied first, these two examples can be understood to suggest
that the pre-order rule does not require a specific order of execution.

Note that the default pre-order trace corresponds with the reversed post-order
trace such that both traces are reversed to each other.

* `preD(n0,n1,n4,n2,n5,n3)` is reversed to `postR(n3,n5,n2,n4,n1,n0)`
