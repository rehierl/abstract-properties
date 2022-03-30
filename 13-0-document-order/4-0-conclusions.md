
<!-- ======================================================================= -->
# conclusions

The following summarizes the conclusions that can be drawn based on the inner
structure of the tag-based syntax.

<!-- ======================================================================= -->
## a method to define a some-of quantifier

```
<root> ... <n> ................. </n> ... </root>
           |-some-of--------------------------->|
           |-all-of---------------->|-none-of-->|
```

Note that the end-tag of a node can be understood as a method to define a
**some-of** quantifier. In particular, the scope of a node contains a node
and all of the nodes subsequent to it, but none of the nodes that are
subsequent to its end-tag.

<!-- ======================================================================= -->
## a tag soup ain't no document tree

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n------------------------------------------>|
       |-fc------->|    |-lc--------------->|
                                |-l-->|
```

Note that the tag soup of a document embeds the edges of a document tree into
the relationships between the scopes it defines. The tag soup of a document
does therefore not define an actual tree. Instead, the tag soup of a document
tree **defines a partial containment order** (i.e. **DI-RE**). As a matter of
consequence hand-written documents must be **well-formed**.

Note that the tag-based syntax does in principle allow to define **overlapping**
scopes. However, such scopes can not be used to define a document tree since
the containment order defined by such a tag soup is **no hierarchy of scopes**.
