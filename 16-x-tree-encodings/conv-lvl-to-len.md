
<!-- ======================================================================= -->
# (Hlvl -> Hlen)

```
default pre-order (PRE)                              a
-------------------------------------------   ---------------
a  b  c  d  e  f  g  h  i - n, trace           b    c      h
1  2  3  4  5  6  7  8  9 - r, node.idx           -----   ---
x  1  1  3  3  5  5  1  8 - par, parent.idx       d   e    i
1  2  2  3  3  4  4  2  3 - lvl, node.lvl           -----
9  1  5  1  3  1  1  2  1 - len, node.len           f   g
```

converting the level-based into the length-based encoding
- explain the Hlvl and Hlen abbreviations

<!-- ======================================================================= -->

```
default pre-order (PRE)
-------------------------------------------
a  b  c  d  e  f  g  h  i - n, trace
1  2  2  3  3  4  4  2  3 - lvl, node.lvl
-------------------------------------------
               4  4       - level 4
         3  3  3  3     3 - level 3
   2  2  2  2  2  2  2  2 - level 2
1  1  1  1  1  1  1  1  1 - level 1
-------------------------------------------
               f  g       - level 4
         d  e  e  e     i - level 3
   b  c  c  c  c  c  h  h - level 2
a  a  a  a  a  a  a  a  a - level 1
-------------------------------------------
```

- higher level -> a child
- same level -> a sibling to the last
- lower level -> a sibling to an ancestor

<!-- ======================================================================= -->

```js
recode(lvl) begin
  assert(0 < #lvl)
  assert(lvl[1] == 1)
  len=(), rp=(), nc=()
  lvOld = 0

  traverse() begin
    for (i=1 to #lvl) begin
      lvNew = lvl[i]
      assert(lvNew > 0)

      //- initialize
      len.append(0)

      //- the current node is a root
      if (lvNew == 1) begin
        nc[lvNew] = 1
        lvOld = lvNew
        continue
      end

      lvOld = lvNew
    end
  end

  pop(lvNew) begin
    assert(0 < lvNew)
    assert(lvNew <= lvOld+1)
    level = lvOld

    while(lvNew <= level) begin
      idx = rp[level]
      count = nc[level]
      len[idx] = count
      nc[level-1] += count
      level = level - 1
    end

    lvOld = level
  end

  traverse()
  return len
end
```

note - backwards oriented, one must know the next in order to know if the
previous node is done
