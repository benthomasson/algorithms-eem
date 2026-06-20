---
source: sources/wiki-Binary_search.md
source_url: https://en.wikipedia.org/wiki/Binary_search
---

I need write permissions to save the entry. Could you grant write access to the entries directory? In the meantime, here's the complete study entry:

---

## Binary Search: Divide-and-Conquer Search on Sorted Arrays

Binary search (also called half-interval search, logarithmic search, or binary chop) is a search algorithm that finds the position of a target value within a sorted array by repeatedly dividing the search interval in half. It compares the target to the middle element, eliminates the half where the target cannot lie, and continues on the remaining half until the target is found or the search space is exhausted. It runs in O(log n) time with O(1) space, making it optimal among comparison-based searches on sorted arrays.

## Key Concepts

- **Precondition**: The array must be sorted before binary search can be applied.
- **Mechanism**: Compare target to the middle element; eliminate the half that cannot contain the target; repeat.
- **Time complexity**: O(log n) worst and average case; O(1) best case (target is the middle element).
- **Space complexity**: O(1) for the iterative version.
- **Optimality**: No comparison-based algorithm can do better than O(log n) in the worst case on sorted arrays.
- **Faster than linear search** for all but small arrays; linear search is O(n).
- **Slower than hash table lookup** (O(1) average), but binary search solves a wider class of problems (approximate matches, rank queries, predecessor/successor).
- **Middle element calculation**: Use `m = L + floor((R - L) / 2)` to avoid integer overflow, not `(L + R) / 2`.
- **Duplicate elements**: The standard procedure returns an arbitrary matching index. Specialized variants find the leftmost or rightmost occurrence.
- **Approximate matches**: Binary search can compute rank, predecessor, successor, nearest neighbor, and range queries.

## Commands and Syntax

### Standard binary search (exact match)
```
function binary_search(A, n, T):
    L := 0
    R := n − 1
    while L ≤ R:
        m := L + floor((R - L) / 2)
        if A[m] < T:       L := m + 1
        else if A[m] > T:  R := m − 1
        else:               return m
    return unsuccessful
```

### Alternative procedure (deferred equality check)
Eliminates one comparison per iteration; checks equality only when L = R. Uses ceiling instead of floor. Converges to the rightmost match.
```
function binary_search_alternative(A, n, T):
    L := 0;  R := n − 1
    while L != R:
        m := L + ceil((R - L) / 2)
        if A[m] > T:  R := m − 1
        else:          L := m
    if A[L] = T then return L
    return unsuccessful
```

### Find leftmost (lower bound)
R initialized to **n** (not n-1). Returns rank of T (number of elements < T) even when T is absent.
```
function binary_search_leftmost(A, n, T):
    L := 0;  R := n
    while L < R:
        m := L + floor((R - L) / 2)
        if A[m] < T:  L := m + 1
        else:          R := m
    return L
```

### Find rightmost (upper bound)
Returns R-1. The value n - R gives the count of elements greater than T.
```
function binary_search_rightmost(A, n, T):
    L := 0;  R := n
    while L < R:
        m := L + floor((R - L) / 2)
        if A[m] > T:  R := m
        else:          L := m + 1
    return R - 1
```

## Relationships

- **Linear search**: O(log n) vs O(n); linear search works on unsorted arrays and is better for very small n.
- **Hash tables**: O(1) average lookup beats binary search, but cannot support ordered queries (rank, predecessor, successor, range).
- **Binary search tree (BST)**: Embeds binary search into a tree structure; each node comparison = one step of binary search.
- **B-tree**: Generalizes BSTs for disk-based storage; uses binary search within each node.
- **Sorted array**: Binary search's required data structure; cost of maintaining sorted order (O(n) per insertion) is the key tradeoff.
- **Bisection method**: Continuous-domain analogue for finding roots of functions.
- **Exponential search**: Extends binary search to unbounded lists by first finding a range.
- **Fractional cascading**: Speeds up binary search across k sorted arrays from O(k log n) to O(k + log n).
- **Divide-and-conquer**: Binary search is a canonical example of this paradigm.
- **Interpolation search**: Uses value distribution to guess position; O(log log n) for uniform distributions but O(n) worst case.

## Exam-Relevant Points

- **Complexity**: O(log n) time worst/average, O(1) best, O(1) space.
- **Precondition**: Array MUST be sorted.
- **Overflow bug**: `(L + R) / 2` can overflow; correct form is `L + (R - L) / 2`.
- **Loop invariant**: Target, if present, is always within A[L..R]. When L > R, target is absent.
- **Floor vs ceiling**: Standard uses floor; Bottenbruch alternative uses ceiling and defers equality check.
- **Leftmost/rightmost variants**: Leftmost initializes R = n, sets R = m on A[m] >= T. Rightmost initializes R = n, sets L = m + 1 on A[m] <= T.
- **Rank from leftmost**: Returns count of elements < T even when T is absent.
- **Range query**: Two rank queries give count of elements in a range.
- **vs. BST**: Binary search on sorted array has better cache locality than BST traversal, but BSTs support O(log n) insertion vs O(n) for sorted arrays.
- **When NOT to use**: Unsorted data, frequent insertions, very small arrays.
- **Worst-case comparisons**: Exactly floor(log2 n) + 1.
