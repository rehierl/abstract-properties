
* Note that there is no pair of sequences that overlap each other.
* None of the borders of any two of the sequences cross each other.

Inconsistent setup
```
0 1 2 3 4 5 6 7 8 9 - A
  =======   ===     - B
```

* Sequence B is defined as `B = [1,2,3,4,6,7]`
* Sequence B is not continuous with regards to A.
* Sequence B has a gap because it does not contain `5`.
* Sequence B is not a subsequence of A.

Inconsistent setup
```
0 1 2 3 4 5 6 7 8 9 - A
    ===========     - C
            =====   - D
```

* Sequences C and D share the pattern `[6,7]`.
* Both sequences overlap each other.
* None of those two is a subsequence of the other.
* The borders of C and D cross each other.
