
<!-- ======================================================================= -->
# a visual summary

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

Given the above unordered document tree (DTU), the pre-order traces of the
nodes in it - pre(n) or simply p(n) - can be visualized as follows.

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

Note that all traces are either disjoint ex-or related, which is why no trace
overlaps another, which would be easily visible in the visual representation.
Finally noe that all traces are substrings to the doctree's pre-order trace.

```
Hpre := {
  [a, b, c, d, e, f, g, h, i, j],
  [c, d, e, f, g],   [h, i, j],   [e, f, g],
  [b],   [d],   [f],   [g],   [i],   [j]
}
```

As can be seen, the visual representation can be understood to correspond with
a formal definition (i.e. an actual set of strings of nodes), which satisfies
the requirements of a hierarchy of pre-order traces.

```
P(V,<) where N := { pre(n) | (n in N) }
and (a < b) := (a superstring-of b) for (a,b in V)
```

A partial order over the pre-order traces can easily be defined based on the
superstring-of comparison

```
DTU(N,E) where N := { ce(t) | (t in V) } and E := {
  (a,b),  (a,c),  (a,h),  (c,d),  (c,e),  (h,i),  (h,j), (e,f),  (e,g)
}
```

If each trace is replaced by its very first element, the order relation of the
tree order DTU can be formed just as easily. The transitive reduction of that
order relation will then yield the graph of the unordered doctree DTU(N,E).

The document tree's set of edges then allows to easily determine the child
nodes of each parent. That is because there is an Edge (pEc) between each
parent (p) and any of its child nodes (c).

```
c(p) := { c | (p,c) in E }
c(a) := { b, c, h }
```

With the child set of a parent, one can then form a suborder of the parent's
pre-order trace by restricting it to its child nodes. The result is the
parent's actual child order, expressed as an ordered sequence of child nodes.

```
pre(a) := [a, b, c, d, e, f, g, h, i, j]
co(a)  := [   b, c,             h      ]
```

Based on being able to recreate the child order of each parent, and thus on
being able to recreate the child order of the document tree, the doctree's
child order can be embedded into the node order of the unordered doctree DTU.
Consequently, even the node order of the ordered doctree DTO can be recreated.
