
<!-- ======================================================================= -->
## pre-sequent (<), sub-sequent (>)

```
s := (.., x, .., e, .., y, ..)
     |<----------|---------->|
        "current" element e
      presequent | subsequent
```

With each sequence a notion of "order" is associated. That is because when
focussing on an element `e` at a specific index, one can determine all the
other elements that appear before (e.g. `x`) or after (e.g. `y`) the given
element.

* `(x presequent-to e) := (idx(x) < idx(e))`
* `(y subsequent-to e) := (idx(y) > idx(e))`

Since the elements within a sequence are treated as abstract values, the
**less-than operator (<)** and the **greater-than operator (>)** have no real
semantical meaning since "less than" and "greater than" is in general only
understood in the context of values that can be said to have some numeric
"weight". However, in the context of "unknown" abstract values both operators
can be understood to be defined as follows:

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
## sequent, in-sequent

Two elements within a sequence can be described as being **sequent** to each
other. That is because, based on the underlying **index order**, one can
always determine if one element is presequent or subsequent to the other.

* `(a sequent-to b) := (a presequent-to b) or (a subsequent-to b)`

Based on that, one can describe two elements of a sequence as being
**in-sequent** to each other, if both are not sequent to each other.

* `(a insequent-to b) := not (a sequent-to b)`

Note that two elements, which are not elements of the same sequence, are
insequent to each other since one can not determine if they are sequent
to each other. Based on that, one can describe two such elements as being
"not in sequence". Consequently, "sequent" allows to tell if two elements
are **in sequence**.

Note that two elements, which are insequent to each other, can also be said
as being **in-comparable** with each other, which is an order-based term
(see - order theory). Hence, "sequent" and "in sequence" can be understood
as being synonymous to **comparable**.

Note that two elements within the same sequence are always "in sequence".
That is, one can always tell which element is presequent to the other. In
contrary to that, partial orders may contain element that are incomparable
with each other (thus the description as "partial").

<!-- ======================================================================= -->
## issues with presequent/subsequent

The issue with these "notions" is however, if the elements within a sequence
are allowed to appear more than once. Since the descriptions "presequent" and
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
each occurrence of `e` within the sequence differently - e.g. as distinct
instances of the same element - e.g. by suffixing the element reference with
an index-of-occurrence.

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
