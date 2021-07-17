
<!-- ======================================================================= -->

clear vs. unclear definitions
- point out the core issue/problem with unclear instructions
  i.e. all-of or none-of vs. some-of

the some-but-not-all qualifier
- using venn diagrams it is easy to recognize overlapping sets
- it is however anything but easy to provide clear definitions
  for overlapping sets/scopes
- after all, how does one clearly (unambiguously, efficiently)
  define that "some, but not all" are included
- how can a definition allow implementations to distinguish
  between "included" and "not included"?
- as it turns out, an end-tag does provide a clear definition
  for the some-but-not-all qualifier

point out that it is in general inherently difficult to define overlapping sets
of elements (i.e. a "some, but not all" qualifier) - one can't in general draw
the line (i.e. which elements are included, which ones are not) - one needs
additional context to make such a determination - in contrary to that, no such
context is required to state "all of the elements" and "none of the elements"

the bigger issue is with having to determine "the parent set" of an element
- what is the parent set of an element in the intersection of two overlapping
sets of elements - that can not be determined since both overlapping sets are
equally relevant to such an element
