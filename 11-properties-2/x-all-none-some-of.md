
Note that the following needs to be fleshed out and/or to be moved to a
different section/chapter.

<!-- ======================================================================= -->
# The all-of, none-of and some-of quantifiers (2)

```
- document/visit order --- d ----------- l ------------->
|- none-of --------------->|- some-of ----------------->|
                           |- all-of --->|- none-of --->|
```

Recall that the scope of an operation `s(d)` is in regards to those nodes that
are subsequent to the defining node `d` up to and including some last node `l`.

* `s(d) := [d,l]`

Assuming that the last node `l` is the last node of a well known **suborder**,
then the default definition of generic properties does still apply in regards
to that suborder. That is because node `l` is then assumed to be the last
node subsequent to `d` in that suborder.

* `s(d) := [d,l] := [d,*]`

Because of that, the all-of quantifier must be understood to be in regards
to such a well defined suborder.

Note that the default scope `s(d) := [d,l]` can therefore be understood to
suggest that a some-of quantifier can be clarified in terms of an all-of and
a none-of sub-quantifier. As one might already suspect, these sub-quantifier
will be in regards to well defined suborders.

<!-- ======================================================================= -->

```
- document/visit order --- d ------------- x ---- l ---->
|- none-of --------------->|- some-of ----------------->|
                           |- all-of ------------>|
                                           |- none-of ->|
```

Assuming that there is some other node `x` that is intended to tell that the
scope of `d` ends with node `x` (excluding `x` itself), then the scope of `d`
can in principle be understood to end prematurely. Based on that, the resulting
scope can be described as an open interval that prematurely ends with node `x`.

* `s(d) := [d,x) := [d,*] \ [x,*]`

It stands to reason if the suffix `[x,*]` can contain any node in the suffix
`(l,*]` (in regards to the document order). Put differently, if the suffixes
`[d,*]` and `[x,*]` do overlap, or if `[x,*]` is completely contained within
`[d,*]`.

<!-- ======================================================================= -->

```
- document/visit order --- d ----------- l x ----------->
|- none-of --------------->|- some-of ----------------->|
                           |- all-of --->| |- none-of ->|
```

Assuming, that the last node `l` subsequent to `d` in the corresponding
suborder is presequent to `x`, then the default scope `s(d)` can not end
prematurely because it has already ended (by default). Since the intervals
`[d,*]` and `[x,*]` are disjoint, the instruction to "prematurely" end the
default scope `s(d)` has no effect on it. That is, the scope `s(d)` remains
as is.

* `(s(d) := [d,*] \ [x,*]) <-> ( s(d) := [d,*] )`
* if `([d,*] disjoint-to [x,*])` is true

One must therefore be aware that the "intended" close instruction of node `x`
might end up having an "unintended" effect on a different scope.

Note that, in the context of a node tree, the interval `[a,b]` will be empty,
if nodes `a` and `b` are incomparable with each other. That is because the
subintervalls `[a,*]` and `[*,b]` are then disjoint.

* `(T[a,b] == Ø)` is true if `(a incomparable-to b)`
