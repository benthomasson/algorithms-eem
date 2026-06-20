---
source: sources/wiki-Prim27s_algorithm.md
source_url: https://en.wikipedia.org/wiki/Prim%27s_algorithm
---

## Prim's Algorithm — Greedy Minimum Spanning Tree Construction

Prim's algorithm is a greedy algorithm that finds a minimum spanning tree (MST) for a weighted undirected graph. It builds the tree one vertex at a time from an arbitrary starting vertex, always adding the cheapest edge connecting the existing tree to a vertex not yet included. Originally developed by Vojtěch Jarník (1930), it was independently rediscovered by Robert C. Prim (1957) and Edsger W. Dijkstra (1959), yielding alternate names: Jarník's algorithm, Prim–Jarník, Prim–Dijkstra, or DJP algorithm.

## Key Concepts

- **Greedy strategy**: at each step, select the minimum-weight edge crossing the cut between tree vertices and non-tree vertices.
- **Operates on weighted undirected graphs**; the basic form requires the graph to be connected. For disconnected graphs, run Prim's separately on each connected component to find the minimum spanning forest.
- **Output is a tree** — the edge and vertex added are always connected to the existing partial tree, so no cycles form.
- **Cut property underpins correctness**: the lightest edge crossing any cut of the graph must belong to some MST. Prim's exploits this at every iteration.
- **Data structure choice determines performance**: the set of candidate vertices (priority queue Q) can be a simple array, binary heap, Fibonacci heap, or d-ary heap.
- **Comparison with alternatives**: Kruskal's algorithm sorts all edges globally and uses union-find; Borůvka's grows multiple components simultaneously. All three have equivalent asymptotic complexity on sparse graphs, but Prim's excels on dense graphs.
- **Parallelism**: the main loop is inherently sequential, but the inner loop (finding the minimum-weight crossing edge) can be parallelized by partitioning vertices/edges across processors.

## Commands and Syntax

**Pseudocode (sequential)**:
```
function Prim(vertices, edges):
    for each vertex: cheapestCost[vertex] ← ∞, cheapestEdge[vertex] ← null
    unexplored ← all vertices; explored ← ∅
    cheapestCost[startVertex] ← 0

    while unexplored not empty:
        currentVertex ← vertex in unexplored with min cheapestCost
        move currentVertex from unexplored to explored
        for each edge (currentVertex, neighbor):
            if neighbor in unexplored and weight < cheapestCost[neighbor]:
                cheapestCost[neighbor] ← weight
                cheapestEdge[neighbor] ← (currentVertex, neighbor)

    return all non-null cheapestEdge values
```

**Key operations per data structure**:
- Array/adjacency matrix: linear scan for minimum → O(|V|^2) total
- Binary heap: extract-min + decrease-key → O(|E| log |V|) total
- Fibonacci heap: O(1) amortized decrease-key → O(|E| + |V| log |V|) total

## Relationships

- **Dijkstra's algorithm**: structurally almost identical — Dijkstra relaxes edges by cumulative path cost; Prim's relaxes by individual edge weight. Same priority-queue-based loop structure.
- **Kruskal's algorithm**: alternate MST approach using global edge sorting + union-find rather than vertex-growing. Better suited when edges are already sorted or the graph is sparse.
- **Borůvka's algorithm**: third classical MST algorithm; grows all components simultaneously. Historically the earliest (1926).
- **Priority queues / heaps**: Prim's performance is directly governed by the heap implementation (binary, Fibonacci, d-ary).
- **Greedoids**: the matroid/greedoid framework provides the theoretical foundation explaining why Prim's greedy choices yield a globally optimal result.
- **Minimum spanning forest**: extension of MST to disconnected graphs; Kruskal's and Borůvka's handle this natively, Prim's requires per-component invocation.

## Exam-Relevant Points

- **Time complexities** (must memorize):
  - Adjacency matrix, linear search: **O(|V|^2)**
  - Binary heap + adjacency list: **O(|E| log |V|)**
  - Fibonacci heap + adjacency list: **O(|E| + |V| log |V|)**
- Prim's achieves **linear time** on sufficiently dense graphs (|E| ≥ |V| log |V|) using a Fibonacci heap, or when |E| ≥ |V|^c (c > 1) using a d-ary heap.
- Prim's basic form works only on **connected** graphs (unlike Kruskal's/Borůvka's which find spanning forests directly).
- The algorithm is a **greedy** algorithm — its correctness relies on the cut property of MSTs.
- **Proof technique**: exchange argument — if Prim's output Y differs from some MST Y1, the first differing edge e can replace an edge f in Y1 without increasing total weight, constructing a new MST that agrees with Y on one more edge. Repeat until Y equals an MST.
- Prim's is preferred over Kruskal's for **dense graphs**; Kruskal's is preferred for **sparse graphs**.
- The main loop is **not parallelizable**, but the inner minimum-finding step can be distributed across processors with running time O(|V|^2/|P|) + O(|V| log |P|).
- The starting vertex is **arbitrary** — it does not affect the total MST weight (though it may produce a different MST when ties exist).
