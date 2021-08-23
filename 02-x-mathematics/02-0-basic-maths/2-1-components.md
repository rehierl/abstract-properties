
# components, elements

In order to form complex values from primitive ones, a concept of **components**
is required. In contrary to programming languages, a component in the context
of this discussion needs to be understood as a simple slot. That is, as some
storage container that is defined to hold a single primitive or complex value
of some sort.

* `ci.value = 2`

Note that the abstract value of a component may also be referred to as the
component's **element**. The description as "element" can be understood to
emphasize the relationship between an abstract value and a component. In
contrary to that, the term "value" can be understood to focus on isolated
entities.

Note that components have **no concept of typed values** associated with them.
That is, a container may in general hold elements of any kind. This includes
all the elements of all the other containers within the same complex value.
Depending on a given complex value, certain restrictions may however still
apply (e.g. "must only contain natural numbers").

Note that components themselves do not represent values of any kind. That is,
no component can have another component as its element. Even though, there is
no direct/explicit nesting of components defined, components can still hold
complex values as their elements, which could be described as an implicit
nesting of components.

In addition to its value, each component may have additional (object) properties
associated with it - e.g. a unique numeric id. Based on that, each component
can be considered **unique** and **distinct** to every other component.

* Complex values do not share any components.
* Complex values do not contain any component more than once.

Apart from an id value, a component may also be associated with one or more
references to other components. Based on such properties components can be
used to define the structure of a complex value.

* `ci.next` may be a defined component property

Note that one must always be aware that components are **inherently independent**
from one another. That is, two components within the same complex type may in
general hold the exact same abstract value.

* `(ci.value == cj.value)` may be true if `(i != j)`
