
<!-- ======================================================================= -->
# Venn diagrams

As mentioned before, the section of a heading is a substring of nodes in regards
to the document order. As such, each section contains each node no more than
once. Because of that, a section corresponds with a simple set of nodes.

Since a document does in general have more than one heading, and therefore in
general more than one section, sections may or may not have one or more nodes
in common. Based on that, relationships between sections are established.

```
|-A-----|
|   |-B-|---|
| 1 | 2 | 3 |
|   |---|---|
|-------|
```

The combinations for subsets 1, 2 and 3, each being empty or non-empty in sets
A and B, and based on that the relationships between both sets, are as follows:

```
subset 1          | subset 1       |
is empty          | is non-empty   |
==================|================|===
1: 000 - DI,RE,EQ | 5: 100 - DI,RE | subset 2
2: 001 - DI,RE    | 6: 101 - DI    | is empty
------------------|----------------|----
3: 010 - RE,EQ    | 7: 110 - RE    | subset 2
4: 011 - RE       | 8: 111 - OV    | is non-empty
```

- XYZ := X represents subset 1, Y subset 2 and Z subset 3
- (Y in {0,1}), where (0 := "2 is empty") and (1 := "2 is non-empty")
- e.g. 001 := subsets 1 and 2 are empty, but subset 3 is not
- e.g. both sets are empty in case (1), only A in (2) and only B in (5)

In cases 4 and 7 one set is a strict subset to the other. Based on that, both
sets are said to be strictly related with each other. Hence, one set is super-
and one set is sub-ordinate to the other. Consequently, there is a strict
orientation between both sets.

Note that the description as "super-ordinate" and as "sub-ordinate" in this
discussion is in regards to the number of elements (aka. cardinality) of the
corresponding sets. That is, of two (strictly) related sets, the set with the
most amount of elements is said to be super-ordinate to the other.

Both sets are equal in cases 1 and 3. That is, none of the sets is super- or
sub-ordinate to the other. Furthermore, those cases are special cases of both
sets being related (RE) with each other. That is, both sets are subsets to
each other.

In cases 2 and 5 only one of the sets is empty. Because of that, theses cases
are ambiguous since the empty set is disjoint and related to any other set.
That is, in regards to having no element in common with any other set, the
empty set can be said to be outside of every other set. Likewise, and with
regards to having no other distinct element of its own, the empty set can be
said to be inside of every other set.

In case 6 both sets are non-empty and disjoint. That is, both sets have no
element in common. As such, both sets are said to be unrelated with each
other.

In case 8 both sets overlap each other, which is why none is a subset to the
other. Since both sets still have some elements in common, both sets can be
said to be related with each other in some way. However, the relationship
between both sets remains unclear.

Since the above listing of relationships is exhaustive, there are only three
distinct types of relationships between two non-empty distinct (i.e. non-equal)
sets possible: Both are either disjoint (DI), (strictly) related (RE), or both
sets overlap each other (OV).

<!-- ======================================================================= -->
## summary

Since the "related" case can be understood to cover the "equal" case, the latter
does not have to be distinguished separately. Because of that, the cases for the
empty set and two non-empty sets can be summarized as follows, while using Ø to
to represent the empty set, and A and B to represent two non-empty set which
may or may not be distinct.

```
     \ set-2 |           |
set-1 \      | Ø         | B
-------------------------------------------
 Ø           | DI and RE | DI and RE
-------------------------------------------
 A           | DI and RE | DI xor RE xor OV
```

As can be seen, two non-empty sets can be disjoint (DI), related (RE), or both
sets overlap (OV) each other - in short **DI ex-or RE ex-or OV**.

Note that, since the relationship between overlapping sets remains unclear,
the overall focus of this discussion will be on cases 4, 6 and 7. That is,
two non-empty distinct sets/sections will either be disjoint ex-or (strictly)
related - in short **DI ex-or RE**.
