---
source: sources/wiki-Heap_data_structure.md
source_url: https://en.wikipedia.org/wiki/Heap_(data_structure)
---

Here is the structured summary for the Heap (data structure) Wikipedia page:

---

## Heap Data Structure

A heap is a tree-based data structure that satisfies the **heap property**: in a max-heap, every parent node's key is greater than or equal to its children's keys; in a min-heap, every parent's key is less than or equal to its children's. The heap is the canonical implementation of a priority queue and supports efficient repeated extraction of the maximum (or minimum) element. Introduced by J. W. J. Williams in 1964 alongside heapsort, heaps are foundational to sorting algorithms, graph algorithms, and scheduling problems.

## Key Concepts

- **Heap property**: Parent-child ordering invariant — max-heap (parent >= child) or min-heap (parent <= child). Only vertical relationships are constrained; siblings and cousins have no ordering.
- **Root node**: The top element with no parent; always holds the maximum (max-heap) or minimum (min-heap) value.
- **Partial ordering**: A heap is NOT a sorted structure — it is only partially ordered by the parent-child relationship.
- **Complete binary tree**: The most common heap form (binary heap) is a complete binary tree, giving it the smallest possible height: O(log n).
- **In-place storage**: Heaps are typically stored implicitly in an array with no extra memory for node pointers — structure is encoded in index arithmetic.
- **Priority queue**: An abstract data type that heaps implement maximally efficiently. "Heap" and "priority queue" are often used interchangeably.
- **No sibling ordering**: Unlike a binary search tree, there is no ordering between siblings or cousins and no meaningful in-order traversal.

## Operations and Complexity

### Basic Operations
- **find-max / find-min (peek)**: Return the root element — O(1).
- **insert (push)**: Add element at the end, then sift-up — O(log n) for binary heap.
- **extract-max / extract-min (pop)**: Remove root, move last element to root, sift-down — O(log n).
- **replace**: Pop root and push new key in one operation — more efficient than separate pop + push since it balances only once.

### Creation Operations
- **heapify (make-heap)**: Build a heap from an unsorted array — O(n) using Floyd's algorithm (bottom-up construction). This is faster than n successive insertions which cost O(n log n).
- **merge / union**: Join two heaps preserving originals.
- **meld**: Join two heaps, destroying originals.

### Internal Operations
- **sift-up (swim)**: Move a node upward to restore heap property after insertion.
- **sift-down (sink)**: Move a node downward to restore heap property after deletion/replacement.
- **increase-key / decrease-key**: Update a key within the heap.

## Commands and Syntax

### Array Index Formulas (0-based indexing)
```
Left child of node i:   2i + 1
Right child of node i:  2i + 2
Parent of node i:       floor((i - 1) / 2)
```

### Array Index Formulas (1-based indexing)
```
Left child of node i:   2i
Right child of node i:  2i + 1
Parent of node i:       floor(i / 2)
```

### Insertion Procedure
1. Add new element at the end of the array (first free position).
2. Sift-up: compare with parent, swap if heap property violated, repeat until correct position.

### Extraction Procedure
1. Remove root element.
2. Move last element to root position.
3. Sift-down: compare with children, swap with larger (max-heap) or smaller (min-heap) child, repeat.

### Replace Procedure
1. Remove root and place new element at root.
2. Sift-down only (no sift-up needed) — saves one balancing pass vs. extract + insert.

### Floyd's Build-Heap Algorithm
- Bottom-up construction: sift-down from the last non-leaf node to the root.
- Time: Theta(n) — linear, NOT O(n log n).

### Standard Library Implementations
| Language | API | Type |
|----------|-----|------|
| Python | `heapq` module (`heappush`, `heappop`, `heapreplace`, `heapify`) | Min-heap |
| Java | `java.util.PriorityQueue` | Min-heap (default) |
| C++ | `std::priority_queue`, `make_heap`, `push_heap`, `pop_heap` | Max-heap (default) |
| Rust | `std::collections::BinaryHeap` | Max-heap |
| Go | `container/heap` package | Interface-based |
| .NET | `PriorityQueue<TElement, TPriority>` (.NET 6+) | Min-heap (quaternary) |

## Heap Variants and Complexity Comparison

| Variant | find-max | delete-max | insert | increase-key | meld |
|---------|----------|------------|--------|--------------|------|
| **Binary** | Theta(1) | Theta(log n) | Theta(log n) | Theta(log n) | Theta(n) |
| **Binomial** | Theta(1) | Theta(log n) | Theta(1) am. | Theta(log n) | Theta(log n) |
| **Fibonacci** | Theta(1) | O(log n) am. | Theta(1) | Theta(1) am. | Theta(1) |
| **Pairing** | Theta(1) | O(log n) am. | Theta(1) | o(log n) am. | Theta(1) |
| **Strict Fibonacci** | Theta(1) | Theta(log n) | Theta(1) | Theta(1) | Theta(1) |
| **Brodal queue** | Theta(1) | Theta(log n) | Theta(1) | Theta(1) | Theta(1) |

- **Brodal queues** and **Strict Fibonacci heaps** achieve optimal worst-case bounds for all operations.
- **Fibonacci heaps** achieve optimal amortized bounds and are practically important for graph algorithms.

## Relationships

- **Priority Queue**: Heap is the standard implementation of the priority queue ADT.
- **Heapsort**: Uses a binary heap to achieve O(n log n) in-place sorting with no quadratic worst case.
- **Dijkstra's Algorithm**: Uses a min-heap; Fibonacci heap gives O(E + V log V).
- **Prim's Algorithm**: Uses a min-heap for minimum spanning tree construction.
- **Binary Search Tree**: Unlike BSTs, heaps have no sibling ordering and no efficient search for arbitrary elements.
- **Binary Tree**: A binary heap is specifically a complete binary tree.
- **Array Data Structure**: Heaps use arrays with implicit tree structure via index arithmetic.
- **K-way Merge**: Heaps efficiently merge k sorted streams.
- **Selection Algorithms**: Heaps enable sub-linear selection after initial O(n) construction.
- **Amortized Analysis**: Many advanced heap variants rely on amortized analysis for their bounds.

## Exam-Relevant Points

- **Heap property definition**: Max-heap: parent >= children. Min-heap: parent <= children. Only vertical relationships — no sibling ordering.
- **Array representation formulas**: Children at 2i+1, 2i+2; parent at floor((i-1)/2) for 0-based indexing.
- **Build-heap is O(n), NOT O(n log n)**: Floyd's bottom-up algorithm achieves linear time. Repeated insertion is O(n log n).
- **find-max is always O(1)**: Constant time access regardless of heap variant.
- **Binary heap operations**: insert O(log n), extract-max O(log n), find-max O(1), merge O(n).
- **Fibonacci heap advantages**: O(1) amortized insert and decrease-key make it superior for Dijkstra's and Prim's.
- **Heap vs. BST**: Heaps do NOT support efficient search, ordered traversal, or predecessor/successor queries.
- **Heapsort properties**: O(n log n) worst case, in-place, not stable.
- **Replace operation**: More efficient than extract + insert — only one sift-down pass.
- **Complete binary tree**: All levels full except possibly the last, filled left-to-right.
- **Brodal queue / Strict Fibonacci heap**: Theoretically optimal worst-case bounds — Theta(1) for everything except delete-max (Theta(log n)).
- **No extra memory**: Array-based heaps require no pointer overhead.

---
*Source: Wikipedia — Heap (data structure)*

I wasn't able to write this to the entries file due to permission restrictions, but the full structured summary is above. Would you like me to try saving it again?
