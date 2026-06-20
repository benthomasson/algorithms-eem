---
source: sources/wiki-Trie.md
source_url: https://en.wikipedia.org/wiki/Trie
---

## Trie (Prefix Tree): String-Indexed Search Structure

A trie (pronounced "try" or "tree") is a tree-based data structure for storing and retrieving strings from a dictionary or set. Unlike binary search trees, trie nodes do not store their keys explicitly — a node's position in the tree determines its key, with edges labeled by individual characters. Also called a digital tree or prefix tree, the trie was first abstractly described by Axel Thue in 1912 and implemented in a computing context by René de la Briandais (1959) and Edward Fredkin (1960), who coined the name from "re**trie**val."

## Key Concepts

- **Implicit key storage**: Each node's position encodes its key; children share a common prefix with their parent. The root represents the empty string.
- **Branching factor**: Each node contains up to |alphabet| child pointers (e.g., 128 for ASCII), most of which are typically null.
- **Time complexity**: Search, insert, and delete are all O(m) where m is the length of the key string — independent of how many keys are stored.
- **Space complexity**: O(n) average, O(w·n) worst case, where w is the alphabet width and n is the number of keys/characters stored.
- **Comparison with BST**: In a balanced BST, search is O(m log n) because O(log n) comparisons are needed and each costs O(m). Tries eliminate the log n factor.
- **Comparison with hash tables**: Tries have no hash collisions, support lexicographic ordering, and have worst-case O(m) lookup (vs. O(N) for hash tables with collisions). However, hash tables outperform tries on secondary storage with high random-access latency.
- **Deterministic finite automaton equivalence**: A trie can be viewed as a tree-shaped DFA.
- **Sentinel values**: String termination is indicated by a sentinel or a value stored at the terminal node.

## Commands and Syntax

**Node structure:**
```
structure Node
    Children  Node[Alphabet-Size]
    Value     Data-Type
end structure
```

**Search** — follow character-indexed child pointers; null means key absent:
```
Trie-Find(x, key)
  for 0 ≤ i < key.length do
    if x.Children[key[i]] = nil then
      return nil
    x := x.Children[key[i]]
  return x.Value
```

**Insert** — traverse/create nodes for each character, set value at terminal:
```
Trie-Insert(x, key, value)
  for 0 ≤ i < key.length do
    if x.Children[key[i]] = nil then
      x.Children[key[i]] := Create-New-Node()
    x := x.Children[key[i]]
  x.Value := value
```

**Delete** — recursively remove the value and prune childless nodes:
```
Trie-Delete(x, key)
  if x = nil then return nil
  if key = "" then x.Value := nil
  else x.Children[key[0]] := Trie-Delete(x.Children[key[0]], key[1:])
  if x.Value != nil then return x
  for 0 ≤ i < x.Children.length do
    if x.Children[i] != nil then return x
  return nil
```

## Relationships

- **Radix tree (compressed trie)**: Merges single-child chains into one node; best for sparse, static key sets. Patricia tree is the binary-encoded variant using "skip numbers" to avoid empty subtrees.
- **Suffix tree**: A trie of all suffixes of a text; enables fast full-text search.
- **Hash tables**: Tries replace hash tables when prefix-based queries, collision-free lookup, or lexicographic ordering are needed.
- **Radix sort**: Building a trie and traversing in pre-order is equivalent to radix sort; tries reflect the execution pattern of top-down radix sort.
- **Burstsort**: Uses tries internally; was the fastest string sorting algorithm as of 2007 due to cache efficiency.
- **Aho-Corasick algorithm**: Multi-pattern string matching built on trie structure.
- **DAFSA (minimal deterministic acyclic finite state automaton)**: More space-efficient than a trie when only dictionary membership is needed (no metadata), because it also compresses shared suffixes.
- **Bitwise trie**: Variant keyed on individual bits of fixed-length binary data (integers, memory addresses); related to x-fast tries.
- **Left-child right-sibling tree**: An alternative trie representation trading pointer-array space for linked-list traversal cost.

## Exam-Relevant Points

- All three core operations (search, insert, delete) run in **O(m)** time where m is key length — this is the defining performance advantage over BSTs.
- BST search is **O(m log n)** because each of O(log n) comparisons costs O(m); tries eliminate the log n factor entirely.
- Tries have **no hash collisions** — a key advantage over hash tables.
- Tries support **lexicographic sorting** via pre-order traversal (hash tables do not).
- The **radix tree** (compressed trie) merges nodes with a single child to save space; **Patricia tree** is its binary-encoded form using skip numbers.
- Tries are space-efficient for **large numbers of short strings** with common prefixes, but naive implementations waste space on sparse alphabets (each node stores |alphabet| pointers).
- **Alphabet reduction** (e.g., splitting bytes into nibbles) trades 2x traversal depth for 8x space reduction.
- The **bitmap technique** stores a 256-bit bitmap instead of 256 pointers per node to reduce memory.
- Key applications: **autocomplete, spell checking, IP routing (longest prefix match), bioinformatics (k-mer indexing in BLAST), web search engine indexing**.
- A trie is equivalent to a **tree-shaped deterministic finite automaton**.
- Tries are less efficient than hash tables on **secondary storage** (disk) due to random access patterns.
