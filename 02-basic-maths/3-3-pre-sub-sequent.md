
<!-- ======================================================================= -->
## pre-sequent (<), sub-sequent (>)

```
s := (.., x, .., e, .., y, ..)
     |<----------|---------->|
        "current" element e
     presequent     subsequent
```

With each sequence comes a notion of "sequence", a notion of "order". That is
because when focussing on an element `e` at a specific index, one can determine
all the other elements (e.g. `x`) that appear before element `e`. Likewise, one
can determine all the elements (e.g. `y`) that appear after element `e`.

* `(x presequent-to e) := (idx(x) < idx(e))`
* `(y subsequent-to e) := (idx(y) > idx(e))`

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
itself". From looking at the given sequence, and while keeping the correspoing
source-index in mind, both of these descriptions do make sense.

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

<!-- ======================================================================= -->
## reduce

```
reduce(s) begin
   t = ()
   for c in s begin
     if (c.value in E(s)) then
       //- ignore
     else
       t.append(c.value)
     end if
   end
   return t
end
```

Each sequence can be reduced such that only the very first occurrence of each
element is retained. That is, every other occurence of an element is dropped.

* `s := (e1, e2, e3, e2, e1)`
* `t := reduce(s) = (e1, e2, e3)`
* `(#t == #E(s))` is true

Note that, from a less strict perspective, the reduce() operation can still
be understood to return a subsequence `t` to the source sequence `s`.

With this operation in mind, one can detect potential problems by simply
comparing the length values of the source sequence with the reduced sequence.

* there is a potential issues if `(#reduce(s) < #s)` turns out to be true
