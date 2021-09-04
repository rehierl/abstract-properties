
<!-- ======================================================================= -->
# an algorithm-based point of view

Given the api definitions used by the pre-order algorithm, the level-order
trace of an ordered doctree `t(N,E)` (i.e. nodes `N`, complex edges `E`)
can be formed as follows:

```
traceInLevelOrder(tree) begin
  t = () × root-of(tree)
  for(i = 1 to #N) begin
    t = t × co(t[i])
  end
  return t
end
```

Note that the algorithm is queue-based.

```
traceInLevelOrder(tree) begin
  r = root-of(tree)
  next = queue()
  next.append(r)
  t = ()

  while(next.isEmpty() == false) begin
    //- pop and "visit" the next node
    n = next.pop()

    //- visit node n
    t = t.append(n)

    //- append the child nodes (in order)
    for (co=co(n), i=1; (i<=co.length); i++) begin
      next.append(co[i])
    end
  end

  return t
end
```

Given a tree and its set of complex edges,
its level-order trace will be formed as follows:

```
ordered tree | set of complex | level_trace(t)
t := (N,E)   | edges E(t)     | i: ns
===============================================
 A           | E(t) := {      | 0: (A)
-----------  |  (A, (B,C)),   | 1: (A,B,C)
 B       C   |  (B, (D,E)),   | 2: (A,B,C,D,E)
------       |  (C, ()),      | 3: (A,B,C,D,E)
 D  E        |  (D, ()),      | 4: (A,B,C,D,E)
   ---       |  (E, (F)),     | 5: (A,B,C,D,E,F)
    F        |  (F, ())   }   | 6: (A,B,C,D,E,F)
```

Note that the child order of a node is a sub-string
to the level-order trace of the node and its ancestors.

* e.g. `((B,C) substring-to (A,B,C,D,E,F)` is *true*
