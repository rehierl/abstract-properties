
<!-- ======================================================================= -->
# a visual summary

Given the following unordered document tree (DTU), ...

```
      a
      |
-------------
|  |        |
b  c        h
   |        |
 -----    -----
 |   |    |   |
 d   e    i   j
   -----
   |   |
   f   g
```

... the pre-order traces of its nodes (i.e. `pre(n)`, in short `p(n)`)
can be visualized as follows.

Note that the nodes are ordered alphabetically in pre-order.

```
n1  n2  n3  n4  n5  n6  n7  n8  n9  n10
 a   b   c   d   e   f   g   h   i   j
 a=====================================  | p(a)
     b=  c=================  h=========  | p(b), p(c), p(h)
             d=  e=========      i=  j=  | p(d), p(e), p(i), p(j)
                     f=  g=              | p(f), p(g)
```

As discussed before, each line corresponds with a subset of nodes. And since
the pre-order trace of a document tree is an ordered sequence of nodes, each
line can be understood to define an induced substring to the doctree's trace
of nodes.

Note that all traces are either disjoint ex-or related (i.e. **DI-RE**),
which is why no trace overlaps another, which would be easily noticeable in
the above visual representation.

As can be seen, the visual representation can be understood to correspond with
a formal definition (i.e. an actual set of strings of nodes), which as a whole
satisfies the requirements of a hierarchy of pre-order traces.

```
Hpre := {
  [a, b, c, d, e, f, g, h, i, j],
  [b], [c, d, e, f, g],   [h, i, j],
  [d], [e, f, g], [i], [j],
  [f], [g]
}
```

A partial order over these traces can thus be defined based on the
**superstring-of** comparison operator.

```
P(V,<) where N := { pre(n) | (n in N) }
and (a < b) := (a superstring-of b) for (a,b in V)
```

If each trace is replaced by its very first element (i.e. its CE), the order
relation of the tree order DTU can be formed just as easily. The transitive
reduction of that order relation will then yield the graph of the unordered
doctree DTU(N,E).

```
DTU(N,E) where N := { ce(t) | (t in V) } and E := {
  (a,b),  (a,c),  (a,h),  (c,d),  (c,e),  (h,i),  (h,j), (e,f),  (e,g)
}
```

The document tree's set of edges allows to determine the child nodes of each
parent. That is because there is an Edge (pEc) between a parent (p) and all
of its child nodes (c).

```
c(p) := { c | ( (p,c) in E ) }
e.g. c(a) := { b, c, h }
```

With the child set of a parent, one can form a suborder of the parent's trace
by restricting it to its set of child nodes. The result is the parent's child
order, expressed as an ordered sequence of child nodes.

```
pre(a) := [a, b, c, d, e, f, g, h, i, j]
co(a)  := [   b, c,             h      ]
```

Based on being able to recreate the child order of each parent, and thus on
being able to recreate the child order of the document tree, the doctree's
child order can be embedded into the node order of the unordered doctree DTU,
which will result in the ordered doctree DTO.
