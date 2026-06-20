---
source: sources/wiki-Binary_search_tree.md
source_url: https://en.wikipedia.org/wiki/Binary_search_tree
---

It seems you're denying the write permission. Would you like me to just output the summary text directly instead of writing it to a file? Or would you like me to adjust the file path or approach?

In the meantime, here's the structured summary:

---

## Binary Search Tree — Structure, Operations, and Balancing

A binary search tree (BST) is a rooted binary tree where each node's key is greater than all keys in its left subtree and less than all keys in its right subtree. This enables O(log n) average-case search, insert, and delete. Invented in 1960 (Windley, Booth, Colin, Hibbard; attributed to Berners-Lee and Wheeler). Without balancing, BSTs degenerate to linked lists with O(n) worst case.

## Key Concepts

- **BST property**: left < node < right (strict total order)
- **Average complexity**: Θ(log n) for search, insert, delete
- **Worst-case complexity**: O(n) — degenerate tree becomes a linked list
- **Space**: Θ(n) always
- **All costs are O(h)** where h = tree height; balanced trees guarantee h = O(log n)
- **Degeneracy**: sorted insertion produces height n
- **Successor**: smallest key greater than x — minimum of right subtree, or walk up to first left-child ancestor
- **Predecessor**: largest key smaller than x — maximum of left subtree, or walk up to first right-child ancestor
- **New nodes are always inserted as leaves**

## Commands and Syntax

**Search** (recursive or iterative): compare key at each node, go left if smaller, right if larger, until found or NIL.

**Insertion**: descend like search using a trailing pointer; attach new node as leaf at the NIL position.

**Deletion** — three cases:
1. Leaf: replace with NIL
2. One child: elevate the child
3. Two children: replace with in-order successor (min of right subtree); if successor isn't the immediate right child, first replace successor with its own right child

**Traversals**: Inorder (L, N, R) produces sorted order. Preorder (N, L, R). Postorder (L, R, N).

**Min/Max**: walk left/right until NIL.

## Relationships

- **Binary search**: BST is the tree analog of binary search on sorted arrays
- **Self-balancing variants**: AVL (1962, first), red-black, treap, B-tree, 2-3 tree, splay tree, T-tree
- **Height-balanced** (AVL, red-black) vs **weight-balanced** (by leaf count, α-ratio)
- **Implements**: dynamic sets, multisets, associative arrays, lookup tables, priority queues
- **Sorting**: tree sort = insert all + inorder traversal; also used in quicksort
- **Priority queues**: min for ascending, max for descending

## Exam-Relevant Points

- Inorder traversal of BST yields sorted order — defining characteristic
- Average Θ(log n), worst O(n) — know why (height depends on insertion order)
- Deletion with two children: use in-order successor OR predecessor (either valid)
- Self-balancing BSTs guarantee O(log n) worst-case; AVL was first (1962)
- Sorted insertion is the classic degeneracy scenario
- New nodes always inserted as leaves
- Successor: right subtree min, or walk-up algorithm
- Tree sort: O(n log n) average, O(n²) worst
- Space always Θ(n)
- BST property (left < node < right) vs heap property (parent vs children) — common exam contrast
