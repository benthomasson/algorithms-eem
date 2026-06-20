---
source: sources/wiki-List_of_data_structures.md
source_url: https://en.wikipedia.org/wiki/List_of_data_structures
---

## Taxonomy of Data Structures

This page provides a comprehensive classification of all major data structures used in computer science, organized by category: primitive types, composite types, abstract data types, linear structures, trees, hash-based structures, and graphs. It serves as a master index linking to detailed articles on each structure.

## Key Concepts

- **Primitive types** are the atomic building blocks: Boolean, Character, Integer, Floating-point (IEEE 754 single/double precision), Fixed-point, Reference, Symbol, Enumerated type, and Complex.
- **Composite types** combine primitives: Array (contiguous, same-type), Record/Struct (named fields), Tuple/Product type (unnamed fields), String, Union, and Tagged union (discriminated union / sum type).
- **Abstract data types (ADTs)** define behavior independent of implementation. Core ADTs: List, Stack, Queue, Deque, Set, Multiset (Bag), Map (Associative array), Multimap, Graph, Tree, Heap.
- **ADT properties** vary on two axes: **Ordered** (elements have explicit sequence) vs. unordered, and **Unique** (duplicates disallowed) vs. non-unique. Sets are unordered+unique; Lists are ordered+non-unique; Maps have unique keys only.
- **Linear data structures** have elements forming a sequence — arrays and linked lists are the two fundamental families.
- **Trees** are a subset of directed acyclic graphs (DAGs), not general graphs.
- **Self-balancing BSTs** (AVL, Red-black, Splay, Treap, Scapegoat, AA, WAVL, Zip) maintain O(log n) operations by rebalancing on mutation.
- **B-trees and variants** (B+, B*, 2-3, 2-3-4) are optimized for disk/block-oriented storage with high branching factor.
- **Heaps** come in many variants trading constant factors, amortized bounds, and merge efficiency: Binary, Binomial, Fibonacci, Pairing, Skew, D-ary, Brodal queue.
- **Hash-based structures** include exact (hash table, dynamic perfect hashing) and probabilistic (Bloom filter, Cuckoo filter, Count-min sketch, MinHash) variants.
- **Space-partitioning trees** (k-d tree, Quadtree, Octree, R-tree, BSP tree) organize multi-dimensional spatial data.
- **Bit-slice trees** (Trie, Radix tree, Suffix tree/array, X-fast/Y-fast trie) compare bit slices of keys for prefix-based retrieval.

## Commands and Syntax

No commands per se — this is a taxonomy page. However, key implementation patterns to know:

- **Dynamic array**: amortized O(1) append via geometric growth (typically 2x)
- **Skip list**: randomized alternative to balanced BSTs; O(log n) expected for search/insert/delete
- **Union-Find (Disjoint-set)**: `find(x)` with path compression + `union(x,y)` with rank — nearly O(α(n)) amortized
- **Bloom filter**: insert = hash k times and set bits; query = check all k bits; false positives possible, false negatives impossible
- **Fenwick tree (BIT)**: prefix sums in O(log n) update and query using binary index arithmetic

## Relationships

- **ADTs vs. Implementations**: A Stack (ADT) can be implemented with an Array or Linked List. A Priority Queue (ADT) can be backed by a Binary Heap, Fibonacci Heap, or sorted array. The distinction between interface and implementation is fundamental.
- **Trees ⊂ DAGs ⊂ Graphs**: Trees are connected acyclic graphs with a root; DAGs allow multiple parents but no cycles; general graphs allow cycles.
- **Tries ↔ Hash Tables**: Both implement associative arrays; tries excel at prefix queries while hash tables excel at exact-match.
- **B-trees ↔ Red-black trees**: A 2-3-4 tree is isomorphic to a red-black tree. B-trees generalize to higher branching factors for external storage.
- **Heaps ↔ Priority Queues**: Heaps are the canonical implementation of the Priority Queue ADT. Fibonacci heaps achieve O(1) amortized decrease-key, enabling faster Dijkstra's algorithm.
- **Space-partitioning trees** connect to computational geometry algorithms (range search, nearest neighbor, collision detection).
- **Suffix trees/arrays** connect to string matching algorithms (pattern search, longest common substring).
- **Hash-based probabilistic structures** (Bloom filter, Count-min sketch, MinHash) connect to streaming algorithms and approximate computing.

## Exam-Relevant Points

- **Know the ADT property table**: List = ordered, non-unique; Set = unordered, unique; Map = unordered, unique keys; Stack/Queue = ordered, non-unique; Multiset = unordered, non-unique.
- **Tagged union vs. Union**: A tagged union stores a discriminator indicating which type is active; a plain union does not. Tagged unions are also called variants, discriminated unions, or sum types.
- **Reference vs. Pointer**: The page notes references are "sometimes erroneously referred to as pointers" — they are semantically distinct (references are abstract; pointers are memory addresses).
- **Trees are DAGs**: Trees are specifically a subset of directed acyclic graphs, not general graphs.
- **Floating-point represents a finite subset of rationals**, not all rationals — a common misconception tested in exams.
- **Self-balancing BST variants** and their guarantees: AVL (strict balance, faster lookup), Red-black (relaxed balance, faster insertion), Splay (amortized via access, no extra storage), Treap (randomized priorities).
- **B-tree family** is critical for database indexing: B+ trees store data only in leaves (range queries); B* trees delay splits for higher occupancy.
- **Fibonacci heap** achieves O(1) amortized insert and decrease-key, O(log n) amortized delete-min — key for optimal Dijkstra and Prim.
- **Bloom filter** properties: no false negatives, tunable false positive rate, space-efficient, cannot delete (unless counting variant).
- **Disjoint-set / Union-Find** with path compression and union-by-rank achieves inverse Ackermann amortized time — effectively constant.
- **Suffix array** is a space-efficient alternative to suffix tree; combined with LCP array, it supports the same queries.
- **Merkle tree** (listed under both bit-slice trees and hash trees) is foundational to blockchain and data integrity verification.
