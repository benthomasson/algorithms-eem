---
source: sources/wiki-Merge_sort.md
source_url: https://en.wikipedia.org/wiki/Merge_sort
---

I'll create the study notes entry for merge sort.

## Merge Sort — Divide-and-Conquer Sorting Algorithm

Merge sort is an efficient, general-purpose, comparison-based sorting algorithm that uses the divide-and-conquer strategy. Invented by John von Neumann in 1945, it works by recursively dividing an unsorted list into single-element sublists, then repeatedly merging sublists to produce sorted output. Most implementations are stable (preserving relative order of equal elements). It guarantees O(n log n) performance in all cases — worst, average, and best — at the cost of O(n) auxiliary space for array implementations.

## Key Concepts

- **Divide-and-conquer**: Split the list into halves recursively until sublists contain one element (base case), then merge sorted sublists back together.
- **Stability**: Most implementations are stable — equal elements retain their original relative order.
- **Recurrence relation**: T(n) = 2T(n/2) + n, solved by the master theorem to give O(n log n).
- **Two main implementations**: Top-down (recursive) and bottom-up (iterative). Top-down splits recursively; bottom-up starts with runs of size 1 and doubles each pass.
- **Not in-place** (standard implementation): Requires O(n) auxiliary space for arrays. Linked-list implementations need only O(1) auxiliary space.
- **Comparison with quicksort**: Merge sort's worst case uses ~39% fewer comparisons than quicksort's average case. Merge sort guarantees O(n log n); quicksort degrades to O(n²) worst case.
- **Sequential access advantage**: More efficient than quicksort when data can only be accessed sequentially (e.g., linked lists, tapes).
- **Sorting numbers**: The exact worst-case comparison count is given by n⌈lg n⌉ − 2^⌈lg n⌉ + 1 (approximately).

## Commands and Syntax

**Top-down merge sort (recursive, array-based):**
```
topDownMergeSort(a, b, n):
  copyArray(a, 0, n, b)
  topDownSplitMerge(a, 0, n, b)

topDownSplitMerge(a, begin, end, b):
  if end - begin <= 1: return
  middle = (begin + end) / 2
  topDownSplitMerge(b, begin, middle, a)   // sort left into a
  topDownSplitMerge(b, middle, end, a)     // sort right into a
  topDownMerge(b, begin, middle, end, a)   // merge from b into a
```

**Bottom-up merge sort (iterative, array-based):**
```
for width = 1; width < n; width *= 2:
  for i = 0; i < n; i += 2 * width:
    bottomUpMerge(a, i, min(i+width, n), min(i+2*width, n), b)
  copyArray(b, a, n)
```

**Merge procedure (core operation):**
```
merge(left, right):
  while left and right not empty:
    if first(left) <= first(right): append first(left)
    else: append first(right)
  append remaining elements from whichever list is non-empty
```

**Natural merge sort** exploits pre-existing sorted runs in the input, reducing passes needed. Best case (already sorted): O(n) with a single pass.

## Relationships

- **Divide-and-conquer paradigm**: Merge sort is the canonical example, alongside quicksort and binary search.
- **Timsort**: Python's and Java's default sort. Uses natural merge sort as a key component, exploiting naturally occurring runs.
- **External sorting**: Merge sort is the basis for sorting data too large for memory, using tape drives or disk (polyphase merge sort, k-way merge).
- **Quicksort**: Main competitor. Quicksort is typically faster in practice (better cache behavior, in-place) but lacks worst-case guarantee and stability.
- **Insertion sort**: Used as base case in optimized merge sort (tiled merge sort) for small subarrays to improve cache performance.
- **K-way merge algorithm**: Generalization used in parallel and external merge sort variants.
- **Block merge sort**: A stable, in-place O(n log n) variant addressing merge sort's space overhead.
- **Parallel algorithms**: Merge sort parallelizes naturally; with parallel merging, achieves span O(log³ n) and parallelism Θ(n / (log n)²).

## Exam-Relevant Points

- **Time complexity**: O(n log n) in ALL cases — worst, average, and best. The natural variant achieves Ω(n) best case.
- **Space complexity**: O(n) auxiliary for arrays; O(1) auxiliary for linked lists (plus O(log n) stack space).
- **Stable**: Yes (most implementations). This is a key differentiator from quicksort and heapsort.
- **Recurrence**: T(n) = 2T(n/2) + n → O(n log n) via the master theorem.
- **Not in-place** by default. In-place variants exist but add complexity (O(n log² n) time or high constant factors).
- **Better than quicksort for**: linked lists, sequential-access data, guaranteed worst-case performance, stability requirement.
- **Worse than quicksort for**: cache performance on arrays (quicksort has better locality), space usage.
- **External sorting**: Merge sort is the standard algorithm for external sorting with tape/disk drives. Basic 4-tape version requires log₂(n) passes.
- **Parallel merge sort with parallel merge** achieves span Θ(log³ n) and work O(n log n).
- **Bottom-up vs top-down**: Same asymptotic complexity; bottom-up avoids recursion overhead; top-down is more naturally expressed.
- **Tiled merge sort**: Cache-aware optimization that uses insertion sort for subarrays fitting in cache, then standard merge sort above that level.
- **Space reduction to n/2**: By only copying the left half to temporary space and merging in-place into the original array.
