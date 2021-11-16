
<!-- ======================================================================= -->
## ordered sequences

```
A = [0,0,1,1,1,4,3,2,6,7]
B = [9,8,7,6,3,2,1,0,4,5]
C = [0,1,2,3,4,5,6,7,8,9]
X = [3,2], Y = [4,5], Z = [6,7]
```

* A, B and C all are sequences of elements/values.
* X is a subsequence of A and B.
* A and B share the (common) pattern X.
* B and C share pattern Y.
* A and C share pattern Z.
* All sequences are different from one another
  i.e. they differ in elements and/or length.
* No sequence (in `{A,B,C}`) is a subsequence of another sequence.

```
B = [9,8,7,6,3,2,1,0,4,5]
C = [0,1,2,3,4,5,6,7,8,9]
```

* Sequences B and C contain no element more than once.
* B and C can both be said to represent a **serialized set**

<!-- ======================================================================= -->
## sub-sequences

```
set-of-sequences = {
  A = [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ],
  B = [    1, 2, 3, 4, 5, 6          ],
  C = [       2, 3,                  ],
  D = [                5, 6, 7       ],
  E = [                         8, 9 ]
}
```

This set-of-sequences could be visualized using the following
box-based representation:

```
|-A--------------------------------------------|
|    |-B-----------------------|               |
|    |    |-C-----|    |-D----------| |-E----| |
| 0, | 1, | 2, 3, | 4, | 5, 6, | 7, | | 8, 9 | |
|    |    |-------|    |------------| |------| |
|    |-------------------------|               |
|----------------------------------------------|
```

Note that the borders of sequences B and D cross each other.
That is, both sequences overlap each other.

An even more compact,
line-based representation is:

```
0 1 2 3 4 5 6 7 8 9 - ordered set
0 1 2 3 4 5 6 7 8 9 - A
  1 2 3 4 5 6   8 9 - B,E
    2 3   5 6 7     - C,D
```

Note that the order of numbers within each sequence (A to E) corresponds with
the order of numbers within the ordered set of numbers. Furthermore, sequence
A is "identical" to the ordered set. Because of that, the numbers only have to
be specified once by the "root sequence".

Note that the left-to-right order of identifiers (i.e. A to E) to the right
corresponds with the order of sequence definitions (i.e. the lines of `=`
characters): That is, the range of B begins with `1` and ends with `6`.

```
0 1 2 3 4 5 6 7 8 9 - A
  ===========   === - B,E
    ===   =====     - C,D
```

Note that it can still be visually detected whether or not two sequences
(e.g. B and D) overlap each other.

```
0 1 2 3 4 5 6 7 8 9 - A
  ===========   === - B,E
    ===   =====     - C,D
                    - F
```

Obviously, the line-based representation is more compact than the box-based
representation. However, this line-based representation only insufficiently
allows to include empty sequences (e.g. empty line/sequence F). Unfortunately,
and if visualized that way, empty sequences appear out of context. That is,
unlike with non-empty sequences, there is no "visual connection" of an empty
sequence with all the other sequences. Because of that, line-based "images"
will only be used in combination with non-empty sequences.
