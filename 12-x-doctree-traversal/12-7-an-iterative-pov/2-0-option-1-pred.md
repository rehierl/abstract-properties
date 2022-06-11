
<!-- ======================================================================= -->
# option-1: (fc -> ns)

```
DTO              in-order
=========   =>   =========
    n                n
    |                |
---------        ---------
|       |        |       |
fc     ns        fc --> ns
```

Based on the definition of the additional child orders one might already
assume that the resulting trace can not correspond with the level-order
traversal. After all, this option will push the first child of each node
in between a node and its next subsequent sibling. Because of that, the
child order of a node can in general not be a substring to the final
race - i.e. the nodes can not appear one level at a time - i.e. not in
level-order.

* can not produce a level-order trace

However, one might assume that this option could be used to produce the
document tree's pre-order trace. After all, the first child of each node
will remain next subsequent to its parent.

* might be able to produce the pre-order trace

<!-- ======================================================================= -->
## example-1: simple tree

```
doctree                     trace
step-0    step-1   step-2   step-3
======= | ====== | ====== | ======
p       | p      | p      | p
|       | |      | n      | n    in
|-->|   | n      | c1     | c1   pre-order
n  ns   | |-->|  | |-->|  | c2
|       | c1 ns  | c2 ns  | ns
|-->|   | |      |        |
c1 c2   | c2     |        |
```

Starting off with the unordered document tree (step-0), continuing with
embedding the child order (step-1), and then iteratively embedding even
more child orders in-order (step-2 and step-3) will result in a path graph
that corresponds with **the pre-order trace (PRED)** of the source tree.

Note that the source tree has two child orders with more than one child -
i.e. `co(p) = (n,ns)` and `co(n) = (c1,c2)`. Also, the subsequent child
orders are **left-to-right oriented** (e.g. `(c1,ns)` in step-1), which
is why they can be described as **consistently oriented** with the
document tree's child order.

<!-- ======================================================================= -->
## example-2: more complex

```
step-0        step-1   step-2   step-3
=========== | ====== | ====== | ======
p           | p      | p      | p
|---->|     | n      | n      | n
n     ns    | |-->|  | c1     | c1   in
|-->| |-->| | c1 ns  | |-->|  | c2   pre-order
c1 c2 s1 s2 | c2 s1  | c2 ns  | ns
            |    s2  |    s1  | s1
            |        |    s2  | s2
```

Applying the iterative process to this document tree will also result in the
doument tree's pre-order trace.

<!-- ======================================================================= -->
## example-3: more complex

```
step-0    step-1     step-2
======= | ======== | ======
p       | p        | p
|---->| | n        | n
n s1 s2 | |-->|    | c    in
c c1 c2 | c  s1    | s1   pre-order
        |    |-->| | c1
        |    c1 s2 | s2
        |       c2 | c2
```

Note that this example is only intended to illustrate that the more siblings
and the more child orders there are, the more difficult it tends to be to
visualize the intermediate steps.

<!-- ======================================================================= -->
## example-4: reversed child order

```
step-0        step-x        step-1   step-2   step-3
=========== | =========== | ====== | ====== | ======
p           | p           | p      | p      | p
|<----|     | |---->|     | ns     | ns     | ns
n     ns    | ns    n     | |-->|  | s2     | s2   in reversed
|<--| |<--| | |-->| |-->| | s2  n  | |-->|  | s1   pre-order
c1 c2 s1 s2 | s2 s1 c2 c1 | s1  c2 | s1  n  | n
            |             |     c1 |     c2 | c2
            |             |        |     c1 | c1
```

Note that, if the document tree's child order is reverse before it is embedded,
the iterative process will result in **the reversed pre-order trace (PRER)**.

<!-- ======================================================================= -->
## remarks

Note that **the pre-order trace of the ordered document tree**, including the
trace of each intermediate tree, is equal to the final trace. That is even
the case, if the document tree's child order is first reversed.
