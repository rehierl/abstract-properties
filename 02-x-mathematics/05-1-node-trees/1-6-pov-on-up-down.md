
<!-- ======================================================================= -->
# a point of view on "up" and "down"

Note that, since the terms "up" and "down" depend on a certain point of view
(i.e. "up" with increasing values, "down" to leaf nodes), it seems to be more
appropriate to use the generic edge-based terms **presequent/subsequent**
whenever such an alternative is applicable. Unfortunately, and due to a lack
of words, that is not always possible (e.g. downward-total).

<!-- ======================================================================= -->
## the number-based point of view

```
a number-based set
==================
a -> .. n .. -> b
------------------
down            up
```

* (a downwards-to b) <=> (a presequent-to b)
* (b upwards-to a) <=> (b subsequent-to a)

Recall that the value-based point of view on the meaning of "up/down" is based
on the value that is associated with each element. As a consequence of that, the
edges in drawings of number-based ordered sets `P(V,<)` are oriented "upwards"
towards those elements with a higher values. That is, "up" is oriented towards
increasing numeric values.

<!-- ======================================================================= -->
## the tree-based point of view

```
a tree               a tree
==============       ===========
   a    | up         a -|-> b
------- |               |-> c
b     c | down       -----------
                     up     down
```

* (b downwards-to a) <=> (b subsequent-to a)
* (a upwards-to b) <=> (a presequent-to b)

In contrary to that, and in the context of a node tree `T(N,E)`, the meaning
of "up/down" is turned upside down. That is because the focus is not on the
values of numbers, but on the paths that can be formed over the edges of a
tree, which are oriented "downwards" in a vertical drawing.

Alternatively, one can speak of an **inside**, if one refers to the descendants
of a a given node. Based on that, one can speak of an **outside**. However, if
it comes to the "outside" of a node, one must distinguish between "not inside"
and the set of "ancestors". That is because the former in general includes more
than the latter.

<!-- ======================================================================= -->
## a default point of view

Even though the above mentioned conflict in semantics can not be resolved,
one can still notice that descriptions, which are based on the orientation
of a drawing, are in general the source of unnecessary confusion.

With that in mind, one can notice that the pair of terms "presequent" and
"subsequent" are independent of the orientation of a drawing, since these
terms are based on the orientation of the corresponding edges.

Because of that, it seems to make more sense to use the pair of terms
**presequent/subsequent** by default in order to decrease the amount of
dependency with a particular context.

<!-- ======================================================================= -->
## non-standard orders

Even more so, since the orientation of the edges can be defined to be against
standard definitions, or such that one can not simply associate a well known
natural order.

The **suffix-of** operator can be used as an example for such an order. After
all, (1) one can define an order based on the offset of a suffix, which is
increasing the smaller a suffix is. In contrary to that, (2) one can define
an order based on the length of a suffix, which is decreasing the greater the
offset of a suffix is.

* (a < b) := (a) is a suffix to (b) - with the number of elements in mind
* (a < b) := (b) is a suffix to (a) - with the offset of a suffix in mind

Note that one will usually want to define an order operator such that it is
more specific to a particular case.
