
<!-- ======================================================================= -->
# value-based classification

In regards to the values of a property,
the following requirements can be defined:

**v0**: There are no requirements in regards to the values of a property.
That is, a property may have any value in the context of any node.

* `(#V(p) in [1,#N(p)])` is true

**v1**: The value of a property is required to be the same in each node.
That is, the property is treated as a named constant.

* `(#V(p) == 1)` is required to be true

**vN**: The value of a property is required to be associated with a value
that is unique in the context of a particular node.

* `(#V(p) == #N(p))` is required to be true

Note that a property which is by definition **required to satisfy vX**, may
be referred to as a **vX-property**. For example, a v1-property must satisfy
v1, whereas a vN-property must satisfy vN.

Note that a v0-property may in a given context still satisfy v1. The difference
is that a v0-property is not required to satisfy v1. Likewise, a vN-property
may still also satisfy v1, if that property is associated with one node only
(i.e. `(#N(p) == 1)`).

<!-- ======================================================================= -->
## examples

**v0-properties**

* A `Node.parentNode` property does not require that its values are distinct
  across all the nodes. That is because a parent may have more than one child.
* A `Node.level` property does not require that its values are distinct across
  all the nodes it is associated with. That is because, multiple nodes may be
  on the same node level.
* A `Node.group` property could be used to associate each node in a doctree
  with a specific group. That is, if each group is understood to be identified
  by the property's value.

Note that, if a `Node.group` property is allowed to hold atomic values only,
then each node can only belong to one such group. That is, the overall set
of nodes `N(p)` is a union of pairwise disjoint subsets, one for each value.

**v1-properties**

* A theoretical `Node.group-x` property could be used to indicate that a node
  belongs to a specific group (i.e. "group-x").

Note toat, if in some node the property `Node.group-x` is set to the value "yes",
then the node is understood to belong to the property's group. If, in contrary
to that the property's value is "no", then the corresponding nodes do not count
towards that particular group.

Note that a yes/no value is an implementation-specific necessity. After all,
a `Node.group-x` property definition applies to every node instance. That is,
a "no" value needs to be understood in terms of "the property does not apply
to the corresponding node". Put differently, a "no" value states that the
property needs to be treated as being synonymous to "undefined". Other than
that, a "yes" value may be implemented as a specific group id/reference and
a "no" value as a null id/reference.

**vN-properties**

* A `Node.id` property requires that the property has a unique value for each
  node it is associated with.
* A `Node.nextSibling` property is, with the only exception of a null reference,
  required to hold a unique reference for each node. After all, no two nodes
  in a tree can have the same next sibling.

<!-- ======================================================================= -->
## disjoint subsets of nodes

Each of the value-based requirements allows to define a subset of nodes
based on the nodes with which a property is associated, and one or more
subsets based on the values it has in regards to these nodes.

However, in order to refer to a certain subset, the value of a v1-property
is secondary. In contrary to that, a specific value must in general be
specified in the case of a v0- and a vN-property.

* `N(p,v) := { (n in N) | (p in K(n)) and (n.p == v) }`
* `(N(p,v) subset-of N(p))` is true if `(v in V(p))`
* `(N(p) == N(p,v))` is true if `(V(p) == {v})`

Note that, even though multiple v1-properties may have the same value, a
v1-property defines a strict 1:1 relationship between a property and its
value. In contrary to that, a v0- and a vN-property in general have any
number of distinct values (i.e. a 1:N relationship) associated with them.

Note that the set of nodes `N(p)` of a v1-property is such that the nodes
can be understood to have a unique characteristic in common (i.e. the
property `p`).

```
a v0/N-property                         a v1-property
===============================   vs.   ==============

|-N(p)------------------------|         |-N(p)-------|
| |-N(p,v1)-| |-N(p,v2)-|     |         | |-N(p,v)-| |
| |   ...   | |   ...   | ... |         | |   ...  | |
| |---------| |---------|     |         | |--------| |
|-----------------------------|         |------------|
```

Since the key of property `p` in the set of properties of a node `P(n)` is
unique, node `n` can not hold more than one value in regards to `p`. Because
of that, node `n` can not be an element in two or more sets of nodes (e.g.
`N(p,v1)` and `N(p,v2)` at the same time). The subset of nodes `N(p)` is
therefore a union of pairwise disjoint subsets (i.e. one for each value in
`V(p)`).

* `(N(p,vi) disjoint-to N(p,vj))` is true for `(vi,vj in V(p))`

Only one such subset exists per node in regards to a v1-property. In contrary
to that, a v0- and a vN-property have in general any number of disjoint subsets.
Also, a vN-property only has one node per subset.

* `(N(p) == N(p,v))` is true, if `p` is a v1-property
* `(#N(p,v) == 1)` is true for all `(v in V(p))`, if `p` is a vN-property

<!-- ======================================================================= -->
## a value-based expansion

```
one v0/N property                  several v1 properties
===========================   =>   =================================

|-N(p)--------------------|        |-N(k1)--------| |-N(k2)--------|
| |-N(p,v1)-| |-N(p,v2)-| |        | |-N(k1,v1)-| | | |-N(k2,v2)-| |
| |   ...   | |   ...   | |        | |    ...   | | | |    ...   | |
| |---------| |---------| |        | |----------| | | |----------| |
|-------------------------|        |--------------| |--------------|
```

Since `N(p)` can be seen as a union of pairwise disjoint subsets, each property
can in general be understood to represent **a set of v1-properties**. Because
of that, a property `p` can be replaced by one or more v1-properties, if each
pair `(p,v)` is replaced by a new pair `(k,v)` whose key is formed by combining
the old key `p` with the associated value `v` - e.g. `k := (p,v)`.

* `(p,v)` => `(k,v)` where `k := (p,v)`
* e.g. `(p,v1)` => `((p,v1), v1)` => `(k,v1)`

That is, keys are replaced by new ones which are unique to a property and one
of its values. Each subset `N(p,v)` of `N(p)` can therefore be understood to
correspond with a v1-property that is unique to it.

* `p` => `{ k1, k2, ... }` => `K`

<!-- ======================================================================= -->
## a value-based consolidation

```
several v1 properties               =>   one v0/N property
=================================        =================================

|-N(k1)--------| |-N(k2)--------|        |-N(p)--------------------|
| |-N(k1,v1)-| | | |-N(k2,v2)-| |        | |-N(p,k1)-| |-N(p,k2)-| |
| |    ...   | | | | ...      | |   =>   | |   ...   | |   ...   | |
| |----------| | | |----------| |        | |---------| |---------| |
|--------------| |--------------|        |-------------------------|
```

Since a v1-property corresponds with a particular subset of nodes, a group of
v1-properties `K := { k1, k2, ... }` can be understood to correspond with the
pairwise disjoint subsets of a v0-property `p`. Because of that, a group of
v1-properties `K` can be consolidated into a v0-property, if each pair `(ki,v)`
is replaced by a new pair `(p,ki)` whose key `ki` must not be an element in
`(K(T) \ K)`. That is because the replacement would otherwise merge two
unrelated properties.

Note that the following requirement must be satisfied: The set of nodes that
is defined by property `(ki in K)` must be disjoint to the set of every other
property `(kj in K)`. In other words, no node in a tree can be associated with
more than one property in `K`. That is because the consolidated property only
supports one value per node. However, one could still form the new key-value
pairs as `(p,s)` such that `s` is a combination of all those properties in `K`
with which a node was associated.

* `(N(ki) disjoint-to N(kj))` must be true for `(ki,kj in K)`

Note that the values of the v1-properties are not required to be distinct (i.e.
`(#V(K) <= #K)` may be true). After all, the consolidation will drop all the
values. However, one could still hold on to those values, if one would form the
new pairs as `(p,(ki,vi))`.

Based on the above, a group of v1-properties, whose sets of nodes are pairwise
disjoint, can be understood to correspond with a single v0-property.

* `K` => `{ k1, k2, ... }` => `p`

Note that the `Node.parentSection` object property is, on a theoretical level,
formed by consolidating one or more section properties.
