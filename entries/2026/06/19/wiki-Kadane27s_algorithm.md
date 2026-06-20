---
source: sources/wiki-Kadane27s_algorithm.md
source_url: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
---

## Maximum Subarray Problem (Kadane's Algorithm)

The maximum subarray problem asks for the contiguous subarray within a one-dimensional array of numbers that has the largest sum. It is a classic dynamic programming problem solvable in O(n) time and O(1) space using Kadane's algorithm. The problem was originally proposed by Ulf Grenander in 1977 as a simplified model for maximum likelihood estimation in digitized images, and the optimal linear-time solution was devised by Jay Kadane shortly after.

## Key Concepts

- **Problem definition**: Given array A[1...n], find indices i and j (1 <= i <= j <= n) such that the sum A[i] + ... + A[j] is maximized.
- **Kadane's algorithm**: Single-pass scan maintaining two variables: `current_sum` (best sum ending at current position) and `best_sum` (best sum seen anywhere so far). At each element x: `current_sum = max(x, current_sum + x)`, then `best_sum = max(best_sum, current_sum)`.
- **Dynamic programming interpretation**: The maximum subarray ending at position j is computed from the maximum subarray ending at position j-1 — an optimal substructure with overlapping subproblems.
- **Loop invariant**: At step j, `current_sum` holds the maximum sum over all subarrays ending exactly at position j.
- **Two variants**: (1) No empty subarrays — initialize `best_sum = -inf`, use `max(x, current_sum + x)`; (2) Empty subarrays admitted — initialize `best_sum = 0`, use `max(0, current_sum + x)`.
- **Trivial cases**: All non-negative numbers — answer is the entire array. All non-positive numbers — answer is the single element closest to zero (or empty subarray if permitted).
- **Multiple subarrays may share the same maximum sum.**

## Commands and Syntax

**Kadane's Algorithm (no empty subarrays):**
```python
def max_subarray(numbers):
    best_sum = float('-inf')
    current_sum = 0
    for x in numbers:
        current_sum = max(x, current_sum + x)
        best_sum = max(best_sum, current_sum)
    return best_sum
```

**Empty subarrays variant — two changes:**
```python
best_sum = 0                            # instead of float('-inf')
current_sum = max(0, current_sum + x)   # instead of max(x, current_sum + x)
```

**Example**: Array [-2, 1, -3, 4, -1, 2, 1, -5, 4] — maximum subarray is [4, -1, 2, 1] with sum 6.

## Relationships

- **Dynamic programming**: Kadane's algorithm is a textbook example of DP with optimal substructure and overlapping subproblems.
- **Prefix sums**: Grenander's earlier O(n^2) solution used prefix sums to compute any subarray sum in O(1) via S[j] - S[i-1].
- **Divide and conquer**: Shamos's O(n log n) solution splits the array, solves each half recursively, and combines by finding the best crossing subarray.
- **Brute force**: Naive O(n^3) tries all pairs (i,j) and sums each; prefix sums reduce to O(n^2); Kadane reduces to O(n).
- **2D generalization**: Maximum sum rectangle in a 2D array is solvable in O(n^3) using Kadane's algorithm as a subroutine. A sub-cubic algorithm would imply a fast all-pairs shortest paths algorithm.
- **Subset sum problem**: Related but different — subset sum allows non-contiguous elements and is NP-complete.
- **k largest subarray sums**: Finding the k largest sums in a 1D array is solvable in optimal O(n+k) time (Brodal & Jorgensen, 2007).
- **k-disjoint subarrays**: Maximum sum of k non-overlapping subarrays also solvable in O(n+k) (Bengtsson & Chen, 2007).

## Exam-Relevant Points

- **Time complexity**: Kadane's algorithm runs in O(n) time — this is optimal since any algorithm must read the entire input.
- **Space complexity**: O(1) — only two variables maintained.
- **The key recurrence**: `current_sum[j] = max(A[j], current_sum[j-1] + A[j])` — decide whether to extend the previous subarray or start fresh.
- **Historical progression of solutions**: O(n^3) brute force -> O(n^2) prefix sums (Grenander) -> O(n log n) divide and conquer (Shamos) -> O(n) dynamic programming (Kadane).
- **Empty vs. non-empty variant**: The difference is just the initialization of `best_sum` and whether `max` compares against 0 or `x`. This is a common source of exam questions.
- **2D extension complexity**: O(n^3) — conditionally optimal assuming no breakthrough in all-pairs shortest paths.
- **Applications**: Genomic sequence analysis (finding protein segments with unusual properties), computer vision (detecting bright regions after threshold subtraction).
- **The algorithm is greedy in spirit**: at each step it decides whether to extend the current subarray or abandon it and start fresh — but is formally classified as dynamic programming due to its subproblem structure.
