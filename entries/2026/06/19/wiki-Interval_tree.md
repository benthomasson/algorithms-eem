---
source: sources/wiki-Interval_tree.md
source_url: https://en.wikipedia.org/wiki/Interval_tree
---

## Interval Tree: Tree Data Structure for Overlapping Interval Queries

An interval tree is a tree data structure designed to hold intervals and efficiently find all intervals that overlap with a given interval or point. It solves the problem that naïve approaches (brute-force or dual binary search trees) cannot: achieving output-sensitive query time of O(log n + m) rather than O(n). Two principal designs exist — the **centered interval tree** and the **augmented tree** — each with different trade-offs for construction, querying, and dynamic updates.

## Key Concepts

- **Problem**: Given n intervals, find all that overlap a query point or interval. Brute-force is O(n); interval trees achieve O(log n + m) where m is the number of results reported.
- **Output-sensitive**: Runtime depends on m (results produced), not just n (total intervals). This is asymptotically optimal since a query could return all n intervals.
- **Centered interval tree**: Recursively partitions intervals around a center point x_center into three sets — S_left (entirely left), S_right (entirely right), S_center (overlapping center). S_center is stored as two sorted lists (by start point and by end point).
- **Augmented tree**: Built on any ordered BST (keyed by interval low values), with each node annotated with the maximum high endpoint in its subtree. Described in CLRS Section 14.3.
- **Small integer range optimization**: When endpoints fall in [1, ..., O(n)], optimal structures exist with O(n) preprocessing and O(1 + m) query time.
- **Not to be confused with segment tree**, which is a related but distinct data structure.

## Commands and Syntax

**Centered interval tree node structure:**
```
Node:
  - center_point: x_center
  - left_child:   pointer to node for intervals entirely left of x_center
  - right_child:  pointer to node for intervals entirely right of x_center
  - sorted_by_start: S_center intervals sorted by beginning point
  - sorted_by_end:   S_center intervals sorted by ending point
```

**Point query algorithm (centered tree):**
```
query(node, x):
  if x < x_center:
    report all intervals in sorted_by_start with start ≤ x  (walk from beginning)
    recurse into left_child
  elif x > x_center:
    report all intervals in sorted_by_end with end ≥ x  (walk from end)
    recurse into right_child
  else:  // x == x_center
    report all intervals in S_center
```

**Interval-interval query:**
1. Use a separate search tree of all start/end points to find intervals with endpoints inside query q.
2. Pick any point inside q, run point query to find intervals enclosing q.
3. Deduplicate results (use a binary flag per interval).

**Augmented tree annotation maintenance:**
```
On insert/delete of a node:
  walk ancestors bottom-up, update max_high = max(own high, left.max_high, right.max_high)
  cost: O(h) per operation where h = height of affected node
  also update on tree rotations
```

## Relationships

- **Binary search tree / Self-balancing BST**: The augmented tree variant is built on top of any BST (e.g., red-black tree, AVL tree); the centered tree is itself a form of binary tree.
- **Segment tree**: Related structure for interval problems but distinct; segment trees partition the coordinate space rather than the intervals.
- **Range tree**: Used for higher-dimensional generalizations of interval trees; replaces the sorted lists at each node with a range tree for multi-dimensional point retrieval.
- **Windowing queries**: Primary application domain — finding objects within a viewport (maps, 3D scenes).
- **CLRS (Cormen et al.)**: The augmented tree design is the textbook-standard treatment (Section 14.3, pp. 348–354).

## Exam-Relevant Points

- **Complexity table**:
  | Operation | Centered Tree | Augmented Tree |
  |-----------|--------------|----------------|
  | Build | O(n log n) | O(n log n) |
  | Query | O(log n + m) | O(log n + m) |
  | Space | O(n) | O(n) |
  | Insert/Delete | O(log n) | O(log n) |
  | Higher-dim space | O(n log n) | — |

- **Why naïve dual-tree approach fails**: Two trees (sorted by start, sorted by end) each discard half in O(log n), but merging results requires O(n), giving O(n) total — no better than brute-force.
- **Centered tree query logic**: When x < x_center, scan the start-sorted list; when x > x_center, scan the end-sorted list. This works because all S_center intervals span x_center.
- **Augmented tree annotation**: Each node stores max(high) of its entire subtree. Overlap condition: intervals A and B overlap iff A_low ≤ B_high AND B_low ≤ A_high.
- **Deletion complexity in centered tree**: More complex than standard BST deletion because promoted nodes may need to absorb intervals from former ancestors, potentially cascading further deletions.
- **Rotation invariant**: Both deletion and rotation must preserve the rule that each interval is stored at the node closest to the root among all nodes whose center point it overlaps.
- **Higher dimensions**: Generalize to N dimensions with same query/construction time but O(n log n) space; uses range trees at each node instead of sorted lists.
