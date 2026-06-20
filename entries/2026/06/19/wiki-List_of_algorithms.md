---
source: sources/wiki-List_of_algorithms.md
source_url: https://en.wikipedia.org/wiki/List_of_algorithms
---

## Comprehensive Index of Algorithms by Domain

This page is a master catalog of well-known algorithms organized by problem domain. It serves as a taxonomic reference, grouping algorithms by the type of problem they solve — from graph traversal and sorting to numerical methods, cryptography, and computational geometry. Rather than explaining any single algorithm in depth, it maps the landscape of algorithmic problem-solving and shows which named algorithms address which classes of problems.

## Key Concepts

- **Algorithms are organized by problem domain**, not by technique — the same underlying method (e.g., divide-and-conquer) appears under multiple categories
- **Combinatorial algorithms** cover graphs, sequences, and discrete structures — the largest category
- **Graph algorithms** subdivide into: matching, coloring, drawing, network flow, routing (shortest path, MST, TSP), search/traversal, and subgraph problems
- **Sequence algorithms** subdivide into: searching, sorting, merging, permutation, alignment, approximate matching, and subsequence/substring problems
- **Sorting algorithms** are classified by mechanism: exchange sorts (bubble, quicksort), insertion sorts, merge sorts, selection sorts (heapsort), non-comparison sorts (radix, counting, bucket), and hybrid sorts (timsort, introsort)
- **Computational mathematics** covers abstract algebra, computer algebra, geometry, number theory, numerical analysis, and optimization
- **Non-comparison sorts** (radix, counting, bucket) can beat the O(n log n) lower bound for comparison-based sorting
- **Hybrid algorithms** combine strategies: introsort (quicksort + heapsort), timsort (merge sort + insertion sort)

## Commands and Syntax

No executable commands — this is a reference taxonomy. However, the classification structure itself is a tool:

- **To find an algorithm for a problem**: identify the problem class (graph routing? sequence search? optimization?) and look under that heading
- **Problem → Algorithm mapping examples**:
  - Shortest path with negative weights → Bellman-Ford
  - Shortest path, non-negative weights → Dijkstra
  - All-pairs shortest path → Floyd-Warshall
  - Maximum flow → Ford-Fulkerson, Edmonds-Karp, Dinic's, Push-relabel
  - Minimum spanning tree → Kruskal, Prim, Boruvka
  - Substring search → KMP, Boyer-Moore, Rabin-Karp, Aho-Corasick
  - Stable matching → Gale-Shapley
  - Convex hull → Graham scan, Quickhull, Chan's algorithm

## Relationships

- **Graph search algorithms** (BFS, DFS, A*, Dijkstra) underpin both **routing algorithms** and **AI/planning** algorithms
- **Sorting** connects to **searching** (binary search requires sorted input) and **selection** (quickselect derives from quicksort)
- **String matching** connects to **sequence alignment** (both use dynamic programming) and **approximate matching** (edit distance metrics)
- **Number theory algorithms** (primality testing, factorization, discrete logarithm) directly underpin **cryptographic algorithms** (RSA, Diffie-Hellman)
- **Computational geometry** (convex hull, Voronoi diagrams, Delaunay triangulation) connects to **graph algorithms** through duality relationships
- **Dynamic programming** appears across domains: sequence alignment (Needleman-Wunsch, Smith-Waterman), shortest paths (Floyd-Warshall, Bellman-Ford), and subsequence problems (LCS, LIS)
- **Flow network algorithms** generalize to **matching problems** (max-flow min-cut theorem)

## Exam-Relevant Points

- **Dijkstra requires non-negative edge weights**; use Bellman-Ford for graphs with negative weights
- **Floyd-Warshall** solves all-pairs shortest path; Johnson's algorithm is better for sparse graphs
- **Timsort** is used in Python (2.3+) and Java SE 7+ — a practical hybrid of merge sort and insertion sort
- **Introsort** switches from quicksort to heapsort when recursion depth exceeds a threshold — guarantees O(n log n) worst case
- **A*** is a special case of best-first search using heuristics; Dijkstra is A* with no heuristic
- **Topological sort** finds linear ordering based on dependencies — appears under both graph routing and sorting categories
- **Gale-Shapley** solves the stable matching problem
- **Non-comparison sorts** (counting, radix, bucket) achieve O(n) but require assumptions about input
- **Strongly connected components**: Tarjan's and Kosaraju's algorithms both run in linear time
- **Maximum flow** algorithms: Ford-Fulkerson is the framework; Edmonds-Karp is the BFS implementation guaranteeing polynomial time; Dinic's is strongly polynomial
- **KMP** avoids re-examination of matched characters in substring search; Boyer-Moore is sublinear in practice
- **Aho-Corasick** searches for multiple patterns simultaneously using a trie
- **Sieve of Eratosthenes** is the classic prime-finding algorithm; AKS is the first deterministic polynomial-time primality test
- **Karatsuba multiplication** is the simplest sub-quadratic multiplication algorithm
