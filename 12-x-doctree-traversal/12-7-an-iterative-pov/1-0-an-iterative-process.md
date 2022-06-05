
# an iterative process

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

Recall that the process of embedding a child order can be explained with an
order-based point of view in mind. After all, each tree is isomorphic to a
hierarchy of scopes, which is why the ordered document tree is such that
each node has no more than two child nodes (i.e. a binary tree), its former
first child `fc` and its former next subsequent sibling `ns`.

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Since the tree's root (e.g. `p`) has no sibling it will be such that it has
its former first child (e.g. `fs`) as its one and only child. One might thus
assume that **iteratively embedding more child orders** will result in a
linear order (i.e. a trace of nodes) after a finite amount of steps.

Note that, one way to imagine such an iterative process would be to think of
**a zipper** that, while being closed, has a linear prefix (a rooted path)
which ends with the topmost parent that has a child order with two or more
nodes. The iterative process would then extend that rooted path by one or
more nodes with each step, until the resulting order is linear.

<!-- ======================================================================= -->
## only two options

```
DTO              1) in-order        2) reversed
=========   =>   ===========   or   ===========
    n                 n                  n
    |                 |                  |
---------         ---------          ---------
|       |         |       |          |       |
fc     ns         fc --> ns          fc <-- ns
```

Since each node in an ordered document tree has no more than two child
nodes, there are only two options available that can be used to define
subsequent child orders:

Option-1 (fc -> ns) - The child order of each node has the former first
child as a first, and the former next sibling as a second/last child -
i.e. **in-order**.

Option-2 (ns -> fc) - The child order of each node has the former next
sibling as a first, and the former first child a second/last child -
i.e. **reversed order**.

<!-- ======================================================================= -->
## remarks

Note that both options will result in a trace that is **order-preserving**.
After all, none of the additional child orders will be in conflict with the
ordered document tree - i.e. its tree order and its child order.

Note that, since the resulting trace will be order-preserving, both options
**can not be used to produce a post-order trace**. After all, a post-order
trace is in conflict with the tree order since ancestors will be subsequent
to their descendants - i.e. overall not order-preserving.
