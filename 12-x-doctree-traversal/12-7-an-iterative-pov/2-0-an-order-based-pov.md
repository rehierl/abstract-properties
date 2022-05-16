
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

aspect-1
- the child order is maintained
- embedded into the ordered tree
- subsequent orders do not contradict
- edges will only be added in between siblings
- i.e. in between incomparable nodes

aspect-2
- explain why it is in pre-order
- in between any node and its next subsequent
  sibling will be its descendants
