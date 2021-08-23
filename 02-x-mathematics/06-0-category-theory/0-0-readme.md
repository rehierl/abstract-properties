
# category theory (CT)

Note that the content in this chapter reflects my level of understanding of
Category Theory (CT). At this point, that understanding can unfortunately only
be summarized as some general first impression. The following content will thus
barely scratch the surface of CT. Because of that, the following must be taken
with a grain of salt .. a lot of salt.

Note that, despite my lack of understanding of CT, the visualizations used in
CT allow to provide visual summaries of transformation processes (as introduced
below) from one class of objects to another class of objects. The focus of
this chapter is therefore to provide an introduction to these visualizations.

<!-- ======================================================================= -->

In essence, a (level-1) category is a directed graph such that its vertices
represent specific objects of some kind and the edges transformations (aka.
morphisms from one object to another. Such categories can therefore be
understood to represent groups of concrete objects.

* example - a set of trees and the operations between them

On the next higher level of abstraction, a (level-2) category can be understood
to have (level-1) categories as its objects, and morphisms (aka. functors) from
one such category to another. Such categories can therefore be understood to
describe how groups of objects can be transformed into one another.

* example - isomorphisms between node trees and order relations

Beyond that, a (level-3) category may be understood to generalize the concept
of transformations between categories. As such, the focus here is to describe
the characteristics of transformations.

Note that the focus on CT in the context of this discussion is on level-2
categories which contain isomorphisms between its (inner) categories.

<!-- ======================================================================= -->
## graph-based visualizations

Subsequent discussions will use labeled graphs in order to summarize
transformations from one group of objects onto another group of objects.

```
A --f--> B --g--> G
|---- h: g¤f ---->|
```

Note that it is assumed that, if two transformations (f: A -> B) and
(g: B -> G) exist, then another transformation (h: A -> G) can be formed
based upon the composition of transformations (i.e. h := g¤f). With that
in mind, one should read such visualizations with a certain amount of
transitivity.

```
A <--f,f°--> B <--g,g°--> G
|<----------h,h°--------->|
```

Subsequent discussions will build upon transformations (f: A -> B) which
allow to transform any object (x in A) onto an object (y in B) such that
there is an inverse transformation (f°: B -> A). Hence, an object x can
then be transformed into object y. Likewise, object y can be transformed
back into object x.

Based on that, the objects in such a pair will be referred to as being
**isomorphic** to each other. And since the groups/categories A and B
are thus understood to consist of pairs of isomorphic objects, both
groups/categories will be referred to as being isomorphic to each other.

As before, if a pair of inverse functors exist for two adjacent pairs of
Groups (A,B) and (B,G) then it is assumed that another pair of inverse
functors (h,h°) could be formed between the pair of groups (A,G). Hence,
one should be able to assume that even groups A and B are isomorphic.

Note that, as one can probably already tell, the transformation of morphisms
isn't on my (mental) radar. Unfortunately, my level of abstraction doesn't
seem to allow me to wrap my head around that aspect ... yet.
