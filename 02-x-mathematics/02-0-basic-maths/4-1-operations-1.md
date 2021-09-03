
<!-- ======================================================================= -->
## union (+, or)

```
unionOf(s, t) begin
  r = {}
  for c in s begin
    r.add(c.value)
  end
  for c in t begin
    r.add(t.value)
  end
  return r
end
```

The union of two sets is formed by creating a new set that contains all the
elements of both sets.

* `(s + t), (s or t), (s union t) := unionOf(s, t)`
* `(#u <= (#s + #t))` is true if `(u := (s + t))`
* `(#u == (#s + #t))` iff `(s disjoint-to t)`

<!-- ======================================================================= -->
## intersection (&, and)

```
commonToBoth(s, t) begin
  r = {}
  for c in s begin
    if (c.value in t) then
      r.add(c.value)
    end if
  end
  return r
end
```

The intersection between two sets refers to a set of elements that is a subset
to both sets: The intersection between two sets contains all those elements
that are shared between (aka. common to) both sets.

* `(s & t), (s and t) := commonToBoth(s, t)`
* `(u subset-of s) and (u subset of t)` is true if `(u := (s & t))`

Note that two sets with a non-empty intersection can be described as
sets that **intersect each other**.

* `(s intersects t) := ((s & t) != Ø)`

Note that the intersection between both sets is equal to both,
if both sets are equal.

* `((s & t) == s) and ((s & t) = t)` if `(s == t)`

<!-- ======================================================================= -->
## subset-of, coupled, disjoint

Recall that set `s` is a subset of `t`, if **all-of** the elements in it are
also elements in `t`. Put differently, set `s` is a subset of `t`, if `s` is
equal to the intersection between both sets.

* `(s subset-of t) := ( (s & t) == s )`

Based on that one can state that sets `s` and `t` are both related with each
other, if one set is a subset of the other.

* `(s related-to t) := (s subset-of t) or (t subset-of s)`

From a less strict point of view on can state that sets `s` and `t` are
coupled with each other, if both sets share **some-of** (i.e. one or more)
their elements. That is, if the intersection between both sets is non-empty.

* `(s coupled-with t) := ( (s & t) != Ø )`

The other extreme in regards to related-to is that two sets are disjoint to
each other, if **none-of** the elements they have are shared elements. That
is, the intersection between two disjoint sets is empty.

* `(s disjoint-to t) := ( (s & t) == Ø )`

<!-- ======================================================================= -->
## difference (\, sub)

```
uniqueTo(s, t) begin
  r = {}
  for c in s begin
    if (c.value in t) then
      //- drop/ignore
    else
      r.add(c.value)
    end if
  end
  return r
end
```

The set difference `(s \ t)` between two sets is formed by removing all the
elements in `t` from the elements in `s`. Put differently, all those elements
in `s` are dropped that are also elements in `t`.

* `(s \ t), (s sub t) := uniqueTo(s, t)`
* `(A \ B) := { x | (x in A) and (x !in B) }`

Note that this operation will return a clone of `s`, if both sets are disjoint.
In such a case the set difference operation can be said to have **no effect**.

* `(s == (s \ t))` if `(s disjoint-to t)`

Likewise, an emty set `Ø` is returned, if both sets are equal. Put differently,
the set difference will be empty if `s` is a subset to `t`.

* `((s \ t) == Ø)` if `(s subset-of t)`

<!-- ======================================================================= -->
## characteristic subset (css)

Note that all the elements within a set difference `(s \ t)` are distinct from
all the other elements in `t`. Put differently, the elements within a set
difference distiguish `s` from `t`, which is why they can be described as being
unique to `s`. Based on that, the set difference `(s \ t)` may also be referred
to as the **characteristic subset** `css(s)` of `s` in regards to `t`.

* `css(s), css(s, t) := (s \ t)`

Note that the set difference is in general also known as a **relative complement**.

<!-- ======================================================================= -->
## overlap

Two sets are said to overlap each other, if neither the intersection, nor the
symmetric difference between both sets are empty. That is, both sets have
elements in common and, on top of that, each of both sets contain elements the
other set does not have. Because of that, overlapping sets are neither disjoint
nor related.

* `(s overlaps t) := ((s & t) != Ø ) and (css(s) != Ø) and (css(t) != Ø)`

Note the qualifier **some-of** in regards to those elements that are shared.
That is, overlapping sets have some, but not all of their elements in common.
Because of that, two distinct and non-empty sets are, in the context of this
discussion, in general required to be disjoint ex-or (strictly) related - in
short **DI ex-or RE**.

<!-- ======================================================================= -->
## symmetric difference (^, xor, ex-or)

The symmetric difference of two sets is formed by removing the intersection of
both sets from the union of both. What remains is a set of those elements that
are elements in one set only. As such, none of the elements within a symmetric
difference between two sets are shared across both sets. Because of that, these
elements can considered unique to the set they originated from.

* `(s ^ t), (s xor t), (s ex-or t) := (s + t) \ (s & t)`
* alternatively `(s ex-or t) := ( (s \ t) + (t \ s) )`

Note that the symmetric difference is equal to the (simple) difference between
both sets, if set `t` is a subset of set `s`.

* `((s ex-or t) == (s \ t))` if `(t subset of s)`
