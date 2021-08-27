
<!-- ======================================================================= -->
# graph-based visualizations

Subsequent discussions will use labeled graphs in order to summarize
transformations from one group of objects onto another group of objects.

```
A --f--> B --g--> G
|---- h: g¤f ---->|
```

Note that it is assumed that, if two transformations (f: A -> B) and
(g: B -> G) exist, then another transformation (h: A -> G) can be formed
based on the composition of transformations (i.e. h := g¤f). With that
in mind, one should read such visualizations with transitivity in mind.

```
A <--f,f°--> B <--g,g°--> G
|<----------h,h°--------->|
```

Subsequent discussions will build upon transformations (f: A -> B) which
allow to transform any object (x in A) into an object (y in B) such that
there is an inverse transformation (f°: B -> A). An object x can thus be
transformed into object y. Likewise, object y can be transformed back
into object x.

Based on that, the objects in such a pair will be referred to as being
**isomorphic** to each other. And since the groups/categories A and B
can be understood to consist of pairs of isomorphic objects, both groups
will be referred to as being isomorphic to each other.

As before, if a pair of inverse functors exist for two adjacent pairs of
Groups (A,B) and (B,G) then it is assumed that another pair of inverse
functors (h,h°) could be formed between the pair of groups (A,G). Hence,
one should be able to assume that even groups A and B are isomorphic to
each other.

Note that, as one can probably already tell, the transformation of morphisms
isn't on my radar. Unfortunately, my level of abstraction doesn't seem to
allow me to wrap my head around that aspect ... yet.
