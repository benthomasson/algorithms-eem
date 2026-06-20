---
source: sources/wiki-Tree_traversal.md
source_url: https://en.wikipedia.org/wiki/Tree_traversal
---

## Tree Traversal Algorithms

Tree traversal (also called tree search or walking the tree) is a form of graph traversal that visits each node in a tree data structure exactly once. Traversals are classified by the order in which nodes are visited and fall into two major categories: depth-first search (DFS) and breadth-first search (BFS). The algorithms are typically described for binary trees but generalize to arbitrary trees.

## Key Concepts

- **Depth-first search (DFS)**: Deepens as far as possible before visiting siblings. Implemented via a **stack** (explicit or implicit call stack).
- **Breadth-first search (BFS) / Level-order**: Visits all nodes at the current depth before moving deeper. Implemented via a **queue**.
- **Three DFS orderings** for binary trees, defined by when the node is visited relative to its subtrees:
  - **Pre-order (NLR)**: Visit node, then left subtree, then right subtree. Produces a topologically sorted sequence (parent before children).
  - **In-order (LNR)**: Left subtree, visit node, right subtree. On a BST, yields keys in **ascending sorted order**.
  - **Post-order (LRN)**: Left subtree, right subtree, visit node. Useful for generating postfix expressions and for deletion (children freed before parent).
- **Reverse variants** (NRL, RLN, RNL) mirror the standard orderings by swapping left/right. Reverse in-order on a BST yields **descending** order.
- **Sequentialisation**: The trace of visited nodes. Pre-order or post-order **paired with in-order** uniquely determines a tree with distinct elements. Pre-order + post-order alone is ambiguous.
- **Morris traversal**: An in-order traversal using **threading** (null child pointers repurposed to point to in-order predecessor/successor). Achieves O(1) extra space by temporarily modifying tree structure, then restoring it.
- **Deferred nodes**: Since trees are non-linear, some nodes must be stored for later visiting -- via stack (DFS) or queue (BFS).
- **Amortized complexity** of sequential in-order traversal via `inorderNext`: O(1) per step amortized (full traversal takes 2n-2 steps). Worst-case per step: O(h) where h is tree height.

## Commands and Syntax

**Recursive DFS implementations:**
```
// Pre-order
procedure preorder(node)
    if node = null return
    visit(node)
    preorder(node.left)
    preorder(node.right)

// In-order
procedure inorder(node)
    if node = null return
    inorder(node.left)
    visit(node)
    inorder(node.right)

// Post-order
procedure postorder(node)
    if node = null return
    postorder(node.left)
    postorder(node.right)
    visit(node)
```

**Iterative pre-order (explicit stack):**
```
procedure iterativePreorder(node)
    if node = null return
    stack ← empty stack
    stack.push(node)
    while not stack.isEmpty()
        node ← stack.pop()
        visit(node)
        if node.right ≠ null  stack.push(node.right)  // right first so left processed first
        if node.left ≠ null   stack.push(node.left)
```

**BFS / Level-order (queue-based):**
```
procedure levelorder(node)
    queue ← empty queue
    queue.enqueue(node)
    while not queue.isEmpty()
        node ← queue.dequeue()
        visit(node)
        if node.left ≠ null   queue.enqueue(node.left)
        if node.right ≠ null  queue.enqueue(node.right)
```

**Array-stored tree**: Level-order is simply iterating index 0 through size-1.

## Relationships

- **Graph traversal**: Tree traversal is a specialization of graph traversal.
- **Binary search trees**: In-order traversal is the canonical way to retrieve BST elements in sorted order.
- **Expression trees**: Pre-order produces prefix notation (Polish notation); post-order produces postfix notation (Reverse Polish notation), directly translatable to stack machine code.
- **Stack / Queue ADTs**: DFS uses a stack; BFS uses a queue -- the data structure choice determines traversal order.
- **Iterative deepening DFS**: A hybrid that combines DFS space efficiency with BFS completeness; relevant for infinite or very large trees.
- **Threaded binary trees**: Enable Morris traversal, eliminating the need for a stack or recursion.
- **Topological sorting**: Pre-order traversal produces a topologically sorted sequence (parent before children).
- **Monte Carlo tree search**: An alternative traversal that uses random sampling rather than exhaustive DFS/BFS.

## Exam-Relevant Points

- **DFS = stack, BFS = queue** -- this mapping is a fundamental and frequently tested fact.
- **In-order on a BST gives sorted (ascending) output**; reverse in-order gives descending.
- **Pre-order + in-order** (or post-order + in-order) **uniquely reconstructs a binary tree**. Pre-order + post-order does **not**.
- Know the visit order for each traversal on a sample tree (e.g., for tree F-B-A-D-C-E-G-I-H: pre-order = F,B,A,D,C,E,G,I,H; in-order = A,B,C,D,E,F,G,H,I; post-order = A,C,E,D,B,H,I,G,F).
- **Space complexity**: Recursive and iterative stack-based DFS both require O(h) space. BFS requires O(w) space where w is maximum width (up to n/2). Morris traversal uses O(1) extra space.
- **Iterative post-order** is the most complex of the three iterative DFS implementations (requires tracking `lastNodeVisited`).
- Pre-order is used to **copy** a tree; post-order is used to **delete** a tree.
- **Infinite trees**: BFS traverses any tree with bounded branching factor but fails on infinite branching. DFS traverses infinite depth with finite branching but fails on infinite depth. Hybrid diagonal methods can traverse any countably infinite tree.
- Morris traversal trades simplicity for O(1) space -- it temporarily modifies the tree and cannot run concurrent traversals.
