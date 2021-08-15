
<!-- ======================================================================= -->
# relationships of scopes

Recall the possible relationships between simple sets of elements that can be
visualized using Venn diagrams. Based on such a diagram one can conclude that
two distinct non-empty sets of elements are **disjoint (DI)**, **related (RE)**,
or both sets **overlap (OV)** each other.

Since a set of scopes must be such that the scopes in it are either disjoint
ex-or related (i.e. **DI ex-or RE**) in order to correspond with a total/partial
order of scopes, and thus in order to correspond with a node tree, overlapping
scopes can not be allowed.

Assuming that each cell/node may declare **no more than one property** of a
kind that can be shared across the nodes, one can conclude that the scope of
a property `pj` that was declared by some node `nj` must, at the very latest,
end with the scope of a property `pi` that was declared by a node `ni`. That
is because if both scopes can not be considered disjoint, then one would
otherwise end up with overlapping scopes.

* if `(ni < nj)` and `(s(pi) coupled-with (s(pj))`
* then `(lastOf(pj) <= lastOf(pi))` must be true
* where `lastOf(pj)` := the last element in `s(pj)`

Consequently, in the context of an ordered sequence,
**the following requirements must be met**, if the set of scopes embedded
into an ordered sequence is intended to correspond with a total/partial
containment order and thus to correspond with a node tree.

* if `(d(pi) < d(pj))`, then ..
* either `(lastOf(pi) < d(pj))` ex-or `(lastOf(pj) <= lastOf(pi))`
* note - either disjoint ex-or related

<!-- ======================================================================= -->
## remarks

Note that, in contrary to such scope orders, the rooted paths in a tree form a
set of rooted paths such that two paths are either related (one is a prefix of
the other) ex-or the paths overlap each other (i.e. **RE ex-or OV**). It seems
as if both orders may turn out to be isomorphic (TODO - proof required).
