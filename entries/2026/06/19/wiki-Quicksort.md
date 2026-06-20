---
source: sources/wiki-Quicksort.md
source_url: https://en.wikipedia.org/wiki/Quicksort
---

I'll create a study entry for Quicksort.

## Quicksort: Divide-and-Conquer Sorting Algorithm

Quicksort is a comparison-based, divide-and-conquer sorting algorithm developed by Tony Hoare in 1959. It works by selecting a pivot element, partitioning the array into elements less than and greater than the pivot, then recursively sorting the sub-arrays. It is an in-place algorithm (requiring only small additional memory) and is generally slightly faster than merge sort and heapsort for randomized data. Most implementations are **not stable**.

## Key Concepts

- **Divide and conquer**: Select a pivot, partition around it, recurse on sub-arrays
- **Average case**: O(n log n) comparisons
- **Worst case**: O(n²) — occurs with poor pivot selection on sorted/reverse-sorted input or all-equal elements (Lomuto scheme)
- **Best case**: O(n log n) with simple partition; O(n) with three-way partition and equal keys
- **Space complexity**: O(n) auxiliary naive; O(log n) auxiliary with Hoare's 1962 optimization (tail-call into larger partition)
- **Not optimal**: There exist sorting algorithms with better worst-case guarantees
- **Comparison sort**: Only requires a total order (less-than relation) on elements
- **Not stable**: Relative order of equal elements is not preserved
- **Two major partition schemes**: Lomuto and Hoare, with significantly different performance characteristics

## Commands and Syntax

**Lomuto Partition Scheme** — pivot is last element; single scan index `j` with boundary index `i`:
```
algorithm partition(A, lo, hi):
  pivot := A[hi]
  i := lo
  for j := lo to hi - 1 do
    if A[j] <= pivot then
      swap A[i] with A[j]
      i := i + 1
  swap A[i] with A[hi]
  return i
```
- Simpler to understand and prove correct
- **3x more swaps** on average than Hoare
- Degrades to O(n²) on already-sorted arrays and all-equal elements
- Recurse on `(lo..p-1)` and `(p+1..hi)` — pivot excluded from both

**Hoare Partition Scheme** — two pointers converge from both ends:
```
algorithm partition(A, lo, hi):
  pivot := A[lo]
  i := lo - 1; j := hi + 1
  loop forever:
    do i := i + 1 while A[i] < pivot
    do j := j - 1 while A[j] > pivot
    if i >= j then return j
    swap A[i] with A[j]
```
- More efficient: 3x fewer swaps on average
- Produces balanced partition even when all values are equal
- Pivot's final location is **not** necessarily at the returned index
- Recurse on `(lo..p)` and `(p+1..hi)` — pivot included in left half
- Must return `j` (not `i`) and use floor-based pivot to avoid infinite recursion

**Three-Way Partition (Dutch National Flag)** — handles repeated elements in O(n):
```
algorithm partition(A, lo, hi):
  pivot := A[(lo+hi)/2]
  lt := lo; eq := lo; gt := hi
  while eq <= gt:
    if A[eq] < pivot: swap A[eq], A[lt]; lt++; eq++
    elif A[eq] > pivot: swap A[eq], A[gt]; gt--
    else: eq++
  return lt, gt
```
- Returns two indices: bounds of the equal-to-pivot region
- Achieves O(n) when all elements are equal
- Recurse on `(lo..lt-1)` and `(gt+1..hi)`

**Median-of-Three Pivot Selection**:
```
mid := floor((lo + hi) / 2)
if A[mid] < A[lo]: swap A[lo], A[mid]
if A[hi] < A[lo]: swap A[lo], A[hi]
if A[mid] < A[hi]: swap A[mid], A[hi]
pivot := A[hi]
```
- Reduces expected comparisons from 1.386n log n to ~1.188n log n
- **Ninther** (pseudomedian of nine): median of three medians-of-three, used for larger arrays

## Relationships

- **Merge sort / Heapsort**: Fellow O(n log n) comparison sorts; quicksort is slightly faster in practice on random data but has worse worst-case
- **Insertion sort**: Used as a fallback for small sub-arrays (threshold ~10 elements); also quicksort's historical predecessor in Hoare's work
- **Dutch National Flag Problem**: The three-way partition solves this problem; critical for handling repeated elements
- **Introsort**: Hybrid that starts with quicksort but switches to heapsort when recursion depth exceeds O(log n), guaranteeing O(n log n) worst case
- **Divide-and-conquer paradigm**: Quicksort is a canonical example alongside merge sort and binary search
- **C standard library `qsort`**: Named after quicksort; Unix adopted it as the default library sort
- **Samplesort**: Generalization studied in Sedgewick's 1975 PhD thesis
- **Comparison sort lower bound**: Quicksort's O(n log n) average matches the theoretical lower bound for comparison sorts

## Exam-Relevant Points

- **Average O(n log n), worst O(n²)**: The worst case is rare with good pivot selection but cannot be eliminated entirely (without hybrid approaches)
- **Lomuto vs. Hoare**: Hoare does 3x fewer swaps; Lomuto degrades to O(n²) on equal elements while Hoare produces balanced partitions
- **Space complexity**: O(log n) auxiliary when recursing into the smaller partition first (tail-call optimization); O(n) without this optimization
- **Not stable**: Cannot preserve relative order of equal elements in standard implementations
- **Pivot selection matters for correctness of termination**: With Hoare's scheme, returning `j` requires floor-based pivot; returning `i` requires ceiling-based pivot. Mismatching causes infinite recursion
- **Three-way partition achieves O(n) on all-equal input** — the best case with this variant
- **Median-of-three reduces comparisons by ~14%** (1.386 to 1.188 coefficient on n log n)
- **Overflow hazard**: Computing `(lo + hi) / 2` can overflow; use `lo + (hi - lo) / 2` instead
- **Practical optimizations**: Switch to insertion sort below threshold (~10 elements); recurse into smaller partition first for O(log n) stack depth; three-way partition for duplicate-heavy data
- **Historical**: Invented by Tony Hoare in 1959 at Moscow State University; published 1961 in CACM
