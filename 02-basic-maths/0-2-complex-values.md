
# complex values

Complex values are formed by grouping components without providing external
access to its internal components. With no further definition, the components
within a complex value may hold elements of any kind.

* `complex := < (atomic|complex)* >`

Note that a complex value with no further definition is in general referred
to as **a (mathematical) group**, or as **a multiset**.

Note that there is by default no restriction on which kinds of elements the
components of a complex type may hold. That is, one component may hold a
numeric value and another a string of characters. Furthermore, two components
may even have the same value as their element.

* `cx := < 21, 21, < true, false >, 'd', "abc" >`

Note that there is by default no order of any kind defined upon the components
of a complex value. That is, a complex value has by default no first, no last
and no n-th component. The order of elements specified by the definition of a
particular complex value must therefore be ignored.

* `cy := < 21, < true, false >, 21, 'd', "abc" >`
* `cx` and `cy` both refer to the same complex value

The number of components grouped by a complex value `cx` can be referred to
as the **cardinality**, or as the **multiplicity** of the complex value.

* `#cx, #(cx), (cardinality-of cx)` := the number of components in `cx`

Note that the cardinality of a complex value may or may not be equal to the
number of distinct elements it contains.

A complex value may be described as being **homogenous**, if the elements it
may hold must have certain characteristics. That is, a complex value may be
restricted to only hold (e.g.) number values, boolean values. Based on that,
the term "homogenous" can be understood to describe that all its elements
belong to a certain type/domain without naming the actual type itself. In
contrary to that, a complex value that has no such restriction may be described
as **heterogenous**.

A complex value may be described as **flat**, if all of its elements are atomic
values. In contrary to that, a complex value may be described as **nested**, if

