---
source: sources/wiki-Heapsort.md
source_url: https://en.wikipedia.org/wiki/Heapsort
---

## Heapsort: Comparison-Based Sorting via Binary Heap

Heapsort is an efficient, in-place, comparison-based sorting algorithm that works in two phases: first building a max-heap from the input array, then repeatedly extracting the maximum element to produce a sorted result. Invented by J.W.J. Williams in 1964 (with Floyd's in-place improvement the same year), it guarantees O(n log n) worst-case performance but is typically 2-3x slower than quicksort in practice due to poor cache locality.

## Key Concepts

- **Two-phase algorithm**: (1) heap construction — O(n), (2) heap extraction — O(n log n)
- **Implicit data structure**: The heap is stored directly in the array with no extra pointers; parent/child relationships are computed via index arithmetic:
  - `leftChild(i) = 2i + 1`, `rightChild(i) = 2i + 2`, `parent(i) = floor((i-1)/2)`
- **Max-heap property**: Every node is greater than or equal to both its children; root holds the maximum
- **In-place but not stable**: Uses O(1) auxiliary space, but does not preserve the relative order of equal elements
- **siftDown** is the core primitive: repairs a heap where only the root may violate the heap property, by repeatedly swapping the root with its greatest child — bounded by tree height O(log n)
- **Floyd's heapify** (bottom-up): Builds heap in O(n) by starting from last non-leaf and sifting down; most nodes are near leaves so most sift-downs are short. Exact worst-case comparisons: 2n - 2s₂(n) - e₂(n) where s₂ is popcount and e₂ is trailing zero count
- **Williams' heapify** (top-up): Appends elements one at a time using siftUp — O(n log n) worst case because most insertions operate on large heaps. All practical implementations use Floyd's version
- **Quicksort relationship**: Heapsort is used as a fallback in introsort and pattern-defeating quicksort when quicksort detects degenerate O(n²) behavior

## Commands and Syntax

**Core algorithm pseudocode:**
```
procedure heapsort(a, count):
    heapify(a, count)           // Build max-heap — O(n)
    end ← count
    while end > 1:
        end ← end - 1
        swap(a[0], a[end])      // Move max to sorted region
        siftDown(a, 0, end)     // Restore heap property — O(log n)
```

**siftDown (heap repair):**
```
procedure siftDown(a, root, end):
    while iLeftChild(root) < end:
        child ← iLeftChild(root)
        if child+1 < end and a[child] < a[child+1]:
            child ← child + 1      // Pick greater child
        if a[root] < a[child]:
            swap(a[root], a[child])
            root ← child
        else: return
```

**Floyd's heapify (bottom-up, O(n)):**
```
procedure heapify(a, count):
    start ← iParent(count-1) + 1
    while start > 0:
        start ← start - 1
        siftDown(a, start, count)
```

**Combined single-loop implementation** merges both phases using `start` and `end` pointers — while `start > 0` it does heap construction; otherwise it does extraction.

## Relationships

- **Binary heap**: Heapsort introduced the binary heap; the implicit array-based heap is the central data structure
- **Selection sort**: Heapsort is conceptually a selection sort that uses a heap to efficiently find the maximum
- **Quicksort**: Primary competitor; quicksort wins on cache locality and branch prediction but has O(n²) worst case
- **Introsort**: Hybrid that starts with quicksort and falls back to heapsort — guarantees O(n log n) worst case
- **Smoothsort** (Dijkstra): Variant that approaches O(n) on nearly-sorted input
- **Priority queue**: The siftUp variant (Williams') is needed for general priority queue operations (insert)
- **Comparison sort lower bound**: Bottom-up heapsort variants approach the information-theoretic minimum of n log₂ n - 1.4427n comparisons
- **Weak heapsort**: Uses one extra bit per node to achieve n log₂ n + O(n) comparisons
- **Treesort**: Floyd's heapsort improvement grew from his earlier treesort research

## Exam-Relevant Points

- **Time complexity**: O(n log n) in all cases (best, average, worst) for distinct keys; O(n) best case for equal keys
- **Space complexity**: O(1) auxiliary (in-place), O(n) total
- **Not stable**: Does not preserve order of equal elements
- **Heap construction is O(n), not O(n log n)**: The geometric series n/2 + n/4 + n/8 + ... = n proves this. This is a frequently tested fact
- **Why Floyd's heapify beats Williams'**: Floyd's siftDown operates mostly on small heaps (leaves); Williams' siftUp operates mostly on large heaps — O(n) vs O(n log n)
- **Bottom-up heapsort** reduces average comparisons from 2n log₂ n to n log₂ n by searching down to a leaf then sifting up — significant when comparisons are expensive (e.g., string keys), negligible for integer keys due to branch prediction
- **Heapsort vs quicksort tradeoffs**: Quicksort is 2-3x faster in practice (better locality, branch-free variants, parallelizable), but heapsort has guaranteed O(n log n) worst case and simpler implementation
- **Real-world usage**: Preferred in real-time systems, embedded systems, and security-sensitive contexts (e.g., Linux kernel) where worst-case guarantees matter; used as fallback in hybrid sorts (introsort)
- **Each siftDown call** is bounded by tree height: floor(log₂ n) iterations
- **Ternary heapsort** reduces comparisons by a constant factor but adds complexity — rarely practical
