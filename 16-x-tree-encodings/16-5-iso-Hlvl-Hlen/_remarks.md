
```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
-------------------------------------------
               f  g       - lv4
         d  e  e  e     i - lv3
   b  c  c  c  c  c  h  h - lv2
a  a  a  a  a  a  a  a  a - lv1
-------------------------------------------
```

converting the level-based into the length-based encoding
- explain the Hlvl and Hlen abbreviations

<!-- ======================================================================= -->
# (Hlvl -> Hlen)

- higher level -> a child
- same level -> a sibling to the last
- lower level -> a sibling to an ancestor

backwards oriented
- one must reach the next in order to know if the previous node is done

# rooted paths

rooted paths, stack-based implementations
- a stack is consistent with the scope closing order
- last opened, first closed - a consequence of DI-RE
- open/enter a scope => push an item
- close/exit a scope => pop an item
- one usually does not care about the first/root node
- one usually focusses on the last/current node
- one might update the next-to-last/parent node
- in short - rooted paths

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- `#s` tells where to place the next element
- `#s` is the element's node level
