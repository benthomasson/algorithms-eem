---
source: sources/wiki-Hash_table.md
source_url: https://en.wikipedia.org/wiki/Hash_table
---

I need write permission to save the entry. Here's the complete study entry for Hash Table:

---

## Hash Table: Associative Array via Hashed Key Indexing

A hash table (also called hash map, dictionary, or map) is a data structure that implements an associative array abstract data type, mapping keys to values. It uses a hash function to compute an index into an array of buckets, from which the desired value can be found. Invented in 1953, hash tables provide average-case O(1) time for search, insert, and delete operations, making them more efficient on average than search trees or other table lookup structures. They are one of the most widely used data structures in practice, powering built-in dictionary types in Python, Java (HashMap), C++ (unordered_map), and Go (map).

## Key Concepts

- **Core mechanism**: A hash function h(x) maps a key x to an index in an array of size m; both the key and value are stored at that index so lookups can verify correctness.
- **Time complexity**: Average O(1) for search, insert, and delete. Worst case O(n) for all three operations (when all keys hash to the same bucket).
- **Space complexity**: Θ(n) average, O(n) worst case.
- **Space-time tradeoff**: Hashing trades memory for speed — with infinite memory you could index directly by key; with infinite time you could search linearly.
- **Hash collision**: Occurs when the hash function maps two or more distinct keys to the same index. Collisions are inevitable with imperfect hash functions and must be resolved.
- **Load factor** α = n/m: The ratio of stored elements (n) to total buckets (m). Performance degrades as α increases. Tables are resized (rehashed) when α reaches a threshold α_max, and may shrink when α drops below α_max/4.
- **Perfect hash function**: A hash function that is injective on the key set S — every key maps to a unique index. Only possible when all keys are known ahead of time.
- **Sets via hash tables**: Implemented by storing only keys (no values) and tracking key presence.
- **Bucket-level distribution**: For an ideally random hash function with large m and n, each bucket's occupancy follows a Poisson distribution with expectation λ = α.

## Collision Resolution Strategies

### Separate Chaining
- Each bucket stores a pointer to a linked list (or other collection) of key-value pairs that hashed to that index.
- **Insert**: Place the new element at the head of the linked list at T[h(k)].
- **Search**: Traverse the linked list at T[h(k)] looking for matching key.
- **Delete**: Remove the element from the linked list at T[h(k)].
- Performance degrades gradually as α grows; no hard failure point.
- Optimal α_max typically between 1 and 3.
- Using a self-balancing BST instead of a linked list reduces worst case from O(n) to O(log n).
- **Dynamic perfect hashing**: Two-level hash tables with k² slots per bucket achieve guaranteed O(1) worst-case lookup.
- **Cache concern**: Linked list nodes scattered in memory cause poor cache locality. Dynamic arrays used as chains are more cache-friendly due to contiguous allocation exploited by hardware prefetchers (TLB, cache prefetching).
- Array-based separate chaining is 97% more performant than linked list chaining under heavy load.

### Open Addressing
- All entries are stored directly in the bucket array; no external data structures.
- On collision, a **probe sequence** determines the next slot to check.
- **Linear probing**: Fixed interval (usually 1) between probes. Simple but susceptible to primary clustering.
- **Quadratic probing**: Interval increases by successive outputs of a quadratic polynomial.
- **Double hashing**: Interval is computed by a secondary hash function.
- Load factor α cannot exceed 1 (table is full at α = 1). Must resize before α = 1 or probing enters infinite loop.
- Optimal α_max for open addressing: 0.6 to 0.75.
- Performance degrades more sharply than chaining as α approaches 1.

## Hash Function Methods

### Hashing by Division
```
h(x) = x mod m
```
Most commonly used scheme. The choice of m matters — prime numbers are often preferred to avoid patterns.

### Hashing by Multiplication
```
h(x) = floor(m * ((x * A) mod 1))
```
Where A is a non-integer real constant. Knuth suggests using the golden ratio for A. Advantage: the choice of m is not critical.

### String Hashing
- Repeatedly left-shift an unsigned integer and XOR with each character's integer value, then take modulo of table size.
- Polynomial rolling hash functions are another common approach.

### Choosing a Good Hash Function
- **Uniform distribution** of hash values is the fundamental requirement.
- Non-uniform distribution increases collisions and resolution cost.
- Uniformity can be tested empirically with Pearson's chi-squared test for discrete uniform distributions.
- For open addressing, the hash function should also avoid **clustering** (mapping keys to consecutive slots), which causes lookup cost to skyrocket even with low load factors.
- **K-independent hashing** provides theoretical guarantees that the hash function has no bad key sets for a given collision resolution scheme.

## Commands and Syntax

### Pseudocode for Chained Hash Table Operations
```
Chained-Hash-Insert(T, k)
  insert x at the head of linked list T[h(k)]

Chained-Hash-Search(T, k)
  search for an element with key k in linked list T[h(k)]

Chained-Hash-Delete(T, k)
  delete x from the linked list T[h(k)]
```

### Rehashing (Resize)
When load factor α reaches α_max:
1. Allocate a new, larger array (typically double the size).
2. Recompute h(x) for every existing element and insert into the new array.
3. Amortized cost of resizing is O(1) per operation over time.

## Relationships

- **Hash function**: The core enabling component — determines distribution quality and thus hash table performance.
- **Linked list**: Used as the chain data structure in separate chaining collision resolution.
- **Self-balancing BST (e.g., red-black tree)**: Can replace linked lists in chaining to achieve O(log n) worst-case per-bucket lookup (Java 8+ HashMap uses this for large buckets).
- **Binary search / search trees**: Hash tables are typically faster (O(1) vs O(log n) average), but BSTs maintain sorted order and support range queries that hash tables cannot.
- **Dynamic array**: Cache-friendly alternative to linked lists for separate chaining.
- **Associative array / dictionary**: The abstract data type that hash tables implement.
- **Set (ADT)**: Hash tables implement sets by omitting values and tracking key presence only.
- **Amortized analysis**: Explains why hash table operations are O(1) on average despite occasional O(n) resizing.
- **Perfect hashing**: Eliminates collisions entirely when the key set is known in advance.
- **Cuckoo hashing**: An open addressing variant using two hash functions with worst-case O(1) lookup.

## Exam-Relevant Points

- **Average-case O(1)** for search, insert, delete; **worst-case O(n)** for all three.
- **Load factor α = n/m** is the key metric governing performance. Know the formula.
- **Open addressing requires α < 1**; practical limit is 0.6–0.75. Separate chaining works with α > 1 (optimal range 1–3).
- **Rehashing** is triggered when α exceeds α_max; table size is typically doubled. Amortized O(1) per operation.
- **Two collision resolution families**: separate chaining (external structures) vs. open addressing (in-place probing).
- **Three probe sequences** for open addressing: linear probing (interval 1), quadratic probing (quadratic polynomial), double hashing (secondary hash function).
- **Hashing by division**: h(x) = x mod m. Most common. Prime m preferred.
- **Hashing by multiplication**: h(x) = floor(m * ((x * A) mod 1)). Golden ratio suggested for A by Knuth.
- **Perfect hash function**: injective on S, possible only when all keys are known in advance. Guarantees zero collisions.
- **Separate chaining with BSTs** reduces worst case from O(n) to O(log n) per bucket.
- **Dynamic perfect hashing** achieves guaranteed O(1) worst-case lookup using two-level tables with k² slots per bucket.
- **Cache locality**: Linked list chaining has poor spatial locality; array-based chaining is more cache-friendly.
- Hash tables **cannot** efficiently support ordered operations (min, max, successor, range queries) — BSTs are preferred for those.
- **Invented 1953** by Hans Peter Luhn (IBM); open addressing credited to Amdahl (and independently Ershov); term "open addressing" coined by W. Wesley Peterson.
- **Space complexity**: Θ(n) average and O(n) worst case.
