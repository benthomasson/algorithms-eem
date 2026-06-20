---
source: sources/wiki-Topological_sorting.md
source_url: https://en.wikipedia.org/wiki/Topological_sorting
---

## Topological Sorting of Directed Acyclic Graphs

Topological sorting produces a linear ordering of vertices in a directed acyclic graph (DAG) such that for every directed edge (u, v), vertex u appears before v. It is equivalent to visiting each node only after all its dependencies have been visited. A topological ordering exists if and only if the graph has no directed cycles, and any DAG has at least one such ordering. Multiple valid orderings typically exist for a given DAG.

## Key Concepts

- **Definition**: A linear ordering of DAG vertices where every edge (u, v) has u before v in the sequence
- **Existence condition**: A topological ordering exists **if and only if** the graph is a DAG (no directed cycles)
- **Non-uniqueness**: A DAG typically has multiple valid topological orderings; the ordering is unique if and only if a Hamiltonian path exists in the DAG
- **Time complexity**: Both standard algorithms (Kahn's and DFS-based) run in **O(|V| + |E|)** linear time
- **Disconnected components**: Topological sorting works even when the DAG has disconnected components
- **Relation to partial orders**: A topological ordering of a DAG is equivalent to a linear extension of the partial order defined by reachability in the DAG
- **Uniqueness test**: If all consecutive pairs in the sorted order are connected by edges, a Hamiltonian path exists and the ordering is unique; this can be tested in linear time despite Hamiltonian path being NP-hard for general directed graphs
- **Parallel complexity**: Topological ordering is in NC2 — constructible in O((log n)^2) time with polynomial processors on a PRAM

## Commands and Syntax

**Kahn's Algorithm** (BFS-based, iterative removal of zero-indegree nodes):
```
L ← Empty list (sorted output)
S ← Set of all nodes with no incoming edge

while S is not empty do
    remove a node n from S
    add n to L
    for each node m with an edge e from n to m do
        remove edge e from the graph
        if m has no other incoming edges then
            insert m into S

if graph has edges then
    return error   (graph has at least one cycle)
else
    return L
```
- S can be a set, queue, or stack — the choice determines which valid ordering is produced
- Lexicographic tie-breaking variant is used in the Coffman-Graham algorithm

**DFS-based Algorithm** (Tarjan 1976, Cormen et al. 2001):
```
L ← Empty list (sorted output)
while exists nodes without a permanent mark do
    select an unmarked node n
    visit(n)

function visit(node n)
    if n has a permanent mark then return
    if n has a temporary mark then stop   (cycle detected)
    mark n with a temporary mark
    for each node m with an edge from n to m do
        visit(m)
    mark n with a permanent mark
    add n to head of L
```
- Nodes are **prepended** to L (added to head), ensuring all dependents appear after their dependencies

**DAG Shortest Path** (using topological order):
```
d[s] = 0, all other d[u] = ∞
p[u] = nil for all u

for each vertex u in topological order starting from s:
    for each edge (u, v) with weight w:
        if d[v] > d[u] + w:
            d[v] = d[u] + w
            p[v] = u
```
- Runs in **Θ(n + m)** time — faster than Dijkstra for DAGs

## Relationships

- **Directed Acyclic Graph (DAG)**: Prerequisite structure; topological sort is defined only for DAGs
- **Depth-First Search**: Foundation of the DFS-based topological sort algorithm
- **Shortest Path Problem**: Topological order enables linear-time shortest paths in weighted DAGs, outperforming Dijkstra's algorithm
- **Critical Path Method (CPM/PERT)**: Topological sort is the basis for finding critical paths in project scheduling
- **Partial Orders / Linear Extensions**: Topological ordering is the graph-theoretic equivalent of computing a linear extension of a partial order
- **Strongly Connected Components (Tarjan's SCC)**: Produces a topologically sorted list of SCCs; related algorithm by the same author
- **Feedback Arc Set**: Edges whose removal makes topological sorting possible on a cyclic graph
- **Coffman-Graham Algorithm**: Uses lexicographic Kahn's variant for parallel scheduling and layered graph drawing
- **Hamiltonian Path**: Unique topological order ↔ existence of a directed Hamiltonian path in the DAG
- **Hu's Algorithm**: Extends topological sort for scheduling optimization with processing times

## Exam-Relevant Points

- Topological sort exists **if and only if** the graph is a DAG — this is the fundamental theorem
- Both Kahn's and DFS algorithms run in **O(|V| + |E|)** time
- **Kahn's algorithm** detects cycles by checking if edges remain after processing; **DFS** detects cycles via temporary marks (back edges)
- The topological ordering is **unique** iff consecutive vertices in the ordering are all connected by edges (Hamiltonian path)
- DAG shortest paths via topological order run in **Θ(n + m)**, which is optimal and works with negative edge weights (unlike Dijkstra)
- In Kahn's algorithm, the data structure for S (set/queue/stack) determines which valid ordering is produced but does not affect correctness
- DFS-based algorithm adds nodes to the **head** of the output list (prepend), not the tail
- Parallel topological sort on PRAM is in **NC2**: O((log n)^2) time with polynomial processors
- Applications: task scheduling, makefile compilation order, spreadsheet formula evaluation, instruction scheduling, linker symbol resolution, database foreign key table loading
- Historical note: first studied in context of PERT (1960s project management); Kahn's algorithm published 1962; DFS variant by Tarjan 1976
