---
source: sources/wiki-Counting_sort.md
source_url: https://en.wikipedia.org/wiki/Counting_sort
---

## Counting Sort: A Linear-Time Integer Sorting Algorithm

Counting sort is a non-comparison-based integer sorting algorithm that sorts a collection of objects by counting occurrences of each distinct key value, then using prefix sums to place each element in its correct output position. It runs in O(n + k) time where n is the number of items and k is the range of key values, making it efficient when k is not significantly greater than n. Invented by Harold H. Seward in 1954, it is most commonly used as a subroutine in radix sort.

## Key Concepts

- **Non-comparison sort**: Does not compare elements against each other; uses key values as array indices, bypassing the Omega(n log n) lower bound for comparison sorts
- **Time complexity**: O(n + k) in all cases, where n = number of items, k = maximum key value
- **Space complexity**: O(n + k) — requires a count array of size k+1 and an output array of size n
- **Stability**: Counting sort is a stable sort — elements with equal keys preserve their relative input order (critical for its use in radix sort)
- **Three-phase algorithm**:
  1. **Histogram phase**: Count occurrences of each key value
  2. **Prefix sum phase**: Compute cumulative counts to determine output positions
  3. **Placement phase**: Iterate input in reverse order, placing each element at its computed position (reverse iteration preserves stability)
- **Not a comparison sort**: The Omega(n log n) comparison-sort lower bound does not apply
- **Not in-place**: Requires separate input and output arrays (an in-place variant exists but sacrifices stability)
- **Key constraint**: Keys must be non-negative integers; works best when key range k is small relative to n
- **Comparison with bucket sort**: Bucket sort achieves similar time bounds but requires linked lists or dynamic arrays per bucket; counting sort stores only a single count per bucket

## Commands and Syntax

**Pseudocode:**
```
function CountingSort(input, k):
    count ← array of k + 1 zeros
    output ← array of same length as input

    // Phase 1: Build histogram
    for i = 0 to length(input) - 1 do
        j = key(input[i])
        count[j] = count[j] + 1

    // Phase 2: Prefix sum
    for i = 1 to k do
        count[i] = count[i] + count[i - 1]

    // Phase 3: Place elements (reverse for stability)
    for i = length(input) - 1 down to 0 do
        j = key(input[i])
        count[j] = count[j] - 1
        output[count[j]] = input[i]

    return output
```

**Simplified variant** (when items are themselves integer keys): Combine phases 2 and 3 — after counting, append `count[i]` copies of `i` to output.

**Duplicate elimination variant**: Replace count array with a bit vector; a `1` at position i indicates key i is present. Output is the set of positions with non-zero bits.

## Relationships

- **Radix sort**: Counting sort is the standard subroutine for each digit pass in radix sort; stability is essential here so that earlier digit orderings are preserved
- **Bucket sort**: Similar time complexity but requires linked lists or dynamic arrays per bucket rather than simple counts
- **Comparison sorts** (quicksort, mergesort, heapsort): Counting sort breaks the Omega(n log n) lower bound by not comparing elements, but is limited to integer keys with bounded range
- **Integer sorting**: Counting sort is a specific instance of the integer sorting problem
- **Prefix sum**: The second phase of counting sort is a prefix sum computation, a primitive that is also independently important in parallel algorithms
- **Parallel algorithms**: Counting sort parallelizes well — split input into subarrays, compute per-subarray counts, merge count arrays; prefix sum is inherently parallelizable

## Exam-Relevant Points

- **O(n + k) time and space** — know both and what n and k represent
- **Not a comparison sort** — therefore the Omega(n log n) lower bound does not apply
- **Stability is guaranteed** (standard version) — the reverse-order traversal in phase 3 is what makes it stable
- **When to use**: Only efficient when k (key range) is not significantly greater than n; impractical for large key ranges
- **In-place variant loses stability** — a common exam trap
- **Radix sort dependency**: Counting sort must be stable to serve as the digit-sorting subroutine in radix sort
- **Three distinct phases**: histogram, prefix sum, placement — know what each does and why
- **Unlike bucket sort**: Stores a single integer per bucket rather than a collection of items
- **Inventor**: Harold H. Seward, 1954 (also credited with applying it to radix sort)
- **Key must be computed first if unknown**: An extra O(n) pass to find max key value does not change overall complexity
