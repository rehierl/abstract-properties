
<!-- ======================================================================= -->
# 2-dimensional, height map

- take the trace of a doctree
- 1st dimension - the node index in that trace
- add a 2nd dimension - the node level
- can be split up into layers
- each layer contains all the nodes in that node level
- or - elevate according to the outline depth
- i.e. the node level within the section hierarchy

<!-- ======================================================================= -->
# 3-dimensional, landscape

- take the plane tree of a doctree
- i.e. layed out on a flat plane
- as such a 2-dimenasional object
- 1st dimension - node level
- 2nd dimension - a level-internal index of sorts
- 3rd dimension - elevate by node level
- i.e. elevate into the next upper layer
