
<!-- ======================================================================= -->
# an algorithm-based point of view

Given the api definitions below, the pre-order trace of a document tree
`t(N,E)` (i.e. nodes `N`, complex edges `E`) can be formed as follows:

```js
traceInPreOrder(tree) {
  t = () × root(tree);
  for(i = 1 to #N) {
    t = prefix(t,i) × co(t[i]) × suffix(t,i+1);
  }
  return t;
}
```

A less mathematical recursive implementation could be as follows.

```js
traceInPreOrder(tree) {
  t = ();

  visitInPreOrder(node) {
    //- visit the node and enter its scope
    t.append(node);

    //- recursively visit all child nodes
    for(child in node.childNodes) {
      visitInPreOrder(child);
    }

    //- exit the node's scope
  }

  r = root(tree);
  visitInPreOrder(r);
  return t;
}
```

Note that the algorithm is inherently stack-based.

```js
traceInPreOrder(tree) {
  r = root(tree);
  next = stack();
  next.push(r);
  t = ();

  while (next.isEmpty() == false) {
    //- visit the node and enter its scope
    n = next.pop();
    t = t.append(n);

    //- push the child nodes - in reversed order
    for (co=co(n), i=co.length; (i>=1); i--) {
      next.push(co[i]);
    }

    //- exit the node's scope
  }

  return t;
}
```

Given a tree and its set of complex edges,
its pre-order trace will be formed as follows:

```
document tree | set of complex | pre_trace(t)
t := (N,E)    | edges E(t)     | i: ns
================================================
 A            | E(t) := {      | 0: (A)
-----------   |  (A, (B,C)),   | 1: (A,B,C)
 B       C    |  (B, (D,E)),   | 2: (A,B,D,E,C)
------        |  (C, ()),      | 3: (A,B,D,E,C)
 D  E         |  (D, ()),      | 4: (A,B,D,E,F,C)
   ---        |  (E, (F)),     | 5: (A,B,D,E,F,C)
    F         |  (F, ())   }   | 6: (A,B,D,E,F,C)
```

Note that the child order of a node is a sub-sequence, but in general
not a sub-string to the pre-order trace of an ancestor.

* e.g. `(B,C)` is no substring to `(A,B,D,E,F,C))`

<!-- ======================================================================= -->
## api definitions

The set of complex edges `E` allows to return the child order of a node:

* `co(n) := co` for `((n,co) in E)` where `(n in N)` and `(co in N*)`

Also, the following string-based operations are assumed to be available:

* string concatenation (×) is straight forward, if linked lists are used
* `substr(s,x,y) := t[x..y]` - i.e. from `x` up to and including `y`
* i.e. `substr(s,x,y) = ()` if `(x,y !in [1,#s])` or `(x > y)`
* `prefix(s,i) := substr(s,1,i)` and `suffix(s,i) := substr(s,i,#s)`
* e.g. `prefix((1,2),1) = (1)`, `suffix((1,2),2) = (2)`

The substring of a trace can be formed by removing a prefix (i.e. `t[1..i-1]`)
and/or a suffix (i.e. `t[j+1..#t]`). That is, `(s substring-of t)` is true, if
`i` and `j` exist in `[1,#t]` such that `(t == (t[1..i-1] × s × t[j+1..#t]))`
is true.

Recall that a sub-sequence is formed by removing any number of nodes at any
index. That is, the term "sub-sequence" only requires to maintain the order
between the remaining nodes. In contrary to that, the term "sub-string" in
general also requires to keep the next neighbor of a node.
