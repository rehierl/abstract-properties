
<!-- ======================================================================= -->
# (covariant) functors

A category is not only used to describe a set of specific objects and the
transformations between them. That is because the objects within a cateory
can be of any kind: The objects in a category can themselves be categories.

Given two categories `C` and `D`, and a morphism `(F: C -> D)`, then `F` is
said to be **a functor**, if it maps every object `(c in C)` onto an object
`(F(c) in D)`, and also every morphism `(m in C)` onto a morphism `(F(m) in D)`
while preserving identity morphisms and compositions.

* `(c in C)` is mapped onto `(F(c) in D)`
* `(f: x -> y)` in hom(C) is mapped onto `(F(f): F(x) -> F(y))` in hom(D)
* `F(g¤f) = F(g)¤F(f)` is true for `(f: x-> y)` and `(g: y -> z)`

Note that a functor can be understood to induce a function such that each
morphism in C (the source category) is translated into a morphism in D
(the target category).

As such, a functor can be understood to map one category onto another.

<!-- ======================================================================= -->
## injective, surjective, bijective

Recall that each function (f: A -> B) corresponds with a binary relation that
is right-unique and left-total.

* right-unique - every target element in B has one unique source element in A
* left-total - every element in A is mapped onto an element in B

An injective function is a function that is also left-unique. That is, no two
elements in A map onto the same target element in B. As such, an injective
function is left-unique and right-unique (aka. one-to-one).

A surjective function is a function that is also right-total. That is, each
element in B has a source element in A. As such, a surjective function is
left-total and right-total (aka. "overall" total).

A bijective function is a function that combines all of these characteristics.
That is, a bijective function is one-to-one and total. Recall that any bijective
function has an inverse.

* **A faithful** functor is an injective mapping of morphisms.
* **A full** functor is a surjective mapping of morphisms.
* **A fully faithful** functior is a bijective mapping of morphisms.

<!-- ======================================================================= -->
## concrete categories

A category C can be described as **a concrete category**, if there is a
faithful function that can be used to map C onto the Set category.

Note that, one can thus consider the object C to be specific objects of some
kind, since they have a counterpart in Set. Hence, the description of category
C as "concrete". Put differently, each object in C can be described in terms
of sets of elements.

Note that a faithful functor is not required to be right-total. That is, the
set of object in C may be smaller than its counterpart in C.

A category that has no such faithful functor can be described as
**an abstract category**. Hence, any category is by default "abstract".
