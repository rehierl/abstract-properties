
<!-- ======================================================================= -->
# Storage location, serialization

In Mathematics, the most basic "container type" is a multiset of elements.
Each non-empty multiset consists of distinct components, each of which must
hold an element of some sort.

<!-- ======================================================================= -->
## infinite vs. finite memory

Since any multiset may hold an infinite amount of elements, the most dominant
difference between Mathematics and computers becomes apparant:

* Mathematics has by default no concept of limited storage.
* Computers have no infinite storage.

In contrary to Mathematics, any computer always has a finite amount of memory
that must be managed by an operating system. Because of that, the memory of
a computer is split up into bytes, each of which is associated with a unique
index, its **(offset) memory address**.

When writing an entity to memory, such as an abstract element, that element
must first be **serialized** into a sequence of bytes, which is then written
to a specific address in memory. Based on that, containers can always be
understood to have a first and a last component. That is, the order of bytes
of a serialized entity can be understood to define an **index order** over
the components in it.

<!-- ======================================================================= -->
## elements vs. instances

In Mathematics, two distinct sets may hold the numeric value 2. Even though
that numeric value is contained within distinct components, each of which is
unique to the corresponding set, one can simply tell that both sets contain
the same numeric value. After all, in Mathematics, there is only one element
that has a numeric value of 2.

* Mathematics has elements.
* Computers have instances.

Since each entity in a computer's memory always has a unique memory address
associated with it, computers can in principle not support entities that are
entirely indistinguishable from one another. That is, even if two entities
are supposed to hold the exact same abstract numeric value, they can still be
distinguished from one another by their memory address.

Because of that, programs first need to detect if two entities are supposed to
hold the same value, then they must treat these distinct entitites as if they
were identical. Because of that, each entity in memory is can be described as
the instance of an abstract element.

<!-- ======================================================================= -->
## unordered vs. ordered complex values

Since any entity must be written to memory as a sequence of bytes, programs
can not write all the elements in a simple set without assigning some order
to them. After all, it must be guaranteed that writing an entity does not
overwrite another entity. Because of that, even a simple set must be written
to memory one element after another.

* Any (unordered) simple set is serialized as an ordered sequence.

As a consequence, no in-memory representation of a container is ever truly
without an "internal order". That is, there always is a first, next and
last (inner) entity. Because of that, mathematical unordered simple sets of
elements may appear to a programmer as being the "artificial" and ordered
complex values as the more "natural" concept.

In contrary to that, and from an abstract mathematical point of view, it is
the other way around: Ordered complex values are the artificial ones since
further information is required that defines the corresponding order.

One must therefore not confuse the order of written information, which can
not be avoided, as actually defining an order over the components of a
container.
