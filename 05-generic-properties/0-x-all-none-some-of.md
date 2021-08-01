
TODO
- all-of, none-of, some-of
- in regards to simple sets of elements
- point out the difficulty with some-of

TODO
- all-of, none-of, some-of in regards to the relationships between sets
- note the difference between this set-based context
  and the quantifiers in regards to sections
- (a section vs. a document) and (a section vs. a section)
- first, how a section is embedded into a document
- then, how a hierarchy of sections is established

intervals and the some-of operator
- `[a,b] := ( [a,*) & (*,b] )`
- i did expect `[a,b]` to be equivalent to `[a,*) \ (*,b)`,
  which is obviously not true (!)
- however, `( [a,*] \ [b,*] )` can still be described
  as defining some-of in terms of all-of and none-of
- i.e. some-of A* while none-of B* are allowed
- i.e. while all-of B* are disallowed
