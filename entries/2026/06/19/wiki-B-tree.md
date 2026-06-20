---
source: sources/wiki-B-tree.md
source_url: https://en.wikipedia.org/wiki/B-tree
---

## B-Tree: Self-Balancing Multi-Way Search Tree

A B-tree is a self-balancing tree data structure invented by Rudolf Bayer and Edward McCreight in 1970 at Boeing Research Labs. It generalizes the binary search tree by allowing nodes to have more than two children, maintaining sorted data with O(log n) search, insert, and delete operations. B-trees are optimized for systems that read and write large blocks of data, making them the standard index structure in virtually all relational databases and file systems.

## Key Concepts

- **Order (Knuth's definition):** A B-tree of order *m* allows each node at most *m* children and *m*−1 keys
- **Minimum fill guarantee:** Every non-root internal node has at least ⌈m/2⌉ children (at least half full), enabling predictable split/merge operations
- **All leaves at the same depth:** B-trees are perfectly balanced — every leaf is equidistant from the root
- **Root special case:** The root may have as few as 2 children (or be a leaf with 0 children if the tree is very small)
- **Keys as separators:** A non-leaf node with *k* children contains *k*−1 keys that partition the key space across its subtrees
- **Space complexity:** O(n); Time complexity for search/insert/delete: O(log n) both amortized and worst case
- **Height reduction:** A B-tree of depth n+1 holds roughly *m* times as many items as one of depth n — the branching factor drastically reduces tree height compared to binary trees
- **Split on overflow:** Inserting into a full node (2d keys) splits it into two d-key siblings, pushing the median key up to the parent
- **Merge on underflow:** Deleting from a node at minimum occupancy triggers a merge with a sibling or redistribution of keys from a neighbor
- **Depth changes are rare:** Depth increases only when the root splits; decreases only when the root's two children merge

## Commands and Syntax

No CLI commands per se, but the core algorithmic procedures are:

- **Search:** Start at root, at each node use binary search among keys to select the correct child pointer; recurse until leaf
- **Insert:** Search to the leaf; insert key in sorted position; if the node overflows (>2d keys), split and propagate the median upward; if the root splits, create a new root (tree grows taller by 1)
- **Delete:** Find the key; if in an internal node, replace with in-order predecessor/successor from a leaf, then delete from the leaf; if the leaf underflows (<d keys), redistribute from a sibling or merge with a sibling and pull a separator down from the parent; propagate merges upward as needed

**Height formulas:**
- Best case (minimum height): h_min = ⌈log_m(n+1)⌉ − 1
- Worst case (maximum height): h_max = ⌊log_d((n+1)/2)⌋, where d = ⌈m/2⌉

## Relationships

- **Binary search tree:** B-tree is a generalization; a B-tree of order 2 is essentially a 2-3 tree
- **B+ tree:** Variant where all record pointers are stored only in leaf nodes, and leaves are linked for fast sequential access; internal nodes hold more keys because they lack record pointers, making the tree shallower
- **B\* tree:** Variant requiring nodes to be at least 2/3 full (not 1/2); delays splits by redistributing keys to siblings first
- **Red-black trees / AVL trees:** Binary self-balancing alternatives; B-trees are preferred when node access cost dominates (disk I/O, cache misses)
- **Order statistic trees:** B-trees can be augmented with subtree sizes to support rank queries
- **Database indexing:** B-trees are the standard implementation for indexes in relational databases (and many non-relational ones)
- **File systems:** Used for directory indexing and metadata management (e.g., NTFS, HFS+, ext4 via htree)
- **CPU cache performance:** Even in-memory B-trees benefit from high branching factor because fewer cache lines are accessed

## Exam-Relevant Points

- All operations (search, insert, delete) are **O(log n)** in both amortized and worst case
- A B-tree of order *m*: max *m* children, max *m*−1 keys per node; internal non-root nodes have at least ⌈m/2⌉ children
- **All leaves are at the same level** — this is the balance invariant
- Splitting a full node produces two half-full nodes and promotes the median key — this is why the 2d/d relationship matters
- The "order" definition is ambiguous in the literature: Knuth defines it as max children; others define it as min keys — know which convention is in use
- B-trees reduce disk reads from O(log₂ N) to O(log_b N), where b is the blocking factor (keys per node)
- B+ trees store all data in leaves and link leaves for sequential scan — the most common variant in practice
- B\* trees require 2/3 minimum fill and use redistribution before splitting
- Depth increases **only** when the root splits; depth decreases **only** when root's children merge — depth changes are global, not local
- Lazy deletion (marking records as deleted without restructuring) is a valid strategy but degrades search/storage efficiency over time
- The terminology confusion (order, leaf) between Knuth, Bayer/McCreight, and Comer is itself a classic exam topic
