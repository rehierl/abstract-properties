
<!-- ======================================================================= -->
## (Ex-8) a removal from an ordered tree: keep c(n) instead

In theory, one could drop `s(n)` instead and hold on to `c(n)`. However, since
the focus of this discussion is on the pre-order traversal of an ordered tree,
this case will not be taken into further consideration. That is because it
seems to require even more changes (e.g. a different type of traversal, i.e.
level-order?).

```
S               =>                        => S*
============================================================
( p -|-> s(p) ) => ( p -|-> s(p)        ) => ( p -|-> s(p) )
     |-> c(p)           |-> n -|-> s(n)           |-> c(n)
                               |-> c(n)
```

* `p` will have `c(n)` as its new sequence of former child nodes

```
S                 =>                         => S*
=================================================================
( ps -|-> s(ps) ) => ( ps -|-> n -|-> s(n) ) => ( ps -|-> c(n)  )
      |-> c(ps)            |      |-> c(n)            |-> c(ps)
                           |-> c(ps)
```

* can `c(n)` act as a sequence of subsequent siblings to `ps`?
* that is quite odd ...
