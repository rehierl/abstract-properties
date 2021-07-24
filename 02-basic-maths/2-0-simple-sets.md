
# (simple) sets of elements

```
(simple) sets (no order)
------------------------
components:  c1 c3 c2
             |  |  |
elements:    v1 v2 v3
```

A simple set is a specialized (i.e. has further characteristics/restrictions)
multiset such that each element in it has a multiplicity of 1. That is, each
component within a simple set holds a unique values.

* `s := { 1, 2, "abc" }`
* `(#(s,v) == 1)` must be true for any `(v in s)`
* `(#E(s) == #(s))` must be true for any simple set `s`

Note that there is a **1:1 relationship** between the components of a simple
set and the elements within that set of elements. Because of that, any component
can be identified by the corresponding element. Hence, labels are of not much
use in the context of simple sets.

Note that there is still no order of any kind defined based upon the elements
a simple set holds. That is, there is no 1st, no last and no n-th element.
Hence,

Simple sets are in general defined using **the set builder notation**. That is,
a boolean expression is specified which allows to uniquely identify all the
elements within the to-be-defined set.

* `s := { vi | (vi is an odd integer) } `

<!-- ======================================================================= -->
## add

```
add(s, v) begin
  if(v in s) then
    return //- ignore
  else
    //- create a new component c
    //- set v as its value
    //- add c to s as a component
  end
end
```

* `(s + v) := add(s, v)`

The addition of a value to a simple set must be ignored, if the given set
already contains the to-be-added value as an element.

Note that, although obvious, this is a critical aspect that is essential to
maintain consistency. That is, the "request" of a user may be silently ignored,
if an implementation would otherwise produce results that are outside of the
boundaries of what is by definition allowed. Depending of a given context,
implementations may have no other choice but to throw an error.

<!-- ======================================================================= -->
## (random) iteration

```
traceOf(ms) begin
  s = ()
  for c in ms begin
    s.append(c.value)
  end
  return s
end
```

Similar to the iteration over generic multisets, an iteration over a simple
set must always be considered to return the elements in random order.

* `si := traceOf(ms), sj := traceOf(ms)`
* `(si != sj)` is in general true

As before, many more operations can be defined based upon random iterations.

Note however that those operations defined for multisets still/also apply to
simple sets. That is, `oneOf(s)` can be considered to be already defined. In
addition to that, if a new definition is specified, then that new definition
is considered to override/replace the old/previous definition.

<!-- ======================================================================= -->
## subset-of, superset-of

```
//- true if t is a subset of s
isSubsetOf(s, t) begin
  for c in t begin
    if (c.value in s) then
      continue //- ignore
    else
      return false
    end if
  end
  return true
end
```

Simple set `t` is a subset of set `s`, if all the elements in it are also
elements in `s`. Put differently, set `t` is no subset to `s` if it contains
an element that is not also an element in `s`.

Note that the empty set (`Ø` or `{}`) is a subset to any other set.

If set `s` is a subset of `t`, then set `t` can be described as a **superset**
of set `s`. Note that superset `t` may contain elements that are no elements in
the subset `s`.

* `(t superset-of s) := (s subset-of t)`
* `(s subset-of t) -> (#s <= #t)`

Note that a subset `s` can be formed from an set `t` by removing elements
(i.e. zero, one or more elements) from `t`. This general point of view will
be referred to as **the removal-based prespective**.

<!-- ======================================================================= -->
## equal, strict/proper-subset-of

If all the elements in set `s` are elements in `t` and vice versa, then both
hold the exact same elements. Based on that, both sets are considered to be
**equal**. Two sets that are not equal are said to be **distinct** from one
another. Based on that, distinct sets differ in one or more elements.

* `(s == t), (s equal-to t) := (s subset-of t) and (t subset-of s)`
* `(s == t) -> (#s == #t)`

In contrary to that, subset `s` is considered to be **a strict subset** of set
`t`, if `t` has one or more additional elements that are no elements in `s`.

* `(s strict-subset-of t) := (s subset-of t) and (s != t)`
* `(s strict-subset-of t) -> (#s < #t)`

Note that a strict subset `s` is formed from a set `t` by removing one or more
elements (i.e. at least one) from `t`. Because of that, and unlinke the simple
subset-of operator, a strict subset is always distinct to its superset.

* `(s strict-subset-of t) -> not (t strict-subset-of s)`

A strict subset is considered to be **sub-ordinate** (in regards to a set's
cardinality) to a superset. Conversely, a superset is considered to be
**super-ordinate** to a subset.

<!-- ======================================================================= -->
## related

Based on the above, and since the overall focus will be on distinct sets of
elements, the subset-of operator can be understood to denote the relationship
between two sets of elements. That is, two sets are said to be **related** if
one set is a subset to the other. Otherwise, both sets are said to be
**unrelated** with each other.

* `(s related-to t) := (s subset-fo t) or (t subset-of s)` if `(s != t)`

Note that the related-to operator is based upon a clear defintion. That is,
**all-of** the elements of one set must also be elements of the other set.
