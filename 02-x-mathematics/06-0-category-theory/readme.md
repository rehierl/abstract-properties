
# mathematics / category theory (CT)

The content in this chapter reflects my current level of understanding of
Category Theory (CT). At this point, that understanding can unfortunately only
be summarized as **some general first impression**. The following content will
thus barely scratch the surface of CT, which is why the following must be taken
with a grain of salt .. a lot of salt.

Note that the focus of this chapter can be understood to be on the introduction
of **graph-based visualizations** which will be used to summarize transformations
(aka. isomorphisms) from one class of objects/structures to another.

<!-- ======================================================================= -->
## what to keep in mind

In essence, a **level-1** category is a directed graph such that its vertices
represent specific objects of some kind, and the edges transformations (aka.
morphisms from one object to another. Such categories can therefore be
understood to represent groups of concrete objects.

* e.g. a set of trees and the operations between them

On the next higher level of abstraction, a **level-2** category can be described
to have (level-1) categories as its objects, and morphisms (aka. functors) from
one such category to another. Such categories can therefore be understood to
describe how groups of objects can be transformed into one another.

* e.g. isomorphisms between node trees and order relations

Beyond that, a **level-3** category may be understood to generalize the concept
of transformations between categories. As such, the focus here is to describe
the characteristics of transformations.

Note that, in the context of this discussion, **the focus on CT is on level-2**
categories which focus on the isomorphisms between its (inner) categories.
