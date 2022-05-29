
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

Recall that the process of embedding of a child order can be explained with
an order-based point of view in mind. After all, each tree is isomorphic to
a hierarchy of scopes, which is why the ordered document tree is such that
each node has no more than two child nodes, its former first child `fc`
and its former next subsequent sibling `ns`.

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Since the tree's root `p` will be such that it has its former first child
`fs` as its one and only child (i.e. it has no subsequent sibling), one
might assume that **iteratively embedding more child orders** will result
in a linear order (i.e. a trace of nodes) after a finite amount of steps.

Note that each iterative step will reduce the number of nodes with more than
one child by more than one node - i.e. at least the tree's root. After that,
one can imagine the resulting tree to be reduced to those induced subtrees
that cover all of the nodes with more than one child.

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
i.e. **in reversed order**.

<!-- ======================================================================= -->
## remarks

Note that both options will result in a trace that is **order-preserving**.
After all, none of the subsequent child orders will be in conflict with the
document tree's tree order or its child order.

Note that, since the resulting trace will be order-preserving, both options
**can not be used to produce a post-order trace**. After all, a post-order
trace is in conflict with the tree order of the ordered document tree, in
which ancestors appear subsequent to their descendants - i.e. overall not
order-preserving.
