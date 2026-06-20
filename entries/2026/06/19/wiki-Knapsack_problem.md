---
source: sources/wiki-Knapsack_problem.md
source_url: https://en.wikipedia.org/wiki/Knapsack_problem
---

I'll create the study notes entry now.

## The Knapsack Problem: Variants, Complexity, and Dynamic Programming Solutions

The knapsack problem is a foundational problem in combinatorial optimization: given items with weights and values, select a subset that maximizes total value without exceeding a weight capacity. It is one of the most studied NP-complete problems, with practical applications in resource allocation, portfolio selection, cryptography, and cutting stock problems. It admits pseudo-polynomial time solutions via dynamic programming and has a fully polynomial-time approximation scheme (FPTAS).

## Key Concepts

- **Problem statement**: Given n items each with weight w_i and value v_i, and capacity W, maximize total value subject to total weight <= W
- **0-1 Knapsack**: Each item is either included or not (x_i in {0, 1}) — the most common variant
- **Bounded Knapsack (BKP)**: Each item may be included up to c copies (x_i in {0, 1, ..., c})
- **Unbounded Knapsack (UKP)**: No limit on copies of each item (x_i in natural numbers)
- **Subset sum problem**: Special case where w_i = v_i for all items; one of Karp's 21 NP-complete problems
- **Decision version**: "Can value >= V be achieved within weight W?" — this form is NP-complete
- **Optimization version**: Verifying a solution is optimal is co-NP-complete
- **Pseudo-polynomial time**: The DP solution runs in O(nW), which is pseudo-polynomial because W is exponential in the number of bits needed to represent it (log W bits)
- **Weakly vs strongly NP-complete**: With integer weights/profits, the problem is weakly NP-complete; with rational weights/profits, it is strongly NP-complete (but still admits FPTAS)
- The knapsack problem ranked 19th most popular and 3rd most needed among 75 combinatorial algorithm problems (1999 Stony Brook survey)

## Commands and Syntax

**0-1 Knapsack DP (bottom-up, tabulation):**
```
array m[0..n, 0..W]
for j from 0 to W do: m[0, j] := 0
for i from 1 to n do: m[i, 0] := 0

for i from 1 to n do:
    for j from 1 to W do:
        if w[i] > j then:
            m[i, j] := m[i-1, j]
        else:
            m[i, j] := max(m[i-1, j], m[i-1, j-w[i]] + v[i])
```
- Time: O(nW), Space: O(nW) — reducible to O(W) if only the optimal value is needed

**0-1 Knapsack DP recurrence (Definition A):**
- Base: m[0, w] = 0
- If w_i > w: m[i, w] = m[i-1, w] (item too heavy, skip)
- If w_i <= w: m[i, w] = max(m[i-1, w], m[i-1, w - w_i] + v_i) (take or skip)

**Unbounded Knapsack DP recurrence:**
- Base: m[0] = 0
- m[w] = max(v_i + m[w - w_i]) for all i where w_i <= w
- Time: O(nW)

**Top-down memoized variant**: Initialize value table to -1, recursively compute m(i, j) only for subproblems actually needed. Runtime between O(nW) and O(2^n) depending on which subproblems are visited.

**Optimization**: Dividing all weights and W by their GCD reduces the table size and improves running time.

## Relationships

- **Dynamic programming**: The knapsack problem is a canonical example of DP with overlapping subproblems and optimal substructure
- **Subset sum problem**: Special case of 0-1 knapsack where weight equals value; connects to cryptography (Merkle-Hellman knapsack cryptosystem)
- **Bin packing problem**: Related combinatorial optimization problem (knapsack was 3rd most needed, after suffix trees and bin packing)
- **Branch and bound**: Alternative exact solving approach, often hybridized with DP
- **FPTAS**: A fully polynomial-time approximation scheme exists, using the pseudo-polynomial DP as a subroutine
- **NP-completeness theory**: The distinction between polynomial in n vs polynomial in W illustrates the difference between weakly and strongly NP-complete problems
- **Public-key cryptography**: Hard knapsack instances are used in cryptosystems (Merkle-Hellman)
- **Greedy algorithms**: The fractional knapsack (not covered here) is solvable greedily, contrasting with the 0-1 version requiring DP
- **Decision tree models**: Lower bound of (1/2)n^2 for linear decision trees (Dobkin-Lipton); O(n^4) upper bound for subset sum in this model (Meyer auf der Heide)

## Exam-Relevant Points

- The 0-1 knapsack DP has **O(nW) time and O(nW) space** — this is **pseudo-polynomial**, not polynomial, because W is measured by its bit-length (log W), not its numeric value
- The knapsack problem is **NP-complete** in its decision form, yet solvable in pseudo-polynomial time — this makes it **weakly NP-complete**
- Space can be reduced to **O(W)** if only the optimal value (not the item selection) is needed
- The **recurrence relation** for 0-1 knapsack: m[i,w] = max(m[i-1,w], m[i-1,w-w_i] + v_i) — know this cold
- **Subset sum** is a special case where w_i = v_i; it is in Karp's 21 NP-complete problems
- Know the three variants and their constraints: **0-1** (x_i in {0,1}), **bounded** (x_i in {0,...,c}), **unbounded** (x_i in N)
- Top-down memoization avoids computing all O(nW) subproblems — actual runtime depends on which subproblems are reachable
- Dividing weights by their GCD is a practical optimization that reduces table dimensions
- With **rational** weights and profits the problem becomes **strongly NP-complete**, but still admits FPTAS
- The connection between decision and optimization versions: a polynomial algorithm for either implies a polynomial algorithm for the other
