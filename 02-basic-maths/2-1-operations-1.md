
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
## disjoint

The other extreme in regards to the related-to operator is the disjoint-to
operator, which requires **none-of** the elements of both sets to also be
elements of the other set. That is, the intersection between two disjoint
sets is empty.

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
As such, the set difference operation can be understood to have **no effect**
in regards to two disjoint sets since no element will be removed from `s`.

* `(s == (s \ t))` if `(s disjoint-to t)`

Likewise, an emty set `Ø` is returned, if both sets are equal. Put differently,
the set difference will be empty if `s` is a subset to `t`.

* `((s \ t) == Ø)` if `(s subset-of t)`

<!-- ======================================================================= -->
## characteristic subset (css)

Since all the elements within the set difference `(s \ t)` are distinct from
all the other elements in `t`, and as such unique to `s`  in regards to `t`,
the set difference `(s \ t)` will also be referred to as the
**characteristic subset** `css(s)` of set `s` in regards to set `t`.

* `css(s, t) := (s \ t)`

Note that the set difference is in general also known as a
**relative complement**.

<!-- ======================================================================= -->
## overlap

Two sets are said to overlap each other, if neither the intersection, nor the
symmetric difference between both sets are empty. That is, both sets have
elements in common and, on top of that, each of both sets contain elements the
other set does not have. Because of that, overlapping sets are neither disjoint
nor related.

* `(s overlaps t) := ((s & t) != Ø ) and ((s \ t) != Ø) and ((t \ s) != Ø)`

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
