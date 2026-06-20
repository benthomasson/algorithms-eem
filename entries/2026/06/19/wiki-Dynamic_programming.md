---
source: sources/wiki-Dynamic_programming.md
source_url: https://en.wikipedia.org/wiki/Dynamic_programming
---

I need write permission to save this entry. Here's the summary I've prepared for `entries/2026/06/19/wiki-Dynamic_programming.md`:

## Dynamic Programming (DP)

Dynamic programming is both a mathematical optimization method and an algorithmic paradigm, developed by Richard Bellman in the 1950s. It simplifies complicated problems by breaking them into simpler overlapping sub-problems solved recursively. The core insight: when sub-problems recur, solve each only once and store results.

**Key Concepts:**
- **Two required properties**: optimal substructure (solution builds from optimal sub-solutions) AND overlapping sub-problems (same sub-problems recur). Both must be present.
- **Top-down (memoization)**: recurse + cache results in a table; check table before solving
- **Bottom-up (tabulation)**: solve smallest sub-problems first, iterate upward; no recursion
- **Bellman equation**: the fundamental recurrence V(state) = optimize { reward + V(next_state) }
- **D&C vs DP**: merge sort/quicksort have optimal substructure but *non-overlapping* sub-problems, so they're divide-and-conquer, not DP
- **Fibonacci canonical example**: naive O(2^n) becomes O(n) with DP
- **Subproblem graph being a DAG (not a tree)** visually indicates overlapping sub-problems

**Relationships:** Bellman-Ford, Floyd-Warshall (graph DP); Hamilton-Jacobi-Bellman (continuous control theory); greedy algorithms (local vs global optimality); divide-and-conquer (non-overlapping variant); backtracking (no sub-problem reuse)

**Exam-critical:** Referential transparency required for automatic memoization. Richard Bellman developed DP in the 1950s. Both top-down and bottom-up achieve the same asymptotic complexity.

Could you grant write permission so I can save this to disk?
