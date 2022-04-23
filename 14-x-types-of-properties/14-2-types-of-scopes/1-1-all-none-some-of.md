
<!-- ======================================================================= -->
# The all-of, none-of and some-of quantifiers

```
|- document/visit order -- d --------- l ---------->|
|- none-of --------------->|- all-of ->|- none-of ->|
                           |- some-of ------------->|
```

As mentioned before, the difficult part is to provide a clear definition for
the some-of quantifier since the none-of and all-of quantifiers are almost
straight forward to define. However, since a scope is defined to include a
defining node and all the other nodes that are subsequent to it over the
corresponding base order, a scope can end before the end of the overal node
order is reached.

* `s(d) := [d,l] = [d,*]`
* all-of in regards to DTU/O
* some-of in regards to DPR

Based on that, a **some-of** quantifier can be defined in terms of all the
nodes in an open interval over a known base order `[d,*]` (all-of), that
implicitly defines which nodes not to include by excluding those that are
subsequent over the document order, but no longer subsequent over the base
order of the interval (none-of).

Note that there are in principle alternatives - e.g. exlude all the nodes
in the base order while including all the nodes that are not subsequent over
that order. However, in the context of this discussion, such a possibility
is understood as a mere theoretical alternative (i.e. not in the focus of
this discussion).

<!-- ======================================================================= -->
## some-of via end-tags

In regards to a substring over the document order, which can be described
as an open interval `[n,*]` over DTO, the following can be noted ..

```
.. <n> fc .. lc .. </n> <ns> ns .. ls .. </p> ..
   |- all-of -------->| |- none-of -------->|
```

The end-tag of a node does not just mark the end of a type-1 scope, it also
**divides a type-2 scope into two branches**: (1) left of the end-tag are all
the nodes that are descendant to `n` in DTU, and (2) right of the end-tag are
all the subsequent siblings and their descendants. That is, a node's end-tag
can be described to separate its type-1 descendants from its type-2 descendants
(i.e. a partition of descendants).

<!-- ======================================================================= -->
## some-of via suffixes

```
.. <n> fc .. lc .. </n> <ns> ... </r>
    |- infix ---------------------->|
                        |- suffix ->|
```

An interval `i := [n,*]` over a well known base order can be used to clarify
a some-of quantifier. Despite that, and due to `i` being a substring to the
document order, the same interval can be expressed in regards to the document
order via **the subtraction of suffixes**. As such, the default type-2 scope
of `n` can be described to be restricted by `ns`.

Note that this is exactly how rank-based headings can be used to define a
hierarchy of sections. That is, even a total order (flat documents) allows
to embed a partial suborder. This seems to suggest that rank-based headings
and the tag-based syntax are **equivalent to some extent**.
