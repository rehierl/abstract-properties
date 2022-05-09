
<!-- ======================================================================= -->
# differences between mathematics and computers

In Mathematics, the most basic "container type" is a multiset of elements.
Each non-empty multiset consists of distinct components, each of which is
defined to hold a well-defined element - e.g. a natural number.

<!-- ======================================================================= -->
## finite vs. infinite memory

Since any multiset may hold an infinite amount of elements, the most dominant
difference between Mathematics and computers becomes apparant:

* Mathematics does in general not care about storage requirements.
* Computers always have finite storage.

In contrary to Mathematics, any computer always has a limited amount of memory
that must be managed by an operating system. Because of that, the memory of a
computer is split up into bytes, each of which has a unique index (i.e. its
**memory address**) associated with it.

When writing an element to memory, that element must first be **serialized**
into a sequence of bytes, which is then written to a specific address. Based
on that, in-memory containers can always be understood to have a first and a
last component. After all, the order of bytes of a serialized container can
be understood to define an **index order** over the components in it.

<!-- ======================================================================= -->
## elements vs. instances

In Mathematics, two distinct sets may hold the numeric value 2. Even though
that abstract value is contained in distinct components, each of which is
unique to the corresponding set, one can state that both sets contain the
same numeric value. After all, in Mathematics, there is only one element
that has a numeric value of 2.

* Mathematics operates on globally unique elements.
* Computers have instances.

Since each entity in the memory of a computer has a unique address associated
with it, computers can in principle not support entities that are completely
indistinguishable from one another. After all, even if two entities hold the
exact same numeric value, they can still be distinguished from one another
via their memory address.

Because of that, programs first need to detect if two entities are supposed
to hold the same value, then they must treat these distinct entitites as if
they were identical. Based on that, each in-memory entity can be described
as the instance of an abstract element.

<!-- ======================================================================= -->
## unordered vs. ordered containers

Since any entity must be serialized into a sequence of bytes, programs can
not write all the elements in a simple set without associating some order
with them. After all, it must be guaranteed that writing an entity does not
overwrite another entity, especially if the binary representation of entities
require different amounts of bytes. Hence, even a simple set must in general
be serialized one element after another.

* Any (unordered) simple set is serialized as an ordered sequence.

As a consequence, no in-memory representation of a container is ever truly
without an "internal order". That is, there always is a first, next and a
last component. Because of that, unordered simple sets appear to a programmer
as the "artificial", and ordered containers as the more "natural" concept.

In contrary to that, and from an abstract mathematical point of view, it is
the other way around: Ordered containers appear as artificial since further
information is required that defines the underlying order.

One must therefore not confuse the order of written information, which can
not be avoided, as the definition of an actual order over the components in
a container. That is because that order might be a mere byproduct of our
inability to accurately visualize unordered containers.

<!-- ======================================================================= -->
## temporary inconsistency

Given the following definition, a human will be able to simply conclude that
a new set of numbers is being created such that all the elements in it are
increased by one.

* `B := { (x+1) | (x in A) }` where `A := { e1, e2, ... }`

Obviously, an implementation won't have much of an issue, if it can simply
create a new container object to return as `B`, and to add the modified values
while iterating over the elements in `A`. However, it is not that simple, if
the available memory is insufficient to hold both containers at the same time.

This limitation could be avoided, if container `A` is no longer required after
the creation of container `B`. After all, the elements in `A` could then be
**modified in-place**. This solution does however have an issue of its own
since no implementation can modify all the elements in one single operation.
It can only increase the value of each element one after another, which
**has the potential to temporarily produce an inconsistent state**. After all,
modifying one element in `A` has the potential to turn that element into one
that is equivalent to another. This however is in conflict with the basic
characterisitc of a simple set (aka. an invariant) as a container of distinct
elements.

* what if `(e1+1) == e2` is true?

Note that this conflict can not be resolved since dropping one of the elements
will produce a result that does not necessarily match the end result. That is
because at least one element might then be missing.

Because of that, and provided that the end-result can still be guaranteed to
be what it needs to be, implementations and data structures might have to allow
for temporary states to be inconsistent.

Note that, in the above example, an order of operation does obviously exist
which allows to avoid such an inconsistent state - i.e. process the elements
in `A` in decreasing order according to each initial value. However, there
is no guarantee that such a processing order does in general exist.
