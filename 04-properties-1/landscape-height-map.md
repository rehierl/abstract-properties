
- scopes amount to nodes
- scopes of nodes amount to sections
  by selecting a subset of scopes
- sections amount to outlines
- outlines amount to outline hierarchies
  by selecting a subsets of sections

can be used to explain
- generic properties - fluid dynamics
- an introduction to hierarchies

<!-- ======================================================================= -->
# landscape, height map

- a visual aid
- the height map of a document
- the landscape of a document

2d
- take the pre-order trace of a doctree
- 1st dimension - the node index in that trace
- add a 2nd dimension - the node level
- each layer contains all the nodes in that node level
- or - elevate according to the outline depth
- i.e. the node level within the section hierarchy

3d
- take a document tree
- lay it out on a flat plane
- as such a 2d object
- 1st dimension - node level
- 2nd dimension - a node index of sorts
- add a 3rd dimension - outline depth

similar to that
- mark/highlight the nodes within an induced subtree
  by elevating its nodes into the next layer

<!-- ======================================================================= -->
# a 3d example - game worlds

creeper world, a video game
- sarch https://youtu.be for "creeper world 4"
- ignore the gameplay mechanics
- here, these are mere visual clutter
- focus on the fluid dynamics instead
- "flat" 3d maps with creeper spawners
- spawners act as sources/roots for the creeper "fluid" (i.e. the enemy)
- the creeper flows along the height differentials of the map
- if the creeper covers the entire map, you loose the game/round

fluid dynamics
- just a visual analogy
- to visualize certain trains of thoughts
- don't expect it to be overly accurate

the game didn't invent ..
- fluid dynamics
- geographical maps
- logical layering

# overall remarks

sequences
- don't focus on the elements in each component
- each component has its own unqiue index
- the indexes allow to identify the elements
- a sequence corresponds with a set of distinct elements
- as such corresponds with an ordered set

remarks
- the timeline still seems to be useful
- to introduce generic properties
- reflect processing decisions (future)
- based upon available knowledge (past)

remarks
- fluid dynamics as introduced here
- to introduce hierarchies based on
  maps of layers of discrete height
  stacked ontop of each other

# abstractions - corridors, paths
- https://youtu.be/CWwdNWyBjQg?list=PLT3Q2Ltb5AnEsI2nX1ksYRUF-YLedXP7v&t=410

height differentials
- maps contain areas of different total height
- each area consists of layers stacked on top of each other
- all layers have the same discrete height
- overall, height changes are multiples of that height
- plus +n if the height increases
- minus -n if the height decreases
- express using differential changes?

consideration - downhill only
- if a spawner is located within a valley
- creeper will first fill that valley
- until it can "flow" over the borders
- ignore valleys, assume downhill only
- i.e. no local minima in that regards
- i.e. monotone decreasing height
- i.e. inverse node levels

abstraction - as a 3d corridor
- narrow the 3d complexity down to a corridor
- with one spawner at one end, on a hill top
- the fluid flowing down towards the other end
- the ground defining the direction of flow
- still 3d, still too complex

abstraction - 3d as 2d
- abstracted as a 2d grid of cells
- each cell has a weight, a differential value
- more like an absolute height value
- fluid flows into adjacent cells with a lower height value

abstraction - linear paths
- starting with a creeper spawner beginn to draw a line
- along the direction of flow
- this line resembles a (rooted) path in a tree

doesn't really have to do with fluid dynamics
- fluids can be used to guide the flow of thoughts
  along the edges of a path from one node to another
- from one point of consideration to another
- a path is defined based upon discrete changes in height
- a path is not defined based on the fluid dynamics
- the latter is a consequence

# barriers, ends
- https://youtu.be/p1vDlGKLAHw?list=PLT3Q2Ltb5AnEsI2nX1ksYRUF-YLedXP7v&t=575

can't flow past the end of the world
- not the real world - a game world - maps are finite
- maps have borders past which the creeper can not flow

if a path reaches a drop-off border
- then the path ends right there
- like a waterfall down a cliff, into oblivion
  out of the context of this discussion
- like a black hole (an ultimate sink),
  everything gets in, nothing gets out
- like a wall of infinite height

assumption
- each path begins at a spawner/source
- and ends at a border/sink

# initially, focus on monotone increasing paths
- https://youtu.be/Q-0Yu4sseLk?list=PLT3Q2Ltb5AnEsI2nX1ksYRUF-YLedXP7v&t=62

paths are considered to be monotone
- plus one ex-or minus one overall
- overall montone increasing/decreasing

assume monotone increasing
- since all layers have the same discrete height
- (+1) with each step/increase
- add up all heights, you get a node level

# height map, node levels
- https://youtu.be/Q-0Yu4sseLk?list=PLT3Q2Ltb5AnEsI2nX1ksYRUF-YLedXP7v&t=62

in regards to borders
- if at a current layer and at an overall level of (n)
- if that layer ends, then that does not mean a reamining height
  of (n-1) - i.e. not a total value minus a discrete change
- it means that the former layer's (+1) is no longer applicable
- i.e. add up all remaining heights - i.e. (+1)*(n-1),
  i.e. the discrete height of each layer multiplied by the
  number of remaining layers - i.e. those that still count
- you don't subtract what no longer exists,
  you add up what still exists
- the difference is subtle but essential

in regards to properties
- the corresponding path has ended
- the information defined on it is no longer relevant
- don't focus what no longer is
- don't focus what is not defined at a certain point
- foucs on what is truly defined,
  do not focus on what your mind adds on top of that

child order, ordered trees
- as visualized in general
- the child order is undefined
- an unordered tree is the only thing visible

partial orders
- similar to in-comparable elements
- they tend to be irritating due to the lack of definition
- but that is not what you should be focussing on

# colors, logical layers
- https://youtu.be/Q-0Yu4sseLk?list=PLT3Q2Ltb5AnEsI2nX1ksYRUF-YLedXP7v&t=647

crimson creeper
- existing creeper is at certain points injected with an additional property
- one that make the creeper immune to guns and mortars
- that property is added to the creeper, it isn't a different creeper
  that replaces the old one
- visualized by adding a pink color to the creeper
- the fluid dynamics continue seamlessly
- like using smoke to visualize aerodynamics

in addition to
- not isolated to that particular layer
- to some extent hereditary to further levels
- in general - other possibility - replacement,
  here not the case/focus
- here like the (+1) height differential of that layer

defining sections
- like marking a layer and all further layers with a color
- all belong to that section

hierarchies of sections
- mark node levels as logically relevant
- allow to focus on a reduced number of layers
- each marked layer - seen as holding its own content

hierarchies of documents
- certain layers - seen as holding its own document
