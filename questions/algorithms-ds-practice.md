# Algorithms & Data Structures Practice Exam

## Q1: What is the time complexity of accessing an element by index in an array?
Answer: O(1)

## Q2: What happens when a hash table's load factor exceeds a threshold?
Answer: The table is rehashed (resized and all elements reinserted), which is amortized O(1) per insertion.

## Q3: Why can't a hash table efficiently support ordered operations like finding the minimum or successor?
Answer: Hash tables distribute keys by hash value, destroying key ordering. Ordered operations require a sorted structure like a BST.

## Q4: What is the time complexity of accessing the k-th element in a singly linked list?
Answer: O(n), because you must traverse from the head.

## Q5: What is the purpose of a sentinel node in a linked list?
Answer: It eliminates special-case handling for empty lists and boundary conditions by providing a dummy node that is always present.

## Q6: What is an XOR linked list?
Answer: A doubly linked list that stores the XOR of the previous and next pointers in a single field, halving pointer storage at the cost of requiring both neighbors for traversal.

## Q7: How can you implement a queue using two stacks with amortized O(1) per operation?
Answer: Use an inbox stack for enqueue and an outbox stack for dequeue. When the outbox is empty, reverse the inbox into it. Each element is moved at most twice, giving amortized O(1).

## Q8: What data structure does DFS use and what does BFS use?
Answer: DFS uses a stack (or recursion call stack), BFS uses a queue.

## Q9: In a binary tree stored as an array, what are the formulas for the left child, right child, and parent of node at index i?
Answer: Left child: 2i+1, Right child: 2i+2, Parent: floor((i-1)/2).

## Q10: What is the relationship between the number of leaves and the number of degree-2 nodes in a binary tree?
Answer: The number of leaves equals the number of degree-2 (internal) nodes plus one.

## Q11: How does an AVL tree differ from a red-black tree in terms of balance strictness?
Answer: AVL trees maintain stricter balance (height difference of at most 1 between subtrees) giving faster lookups, while red-black trees allow looser balance (no path more than twice as long as any other) giving faster insertions and deletions with fewer rotations.

## Q12: What is the 2-3-4 tree isomorphism of a red-black tree?
Answer: Every red-black tree corresponds to a 2-3-4 tree: a black node with no red children is a 2-node, with one red child is a 3-node, and with two red children is a 4-node.

## Q13: Why are B-trees preferred for disk-based storage over binary search trees?
Answer: B-trees have high branching factor, so tree height is small and each node corresponds to a disk page. This minimizes disk I/O operations, which are the bottleneck for on-disk data.

## Q14: What is the time complexity of building a binary heap from an unsorted array using Floyd's algorithm?
Answer: O(n), because most nodes are near the bottom and sift down a small distance.

## Q15: What are the amortized bounds of a Fibonacci heap for insert and decrease-key?
Answer: Insert: O(1) amortized. Decrease-key: O(1) amortized. Delete-min: O(log n) amortized.

## Q16: Why is a heap not suitable for searching for an arbitrary element?
Answer: The heap property only guarantees the min (or max) is at the root. There is no ordering invariant among siblings or across subtrees that would enable pruning a search, so finding an arbitrary element requires O(n) scan.

## Q17: What is the lower bound on comparison-based sorting and why?
Answer: Omega(n log n). Any comparison-based sort must distinguish between n! permutations, requiring at least log2(n!) = Omega(n log n) comparisons in the worst case (decision tree argument).

## Q18: Why is quicksort generally faster than merge sort in practice despite having worse worst-case complexity?
Answer: Quicksort has better cache locality (in-place partitioning), lower constant factors, and smaller space overhead. Its O(n^2) worst case is avoidable with randomized or median-of-three pivot selection.

## Q19: What makes counting sort stable, and why does that matter for radix sort?
Answer: Counting sort places equal elements in the order they appear in the input by using a cumulative count array and iterating the input right-to-left. Stability is essential for radix sort because it sorts by one digit at a time (LSD first), and each pass must preserve the order established by previous passes.

## Q20: What is the time complexity of radix sort and when is it linear?
Answer: O(d(n+k)) where d is the number of digits and k is the radix. It is effectively linear when d is constant (bounded key length) and k is O(n).

## Q21: What is the time complexity of BFS and why does it find shortest paths in unweighted graphs?
Answer: O(V+E). BFS explores nodes level by level (by distance from source), so the first time it reaches a node is via the shortest path.

## Q22: What are the four edge classifications in DFS on a directed graph?
Answer: Tree edges (to unvisited vertices), back edges (to ancestors, indicate cycles), forward edges (to descendants already visited), and cross edges (to vertices in other branches already finished).

## Q23: When can topological sort be performed on a graph?
Answer: Only on directed acyclic graphs (DAGs). A topological ordering exists if and only if the graph has no cycles.

## Q24: What is the difference between Kahn's algorithm and DFS-based topological sort?
Answer: Kahn's uses BFS with in-degree tracking (repeatedly remove zero in-degree vertices). DFS-based uses reverse postorder. Both run in O(V+E). Kahn's can detect cycles (if not all vertices are output), while DFS detects them via back edges.

## Q25: What is the time complexity of Dijkstra's algorithm with a Fibonacci heap?
Answer: O(E + V log V). The Fibonacci heap gives O(1) amortized decrease-key, improving over the O(E log V) of a binary heap implementation.

## Q26: Why can't Dijkstra's algorithm handle negative edge weights?
Answer: Dijkstra greedily finalizes the closest unvisited vertex, assuming no shorter path can be found later. A negative edge could create a shorter path through an already-finalized vertex, violating this greedy invariant.

## Q27: What is the time complexity of Bellman-Ford and what can it detect that Dijkstra cannot?
Answer: O(VE). It can detect negative-weight cycles by checking if any distance can still be reduced after V-1 relaxation passes.

## Q28: What is the Floyd-Warshall algorithm used for and what is its complexity?
Answer: All-pairs shortest paths. O(V^3) time and O(V^2) space. It works by considering each vertex as a potential intermediate vertex in shortest paths.

## Q29: Why does the loop order matter in Floyd-Warshall?
Answer: The outermost loop must iterate over intermediate vertices k, with i and j as inner loops. This ensures that when considering vertex k as intermediate, all shortest paths using vertices 1..k-1 are already computed.

## Q30: What is the difference between Kruskal's and Prim's algorithms for MST, and when is each preferred?
Answer: Kruskal's sorts edges and uses union-find, running in O(E log E). Prim's grows from a vertex using a priority queue. Kruskal's is better for sparse graphs, Prim's (with Fibonacci heap, O(E + V log V)) is better for dense graphs.

## Q31: What two properties must a problem have for dynamic programming to apply?
Answer: Optimal substructure (optimal solution contains optimal solutions to subproblems) and overlapping subproblems (same subproblems are solved multiple times).

## Q32: What is the difference between top-down and bottom-up dynamic programming?
Answer: Top-down (memoization) uses recursion with caching, solves only needed subproblems. Bottom-up (tabulation) iterates in dependency order filling a table, avoids recursion overhead and may have better cache behavior.

## Q33: What is the time and space complexity of the standard LCS algorithm?
Answer: O(mn) time and O(mn) space for two sequences of length m and n. Space can be reduced to O(min(m,n)) if only the length is needed.

## Q34: Why is the 0/1 knapsack problem only pseudo-polynomial and not truly polynomial?
Answer: The DP runs in O(nW) where W is the capacity. But W is exponential in the input size (number of bits to represent W), so the algorithm is exponential in input length. This is why knapsack is weakly NP-complete.

## Q35: What is Kadane's algorithm and what is its complexity?
Answer: It finds the maximum subarray sum in O(n) time using the recurrence: max_ending_here = max(a[i], max_ending_here + a[i]). It maintains a running local maximum and a global maximum.

## Q36: What is the Master Theorem used for?
Answer: Solving recurrences of the form T(n) = aT(n/b) + f(n), which arise in divide-and-conquer algorithms. It gives the asymptotic complexity based on the relationship between f(n) and n^(log_b(a)).

## Q37: How does a greedy algorithm differ from dynamic programming?
Answer: Greedy makes locally optimal choices without reconsidering, requiring the greedy-choice property. DP considers all subproblems and combines their solutions. Greedy is a special case of DP where the locally optimal choice happens to be globally optimal.

## Q38: What is the exchange argument used for in greedy algorithm proofs?
Answer: It proves optimality by showing that any optimal solution can be transformed into the greedy solution without worsening it, by swapping elements that differ between the two solutions.

## Q39: What is backtracking and when does it improve over brute force?
Answer: Backtracking explores a search tree incrementally, abandoning partial candidates (pruning) as soon as they cannot lead to a valid solution. It improves over brute force when the reject function can prune large subtrees early, avoiding enumeration of all candidates.

## Q40: What is the time complexity of operations in a trie and how does it compare to a BST?
Answer: Trie operations (insert, search, delete) are O(m) where m is the key length, independent of the number of keys. A BST takes O(m log n) because each of the O(log n) comparisons takes O(m) time for string keys.

## Q41: What is a Fenwick tree (Binary Indexed Tree) used for?
Answer: Efficient prefix sum queries and point updates on an array, both in O(log n) time with O(n) space.

## Q42: What is the inverse Ackermann amortized bound for union-find, and what optimizations achieve it?
Answer: O(alpha(n)) amortized per operation, where alpha is the inverse Ackermann function (effectively constant for all practical inputs). Achieved by combining union by rank (or size) with path compression.

## Q43: What is the formal definition of Big-O notation?
Answer: f(n) = O(g(n)) means there exist positive constants c and n0 such that f(n) <= c*g(n) for all n >= n0. It provides an asymptotic upper bound on growth rate.

## Q44: Why is Big-O notation not an equality but a set membership?
Answer: O(g(n)) is a set of functions. Writing f(n) = O(g(n)) is a conventional abuse of notation meaning f(n) is in O(g(n)). The equals sign is not symmetric.

## Q45: What is amortized analysis and how does it differ from average-case analysis?
Answer: Amortized analysis gives a worst-case bound on the average cost per operation over a sequence of operations, with no probabilistic assumptions. Average-case analysis assumes a probability distribution over inputs.

## Q46: What are the three standard depth-first binary tree traversals and one application of each?
Answer: Inorder (left-root-right): produces sorted output from a BST. Preorder (root-left-right): used for copying/serializing a tree. Postorder (left-right-root): used for deletion (deletes children before parent).

## Q47: What is Morris traversal and what makes it special?
Answer: Morris traversal performs inorder traversal using O(1) extra space (no stack or recursion) by temporarily modifying tree pointers, threading right-null pointers to inorder successors, then restoring them.

## Q48: How can you reconstruct a binary tree from traversal sequences?
Answer: A binary tree can be uniquely reconstructed from inorder + preorder, or inorder + postorder. Preorder + postorder alone is not sufficient (ambiguous for trees with single-child nodes).

## Q49: Why does memoization require referential transparency (pure functions)?
Answer: Memoization caches return values by input. If a function has side effects or depends on mutable state, the cached result may be incorrect for subsequent calls with the same input but different state. Purity guarantees the same input always produces the same output.

## Q50: What is the time complexity of heapsort and why is it not stable?
Answer: O(n log n) in all cases (best, average, worst). It is not stable because the heap operations (sift-down during extract-max) can change the relative order of equal elements when swapping with distant array positions.
