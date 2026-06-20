---
source: https://en.wikipedia.org/wiki/List_of_data_structures
fetched: 2026-06-19
---

Data organization and storage formats 

This is a list of well-known [data structures](./Data_structure). For a wider list of terms, see [list of terms relating to algorithms and data structures](./List_of_terms_relating_to_algorithms_and_data_structures?action=edit&redlink=1). For a comparison of [running times](./Running_time) for a subset of this list see [comparison of data structures](./Comparison_of_data_structures).

 

## Data types

 

### Primitive types

 Main article: [Primitive type](./Primitive_type) 
- [Boolean](./Boolean_data_type), [true](./Truth_value) or [false](./False_(logic)).
- [Character](./Character_(computing))
- [Floating-point](./Floating-point_arithmetic) representation of a finite subset of the [rationals](./Rationals).

- Including [single-precision](./Single-precision_floating-point_format) and [double-precision](./Double-precision_floating-point_format) [IEEE 754](./IEEE_754) floats, among [others](./Category:Floating_point_types)

- [Fixed-point](./Fixed-point_arithmetic) representation of the rationals
- [Integer](./Integer_(computer_science)), a direct representation of either the [integers](./Integer) or the [non-negative integers](./Non-negative_integers)
- [Reference](./Reference_(computer_science)), sometimes erroneously referred to as a [pointer](./Pointer_(computer_programming)) or handle, is a value that refers to another value, possibly including itself
- [Symbol](./Symbol_(programming)), a unique identifier
- [Enumerated type](./Enumerated_type), a [set](./Set_(mathematics)) of symbols
- [Complex](./Complex_data_type), representation of [complex numbers](./Complex_numbers)

 

### Composite types or non-primitive type

 Main article: [Composite type](./Composite_type) 
- [Array](./Array_(data_type)), a sequence of elements of the same type stored contiguously in memory
- [Record](./Record_(computer_science)) (also called a structure or [struct](./Struct_(C_programming_language))), a collection of fields
- [Product type](./Product_type) (also called a tuple), a record in which the fields are not named
- [String](./String_(computing)), a sequence of characters representing text
- [Union](./Union_type), a datum which may be one of a set of types
- [Tagged union](./Tagged_union) (also called a *variant*, *discriminated union* or *sum type*), a union with a tag specifying which type the data is

 

### Abstract data types

 Main article: [Abstract data type](./Abstract_data_type) 
- [Container](./Container_(data_structure))
- [List](./List_(abstract_data_type))
- [Tuple](./Tuple)
- [Associative array, Map](./Associative_array)
- [Multimap](./Multimap)
- [Set](./Set_(abstract_data_type))
- [Multiset (bag)](./Multiset_(abstract_data_type))
- [Stack](./Stack_(abstract_data_type))
- [Queue](./Queue_(abstract_data_type)) (example [Priority queue](./Priority_queue))
- [Double-ended queue](./Double-ended_queue)
- [Graph](./Graph_(data_structure)) (example [Tree](./Tree_(data_structure)), [Heap](./Heap_(data_structure)))

 

Some properties of abstract data types:

 
| Structure | Ordered? | Uniqueness? |
| --- | --- | --- |
| List | yes | no |
| Associative array | no | keys (indexes) only |
| Set | no | yes |
| Stack | yes | no |
| Multimap | no | no |
| Multiset (bag) | no | no |
| Queue | yes | no |

 

"Ordered" means that the elements of the data type have some kind of explicit order to them, where an element can be considered "before" or "after" another element. This order is usually determined by the order in which the elements are added to the structure, but the elements can be rearranged in some contexts, such as [sorting](./Sorting_algorithm) a list. For a structure that isn't ordered, on the other hand, no assumptions can be made about the ordering of the elements (although a physical implementation of these data types will often apply some kind of arbitrary ordering). "Uniqueness" means that duplicate elements are not allowed. Depending on the implementation of the data type, attempting to add a duplicate element may either be ignored, overwrite the existing element, or raise an error. The detection for duplicates is based on some inbuilt (or alternatively, user-defined) rule for comparing elements.

 

## Linear data structures

 

A data structure is said to be linear if its elements form a sequence.

 

### Arrays

 
- [Array](./Array_data_structure)
- [Associative array](./Associative_array)
- [Bit array](./Bit_array)
- [Bit field](./Bit_field)
- [Bitboard](./Bitboard)
- [Bitmap](./Bitmap)
- [Circular buffer](./Circular_buffer)
- [Control table](./Control_table)
- [Image](./System_image)
- [Dope vector](./Dope_vector)
- [Dynamic array](./Dynamic_array)
- [Gap buffer](./Gap_buffer)
- [Hashed array tree](./Hashed_array_tree)
- [Lookup table](./Lookup_table)
- [Matrix](./Matrix_(computer_science))
- [Parallel array](./Parallel_array)
- [Sorted array](./Sorted_array)
- [Sparse matrix](./Sparse_matrix)
- [Iliffe vector](./Iliffe_vector)
- [Variable-length array](./Variable-length_array)

 

### Lists

 
- [Doubly linked list](./Doubly_linked_list)
- [Array list](./Array_list)
- [Linked list](./Linked_list) also known as a Singly linked list
- [Association list](./Association_list)
- [Self-organizing list](./Self-organizing_list)
- [Skip list](./Skip_list)
- [Unrolled linked list](./Unrolled_linked_list)
- VList
- [Conc-tree list](./Conc-tree_list)
- [Xor linked list](./Xor_linked_list)
- [Zipper](./Zipper_(data_structure))
- [Doubly connected edge list](./Doubly_connected_edge_list) also known as half-edge
- [Difference list](./Difference_list)
- [Free list](./Free_list)

 

## Trees

 Main article: [Tree (data structure)](./Tree_(data_structure)) 

Trees are a subset of [directed acyclic graphs](./Directed_acyclic_graph).

 

### Binary trees

 
- [AA tree](./AA_tree)
- [AVL tree](./AVL_tree)
- [Binary search tree](./Binary_search_tree)
- [Binary tree](./Binary_tree)
- [Cartesian tree](./Cartesian_tree)
- [Conc-tree list](./Conc-tree_list)
- [Left-child right-sibling binary tree](./Left-child_right-sibling_binary_tree)
- [Order statistic tree](./Order_statistic_tree)
- [Pagoda](./Pagoda_(data_structure))
- [Randomized binary search tree](./Randomized_binary_search_tree)
- [Red–black tree](./Red–black_tree)
- [Rope](./Rope_(computer_science))
- [Scapegoat tree](./Scapegoat_tree)
- [Self-balancing binary search tree](./Self-balancing_binary_search_tree)
- [Splay tree](./Splay_tree)
- [T-tree](./T-tree)
- [Tango tree](./Tango_tree)
- [Threaded binary tree](./Threaded_binary_tree)
- [Top tree](./Top_tree)
- [Treap](./Treap)
- [WAVL tree](./WAVL_tree)
- [Weight-balanced tree](./Weight-balanced_tree)
- [Zip tree](./Zip_tree)

 

### B-trees

 
- [B-tree](./B-tree)
- [B+ tree](./B+_tree)
- [B*-tree](./B*-tree)
- [Dancing tree](./Dancing_tree)
- [2–3 tree](./2–3_tree)
- [2–3–4 tree](./2–3–4_tree)
- [Queap](./Queap)
- [Fusion tree](./Fusion_tree)
- [Bx-tree](./Bx-tree_Moving_Object_Index)

 

### Heaps

 
- [Heap](./Heap_(data_structure))
- [Min-max heap](./Min-max_heap)
- [Binary heap](./Binary_heap)
- [B-heap](./B-heap)
- [Weak heap](./Weak_heap)
- [Binomial heap](./Binomial_heap)
- [Fibonacci heap](./Fibonacci_heap)
- [AF-heap](./AF-heap)
- [Leonardo heap](./Smoothsort)
- [2–3 heap](./2–3_heap)
- [Soft heap](./Soft_heap)
- [Pairing heap](./Pairing_heap)
- [Leftist heap](./Leftist_tree)
- [Treap](./Treap)
- [Beap](./Beap)
- [Skew heap](./Skew_heap)
- [Ternary heap](./Ternary_heap)
- [D-ary heap](./D-ary_heap)
- [Brodal queue](./Brodal_queue)

 

### Bit-slice trees

 

In these data structures each tree node compares a bit slice of key values.

 
- [Radix tree](./Radix_tree)
- [Suffix tree](./Suffix_tree)
- [Suffix array](./Suffix_array)
- [Compressed suffix array](./Compressed_suffix_array)
- [FM-index](./FM-index)
- [Generalised suffix tree](./Generalised_suffix_tree)
- [B-tree](./B-tree)
- [Judy array](./Judy_array)
- [Trie](./Trie)
- [X-fast trie](./X-fast_trie)
- [Y-fast trie](./Y-fast_trie)
- [Merkle tree](./Merkle_tree)

 

### Multi-way trees

 
- [Ternary search tree](./Ternary_search_tree)
- [Ternary tree](./Ternary_tree)
- [K-ary tree](./K-ary_tree)
- [And–or tree](./And–or_tree)
- [(a,b)-tree](./(a,b)-tree)
- [Link/cut tree](./Link/cut_tree)
- [SPQR-tree](./SPQR-tree)
- [Spaghetti stack](./Spaghetti_stack)
- [Disjoint-set data structure (Union-find data structure)](./Disjoint-set_data_structure)
- [Fusion tree](./Fusion_tree)
- [Enfilade](./Enfilade_(Xanadu))
- [Exponential tree](./Exponential_tree)
- [Fenwick tree](./Fenwick_tree)
- [Van Emde Boas tree](./Van_Emde_Boas_tree)
- [Rose tree](./Rose_tree)

 

### Space-partitioning trees

 

These are data structures used for [space partitioning](./Space_partitioning) or [binary space partitioning](./Binary_space_partitioning).

 
- [Segment tree](./Segment_tree)
- [Interval tree](./Interval_tree)
- [Range tree](./Range_tree)
- [Bin](./Bin_(computational_geometry))
- [K-d tree](./K-d_tree)
- [Implicit k-d tree](./Implicit_k-d_tree)
- [Min/max k-d tree](./Min/max_kd-tree)
- [Relaxed k-d tree](./Relaxed_k-d_tree)
- [Adaptive k-d tree](./Adaptive_k-d_tree)
- [Quadtree](./Quadtree)
- [Octree](./Octree)
- [Linear octree](./Linear_octree)
- [Z-order](./Z-order_(curve))
- [UB-tree](./UB-tree)
- [R-tree](./R-tree)
- [R+ tree](./R+_tree)
- [R* tree](./R*_tree)
- [Hilbert R-tree](./Hilbert_R-tree)
- [X-tree](./X-tree)
- [Metric tree](./Metric_tree)
- [Cover tree](./Cover_tree)
- [M-tree](./M-tree)
- [VP-tree](./VP-tree)
- [BK-tree](./BK-tree)
- [Bounding interval hierarchy](./Bounding_interval_hierarchy)
- [Bounding volume hierarchy](./Bounding_volume_hierarchy)
- [BSP tree](./BSP_tree)
- [Rapidly exploring random tree](./Rapidly_exploring_random_tree)

 

### Application-specific trees

 
- [Abstract syntax tree](./Abstract_syntax_tree)
- [Parse tree](./Parse_tree)
- [Decision tree](./Decision_tree)
- [Alternating decision tree](./Alternating_decision_tree)
- [Game tree](./Game_tree)
- [Expectiminimax tree](./Expectiminimax_tree)
- [Finger tree](./Finger_tree)
- [Expression tree](./Expression_tree)
- [Log-structured merge-tree](./Log-structured_merge-tree)
- [PQ tree](./PQ_tree)

 

## Hash-based structures

 
- [Approximate Membership Query Filter](./Approximate_Membership_Query_Filter) 
- [Bloom filter](./Bloom_filter)
- [Cuckoo filter](./Cuckoo_filter)
- [Quotient filter](./Quotient_filter)

- [Count–min sketch](./Count–min_sketch)
- [Distributed hash table](./Distributed_hash_table)
- [Double hashing](./Double_hashing)
- [Dynamic perfect hash table](./Dynamic_perfect_hashing)
- [Hash array mapped trie](./Hash_array_mapped_trie)
- [Hash list](./Hash_list)
- [Hash table](./Hash_table)
- [Hash tree](./Merkle_tree)
- [Hash trie](./Hash_trie)
- [Koorde](./Koorde)
- [Prefix hash tree](./Prefix_hash_tree)
- [Rolling hash](./Rolling_hash)
- [MinHash](./MinHash)
- [Ctrie](./Ctrie)

 

## Graphs

 

Many [graph](./Graph_(discrete_mathematics))-based data structures are used in computer science and related fields:

 
- [Graph](./Graph_(data_structure))
- [Adjacency list](./Adjacency_list)
- [Adjacency matrix](./Adjacency_matrix)
- [Graph-structured stack](./Graph-structured_stack)
- [Scene graph](./Scene_graph)
- [Decision tree](./Decision_tree) 
- [Binary decision diagram](./Binary_decision_diagram)

- [Zero-suppressed decision diagram](./Zero-suppressed_decision_diagram)
- [And-inverter graph](./And-inverter_graph)
- [Directed graph](./Directed_graph)
- [Directed acyclic graph](./Directed_acyclic_graph)
- [Propositional directed acyclic graph](./Propositional_directed_acyclic_graph)
- [Multigraph](./Multigraph)
- [Hypergraph](./Hypergraph)

 

## Other

 
- [Lightmap](./Lightmap)
- [Winged edge](./Winged_edge)
- [Quad-edge](./Quad-edge)
- [Routing table](./Routing_table)
- [Symbol table](./Symbol_table)
- [Piece table](./Piece_table)
- [E-graph](./E-graph)

 

## See also

 
- [List of algorithms](./List_of_algorithms)
- [Purely functional data structure](./Purely_functional_data_structure)
- [Blockchain](./Blockchain), a hash-based chained data structure that can persist state history over time

 

## External links

 
- [Tommy Benchmarks](https://tommyds.sourceforge.net/doc/benchmark.html) Comparison of several data structures.

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |