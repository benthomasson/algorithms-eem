---
source: sources/wiki-Graph_theory.md
source_url: https://en.wikipedia.org/wiki/Graph_theory
---

## Graph Theory: Foundations, Subareas, and Applications

Graph theory is a branch of discrete mathematics and computer science that studies graphs — mathematical structures consisting of vertices (nodes) connected by edges (arcs). It models pairwise relations between objects and is foundational to algorithms, network analysis, optimization, and numerous applied domains. The field originated with Euler's 1736 paper on the Seven Bridges of Königsberg and has grown into a major discipline with many specialized subareas.

## Key Concepts

- **Graph**: A structure of vertices (nodes/points) connected by edges (arcs/links/lines). Two vertices connected by an edge are called endpoints.
- **Undirected graph**: Edges link vertices symmetrically (no direction).
- **Directed graph (digraph)**: Each edge has an orientation/direction, designated with an arrow.
- **Mixed graph**: Contains both directed and undirected edges.
- **Simple graph**: No multiple edges between the same pair of vertices, no self-loops.
- **Multigraph**: Allows multiple edges between the same endpoints and self-loops.
- **Weighted graph**: Edges are assigned numerical values (weights).
- **Loop**: An edge connecting a vertex to itself.
- **Planar graph**: Can be drawn in the plane with no edge crossings.
- **Graph minor**: Formed from a graph by deleting vertices/edges and contracting edges.
- **Chromatic number**: Minimum number of colors needed to color vertices so no two adjacent vertices share a color.
- **Graph embedding**: Representing a graph on a surface such that edges only intersect at endpoints.
- **Crossing number**: Minimum number of edge crossings when a graph is drawn in the plane.
- **Graph invariant**: A property depending only on abstract structure, not on labeling or drawing.

## Major Subareas

- **Topological graph theory**: Studies graph embeddings in surfaces, graph minors, crossing numbers, map coloring, and voltage graphs. Key results include Wagner's theorem (planarity via forbidden minors K5 and K3,3) and the Robertson-Seymour theorem.
- **Algebraic graph theory**: Uses linear algebra (spectral graph theory — adjacency matrix, eigenvalues, Laplacian matrix) and group theory (automorphism groups, symmetric/vertex-transitive/distance-regular graphs). Key results include Frucht's theorem (every finite group is the automorphism group of some graph).
- **Geometric graph theory**: Studies graphs drawn with straight-line or curved edges in Euclidean space. Covers planar straight-line graphs (Fary's theorem), Euclidean minimum spanning trees, visibility graphs, polyhedral graphs (Steinitz's theorem), intersection graphs, and coin graphs (Koebe-Andreev-Thurston theorem).
- **Extremal graph theory**: Studies the maximum number of edges a graph can have while avoiding a particular subgraph. Originates from Mantel's theorem on triangle-free graphs and Turan's results.
- **Random graph theory**: Studies probabilistic properties of graphs, initiated by Erdos and Renyi on asymptotic graph connectivity.
- **Graph drawing**: Visualization of graphs as node-link diagrams, optimizing for crossing number, area, symmetry, angular resolution, and bend minimization.

## Commands and Syntax

Not directly applicable (mathematical field), but key formal notation includes:
- **K_n**: Complete graph on n vertices
- **K_{m,n}**: Complete bipartite graph with partitions of size m and n
- **Adjacency matrix**: Square matrix A where A[i][j] = 1 if edge (i,j) exists
- **Degree matrix**: Diagonal matrix D where D[i][i] = degree of vertex i
- **Laplacian matrix**: L = D - A
- **Chromatic polynomial**: P(G, k) counts proper k-colorings of graph G
- **Tutte polynomial**: Two-variable polynomial encoding connectivity properties

## Relationships

- **Discrete mathematics / Combinatorics**: Graph theory is a core subfield of both.
- **Topology**: Graph theory and topology co-evolved; Euler's formula (V - E + F = 2) is foundational to both.
- **Linear algebra**: Spectral graph theory applies eigenvalue analysis to adjacency and Laplacian matrices.
- **Group theory**: Automorphism groups classify graph symmetries.
- **Computational geometry**: Geometric graph theory overlaps with planar graphs, Voronoi diagrams, and shortest path problems.
- **Algorithm design**: Graph theory provides the mathematical foundation for BFS, DFS, shortest path (Dijkstra, Bellman-Ford), minimum spanning tree (Kruskal, Prim), network flow, and matching algorithms.
- **Chemistry**: Cayley's work on trees originated from molecular structure analysis; graph terminology reflects this heritage.
- **Probability theory**: Random graph theory connects graph structure to probabilistic methods.

## Exam-Relevant Points

- Euler's 1736 paper on the Seven Bridges of Königsberg is the origin of graph theory.
- The term "graph" was introduced by J.J. Sylvester in 1878.
- **Four-color theorem**: Any planar map can be colored with at most 4 colors so no two adjacent regions share a color. Proved by Appel and Haken (1976) using computer assistance.
- **Wagner's theorem**: A graph is planar if and only if it has no K5 or K3,3 minor.
- **Fary's theorem**: Every planar graph can be drawn with straight-line edges.
- **Steinitz's theorem**: A graph is a polyhedral graph iff it is 3-connected and planar.
- **Frucht's theorem**: Every finite group is the automorphism group of some graph.
- **Robertson-Seymour theorem**: Every graph property closed under minors and subgraphs has a finite set of forbidden minors.
- **Spectral graph theory** studies the adjacency matrix and Laplacian matrix eigenvalues/eigenvectors.
- **Chromatic polynomial** counts proper colorings as a function of number of colors.
- **Tutte polynomial** is a two-variable polynomial encoding graph connectivity.
- Know the distinctions: simple vs. multigraph, directed vs. undirected vs. mixed, weighted vs. unweighted.
- **Extremal graph theory** originated from Turan's 1941 results on maximum edges avoiding specific subgraphs.
- **Random graph theory** was initiated by Erdos and Renyi studying asymptotic connectivity.
