
# components, elements

In order to form complex values from primitive ones, a concept of **components**
is required. In contrary to programming languages, a component in the context
of this discussion needs to be understood as a simple slot. That is, as an
abstract storage container which is defined to hold a single primitive or
complex value of some sort.

* `ci.value = 2`

Note that the abstract value of a component may also be referred to as the
component's **element**. The description as "element" can be understood to
emphasize the relationship between an abstract value and a component. In
contrary to that, the term "value" can be understood to focus on isolated
entities.

Note that components have no type associated with them. That is, any container
may in general hold elements of any kind. This includes all the containers
within the same complex value.

In addition to its value, a component may have additional (object) properties
associated with it - e.g. a unique numeric id. As such, each component within
a complex value can be considered **unique** and **distinct** to every other
component.

* No complex value contains a component more than once.
* Complex values do not share any components.

Apart from an id value, a component may also be associated with one or more
named references to other components. Based on such properties components can
be used to define the structure of a complex value.

* `ci.next` may be a defined component property

Note that one must always be aware that components are **inherently independent**
units. That is, two components within the same complex type may in general hold
the exact same abstract value.

* `(ci.value == cj.value)` may be true if `(i != j)`
