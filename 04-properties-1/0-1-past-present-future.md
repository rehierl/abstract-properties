
<!-- ======================================================================= -->
# An analogy - a timeline

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
        current event ^ ---------> forward only
```

Given an infinte timeline with discrete timestamps, each of which represents a
certain event in time at which some implementation can access information and
execute one or more actions.

Based on that, one can imagine that the implementation travels from one point
in time to another in an orderly fashion while processing the corresponding
events. That is, the implementation is understood to only travel forwards in
time, never backwards.

With that in mind, one can imagine that the implementation is paused at some
point in time, before it has started to process the corresponding event.

<!-- ======================================================================= -->
## past, present, future

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
          <---------- ^ ----------->
          past     present    future
```

The current event at which the implementation was paused `(n5)` can be described
as the implementation's **current present**. Similar to that, all the events
that are presequent to the current event `(*,n4)` can be understood to comprise
the **current past**. Likewise, all the events that are subsequent to the current
event `(n6,*)`, i.e. those that the implementation still has to process, can be
understood to comprise the **current future**.

<!-- ======================================================================= -->
## forward only

Since the implementation has already processed those events that are presequent
to the current event, one needs to see the events in `(*,n4)` as being "done".
That is, there isn't a reason as to why the implementation would even want to
revisit those events.

And even if it wanted to travel back to (e.g.) event `(n2)`, the implementation
would then require the means to forget about all those events it has already
processed in between the current event `(n5)` and the event it intends to
travel back to (i.e. `(n3,n4)`). In some sense, the implementation would have
to be able to rewind some of the processing steps it has already executed.

In general, such a "rewind" is possible for an implementation, but needlessly
difficult to clearly define and implement. One would therefore need rock solid
reasons that allow to justify the additional complexity.

Because of that, a design that is expected to be in widespread use should not
make use of such processing steps. After all, these steps would make the design
needlessly difficult to communicate.

<!-- ======================================================================= -->
## knowledge based on past events

Similar to the issue with wanting to travel backwards in time is the issue about
the lack of knowledge of future events. That is, based on a given current event,
an implementation has no knowledge of any future event.

In order to choose which actions an implementation has to execute knowledge is
required. That knowledge can however not build upon those events that are yet
to come. After all, these events have not yet been reached and are as such
unknown. An implementation can therefore only build upon the knowledge it has
gained from past events.

However, one could in general assume that, given a certain sequence of past
events, some specific future event might happen with some certainty. Based on
that assumption, an implementation could be tempted to execute certain actions
in the hopes that the predicted event will eventually be reached at some point
in the current future.

The issue with that is however, that the predicted future event can not be
guaranteed to even exist. (In that regards, one just needs to think of random
input errors). With that in mind, and if the implementation would eventually
be able to detect that the event which was predicted in the past wasn't
actually encountered, the implementation would then have to rewind to the
event at which the prediction was mand. That in order to fix the inconsistent
outcome.

Because of that, a design that is expected to be in widespread use should not
make use of such predictions. After all, these steps would make the design
needlessly difficult to communicate.

<!-- ======================================================================= -->
## conclusions

```
- n1 - n2 - n3 - n4 - n5 - n6 - n7 - n8 - n9 ->
          <---------- ^ ----------->
          context   current    scope
```

Due to the above, and since an implementation can be thought of as being paused
at some current point in time, one can make the following statements in regards
to what an implementation can and can not do.

(**I1**) An implementation knows about past events. Based on that, it can
be assumed to know which events have occurred and which actions it took in
response to these events.

(**I2**) An implementation knows about the current event. Because of that,
it can take the knowledge it gained from the current event into account
when chosing which actions to take in response to that event.

Note that the knowledge an implementation gained from past events, and the
actions it took in the past, including the knowledge it gained from the
current event, will in general be referred to as the implementation's
**(current) context**.

Note that the knowledge of the current event can be described to introduce
some **reflexivity**. Based on that, certain actions may affect other actions
that are to be executed at the current point in time. This does for example
allow an implementation to associate a sectioning node with the section it
declares.

(**I3**) The actions an implementation chooses to execute in response to the
current event can only be taken into account when an implementation has to
decide which other actions to execute in response to the current event, and
when deciding which actions to execute in response to some future event.

Note that the amount of events that may take some action into account, can
be described as the action's **scope**. Since the current context does also
include the current event, the context of an implementation can be understood
to overlap the scope of a current action in the current event.

(**I4**) Not every bit of knowledge gained from the current event and from
past events must be taken into account when deciding which actions to execute
in response to some current event. Put differently, an action taken in the
past may have no effect on any of the future events.

Note that I4 is not meant to express that an implementation can freely choose
which bits of information it chooses to use, and which bits of information it
chooses to ignore. After all, depending on its purpose an implementation is
requried to follow certain rules. Rules for example which tell that a certain
section has already ended.
