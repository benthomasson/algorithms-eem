---
source: sources/wiki-Binary_tree.md
source_url: https://en.wikipedia.org/wiki/Binary_tree
---

## Binary Tree: Structure, Types, and Properties

A binary tree is a tree data structure in which each node has at most two children, called the left child and the right child. It is a k-ary tree where k = 2. Formally, a binary tree is a triple (L, S, R) where L and R are binary trees or the empty set, and S is a singleton containing the root. From a graph theory perspective, binary trees are arborescences. Binary trees serve two primary purposes in computing: as a means of accessing nodes based on value/label (binary search trees, binary heaps) and as a representation of data with inherent bifurcating structure (Huffman coding, cladograms).

## Key Concepts

- **Binary tree**: A tree where each node has at most two children (left and right). A k-ary tree with k = 2.
- **Rooted binary tree**: Has a root node; every node has at most two children. All binary trees as defined in CS are rooted.
- **Full (proper/strict/plane) binary tree**: Every node has either 0 or 2 children — no node has exactly one child.
- **Perfect binary tree**: All interior nodes have exactly two children AND all leaves are at the same depth. A perfect tree is always full.
- **Complete binary tree**: Every level is completely filled except possibly the last, where nodes are packed as far left as possible. A perfect tree is always complete, but not vice versa. Can be efficiently stored in an array.
- **Balanced binary tree**: Left and right subtrees of every node differ in height by no more than 1.
- **Degenerate (pathological) tree**: Each parent has only one child — behaves like a linked list with O(n) search instead of O(log n).
- **Recursive definition (extended)**: Base case is the empty set; recursive step builds (r, T1, T2) from non-overlapping extended binary trees T1, T2 and a fresh root r.
- The number of full binary trees with n internal nodes equals the **Catalan number** C_n.
- Binary trees can represent elements of a **free magma** on a singleton set.

## Commands and Syntax

**Array storage (implicit data structure, 0-indexed):**
- Left child of node at index i: `2i + 1`
- Right child of node at index i: `2i + 2`
- Parent of node at index i: `floor((i - 1) / 2)`

**Array storage (1-indexed):**
- Left child: `2i`
- Right child: `2i + 1`
- Parent: `floor(i / 2)`

**OCaml type definition:**
```ocaml
type chr_tree = Empty | Node of char * chr_tree * chr_tree
```

**Node-and-references storage:** Each node holds data, a left pointer, a right pointer, and optionally a parent pointer. Null pointers waste space; threaded binary trees are a more space-efficient alternative.

## Relationships

- **Binary search tree (BST)**: A binary tree with an ordering invariant on node values — distinct concept from a plain binary tree.
- **Binary heap**: Uses a complete binary tree, typically stored as an array.
- **B-tree / B+ tree**: Multi-way trees, not binary — related but different.
- **k-ary tree (m-ary tree)**: Binary tree is the special case k = 2.
- **Huffman coding**: Uses binary trees to represent variable-length prefix codes.
- **Linked list**: A degenerate binary tree is structurally equivalent to a linked list.
- **Catalan numbers / Dyck language**: The count of structurally distinct full binary trees with n internal nodes is the nth Catalan number; bijection exists to Dyck words of length 2n.
- **Threaded binary tree**: Space-optimization of node-and-reference storage that replaces null pointers with in-order traversal links.
- **Self-balancing BST**: Maintains balanced structure to guarantee O(log n) operations.

## Exam-Relevant Points

- A full binary tree with height h has between **2h + 1** and **2^(h+1) − 1** nodes.
- A perfect binary tree has **2^h** leaves and **2^(h+1) − 1** total nodes at height h.
- In a perfect binary tree: **leaves = (n + 1) / 2** where n is total nodes.
- For any non-empty binary tree: **number of leaves = number of degree-2 nodes + 1** (l = i₂ + 1).
- **Edges = n − 1** in any binary tree with n nodes (every node except root has one incoming edge).
- **Null links in a binary tree of n nodes = n + 1**.
- Internal nodes in a complete binary tree of n nodes = **floor(n / 2)**.
- Minimum height with n nodes: **h_min = log₂(n + 1) − 1**.
- Minimum height with l leaves: **h_min = log₂(l)**.
- Complete binary trees can be stored in arrays with **zero wasted space**, using index arithmetic for parent/child navigation.
- The number of structurally distinct full binary trees with n internal nodes is the **nth Catalan number**.
- **Terminology is not standardized**: "complete" vs "perfect" definitions vary across textbooks — some authors call a perfect tree "complete" and use "almost complete" for what others call "complete."
- Array representation benefits from **locality of reference** and is the standard for binary heaps.
