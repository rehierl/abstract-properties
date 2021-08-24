
<!-- ======================================================================= -->
## if (#CE(s) == 1) is required to be true

```
|----------------|
| s1    s2    s3 | - S
|-|-----|-----|--|
  |     |     |
|-|-----|-----|--|
| c1    c2    c3 | - CSS(S)
|-|-----|-----|--|
  |     |     |
|-|-----|-----|--|
| e1    e2    e3 | - CE(S)
|----------------|
```

The following is true, iff each CSS has exactly one CE:

* if `(#CE(s) == 1)` is true for each `(s in S)`, then ...
* `ce-of-set()` is defined and unique for every `(s in S)`
* `set-of-ce()` allows to reliably retrieve each `(s in S)`

If each CSS has exactly one CE (i.e. `(#css(s) == 1)`), then
`U` and `S` have the same number of elements (i.e. `(#U == #S)`).

(1) `(#CSS(S) == #S)` is true.
That is because each set `(s in S)` has a unique non-empty CSS

(2) `(#CE(S) == #CSS(S))` is true.
That is because each CSS is required to have exactly one CE.

(3) `(#U == #S)` is true.
That is because `(#U == #CE(S) == #CSS(S) == #S)`.

* `(#U == #S)` is true, iff `(#CE(s) == 1)`

Due to the above `ce-of-set()` is then **inverse** to `set-of-ce()`.

* `(set-of-ce( ce-of-set(s) ) == s)` is true for each `(s in S)`
* `(ce-of-set( set-of-ce(ce) ) == ce)` is true for each `(ce in CE(S))`

<!-- ======================================================================= -->
## visual simplification iff (#CE(s) == 1)

```
S: normalized setup      S: compacted display
===================  =>  ====================
|-----------------|      |-1---------------|
| 1               |      | |-2-----------| |
| |-------------| |      | | |-3-| |-4-| | |
| | 2           | |      | | |---| |---| | |
| | |---| |---| | |      | |-------------| |
| | | 3 | | 4 | | |      |-----------------|
| | |---| |---| | |
| |-------------| |
|-----------------|
```

Since each set is now required to have exactly one CE, specific labels are no
longer required. That is because each CE can be understood as a label which
allows to uniquely identify the corresponding set. Visual representations can
therefore be compacted/condensed, if each CE is "highlighted" into the border
of the corresponding set.

Since even leaf sets are now required to have exactly one CE, and since these
sets have empty inner subsets, leaf sets appear as if they were empty. However,
if one recalls that no set in a setup is allowed to be empty, then one can still
conclude that each label must be the CE of the corresponding set.

Note that, in order to allow to distinguish one case (a specific label) from
the other (a CE is used as a label), one should not mix both cases into one
visual representation. That is, one should either use specific labels for all
sets, or use all the CEs as lables.
