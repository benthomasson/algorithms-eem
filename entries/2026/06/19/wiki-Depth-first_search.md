---
source: sources/wiki-Depth-first_search.md
source_url: https://en.wikipedia.org/wiki/Depth-first_search
---

## Depth-First Search (DFS)

Depth-first search is a fundamental graph and tree traversal algorithm that explores as far as possible along each branch before backtracking. It uses a stack (either the call stack via recursion or an explicit stack) to track the current path. Originally investigated by Charles Pierre Trémaux in the 19th century as a maze-solving strategy, DFS is one of the two primary graph traversal methods alongside breadth-first search.

## Key Concepts

- **Core mechanism**: Start at a root node, explore each branch to its deepest point before backtracking. Uses a stack to track discovered nodes along the current path.
- **Time complexity**: O(|V| + |E|) for explicit graphs traversed without repetition; O(b^d) for implicit graphs with branching factor b searched to depth d.
- **Space complexity**: O(|V|) for full graph traversal (stores stack + visited set); O(bd) for depth-limited search on implicit graphs.
- **Not optimal**: DFS does not guarantee finding the shortest path.
- **Edge classification in DFS spanning tree**:
  - **Tree edges**: edges belonging to the spanning tree itself.
  - **Forward edges**: point from a node to one of its descendants.
  - **Back edges**: point from a node to one of its ancestors.
  - **Cross edges**: all other edges (neither ancestor nor descendant).
  - In undirected graphs, all edges are either tree edges or back edges.
- **Vertex orderings produced by DFS**:
  - **Preordering**: order of first visit (equivalent to Polish notation on expression trees).
  - **Postordering**: order of last visit (equivalent to reverse Polish notation).
  - **Reverse preordering**: reverse of preordering (not the same as postordering).
  - **Reverse postordering**: reverse of postordering (not the same as preordering); produces a topological sort on DAGs.
- **Non-termination risk**: On graphs with cycles, DFS without a visited set can loop forever. Iterative deepening DFS addresses this.
- **Sampling bias**: Incomplete DFS is biased toward nodes of high degree.
- **Parallel complexity**: Lexicographic DFS ordering is P-complete (inherently sequential). A randomized DFS ordering can be computed in RNC; whether a deterministic NC algorithm exists is an open problem.

## Commands and Syntax

**Recursive DFS:**
```
procedure DFS(G, v) is
    label v as discovered
    for all directed edges from v to w that are in G.adjacentEdges(v) do
        if vertex w is not labeled as discovered then
            recursively call DFS(G, w)
```

**Iterative DFS (stack of nodes)** — O(|E|) space, may have duplicate vertices on stack:
```
procedure DFS_iterative(G, v) is
    let S be a stack
    S.push(v)
    while S is not empty do
        v = S.pop()
        if v is not labeled as discovered then
            label v as discovered
            for all edges from v to w in G.adjacentEdges(v) do
                S.push(w)
```

**Iterative DFS (stack of iterators)** — produces same traversal order as recursive DFS:
```
procedure DFS_iterative(G, v) is
    let S be a stack
    label v as discovered
    S.push(iterator of G.adjacentEdges(v))
    while S is not empty do
        if S.peek().hasNext() then
            w = S.peek().next()
            if w is not labeled as discovered then
                label w as discovered
                S.push(iterator of G.adjacentEdges(w))
        else
            S.pop()
```

**Key implementation difference**: Recursive and iterator-based iterative DFS visit the first neighbor in adjacency list order. The stack-of-nodes iterative version visits neighbors in reverse order (last neighbor first) due to LIFO stack behavior.

**DFS vs BFS structural difference**: Replace the stack with a queue to convert DFS into BFS. The iterative DFS also delays the discovery check until pop (unlike BFS which checks before enqueue).

## Relationships

- **Breadth-First Search (BFS)**: The complementary traversal; same time/space complexity for full graph traversal, but uses a queue instead of a stack and produces different vertex orderings.
- **Iterative Deepening DFS (IDDFS)**: Combines DFS space efficiency with BFS completeness by running DFS with increasing depth limits. Only a constant-factor overhead when branching factor > 1.
- **Depth-Limited Search**: DFS variant that stops at a fixed depth; avoids non-termination but may miss deeper solutions.
- **Topological Sorting**: Reverse postorder of DFS produces a topological sort for directed acyclic graphs.
- **Strongly Connected Components**: Tarjan's and Kosaraju's algorithms use DFS as a building block.
- **Spanning Trees / Trémaux Trees**: DFS traversal edges form a spanning tree with applications in graph theory and planarity testing.
- **Stack (data structure)**: The core data structure enabling DFS's depth-priority behavior.

## Exam-Relevant Points

- Time complexity is O(|V| + |E|) for explicit graphs — know this precisely, not just "linear."
- Space complexity is O(|V|) for full traversal; O(bd) for depth-limited implicit graphs — this is DFS's main advantage over BFS for large/infinite graphs.
- DFS is **not optimal** — it does not find shortest paths.
- **Reverse postordering produces topological sort** on DAGs — a frequently tested fact.
- In undirected graphs, DFS produces only tree edges and back edges (no forward or cross edges).
- The iterative stack-of-nodes version visits neighbors in **reverse order** compared to the recursive version — a subtle but testable distinction.
- Lexicographic DFS ordering is **P-complete** (inherently hard to parallelize).
- DFS without a visited set on cyclic graphs leads to infinite loops; iterative deepening is the standard remedy.
- Preorder = Polish notation; postorder = reverse Polish notation on expression trees.
- Key applications to remember: connected components, topological sort, strongly connected components, bridges, biconnectivity, planarity testing, maze solving/generation.
