---
source: sources/wiki-Backtracking.md
source_url: https://en.wikipedia.org/wiki/Backtracking
---

## Backtracking: Algorithmic Paradigm for Constraint Satisfaction and Enumeration

Backtracking is a class of algorithms that incrementally builds candidate solutions and abandons ("backtracks" from) any candidate as soon as it determines that candidate cannot be completed to a valid solution. It is a metaheuristic — a general algorithmic framework rather than a specific algorithm — that is guaranteed to find all solutions to a finite problem in bounded time. The term was coined by D. H. Lehmer in the 1950s.

## Key Concepts

- **Partial candidates**: Solutions are built incrementally; at any point, a partial candidate represents a solution-in-progress that may or may not be completable
- **Search tree**: Partial candidates form a tree structure (the "potential search tree") where each node extends its parent by one step; leaves are candidates that cannot be extended further
- **Depth-first traversal**: The algorithm traverses the search tree recursively in depth-first order from the root
- **Pruning**: When a node `c` cannot lead to a valid solution, its entire subtree is skipped — this is the source of backtracking's efficiency over brute-force search
- **Actual vs. potential tree**: The algorithm only visits a subset of the full potential tree; total cost = (nodes in actual tree) x (cost per node)
- **Applicability requirement**: The problem must admit (1) a concept of "partial candidate solution" and (2) a relatively quick test for whether it can be completed to a valid solution
- **Not a heuristic**: Unlike many metaheuristics, backtracking is complete — it guarantees finding all solutions (or proving none exist) for finite problems
- **Variable ordering**: Ordering variables so the most constrained (fewest options or greatest impact) come first improves efficiency
- **Constraint propagation**: A technique that can further improve backtracking by reducing domains of unassigned variables after each assignment

## Commands and Syntax

### Core pseudocode — six procedural parameters define the problem:

| Procedure | Purpose |
|-----------|---------|
| `root(P)` | Return the partial candidate at the root of the search tree |
| `reject(P, c)` | Return `true` only if candidate `c` is not worth completing |
| `accept(P, c)` | Return `true` if `c` is a complete, valid solution |
| `first(P, c)` | Generate the first extension of candidate `c` |
| `next(P, s)` | Generate the next alternative extension after `s` |
| `output(P, c)` | Use/report the solution `c` |

### Generic backtracking procedure:
```
procedure backtrack(P, c) is
    if reject(P, c) then return
    if accept(P, c) then output(P, c)
    s <- first(P, c)
    while s != NULL do
        backtrack(P, s)
        s <- next(P, s)
```

### Constraint satisfaction specialization (variables x[1]..x[n], each in {1..m}):
```
function first(P, c) is
    k <- length(c)
    if k = n then return NULL
    else return (c[1], c[2], ..., c[k], 1)

function next(P, s) is
    k <- length(s)
    if s[k] = m then return NULL
    else return (s[1], s[2], ..., s[k-1], 1 + s[k])
```

## Relationships

- **Depth-first search**: Backtracking traverses the search tree in DFS order; DFS is the underlying traversal strategy
- **Brute-force search**: Backtracking with a `reject` that always returns `false` degenerates to brute-force enumeration — pruning is what distinguishes it
- **Constraint satisfaction problems (CSPs)**: Backtracking is a primary solving technique; enhanced by constraint propagation
- **Combinatorial optimization**: Applied to knapsack problem, parsing, and similar problems
- **DPLL algorithm**: Uses backtracking to solve Boolean satisfiability (SAT)
- **Backjumping**: An enhancement that jumps back further than one level when a dead end is found, reducing the search space
- **Dynamic programming**: An alternative paradigm; where backtracking explores a tree, DP exploits overlapping subproblems via memoization
- **Recursion**: Backtracking is inherently recursive in structure
- **Programming languages**: Icon, Planner, Prolog, and SNOBOL use backtracking as a core execution strategy

## Exam-Relevant Points

- Backtracking is **depth-first** traversal of an implicit search tree with **pruning** — not BFS
- The `reject` function must return `true` **only** when it is certain no extension can succeed; a false `true` causes missed solutions; a false `false` merely reduces efficiency
- Efficiency depends on `reject` returning `true` as close to the root as possible — early pruning eliminates the largest subtrees
- The algorithm is **complete** (finds all solutions) and **sound** (only reports valid solutions), unlike many metaheuristics
- Solutions need not be leaves of the search tree — intermediate nodes can also be valid solutions
- The algorithm can be modified for **early stopping**: stop after first solution, after N solutions, after a time budget, or after testing N candidates
- For CSPs with conjunctive constraints (F = F[1] AND F[2] AND ... AND F[p]), `reject` only needs to check terms involving the most recently assigned variable x[k], since earlier terms were checked higher in the tree
- **Variable trail** or **timestamps** are implementation techniques for efficiently undoing assignments during backtracking
- Time complexity: worst case explores the full search tree (e.g., O(m^n) for CSP with n variables, m values each), but pruning typically makes it much faster in practice
- Classic example: the **eight queens puzzle** — place 8 queens on a chessboard with no mutual attacks
