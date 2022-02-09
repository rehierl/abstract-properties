
<!-- ======================================================================= -->
# Forest/Hierarchy of reversed scopes

Forests and hierarchies of reversed scopes can be defined as follows.

<!-- ======================================================================= -->
## a forest of rscopes (F)

A set of reversed scopes `S` may be referred to as **a forest**,
if the following requirements are met.

* (R0) `S` is a partial setup of rscopes.
* (R1) Each rscope `(s in S)` has `#s` subscopes in `S`.

Note that the scopes in a forest of reversed scopes may be disjoint (DI),
related (RE), or overlap each other (OV) - i.e. the **DI-RE-OV** case.

<!-- ======================================================================= -->
## remarks on requirement R1

Unlike a forest of rooted paths, subscopes can in general be formed in any
number of ways. Because of that, a forest of rscopes can not be described as
being downward-closed since there is no fixed rule one could follow in order
to detect and determine missing scopes from existing ones.

However, requirement R1 is still a necessity since it ensures that each rscope
has one and only one characteristic element **CE**. That is because a forest
of rscopes is, as a partial setup, still required to be downward-total. Because
of that, all the ancestors of an rscope must be related with each other, which
is why any rscope has one more element in addition to its parent rscope. Hence,
any rscope has one and only one characteristic element.

* `(#css(s) == 1)` is true for any `(s in S)`
* `CE(S) == U(S)` is true

Since a forest is required to hold `#s` subsets for each scope `s` (including
scope `s` itself), any **root** rscope `r` in it is a 1-element set of nodes.

* `(#r == 1)` for any `(r in RS(S))`

As a matter of conseqeuence, the amount of rscopes in `A(s)` is anything but
arbitrary. That is because a forest must contain `#s` distinct subsets for
each rscope in it. Any **child** therefore has one more element in addition
to its parent, which is why **siblings** have the same size.

* `(#A(s) == (#s-1))` is true for any `(s in S)`
* `(#c == #p+1)` if `(p parent-of c)`
* `(#s1 == #s2)` if `(s1 sibling-of s2)`

The intersection between any two reversed scopes in `S` is either empty
or a reversed scope in that setup.

<!-- ======================================================================= -->
## a hierarchy of rscopes (H)

A set of reversed scopes `S` may be referred to as **a hierarchy**,
if the following requirements are met.

* (R0) `S` is a forest of rscopes.
* (R1) `S` has one and only one root.

Note that a hierarchy of rscopes `H` has the following properties.

* `(#RS(S) == 1)` and `(#S > 0)` must be true.
* Each rscope has no ex-or one parent - a subset.
* Each rscope may have any number of child scopes - overlappping.
* Each rscope has a unique rooted path (of reversed scopes).
* Any ancestor has fewer elements than all of its descendants.
* The root scope `r` in a setup is a set of one node only.

Note that, since a hierarchy is required to have one and only one root, the
rooted paths in a hierarchy of reversed scopes are not allowed to be disjoint -
i.e. the **RE-OV** case. That is because the root of a hierarchy is a subset
to all the scopes in that hierarchy.

<!-- ======================================================================= -->
## remarks

Note that there are remarks on hierarchies of rooted paths that might still
apply (with minor changes) to hierarchies of reversed scopes (i.e. disjoint,
subset).
