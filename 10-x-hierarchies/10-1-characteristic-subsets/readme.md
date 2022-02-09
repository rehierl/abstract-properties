
# hierarchies / characteristic subsets

Since the relationships between the sets in a setup of sets are used to embed
the definitions of the edges of the order relation the setup defines, the open
question that remains is, how the **vertex definitions** are embeddded into a
setup.

In short, the definition of the vertices must be embedded in such a way that
the information can be reliably determined. That is, it must be possible to
reliably determine the vertex each set represents when decoding a setup.

To achieve that, one needs to think of the definition of a vertex as being
provided by certain elements that are embedded into the sets - obviously in
such a way that the relationships between the resulting vertices is maintained
in terms of the relationships between the corresponding sets.

```
       |-oss(s)=s--------------|
       | |-css(s)-| |-iss(s)-| |
A(s) <---| { .. } | | { .. } |---> D(s)
       | |--------| |--------| |
       |-----------------------|
```

Since the definition of the vertex a set represents must be embedded into the
corresponding set, one can think of a set as consisting of two disjoint subsets.
One is a subset `css(s)` that can be thought of as being is restricted to the
vertex definition. The other subset can therefore be described as the inner
subset `iss(s)`, that holds all of those elements which are unrelated to that
purpose. Both subsets combined can be understood to form the corresponding set
`s`, which can also be described as the outer subset `oss(s)`. In other words,
the definition of a vertex is provided by the characteristic subset of a set.

* `css(s) := (s \ iss(s))`

Recall the non-standard definitions of **characteristic subset (CSS)** and
**characteristic element (CE)** in the context of simple sets.

As a matter of consequence, the definition of a setup must be such that the
inner subset `iss(s)` of each set can be uniquely determined. Since the only
available bit of information left in a setup are the sets of elements in it,
the inner subset must be defined in terms of all the other sets that are
subsets to the corresponding set.

* `iss(s) := { x | (x in t), (t in S), (t subset-of s), (t != s) }`

Note that `iss(s)` itself can, but is not required to be an element in the
corresponding setup.

* `(iss(s) in S)` may or may not be true
