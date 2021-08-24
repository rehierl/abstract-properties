
<!-- ======================================================================= -->
## order of scopes => node tree

```
S: a rooted normalized setup                   T: a node tree
=========================================  =>  ==============
|---------------------------------------|            1
| 1                                     |         -------
| |-------------| |---| |-------------| |         2  5  6
| | 2           | | 5 | | 6           | |      ----     ----
| | |---| |---| | |---| | |---| |---| | |      3  4     7  8
| | | 3 | | 4 | |       | | 7 | | 8 | | |
| | |---| |---| |       | |---| |---| | |
| |-------------|       |-------------| |
|---------------------------------------|
```

Provided that a given setup of sets `S` has (1) one root set only, and (2)
a unique node identifier as the CE of each set, one can use `S` to form an
order of scopes `P(S,<)` ..

* `P(S,<)` where ..
* `(a < b) := (a superset-of b) for (a,b in S)`

.. and also a node tree `T(N,E)`.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-set-of b) for (a,b in S) }`

Note that labels are no longer required since the single CE of each set allows
to identify the corresponding set. The CE of each set can therefore be used as
a unique label for the corresponding set. Because of that, the visual
representation can be compacted:

```
S: a rooted normalized setup                   T: a node tree
=========================================  =>  ==============
|-1-------------------------------------|            1
| |-2-----------| |-5-| |-6-----------| |         -------
| | |-3-| |-4-| | |---| | |-7-| |-8-| | |         2  5  6
| | |---| |---| |       | |---| |---| | |      ----     ----
| |-------------|       |-------------| |      3  4     7  8
|---------------------------------------|
```

Note that leaf sets only appear to be empty. The CE of each set is in this
visualization elevated into the position of a label. However, in contrary
to before each CE remains to be an element of the corresponding set.
