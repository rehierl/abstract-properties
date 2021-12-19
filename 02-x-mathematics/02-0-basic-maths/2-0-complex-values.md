
# container types

Containers (aka. complex values) are formed by grouping components without
providing external access to these components. With no further definition,
the components within a complex value may hold elements/values of any kind.

* `complex := < id:(atomic|complex)* >`

Note that there is by default no restriction on which kinds of elements the
components of a complex type may hold. That is, one component may hold a
numeric value and another a string of characters. Furthermore, distinct
components may contain the same abstract value as their element.

* `cx := < 21, 21, < true, false >, 'd', "abc" >`

Note that labels may be used to specify the id value of a component/value.
These labels can then be used in subsequent discussions to refer to the
denoted component and/or the value it holds.

* `cz := < v1:21, v2:"abc" >`
* `(v1 == 21)` is true

Note that there is by default **no order of any kind** defined upon the
components of a complex value. That is, a complex value has by default no first
and no last component. The inherent order of elements specified by a syntactic
definition must therefore be ignored.

* `cy := < 21, < true, false >, 21, 'd', "abc" >`
* `cx` and `cy` both define the same complex value

A complex value may be described as being **homogenous** or **typed**, if the
elements it may hold must have certain characteristics. That is, a complex
value may be restricted to only hold (e.g.) number values, boolean values.

Based on that, the term "homogenous" can be understood to describe that all
its elements belong to a certain type/domain without naming the actual type
itself. In contrary to that, a complex value that has no such restriction may
be described as **heterogenous**.

* `m1 := < 1, 2, 3, ... >` is homogenous
* `m2 := < 'a', 1, 2, 3, ... >` is heterogenous

A complex value may be described as **flat**, if all of its elements are atomic
values. In contrary to that, a complex value may be described as **nested**,
if it contains other complex values. Obviously, further restrictions may apply
such that a multiset may contain only complex values. In order to allow for
further clarifications, one may speak of "strictly nested" and of "mixed"
multisets.

* `m1` and `m2` are both flat
* `m3 := < < 'a' >, 1, 2, 3, ... >` is nested/mixed

One may speak of **nesting levels**. In addition to that, one may refer to the
**nesting depth** (i.e. the maximum "depth") of a nested multiset. With that
in mind, multiset `m4` can be said to have a nesting level of 3 and a nesting
depth of 2.

* `m4 := < 1, < 2, < 3 >, 4 >, 5 >`
