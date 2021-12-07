
<!-- ======================================================================= -->
# hierarchy of scopes (Hs) <=> hierarchy of rpaths (Hrp)

Even though one can first transform any hierarchy of rooted paths `Hrp` into
a node tree `T(N,E)`, and then into a hierarchy of scopes `Hs`, one can also
directly transform `Hrp` into `Hs`. Likewise, a direct transformation of `Hs`
into `Hrp` is possible.

<!-- ======================================================================= -->
## (Hs => Hrp)

Recall that each set `(s in Hs)` in a hierarchy of scopes `Hs` has a unique
rooted path `rp(s)`. In addition to that, each set in `Hs` is required to have
one and only one CE, which can be understood to denote the node a set represents.
Because of that, `rp(s)` can be transformed such that each element in it is the
CE of the corresponding set. That is, the rooted path of each set in Hs can be
directly transformed into a rooted path of nodes.

* `Hr := { rpath(s) | (s in Hs) }` where ..
* `rpath(s) := (ce(s1),..,ce(sN))` and `rp(s) := (s1,..,sN)`
* note - `rp(s)` is over `Hs`

Note that ..

* `(rpath(s) == rp(n))` where `n := ce(s)`
* note - `rp(n)` is over `T`

<!-- ======================================================================= -->
## (Hrp => Hs)

```
rp(b) := (r  ..  a  ..  b)
         |-------|-------|
          rp(a)   p(a,b)
```

In order to transform Hrp into Hs, one needs to recall the general pattern of
the rooted path of some node `b` that has node `a` as an ancestor. That is,
each rooted path `rp(b)` has the rooted paths of each of its ancestors `rp(a)`
as a prefix, and path `p(a,b)` as a suffix.

* `rp(b) := (rp(a) \ (a)) × p(a,b)`

Note that `rp(a)` and `p(a,b)` overlap each other in ancestor `a`. That is,
`(a)` is a suffix to `rp(a)` and a prefix to `p(a,b)`. After all, paths in a
tree are formed by connecting the edges in a source tree.

Due to the above, and in order to form the scope of node `a` from the rooted
paths in Hrp, one first needs to restrict Hrp to those paths that contain `a`
as an element. After that, all paths need to be reduced such that they all
begin in `a`. As such, `Hrp(a)` can be understood to correspond with all the
rooted paths of the induced subtree `T[a]` that have `a` as their root. The
universal set `U()` of `Hrp(a)` is therefore equal to the scope of node `a`.

* `Hs := { U(Hrp(a)) | (a in U(Hrp)) }`
* `U(Hrp)` - the universal set of elements of the setup of rpaths
* `Hrp(a)` - the set of all rooted paths in the induced subtree `T[a]`

<!-- ======================================================================= -->
## (Hrp => Hs) in pseudocode

The following pseudocode fragment showcases a rudimentary direct approach.

```js
getHsFromHrp(hr) begin
  //- the resulting setup of scopes
  hs = new set()

  foreach (a in U(hr)) begin
    //- initialize the scope of node 'a'
    ha = new set()
    ha.add( a )

    foreach (r in hr) begin
      //- find node 'a' in path 'r'
      ia = idx(r, a)

      //- ignore rooted path 'r',
      //  if 'a' is no node in it
      if(ia < 1) begin
        continue
      end

      //- add each successor/descendant
      //  of 'a' in 'r' to 'ha'
      for (i=ia+1; i<#r; i++) begin
        ha.add( r[i] )
      end
    end

    //- add the scope of 'a' to the setup
    hs.add( ha )
  end

  return hs
end
```

Note that optimizations are obviously possible. After all, once one has a valid
offset of a certain node in a rooted path, then that node will have the exact
same index in every rooted path to which that node is an element. Because of
that, the index of that node could be cached in a hashtable, which is why one
would not have to actually search each rooted path for a specific node. That
is, once the index of a node is known, one would only have to test a subsequent
rooted path, if that node is at the known index.
