---
source: sources/wiki-RedE28093black_tree.md
source_url: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
---

I need write permission to create the entry file. Could you grant write access so I can save the entry to `entries/2026/06/19/wiki-RedE28093black_tree.md`?

In the meantime, here's the structured summary:

## Red-Black Trees: Self-Balancing Binary Search Tree

A red-black tree is a self-balancing binary search tree where each node stores an extra color bit (red or black). The coloring constraints ensure the tree remains approximately balanced, guaranteeing O(log n) worst-case time for search, insertion, and deletion. Invented by Guibas and Sedgewick in 1978, red-black trees evolved from Bayer's symmetric binary B-trees (1972) and are structurally isomorphic to 2-3-4 trees.

## Key Concepts

- Each node is colored red or black; costs only 1 bit per node (sometimes zero via pointer alignment)
- **Black depth**: number of black ancestors from root to a node
- **Black height**: number of black nodes on any root-to-leaf path (constant by property 4)
- Longest root-to-leaf path is at most 2x the shortest, ensuring h ∈ O(log n)
- Rebalancing: O(log n) worst-case, O(1) amortized
- Insert requires at most 2 rotations; delete requires at most 3
- Read-only operations (search, traversal) are identical to standard BST

**Four invariant properties:**
1. Every node is red or black
2. All null nodes are considered black
3. No red node has a red child (no consecutive reds)
4. Every root-to-null path has the same number of black nodes

**Derived:** A node with exactly one child must have that child be red.

## Commands and Syntax

```c
typedef enum Color: char { BLACK, RED } Color;
typedef struct Node {
    struct Node* parent;
    struct Node* left;
    struct Node* right;
    Color color;
    int key;
} Node;
```

Rebalancing primitive: `rotate_subtree(tree, node, direction)`.

## Relationships

- **BST**: red-black tree is a specialization; all BST read operations apply unchanged
- **AVL tree**: stricter balancing (worst-case height 0.720× red-black); AVL trees are a subset of RB trees; AVL has faster lookups, RB has cheaper modifications
- **2-3-4 tree / B-tree**: structurally isomorphic (2-node → black, 3-node → black+red child, 4-node → black+2 red children); color flip = node split
- **LLRB**: Sedgewick's 2008 simplification; red links lean left only
- **Applications**: Linux CFS & epoll, Java 8+ HashMap collision chains, computational geometry, persistent functional data structures

## Exam-Relevant Points

- O(log n) **worst-case** for search, insert, delete — not just amortized
- Max rotations: 2 for insert, 3 for delete; recoloring O(log n) worst / O(1) amortized
- The four invariant properties and consequence: longest path ≤ 2× shortest
- Isomorphic to 2-3-4 trees; color flip = node split
- AVL is stricter (better search) vs RB (cheaper insert/delete)
- "Root is black" rule is non-essential — red root can always be recolored
- New nodes are inserted red to preserve black-height, potentially causing a red-violation
- Space overhead: 1 bit per node
