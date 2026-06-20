---
source: sources/wiki-Radix_sort.md
source_url: https://en.wikipedia.org/wiki/Radix_sort
---

## Radix Sort: Non-Comparative Distribution Sorting Algorithm

Radix sort is a non-comparative sorting algorithm that sorts data by distributing elements into buckets according to individual digits (or characters), processing one digit position at a time. It applies to any lexicographically sortable data: integers, strings, punch cards, or mail. Dating back to Herman Hollerith's 1887 tabulating machines, the first memory-efficient computer implementation was developed by Harold H. Seward at MIT in 1954, who used a linear scan to predetermine bucket sizes — an insight closely related to counting sort.

## Key Concepts

- **Non-comparative**: avoids element-to-element comparisons entirely; distributes into buckets based on digit values
- **Two processing orders**:
  - **LSD (Least Significant Digit)**: processes from rightmost digit to leftmost; generally stable; produces natural integer ordering (short keys before longer keys of same prefix)
  - **MSD (Most Significant Digit)**: processes from leftmost digit to rightmost; produces lexicographic ordering; naturally recursive (each bucket is independently sub-sorted); not necessarily stable
- **Radix**: the base of the number system used for digit extraction (e.g., base-10, base-256 for byte-level processing)
- **Stability**: LSD radix sort is inherently stable; in-place MSD variants (including binary quicksort) are not stable; stable MSD requires an auxiliary buffer of size O(n)
- **Bucket sizing**: Seward's key innovation — use counting sort as a subroutine to predetermine bucket boundaries, enabling single static memory allocation instead of dynamic allocation
- **Variable-length keys**: LSD handles these by grouping by length, sorting each group, then concatenating; MSD must logically pad shorter keys

## Commands and Syntax

**LSD Radix Sort procedure** (conceptual):
```
for each digit position d from least significant to most significant:
    use a stable sort (typically counting sort) to sort array by digit d
```

**MSD Radix Sort procedure** (recursive):
```
function msd_radix_sort(array, digit_position):
    if digit_position > max_digits or array.length <= 1:
        return
    distribute elements into buckets by digit at digit_position
    for each bucket:
        msd_radix_sort(bucket, digit_position + 1)
    concatenate buckets
```

**In-place binary MSD (binary quicksort)**:
```
grow 0s-bin from left, 1s-bin from right
for each unprocessed element:
    if MSB == 1: swap to 1s-bin end, decrement boundary
    if MSB == 0: advance 0s-bin boundary
recurse on each bin with next bit position
```

**Counting optimization**: perform all digit counts in a single pass over the array (rather than one count pass per digit), reducing total passes from Θ(2d(n+k)) to Θ((d+1)(n+k)).

## Relationships

- **Counting sort**: used as the stable subroutine for each digit pass in LSD radix sort; Seward developed both algorithms together
- **Bucket sort**: radix sort is historically called bucket sort; both are distribution sorts
- **Comparison sorts** (quicksort, merge sort, heapsort): radix sort breaks the O(n log n) comparison lower bound by not comparing elements; benchmarks show 50%–3× speedup over general-purpose comparison sorts in suitable domains
- **Insertion sort**: used as a hybrid optimization when MSD recursion produces small buckets
- **Radix tree / trie**: tree-based radix sorting builds a trie from input and does pre-order traversal (analogous to heapsort's relationship to heap)
- **Burstsort**: trie-based extension that bursts buckets into sub-tries at capacity thresholds
- **Parallel computing**: MSD radix sort is naturally parallelizable — each bucket can be sorted on a separate processor; counting phase is amenable to parallel_reduce pattern
- **Prefix sum**: related algorithmic primitive used in parallel implementations

## Exam-Relevant Points

- **Time complexity**: O(d·n) where d = key length in digits and n = number of keys; more precisely Θ(d(n+k)) where k = range of each digit (e.g., 256 for bytes)
- **Space complexity**: O(d + n) worst case
- **Not comparison-based**: circumvents the Ω(n log n) comparison sort lower bound
- **LSD is stable; in-place MSD variants are not stable**; stable MSD requires O(n) auxiliary memory
- **When d is constant and k = O(n)**, radix sort runs in **linear time Θ(n)**
- **Large key sizes degrade LSD performance** because the number of required passes grows with d
- **MSD best case is a single pass**; worst case matches LSD
- **Two's complement signed integers** require treating the MSB with opposite sense (invert comparison on sign bit)
- **Practical optimization**: count all digit frequencies in one pass to reduce from 2d to d+1 passes
- **Hybrid approach**: switch to insertion sort for small bins during MSD recursion to reduce constant-factor overhead
- **Parallelism**: counting phase is data-independent (parallel_reduce); recursive bucket processing is data-dependent (worst case: all identical keys yield zero parallelism)
- **Historical**: Hollerith (1887), punched card sorting (1923), Seward's memory-efficient algorithm (1954, MIT)
- **Applicability constraint**: data must be sortable lexicographically
