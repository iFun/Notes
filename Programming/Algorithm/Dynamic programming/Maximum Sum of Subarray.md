# Kadane's algorithm

> Kadane’s Algorithm, aka Maximum Sum of Subarray, is an interesting algorithm problem that can be solved with different approaches. This problem is a nice and intuitive question to learn more about Dynamic Programming.

### Maximum Subarray Problem

The task is to find a subarray (contiguous elements) of the given array that has the largest sum. For instance:

```
[1, 5, -1, 0, 10]
```

The answer would be `15` or the entire array (it’s also a subarray)

### Solutions

Kadane’s algorithm is the answer to solve the problem with `O(n)` runtime complexity and `O(1)`space.

Following function shows the Kadane’s algorithm implementation which uses two variables, one to store the local maximum and the other to keep track of the global maximum:

```
def max_subarray(A):
    max_ending_here = max_so_far = A[0]
    for x in A[1:]:
        max_ending_here = max(x, max_ending_here + x)
        max_so_far = max(max_so_far, max_ending_here)
    return max_so_far
```

So we assume that the largest subarray is the first element, then we go through `A[1:]` elements (all elements except the first one).

At each step, what we do is:

- Can current element plus the last largest sum_ help to find a largest subarray (line 4)?
- If yes, update the `max_ending_here` or our local maximum, otherwise current element is the largest subarray (array of one).
- Then update the global maximum or `max_so_far` if there is a new global maximum.

When the loop is over, return the global maximum.

But that might be a bit unintuitive to grasp why `max_ending_here` is calculated. I rewrote that script this way:

```
def max_subarray(A):
    max_so_far = A[0]
    elements_so_far = [A[0]]

    for x in A[1:]:
        if x > sum(elements_so_far + [x]):
            elements_so_far = [x]
        else:
            elements_so_far.append(x)

        max_so_far = max(max_so_far, sum(elements_so_far))

    return max_so_far
```

The difference now is, instead of keeping a sum of contiguous elements we keep the actual elements such that:

- Assume the first item of our array is the maximum, so add it to `elements_so_far`
- Go through all elements except the first one
- Is the current element bigger that the sum of entire elements that we’ve seen? (i.e `sum(elements_so_far)`)
- If yes, reset the `elements_so_far` to this element, otherwise just keep adding items

I hope it makes a bit more sense now. Be aware that adding that array can increase the space complexity by O(n).

### Conclusion

Kadane’s algorithm is a [Dynamic Programming](https://en.wikipedia.org/wiki/Dynamic_programming) approach to solve “the largest contiguous elements in an array” with runtime of O(n). In this blog post we rewrote the algorithm to use an array instead of sum (which needs more space to hold them) that makes it a bit more easier to understand.