---
source: sources/wiki-Queue_abstract_data_type.md
source_url: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
---

## Queue (Abstract Data Type)

A queue is a fundamental abstract data type that maintains an ordered collection of elements following the **First-In-First-Out (FIFO)** principle. Elements are added at the rear (enqueue) and removed from the front (dequeue). This page covers the queue's operations, complexity guarantees, implementation strategies (arrays, linked lists, purely functional), and its role as a linear data structure used extensively in scheduling, buffering, and graph traversal.

## Key Concepts

- **FIFO ordering**: the first element enqueued is the first dequeued; all earlier elements must be removed before a later one becomes accessible
- **Core operations**: **enqueue** (add to rear), **dequeue** (remove from front), and optionally **peek/front** (inspect front element without removal)
- **Time complexity**: enqueue O(1), dequeue O(1), search O(n); space O(n)
- **Bounded queue**: a queue with a fixed maximum capacity; attempting to enqueue beyond capacity causes **overflow**; dequeuing from an empty queue causes **underflow**
- **Circular buffer implementation**: a fixed-length array treated as a circle using modular arithmetic on indices, avoiding costly element shifting
- **Linked list implementation**: a doubly linked list gives O(1) at both ends naturally; a singly linked list achieves this by maintaining a pointer to both the first and last node
- **Deque generalization**: a queue can be viewed as a restricted double-ended queue (deque)

## Commands and Syntax

**TypeScript implementation:**
```typescript
class Queue<T> {
    private items: T[] = [];

    enqueue(element: T): void {
        this.items.push(element);
    }

    dequeue(): T | undefined {
        return this.items.shift();
    }

    isEmpty(): boolean {
        return this.items.length === 0;
    }
}
```

**Language-specific queue access:**
- **C++ STL**: `std::queue` — push/pop only
- **Java**: `Queue` interface (since J2SE 5.0), implemented by `LinkedList` and `ArrayDeque`
- **Perl/Ruby**: use `push`/`shift` (or `unshift`/`pop`) on arrays
- **PHP**: `SplQueue` class

## Relationships

- **Stack**: the "opposite" data structure — Last-In-First-Out (LIFO) instead of FIFO
- **Double-ended queue (deque)**: generalization allowing insertion/removal at both ends; queue is a restricted deque
- **Priority queue**: elements are dequeued by priority rather than insertion order
- **Circular buffer**: a common array-based implementation technique for bounded queues
- **Linked list / doubly linked list**: standard pointer-based implementations
- **Breadth-first search (BFS)**: uses a queue to explore graph nodes level by level
- **Buffer**: queues serve as buffers in I/O, networking, and event processing
- **Event loop / message queue**: real-world applications where queues manage asynchronous work

## Exam-Relevant Points

- Enqueue and dequeue are both **O(1)**; search is **O(n)** — know why search isn't constant (no indexing, must traverse)
- A circular buffer avoids element shifting by using **modular index arithmetic** (`index mod n`); the array logically wraps around
- **Amortized queue** (purely functional): uses two singly linked lists (front `f` and reversed rear `r`); enqueue is O(1), dequeue is amortized O(1) because the O(n) reverse of `f` into `r` is charged across all prior insertions
- **Real-time queue**: achieves **worst-case O(1)** for all operations using three lists `(f, r, s)` with lazy evaluation and memoization; the schedule list `s` incrementally forces computation of `f` so no single operation bears the full reversal cost
- The invariant of the real-time queue is `|s| = |f| - |r|`; when `s` is empty, `|f| = |r|` and a rotation is triggered
- A singly linked list needs a **tail pointer** (in addition to head) to implement an efficient queue
- Overflow = enqueue on full bounded queue; underflow = dequeue on empty queue
- Queues are **linear data structures** (elements form a sequence), contrasted with trees and graphs
- BFS relies on a queue; DFS relies on a stack — a classic exam comparison point
