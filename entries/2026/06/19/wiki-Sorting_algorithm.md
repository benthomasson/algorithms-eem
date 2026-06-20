---
source: sources/wiki-Sorting_algorithm.md
source_url: https://en.wikipedia.org/wiki/Sorting_algorithm
---

## Sorting Algorithms: Classification, Complexity, and Practical Usage

Sorting algorithms arrange elements of a list into a defined order (numerical, lexicographical, ascending, or descending). They are foundational to computer science because efficient sorting optimizes downstream algorithms like search and merge. The output must satisfy two conditions: monotonic ordering and being a permutation of the input. This page covers classification criteria, stability, comparison vs. non-comparison sorts, complexity tables, and practical algorithm selection.

## Key Concepts

- **Formal requirements**: A correct sort produces (1) a monotonically ordered output and (2) a permutation of the input
- **Comparison sort lower bound**: No comparison sort can do better than O(n log n) on average; the information-theoretic lower bound is n log n − 1.4427n + O(log n) comparisons
- **Non-comparison sorts** (counting sort, radix sort, bucket sort) can break the O(n log n) barrier by exploiting key structure
- **Stability**: A stable sort preserves the relative order of records with equal keys; critical when sorting by multiple keys sequentially (e.g., sort by name, then stable sort by section preserves name order within each section)
- **In-place**: Strictly requires only O(1) extra memory; O(log n) is sometimes considered in-place
- **Adaptivity**: Adaptive sorts exploit existing order in the input (e.g., Timsort, Smoothsort achieve O(n) on already-sorted data)
- **Online sorting**: Algorithms like insertion sort can process input as it arrives without needing the full dataset upfront
- **Classification axes**: computational complexity (best/average/worst), memory usage, recursion, stability, comparison vs. non-comparison, method (insertion/exchange/selection/merging/partitioning), serial vs. parallel, adaptivity, online capability

## Commands and Syntax

No CLI commands per se, but key complexity signatures for algorithm selection:

- **O(n log n) guaranteed** (worst case): Heapsort, Merge sort, Timsort, Introsort
- **O(n log n) average, O(n^2) worst**: Quicksort, Library sort
- **O(n^2) average**: Insertion sort, Selection sort, Bubble sort, Shell sort (gap-dependent)
- **O(n) best case** (adaptive): Timsort, Block sort, Smoothsort, Cubesort, Insertion sort
- **Non-comparison O(n+k) or O(n·k/d)**: Counting sort, Radix sort (LSD/MSD), Bucket sort
- **Hybrid patterns**: Timsort = merge sort + insertion sort; Introsort = quicksort + heapsort + insertion sort

## Relationships

- **Search algorithms** depend on sorted input (binary search requires sorted array)
- **Merge algorithms** both use and are used by sorting (merge sort relies on merging; merge operations need sorted sublists)
- **Radix sort** leverages stable sorting as a subroutine (each digit pass must be stable)
- **Heaps** (data structure) underpin heapsort and tournament sort
- **Binary search trees** underpin tree sort; self-balancing BSTs guarantee O(n log n) worst case
- **Divide-and-conquer** paradigm connects to merge sort and quicksort
- **Parallel computing**: Merge sort is highly parallelizable (O(log n) with Three Hungarians' Algorithm); samplesort parallelizes non-comparison sorts via bucket distribution
- **Canonicalization** uses sorting to produce canonical forms of data

## Exam-Relevant Points

- Comparison sorts **cannot** beat O(n log n) average-case — this is a proven lower bound
- **Quicksort**: O(n log n) average, O(n^2) worst; in-place with O(log n) stack space; **not stable**
- **Merge sort**: O(n log n) all cases; requires O(n) extra memory; **stable**; highly parallelizable
- **Heapsort**: O(n log n) all cases; O(1) memory; **not stable**; in-place
- **Timsort**: O(n) best, O(n log n) average/worst; O(n) memory; **stable**; used in Python, Java, Android
- **Introsort**: O(n log n) all cases; used in C++ STL; **not stable**
- **Counting sort**: O(n+r) time and space; **stable**; only works when range r is O(n)
- **Radix sort (LSD)**: O(n·k/d) all cases; **stable**; can sort non-integers unlike most distribution sorts
- Stability matters when performing multi-key sorts sequentially — a stable sort on the secondary key preserves the primary key ordering
- Making an unstable sort stable is possible by extending the key with original position, at the cost of additional time and space
- **Selection sort** makes exactly n−1 swaps (optimal for expensive writes) but is O(n^2) in all cases
- **Insertion sort**: O(n+d) where d is the number of inversions; preferred for small or nearly-sorted data
- Practical implementations use **hybrid algorithms**: asymptotically efficient sorts for overall structure, insertion sort for small sublists at recursion base cases
- **Block sort**: the only O(1) memory, stable, O(n log n) comparison sort (combines in-place merge with bottom-up merge sort)
