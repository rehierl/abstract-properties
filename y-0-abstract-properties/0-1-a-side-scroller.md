
<!-- ======================================================================= -->
# a side scroller (game)

(N)arrator: Imagine a side scroller with a flat world such that it has width
and height, but no depth. The width is split up into cells of uniform size
`w`. Also imagine that the protagonist `P` can only hop from his current
cell to the next subsequent cell.

```
(height)
lY |      |-----------------|
   |      | (P)rotagonist?  |
   |      | Hey, that's me! |
   |     /| Hi there!       |
   |    / |-----------------|
   |   /
   | ¤ --->| (foward only, one cell at a time)
l1 |====|===(ground level)==|===|=====|=== (width)
   | c1 - c2 - c3 - c4 - c5 - c6 - c7 - .. cX
```

Now imagine that the world isn't just flat. Instead, it is layered. With each
next cell, the current height will increase by one layer at a time. Let's say
that all the layers are of equal height `h`. As such, the surface of the world
can be broken apart into cubicles of equal size `(w*h)`, each of which can be
identified by the current cell `ci` and the current ground level `lj`. The
latter of which is at height `lj -> h*j`.

```
(height)
   |  Uff, you want me to   (cursor)
l6 |  climb all of that,      =|===|
   |  don't you? ..      ======|===|
l4 |   /            ===========|===|
   |           ================|===|
l2 | ¤    =====================|===|
l1 |===========================|===| (width)
   | c1 - c2 - c3 - c4 - c5 - c6 ->|
```

Right now, the protagonist can be said to stand on top of cubicle `(c1,l1)`.
Based on that, the protagonist can be said to have a current height of `l1`.

Finally, assume that there is gravity such that, when the protagonist hops
onto the next subsequent cell, he will always land on the topmost layer on
top of the next subsequent cell, and not vanish into the space above it.

Note that the protagonist is essentially (ab)used as a pointer/cursor.