---
source: sources/wiki-Greedy_algorithm.md
source_url: https://en.wikipedia.org/wiki/Greedy_algorithm
---

## Greedy Algorithms: Locally Optimal Choice Strategies

A greedy algorithm solves optimization problems by making the locally optimal choice at each step without reconsidering past decisions. Greedy algorithms are a special case of dynamic programming where only one partial solution is maintained — requiring significantly more problem structure to work correctly. While they often produce exact optimal solutions for well-structured problems, in many cases they yield approximations rather than exact solutions.

## Key Concepts

- **Core principle**: At each step, choose the locally optimal option; never revise previous choices. Algorithms that undo past steps (e.g., Gale-Shapley) are explicitly *not* greedy.
- **Relationship to dynamic programming**: Greedy is "the ultimate form of dynamic programming" — maintaining only one partial solution instead of many. Requires more problem structure than general DP.
- **Matroid structure**: Jack Edmonds showed greedy algorithms optimally solve linear combinatorial optimization problems with matroid structure. Korte and Lovász generalized this via the greedoid concept.
- **Exchange argument**: The primary proof technique for greedy correctness. Assumes an optimal solution differing from the greedy solution, then shows exchanging choices at the first difference point cannot worsen the result, concluding optimality by induction.
- **Failure modes**: Greedy can get stuck at local optima, missing global optima (the classic hill-climbing trap). The "largest immediate value" may lead away from the globally best path.
- **No formal definition exists**: There is no complete characterization of when a problem admits a greedy solution.

## Commands and Syntax

**Activity Selection Problem** (exact greedy solution):
1. Sort tasks by end time — O(n log n)
2. Repeatedly choose the first task that begins after the last selected task ended

**Fractional Knapsack** (exact greedy solution):
1. Compute value-to-weight ratio for each item
2. Greedily select items by highest ratio, taking fractions of items as needed

**Greedy Graph Coloring** (upper bound):
1. Take an uncolored vertex
2. Assign the smallest color not used by its neighbors
3. Yields bound: χ(G) ≤ Δ(G) + 1

**Zeckendorf Representation**:
1. Repeatedly subtract the largest Fibonacci number ≤ remaining value
2. Produces the unique non-consecutive Fibonacci sum representation

## Relationships

- **Dynamic programming**: Greedy is a restricted special case — when only one subproblem matters, DP collapses to greedy
- **Approximation algorithms**: Greedy provides approximation guarantees for NP-hard problems:
  - TSP: greedy yields at most Θ(log n) times optimal tour length
  - 0-1 Knapsack: greedy on fractional relaxation yields ≥ 1/2 optimal value
  - Submodular maximization: greedy yields ≥ 1/2 optimal value
  - Set cover, load balancing, Steiner tree, independent set all use greedy approximations
- **Graph algorithms**: Dijkstra's (shortest path), Prim's and Kruskal's (MST), Huffman coding — all greedy
- **Matroids and greedoids**: The mathematical structures that characterize when greedy works optimally
- **Combinatorial optimization**: The primary problem domain where greedy algorithms apply
- **Hill climbing / best-first search**: Related local-search strategies sharing the greedy philosophy

## Exam-Relevant Points

- Greedy is a special case of DP, not a separate paradigm — it applies when only one partial solution needs to be maintained
- The **exchange argument** is the standard technique for proving greedy correctness (know the four steps)
- **Matroid structure** guarantees greedy optimality for linear combinatorial optimization (Edmonds' theorem)
- Know which classic algorithms are greedy: **Dijkstra's, Prim's, Kruskal's, Huffman coding**
- A* search is *conditionally* optimal greedy — requires an admissible heuristic (never overestimates)
- **Fractional knapsack** admits polynomial greedy solution; **0-1 knapsack** is NP-hard (key distinction)
- Gale-Shapley is **not** greedy because it modifies existing pairings
- Greedy TSP approximation ratio: Θ(log n) times optimal
- Greedy 0-1 knapsack approximation: at least half the optimal value
- The greedy coloring bound χ(G) ≤ Δ(G) + 1 is a direct consequence of the algorithm
- **Greedoid** (Korte & Lovász) generalizes matroid to characterize a broader class of greedy-solvable problems
