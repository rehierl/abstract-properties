
Hlvl
- a herarchy of level values (lvl-rps)
- explain - Hlvl <-> HrsSer <-> HrpSer
- explain - Hlvl <-> Hlen

the last element of a rooted path
- is the path's CE - `ce(s) = s[#s]`
- while deserializing a tree, `#s`
  tells where to place the next element
- `#s` is the element's node level

node levels as rank values
- a non-tag based notation
- a sequence of rank values

level values vs. rank values
- level values count the number of open scopes
- as instructions to end/close the corresponding scopes
- if generated, they can be relied upon
- not much different to rank values
- level values are absolute

a sequence of level values reflects a height-map
- seems like that would be helpful for explanations
- could be transformed into a length-based encoding?
