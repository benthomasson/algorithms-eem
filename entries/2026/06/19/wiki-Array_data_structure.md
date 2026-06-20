---
source: sources/wiki-Array_data_structure.md
source_url: https://en.wikipedia.org/wiki/Array_(data_structure)
---

## Array Data Structure: Memory Layout and Addressing

An array is a fundamental data structure consisting of a contiguous collection of same-sized elements, each accessible via an index tuple. This page covers the low-level memory layout of arrays — how elements are addressed, stored in memory, and accessed efficiently — as distinct from the abstract array data type provided by programming languages.

## Key Concepts

- **Definition**: A collection of same-memory-size elements identified by index tuples, stored so that each element's memory address is computable from its indices via a mathematical formula.
- **Base address**: The memory address of the first element (also called foundation address or first address).
- **Addressing formula (1D)**: `address = B + c · i` where B is the base address, c is the stride (element size), and i is the index.
- **Addressing formula (kD)**: `address = B + c₁·i₁ + c₂·i₂ + … + cₖ·iₖ` — requires only k multiplications and k additions.
- **Indexing schemes**: Zero-based (C, Java, Lisp), one-based (FORTRAN 77), or n-based (Pascal, Algol — arbitrary start index).
- **Dimension (rank)**: The number of indices needed to select an element — not the total element count.
- **Row-major order**: Elements of each row are contiguous in memory (C convention). The last index varies fastest.
- **Column-major order**: Elements of each column are contiguous in memory (Fortran convention). The first index varies fastest.
- **Dope vector (descriptor/stride vector)**: A record packing dimension d, base address B, and increments c₁…cₖ — serves as a complete handle for the array and enables efficient slicing operations.
- **Spatial locality**: Sequential array iteration is faster than iteration over most other data structures because elements occupy contiguous memory, minimizing cache misses.
- **Packed arrays**: Multiple elements stored per word; extreme case is the bit array (1 bit per element, 8 conditions per octet).
- **Iliffe vector**: Alternative to true multidimensional layout — a 1D array of pointers to 1D arrays, enabling jagged arrays where rows have different sizes.
- **Static vs. dynamic**: Static arrays have fixed size at creation; dynamic arrays support insertion/deletion by reallocating and copying, with amortized O(1) append.

## Commands and Syntax

- **C declaration (1D)**: `int a[10];` — array of 10 integers, indices 0–9.
- **C declaration (2D)**: `int a[2][3];` — 2 rows, 3 columns, stored row-major as a₁₁, a₁₂, a₁₃, a₂₁, a₂₂, a₂₃.
- **Element access**: `A[1][3]` accesses row 2, column 4 in zero-based indexing.
- **Address calculation example**: Ten 4-byte integers starting at address 2000 — element i is at `2000 + (i × 4)`, giving addresses 2000, 2004, …, 2036.

## Relationships

- **Dynamic array**: Extends static arrays with resizable capacity; amortized O(1) append but O(n) insert/delete at arbitrary positions.
- **Hash table, heap, deque, queue, stack, string**: All commonly implemented using arrays as the underlying storage.
- **Linked list**: Trades O(1) indexed access (array advantage) for O(1) insertion/deletion at known positions.
- **Balanced tree (e.g., counted B-tree)**: O(log n) for both access and mutation — a middle ground.
- **Associative array**: Provides array-like functionality for sparse index spaces; implementations include Patricia tries, Judy arrays, van Emde Boas trees.
- **Matrix/vector**: Mathematical matrices and vectors are represented directly as 2D and 1D arrays.
- **Implicit data structures**: Array-based implementations of other structures are typically space-efficient with no per-element overhead.

## Exam-Relevant Points

- **O(1) access**: Both store and select operations are worst-case constant time — the defining performance characteristic of arrays.
- **O(n) space**: Arrays use linear space with zero per-element overhead.
- **Cache performance**: Iterating n elements of size k with cache line B requires ⌈nk/B⌉ cache misses — roughly B/k times better than random access.
- **Row-major vs. column-major** determines optimal traversal order and matters for matrix multiplication performance (store A row-major, B column-major for A·B).
- **Comparison table** (access / insert-delete): Array O(1)/N/A; Dynamic array O(1)/O(n) general, amortized O(1) end; Linked list O(n)/O(1); Balanced tree O(log n)/O(log n); Hashed array tree O(1)/amortized O(1) end with O(√n) excess space.
- **Historical note**: John von Neumann wrote the first array-sorting program (merge sort) in 1945 for EDVAC. Early indexing used self-modifying code, later index registers and indirect addressing.
- **Dynamic array amortized cost**: Appending to end is amortized O(1) when capacity is doubled on overflow.
- **If stride coefficient cₖ is a power of 2**, multiplication can be replaced by bit shifting — a common hardware optimization.
- **Dope vectors** enable efficient array slicing (sub-arrays, index swaps, reversals) by manipulating metadata rather than copying data.
