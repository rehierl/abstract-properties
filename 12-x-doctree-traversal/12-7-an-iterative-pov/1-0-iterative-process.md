
# document traversal / an iterative process

```
unordered doctree       co(T) partially embedded
=================  ==>  ==============================
        p           |           p
        |           |           |
-----------------   |   ------------------------------
| .. |  |  | .. |   |   | .. |   |
fs  ps  n  ns  ls   |   fs  ps |-n-------------------|
        |           |          | |-fc----| |-ns----| |
     -------        |          | | .. lc | | .. ls | |
     | ... |        |          | |-------| |-------| |
     fc   lc        |          |---------------------|
```

Recall that the process of embedding of a child order can be explained with
an order-based point of view in mind. After all, each tree is isomorphic to
a hierarchy of scopes, which is why the ordered document tree is such that
each node has no more than two child nodes, its former first child `fc` and
its former next subsequent sibling `ns`.

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Since the tree's root `p` will be such that it has its former first child as
its one and only child (i.e. it has no subsequent sibling), one might assume
that **iteratively embedding even more child orders** will yield a linear
order (i.e. a trace of nodes) after a finite amount of iterations.

<!-- ======================================================================= -->
## two options only

```
DTO              1) in-order        2) reversed
=========   =>   ===========   or   ===========
    n                 n                  n
    |                 |                  |
---------         ---------          ---------
|       |         |       |          |       |
fc     ns         fc --> ns          fc <-- ns
```

Since each node in a document tree has no more than two child nodes, there
are only two options available that can be used to define subsequent child
orders: (1) the child order of each node has its former first child as its
first and its former next sibling as its last child (i.e. in-order), or (2)
the child order of each node has its former next sibling as its first and
its former first child as its last child (i.e. in reversed order).

Note that both options will produce a trace that is **overall order-preserving**.
That is because none of the subsequent child orders will be in conflict with
the tree order of the ordered document tree.

Note that, since the resulting trace will be order-preserving, both options
**can not be used to form a post-order trace**. After all, such a trace is
in conflict with the tree order of the ordered document tree - i.e. overall
not order-preserving.

<!-- ======================================================================= -->
## option-1: pre-order

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

Note that, based on this basic example, iteratively applying option-1 to the
ordered document tree **seems to produce the pre-order trace (PRED)** of the
source tree.

<!-- ======================================================================= -->
## option-2: fail

```
step-0           step-1   step-2   step-3   step-4
============   | ====== | ====== | ====== | ======
p              | p      | p      | p      | p
|------>|      | n      | n      | n      | n
n       ns     | |<--|  | ns     | ns     | ns
|-->|   |-->|  | c1  ns | |<--|  | s1     | s1
c1  c2  s1  s2 | c2  s1 | c1  s1 | |<--|  | s2
               |     s2 | c2  s2 | c1  s2 | c1
               |        |        | c2     | c2
```

Note that the trace produced by option-2 (no twist), regardless of whether the
child orders of each intermediate tree is reversed or not, does not produce a
trace that matches the document tree's (default) level-order trace - i.e.
**not the level-order trace**.
