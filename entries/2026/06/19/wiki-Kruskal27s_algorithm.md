---
source: sources/wiki-Kruskal27s_algorithm.md
source_url: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
---

## Kruskal's Algorithm — Minimum Spanning Tree/Forest Construction

Kruskal's algorithm is a greedy algorithm that finds a minimum spanning forest (or minimum spanning tree for connected graphs) by repeatedly adding the lowest-weight edge that does not create a cycle. It was first published by Joseph Kruskal in 1956. The algorithm relies on sorting edges by weight and using a disjoint-set (union-find) data structure to efficiently detect cycles.

## Key Concepts

- **Minimum spanning tree (MST)**: A connected subgraph without cycles whose total edge weight is minimal
- **Minimum spanning forest**: For disconnected graphs, composed of one MST per connected component
- **Greedy strategy**: Always pick the cheapest edge that doesn't form a cycle
- **Disjoint-set data structure (Union-Find)**: Used to track which vertices belong to which component; supports MAKE-SET, FIND-SET, and UNION operations
- **Cycle detection**: An edge creates a cycle iff both endpoints are already in the same component (FIND-SET(u) == FIND-SET(v))
- **The algorithm produces exactly V-1 edges for a connected graph with V vertices**
- **Inverse Ackermann function α(V)**: The amortized cost per union-find operation; grows so slowly it is effectively constant for all practical inputs

## Commands and Syntax

**Standard Kruskal's pseudocode:**
```
function Kruskal(Graph G):
    F := ∅
    for each v in G.Vertices:
        MAKE-SET(v)
    for each {u, v} in G.Edges ordered by increasing weight:
        if FIND-SET(u) ≠ FIND-SET(v):
            F := F ∪ { {u, v} }
            UNION(FIND-SET(u), FIND-SET(v))
    return F
```

**Filter-Kruskal variant (parallelizable):**
```
function filter_kruskal(G):
    if |G.E| < kruskal_threshold:
        return kruskal(G)
    pivot = choose_random(G.E)
    E≤, E> = partition(G.E, pivot)
    A = filter_kruskal(E≤)
    E> = filter(E>)           # remove edges within same component
    A = A ∪ filter_kruskal(E>)
    return A
```

## Relationships

- **Prim's algorithm**: Alternative MST algorithm; grows a single tree from a starting vertex using a priority queue. Better for dense graphs
- **Borůvka's algorithm**: Another MST algorithm; each component selects its cheapest outgoing edge simultaneously. More naturally parallelizable
- **Reverse-delete algorithm**: Works in the opposite direction — starts with all edges, removes the heaviest that doesn't disconnect the graph
- **Disjoint-set data structure**: Essential to Kruskal's efficiency; union by rank + path compression gives near-constant amortized operations
- **Comparison sorting**: Dominates the runtime; if edges are pre-sorted or have small integer weights (enabling counting/radix sort), the bottleneck shifts to union-find operations
- **Quicksort**: Filter-Kruskal partitions edges similarly to quicksort to reduce sorting overhead
- **Dijkstra's algorithm**: Related graph algorithm for shortest paths (not spanning trees)
- **Single-linkage clustering**: Kruskal's algorithm directly produces a single-linkage hierarchical clustering dendrogram

## Exam-Relevant Points

- **Time complexity**: O(E log V) with comparison sort; equivalent to O(E log E) since log E = Θ(log V) for graphs without isolated vertices
- **With pre-sorted edges**: Complexity drops to O(E · α(V)), dominated by union-find operations
- **Space complexity**: O(V + E) for the disjoint-set structure and edge list
- **Kruskal's is optimal for sparse graphs**; Prim's (with Fibonacci heap) is better for dense graphs
- **Correctness proof**: Uses an exchange argument via induction — at every stage, the chosen edges F are a subset of some MST; adding the next safe edge preserves this invariant
- **Parallelization**: The main loop is inherently sequential, but sorting can be parallelized; Filter-Kruskal improves parallelism by partitioning edges like quicksort
- **With parallel sorting on O(log n) processors**, runtime reduces to O(E · α(V))
- **Ties in edge weight are broken arbitrarily** without affecting correctness
- **Works on disconnected graphs** — produces a minimum spanning forest (one tree per component)
