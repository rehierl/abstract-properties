
<!-- ======================================================================= -->
# set-like/ordered/linear sequences

```
(ordered) sequences (linear order)
------------------------
components:  c1 c2 c3
             |  |  |
elements:    v1 v2 v3
```

A sequence will be referred to as **a set-like sequence**, if no element in
it appears more than once. That is, the multiplicity of each element in such
a sequence is, like in simple sets of elements, exactly one/1.

* `(#E(s) == #s)` is required to be true
* i.e. `s` has no repeating elements

Defined as such, each element in a set-like sequence can be understood to be
associated with a unique index. Based on that, the index order in an ordered
sequence can be understood to carry over onto the elements within the sequence.
Because of that, a set-like sequence can be understood to define an ordered
set of elements. Based on that, a set-like sequence can also be described as
**an ordered/linear sequence** of elements.

* `(s(i) < s(j)) := (i < j)` for `(i,j in [1,#s])`

Note that the focus of the subsequent discussion will be on paths of nodes
such that no node within these paths appears more than once. Despite that,
the description as "a set-like sequence", or as "an ordered sequence" is
intended to imply that these sequences correspond with total orders of
elements. As such, ordered sequences can be understood to be closely related
to ordered sets of elements. (see - **order theory**).

Note that sub-sequences of ordered sequences are themselves ordered sequences.

<!-- ======================================================================= -->
## pre-sequent (<), sub-sequent (>)

* `s := ( .., x, .., y, ..)`

If element `y` appears after element `x` in the ordered sequence `s`, then `y`
is said to be subsequent to `x`. Conversely, `x` is said to be presequent to
`y` in regards to `s`.

* `(x subsequent-to y) := (idx(s,x) > idx(s,y))` for `(x,y in s)`
* `(x presequent-to y) := (y subsequent-to x)`

Since the elements within a sequence are treated as abstract values, the `<`
operator has no real semantical meaning. That is, the "smaller-than" semantics
that is usually associated with that operator in the context of numeric values
doesn't exactly apply in the context of "unknown" items. Hence, the `<` operator
must be understood to be **redefined as follows**:

* `(a < b) := (a presequent-to b)`
* `(a > b) := (a subsequent-to b)`

Defined as such, presequent-to and subsequent-to can be described as the
**default/generic semantics** of these operators.

Note that an element may be described as being strictly presequent/subsequent
(i.e. <</>>) to another, if both elements are next to each other. Conversely,
an element may be described as being loosely presequent/subsequent, if there
are one or more other elements in between. Furthermore, if both elements are
next to each other, then both elements can be said to be **covered by** each
other.

* `(a << b) := (i == j-1)` if `(s(i) == a) and (s(j) == b)`
* `(a >> b) := (i == j+1)` if `(s(i) == a) and (s(j) == b)`
* `(a covered-by b) := (a << b) or (a >> b)`

Note that, if `(a << b)` is true, then `a` is in general referred to as "the
next previous element" in regards to `b`. Likewise, `b` is in general referred
to as "the next subsequent element" in regards to `a`.

<!-- ======================================================================= -->
## comparable

Two elements within the same ordered sequence are said to be comparable under
the corresponding comparison operator (i.e. < or >) since one can always
determine if one is presequent or subsequent to the other. In contrary to that,
if both elements are not within the same ordered sequence, then both elements
are said to be incomparable with/to each other.

* `(a comparable-to b) := (a < b) or (a > b)`
* `(a incomparable-to b) := not (a comparable-to b)`
