---
source: sources/wiki-Graph_abstract_data_type.md
source_url: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
---

## Graph (Abstract Data Type) — Representations, Operations, and Complexity

This page covers the graph as an abstract data type in computer science, including its formal definition (vertices and edges), the standard operations it supports, the three primary data structures used to represent graphs (adjacency list, adjacency matrix, incidence matrix), their time complexity tradeoffs, and considerations for parallel and compressed representations.

## Key Concepts

- A **graph** consists of a finite set of **vertices** (nodes) and a set of **edges** (links) — unordered pairs for undirected graphs, ordered pairs for directed graphs.
- Edges may carry associated values (weights, labels, capacities).
- Three canonical representations:
  - **Adjacency list**: Each vertex stores a list of its adjacent vertices. Space: O(|V| + |E|). Best for **sparse graphs**.
  - **Adjacency matrix**: 2D matrix where rows = source vertices, columns = destination vertices. Space: O(|V|²). Best for **dense graphs** or when fast edge lookup is needed.
  - **Incidence matrix**: 2D matrix where rows = vertices, columns = edges. Space: O(|V| · |E|). Rarely preferred due to poor complexity across all operations.
- A graph is **sparse** when |E| << |V|² and **dense** when |E| ≈ |V|².
- Adjacency list performance can be improved by replacing lists with **hash tables** (amortized O(1) adjacency test and edge removal) or **balanced BSTs**.

## Commands and Syntax

Standard graph ADT operations:

| Operation | Signature | Description |
|---|---|---|
| `adjacent(G, x, y)` | → boolean | Test if edge exists from x to y |
| `neighbors(G, x)` | → list of vertices | All vertices adjacent to x |
| `add_vertex(G, x)` | → void | Add vertex x |
| `remove_vertex(G, x)` | → void | Remove vertex x and incident edges |
| `add_edge(G, x, y, z)` | → void | Add edge z from x to y |
| `remove_edge(G, x, y)` | → void | Remove edge from x to y |
| `get_vertex_value(G, x)` | → value | Return value of vertex x |
| `set_vertex_value(G, x, v)` | → void | Set value of vertex x |
| `get_edge_value(G, x, y)` | → value | Return value of edge (x, y) |
| `set_edge_value(G, x, y, v)` | → void | Set value of edge (x, y) |

**Complexity comparison:**

| Operation | Adjacency List | Adjacency Matrix | Incidence Matrix |
|---|---|---|---|
| Store graph | O(\|V\| + \|E\|) | O(\|V\|²) | O(\|V\| · \|E\|) |
| Add vertex | O(1) | O(\|V\|²) | O(\|V\| · \|E\|) |
| Add edge | O(1) | O(1) | O(\|V\| · \|E\|) |
| Remove vertex | O(\|E\|) | O(\|V\|²) | O(\|V\| · \|E\|) |
| Remove edge | O(\|V\|) | O(1) | O(\|V\| · \|E\|) |
| Adjacency test | O(\|V\|) | O(1) | O(\|E\|) |

## Relationships

- **Graph theory** (mathematics) provides the formal underpinning; the ADT implements these concepts in code.
- **BFS and DFS** are fundamental traversal algorithms that operate on graph representations.
- **Dijkstra's algorithm** uses graphs for shortest-path computation on non-negative weighted graphs.
- **Kosaraju's algorithm** finds strongly connected components via modified DFS.
- **Hash tables** and **balanced BSTs** can improve adjacency list performance.
- **Graph partitioning** (NP-hard) is essential for distributed-memory parallel graph algorithms; relates to MPI and parallel computing.
- Connected to other data structures: trees are special cases of graphs; DAGs, heaps, and tries are graph-related structures.

## Exam-Relevant Points

- **Adjacency list vs. adjacency matrix**: Know when to use each. Adjacency list for sparse graphs (O(|V| + |E|) space), adjacency matrix for dense graphs or O(1) edge lookup (O(|V|²) space).
- **Adjacency test complexity**: O(|V|) for adjacency list, O(1) for adjacency matrix — a frequently tested distinction.
- **Adding/removing vertices**: O(1) for adjacency list but O(|V|²) for adjacency matrix (matrix resize).
- **Hash table optimization**: Replacing adjacency lists with hash sets gives amortized O(1) adjacency test and edge removal, with O(deg(x)) vertex removal.
- **Incidence matrix** is almost never the optimal choice — it has O(|V| · |E|) for every mutating operation.
- **Graph partitioning is NP-hard** — practical approaches use heuristics (1D and 2D partitioning).
- **1D partitioning** requires All-to-All communication; **2D partitioning** bounds communication partners to p_r + p_c - 1.
- **Shared memory** parallelism reuses sequential representations; **distributed memory** requires explicit partitioning.
- Dijkstra's algorithm requires **non-negative edge weights**.
