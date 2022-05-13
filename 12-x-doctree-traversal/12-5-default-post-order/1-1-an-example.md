
<!-- ======================================================================= -->
# example: (default) post-order

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
single child in the ordered doctree. Applying the post-order rule to the root
will therefore set the root's child nodes as its next presequent siblings.
Because of that, root `n0` will be ignored by the following considerations.

```
ordered doctree       first n1, then n2        post-order trace
================  =>  ===================  =>  ===================
n1 -|- n2 -|- n3      n4 - n1 - n2 -|- n3      (n4,n1,n5,n2,n3,n0)
    |- n4  |- n5                    |- n5
```

If the post-order rule is first applied to `n1`, then `n1` will be prefixed
by `n4` and then suffixed by `n2`. After that, applying the rule to `n2` will
prefix `n2` by `n5` and then suffix it by `n3`.

```
ordered doctree       first n2, then n1        post-order trace
================  =>  ===================  =>  ===================
n1 -|- n2 -|- n3      n1 -|- n5 - n2 - n3      (n4,n1,n5,n2,n3,n0)
    |- n4  |- n5          |- n4
```

Since the resulting post-order traces are the same, regardless to which node
the rule is applied first, these two examples can be understood to suggest
that the post-order rule does not require a specific order of execution.

Note that the default post-order trace correspond with the reversed pre-order
trace. That is because both traces are reversed to each other.

* `postD(n4,n1,n5,n2,n3,n0)` is reversed to `preR(n0,n3,n2,n5,n1,n4)`
