
<!-- ======================================================================= -->
## pre-sequent (<), sub-sequent (>)

```
s := (.., x, .., e, .., y, ..)
     |<----------|---------->|
        "current" element e
     presequent     subsequent
```

With each sequence comes a notion of "order". That is because when focussing
on an element `e` at a specific index, one can determine all the other elements
(e.g. `x`) that appear before the element. Likewise, one can determine all the
elements (e.g. `y`) that appear after it.

* `(x presequent-to e) := (idx(x) < idx(e))`
* `(y subsequent-to e) := (idx(y) > idx(e))`

Since the elements within a sequence are treated as abstract values, the
**less-than operator (<)** and the **greater-than operator (>)** have no real
semantical meaning since "less than" and "greater than" is in general only
understood in the context of values that can be understood to have some numeric
"weight". However, in the context of "unknown" abstract values both operators
can be understood to be redefined as follows:

* `(a < b) := (a presequent-to b)`
* `(a > b) := (a subsequent-to b)`

Defined as such, presequent-to and subsequent-to can be described as the
**default/generic semantics** of both operators.

<!-- ======================================================================= -->
## next-presequent (<<), next-subsequent (>>)

An element may be described as being next presequent/subsequent to another, if
both elements are next to each other. Conversely, an element may be described
as being loosely presequent/subsequent, if there are one or more other elements
in between.

* `(x >> y), (x next-subsequent-to y) := (idx(x) == idx(y)+1)`
* `(x << y), (x next-presequent-to y) := (idx(x) == idx(y)-1)`

Note that, if both elements are next to each other, then both elements can be
referred to as being **covered by** each other (i.e. covered by a close "buddy"
so to speak).

* `(a covered-by b) := (a << b) or (a >> b)`

Note that, if `(a << b)` is true, then `a` is in general more naturally referred
to as **the next previous element** in regards to `b`. Likewise, `b` can more
naturally be referred to as **the next subsequent element** in regards to `a`.

<!-- ======================================================================= -->
## comparable

Two elements within the same ordered sequence are said to be comparable under
the presequent/subsequent operator (i.e. `<` or `>`) since one can always
determine if one is presequent or subsequent to the other. In contrary to that,
if both elements are not within the same ordered sequence, then both elements
are said to be incomparable with/to each other.

* `(a comparable-to b) := (a < b) or (a > b)`
* `(a incomparable-to b) := not (a comparable-to b)`

The catch - There are no incomparable elements within an ordered sequence.

<!-- ======================================================================= -->
## issues with presequent/subsequent

The issue with these "notions" is however, if the elements within a sequence
are allowed to appear multiple times. Since the descriptions "presequent" and
"subsequent" then allow to derive seemingly conflicting statements.

```
s := (.., e, .., x, .., e, ..)
          |<----------->|
idx(e)=   i             j
```

Given this pattern, and in regards to `e` at index `i`, `e` also appears at
index `j` and therefore "subsequent to itself". Likewise, and in regards to
`e` at index `j`, `e` also appears at index `i` and therefore "presequent to
itself". From looking at the sequence, and while keeping the corresponding
source-index in mind, both of these descriptions do make sense to some extent.

However, if boiled down to the boolean expressions, the context required to
make sense of these is lost since one no longer knows which index is referred
to by one of the two `idx(e)` subexpressions. (note - at this point one needs
to ignore that idx(e) always returns the index of the 1st occurrence).

* `(e presequent-to e) ?=? (idx(e) < idx(e))`
* `(e subsequent-to e) ?=? (idx(e) > idx(e))`

Based on that, and even though both components in the sequence hold the exact
same element `e` (i.e. `e` is identical to itself), one would have to treat
each occurrence of `e` within the sequence differently. For example by
suffixing the element reference with an index-of-occurrence.

* `e1` := the 1st occurrence of `e` in `s`
* `eN` := the n-th occurrence of `e` in `s`
* `(e1 presequent-to e2)` is certainly true.

Similar to that is the unclear relationship between element `e` and element `x`.
That is, `x` appears to be presequent and subsequent to the same element `e`.

* `(x presequent-to e)` since `(idx(x) < idx(e2))`
* `(x subsequent-to e)` since `(idx(x) > idx(e1))`

Suffice to state that the relationships between the elements are inherently
unclear under the presequent/subsequent operators, if multiple occurrences
are allowed.
