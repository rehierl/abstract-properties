
- continue here ...

# document order / conclusions

```
<root> ... <n> ................. </n> ... </root>
           |-all-of---------------->|-none-of-->|
           |-some-of--------------------------->|
```

Note that the end-tag of a node can be understood as a method to provide a
definition for the difficult-to-define **some-of** quantifier. That is, the
scope of a node contains a node and all of the nodes subsequent to it, but
none of the nodes that are subsequent to its end-tag.
