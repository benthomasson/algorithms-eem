# Exam Results: algorithms-ds-practice.md

**Date:** 2026-06-22 15:56
**Model:** claude:haiku
**Score:** 48/50 (96%)

## Per-Question Results

- **Q1**: CORRECT — What is the time complexity of accessing an element by index in an array?
- **Q2**: CORRECT — What happens when a hash table's load factor exceeds a threshold?
- **Q3**: CORRECT — Why can't a hash table efficiently support ordered operations like finding the minimum or successor?
- **Q4**: CORRECT — What is the time complexity of accessing the k-th element in a singly linked list?
- **Q5**: CORRECT — What is the purpose of a sentinel node in a linked list?
- **Q6**: CORRECT — What is an XOR linked list?
- **Q7**: CORRECT — How can you implement a queue using two stacks with amortized O(1) per operation?
- **Q8**: CORRECT — What data structure does DFS use and what does BFS use?
- **Q9**: CORRECT — In a binary tree stored as an array, what are the formulas for the left child, right child, and parent of node at index i?
- **Q10**: CORRECT — What is the relationship between the number of leaves and the number of degree-2 nodes in a binary tree?
- **Q11**: CORRECT — How does an AVL tree differ from a red-black tree in terms of balance strictness?
- **Q12**: CORRECT — What is the 2-3-4 tree isomorphism of a red-black tree?
- **Q13**: CORRECT — Why are B-trees preferred for disk-based storage over binary search trees?
- **Q14**: CORRECT — What is the time complexity of building a binary heap from an unsorted array using Floyd's algorithm?
- **Q15**: CORRECT — What are the amortized bounds of a Fibonacci heap for insert and decrease-key?
- **Q16**: CORRECT — Why is a heap not suitable for searching for an arbitrary element?
- **Q17**: CORRECT — What is the lower bound on comparison-based sorting and why?
- **Q18**: CORRECT — Why is quicksort generally faster than merge sort in practice despite having worse worst-case complexity?
- **Q19**: CORRECT — What makes counting sort stable, and why does that matter for radix sort?
- **Q20**: WRONG — What is the time complexity of radix sort and when is it linear?
  - Expected: O(d(n+k)) where d is the number of digits and k is the radix. It is effectively linear when d is constant (bounded key length) and k is O(n).
  - Got: O(d*(n+k)) where d=digits, n=elements, k=radix; linear O(n) when d is constant
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
- **Q40**: WRONG — What is the time complexity of operations in a trie and how does it compare to a BST?
  - Expected: Trie operations (insert, search, delete) are O(m) where m is the key length, independent of the number of keys. A BST takes O(m log n) because each of the O(log n) comparisons takes O(m) time for string keys.
  - Got: Trie: O(m) where m is key length; BST: O(log n) average for balanced trees
- **Q41**: CORRECT — What is a Fenwick tree (Binary Indexed Tree) used for?
- **Q42**: CORRECT — What is the inverse Ackermann amortized bound for union-find, and what optimizations achieve it?
- **Q43**: CORRECT — What is the formal definition of Big-O notation?
- **Q44**: CORRECT — Why is Big-O notation not an equality but a set membership?
- **Q45**: CORRECT — What is amortized analysis and how does it differ from average-case analysis?
- **Q46**: CORRECT — What are the three standard depth-first binary tree traversals and one application of each?
- **Q47**: CORRECT — What is Morris traversal and what makes it special?
- **Q48**: CORRECT — How can you reconstruct a binary tree from traversal sequences?
- **Q49**: CORRECT — Why does memoization require referential transparency (pure functions)?
- **Q50**: CORRECT — What is the time complexity of heapsort and why is it not stable?

## Wrong Answers (Detail)

### Q20: What is the time complexity of radix sort and when is it linear?
- **Expected:** O(d(n+k)) where d is the number of digits and k is the radix. It is effectively linear when d is constant (bounded key length) and k is O(n).
- **Got:** O(d*(n+k)) where d=digits, n=elements, k=radix; linear O(n) when d is constant

**Model response:**

```
```json
{"answer": "O(d*(n+k)) where d=digits, n=elements, k=radix; linear O(n) when d is constant", "explanation": "Radix sort processes each digit position independently, making d passes through n elements, using O(n+k) work per pass (counting sort for each digit where k is the radix base). This yields O(d*(n+k)) total complexity. It achieves linear time O(n) when the number of digits d is constant, which is true for fixed-width integers (e.g., 32-bit or 64-bit numbers have constant d regardless of n). In such cases, radix sort beats comparison-based sorts' O(n log n) lower bound because it doesn't compare elements directly but exploits the structure of the input representation."}
```
```

### Q40: What is the time complexity of operations in a trie and how does it compare to a BST?
- **Expected:** Trie operations (insert, search, delete) are O(m) where m is the key length, independent of the number of keys. A BST takes O(m log n) because each of the O(log n) comparisons takes O(m) time for string keys.
- **Got:** Trie: O(m) where m is key length; BST: O(log n) average for balanced trees

**Model response:**

```
```json
{
  "answer": "Trie: O(m) where m is key length; BST: O(log n) average for balanced trees",
  "explanation": "Trie operations (search, insert, delete) have time complexity O(m) where m is the length of the key being processed, regardless of the number of elements stored. In contrast, BST operations have O(log n) average time complexity (O(n) worst case) where n is the number of elements, making the complexity dependent on dataset size rather than key length. Tries excel at prefix-based queries and when key length is bounded and small; BSTs maintain sorted order and are more space-efficient for long keys or small datasets. For example, a trie with 1 million 5-character words searches in O(5) = constant time, while a BST requires O(log 1,000,000) ≈ O(20) comparisons—but each BST comparison might involve expensive string operations, whereas trie operations always do work proportional to key length."
}
```
```


## By Objective

- **None**: 48/50 (96%)
