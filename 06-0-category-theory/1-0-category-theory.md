
<!-- ======================================================================= -->
# Category theory (CT)

The intention of Category theory is to formalize mathematical concepts in terms
of labeled directed graphs, each of which is referred to as **a cagetory**.

<!-- ======================================================================= -->
## (abstract) category

The vertices in a category represents **objects** of some kind, and the edges
**morphisms** represent transformations between these objects. Based on that,
a category can be described as a directed graph that is associated with a
mapping between its edges and a set of morphisms (hence - labeled graphs),
each of which can be described as a function (f: A -> B) from one vertex/object
to another. Because of that, the focus of CT is not on the vertices, but on
the morphisms between them.

```
A --f--> B --g--> G
|------ g¤f------>|
```

However, a category is not a simple graph that has labeled edges.
That is because the following requirements must be met:

(1) An identity morhpism `id(x)` must exist for each object in it such that
its result is the input object given (i.e. `(id(x) = x)`). That however seems
to be a mere formal requirement, which can be understood to be satisfied at
all times.

(2) It must be possible to compose morphisms (e.g. g¤f) associatively. That
is, `h¤(g¤f) = (h¤g)¤f` is required to be true.

Due to the above, a category `C` can be described as consisting of a set of
objects `ob(C)` and of a set of (homo)morphisms `hom(a,b)`.

Note that, since `hom(a,b)` is a set of morphisms, the definition of a category
does by default only support one edge/morphism between two objects, which seems
somewhat restrictive.

Note that, as with node trees, and except for the `id(x)` morphism, there seems
to be no general concept of semantics. That is, one is simply supposed to "know"
the meaning of every other morphism. Put differently, like node trees, CT seems
to only focus on structure.

<!-- ======================================================================= -->
## morphisms

As introduced above, a morphism is a mapping (f: A -> B) from one object to
another. Because of that, a morphism can be formed and classified as if they
were ordinary functions.

```
A --f--> B
|<---g---|
```

A morphism/transformation (f: A -> B) for which there is an inverse (g: B -> A)
can be described as **an isomorphism**.

* `f¤g(B) = B` and `g¤f(A) = A`

Note that, in some sense, (f) can be understood to transform object A into
object B such that, B can be understood to represent an alternative description
of A. Because of that, B can be used to recreate A. Based on that, objects A
and B can be described as being **isomorphic** to each other. Because of that,
objects A and B can be considered **equivalent**.

Even though there are several other characteristics a morphism may have, the
overall focus in the context of this discussion is on isomorphisms.

<!-- ======================================================================= -->
## Set - the category of sets

*The category of sets* is the category whose objects are sets, and whose
morphisms are total functions between these sets.

Based on the above, I am under the impression that a category is in general
understood to contain all of the concrete objects of a certain kind in a given
context, and that the morphisms are specific (aka. concrete) transformations
which turn one such object into another.

* ob(Set) contains every set of elements that is possible (a universe)
* `A := {1,2,3}`, `B := {1,2}`, `(f: A -> B)`
* morphism (f) represents the removal of element `3` from `A`

Note that any category for which there is a faithful functor, i.e. an injective
morphism, onto the Set category can be described as **a concrete category**.
