---
source: sources/wiki-Set_abstract_data_type.md
source_url: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
---

## Set (Abstract Data Type)

The set is an abstract data type that stores a collection of distinct values with no particular ordering. It is the computer science implementation of the mathematical finite set. Unlike sequential collections where elements are accessed by position, the primary operation on a set is testing membership — checking whether a value belongs to the set.

## Key Concepts

- **Set**: an ADT storing unique values without ordering; primary operation is membership testing, not element retrieval by index
- **Static (frozen) sets**: immutable after construction; support only query operations (membership test, enumeration)
- **Dynamic (mutable) sets**: support insertion and deletion in addition to queries
- **Multiset (bag)**: a generalization that allows duplicate elements; two interpretations exist — counting duplicates (identical) or storing them as distinct equivalent items
- **Indicator (characteristic) function**: in type theory, a set is identified with a function F(x) returning 1 if x is in the set, 0 otherwise; denoted 2^A or P(A)
- **Sets as specialized maps**: a set can be implemented as an associative array where keys are elements and values are a sentinel (e.g., 1 or unit type)
- **Other ADTs as sets**: many structures (e.g., heaps) can be viewed as sets with additional operations or axioms

## Commands and Syntax

**Core set-theoretic operations:**
- `union(S, T)` — set union
- `intersection(S, T)` — set intersection
- `difference(S, T)` — set difference
- `subset(S, T)` — predicate testing if S ⊆ T

**Static set operations:**
- `is_element_of(x, S)` — membership test
- `is_empty(S)`, `size(S)` / `cardinality(S)`
- `iterate(S)`, `enumerate(S)`
- `build(x1, x2, ..., xn)`, `create_from(collection)`

**Dynamic set operations:**
- `create()`, `create_with_capacity(n)`
- `add(S, x)`, `remove(S, x)`, `capacity(S)`

**Additional operations:**
- `pop(S)` — return and remove arbitrary element
- `pick(S)` — return arbitrary element without removal
- `map(F, S)`, `filter(P, S)`, `fold(A0, F, S)` (F must be associative and commutative for fold)
- `clear(S)`, `equal(S1, S2)`, `hash(S)`
- `min(S)`, `max(S)`, `nearest(S, x)`, `sum(S)`, `collapse(S)`, `flatten(S)`

**Multiset operations:**
- `contains(B, x)`, `count(B, x)`, `is_sub_bag(B1, B2)`
- `scaled_by(B, n)`, `union(B1, B2)` — additive union where counts sum

**SQL multisets:**
```sql
SELECT DISTINCT col FROM table;          -- yields a set
MULTISET(SELECT col FROM table);         -- collection expression (ANSI SQL)
```

**Language-specific examples:**
```python
# Python set literal (3.0+, 2.7+)
s = {1, 2, 3}
empty = set()            # {} is a dict, not a set
```
```perl
# Perl: array to set via hash
my %elements = map { $_ => 1 } @elements;
```

## Relationships

- **Hash tables**: primary implementation for unordered sets (O(1) average, O(n) worst-case for most operations)
- **Self-balancing BSTs** (red-black, AVL): implementation for sorted/ordered sets (O(log n) for most operations)
- **Tries**: alternative tree-based implementation for string or prefix-oriented sets
- **Bit arrays**: efficient for sets that are subsets of integers 1..n; support fast union/intersection via bitwise ops
- **Bloom filters/maps**: probabilistic set representation — compact but may yield false positives
- **Union-find (disjoint-set)**: specialized structure optimized for union operations
- **Associative arrays (maps)**: sets can be implemented as maps with dummy values; conversely, sets are maps where value is the unit type
- **Multisets**: generalization of sets; implemented with same structures (hash tables, trees) plus multiplicity tracking
- **Heaps**: can be viewed as sets with a `min(S)` operation
- **SQL/relational databases**: tables are multisets unless DISTINCT or a candidate key constraint enforces uniqueness

## Exam-Relevant Points

- A set stores **distinct** values with **no ordering** — the defining characteristic vs. lists/sequences
- The **fold** operation on a set requires F to be **associative and commutative** because iteration order is arbitrary
- Naive list-based set implementation: membership and deletion are **O(n)**; insertion is O(1) only if duplicates aren't checked
- Hash table implementation: **O(1) average**, **O(n) worst-case** for element_of, add, delete
- BST (e.g., red-black tree) implementation: **O(log n)** for most operations; provides sorted iteration
- Sorted-list union can be done in **O(m+n)** using merge, vs. naive **O(m×n)**
- **Bit array** implementation for integer subsets of 1..n supports O(1) membership test and very efficient union/intersection
- In Python, `{}` creates an **empty dict**, not an empty set — use `set()` instead
- C++ STL: `set` (sorted, BST), `unordered_set` (hash, C++11); `multiset` / `unordered_multiset` for bags
- Java: `HashSet` (hash), `TreeSet` (BST implementing `SortedSet`)
- SQL `DISTINCT` converts a multiset query result into a set
- A **multiset** tracks element multiplicity — implementable via associative array mapping values to counts (e.g., Python's `collections.Counter`)
- `hash(S)` must satisfy: if `equal(S1, S2)` then `hash(S1) = hash(S2)` — the hash consistency contract
