# Exam Results: algorithms-ds-practice.md

**Date:** 2026-06-22 15:33
**Model:** claude:sonnet
**Score:** 47/50 (94%)

## Per-Question Results

- **Q1**: CORRECT — What is the time complexity of accessing an element by index in an array?
- **Q2**: WRONG — What happens when a hash table's load factor exceeds a threshold?
  - Expected: The table is rehashed (resized and all elements reinserted), which is amortized O(1) per insertion.
  - Got: The table is resized
- **Q3**: CORRECT — Why can't a hash table efficiently support ordered operations like finding the minimum or successor?
- **Q4**: CORRECT — What is the time complexity of accessing the k-th element in a singly linked list?
- **Q5**: CORRECT — What is the purpose of a sentinel node in a linked list?
- **Q6**: CORRECT — What is an XOR linked list?
- **Q7**: CORRECT — How can you implement a queue using two stacks with amortized O(1) per operation?
- **Q8**: CORRECT — What data structure does DFS use and what does BFS use?
- **Q9**: CORRECT — In a binary tree stored as an array, what are the formulas for the left child, right child, and parent of node at index i?
- **Q10**: CORRECT — What is the relationship between the number of leaves and the number of degree-2 nodes in a binary tree?
- **Q11**: CORRECT — How does an AVL tree differ from a red-black tree in terms of balance strictness?
- **Q12**: WRONG — What is the 2-3-4 tree isomorphism of a red-black tree?
  - Expected: Every red-black tree corresponds to a 2-3-4 tree: a black node with no red children is a 2-node, with one red child is a 3-node, and with two red children is a 4-node.
  - Got: Red-black trees are structurally isomorphic to 2-3-4 trees through the following mapping: a 2-node maps to a black node, a 3-node maps to a black node with one red child, and a 4-node maps to a black node with two red children. Color flips in red-black trees correspond to node splits in 2-3-4 trees.
- **Q13**: CORRECT — Why are B-trees preferred for disk-based storage over binary search trees?
- **Q14**: CORRECT — What is the time complexity of building a binary heap from an unsorted array using Floyd's algorithm?
- **Q15**: CORRECT — What are the amortized bounds of a Fibonacci heap for insert and decrease-key?
- **Q16**: CORRECT — Why is a heap not suitable for searching for an arbitrary element?
- **Q17**: CORRECT — What is the lower bound on comparison-based sorting and why?
- **Q18**: CORRECT — Why is quicksort generally faster than merge sort in practice despite having worse worst-case complexity?
- **Q19**: CORRECT — What makes counting sort stable, and why does that matter for radix sort?
- **Q20**: CORRECT — What is the time complexity of radix sort and when is it linear?
- **Q21**: CORRECT — What is the time complexity of BFS and why does it find shortest paths in unweighted graphs?
- **Q22**: CORRECT — What are the four edge classifications in DFS on a directed graph?
- **Q23**: CORRECT — When can topological sort be performed on a graph?
- **Q24**: CORRECT — What is the difference between Kahn's algorithm and DFS-based topological sort?
- **Q25**: CORRECT — What is the time complexity of Dijkstra's algorithm with a Fibonacci heap?
- **Q26**: CORRECT — Why can't Dijkstra's algorithm handle negative edge weights?
- **Q27**: CORRECT — What is the time complexity of Bellman-Ford and what can it detect that Dijkstra cannot?
- **Q28**: CORRECT — What is the Floyd-Warshall algorithm used for and what is its complexity?
- **Q29**: CORRECT — Why does the loop order matter in Floyd-Warshall?
- **Q30**: CORRECT — What is the difference between Kruskal's and Prim's algorithms for MST, and when is each preferred?
- **Q31**: CORRECT — What two properties must a problem have for dynamic programming to apply?
- **Q32**: CORRECT — What is the difference between top-down and bottom-up dynamic programming?
- **Q33**: CORRECT — What is the time and space complexity of the standard LCS algorithm?
- **Q34**: CORRECT — Why is the 0/1 knapsack problem only pseudo-polynomial and not truly polynomial?
- **Q35**: CORRECT — What is Kadane's algorithm and what is its complexity?
- **Q36**: CORRECT — What is the Master Theorem used for?
- **Q37**: CORRECT — How does a greedy algorithm differ from dynamic programming?
- **Q38**: CORRECT — What is the exchange argument used for in greedy algorithm proofs?
- **Q39**: CORRECT — What is backtracking and when does it improve over brute force?
- **Q40**: CORRECT — What is the time complexity of operations in a trie and how does it compare to a BST?
- **Q41**: CORRECT — What is a Fenwick tree (Binary Indexed Tree) used for?
- **Q42**: CORRECT — What is the inverse Ackermann amortized bound for union-find, and what optimizations achieve it?
- **Q43**: WRONG — What is the formal definition of Big-O notation?
  - Expected: f(n) = O(g(n)) means there exist positive constants c and n0 such that f(n) <= c*g(n) for all n >= n0. It provides an asymptotic upper bound on growth rate.
  - Got: f(x) = O(g(x)) means there exists a positive constant M such that |f(x)| ≤ M·g(x) for all x in the domain
- **Q44**: CORRECT — Why is Big-O notation not an equality but a set membership?
- **Q45**: CORRECT — What is amortized analysis and how does it differ from average-case analysis?
- **Q46**: CORRECT — What are the three standard depth-first binary tree traversals and one application of each?
- **Q47**: CORRECT — What is Morris traversal and what makes it special?
- **Q48**: CORRECT — How can you reconstruct a binary tree from traversal sequences?
- **Q49**: CORRECT — Why does memoization require referential transparency (pure functions)?
- **Q50**: CORRECT — What is the time complexity of heapsort and why is it not stable?

## Wrong Answers (Detail)

### Q2: What happens when a hash table's load factor exceeds a threshold?
- **Expected:** The table is rehashed (resized and all elements reinserted), which is amortized O(1) per insertion.
- **Got:** The table is resized

**Model response:**

```
When a hash table's load factor α (defined as n/m, where n is the number of stored elements and m is the total number of buckets) exceeds a predetermined threshold α_max, the hash table is resized to maintain acceptable performance. This resizing operation typically involves creating a larger array (often doubling the capacity) and rehashing all existing elements into the new array using the updated hash function that accounts for the new size. This process ensures that operations like search, insert, and delete continue to have expected constant-time performance by preventing the table from becoming too crowded, which would lead to excessive collisions.
```

### Q12: What is the 2-3-4 tree isomorphism of a red-black tree?
- **Expected:** Every red-black tree corresponds to a 2-3-4 tree: a black node with no red children is a 2-node, with one red child is a 3-node, and with two red children is a 4-node.
- **Got:** Red-black trees are structurally isomorphic to 2-3-4 trees through the following mapping: a 2-node maps to a black node, a 3-node maps to a black node with one red child, and a 4-node maps to a black node with two red children. Color flips in red-black trees correspond to node splits in 2-3-4 trees.

**Model response:**

```
The belief database confirms that red-black trees are binary encodings of 2-3-4 trees (which are B-trees of order 4). The isomorphism preserves the structural properties: each node type in the 2-3-4 tree has a direct corresponding representation in the red-black tree using the color property. This relationship explains why the red-black tree invariants (which may seem arbitrary) are actually direct consequences of the B-tree structural constraints translated into binary tree form. The mapping ensures that both trees maintain the same balance properties and height guarantees.
```

### Q43: What is the formal definition of Big-O notation?
- **Expected:** f(n) = O(g(n)) means there exist positive constants c and n0 such that f(n) <= c*g(n) for all n >= n0. It provides an asymptotic upper bound on growth rate.
- **Got:** f(x) = O(g(x)) means there exists a positive constant M such that |f(x)| ≤ M·g(x) for all x in the domain

**Model response:**

```
The formal definition of Big-O notation is: f(x) = O(g(x)) if and only if there exists a positive constant M such that |f(x)| ≤ M·g(x) for all x in the domain. This definition establishes Big-O as an asymptotic upper bound, where the specific value of the constant M doesn't matter—only its existence is required. This formalism is essential for rigorous complexity analysis, though it's important to note that Big-O only provides an upper bound (not a tight bound), and that the tightest correct bound should be preferred to avoid uselessly loose characterizations like O(x^10) for a degree-4 polynomial.
```


## By Objective

- **None**: 47/50 (94%)
