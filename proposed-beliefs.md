# Proposed Beliefs

Review each entry: change `[ACCEPT]` to `[ACCEPT]` to keep, or vice versa.
Then run: `expert-build accept-beliefs`

---

**Generated:** 2026-06-19
**Source:** 52 entries from entries/
**Model:** claude

### [ACCEPT] array-o1-access
Array store and select operations are worst-case O(1) time; this is the defining performance characteristic of arrays.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-address-formula-1d
The address of element i in a 1D array is computed as address = B + c * i, where B is the base address and c is the stride (element size in bytes).
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-address-formula-kd
The address of an element in a k-dimensional array is address = B + c₁·i₁ + c₂·i₂ + … + cₖ·iₖ, requiring only k multiplications and k additions.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-row-major-order
Row-major order (C convention) stores elements of each row contiguously in memory; the last index varies fastest.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-column-major-order
Column-major order (Fortran convention) stores elements of each column contiguously in memory; the first index varies fastest.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-dope-vector
A dope vector (descriptor/stride vector) packs dimension d, base address B, and increments c₁…cₖ, serving as a complete handle for the array and enabling efficient slicing by manipulating metadata rather than copying data.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-cache-misses
Iterating n array elements of size k with cache line size B requires ⌈nk/B⌉ cache misses — roughly B/k times better than random access patterns.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-iliffe-vector
An Iliffe vector is a 1D array of pointers to 1D arrays, enabling jagged arrays where rows have different sizes; it is an alternative to true contiguous multidimensional layout.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-von-neumann-merge-sort
John von Neumann wrote the first array-sorting program (merge sort) in 1945 for EDVAC.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] array-dimension-is-rank
The dimension (rank) of an array is the number of indices needed to select an element, not the total element count.
- Source: entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)

### [ACCEPT] btree-definition
A B-tree is a self-balancing tree data structure where all leaves are at the same depth, invented by Rudolf Bayer and Edward McCreight in 1970 at Boeing Research Labs.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-order-knuth
Under Knuth's definition, a B-tree of order m allows each node at most m children and m−1 keys; the 'order' definition is ambiguous in the literature (Knuth = max children, others = min keys).
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-minimum-fill
Every non-root internal node in a B-tree of order m has at least ⌈m/2⌉ children (at least half full).
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-complexity
B-tree search, insert, and delete are all O(log n) in both amortized and worst case; space complexity is O(n).
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-split-on-overflow
Inserting into a full B-tree node (2d keys) splits it into two d-key siblings, pushing the median key up to the parent; if the root splits, a new root is created and the tree grows taller by 1.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-depth-change-rules
B-tree depth increases only when the root splits; depth decreases only when the root's two children merge — depth changes are global events, not local.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-height-formulas
B-tree height bounds: minimum h = ⌈log_m(n+1)⌉ − 1; maximum h = ⌊log_d((n+1)/2)⌋ where d = ⌈m/2⌉.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] bplus-tree-variant
A B+ tree stores all record pointers only in leaf nodes and links leaves for fast sequential access; internal nodes hold more keys (no record pointers), making the tree shallower than a standard B-tree.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] bstar-tree-variant
A B* tree requires nodes to be at least 2/3 full (vs B-tree's 1/2) and delays splits by redistributing keys to siblings first.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] btree-disk-io-advantage
B-trees reduce disk reads from O(log₂ N) (binary tree) to O(log_b N) where b is the blocking factor (keys per node), making them the standard index structure in virtually all relational databases and file systems.
- Source: entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree

### [ACCEPT] backtracking-definition
Backtracking incrementally builds candidate solutions and abandons any candidate as soon as it determines that candidate cannot be completed to a valid solution; it traverses the implicit search tree in depth-first order with pruning.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-completeness
Backtracking is complete (guaranteed to find all solutions) and sound (only reports valid solutions) for finite problems, unlike many metaheuristics.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-vs-bruteforce
Backtracking with a reject function that always returns false degenerates to brute-force enumeration; pruning via the reject function is what distinguishes backtracking from brute force.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-reject-correctness
The backtracking reject function must return true ONLY when certain no extension of the candidate can succeed; a false positive causes missed solutions, while a false negative merely reduces efficiency.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-early-pruning
Backtracking efficiency depends on the reject function returning true as close to the root as possible, since early pruning eliminates the largest subtrees.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-csp-worst-case
For constraint satisfaction problems with n variables each taking m values, backtracking worst case explores the full search tree in O(m^n) time, but pruning typically makes it much faster in practice.
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] backtracking-six-procedures
Generic backtracking is defined by six procedural parameters: root(P), reject(P,c), accept(P,c), first(P,c), next(P,s), and output(P,c).
- Source: entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking

### [ACCEPT] big-o-formal-definition
f(x) = O(g(x)) means there exists a positive constant M such that |f(x)| ≤ M·g(x) for all x in the domain; the implied constant M must exist but its specific value does not matter.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] big-o-not-equality
The '=' in f(x) = O(g(x)) denotes set membership, not equality; it is not symmetric — writing O(g(x)) = f(x) is invalid.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] big-o-simplification
In Big O notation (as x → ∞), constant factors and lower-order terms are dropped: in a sum keep only the term with the largest growth rate; in a product drop factors not depending on the variable.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] big-o-upper-bound-only
Big O provides an asymptotic upper bound only and says nothing about lower bounds; Θ (Theta) notation gives a tight bound covering both upper and lower bounds.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] big-o-tightness
A Big O bound can be technically correct but not tight: O(x^10) is valid for a degree-4 polynomial but uselessly loose; the tightest correct bound should be preferred.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] big-o-domain-matters
The same function can have different Big O characterizations on finite vs. infinite domains; Taylor approximation uses finite-domain Big O while algorithm analysis uses infinite-domain Big O.
- Source: entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation

### [ACCEPT] binary-search-definition
Binary search finds a target value in a sorted array by repeatedly halving the search interval; it runs in O(log n) worst/average case, O(1) best case, with O(1) space, and is optimal among comparison-based searches on sorted arrays.
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] binary-search-overflow-bug
The midpoint calculation (L + R) / 2 can cause integer overflow; the correct form is L + floor((R - L) / 2).
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] binary-search-worst-comparisons
Binary search requires exactly floor(log2 n) + 1 comparisons in the worst case.
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] binary-search-precondition-sorted
Binary search requires the input array to be sorted as a precondition; it cannot be applied to unsorted arrays.
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] binary-search-leftmost-variant
The leftmost binary search variant initializes R = n (not n-1) and returns the rank of T (count of elements less than T) even when T is absent from the array.
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] binary-search-vs-hash-table
Hash tables provide O(1) average lookup (faster than binary search's O(log n)), but cannot support ordered queries such as rank, predecessor, successor, or range queries.
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] fractional-cascading
Fractional cascading speeds up binary search across k sorted arrays from O(k log n) to O(k + log n).
- Source: entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search

### [ACCEPT] bst-definition
A binary search tree (BST) is a rooted binary tree where each node's key is greater than all keys in its left subtree and less than all keys in its right subtree, enabling O(log n) average-case search, insert, and delete.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-worst-case-degenerate
Without balancing, a BST degenerates to a linked list with O(n) worst-case operations; sorted insertion is the classic degeneracy scenario producing tree height n.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-deletion-three-cases
BST deletion has three cases: leaf node (replace with NIL), one child (elevate the child), two children (replace with in-order successor or predecessor).
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-inorder-sorted
Inorder traversal (left, node, right) of a BST yields keys in sorted order; this is the defining operational characteristic of the BST property.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-insert-always-leaf
In a standard BST, new nodes are always inserted as leaves by descending like search using a trailing pointer and attaching at the NIL position.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-successor-algorithm
The in-order successor of node x in a BST is the minimum of x's right subtree if it exists; otherwise, walk up ancestors until finding the first ancestor where x is in the left subtree.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] binary-tree-definition
A binary tree is a tree data structure in which each node has at most two children (left and right); it is a k-ary tree with k = 2
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-full-definition
A full (proper/strict/plane) binary tree is one where every node has either 0 or 2 children — no node has exactly one child
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-perfect-definition
A perfect binary tree has all interior nodes with exactly two children and all leaves at the same depth; it has 2^h leaves and 2^(h+1) - 1 total nodes at height h
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-complete-definition
A complete binary tree has every level completely filled except possibly the last, where nodes are packed as far left as possible; it can be efficiently stored in an array with zero wasted space
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-array-indexing
In array storage of a complete binary tree (0-indexed), left child is at 2i+1, right child at 2i+2, parent at floor((i-1)/2); 1-indexed: left=2i, right=2i+1, parent=floor(i/2)
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-leaves-eq-degree2-plus1
In any non-empty binary tree, the number of leaves equals the number of degree-2 (internal with two children) nodes plus 1: l = i₂ + 1
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-null-links
A binary tree with n nodes contains exactly n + 1 null links (null child pointers)
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-edges
A binary tree with n nodes has exactly n - 1 edges, since every node except the root has exactly one incoming edge
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-catalan-count
The number of structurally distinct full binary trees with n internal nodes equals the nth Catalan number C_n
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] binary-tree-degenerate
A degenerate (pathological) binary tree has each parent with only one child, making it structurally equivalent to a linked list with O(n) search instead of O(log n)
- Source: entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree

### [ACCEPT] bfs-definition
Breadth-first search is a queue-based graph traversal algorithm that explores all vertices at the current depth before moving to the next level (level-order traversal)
- Source: entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search

### [ACCEPT] bfs-complexity
BFS has time complexity O(|V|+|E|) for explicit graphs and space complexity O(|V|); for implicit graphs with branching factor b and depth d, time is O(b^(d+1))
- Source: entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search

### [ACCEPT] bfs-shortest-path-unweighted
BFS finds shortest paths in unweighted graphs and is complete (guaranteed to find a solution if one exists); it is optimal for unweighted shortest paths
- Source: entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search

### [ACCEPT] bucket-sort-definition
Bucket sort is a distribution sort that scatters elements into k buckets based on value, sorts each bucket individually (typically with insertion sort), then concatenates the results
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] bucket-sort-average-case
Bucket sort achieves O(n) average-case time when the number of buckets k = Theta(n) and input is uniformly distributed; the exact average is O(n + n²/k + k)
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] bucket-sort-worst-case
Bucket sort worst case is O(n²) when all elements cluster into one bucket (using insertion sort per bucket); worst case becomes O(n log n) if merge sort is used per bucket instead
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] bucket-sort-space
Bucket sort has space complexity O(n + k) where n is the number of elements and k is the number of buckets
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] bucket-sort-two-buckets-quicksort
Bucket sort with 2 buckets is effectively quicksort with the pivot at the midpoint of the value range
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] bucket-sort-counting-sort-degenerate
Bucket sort with bucket size 1 degenerates to counting sort; bucket sort trades counting sort's O(n + M) worst-case guarantee for lower O(n) average-case memory
- Source: entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort

### [ACCEPT] counting-sort-definition
Counting sort is a non-comparison integer sorting algorithm that counts occurrences of each key value and uses prefix sums to place elements in correct output positions, running in O(n + k) time and O(n + k) space where k is the key range
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] counting-sort-stable
Counting sort is a stable sort — elements with equal keys preserve their relative input order — achieved by iterating the input in reverse order during the placement phase
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] counting-sort-three-phases
Counting sort has three phases: (1) histogram — count occurrences of each key, (2) prefix sum — compute cumulative counts for output positions, (3) placement — iterate input in reverse, placing each element at its computed position
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] counting-sort-radix-subroutine
Counting sort is most commonly used as the per-digit subroutine in radix sort; its stability is essential so that earlier digit orderings are preserved across passes
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] counting-sort-not-comparison
Counting sort is not a comparison sort — it uses key values as array indices rather than comparing elements, so the Omega(n log n) comparison-sort lower bound does not apply
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] counting-sort-inplace-loses-stability
An in-place variant of counting sort exists but sacrifices stability, making it unsuitable as a radix sort subroutine
- Source: entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort

### [ACCEPT] dfs-definition
Depth-first search explores as far as possible along each branch before backtracking, using a stack (call stack or explicit) to track the current path; time is O(|V|+|E|) for explicit graphs
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-space-complexity
DFS space complexity is O(|V|) for full graph traversal (stack + visited set); O(bd) for depth-limited search on implicit graphs with branching factor b and depth d
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-not-optimal
DFS does not guarantee finding the shortest path — it is not optimal for shortest-path problems
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-reverse-postorder-topsort
Reverse postorder of DFS produces a topological sort for directed acyclic graphs (DAGs)
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-edge-classification
DFS classifies edges into four types: tree edges (in spanning tree), forward edges (ancestor to descendant), back edges (descendant to ancestor), and cross edges (all others); in undirected graphs only tree edges and back edges occur
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-vertex-orderings
DFS produces four vertex orderings: preorder (first visit, = Polish notation on expression trees), postorder (last visit, = reverse Polish notation), reverse preorder, and reverse postorder; reverse preorder is NOT the same as postorder
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-iterative-reverse-order
The iterative stack-of-nodes DFS visits neighbors in reverse order compared to the recursive version due to LIFO stack behavior; the iterator-based iterative version preserves the same order as recursion
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] dfs-lexicographic-p-complete
Computing a lexicographic DFS ordering is P-complete, meaning it is inherently sequential and hard to parallelize; a randomized DFS ordering can be computed in RNC
- Source: entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search

### [ACCEPT] quicksort-complexity
Quicksort has average-case time complexity O(n log n) and worst-case O(n²); the worst case occurs with poor pivot selection on sorted, reverse-sorted, or all-equal input (Lomuto scheme).
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-not-stable
Quicksort is not a stable sort: the relative order of equal elements is not preserved in standard implementations.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-space-complexity
Quicksort uses O(log n) auxiliary space when recursing into the smaller partition first (Hoare's 1962 tail-call optimization); without this optimization it uses O(n) auxiliary space.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-lomuto-vs-hoare
Hoare's partition scheme performs approximately 3x fewer swaps on average than Lomuto's; Lomuto degrades to O(n²) on all-equal elements while Hoare produces balanced partitions.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-three-way-partition
Three-way partition (Dutch National Flag) achieves O(n) best-case time when all elements are equal by partitioning into less-than, equal-to, and greater-than regions.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-median-of-three
Median-of-three pivot selection reduces quicksort's expected comparisons from ~1.386n log n to ~1.188n log n, an approximately 14% reduction.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-introsort
Introsort is a hybrid algorithm that starts with quicksort but switches to heapsort when recursion depth exceeds O(log n), guaranteeing O(n log n) worst-case time.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] quicksort-history
Quicksort was invented by Tony Hoare in 1959 at Moscow State University and published in 1961 in Communications of the ACM.
- Source: entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort

### [ACCEPT] radix-sort-non-comparative
Radix sort is a non-comparative sorting algorithm that distributes elements into buckets by individual digit values, circumventing the Ω(n log n) comparison sort lower bound.
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] radix-sort-complexity
Radix sort has time complexity Θ(d(n+k)) where d is key length in digits, n is number of keys, and k is the range of each digit; space complexity is O(d+n).
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] radix-sort-lsd-stable
LSD (least significant digit) radix sort is inherently stable; in-place MSD variants including binary quicksort are not stable. Stable MSD requires O(n) auxiliary memory.
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] radix-sort-linear-time
When key length d is constant and digit range k = O(n), radix sort runs in linear time Θ(n).
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] radix-sort-counting-subroutine
LSD radix sort uses counting sort as a stable subroutine for each digit pass; Seward developed both algorithms together at MIT in 1954.
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] radix-sort-lsd-vs-msd
LSD processes digits from rightmost to leftmost producing natural integer ordering; MSD processes leftmost to rightmost producing lexicographic ordering and is naturally recursive with each bucket independently sub-sorted.
- Source: entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort

### [ACCEPT] structural-recursion-terminates
Structural recursion (each call receives an immediate structural component of the input) always terminates on finite data, provable by structural induction. Generative recursion (generates new data and recurses on it) requires a separate termination proof.
- Source: entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)

### [ACCEPT] recursion-turing-complete
Recursion-only languages are Turing complete, equivalent in computational power to imperative languages with loops.
- Source: entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)

### [ACCEPT] single-vs-multiple-recursion
Single recursion (one self-reference) can be replaced by iteration in O(n) time and O(1) space. Multiple recursion (multiple self-references, e.g., naive Fibonacci) may require exponential time and space and cannot be replaced by iteration without an explicit stack.
- Source: entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)

### [ACCEPT] arms-length-recursion
Short-circuiting (arm's-length recursion) checks the base case before making the recursive call rather than after entering it, cutting function calls in half for perfect binary trees.
- Source: entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)

### [ACCEPT] recursion-first-languages
LISP (McCarthy, 1960) was the first language to use recursion as a core feature; ALGOL 60 independently added recursive procedure calls the same year.
- Source: entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)

### [ACCEPT] redblack-complexity
Red-black trees provide O(log n) worst-case time for search, insert, and delete operations.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-invariants
Red-black tree invariants: (1) every node is red or black, (2) all null nodes are black, (3) no red node has a red child, (4) every root-to-null path has the same number of black nodes.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-height-bound
In a red-black tree, the longest root-to-leaf path is at most twice the shortest, ensuring tree height h ∈ O(log n).
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-rotation-bounds
Red-black tree insert requires at most 2 rotations and delete requires at most 3 rotations; recoloring is O(log n) worst-case but O(1) amortized.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-234-isomorphism
Red-black trees are structurally isomorphic to 2-3-4 trees: a 2-node maps to a black node, a 3-node to black with one red child, a 4-node to black with two red children; color flip corresponds to node split.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-history
Red-black trees were invented by Guibas and Sedgewick in 1978, evolving from Bayer's symmetric binary B-trees (1972).
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-insert-red
New nodes in a red-black tree are inserted as red to preserve black-height; this may create a red-red violation requiring rebalancing.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] redblack-space-overhead
Red-black tree color storage costs 1 bit per node; in practice this can be zero by exploiting pointer alignment.
- Source: entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree

### [ACCEPT] union-find-definition
A disjoint-set (union-find) data structure maintains a collection of disjoint sets with three operations: MakeSet (create singleton set), Find (determine which set an element belongs to), and Union (merge two sets), represented as a forest of rooted trees
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-amortized-inverse-ackermann
With both path compression and union by rank, m union-find operations on n elements take O(m·α(n)) amortized time, where α is the inverse Ackermann function — effectively O(1) per operation for all practical input sizes
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-path-compression-variants
Three path compression variants all achieve the same asymptotic bound: full path compression (two-pass, reparent every node to root), path splitting (single-pass, reparent each node to its grandparent), and path halving (single-pass, reparent every other node to its grandparent)
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-union-strategies
Union by rank attaches the shorter tree under the root of the taller tree; union by size attaches the tree with fewer nodes under the root of the larger tree. Both strategies guarantee O(log n) tree height without path compression.
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-complexity-hierarchy
Union-find complexity hierarchy: no optimization O(n) per operation, path compression only O(log n) amortized, union by rank only O(m log n) total, both optimizations combined O(m·α(n)) total
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-kruskal
Union-find is used in Kruskal's minimum spanning tree algorithm to efficiently detect whether adding an edge would create a cycle, by checking if both endpoints are in the same set
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] union-find-history
Union-find was invented by Galler and Fischer in 1964; Tarjan proved the O(m·α(n)) upper bound in 1975; Fredman and Saks proved the matching Ω(m·α(n)) lower bound in 1989
- Source: entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure

### [ACCEPT] dnc-three-steps
Divide and conquer has three steps: (1) divide the problem into smaller sub-problems, (2) conquer each sub-problem recursively, (3) combine the sub-solutions to produce the solution to the original problem
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dnc-decrease-and-conquer
Decrease and conquer is the variant of divide and conquer where each problem reduces to only one sub-problem (e.g., binary search, Euclidean GCD); some authors reserve 'divide and conquer' for the multi-subproblem case only
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dnc-master-theorem
The Master Theorem determines the time complexity of divide-and-conquer recurrences from three parameters: the number of sub-problems, their size ratio relative to the original, and the cost of the divide/combine work
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dnc-cache-oblivious
Divide-and-conquer algorithms are cache-oblivious: once sub-problems fit in cache, all further work stays in cache without needing to know cache size explicitly
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dnc-merge-sort-first
Merge sort (von Neumann, 1945) was the first divide-and-conquer algorithm specifically developed for computers
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] karatsuba-disproved-kolmogorov
Karatsuba's algorithm (1960) disproved Kolmogorov's conjecture that integer multiplication requires Ω(n²) operations, achieving O(n^1.585) via divide and conquer with 3 sub-multiplications of half-size operands
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dnc-natural-parallelism
Divide-and-conquer algorithms are naturally parallelizable because sub-problems are independent and can be distributed across processors; the fork-join model maps directly to D&C execution
- Source: entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm

### [ACCEPT] dp-two-properties
Dynamic programming requires two properties: optimal substructure (optimal solution builds from optimal sub-solutions) AND overlapping sub-problems (same sub-problems recur). Both must be present for DP to apply.
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] dp-top-down-vs-bottom-up
Dynamic programming has two implementation approaches: top-down (memoization — recurse and cache results) and bottom-up (tabulation — solve smallest sub-problems first and iterate upward). Both achieve the same asymptotic complexity.
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] dp-bellman-equation
The Bellman equation V(state) = optimize{reward + V(next_state)} is the fundamental recurrence relation underlying dynamic programming
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] dp-bellman-1950s
Dynamic programming was developed by Richard Bellman in the 1950s as both a mathematical optimization method and an algorithmic paradigm
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] dp-vs-dnc
Merge sort and quicksort have optimal substructure but non-overlapping sub-problems, making them divide-and-conquer algorithms rather than dynamic programming; overlapping sub-problems (subproblem graph is a DAG, not a tree) is what distinguishes DP from D&C
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] dp-fibonacci-example
Fibonacci computation is the canonical dynamic programming example: naive recursive computation is O(2^n) due to redundant sub-problem evaluation, but reduces to O(n) with either memoization or tabulation
- Source: entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming

### [ACCEPT] set-adt-definition
A set is an abstract data type that stores a collection of distinct values with no particular ordering; its primary operation is membership testing, not element retrieval by index.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-hash-table-complexity
Hash table implementation of a set provides O(1) average-case and O(n) worst-case time for membership test, add, and delete operations.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-bst-complexity
Self-balancing BST implementation of a set (e.g., red-black, AVL) provides O(log n) for most operations and additionally supports sorted iteration.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-fold-requires-associative-commutative
The fold operation on a set requires the combining function F to be both associative and commutative, because the iteration order over set elements is arbitrary and unspecified.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-as-map-with-dummy-values
A set can be implemented as an associative array (map) where keys are the set elements and values are a sentinel (e.g., 1 or unit type); conversely, a set is a map where the value type is the unit type.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-bit-array-integer-subsets
Bit array implementation for sets that are subsets of integers 1..n supports O(1) membership test and very efficient union/intersection via bitwise operations.
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] python-empty-set-literal
In Python, {} creates an empty dict, not an empty set; an empty set must be created with set().
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] set-hash-consistency-contract
A set hash function must satisfy the consistency contract: if equal(S1, S2) then hash(S1) = hash(S2).
- Source: entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)

### [ACCEPT] sliding-window-sequence-modulus
In a sliding window protocol, the sequence number space N must satisfy N >= wt + wr to avoid ambiguity between new packets and retransmissions, where wt is the sender window size and wr is the receiver window size.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] stop-and-wait-degenerate-case
Stop-and-wait ARQ is a degenerate sliding window with wt=1, wr=1, requiring only N=2 (a 1-bit sequence number).
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] go-back-n-vs-selective-repeat
Go-Back-N (wr=1) discards out-of-order packets and retransmits the entire window on loss; Selective Repeat (wr>1) buffers out-of-order packets and retransmits only the lost packet.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] tcp-window-field-16-bit
TCP's receiver window field is 16 bits, limiting the base window to 64 KB; RFC 1323 window scaling extends this limit.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] sliding-window-bdp
A sliding window must exceed the bandwidth-delay product (BDP) of the link to fully utilize available bandwidth; otherwise the sender idles waiting for acknowledgments.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] tcp-slow-start
TCP slow start doubles the congestion window each RTT (exponential growth) until reaching the slow-start threshold, then switches to linear growth (congestion avoidance) of one segment per RTT.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] comparison-sort-lower-bound
No comparison sort can do better than O(n log n) on average; this is a proven information-theoretic lower bound requiring at least n log n − 1.4427n + O(log n) comparisons.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] quicksort-complexity
Quicksort runs in O(n log n) average-case and O(n^2) worst-case time, uses O(log n) stack space (in-place), and is not stable.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] mergesort-complexity
Merge sort runs in O(n log n) in all cases (best, average, worst), requires O(n) extra memory, is stable, and is highly parallelizable.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] heapsort-complexity
Heapsort runs in O(n log n) in all cases, uses O(1) extra memory (in-place), and is not stable.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] timsort-complexity
Timsort achieves O(n) best-case on nearly-sorted input and O(n log n) average/worst, uses O(n) memory, is stable, and is the default sort in Python, Java, and Android.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] counting-sort-complexity
Counting sort runs in O(n+r) time and space where r is the range of input values; it is stable but only practical when r is O(n).
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] stable-sort-definition
A stable sort preserves the relative order of records with equal keys; this is critical when sorting by multiple keys sequentially (the later stable sort preserves ordering from the earlier sort).
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] block-sort-unique
Block sort is the only known O(n log n) comparison sort that is both stable and uses only O(1) extra memory.
- Source: entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm

### [ACCEPT] stack-adt-definition
A stack is an abstract data type implementing LIFO (last-in, first-out) access with two principal operations: push (add to top) and pop (remove from top), both operating on a single end called the top.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] stack-array-vs-linkedlist
Array-based stacks provide O(1) push/pop with bounded capacity; linked-list-based stacks provide O(1) worst-case push/pop with no overflow (until memory exhaustion) but incur per-element pointer overhead.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] stack-peek-non-essential
Peek (top-of-stack) is a non-essential stack operation — it can be decomposed into a pop followed by a push of the same element.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] stack-overflow-underflow
Stack overflow occurs when push is called on a bounded stack at full capacity; stack underflow occurs when pop or peek is called on an empty stack.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] stack-applications
Stacks are used in expression evaluation (RPN/postfix), syntax parsing (pushdown automata), backtracking algorithms (DFS, branch-and-bound), call stack management, Graham scan (convex hull), and all nearest smaller values.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] call-stack-security
The call stack stores return addresses and local variables; sharing data and return addresses on the same stack creates stack smashing (buffer overflow) vulnerabilities.
- Source: entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

### [ACCEPT] topological-sort-iff-dag
A topological ordering of a directed graph exists if and only if the graph is a directed acyclic graph (DAG); this is the fundamental existence theorem.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] topological-sort-complexity
Both standard topological sort algorithms (Kahn's BFS-based and DFS-based) run in O(|V| + |E|) linear time.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] kahns-vs-dfs-topo-sort
Kahn's algorithm detects cycles by checking if edges remain after processing all zero-indegree nodes; DFS-based topological sort detects cycles via temporary marks (back edges) and prepends nodes to the output list.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] topological-sort-unique-iff-hamiltonian
A DAG's topological ordering is unique if and only if every pair of consecutive vertices in the ordering is connected by an edge, which is equivalent to the existence of a directed Hamiltonian path in the DAG.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] dag-shortest-path-linear
Shortest paths in a weighted DAG can be computed in Θ(|V| + |E|) time by relaxing edges in topological order; this works with negative edge weights, unlike Dijkstra's algorithm.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] topological-sort-applications
Topological sort applications include: task scheduling, makefile compilation order, spreadsheet formula evaluation, instruction scheduling, linker symbol resolution, and database foreign key table loading.
- Source: entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting

### [ACCEPT] kruskal-definition
Kruskal's algorithm is a greedy algorithm that finds a minimum spanning tree (or forest for disconnected graphs) by repeatedly adding the lowest-weight edge that does not create a cycle, using a disjoint-set (union-find) data structure for cycle detection.
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] kruskal-complexity
Kruskal's algorithm has time complexity O(E log V) with comparison sort, equivalent to O(E log E) since log E = Θ(log V) for graphs without isolated vertices. Space complexity is O(V + E).
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] kruskal-presorted-complexity
When edges are pre-sorted or have small integer weights (enabling counting/radix sort), Kruskal's complexity drops to O(E · α(V)), dominated by union-find operations rather than sorting.
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] kruskal-sparse-vs-prim-dense
Kruskal's algorithm is optimal for sparse graphs; Prim's algorithm (with Fibonacci heap) is better for dense graphs.
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] kruskal-mst-edge-count
Kruskal's algorithm produces exactly V-1 edges for a connected graph with V vertices. For disconnected graphs it produces a minimum spanning forest with one tree per connected component.
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] filter-kruskal-variant
Filter-Kruskal is a parallelizable variant of Kruskal's that partitions edges similarly to quicksort, reducing sorting overhead. With parallel sorting on O(log n) processors, runtime reduces to O(E · α(V)).
- Source: entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm

### [ACCEPT] linked-list-access-o-n
Linked list access is O(n) — sequential traversal only, no random access. Arrays have superior cache locality because linked list nodes are scattered in memory.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] linked-list-insert-delete-o1
Linked list insertion/deletion at a known position is O(1) requiring only pointer reassignment. However, finding that position requires O(n) traversal. In singly linked lists, deletion requires a pointer to the previous node; doubly linked lists can delete given only the node's address.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] singly-vs-doubly-linked
A singly linked list has one pointer (next) per node supporting forward traversal only. A doubly linked list has two pointers (next and prev) supporting bidirectional traversal at the cost of extra space per node.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] circular-linked-list-definition
In a circular linked list, the last node points back to the first node instead of null. A single pointer to the last node provides O(1) access to both ends, making it useful for queue implementations and naturally cyclic structures like round-robin scheduling.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] xor-linked-list
XOR-linking implements a doubly linked list using only one link field per node by storing prev XOR next. It saves space but requires bitwise address operations, limiting portability to high-level languages.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] linked-list-tail-sharing
Tail-sharing (multiple lists sharing a common suffix) is exclusive to singly linked linear lists — a form of persistent data structure. Doubly linked and circular lists cannot share structure this way.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] sentinel-node-purpose
A sentinel (dummy) node added before the first or after the last element of a linked list eliminates null-check edge cases in algorithms, trading extra space for simpler code — a poor tradeoff when many short lists exist.
- Source: entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list

### [ACCEPT] non-comparison-sort-linear
Non-comparison sorts (counting sort, radix sort, bucket sort) can achieve O(n) time, beating the Ω(n log n) lower bound for comparison-based sorting, but require assumptions about the input (e.g., bounded integer keys).
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] timsort-hybrid
Timsort is a hybrid sorting algorithm combining merge sort and insertion sort. It is used as the default sort in Python (since 2.3) and Java SE 7+.
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] introsort-hybrid
Introsort begins with quicksort and switches to heapsort when recursion depth exceeds a threshold, guaranteeing O(n log n) worst-case time while retaining quicksort's practical speed.
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] floyd-warshall-all-pairs
Floyd-Warshall solves the all-pairs shortest path problem. Johnson's algorithm is better for sparse graphs. Both handle negative edge weights (but not negative cycles).
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] aho-corasick-multi-pattern
Aho-Corasick searches for multiple patterns simultaneously using a trie-based automaton, unlike KMP which searches for a single pattern. KMP avoids re-examination of matched characters; Boyer-Moore achieves sublinear performance in practice.
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] karatsuba-sub-quadratic
Karatsuba multiplication is the simplest sub-quadratic multiplication algorithm, reducing integer multiplication from O(n²) to O(n^log₂3) ≈ O(n^1.585) by trading one multiplication for additions.
- Source: entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms

### [ACCEPT] adt-property-axes
Abstract data types vary on two axes: ordered vs unordered (elements have explicit sequence or not), and unique vs non-unique (duplicates allowed or not). List = ordered + non-unique; Set = unordered + unique; Map = unique keys; Multiset/Bag = unordered + non-unique.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] trees-subset-of-dags
Trees are a subset of directed acyclic graphs (DAGs), which are a subset of general graphs. Trees are connected acyclic graphs with a root; DAGs allow multiple parents but no cycles; general graphs allow cycles.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] b-plus-tree-leaves-only
B+ trees store data only in leaf nodes (internal nodes store only keys for routing), making them efficient for range queries. B* trees delay node splits for higher occupancy. Both are B-tree variants optimized for disk-based storage.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] bloom-filter-properties
A Bloom filter is a probabilistic data structure with no false negatives, tunable false positive rate, and space-efficient membership testing. Standard Bloom filters cannot support deletion; counting variants can.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] skip-list-randomized
A skip list is a randomized alternative to balanced BSTs, achieving O(log n) expected time for search, insert, and delete using multiple levels of linked lists with probabilistic balancing.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] tagged-union-vs-union
A tagged union (discriminated union, sum type, variant) stores a discriminator indicating which type is currently active; a plain union does not track which member is valid. Tagged unions are type-safe; plain unions are not.
- Source: entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures

### [ACCEPT] lcs-dp-complexity
The longest common subsequence (LCS) of two sequences of lengths m and n can be computed in O(mn) time and O(mn) space using dynamic programming. Space can be reduced to O(min(m,n)) for length-only computation, but full table is needed for traceback.
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] lcs-general-np-hard
The LCS problem for an arbitrary number of sequences is NP-hard. For a fixed number N of sequences, dynamic programming gives O(N · product of all sequence lengths).
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] lcs-optimal-substructure
LCS exhibits optimal substructure: if both sequences end with the same character, extend LCS of shorter prefixes; if they end with different characters, take the longer of the two subproblems dropping one character from each sequence.
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] lcs-scs-edit-distance
LCS relates to other problems: shortest common supersequence |SCS(X,Y)| = n + m - |LCS(X,Y)|; edit distance with only insertions and deletions (no substitution) d'(X,Y) = n + m - 2·|LCS(X,Y)|.
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] lcs-not-unique
The longest common subsequence is not necessarily unique — multiple LCSs of the same maximum length may exist. The number of common subsequences can be exponential, making enumeration of all LCSs non-polynomial.
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] lcs-diff-backbone
LCS is the algorithmic backbone of diff utilities, patch, and merge operations in version control systems like Git. The LCS DP table directly produces a diff by tracing diagonal moves (match), up moves (deletion), and left moves (insertion).
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] subsequence-vs-substring
A subsequence preserves relative order of elements but they need not be adjacent in the original sequence; a substring requires contiguous positions. LCS (longest common subsequence) and longest common substring are different problems with different DP formulations.
- Source: entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence

### [ACCEPT] heap-property-definition
A heap satisfies the heap property: in a max-heap every parent key >= its children's keys; in a min-heap every parent key <= its children's keys. Only vertical (parent-child) relationships are constrained — siblings and cousins have no ordering.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] binary-heap-array-formulas
A binary heap is stored implicitly in an array with no pointer overhead. With 0-based indexing: left child = 2i+1, right child = 2i+2, parent = floor((i-1)/2). With 1-based indexing: left child = 2i, right child = 2i+1, parent = floor(i/2).
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] binary-heap-operations-complexity
Binary heap operation complexities: find-max Θ(1), insert Θ(log n), extract-max Θ(log n), increase-key Θ(log n), merge Θ(n). Insert uses sift-up; extract-max replaces root with last element then sift-down.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] floyd-build-heap-linear
Floyd's bottom-up heap construction (heapify) runs in Θ(n) time, NOT O(n log n). It sift-downs from the last non-leaf node to the root. Most nodes are near the leaves so most sift-downs are short — the geometric series n/2 + n/4 + n/8 + ... = n proves this. Repeated insertion is O(n log n) by contrast.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] fibonacci-heap-amortized-bounds
Fibonacci heap achieves O(1) amortized insert and O(1) amortized decrease-key, with O(log n) amortized delete-max. These bounds make it superior for Dijkstra's (O(E + V log V)) and Prim's algorithms compared to binary heaps.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] brodal-queue-optimal-bounds
Brodal queues and strict Fibonacci heaps achieve theoretically optimal worst-case (not amortized) bounds: Θ(1) for find-max, insert, increase-key, and meld; Θ(log n) for delete-max.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] heap-vs-bst-no-search
Unlike binary search trees, heaps have no sibling ordering and do not support efficient search for arbitrary elements, ordered traversal, or predecessor/successor queries.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] heap-replace-operation
The heap replace operation (pop root and push new key) is more efficient than separate extract + insert because it requires only one sift-down pass instead of a sift-down followed by a sift-up.
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] heapsort-all-case-nlogn
Heapsort has O(n log n) time complexity in best, average, and worst cases for distinct keys. Best case is O(n) when all keys are equal. It uses O(1) auxiliary space (in-place).
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] heapsort-not-stable
Heapsort is not a stable sort — it does not preserve the relative order of equal elements.
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] heapsort-two-phases
Heapsort works in two phases: (1) build a max-heap from the input array in O(n) using Floyd's bottom-up construction, (2) repeatedly extract the maximum element (swap root with last unsorted element, sift-down) in O(n log n) total.
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] heapsort-vs-quicksort-practice
Heapsort is typically 2-3x slower than quicksort in practice due to poor cache locality and branch prediction behavior, despite heapsort's guaranteed O(n log n) worst case vs quicksort's O(n²) worst case.
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] heapsort-introsort-fallback
Introsort is a hybrid sorting algorithm that starts with quicksort and falls back to heapsort when it detects degenerate O(n²) behavior, guaranteeing O(n log n) worst case. Pattern-defeating quicksort also uses heapsort as a fallback.
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] heapsort-siftdown-bounded-by-height
Each siftDown call in heapsort is bounded by the tree height: floor(log₂ n) iterations. siftDown is the core primitive — it repairs a heap where only the root may violate the heap property.
- Source: entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort

### [ACCEPT] interval-tree-output-sensitive
An interval tree answers overlap queries (find all intervals containing a query point) in O(log n + m) time where m is the number of results reported. This is output-sensitive and asymptotically optimal, vs O(n) for brute force.
- Source: entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree

### [ACCEPT] interval-tree-two-designs
Two principal interval tree designs exist: the centered interval tree (recursively partitions around a center point, stores overlapping intervals in two sorted lists) and the augmented tree (BST keyed by low endpoint, each node annotated with max high endpoint in subtree — described in CLRS Section 14.3).
- Source: entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree

### [ACCEPT] interval-tree-complexity
Interval tree complexity: O(n log n) build time, O(n) space, O(log n + m) query time, O(log n) insert/delete. The centered tree generalizes to higher dimensions with O(n log n) space.
- Source: entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree

### [ACCEPT] augmented-tree-overlap-condition
In an augmented interval tree, each node stores max(high endpoint) of its entire subtree. Two intervals A and B overlap iff A_low <= B_high AND B_low <= A_high. This annotation enables pruning entire subtrees during queries.
- Source: entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree

### [ACCEPT] kadane-algorithm-linear
Kadane's algorithm solves the maximum subarray problem in O(n) time and O(1) space using a single-pass scan with two variables: current_sum (best sum ending at current position) and best_sum (global best). This is optimal since any algorithm must read the entire input.
- Source: entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm

### [ACCEPT] kadane-recurrence
Kadane's key recurrence: current_sum[j] = max(A[j], current_sum[j-1] + A[j]) — at each position, decide whether to extend the previous subarray or start a new one. Then best_sum = max(best_sum, current_sum[j]).
- Source: entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm

### [ACCEPT] kadane-empty-vs-nonempty
Kadane's algorithm has two variants: (1) no empty subarrays allowed — initialize best_sum = -inf, use max(x, current_sum + x); (2) empty subarrays allowed — initialize best_sum = 0, use max(0, current_sum + x). The difference is a common source of exam questions.
- Source: entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm

### [ACCEPT] max-subarray-historical-progression
Maximum subarray solutions progressed: O(n³) brute force → O(n²) prefix sums (Grenander) → O(n log n) divide and conquer (Shamos) → O(n) dynamic programming (Kadane). The problem was proposed by Grenander in 1977 as a simplified model for maximum likelihood estimation in digitized images.
- Source: entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm

### [ACCEPT] max-subarray-2d-cubic
The maximum sum rectangle in a 2D array is solvable in O(n³) time using Kadane's algorithm as a subroutine. A sub-cubic algorithm would imply a fast all-pairs shortest paths algorithm, suggesting this bound may be optimal.
- Source: entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm

### [ACCEPT] knapsack-dp-pseudo-polynomial
The 0-1 knapsack DP solution runs in O(nW) time and O(nW) space. This is pseudo-polynomial, not polynomial, because W is exponential in its bit-length (log W bits). Space is reducible to O(W) if only the optimal value (not item selection) is needed.
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] knapsack-weakly-np-complete
The knapsack problem (decision version) is NP-complete. With integer weights/profits it is weakly NP-complete (admits pseudo-polynomial time solution). With rational weights/profits it is strongly NP-complete but still admits an FPTAS.
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] knapsack-01-recurrence
The 0-1 knapsack recurrence: m[i,w] = max(m[i-1,w], m[i-1,w-w_i] + v_i) when w_i <= w; m[i,w] = m[i-1,w] when w_i > w. Base case: m[0,w] = 0. Each item is either taken or skipped.
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] knapsack-three-variants
Three main knapsack variants: 0-1 (each item included or not, x_i in {0,1}), bounded (up to c copies, x_i in {0,...,c}), unbounded (unlimited copies, x_i in natural numbers). The unbounded variant has a simpler 1D DP: m[w] = max(v_i + m[w-w_i]).
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] subset-sum-knapsack-special-case
The subset sum problem is a special case of the 0-1 knapsack problem where w_i = v_i for all items. It is one of Karp's 21 NP-complete problems and has connections to cryptography (Merkle-Hellman knapsack cryptosystem).
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] knapsack-fptas-exists
The knapsack problem admits a fully polynomial-time approximation scheme (FPTAS), which uses the pseudo-polynomial DP as a subroutine. This distinguishes it from strongly NP-hard problems which have no FPTAS unless P=NP.
- Source: entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem

### [ACCEPT] heap-stdlib-implementations
Standard library heap implementations: Python heapq (min-heap), Java PriorityQueue (min-heap default), C++ std::priority_queue (max-heap default), Rust BinaryHeap (max-heap), Go container/heap (interface-based), .NET PriorityQueue (.NET 6+, min-heap, quaternary).
- Source: entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)

### [ACCEPT] floyd-warshall-definition
The Floyd-Warshall algorithm solves the all-pairs shortest path problem using dynamic programming, decomposing paths through progressively larger sets of intermediate vertices
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-complexity
Floyd-Warshall runs in Θ(|V|³) time and Θ(|V|²) space in all cases
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-loop-order
Floyd-Warshall requires KIJ loop order (k outermost); incorrect loop ordering produces wrong results
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-negative-weights
Floyd-Warshall handles negative edge weights but not negative cycles; negative cycles are detected by checking for negative values on the main diagonal of the distance matrix
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-path-reconstruction
Floyd-Warshall reconstructs shortest paths via a predecessor matrix requiring Θ(|V|²) additional space
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-transitive-closure
Warshall's algorithm (1962) is a Boolean specialization of Floyd-Warshall that computes the transitive closure of a graph by replacing min/+ with OR/AND operations
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] floyd-warshall-sparse-alternatives
For sparse graphs, running Dijkstra from each vertex or using Johnson's algorithm is faster than Floyd-Warshall for all-pairs shortest paths
- Source: entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm

### [ACCEPT] adj-list-space-complexity
Adjacency list representation uses O(|V| + |E|) space and is the preferred representation for sparse graphs where |E| << |V|²
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] adj-matrix-space-complexity
Adjacency matrix representation uses O(|V|²) space and is preferred for dense graphs or when O(1) edge existence testing is needed
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] adj-list-vs-matrix-adjacency-test
Adjacency test is O(|V|) for adjacency list but O(1) for adjacency matrix — a fundamental complexity tradeoff between the two representations
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] adj-list-hash-optimization
Replacing adjacency lists with hash sets gives amortized O(1) adjacency test and edge removal, improving over the default O(|V|) adjacency test of plain adjacency lists
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] adj-matrix-add-vertex-cost
Adding a vertex to an adjacency matrix costs O(|V|²) due to matrix resizing, compared to O(1) for an adjacency list
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] incidence-matrix-poor-complexity
The incidence matrix representation uses O(|V| · |E|) space and has O(|V| · |E|) cost for every mutating operation, making it almost never the optimal choice
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] graph-partitioning-np-hard
Graph partitioning is NP-hard; practical approaches use heuristics such as 1D partitioning (requires All-to-All communication) and 2D partitioning (bounds communication partners to p_r + p_c - 1)
- Source: entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)

### [ACCEPT] graph-theory-origin-euler-1736
Graph theory originated with Euler's 1736 paper on the Seven Bridges of Königsberg; the term 'graph' was later introduced by J.J. Sylvester in 1878
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] four-color-theorem
The four-color theorem states that any planar map can be colored with at most 4 colors so no two adjacent regions share a color; proved by Appel and Haken (1976) using computer assistance
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] wagners-theorem-planarity
Wagner's theorem: a graph is planar if and only if it has no K₅ or K₃,₃ minor
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] farys-theorem-straight-line
Fáry's theorem: every planar graph can be drawn in the plane with straight-line edges (no curves needed)
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] laplacian-matrix-definition
The Laplacian matrix of a graph is L = D - A, where D is the diagonal degree matrix and A is the adjacency matrix; its eigenvalues are studied in spectral graph theory
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] robertson-seymour-theorem
The Robertson-Seymour theorem states that every graph property closed under minors and subgraphs has a finite set of forbidden minors characterizing it
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] steinitz-theorem
Steinitz's theorem: a graph is a polyhedral graph (skeleton of a 3D convex polyhedron) if and only if it is 3-connected and planar
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] frucht-theorem
Frucht's theorem: every finite group is the automorphism group of some graph
- Source: entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory

### [ACCEPT] greedy-special-case-of-dp
A greedy algorithm is a special case of dynamic programming that maintains only one partial solution instead of many, requiring more problem structure (matroid/greedoid) to guarantee optimality
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] greedy-exchange-argument
The exchange argument is the standard proof technique for greedy correctness: assume an optimal solution differing from greedy, show exchanging choices at the first difference point cannot worsen the result, conclude optimality by induction
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] greedy-matroid-optimality
Edmonds showed greedy algorithms optimally solve linear combinatorial optimization problems with matroid structure; Korte and Lovász generalized this to greedoids
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] fractional-vs-01-knapsack
Fractional knapsack admits a polynomial-time greedy solution (sort by value/weight ratio), while 0-1 knapsack is NP-hard — a key distinction in algorithm design
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] greedy-tsp-log-n-approximation
Greedy nearest-neighbor TSP yields a tour at most Θ(log n) times the optimal tour length
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] gale-shapley-not-greedy
The Gale-Shapley stable matching algorithm is explicitly NOT greedy because it modifies existing pairings — greedy algorithms by definition never revise past choices
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] greedy-coloring-bound
The greedy graph coloring algorithm yields the bound χ(G) ≤ Δ(G) + 1, where χ is the chromatic number and Δ is the maximum degree
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] greedy-classic-algorithms
Dijkstra's shortest path, Prim's MST, Kruskal's MST, and Huffman coding are all examples of greedy algorithms that produce optimal solutions
- Source: entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm

### [ACCEPT] hash-table-average-o1
Hash tables provide average-case O(1) time for search, insert, and delete operations, with worst-case O(n) for all three when all keys hash to the same bucket
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] hash-table-load-factor
Hash table load factor α = n/m (stored elements / total buckets) is the key metric governing performance; tables are resized when α exceeds a threshold α_max
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] open-addressing-load-limit
Open addressing requires load factor α < 1 (table full at α = 1); practical optimal range is 0.6–0.75. Performance degrades sharply as α approaches 1
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] separate-chaining-load-range
Separate chaining allows load factor α > 1 with optimal α_max between 1 and 3; performance degrades gradually with no hard failure point unlike open addressing
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] open-addressing-probe-sequences
Open addressing uses three probe sequence strategies: linear probing (fixed interval, susceptible to primary clustering), quadratic probing (quadratic polynomial intervals), and double hashing (interval from secondary hash function)
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] hash-table-rehashing-amortized
Hash table rehashing (triggered when α exceeds α_max) doubles the table size and recomputes all hash indices; amortized cost is O(1) per operation over time
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] perfect-hash-function-definition
A perfect hash function is injective on the key set S (every key maps to a unique index with zero collisions); only possible when all keys are known in advance
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] hash-table-no-ordered-ops
Hash tables cannot efficiently support ordered operations (min, max, successor, range queries); balanced BSTs are preferred for workloads requiring sorted-order access
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] dfs-stack-bfs-queue
Depth-first search (DFS) on a tree uses a stack (explicit or implicit call stack); breadth-first search (BFS) uses a queue. The data structure choice determines traversal order.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] inorder-bst-sorted
In-order traversal (LNR) of a binary search tree visits keys in ascending sorted order; reverse in-order (RNL) visits keys in descending order.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] tree-reconstruction-uniqueness
Pre-order paired with in-order, or post-order paired with in-order, uniquely determines a binary tree with distinct elements. Pre-order paired with post-order alone is ambiguous and does not uniquely determine the tree.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] morris-traversal-o1-space
Morris traversal performs in-order tree traversal in O(1) extra space by temporarily repurposing null child pointers as threading links to the in-order predecessor/successor, then restoring the tree structure. It cannot support concurrent traversals.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] dfs-space-o-height-bfs-space-o-width
DFS (recursive or iterative with explicit stack) requires O(h) space where h is tree height. BFS requires O(w) space where w is maximum tree width, which can be up to n/2 for a complete binary tree.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] preorder-prefix-postorder-postfix
Pre-order traversal of an expression tree produces prefix notation (Polish notation); post-order traversal produces postfix notation (Reverse Polish notation), which is directly translatable to stack machine code.
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] preorder-copy-postorder-delete
Pre-order traversal is used to copy a tree (parent created before children); post-order traversal is used to delete a tree (children freed before parent).
- Source: entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal

### [ACCEPT] trie-operations-o-m
Trie search, insert, and delete all run in O(m) time where m is the length of the key string, independent of the number of keys stored in the trie.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-vs-bst-complexity
In a balanced BST, string search is O(m log n) because O(log n) comparisons are needed and each string comparison costs O(m). Tries eliminate the log n factor, achieving O(m) regardless of n.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-implicit-key-storage
Trie nodes do not store their keys explicitly; a node's position in the tree determines its key, with edges labeled by individual characters. Children share a common prefix with their parent.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-no-hash-collisions
Tries have no hash collisions and provide worst-case O(m) lookup, compared to hash tables which degrade to O(N) with collisions. However, hash tables outperform tries on secondary storage due to high random-access latency.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-lexicographic-preorder
Pre-order traversal of a trie yields keys in lexicographic (sorted) order. Building a trie and traversing in pre-order is equivalent to radix sort.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] radix-tree-compressed-trie
A radix tree (compressed trie) merges single-child chain nodes into one node, saving space for sparse key sets. The Patricia tree is the binary-encoded variant using skip numbers to avoid empty subtrees.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-dfa-equivalence
A trie can be viewed as a tree-shaped deterministic finite automaton (DFA). A DAFSA (minimal deterministic acyclic FSA) is more space-efficient when only dictionary membership is needed, because it also compresses shared suffixes.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] memoization-requires-purity
Memoization requires referential transparency: only pure functions (no side effects) can be correctly memoized, because calling the function must have the same effect as substituting its return value.
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] memoization-runtime-not-compile-time
Memoization is a runtime optimization technique, distinct from compile-time optimizations such as strength reduction; it is machine-independent and cross-platform.
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] memoization-automatic-via-hof
Automatic memoization can be applied externally to any referentially transparent function using higher-order functions, closures, or decorators, without modifying the original function.
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] memoization-top-down-dp
Memoization is the top-down counterpart to bottom-up dynamic programming; both cache subproblem results to avoid redundant computation.
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] packrat-parsing-linear-time
Packrat parsing (Ford 2002) uses memoization to guarantee linear-time parsing of Parsing Expression Grammars (PEGs).
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] memoization-parsing-complexity
Memoization reduces exponential backtracking parsers to polynomial time: O(n³) for non-left-recursive grammars, O(n⁴) for left-recursive grammars (Frost, Hafiz, Callaghan 2007).
- Source: entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization

### [ACCEPT] mergesort-all-case-nlogn
Merge sort guarantees O(n log n) time complexity in all cases: worst, average, and best.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] mergesort-space-complexity
Merge sort requires O(n) auxiliary space for array implementations; linked-list implementations need only O(1) auxiliary space plus O(log n) stack space.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] mergesort-stable
Merge sort is stable: equal elements retain their original relative order in most implementations. This is a key differentiator from quicksort and heapsort.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] mergesort-recurrence
Merge sort's recurrence relation is T(n) = 2T(n/2) + n, solved by the master theorem to O(n log n).
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] natural-mergesort-best-case
Natural merge sort exploits pre-existing sorted runs in the input, achieving O(n) best-case time on already-sorted data with a single pass.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] mergesort-external-sorting
Merge sort is the standard algorithm for external sorting (data too large for memory), used with tape drives or disk via k-way merge; a basic 4-tape version requires log₂(n) passes.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] mergesort-vs-quicksort
Merge sort's worst case uses ~39% fewer comparisons than quicksort's average case. Merge sort guarantees O(n log n) while quicksort degrades to O(n²) worst case, but quicksort has better cache locality on arrays.
- Source: entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort

### [ACCEPT] prim-definition
Prim's algorithm is a greedy algorithm that finds a minimum spanning tree by growing from an arbitrary starting vertex, always adding the cheapest edge crossing the cut between tree and non-tree vertices.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-adjacency-matrix-complexity
Prim's algorithm with adjacency matrix and linear search runs in O(|V|²) total time.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-binary-heap-complexity
Prim's algorithm with binary heap and adjacency list runs in O(|E| log |V|) total time.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-fibonacci-heap-complexity
Prim's algorithm with Fibonacci heap and adjacency list runs in O(|E| + |V| log |V|) total time, achieving linear time on sufficiently dense graphs.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-requires-connected-graph
Prim's algorithm in its basic form works only on connected graphs, unlike Kruskal's and Borůvka's which find minimum spanning forests of disconnected graphs directly.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-cut-property-correctness
Prim's algorithm correctness relies on the cut property: the lightest edge crossing any cut of a graph must belong to some minimum spanning tree.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-vs-kruskal-density
Prim's algorithm is preferred over Kruskal's for dense graphs; Kruskal's is preferred for sparse graphs.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] prim-dijkstra-structural-similarity
Prim's algorithm is structurally almost identical to Dijkstra's: same priority-queue-based loop, but Prim relaxes edges by individual edge weight while Dijkstra relaxes by cumulative path cost.
- Source: entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm

### [ACCEPT] priority-queue-is-adt
A priority queue is an abstract data type (not a data structure); it can be implemented with unsorted arrays, sorted arrays, binary heaps, binomial heaps, Fibonacci heaps, or balanced BSTs, each with different complexity tradeoffs.
- Source: entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue

### [ACCEPT] stack-queue-as-priority-queue
A stack (LIFO) and queue (FIFO) are special cases of a priority queue, where priority is determined by insertion order (descending for stack, ascending for queue).
- Source: entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue

### [ACCEPT] cpp-maxheap-java-minheap
C++ std::priority_queue defaults to max-heap ordering; Java PriorityQueue defaults to min-heap ordering.
- Source: entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue

### [ACCEPT] priority-queue-sorting-equivalence
There is a deep equivalence between priority queues and sorting algorithms: using a priority queue to sort yields a comparison sort (heapsort ↔ binary heap, selection sort ↔ unsorted array, insertion sort ↔ sorted array, tree sort ↔ BST).
- Source: entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue

### [ACCEPT] circular-buffer-modular-arithmetic
A circular buffer implements a bounded queue using a fixed-length array with modular index arithmetic (index mod n), logically wrapping around to avoid costly element shifting on dequeue.
- Source: entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)

### [ACCEPT] realtime-queue-worst-case-o1
A real-time queue achieves worst-case O(1) for all operations using three lists (f, r, s) with lazy evaluation and memoization; the schedule list s incrementally forces computation so no single operation bears the full O(n) reversal cost.
- Source: entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)

### [ACCEPT] realtime-queue-invariant
The real-time queue maintains the invariant |s| = |f| - |r|; when s is empty, |f| = |r| and a rotation is triggered.
- Source: entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)

### [ACCEPT] bfs-queue-dfs-stack
Breadth-first search uses a queue to explore graph nodes level by level; depth-first search uses a stack. The choice of data structure is the fundamental distinction between the two traversal strategies.
- Source: entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)


---

**Generated:** 2026-11-11
**Source:** 52 entries from /home/forge/workspace/entries/
**Model:** openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-balance-factor-formula
An AVL tree balance factor is computed as height(right subtree) − height(left subtree).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-balance-factor-storage-2-bits
An AVL tree balance factor can be stored in 2 bits per node.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-four-rotation-cases
AVL insertion rebalancing uses four rotation cases: RR, LL, RL, and LR, each taking O(1) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-insert-retrace-stops-at-zero
During AVL insertion retracing, the retrace stops when a node's balance factor becomes 0.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-delete-retrace-stops-at-plus-minus-one
During AVL deletion retracing, the retrace stops when a node's balance factor becomes +1 or −1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-traversal-linear
In-order traversal of an AVL tree takes O(n) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] avl-successor-predecessor-amortized-o1
Successor and predecessor queries in an AVL tree have amortized O(1) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-AVL_tree.md
- Source URL: https://en.wikipedia.org/wiki/AVL_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] astar-evaluation-function
A* selects nodes using the evaluation function f(n) = g(n) + h(n), where g(n) is the cost from the start and h(n) is the heuristic estimate to the goal.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] astar-admissible-heuristic-definition
An admissible A* heuristic never overestimates the true cost from a node to the goal.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] astar-consistent-heuristic-definition
A consistent A* heuristic satisfies h(n) ≤ c(n,n′) + h(n′) for every edge (n,n′).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] astar-consistent-implies-admissible
A consistent heuristic is stronger than an admissible heuristic because consistency implies admissibility.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] astar-complexity-exponential
A* has worst-case time and space complexity O(b^d), where b is the branching factor and d is the solution depth.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] amortized-analysis-definition
Amortized analysis bounds the total cost of a worst-case sequence of operations divided by the number of operations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Amortized_analysis.md
- Source URL: https://en.wikipedia.org/wiki/Amortized_analysis
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] amortized-accounting-credit-nonnegative
In the accounting method, the stored credit must remain non-negative at all times.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Amortized_analysis.md
- Source URL: https://en.wikipedia.org/wiki/Amortized_analysis
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-base-address
The base address, also called foundation address or first address, is the memory address of an array's first element.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-indexing-schemes
Arrays may use zero-based indexing (C, Java, Lisp), one-based indexing (FORTRAN 77), or n-based indexing (Pascal, Algol) with an arbitrary start index.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-packed-bit-array
A bit array is a packed array that stores one bit per element, packing eight conditions per octet.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-static-fixed-size
A static array has a fixed size determined at creation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-power-of-two-stride-bit-shift
If an array's stride coefficient is a power of 2, multiplication in the address calculation can be replaced by bit shifting.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-c-2d-declaration-row-major
In C, int a[2][3] declares a 2-row by 3-column array stored row-major as a11, a12, a13, a21, a22, a23.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Array_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Array_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-root-child-minimum
In a B-tree, the root may have as few as 2 children, or be a leaf with 0 children if the tree is very small.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-keys-as-separators
A non-leaf B-tree node with k children contains k−1 keys that partition the key space across its subtrees.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-merge-on-underflow
Deleting from a B-tree node at minimum occupancy triggers a merge with a sibling or redistribution of keys from a neighbor.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-order-2-is-2-3-tree
A B-tree of order 2 is essentially a 2-3 tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-search-binary-search-keys
B-tree search starts at the root and uses binary search among keys at each node to select the correct child pointer.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-delete-internal-key-replacement
When deleting a key from an internal B-tree node, the key is replaced with its in-order predecessor or successor from a leaf before deletion from the leaf.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] btree-file-system-implementations
B-trees are used for directory indexing and metadata management in file systems such as NTFS, HFS+, and ext4 via htree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-B-tree.md
- Source URL: https://en.wikipedia.org/wiki/B-tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] backtracking-term-coined-by-lehmer-1950s
The term 'backtracking' was coined by D. H. Lehmer in the 1950s.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] constraint-propagation-improves-backtracking-efficiency
Constraint propagation can improve backtracking efficiency by reducing the domains of unassigned variables after each assignment.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] backjumping-extends-backtracking
Backjumping extends backtracking by jumping back further than one level when a dead end is found, reducing the search space.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] backtracking-solutions-not-only-leaves
In backtracking, solutions need not be leaves of the search tree; intermediate nodes can also be valid solutions.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] backtracking-variable-trail-timestamps
Variable trail or timestamps are implementation techniques for efficiently undoing assignments during backtracking.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Backtracking.md
- Source URL: https://en.wikipedia.org/wiki/Backtracking
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] big-o-is-bachmann-landau-notation
Big O notation is a member of the Bachmann–Landau family of asymptotic notations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] big-o-o-stands-for-ordnung
The 'O' in Big O notation stands for Ordnung (order of approximation).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] vinogradov-notation-equivalent-to-big-o
Vinogradov notation f ≪ g is equivalent to f = O(g) and is commonly used in number theory.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] big-o-additive-form-definition
The additive form f(x) = h(x) + O(g(x)) means f(x) − h(x) = O(g(x)).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] big-o-example-degree-four-polynomial
For f(x) = 6x⁴ − 2x³ + 5, f(x) = O(x⁴) can be proven with M = 13 for x ≥ 1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Big_O_notation.md
- Source URL: https://en.wikipedia.org/wiki/Big_O_notation
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-search-alternative-names
Binary search is also known as half-interval search, logarithmic search, or binary chop.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-search-deferred-equality-variant
The deferred equality check binary search variant eliminates one comparison per iteration, checks equality only when L = R, uses ceiling instead of floor, and converges to the rightmost match.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-search-rightmost-variant-returns-r-minus-one
The rightmost binary search variant returns R−1, and n − R gives the count of elements greater than the target T.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-search-duplicates-arbitrary-index
For duplicate elements, the standard binary search procedure returns an arbitrary matching index, while specialized variants find the leftmost or rightmost occurrence.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-search-vs-bst-cache-and-insertion-tradeoff
Binary search on a sorted array has better cache locality than BST traversal, but BSTs support O(log n) insertion compared to O(n) insertion for sorted arrays.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] exponential-search-extends-binary-search
Exponential search extends binary search to unbounded lists by first finding a range.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bst-invented-1960
The binary search tree was invented in 1960 and attributed to Windley, Booth, Colin, Hibbard, Berners-Lee, and Wheeler.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bst-costs-bounded-by-height
In a BST, all operations cost O(h) where h is the tree height; balanced trees guarantee h = O(log n).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bst-predecessor-algorithm
The in-order predecessor of a node x in a BST is the maximum of x's left subtree if it exists; otherwise, walk up ancestors until finding the first ancestor where x is in the right subtree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bst-preorder-postorder-traversal-orders
Preorder traversal of a BST visits nodes in node-left-right order; postorder visits nodes in left-right-node order.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] tree-sort-uses-bst-inorder
Tree sort inserts all elements into a BST and then performs an inorder traversal, yielding O(n log n) average and O(n²) worst-case time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-tree-balanced-definition
A balanced binary tree is a binary tree in which the left and right subtrees of every node differ in height by no more than 1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] perfect-binary-tree-is-full
Every perfect binary tree is a full binary tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] perfect-binary-tree-is-complete
Every perfect binary tree is a complete binary tree, but not every complete binary tree is perfect.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] full-binary-tree-height-node-range
A full binary tree of height h has between 2h + 1 and 2^(h+1) - 1 nodes.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] complete-binary-tree-internal-nodes-floor-half
A complete binary tree with n nodes has floor(n/2) internal nodes.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-tree-free-magma
Binary trees can represent elements of a free magma on a singleton set.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Binary_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-generalizes-pigeonhole-sort
Bucket sort generalizes pigeonhole sort by allowing multiple elements per bucket rather than exactly one element per bucket.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-index-formula
Bucket sort computes a bucket index using floor(k * array[i] / M), where k is the number of buckets and M is 1 + the maximum key value.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-stability-depends-on-sub-sort
Bucket sort is not inherently stable or unstable; its stability depends on the sorting algorithm used within each bucket.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-four-phases
Bucket sort proceeds in four phases: initialize buckets, scatter elements into buckets, sort each bucket, and gather buckets in order.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-scatter-back-optimization
An optimization for bucket sort scatters elements back into the original array and then performs a single insertion sort pass, exploiting cache locality and the fact that elements are already close to their final positions.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bucket-sort-not-comparison-sort-pure
Bucket sort is not a comparison sort in its pure form because it uses arithmetic to assign buckets, though it can be implemented with comparisons.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Bucket_sort.md
- Source URL: https://en.wikipedia.org/wiki/Bucket_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-invented-by-harold-seward-1954
Counting sort was invented by Harold H. Seward in 1954.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-requires-nonnegative-integer-keys
Counting sort requires keys to be non-negative integers and works best when the key range k is small relative to n.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-stores-single-count-per-key
Counting sort stores only a single integer count per key value, unlike bucket sort which stores a collection of items per bucket.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-standard-not-in-place
The standard counting sort is not in-place; it requires a separate output array of the same length as the input.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-parallelizes-via-subarray-counts
Counting sort parallelizes by splitting the input into subarrays, computing per-subarray counts, and merging the count arrays, with the prefix sum phase being inherently parallelizable.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] counting-sort-duplicate-elimination-bit-vector
A duplicate-elimination variant of counting sort replaces the count array with a bit vector, where a 1 at position i indicates that key i is present.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Counting_sort.md
- Source URL: https://en.wikipedia.org/wiki/Counting_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-originated-with-tremaux-maze-solving
Depth-first search was originally investigated by Charles Pierre Trémaux in the 19th century as a maze-solving strategy.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-implicit-graph-time-o-b-d
For implicit graphs with branching factor b searched to depth d, DFS time complexity is O(b^d).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-without-visited-set-loops-on-cycles
DFS without a visited set on graphs with cycles can loop forever.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-incomplete-biased-toward-high-degree
Incomplete DFS is biased toward nodes of high degree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-iterative-stack-of-nodes-may-have-duplicates
The iterative stack-of-nodes DFS may have duplicate vertices on the stack, requiring a discovery check when a node is popped.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dfs-applications-include-scc-bridges-planarity
DFS is used as a building block in algorithms for connected components, topological sorting, strongly connected components, bridges, biconnectivity, planarity testing, and maze solving/generation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Depth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Depth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bfs-explored-before-enqueue
BFS maintains an explored-before-enqueue invariant, marking a vertex as explored before or when it is enqueued to prevent duplicate entries in the queue.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bfs-parent-pointers-reconstruct-path
BFS uses parent pointers to reconstruct the shortest path from the source to a target vertex.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bfs-standard-pseudocode-components
Standard BFS pseudocode uses a queue, an explored set, and parent pointers.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Breadth-first_search.md
- Source URL: https://en.wikipedia.org/wiki/Breadth-first_search
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dijkstra-relaxation-operation
Dijkstra's algorithm uses a relaxation operation to update tentative distances of neighboring vertices.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dijkstra27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dijkstra-early-termination-for-single-target
For a single-target query, Dijkstra's algorithm can terminate early once the target vertex is extracted from the priority queue.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dijkstra27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dijkstra-correctness-proof-by-induction
Dijkstra's algorithm's correctness is proved by induction.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dijkstra27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] union-find-register-allocation-application
Union-find is used in register allocation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] union-find-dynamic-connectivity-application
Union-find supports dynamic connectivity queries.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] union-find-persistent-variants
Persistent variants of the union-find data structure have been developed.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Disjoint-set_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dnc-complexity-p-subproblems-linear-overhead
For p sub-problems each of size n/p with O(n) divide/combine overhead, the divide-and-conquer recurrence solves to O(n log_p n).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dnc-complexity-q-subproblems-half-size
For q > 2 sub-problems each of size n/2 with O(n) overhead, the divide-and-conquer recurrence solves to O(n^(log_2 q)).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dnc-single-subproblem-linear-overhead-complexity
A divide-and-conquer recurrence with one sub-problem of size n/2 and O(n) overhead solves to O(n).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dnc-two-half-subproblems-quadratic-overhead
With two sub-problems of size n/2 and O(n²) combine overhead, the divide-and-conquer recurrence solves to O(n²).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] akra-bazzi-generalizes-master-theorem
The Akra-Bazzi method generalizes the Master Theorem for more complex divide-and-conquer recurrences.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] pairwise-summation-improves-numerical-accuracy
Pairwise summation using divide and conquer reduces floating-point error accumulation compared with naive iterative summation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-recursion-depth-logarithmic-with-smaller-partition-first
Quicksort's recursion depth can be limited to O(log n) by always recursing on the smaller partition first.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dnc-arms-length-recursion-short-circuits-base-case
Arm's-length recursion checks whether the next recursive call will hit a base case before making the call, avoiding unnecessary function invocations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Divide-and-conquer_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dp-automatic-memoization-requires-referential-transparency
Automatic memoization in dynamic programming requires referential transparency.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hamilton-jacobi-bellman-extends-dp-to-continuous-control
The Hamilton-Jacobi-Bellman equation extends dynamic programming to continuous control theory.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dp-backtracking-no-subproblem-reuse
Backtracking does not reuse subproblem solutions, whereas dynamic programming stores and reuses them.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Dynamic_programming.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_programming
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] fenwick-lsb-bit-trick-index-navigation
Fenwick tree operations use the least significant set bit (LSB) of an index to navigate the implicit tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Fenwick_tree.md
- Source URL: https://en.wikipedia.org/wiki/Fenwick_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] fenwick-linear-time-construction
A Fenwick tree can be built in O(n) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Fenwick_tree.md
- Source URL: https://en.wikipedia.org/wiki/Fenwick_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] fenwick-node-stores-range-sum-by-lsb
Each Fenwick tree node stores the sum of a range of elements whose length is determined by the least significant bit of the node index.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Fenwick_tree.md
- Source URL: https://en.wikipedia.org/wiki/Fenwick_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] floyd-warshall-generalizes-widest-paths
Floyd-Warshall generalizes to widest (maximum bottleneck) path problems by using a different semiring (replacing min/+ with max/min operations).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-FloydE28093Warshall_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-adt-definition
A graph consists of a finite set of vertices and a set of edges (unordered pairs for undirected graphs, ordered pairs for directed graphs).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-three-canonical-representations
The three canonical graph representations are adjacency list, adjacency matrix, and incidence matrix.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-sparse-dense-definition
A graph is sparse when |E| << |V|² and dense when |E| ≈ |V|².
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] add-edge-o1-adj-list-matrix
Adding an edge costs O(1) for both adjacency list and adjacency matrix representations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] remove-edge-complexity-adj-list-vs-matrix
Removing an edge costs O(|V|) for an adjacency list but O(1) for an adjacency matrix.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] remove-vertex-complexity-adj-list-vs-matrix
Removing a vertex costs O(|E|) for an adjacency list and O(|V|²) for an adjacency matrix.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-adt-operations
The graph ADT supports operations including adjacent, neighbors, add_vertex, remove_vertex, add_edge, remove_edge, get_vertex_value, set_vertex_value, get_edge_value, and set_edge_value.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] shared-vs-distributed-memory-graph-representation
Shared memory parallel graph algorithms can reuse sequential representations, while distributed memory requires explicit graph partitioning.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] euler-formula-planar-graphs
Euler's formula for connected planar graphs states V - E + F = 2, where V is vertices, E is edges, and F is faces.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mantel-theorem-triangle-free
Mantel's theorem states that the maximum number of edges in a triangle-free graph on n vertices is floor(n²/4).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] turan-theorem-generalization
Turán's theorem generalizes Mantel's theorem by giving the maximum number of edges in a graph avoiding a complete subgraph K_r.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] erdos-renyi-random-graph-theory
Random graph theory was initiated by Erdős and Rényi studying asymptotic graph connectivity.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] spectral-graph-theory-definition
Spectral graph theory studies the eigenvalues and eigenvectors of the adjacency matrix and Laplacian matrix.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] chromatic-polynomial-definition
The chromatic polynomial P(G, k) counts the number of proper k-colorings of a graph G.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] tutte-polynomial-definition
The Tutte polynomial is a two-variable polynomial that encodes connectivity properties of a graph.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-minor-definition
A graph minor is formed from a graph by deleting vertices and/or edges and contracting edges.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Graph_theory.md
- Source URL: https://en.wikipedia.org/wiki/Graph_theory
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] greedy-local-optima-failure
Greedy algorithms can get stuck at local optima and miss global optima, as in the hill-climbing trap.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] greedy-no-complete-characterization
There is no complete characterization of when a problem admits a greedy solution.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] activity-selection-greedy-algorithm
The activity selection problem is solved exactly by a greedy algorithm that sorts tasks by end time and repeatedly selects the first task that starts after the last selected task ends.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] zeckendorf-greedy-representation
Zeckendorf representation is produced by repeatedly subtracting the largest Fibonacci number less than or equal to the remaining value, yielding a unique non-consecutive Fibonacci sum.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] greedy-01-knapsack-half-approximation
Greedy on the fractional relaxation of 0-1 knapsack yields a solution with at least 1/2 of the optimal value.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] greedy-submodular-half-approximation
Greedy algorithms for submodular maximization provide a ≥ 1/2 approximation guarantee.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Greedy_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Greedy_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-table-definition
A hash table (hash map, dictionary) is a data structure that implements an associative array by using a hash function to map keys to array indices.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-table-invented-1953
The hash table was invented in 1953 by Hans Peter Luhn at IBM.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-table-space-complexity
Hash table space complexity is Θ(n) on average and O(n) in the worst case.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-collision-definition
A hash collision occurs when a hash function maps two or more distinct keys to the same index.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-division-method
The division method for hashing computes h(x) = x mod m, with prime m often preferred.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hash-multiplication-method
The multiplication method computes h(x) = floor(m * ((x * A) mod 1)) with A a non-integer constant; Knuth suggests the golden ratio for A.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] separate-chaining-bst-worst-case
Using a self-balancing BST instead of a linked list for separate chaining reduces the worst-case per-bucket lookup from O(n) to O(log n).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] cuckoo-hashing-worst-case-o1
Cuckoo hashing is an open addressing variant that uses two hash functions to achieve worst-case O(1) lookup.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] heap-implements-priority-queue-adt
A heap is the canonical implementation of the priority queue ADT.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] heap-introduced-williams-1964
The heap data structure was introduced by J. W. J. Williams in 1964 alongside heapsort.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] binary-heap-complete-tree-height
A binary heap is a complete binary tree, giving it the smallest possible height O(log n).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] heap-find-max-o1-regardless-variant
For all heap variants listed, find-max (peek) returns the root element in O(1) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] heap-merge-vs-meld-preserves-originals
Merge/union joins two heaps while preserving the originals, whereas meld joins two heaps and destroys the originals.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] pairing-heap-amortized-bounds
Pairing heaps provide Θ(1) find-max, Θ(1) insert, Θ(1) meld, O(log n) amortized delete-max, and o(log n) amortized increase-key.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heap_data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Heap_(data_structure)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] floyd-heapify-exact-comparisons
Floyd's bottom-up heapify has exact worst-case comparison count 2n - 2s₂(n) - e₂(n), where s₂ is popcount and e₂ is trailing zero count.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] williams-heapify-topup-nlogn
Williams' top-up heapify appends elements one at a time using siftUp and has O(n log n) worst-case time; practical implementations use Floyd's bottom-up version.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bottom-up-heapsort-reduces-comparisons
Bottom-up heapsort reduces average comparisons from 2n log₂ n to n log₂ n by searching down to a leaf then sifting up.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] weak-heapsort-extra-bit
Weak heapsort uses one extra bit per node to achieve n log₂ n + O(n) comparisons.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] smoothsort-nearly-sorted-linear
Smoothsort, a heapsort variant by Dijkstra, approaches O(n) time on nearly-sorted input.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] heapsort-is-heap-based-selection-sort
Heapsort is conceptually a selection sort that uses a heap to efficiently find the maximum.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Heapsort.md
- Source URL: https://en.wikipedia.org/wiki/Heapsort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] centered-interval-tree-point-query-logic
In a centered interval tree point query, if x < center report S_center intervals with start ≤ x and recurse left; if x > center report S_center intervals with end ≥ x and recurse right; if x == center report all S_center intervals.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] interval-tree-interval-query-procedure
Interval-interval query uses a separate search tree of endpoints to find intervals with endpoints inside the query, then a point query to find intervals enclosing the query, then deduplicates with a binary flag per interval.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] augmented-tree-max-high-maintenance
Augmented interval tree insert/delete updates max_high bottom-up along ancestors in O(h) per operation and must also update on tree rotations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] interval-tree-small-integer-range-o1
When interval endpoints fall in [1,...,O(n)], optimal interval structures exist with O(n) preprocessing and O(1 + m) query time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] centered-interval-tree-deletion-cascades
Deletion in a centered interval tree is more complex than standard BST deletion because promoted nodes may need to absorb intervals from former ancestors, potentially cascading further deletions.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] centered-interval-tree-rotation-invariant
Centered interval tree deletion and rotation must preserve the invariant that each interval is stored at the node closest to the root among all nodes whose center point it overlaps.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dual-sorted-interval-trees-merge-linear
A naive dual-tree interval query using two trees sorted by start and end still requires O(n) to merge results, giving no asymptotic improvement over brute force.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Interval_tree.md
- Source URL: https://en.wikipedia.org/wiki/Interval_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] maximum-subarray-problem-definition
The maximum subarray problem asks, given array A[1...n], for indices i ≤ j maximizing A[i]+...+A[j].
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] max-subarray-trivial-cases
For maximum subarray, all non-negative numbers make the entire array optimal; all non-positive numbers make the single element closest to zero optimal (or empty subarray if permitted).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] max-subarray-multiple-optima
Multiple subarrays may share the same maximum sum.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kadane-example-sum-6
For array [-2,1,-3,4,-1,2,1,-5,4], the maximum subarray is [4,-1,2,1] with sum 6.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] shamos-divide-conquer-crossing-subarray
Shamos's O(n log n) maximum subarray algorithm splits the array, solves each half recursively, and combines by finding the best crossing subarray.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] k-largest-subarray-sums-linear
Finding the k largest subarray sums in a one-dimensional array is solvable in optimal O(n+k) time (Brodal & Jorgensen, 2007).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] k-disjoint-subarrays-linear
Maximum sum of k non-overlapping subarrays is solvable in O(n+k) time (Bengtsson & Chen, 2007).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kadane27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-problem-statement
The knapsack problem: given n items each with weight w_i and value v_i and capacity W, select a subset maximizing total value subject to total weight ≤ W.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-optimization-verification-co-np-complete
In the optimization version of knapsack, verifying that a proposed solution is optimal is co-NP-complete.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-top-down-memoized-runtime-range
Top-down memoized 0-1 knapsack runs in time between O(nW) and O(2^n) depending on which subproblems are visited.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-gcd-weight-optimization
Dividing all weights and the capacity W by their greatest common divisor reduces the DP table size and improves running time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-survey-rank-1999
In a 1999 Stony Brook survey of 75 combinatorial algorithm problems, knapsack ranked 19th most popular and 3rd most needed.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] knapsack-decision-optimization-equivalence
A polynomial-time algorithm for the knapsack decision version implies a polynomial-time algorithm for the optimization version, and vice versa.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] subset-sum-linear-decision-tree-bounds
For subset sum in the linear decision tree model, the lower bound is (1/2)n² (Dobkin-Lipton) and the upper bound is O(n⁴) (Meyer auf der Heide).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Knapsack_problem.md
- Source URL: https://en.wikipedia.org/wiki/Knapsack_problem
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kruskal-published-1956
Kruskal's algorithm was first published by Joseph Kruskal in 1956.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kruskal-cycle-detection-condition
In Kruskal's algorithm, an edge {u, v} creates a cycle if and only if FIND-SET(u) equals FIND-SET(v).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] filter-kruskal-threshold-fallback
Filter-Kruskal falls back to standard Kruskal when the number of edges is below a threshold called kruskal_threshold.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] reverse-delete-starts-all-edges
The reverse-delete MST algorithm starts with all edges and repeatedly removes the heaviest edge that does not disconnect the graph.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] boruvka-simultaneous-cheapest-edge
Boruvka's algorithm has each component select its cheapest outgoing edge simultaneously, making it naturally parallelizable.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kruskal-tie-breaking-arbitrary
Ties in edge weights can be broken arbitrarily in Kruskal's algorithm without affecting correctness.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kruskal-produces-single-linkage-dendrogram
Kruskal's algorithm directly produces a single-linkage hierarchical clustering dendrogram.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Kruskal27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] linked-list-node-structure
A linked list node contains a data or payload field and one or more link or pointer fields to other nodes.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] linked-list-head-provides-access
The head is the first node in a linked list and provides access to the entire structure.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] multiply-linked-list-multiple-orderings
A multiply linked list has nodes with two or more link fields that connect the same data in different orderings, such as by name and by date.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] linked-list-cycle-detection-floyd
Floyd's cycle detection algorithm uses two pointers moving at different speeds; if they meet, the linked list contains a cycle.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] cdr-coding-inline-data
CDR coding is an optimization for linked lists that replaces pointers with inline data to reduce pointer overhead.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] unrolled-linked-list-multiple-elements
An unrolled linked list stores multiple elements per node, improving cache performance and reducing pointer overhead compared with a standard linked list.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] os-process-thread-lists-doubly-linked
Operating systems use doubly linked lists to maintain active process and thread lists.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] linked-list-created-ipl-1955
Linked lists were created by Newell, Shaw, and Simon in 1955-56 for IPL.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Linked_list.md
- Source URL: https://en.wikipedia.org/wiki/Linked_list
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] algorithm-catalog-organized-by-domain
The List of Algorithms reference taxonomy organizes algorithms by problem domain rather than by technique, so the same method can appear under multiple categories.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] graph-algorithms-subdomains
Graph algorithms subdivide into matching, coloring, drawing, network flow, routing, search/traversal, and subgraph problems.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sorting-algorithms-classified-by-mechanism
Sorting algorithms are classified by mechanism into exchange sorts, insertion sorts, merge sorts, selection sorts, non-comparison sorts, and hybrid sorts.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] ford-fulkerson-max-flow-framework
Ford-Fulkerson is the framework for maximum flow algorithms.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] edmonds-karp-bfs-polynomial
Edmonds-Karp is the breadth-first-search implementation of Ford-Fulkerson that guarantees polynomial time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dinic-strongly-polynomial
Dinic's maximum flow algorithm is strongly polynomial.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] gale-shapley-stable-matching
The Gale-Shapley algorithm solves the stable matching problem.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] scc-tarjan-kosaraju-linear
Tarjan's and Kosaraju's algorithms both find strongly connected components in linear time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/List_of_algorithms
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] primitive-types-list
Primitive types in the taxonomy include Boolean, Character, Integer, Floating-point (IEEE 754 single/double precision), Fixed-point, Reference, Symbol, Enumerated type, and Complex.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] composite-types-list
Composite types include Array (contiguous same-type), Record/Struct (named fields), Tuple/Product type (unnamed fields), String, Union, and Tagged union.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] core-adts-list
Core abstract data types include List, Stack, Queue, Deque, Set, Multiset, Map, Multimap, Graph, Tree, and Heap.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] linear-structures-array-linked-list-families
Linear data structures have elements forming a sequence, with arrays and linked lists as the two fundamental families.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] self-balancing-bst-variants-list
Self-balancing binary search trees such as AVL, Red-black, Splay, Treap, Scapegoat, AA, WAVL, and Zip maintain O(log n) operations by rebalancing on mutation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] probabilistic-hash-structures-list
Probabilistic hash-based data structures include Bloom filters, Cuckoo filters, Count-min sketches, and MinHash.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] space-partitioning-trees-list
Space-partitioning trees such as k-d trees, quadtrees, octrees, R-trees, and BSP trees organize multi-dimensional spatial data.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] two-three-four-tree-isomorphic-red-black
A 2-3-4 tree is isomorphic to a red-black tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-List_of_data_structures.md
- Source URL: https://en.wikipedia.org/wiki/List_of_data_structures
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] lcs-finds-common-subsequence-all-sequences
The longest common subsequence problem finds the longest subsequence present in all sequences from a given set.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] lcs-example-abcd-acbad
For the sequences (ABCD) and (ACBAD), both (ABD) and (ACD) are longest common subsequences of length 3.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] lcs-base-case-empty
In the LCS dynamic programming recurrence, if either sequence is empty, the LCS is the empty string.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] lcs-generalizes-sequence-alignment
LCS generalizes to sequence alignment scoring in DNA and protein sequence comparison in bioinformatics.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] lcs-strip-matching-prefix-suffix
A practical LCS optimization strips matching prefixes and suffixes before building the dynamic programming table.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Longest_common_subsequence.md
- Source URL: https://en.wikipedia.org/wiki/Longest_common_subsequence
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-definition-caches-pure-function-results
Memoization is an optimization technique that stores the results of expensive pure function calls and returns the cached result when the same inputs recur.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-coined-by-donald-michie-1968
The term memoization was coined by Donald Michie in 1968.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoized-cache-populated-on-the-fly
A memoized function populates its cache on the fly as new inputs are encountered, unlike a precomputed lookup table.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-space-time-tradeoff
Memoization trades increased memory usage for reduced computation time, typically using a hash table.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-cache-keyed-by-arguments
Memoized results are keyed by the function's input arguments in an associative array or hash map.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-cache-replacement-fixed-or-unbounded
A memoization cache may be fixed-size with a replacement algorithm or unbounded, depending on the use case.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-called-tabling-in-logic-programming
In logic programming languages, memoization is called tabling.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] memoization-singleton-pattern-degenerate-case
Creating an object on first call and returning the cached instance thereafter is a degenerate form of memoization.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Memoization.md
- Source URL: https://en.wikipedia.org/wiki/Memoization
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-invented-by-john-von-neumann-1945
Merge sort was invented by John von Neumann in 1945.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-is-comparison-based-divide-and-conquer
Merge sort is an efficient, general-purpose, comparison-based sorting algorithm that uses the divide-and-conquer strategy.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-has-top-down-and-bottom-up-implementations
Merge sort has top-down recursive and bottom-up iterative implementations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-bottom-up-starts-runs-size-1
Bottom-up merge sort starts with runs of size 1 and doubles the run width each pass.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-sequential-access-advantage
Merge sort is more efficient than quicksort when data can only be accessed sequentially, such as linked lists or tapes.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-worst-case-comparison-formula
The exact worst-case comparison count for merge sort is n⌈lg n⌉ − 2^⌈lg n⌉ + 1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] tiled-mergesort-uses-insertion-sort-for-cache-subarrays
Tiled merge sort uses insertion sort for subarrays that fit in cache, then standard merge sort above that level.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] mergesort-space-reduction-copies-left-half
Merge sort's auxiliary space can be reduced to n/2 by copying only the left half to temporary space and merging in-place into the original array.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Merge_sort.md
- Source URL: https://en.wikipedia.org/wiki/Merge_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-origin-jarnik-1930-prim-1957-dijkstra-1959
Prim's algorithm was developed by Vojtěch Jarník in 1930 and independently rediscovered by Robert C. Prim in 1957 and Edsger W. Dijkstra in 1959.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-output-forest-by-running-per-component
For disconnected graphs, running Prim's algorithm separately on each connected component finds the minimum spanning forest.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-main-loop-sequential-inner-loop-parallelizable
Prim's main loop is inherently sequential, but its inner loop for finding the minimum-weight crossing edge can be parallelized.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-starting-vertex-does-not-affect-total-weight
The starting vertex in Prim's algorithm is arbitrary and does not affect the total MST weight, though it may produce a different MST when ties exist.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-exchange-argument-proves-correctness
Prim's correctness can be proved by an exchange argument: the first differing edge can replace an edge in some MST without increasing total weight.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-greedoid-framework-explains-optimality
The matroid/greedoid framework provides the theoretical foundation explaining why Prim's greedy choices yield a globally optimal MST.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-dary-heap-dense-linear-condition
Prim's algorithm achieves linear time on dense graphs using a d-ary heap when |E| ≥ |V|^c for c > 1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] prim-kruskal-boruvka-equivalent-asymptotic-on-sparse
Prim's, Kruskal's, and Borůvka's algorithms have equivalent asymptotic complexity on sparse graphs.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Prim27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Prim%27s_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] priority-queue-has-min-and-max-variants
Priority queues have min-priority and max-priority variants.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] priority-queue-used-in-huffman-astar-event-simulation
Priority queues are used in Huffman coding, A* search, and discrete event simulation.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] priority-queue-stdlib-classes-vary-across-languages
Standard library priority queue classes across seven languages differ in default ordering and backing data structure.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] integer-key-priority-queue-specializations
Priority queues with integer keys can be specialized using bucket queues or van Emde Boas trees.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Priority_queue.md
- Source URL: https://en.wikipedia.org/wiki/Priority_queue
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] queue-fifo-definition
A queue is an abstract data type that maintains an ordered collection of elements following First-In-First-Out (FIFO) order.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] queue-enqueue-dequeue-o1
Queue enqueue and dequeue operations both run in O(1) time.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] queue-search-on
Searching a queue takes O(n) time because elements must be traversed without indexing.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bounded-queue-overflow-underflow
In a bounded queue, enqueueing beyond capacity causes overflow, and dequeuing from an empty queue causes underflow.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] queue-is-restricted-deque
A queue can be viewed as a restricted double-ended queue (deque).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] singly-linked-list-queue-requires-tail-pointer
An efficient queue implementation using a singly linked list needs a tail pointer in addition to a head pointer.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] java-queue-interface-since-j2se5
Java's Queue interface has existed since J2SE 5.0 and is implemented by LinkedList and ArrayDeque.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Queue_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-hoare-return-j-floor-pivot
In Hoare's partition scheme, the partition function must return j (not i) and use a floor-based pivot to avoid infinite recursion.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-hoare-pivot-final-location
In Hoare's partition scheme, the pivot's final location is not necessarily at the index returned by the partition function.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-partition-recursion-bounds
Lomuto partition recurses on (lo..p-1) and (p+1..hi) excluding the pivot, while Hoare partition recurses on (lo..p) and (p+1..hi) including the pivot in the left half.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-insertion-sort-fallback-threshold
Practical quicksort implementations switch to insertion sort for subarrays below a threshold of about 10 elements.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-midpoint-overflow-avoidance
Computing (lo + hi) / 2 can overflow, so quicksort implementations should use lo + (hi - lo) / 2 instead.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-ninther-pivot-selection
The ninther pivot selection method uses the median of three medians-of-three and is used for larger arrays.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] quicksort-three-way-partition-two-indices
Three-way partition returns two indices bounding the equal-to-pivot region and recurses on (lo..lt-1) and (gt+1..hi).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Quicksort.md
- Source URL: https://en.wikipedia.org/wiki/Quicksort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-history-hollerith-1887
Radix sort dates back to Herman Hollerith's 1887 tabulating machines.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-msd-naturally-parallelizable
MSD radix sort is naturally parallelizable because each bucket can be sorted on a separate processor.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-signed-integers-sign-bit
For two's complement signed integers, radix sort must treat the most significant (sign) bit with opposite sense, inverting comparison on the sign bit.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-single-pass-digit-counting
Counting all digit frequencies in a single pass reduces radix sort's total passes from Θ(2d(n+k)) to Θ((d+1)(n+k)).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-msd-insertion-sort-hybrid
Hybrid MSD radix sort switches to insertion sort for small buckets to reduce constant-factor overhead.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-radix-base-definition
In radix sort, the radix is the base of the number system used for digit extraction, such as base-10 or base-256 for byte-level processing.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] radix-sort-applicability-lexicographic-data
Radix sort applies to any lexicographically sortable data, including integers, strings, punch cards, and mail.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Radix_sort.md
- Source URL: https://en.wikipedia.org/wiki/Radix_sort
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-base-case-required
A recursive function requires a base case that returns a direct result without further recursion; omitting it causes infinite recursion or stack overflow.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-direct-and-indirect
Direct recursion occurs when a function calls itself; indirect (mutual) recursion occurs when function f calls function g, which calls f again, possibly through chains of three or more functions.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-generative-examples
Generative recursion generates new data from the input and recurses on it, with examples including quicksort, binary search, mergesort, Newton's method, and GCD.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-tail-call-optimization
Tail call optimization reuses stack frames when the recursive call is the last operation, improving recursive performance.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-wrapper-function-pattern
The wrapper function pattern validates parameters, initializes state, and delegates to a private recursive auxiliary function, often also setting up memoization.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] recursion-recursive-data-types-inductive-coinductive
Recursive data types are self-referential data definitions such as linked lists, natural numbers, and BNF grammars; inductive definitions specify how to construct instances, while coinductive definitions specify operations on possibly infinite structures.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Recursion_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Recursion_(computer_science)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] redblack-definition-self-balancing-bst-color-bit
A red-black tree is a self-balancing binary search tree where each node stores an extra color bit (red or black) and coloring constraints ensure the tree remains approximately balanced.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] redblack-read-operations-identical-bst
Red-black tree read-only operations such as search and traversal are identical to standard binary search tree operations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] redblack-single-child-must-be-red
In a red-black tree, a node with exactly one child must have that child be red.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] redblack-llrb-left-leaning
LLRB (left-leaning red-black tree) is Sedgewick's 2008 simplification of red-black trees in which red links lean left only.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] redblack-root-black-rule-nonessential
The red-black tree rule that the root must be black is non-essential because a red root can always be recolored.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-RedE28093black_tree.md
- Source URL: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] segtree-definition-stabbing-queries
A segment tree is a classical data structure that stores intervals and solves stabbing queries.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Segment_tree.md
- Source URL: https://en.wikipedia.org/wiki/Segment_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] segtree-elementary-intervals-4n-plus-1
A segment tree partitions the real line into up to 4n+1 elementary intervals.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Segment_tree.md
- Source URL: https://en.wikipedia.org/wiki/Segment_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] segtree-complexity-build-query
A segment tree has O(n log n) build time and storage, and answers queries in O(log n + k) time where k is the number of reported intervals.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Segment_tree.md
- Source URL: https://en.wikipedia.org/wiki/Segment_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] segtree-higher-dimensions-fractional-cascading
Segment trees generalize to higher dimensions with multi-level structures, and fractional cascading can optimize them.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Segment_tree.md
- Source URL: https://en.wikipedia.org/wiki/Segment_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] segtree-history-bentley-1977
The segment tree was invented by Bentley in 1977.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Segment_tree.md
- Source URL: https://en.wikipedia.org/wiki/Segment_tree
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] static-sets-immutable-dynamic-sets-mutable
Static (frozen) sets are immutable after construction and support only query operations such as membership testing and enumeration; dynamic (mutable) sets additionally support insertion and deletion.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] multiset-allows-duplicate-elements
A multiset (bag) is a generalization of a set that allows duplicate elements and tracks element multiplicity.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] set-core-operations-union-intersection-difference-subset
Core set-theoretic operations include union(S,T), intersection(S,T), difference(S,T), and subset(S,T).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sql-distinct-converts-multiset-to-set
In SQL, SELECT DISTINCT converts a multiset query result into a set.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] naive-list-set-membership-deletion-on
A naive list-based set implementation has O(n) membership and deletion, and insertion is O(1) only if duplicates are not checked.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sorted-list-set-union-linear-merge
Union of two sorted-list set implementations can be performed in O(m+n) using a merge, compared with O(m×n) for the naive approach.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] multiset-counter-associative-array-counts
A multiset can be implemented as an associative array mapping values to counts, as in Python's collections.Counter.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Set_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Set_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sliding-window-protocol-flow-control-reliable-delivery
The sliding window protocol is a flow-control and reliable-delivery mechanism for packet-based data transmission that lets a sender transmit multiple packets before requiring acknowledgment.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sliding-window-operates-at-data-link-and-transport-layers
Sliding windows operate at the data link layer (OSI layer 2) and the transport layer (TCP).
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sliding-window-slides-forward-on-ack
In a sliding window protocol, the window slides forward as acknowledgments arrive.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sliding-window-variable-invariant-na-nr-ns-nt
Sliding window state variables satisfy the invariant na <= nr <= ns <= nt <= na + wt, where nt is next to transmit, nr is first not received, ns is one past greatest received, na is greatest acknowledgment, and wt is the sender window.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] tcp-ack-cumulative-nr
TCP acknowledgments carry nr as a cumulative ACK of all packets below that sequence number, though selective ACK (SACK) extends this.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] hdlc-uses-3-bit-sequence-numbers
HDLC uses a 3-bit sequence number (N=8); with Go-Back-N wt <= 7, and with Selective Repeat and wr=2 wt <= 6.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] sorting-output-monotonic-permutation
A correct sorting algorithm must produce output that is monotonically ordered and is a permutation of the input.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] in-place-sort-requires-o1-extra-memory
An in-place sort strictly requires only O(1) extra memory, although O(log n) extra memory is sometimes considered in-place.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] smoothsort-adaptive-linear-sorted-input
Smoothsort is an adaptive sort that achieves O(n) time on already-sorted data.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] insertion-sort-online-processing
Insertion sort can process input online as it arrives without needing the full dataset upfront.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] selection-sort-n-minus-one-swaps
Selection sort makes exactly n−1 swaps, which is optimal for expensive writes, but is O(n^2) in all cases.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] timsort-hybrid-merge-insertion
Timsort is a hybrid of merge sort and insertion sort.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Sorting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Sorting_algorithm
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] dynamic-array-stack-amortized-o1
A dynamic-array-based stack provides amortized O(1) push and pop as it grows and shrinks.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] stack-hardware-duplicate-swap-rotate
Some hardware stack architectures provide additional operations such as Duplicate, Swap/Exchange, and Rotate/Roll.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] cisc-has-stack-instructions-risc-generally-lacks
CISC processors such as x86, Z80, and 68000 typically have dedicated stack pointer registers and push/pop instructions, while RISC processors generally do not.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] stack-machines-use-implicit-top-of-stack-operands
Stack machines use the implicit top of stack as operands for arithmetic and logic operations.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] stack-oriented-languages-forth-postscript
Forth and PostScript are stack-oriented languages that operate directly on language-visible stacks.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Stack_abstract_data_type.md
- Source URL: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] topological-sort-linear-ordering-definition
A topological sort of a DAG produces a linear ordering of vertices such that for every directed edge (u, v), u appears before v.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] topological-sort-equivalent-linear-extension-partial-order
A topological ordering of a DAG is equivalent to a linear extension of the partial order defined by reachability in the DAG.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] topological-sort-works-disconnected-dags
Topological sorting works for DAGs with disconnected components.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] kahn-s-data-structure-choice-determines-ordering
In Kahn's algorithm, using a set, queue, or stack for the zero-indegree collection determines which valid topological ordering is produced but does not affect correctness.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] topological-sort-parallel-nc2
Topological ordering is in NC2; it can be constructed in O((log n)^2) time with polynomial processors on a PRAM.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] critical-path-method-uses-topological-sort
The Critical Path Method (CPM/PERT) uses topological sort as the basis for finding critical paths in project scheduling.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Topological_sorting.md
- Source URL: https://en.wikipedia.org/wiki/Topological_sorting
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] tree-traversal-visits-each-node-exactly-once
Tree traversal is a form of graph traversal that visits each node in a tree data structure exactly once.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] preorder-topological-parent-before-children
Pre-order (NLR) traversal produces a topologically sorted sequence in which every parent node appears before its children.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] iterative-preorder-pushes-right-before-left
Iterative pre-order DFS pushes the right child onto the stack before the left child so that the left child is processed first.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] array-stored-tree-levelorder-is-index-iteration
For a tree stored in an array, level-order traversal is simply iterating array indices 0 through size-1.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] iterative-deepening-dfs-combines-dfs-space-and-bfs-completeness
Iterative deepening DFS combines DFS space efficiency with BFS completeness and is relevant for infinite or very large trees.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] bfs-fails-infinite-branching-dfs-fails-infinite-depth
BFS traversal fails on trees with infinite branching, and DFS traversal fails on trees with infinite depth.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] diagonal-traversal-covers-countably-infinite-trees
Hybrid diagonal traversal methods can traverse any countably infinite tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] iterative-postorder-tracks-last-node-visited
Iterative post-order DFS requires tracking the lastNodeVisited node.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] inorder-next-amortized-o1
Sequential in-order traversal via inorderNext runs in O(1) amortized time per step, with a full traversal taking 2n-2 steps and worst-case O(h) per step.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Tree_traversal.md
- Source URL: https://en.wikipedia.org/wiki/Tree_traversal
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-also-called-digital-or-prefix-tree
A trie is also called a digital tree or prefix tree.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-node-has-alphabet-size-child-pointers
Each trie node contains up to |alphabet| child pointers (e.g., 128 for ASCII), most of which are typically null.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-space-complexity-average-o-n-worst-o-w-n
Trie space complexity is O(n) on average and O(w·n) in the worst case, where w is alphabet width and n is the number of keys or characters stored.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-naive-wastes-space-on-sparse-alphabets
Naive trie implementations waste space on sparse alphabets because each node stores |alphabet| pointers, though tries are space-efficient for large numbers of short strings with common prefixes.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-alphabet-reduction-trades-depth-for-space
Alphabet reduction, such as splitting bytes into nibbles, trades 2x traversal depth for 8x space reduction in a trie.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-bitmap-replaces-pointer-array
The bitmap technique stores a 256-bit bitmap instead of 256 pointers per trie node to reduce memory.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-applications-autocomplete-spellcheck-ip-bioinformatics-web-indexing
Tries are used in autocomplete, spell checking, IP routing for longest prefix match, bioinformatics k-mer indexing in BLAST, and web search engine indexing.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

### [ACCEPT] trie-left-child-right-sibling-representation
A left-child right-sibling tree is an alternative trie representation that trades pointer-array space for linked-list traversal cost.
- Source: /home/forge/workspace/entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie
- Model: openai:rits/deepseek-ai/DeepSeek-V4.1-Flash-1017

