
<!-- ======================================================================= -->
## chains in order theory

A total suborder of a poset `S` can be described as **a chain (order)**.
Typically, the description as "a chain" is understood to refer to a subset
of `P(S)` that can be described as a total containment order.

<!-- ======================================================================= -->
## well-founded relation

A relation R over a set X is described as a **well-founded** relation,
if every non-empty subset S of X has a minimal element in R.

Note that, if the relation R is a total order relation, then each subset
has a least element. Because of that, the corresponding total order can
be described as a well-order.

Note that this characteristic can be used for inductive/recursive reasoning
(e.g. to proof that some proposition P(x) is true for all (x in X)).

Note that "each subset has a minimal element" does not state that "each subset
must have one (and only one) minimal element". That is, these subsets are not
required to have a least element. Consequently, each subset may have one or
more minimal elements.

Note that the order relation of a tree is a well-founded order relation.

<!-- ======================================================================= -->
## well-order

A **total order** such that **each subset has a least element**
can be described as a well ordered set.

Note that ...

* each finite well-ordered set has a least and a gratest element
* the set of natural Numbers is well ordered under the default/natural order
* the set of integers is not well ordered - there is no least negative
* each rooted path can be considered to correspond with a well-order

( Note that this definition is not entirely clear to me. The reason for that
is most likely that it has its origins in the context of infinite sets of
numbers. )

<!-- ======================================================================= -->
## family of scopes over an ordered sequence

Note that forming a family of scopes over an ordered sequence `s`
does something that can be considered similar to the above:

* (1) the first scope consists of all the elements in `s`
* (2) the least element `l` is removed from that set
* (3) the process is repeated for the set of remaining elements `E(s)\{l}`
* (4) the process continues until it ends with the last element `g`
* (5) `g` is the greatest element in `s`
