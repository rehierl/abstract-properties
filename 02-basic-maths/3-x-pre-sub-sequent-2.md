
Note that, at the time of writing, it is unclear if the following definitions
(in regards to ordered sequences of nodes) will be of any use.

* Kept in regards to past content.
* Kept in regards to communicate a certain way of thinking.
* May be modfied or even dropped at some point.

Note that "presequent" is dual to "subsequent". Because of that, the following
definitions will be reduced to one case only. The other case can be thought of
as being defined accordingly.

Note also, that (in here only) the word "subsequence" is used as a synonym for
"substring" (a past point of view that is no longer supported). This in regards
to the overall focus on substrings rather than on less strict and more general
definition.

<!-- ======================================================================= -->
## sequences subsequent to a node

```
              |-t-------
s := n1 n2 n3 | n4 n5 n6 ...
              |---------
```

Subsequence `t` can be described as
**a sequence that is (loosely) subsequent to `n2`**,
since the 1st node `n4` of `t` is subsequent to `n2`.

`t` can be thought of as
**a sequence that is strictly subsequent to `n3`**,
since the 1st node `n4` is strictly subsequent to `n3`.

<!-- ======================================================================= -->
## nodes subsequent to a sequence

```
      |-t--------|
n1 n2 | n3 n4 n5 | n6 n7
      |----------|
```

Note that "left" is in regards to the last node of a sequence and understood to
imply that a denoted node is within the corresponding sequence. In that regards
"right" is more strict (i.e. outside, subsequent to all the nodes in the sequence).

Node `n4` can be described as being **left-subsequent** or **(loosely) subsequent**
to subsequence `t` since it is at least subsequent to the first node of `t`.

Node `n7` can be described as being **right-subsequent** or **strictly subsequent**
to `t` since it is subsequent to all the nodes in that sequence.

<!-- ======================================================================= -->
## sequences subsequent to a sequence

```
      |-s--------------|    |-t---
n1 n2 | n3 n4 n5 n6 n7 | n8 | n9
      |----------------|    |-----
```

* to be defined ...
* a sequence that is left subsequent to a sequence
* a sequence that is strictly left subsequent to a sequence
* a sequence that is loosely left subsequent to a sequence
* dual to that the cases of "right subsequent"

Note that these definitions seem to be too complicated to allow for clear
descriptions in regards to subsequent discussions.
