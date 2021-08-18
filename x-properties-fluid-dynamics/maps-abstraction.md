
doesn't really have to do with fluid dynamics
- fluids can be used to guide the flow of thoughts
  along the edges of a path from one node to another
- from one point of consideration to another
- a path is defined based upon discrete changes in height
- a path is not defined based on the fluid dynamics
- the latter is a consequence

# 3d to linear

- from a layered 3d world to paths over height diffs
- from 3d to corridors to paths

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
- narrow the 3d complexity down to a "linear" corridor
- with one spawner at one end, on the top of a hilld
  i.e. from a global maxima
- the fluid flowing down towards the other end
  i.e. to a global minima
- the ground defining the direction of flow
- still 3d, still too complex

abstraction - 3d as 2d
- abstracted as a 2d grid of cells
- each cell has a differential value
- fluid flows into adjacent cells with the lowest value

abstraction - linear paths
- starting with a creeper spawner beginn to draw a line
- along the direction of flow
- this line resembles a (rooted) path in a tree

# barriers, ends

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
