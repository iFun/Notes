# Boyer–Moore majority vote algorithm

> The **Boyer–Moore majority vote algorithm** is an [algorithm](https://en.wikipedia.org/wiki/Algorithm) for finding the [majority](https://en.wikipedia.org/wiki/Majority) of a sequence of elements using [linear time](https://en.wikipedia.org/wiki/Linear_time) and constant space.

The algorithm maintains in its [local variables](https://en.wikipedia.org/wiki/Local_variable) a sequence element and a counter, with the counter initially zero. It then processes the elements of the sequence, one at a time. When processing an element *x*, if the counter is zero, the algorithm stores *x* as its remembered sequence element and sets the counter to one. Otherwise, it compares *x* to the stored element and either increments the counter (if they are equal) or decrements the counter (otherwise). At the end of this process, if the sequence has a majority, it will be the element stored by the algorithm. This can be expressed in [pseudocode](https://en.wikipedia.org/wiki/Pseudocode) as the following steps:

- Initialize an element *m* and a counter *i* with *i* = 0
- For each element x of the input sequence:
  - If *i* = 0, then assign *m* = *x* and *i* = 1
  - else if *m* = *x*, then assign *i* = *i* + 1
  - else assign *i* = *i* − 1
- Return *m*