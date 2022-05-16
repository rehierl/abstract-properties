
<!-- ======================================================================= -->
# option 1: (fc -> ns)

```
DTO              1) in-order
=========   =>   ===========
    n                 n
    |                 |
---------         ---------
|       |         |       |
fc     ns         fc --> ns
```

Based on the definition of the additional child orders of **option 1** one
might already assume that the iterative steps will maintain the tree order
of the document tree and also its child order. After all, the additional
child orders will not be in conflict with any of these orders.

* will be overall order-preserving

However, one might also assume that the resulting trace can not correspond
with the level-order traversal. That is because this option will push the
first child of each node in between the node and its next subsequent sibling,
which is why the child order of the node's parent can not be a substring to
the resulting trace of nodes.

* can not correspond with the level-order traversal.

Based on the above, one might assume that this child order might allow an
iterative definition of the pre-order traversal. After all, the first child
of each node will remain next subsequent to its parent.

* might correspond with the pre-order traversal

Note that, as can be seen below, this option **does seem to allow** to
iteratively produce the pre-order trace of a document tree.

<!-- ======================================================================= -->
## example-1: basic tree

```
step-0   step-1   step-2   step-3   reduced
====== | ====== | ====== | ====== | =======
p      | p      | p      | p      | p
|      | |      | |      | |      | n
|--->| | n      | n      | n      | c1
n   ns | |-->|  | |      | |      | c2
|      | c1  ns | c1     | c1     | ns
|--->| | |      | |-->|  | |      |
c1  c2 | c2     | c2  ns | c2     |
       |        |        | |      |
       |        |        | ns     |
```

Starting off with the unordered document tree (step-0), embedding the child
order into its tree order (step-0/1), and then iteratively embedding even
more child orders in-order (step-1/2 and step-2/3) will produce a path graph
that corresponds with **the pre-order trace (PRED)** of the source tree.

Note that the source tree has two parent nodes `p` and `n`, and child orders
`co(p) = (n,ns)` and `co(n) = (c1,c2)`. Also note that the subsequent child
orders in this option are **left-to-right oriented** - e.g. `(c1,ns)` in
step-1.

<!-- ======================================================================= -->
## example-2: more complex

```
step-0           step-1   step-2   step-3
============   | ====== | ====== | ======
p              | p      | p      | p
|------>|      | n      | n      | n
n       ns     | |-->|  | c1     | c1
|-->|   |-->|  | c1  ns | |-->|  | c2
c1  c2  s1  s2 | c2  s1 | c2  ns | ns
               |     s2 |     s1 | s1
               |        |     s2 | s2
```

Applying the iterative process to this slightly more complex document tree
will also result in the pre-order trace of the source tree.

<!-- ======================================================================= -->
## example-3: more complex

```
step-0      step-1     step-2
========= | ======== | ======
p         | p        | p
|------>| | n        | n
n  s1  s2 | |-->|    | c
c  c1  c2 | c  s1    | s1
          |    |-->| | c1
          |    c1 s2 | s2
          |       c2 | c2
```

Note that this example is merely intended to illustrate that the more
siblings and the more child orders there are, the intermediate steps
tend to be difficult to visualize.

<!-- ======================================================================= -->
## example-4: reversed, in-order

```
step-0           step-x           step-1   step-2   step-3
============   | ============== | ====== | ====== | ======
p              | p              | p      | p      | p
|<------|      | |------>|      | ns     | ns     | ns
n       ns     | ns      n      | |-->|  | s2     | s2
|<--|   |<--|  | |-->|   |-->|  | s2  n  | |-->|  | s1
c1  c2  s1  s2 | s2  s1  c2  c1 | s1  c2 | s1  n  | n
               |                |     c1 |     c2 | c2
               |                |        |     c1 | c1
```

The iterative process will, if the document tree's reversed child order is
embedded, result in **the reversed pre-order trace (PRER)** of the source tree.

<!-- ======================================================================= -->
## remarks

Note that **the pre-order trace of each tree**, including the trace of each
intermediate tree, is equal to the pre-order trace of the ordered document
tree. That is also the case, if the document tree's child order is reversed
beforehand.
