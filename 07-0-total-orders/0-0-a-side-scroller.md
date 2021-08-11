
<!-- ======================================================================= -->
# a side scrolling game

```
(height)
lY |      |-----------------|
   |      | (P)rotatonist?  |
   |      | Hey, that's me! |
   |     /| Hi there!       |
   |    / |-----------------|
   |   /
   | ¤ --->| (foward only, one cell at a time)
l1 |====|===(ground level)==|===|=====|=== (width)
   | c1 - c2 - c3 - c4 - c5 - c6 - c7 - .. cX
```

(N)arrator: Imagine a side scroller (game) with a flat world such that it has
width and height, but no depth. The width is split up into cells of uniform
size `w`. Also imagine, that the protagonist `P` can only hop from the cell he
is currently in, onto the next cell that is subsequent to the protagonist's
current cell.

```
(height)
   |  Uff, you want me to
l6 |  climb all of that,      ====|
   |  don't you? ..      =========|
l3 |   /            ==============|
   |           ===================|
l2 | ¤    ========================|
l1 |==============================|
   | c1 - c2 - c3 - c4 - c5 - c6 >|
```

Now imagine that the world is layered. With each next cell, the current height
can increase by no more than one layer per cell. Let's say that all the layers
are of equal height `h`. As such, the world can be broken apart into cubicles
of equal size `(w*h)`, each of which can be identified by the current cell `ci`
and the current ground level `lj`. The latter of which is at height `lj -> j*h`.

Right now, the protagonist can be said to stand on top of cell `(c1,l1)`.
Based on that, the protagonist can be said to have a current height of `l1`.

Assume that there is gravity such that, when the protagonist hops onto the next
cell, he will always land on the topmost layer over that next cell, and not
vanish into space above it.
