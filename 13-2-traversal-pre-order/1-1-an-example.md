
<!-- ======================================================================= -->
# an example

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
will therefore set the root's child nodes as its subsequent siblings. Because
of that, root `n0` will be ignored by the following considerations.

```
ordered doctree         first n1, then n2           pre-order trace
==================  =>  ======================  =>  ================
n1 -|-> n2 -|-> n3      n1 -> n4 -> n2 -|-> n3      (n0,n1,n4,n2,n5,n3)
    |-> n4  |-> n5                      |-> n5
```

If the pre-order rule is first applied to `n1`, then `n4` becomes the next
sibling of `n1`. After that, applying the rule to `n2` will set `n5` as
the next sibling of `n2`.

```
ordered doctree         first n2, then n1           pre-order trace
==================  =>  ======================  =>  ================
n1 -|-> n2 -|-> n3      n1 -|-> n2 -> n5 -> n3      (n0,n1,n4,n2,n5,n3)
    |-> n4  |-> n5          |-> n4
```

If the pre-order rule is first applied to `n2`, then `n5` becomes the next
sibling of `n2`. After that, applying the rule to `n1` will set `n4` as the
next sibling of `n1`.

Since the resulting pre-order traces are the same, regardless to which node the
pre-order rule is applied first, these two examples can be understood to suggest
that the pre-order rule does not require a specific order of execution. However,
and since some other example may in general still exist that yields a distinct
traces, one can not (yet) conclude that the resulting trace will always be the
same.
