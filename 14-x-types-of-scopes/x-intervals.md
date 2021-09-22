
<!-- ======================================================================= -->
## intervals over posets

all-of, none-of, some-of
- the `( [d,*] \ [x,*] )` issue
- what if `( x subsequent-to d )`
- messed up, if `[x,*]` overlaps `[d,*]`
- html's inconsistency issue ...

intervals over posets
- `[a,b] := ( [a,*] and [*,b] )`
- `[a,b] <=!=> ( [a,*] \ [b,*] )` (!)

Note that, if intervals `[n,*]` and `[ns,*]` are both understood to be in
regards to DTU, then both are disjoint. That is, `[ns,*]` does not contain
any node in `[n,*]` and no subsequent sibling of `ns` (including all of their
descendants). Based on that, the following subtraction would have no effect.

* `i := [n,ns) = ( [n,*] and [*,ns) )` over DTO
* `i = ( [n,*] \ [ns,*] )` over DTO - not in general (!)
* `i = Ø` over DTU

Note that, in the context of a tree, the interval `[a,b]` will be empty,
if nodes `a` and `b` are incomparable with each other. That is because the
intervalls `[a,*]` and `[*,b]` are then disjoint.

* `( [a,*] disjoint-to [b,*] )` over DTU
* `i := [a,b) = Ø` over DTU

<!-- ======================================================================= -->
## some-of via start-tags

```
--- d ------------ x ------ l --->|
    |- all-of ------------->|
                   |- none-of --->|
```

* `s(d) := ( [d,*] \ [x,*] )`
* note - `( x descendant-of d )`

It stands to reason, if suffix `[x,*]` can contain any node in suffix `(l,*]`
(in regards to the document order). Put differently, if `[d,l]` and `[x,*]`
do overlap, or if `[x,*]` is a subset to `[d,*]`.

<!-- ======================================================================= -->
## remarks

Since `t(x,y) := tO(x) \ t(y)` will in general not work if `y` is anything but
a subsequent sibling to `x` (WHY ?!?) ...

* the `(\)` must be understood to remove a suffix
* `y` can not be an ancestor to `x` since these are not subsequent to `x`
* `y` can not be a subsequent sibling to `x` since `tO(x)` is then disjoint to `t(y)`
* `y` can not be a descendant of `x` since `(\)` is then, as the removal of a
  suffix, not applicable - i.e. in general not a suffix
* if `(\)` were to be redefined as the removal of a subset, then that would
  tear the section of `x` apart - i.e. it would introduce a gap
* `(\)` can not be redefined to end `x` either way since the other nodes are
  simply not subsequent to `y` - i.e. as an extension to the before
* an attempt to redefine `(\)` in regards to TO will end in a fucking mess
* you would have to move on to `tP()` - has issues of its own

Note that `tU(n)` acts like the **characteristic element (CE)** to, or as the
**characteristic subset (CSS)** of `tO(n)`.
