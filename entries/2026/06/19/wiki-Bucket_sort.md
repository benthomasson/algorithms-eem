---
source: sources/wiki-Bucket_sort.md
source_url: https://en.wikipedia.org/wiki/Bucket_sort
---

## Bucket Sort Algorithm

Bucket sort (also called bin sort) is a distribution sort that works by partitioning elements into a fixed number of buckets, sorting each bucket individually, then concatenating the results. It achieves linear average-case time when input is uniformly distributed and the number of buckets is proportional to n. Performance degrades with clustering, as many elements may land in the same bucket.

## Key Concepts

- **Mechanism**: Scatter elements into k buckets based on value, sort each bucket, then gather (concatenate) buckets in order
- **Distribution sort**: Does not rely solely on element comparisons; exploits knowledge of value distribution to partition work
- **Generalization of pigeonhole sort**: Allows multiple keys per bucket rather than exactly one
- **Cousin of radix sort**: Bucket sort with recursive application produces a relative of radix sort; the case of 2 buckets corresponds to quicksort
- **Average-case O(n)**: Achieved when k = Theta(n) and input is uniformly distributed over the range
- **Worst-case O(n^2)**: Occurs when all elements cluster into a single bucket (using insertion sort per bucket); can be O(n log n) if merge sort is used per bucket
- **Space complexity**: O(n + k) — the array plus the bucket structure
- **Not inherently stable or unstable**: Stability depends on the sub-sort used within each bucket
- **Bucket index formula**: `floor(k * array[i] / M)` where M is 1 + max key value

## Commands and Syntax

```
function bucketSort(array, k):
    buckets ← new array of k empty lists
    M ← 1 + max key value in array
    for i = 0 to length(array):
        insert array[i] into buckets[floor(k × array[i] / M)]
    for i = 0 to k:
        nextSort(buckets[i])     // typically insertion sort
    return concatenation of buckets[0] ... buckets[k]
```

**Optimization**: Instead of sorting each bucket separately, scatter elements back into the original array, then run a single insertion sort pass over the entire array. This exploits cache locality and the fact that elements are already close to their final positions.

## Relationships

- **Counting sort**: Bucket sort with bucket size 1 degenerates to counting sort; bucket sort trades counting sort's O(n + M) worst-case for O(n) memory
- **Quicksort**: Bucket sort with 2 buckets is effectively quicksort with the pivot at the midpoint of the value range
- **Radix sort**: Top-down radix sort is a special case where both range and bucket count are powers of two; recursive bucket sort produces a radix sort variant
- **Mergesort**: n-way mergesort also distributes into sublists, but sublists have overlapping ranges requiring a merge phase rather than simple concatenation
- **Pigeonhole sort**: Bucket sort generalizes pigeonhole sort by allowing multiple elements per bucket
- **Insertion sort**: Conventionally used as the per-bucket sort due to good performance on small inputs
- **Distribution sort family**: Sits alongside counting sort, radix sort, pigeonhole sort, and flashsort

## Variants

- **ProxmapSort**: Uses a "map key" function to place elements approximately in sorted position; maintains sorted subarrays via insertion sort
- **Histogram sort**: Adds an initial counting pass to determine bucket sizes, enabling in-place bucket placement via exchanges (no extra bucket storage)
- **Postman's sort**: Exploits hierarchical key structure (like postal addresses); processes most-significant attribute first, similar to MSD radix sort; time is O(cn) where c depends on key size
- **Shuffle sort**: Removes first 1/8 of elements, sorts them recursively to create n/8 bucket boundaries, distributes remaining 7/8, sorts each bucket

## Exam-Relevant Points

- Average time is **O(n + n^2/k + k)**; setting k = Theta(n) yields **O(n)** average time with uniform input
- Worst case is **O(n^2)** when all elements fall into one bucket (with insertion sort); worst case is **O(n log n)** if a comparison sort like merge sort is used per bucket
- Space is always **O(n + k)**
- The algorithm **assumes knowledge of input distribution** — uniform distribution over [0, 1) is the classic assumption (from CLRS)
- Bucket sort is **not a comparison sort** in its pure form (it uses arithmetic to assign buckets), but it can be implemented with comparisons
- The four phases are: **initialize buckets, scatter, sort buckets, gather**
- Key optimization: scatter back to original array, then single insertion sort pass (cache-friendly, fewer comparisons since elements are near final position)
- With 2 buckets, equivalent to quicksort with midpoint pivot — poor pivot choice for non-uniform data
- Counting sort is the degenerate case (bucket size = 1) with O(n + M) time and O(M) space
