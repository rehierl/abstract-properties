
<!-- ======================================================================= -->
# Intervals

Intervals are most commonly used in the context of (real) numbers to denote a
certain range in the context of a known set of numbers. That is, an interval
can be described as the shorthand definition of a **(sub)set** of numbers:

* `i1 := [a,b] := { x | (a <= x <= b) }`
* that is `[a,b] := ( [a,*) and (*,b] )`

The interval `[a,b]` is said to have `a` and `b` as its **endpoints** such
that the set of numbers an interval defines contains all the numbers that are
greater than or equal to its 1st/lower endpoint and lower than or equal to
its 2nd/upper endpoint.

Note that, in the context of this discussion, the **lower endpoint** (i.e. `a`)
is expected to be lower than or equal to the **upper endpoint** (i.e. `b`).
That is, `(a <= b)` is required to be true.

* `(a presequent-to b) or (a equal-to b)` must be true

Note that the resulting set of numbers can be said to have a first and a last
number, and to contain every other number in between. As such, the set of
numbers an interval defines can be said to have **no gaps**.

In case an endpoint is not to be specified, it can be replaced by `+Inf` or
`-Inf`. In the context of this discussion, an unspecified endpoint will be
denoted by `*` and, depending on its position, needs to be understood to refer
to the smallest/largest element in the corresponding set of elements. Based on
that, interval `i1` can be redefined as the intersection between two sets:

* `i1 := [a,b] := (A & B)` where
* `A := [a,*] := { x | (a <= x) }` and
* `B := [*,b] := { y | (y <= b) }`

Interval `i1` can be described as being **closed** since it is defined to
include both of its endpoints (i.e. `<=` rather than `<`). In case neither
of the endpoints are to be included, the interval can be described as being
**open**. And if only one endpoint is not to be included, then the interval
can be described as **half-open**.

* `i2 := [a,b) := ( [a,*] & [*,b) ) := ( [a,*] & { y | (y < b) } )`
* `i3 := (a,b] := ( (a,*] & [*,b] ) := ( { x | (a < x } & [*,b] )`

In case the upper endpoint is excluded, an interval can be said to be
**right-open** and **left-closed** (e.g. `i2`). Similar to that, an interval
can be described as being **left-open** and **right-closed** (e.g. `i3`).

Note that, since the focus of this discussion is on finite sets of elements,
`[a,*]` and `[a,*)` are both considered to define the same interval. That is,
the largest element is always considered to be included. Likewise, there is
no strict distinction between `[*,b]` and `(*,b]` since the smallest element
is always considered to be included.

Note that, since intervals can be understood to define sets of elements based
upon a known superset, all of the **set-based opperations apply**. That is,
intervals can be used as actual sets of elements.
