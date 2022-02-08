
<!-- ======================================================================= -->
# a recap on relationships between sets

The focus of the following is on a set of elements (e.g. `s`) that is related
to other sets (e.g. `t` and `u`) in a well defined way. In addition to that,
the relationships between pairs of sets (e.g. `s-t` and `s-u`) needs to be
such that it can be determined which of those two sets (i.e. `t` or `u`) is
more relevant to the initial set (i.e. `s`). Based on that, the overall focus
is on a set of sets (aka. a family of sets) such that the relationships between
any two of its sets (i.e. in regards to all the other sets) is well defined.

<!-- ======================================================================= -->
## a recap on venn diagrams

Recall the possible combinations for two intersecting sets:

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
------------------|----------------|---
3: 010 - RE,EQ    | 7: 110 - RE    | subset 2
4: 011 - RE       | 8: 111 - OV    | is non-empty
```

Recall that "110" of case-7 denotes that subsets 1 and 2 are both non-empty,
whereas subset 3 is empty. Both sets A and B are therefore non-empty.

Since the "related" case can be understood to also cover the "equal" case, the
latter does not have to be distinguished separately. Because of that, the cases
for the empty set and two non-empty sets A and B can be summarized as follows:

```
     \ set-2 |           |
set-1 \      | Ø         | B
-------------------------------------------
 Ø           | DI and RE | DI and RE
-------------------------------------------
 A           | DI and RE | DI xor RE xor OV
```

As can be seen, two non-empty sets can be disjoint (DI), related (RE), or both
sets overlap each other (OV) - in short **DI xor RE xor OV**, or **DI-RE-OV**.

Consequently, to achieve clear definitions one must require sets to be non-empty,
distinct, and one must disallow disjoint and/or overlapping sets. Most commonly,
sets are allowed to be disjoint, but not allowed to overlap each other (DI-RE).
However, depending on a given context, one can allow overlapping sets while
disallowing disjoint sets (RE-OV).

* case DI-RE: a setup of scopes
* case RE-OV: a setup of rooted paths

Note that in both cases, and in regards to distinct non-empty sets, an unclear
relationship (i.e. DI and OV) is used in combination with an unambiguious
relationship (i.e. RE). Based on that, one can state that the "unrelated" case
is covered by the unclear case.

<!-- ======================================================================= -->
## visualization of sets

A multiset of "flat sets" can be visualized as a multiset of "nested sets"
(i.e. a box/border-based representation). That is, flat sets are visualized
**as if they were nested**.

```
|-A-----------------|        multiset-of-sets := <
| 1 |-B-| |-C,D-| 4 |          A: { 1, 2, 3, 4 },
|   | 2 | |  3  |   |   <=>    B: { 2 },
|   |---| |-----|   |          C: { 3 },
|-------------------|          D: { 3 } >
```

* Set A contains elements 1 to 4.
* Set B only contains element 2.
* Set C and D both only contain element 3.

Elements may belong to more than one set:

* Element 1 and 4 both only belong to set A.
* Element 2 belongs to sets A and B.
* Element 3 belongs to sets A, C and D.

Note that the term **nested set** is in general used to refer to sets that
have elements which are themselves sets. That is, the elements in a nested
set may or may not be sets of elements. The notion of "nested" in the context
of this discussion is however on a set that has another set as a subset (i.e.
"subset-of" instead of "element-of") and therefore does not contain the other
set as an element.

<!-- ======================================================================= -->
## the empty set (Ø)

```
|-A-------------------|
| 1 |-B-| |-C-| |-D-| |
|   | 2 | | 3 | |   | |
|   |---| |---| |---| |
|---------------------|
```

Set D has no element and therefore represents the empty set. Despite having
no element, set D still counts as a subset of set A and more importantly also
as a subset of sets B and C. That is because the empty set can be formed from
any non-empty set by removing all of their elements. The empty set is as such
a subset and also disjoint to any set.

Note that no other set (i.e. no non-empty set) is a subset to another set and
also disjoint to it. This characteristic is **unique** to the empty set.

Since the relationships of the sets in the pairs B-D and C-D can not be
distinguished in regards to D, sets B and C appear to be equally relevant
to D. Due to this ambiguity, the empty set can not be allowed as an element
in a setup/family of sets.

<!-- ======================================================================= -->
## equal sets

Sets C and D are equal because there is no element that allows to distinguish
both from one another. As such, both sets represent distinct instances of two
sets that have identical content. Based on that, the following visual
representations are equivalent:

```
|-C,D-|       |-C-----|      |-D-----|       |-D,C-|
|  3  |  <=>  | |-D-| |  <=> | |-C-| |  <=>  |  3  |
|-----|       | | 3 | |      | | 3 | |       |-----|
              | |---| |      | |---| |
              |-------|      |-------|
```

Since both sets are equal, there is no distinct order between the two. In order
to avoid such unclear relationships, each set needs to have elements that allow
to distinguish it from every other set. That is, **sets must be distinct**,
which is why "a set of sets" rather than "a multiset of sets", is required.

<!-- ======================================================================= -->
## overlapping sets

```
|-E-----|           |-F-----|
|   |-F-|---|       |   |-E-|---|
| 1 | 2 | 3 |  <=>  | 3 | 2 | 1 |
|   |---|---|       |   |---|---|
|-------|           |-------|
```

Set E contains elements 1 and 2, and set F elements 2 and 3. That is, both sets
contain element 2, but E does not contain 3 and F does not contain 1. As before,
there is no distinct order between the two since both sets are not related with
each other.

Note that sets E and F are said to **overlap** each other, which is visible via
the **crossing borders**. That is, both sets have elements in common (i.e. not
disjoint) and elements the other set does not have (i.e. not related with each
other). As such, overlapping sets represent another type of unclear relationships
between sets.
