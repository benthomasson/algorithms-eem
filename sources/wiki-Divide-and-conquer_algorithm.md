---
source: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
fetched: 2026-06-19
---

Algorithms which recursively solve subproblems 

In [computer science](./Computer_science), **divide and conquer** is an [algorithm design paradigm](./Algorithm_design_paradigm). A divide-and-conquer [algorithm](./Algorithm) [recursively](./Recursion_(computer_science)) breaks down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly. The solutions to the sub-problems are then combined to give a solution to the original problem.

 

The divide-and-conquer technique is the basis of efficient algorithms for many problems, such as [sorting](./Sorting_algorithm) (e.g., [quicksort](./Quicksort), [merge sort](./Merge_sort)), [multiplying large numbers](./Multiplication_algorithm) (e.g., the [Karatsuba algorithm](./Karatsuba_algorithm)), finding the [closest pair of points](./Closest_pair_of_points_problem), [syntactic analysis](./Syntactic_analysis) (e.g., [top-down parsers](./Top-down_parser)), [SAT solving](./SAT_solver),[[1]](./Divide-and-conquer_algorithm#cite_note-:0-1) and computing the [discrete Fourier transform](./Discrete_Fourier_transform) ([FFT](./Fast_Fourier_transform)).[[2]](./Divide-and-conquer_algorithm#cite_note-2)

 

Designing efficient divide-and-conquer algorithms can be difficult. As in [mathematical induction](./Mathematical_induction), it is often necessary to generalize the problem to make it amenable to a [recursive](./Recursion_(computer_science)) solution. The correctness of a divide-and-conquer algorithm is usually proved by mathematical induction, and its computational cost is often determined by solving [recurrence relations](./Recurrence_relation).

 

## Divide and conquer

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Merge_sort_algorithm_diagram.svg/250px-Merge_sort_algorithm_diagram.svg.png)](./File:Merge_sort_algorithm_diagram.svg)Divide-and-conquer approach to sort the list (38, 27, 43, 3, 9, 82, 10) in increasing order. *Upper half:* splitting into sublists; *mid:* a one-element list is trivially sorted; *lower half:* composing sorted sublists. 

The divide-and-conquer [paradigm](./Programming_paradigm) is often used to find an optimal solution of a problem. Its basic idea is to decompose a given problem into two or more similar, but simpler, subproblems, to solve them in turn, and to compose their solutions to solve the given problem. Problems of sufficient simplicity are solved directly. 
For example, to sort a given list of *n* [natural numbers](./Natural_number), split it into two lists of about *n*/2 numbers each, sort each of them in turn, and interleave both results appropriately to obtain the sorted version of the given list (see the picture). This approach is known as the [merge sort](./Merge_sort) algorithm.

 

The name "divide and conquer" is sometimes applied to algorithms that reduce each problem to only one sub-problem, such as the [binary search](./Binary_search) algorithm for finding a record in a sorted list (or its analogue in [numerical computing](./Numerical_algorithm), the [bisection algorithm](./Bisection_algorithm) for [root finding](./Root-finding_algorithm)).[[3]](./Divide-and-conquer_algorithm#cite_note-CormenLeiserson2009-3)  These algorithms can be implemented more efficiently than general divide-and-conquer algorithms; in particular, if they use [tail recursion](./Tail_recursion), they can be converted into simple [loops](./Loop_(computing)).  Under this broad definition, however, every algorithm that uses recursion or loops could be regarded as a "divide-and-conquer algorithm".  Therefore, some authors consider that the name "divide and conquer" should be used only when each problem may generate two or more subproblems.[[4]](./Divide-and-conquer_algorithm#cite_note-4) The name **decrease and conquer** has been proposed instead for the single-subproblem class.[[5]](./Divide-and-conquer_algorithm#cite_note-5)

 

An important application of divide and conquer is in optimization,[*[example needed](./Wikipedia:AUDIENCE)*] where if the search space is reduced ("pruned") by a constant factor at each step, the overall algorithm has the same asymptotic complexity as the pruning step, with the constant depending on the pruning factor (by summing the [geometric series](./Geometric_series)); this is known as [prune and search](./Prune_and_search).

 

## Early historical examples

 

Early examples of these algorithms are primarily decrease and conquer – the original problem is successively broken down into *single* subproblems, and indeed can be solved iteratively.

 

[Binary search](./Binary_search_algorithm), a decrease-and-conquer algorithm where the subproblems are of roughly half the original size, has a long history. While a clear description of the algorithm on computers appeared in 1946 in an article by [John Mauchly](./John_Mauchly), the idea of using a sorted list of items to facilitate searching dates back at least as far as [Babylonia](./Babylonia) in 200 BC.[[6]](./Divide-and-conquer_algorithm#cite_note-Knuth3-6) Another ancient decrease-and-conquer algorithm is the [Euclidean algorithm](./Euclidean_algorithm) to compute the [greatest common divisor](./Greatest_common_divisor) of two numbers by reducing the numbers to smaller and smaller equivalent subproblems, which dates to several centuries BC.

 

An early example of a divide-and-conquer algorithm with multiple subproblems is [Gauss](./Carl_Friedrich_Gauss)'s 1805 description of what is now called the [Cooley–Tukey fast Fourier transform](./Cooley–Tukey_FFT_algorithm) (FFT) algorithm,[[7]](./Divide-and-conquer_algorithm#cite_note-Heideman84-7) although he did not [analyze its operation count](./Analysis_of_algorithms) quantitatively, and FFTs did not become widespread until they were rediscovered over a century later.

 

An early two-subproblem D&C algorithm that was specifically developed for computers and properly analyzed is the [merge sort](./Merge_sort) algorithm, invented by [John von Neumann](./John_von_Neumann) in 1945.[[8]](./Divide-and-conquer_algorithm#cite_note-8)

 

Another notable example is the [algorithm](./Karatsuba_algorithm) invented by [Anatolii A. Karatsuba](./Anatolii_Alexeevitch_Karatsuba) in 1960[[9]](./Divide-and-conquer_algorithm#cite_note-9) that could multiply two *n*-[digit](./Units_of_information) numbers in     O (  n   log  2   ⁡ ⁡  3   )   {\displaystyle O(n^{\log _{2}3})}  ![{\displaystyle O(n^{\log _{2}3})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/770c7081e94ce7027c145a2f892341605e9b0272) operations (in [Big O notation](./Big_O_notation)). This algorithm disproved [Andrey Kolmogorov](./Andrey_Kolmogorov)'s 1956 conjecture that     Ω Ω  (  n  2   )   {\displaystyle \Omega (n^{2})}  ![{\displaystyle \Omega (n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c14304cd1cb8bf603cb59037b666c5a85cd8e7ae) operations would be required for that task.

 

As another example of a divide-and-conquer algorithm that did not originally involve computers, [Donald Knuth](./Donald_Knuth) gives the method a [post office](./Post_office) typically uses to route mail: letters are sorted into separate bags for different geographical areas, each of these bags is itself sorted into batches for smaller sub-regions, and so on until they are delivered.[[6]](./Divide-and-conquer_algorithm#cite_note-Knuth3-6) This is related to a [radix sort](./Radix_sort), described for [punch-card sorting](./IBM_80_series_Card_Sorters) machines as early as 1929.[[6]](./Divide-and-conquer_algorithm#cite_note-Knuth3-6)

 

## Advantages

 

### Solving difficult problems

 

Divide and conquer is a powerful tool for solving conceptually difficult problems: all it requires is a way of breaking the problem into sub-problems, of solving the trivial cases, and of combining sub-problems to the original problem. Similarly, decrease and conquer only requires reducing the problem to a single smaller problem, such as the classic [Tower of Hanoi](./Tower_of_Hanoi) puzzle, which reduces moving a tower of height     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) to move a tower of height     n − −  1   {\displaystyle n-1}  ![{\displaystyle n-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521).

 

### Algorithm efficiency

 

The divide-and-conquer paradigm often helps in the discovery of efficient algorithms.  It was the key, for example, to [Karatsuba](./Karatsuba_algorithm)'s fast multiplication method, the quicksort and mergesort algorithms, the [Strassen algorithm](./Strassen_algorithm) for [matrix multiplication](./Matrix_multiplication), and fast Fourier transforms.

 

In all these examples, the D&C approach led to an improvement in the [asymptotic cost](./Asymptotic_complexity) of the solution. For example, if (a) the [base cases](./Recursion_(computer_science)) have constant-bounded size, the work of splitting the problem and combining the partial solutions is proportional to the problem's size     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), and (b) there is a bounded number     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) of sub-problems of size ~       n p     {\displaystyle {\frac {n}{p}}}  ![{\displaystyle {\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b32fd3506523ca103ed9eb0fdd51780648235158) at each stage, then the cost of the divide-and-conquer algorithm will be     O ( n  log  p   ⁡ ⁡  n )   {\displaystyle O(n\log _{p}n)}  ![{\displaystyle O(n\log _{p}n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ec332e6a1bd01306f96977220505689e4c578ec).

 

For other types of divide-and-conquer approaches, running times can also be generalized. For example, when a) the work of splitting the problem and combining the partial solutions take     c n   {\displaystyle cn}  ![{\displaystyle cn}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7f0390269a433e7f1a987b5968c6229e43cd7a2b) time, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the input size and     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) is some constant; b) when     n < 2   {\displaystyle n<2}  ![{\displaystyle n<2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34a7846d78a64db4abe69af89c7ef79c249e75ff), the algorithm takes time upper-bounded by     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455), and c) there are     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) subproblems where each subproblem has size ~       n 2     {\displaystyle {\frac {n}{2}}}  ![{\displaystyle {\frac {n}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1216d48de276dc45542cb80b1e49037131ec9624). Then, the running times are as follows:

 
- if the number of subproblems     q > 2   {\displaystyle q>2}  ![{\displaystyle q>2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a51ff72f66c28051a819a034dea86997914ab599), then the divide-and-conquer algorithm's running time is bounded by     O (  n   log  2   ⁡ ⁡  q   )   {\displaystyle O(n^{\log _{2}q})}  ![{\displaystyle O(n^{\log _{2}q})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d93c45f148617f5dd55a590a7d91a6a3fb82f002).
- if the number of subproblems is exactly one, then the divide-and-conquer algorithm's running time is bounded by     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a).[[10]](./Divide-and-conquer_algorithm#cite_note-kleinberg&Tardos-10)

 

If, instead, the work of splitting the problem and combining the partial solutions take     c  n  2     {\displaystyle cn^{2}}  ![{\displaystyle cn^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48d6ba2aa952fc4610423a129d41f2c5f3f31c8d) time, and there are 2 subproblems where each has size       n 2     {\displaystyle {\frac {n}{2}}}  ![{\displaystyle {\frac {n}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1216d48de276dc45542cb80b1e49037131ec9624), then the running time of the divide-and-conquer algorithm is bounded by     O (  n  2   )   {\displaystyle O(n^{2})}  ![{\displaystyle O(n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cd9594a16cb898b8f2a2dff9227a385ec183392).[[10]](./Divide-and-conquer_algorithm#cite_note-kleinberg&Tardos-10)

 

### Parallelism

 

Divide-and-conquer algorithms are naturally adapted for execution in [multi-processor](./Multiprocessing) machines, especially [shared-memory](./Shared-memory) systems where the communication of data between [processors](./Central_processing_unit) does not need to be planned in advance because distinct sub-problems can be executed on different processors.

 

### Memory access

 

Divide-and-conquer algorithms naturally tend to make efficient use of [memory caches](./Memory_cache). The reason is that once a sub-problem is small enough, it and all its sub-problems can, in principle, be solved within the [cache](./Cache_(computing)), without accessing the slower [main memory](./Computer_data_storage). An algorithm designed to exploit the cache in this way is called *[cache-oblivious](./Cache-oblivious_algorithm)*, because it does not contain the cache size as an explicit [parameter](./Parameter_(computer_programming)).[[11]](./Divide-and-conquer_algorithm#cite_note-cahob-11) Moreover, D&C algorithms can be designed for important algorithms (e.g., sorting, FFTs, and matrix multiplication) to be *optimal* cache-oblivious algorithms–they use the cache in a probably optimal way, in an asymptotic sense, regardless of the cache size. In contrast, the traditional approach to exploiting the cache is *blocking*, as in [loop nest optimization](./Loop_nest_optimization), where the problem is explicitly divided into chunks of the appropriate size—this can also use the cache optimally, but only when the algorithm is tuned for the specific cache sizes of a particular machine.

 

The same advantage exists with regards to other hierarchical storage systems, such as [NUMA](./Non-uniform_memory_access) or [virtual memory](./Virtual_memory), as well as for multiple levels of cache: once a sub-problem is small enough, it can be solved within a given level of the hierarchy, without accessing the higher (slower) levels.

 

### Roundoff control

 

In computations with rounded arithmetic, e.g. with [floating-point](./Floating-point) numbers, a divide-and-conquer algorithm may yield more accurate results than a superficially equivalent iterative method. For example, one can add *N* numbers either by a simple loop that adds each datum to a single variable, or by a D&C algorithm called [pairwise summation](./Pairwise_summation) that breaks the data set into two halves, recursively computes the sum of each half, and then adds the two sums.  While the second method performs the same number of additions as the first and pays the overhead of the recursive calls, it is usually more accurate.[[12]](./Divide-and-conquer_algorithm#cite_note-12)

 

## Implementation issues

 

### Recursion

 

Divide-and-conquer algorithms are naturally implemented as [recursive procedures](./Recursion_(computer_science)). In that case, the partial sub-problems leading to the one currently being solved are automatically stored in the [procedure call stack](./Call_stack). A recursive function is a function that calls itself within its definition.

 

### Explicit stack

 

Divide-and-conquer algorithms can also be implemented by a non-recursive program that stores the partial sub-problems in some explicit data structure, such as a [stack](./Stack_(data_structure)), [queue](./Queue_(data_structure)), or [priority queue](./Priority_queue).  This approach allows more freedom in the choice of the sub-problem that is to be solved next, a feature that is important in some applications — e.g. in [breadth-first recursion](./Breadth_first_recursion) and the [branch-and-bound](./Branch-and-bound) method for function optimization. This approach is also the standard solution in programming languages that do not provide support for recursive procedures.

 

### Stack size

 

In recursive implementations of D&C algorithms, one must make sure that there is sufficient memory allocated for the recursion stack, otherwise, the execution may fail because of [stack overflow](./Stack_overflow).  D&C algorithms that are time-efficient often have relatively small recursion depth.  For example, the quicksort algorithm can be implemented so that it never requires more than      log  2   ⁡ ⁡  n   {\displaystyle \log _{2}n}  ![{\displaystyle \log _{2}n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d74677fc45e0d926639433586327cbc2982eae89) nested recursive calls to sort     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) items.

 

Stack overflow can be difficult to prevent when using recursive procedures, since many compilers treat the recursion stack as a contiguous block of memory, and some reserve a fixed amount of space for it. In addition, compilers may store more information on the recursion stack than is strictly required, including the return address, unchanged parameters, and the procedure’s local variables. As a result, the likelihood of stack overflow may be reduced by limiting the number of parameters and local variables in the recursive procedure, or by replacing recursion with an explicit stack data structure.

 

### Choosing the base cases

 

In any recursive algorithm, there is considerable freedom in the choice of the *base cases*, the small subproblems that are solved directly in order to terminate the recursion.

 

Choosing the smallest or simplest possible base cases is more elegant and usually leads to simpler programs, because there are fewer cases to consider and they are easier to solve. For example, a [Fast Fourier Transform](./Fast_Fourier_transform) algorithm could stop the recursion when the input is a single sample, and the quicksort list-sorting algorithm could stop when the input is the empty list; in both examples, there is only one base case to consider, and it requires no processing.

 

On the other hand, efficiency often improves if the recursion is stopped at relatively large base cases, and these are solved non-recursively, resulting in a [hybrid algorithm](./Hybrid_algorithm). This strategy avoids the overhead of recursive calls that do little or no work and may also allow the use of specialized non-recursive algorithms that, for those base cases, are more efficient than explicit recursion. A general procedure for a simple hybrid recursive algorithm is *short-circuiting the base case*, also known as *[arm's-length recursion](./Arm's-length_recursion)*. In this case, whether the next step will result in the base case is checked before the function call, avoiding an unnecessary function call. For example, in a tree, rather than recursing to a child node and then checking whether it is null, checking null before recursing avoids half the function calls in some algorithms on binary trees. Since a D&C algorithm eventually reduces each problem or sub-problem instance to a large number of base instances, these often dominate the overall cost of the algorithm, especially when the splitting/joining overhead is low. Note that these considerations do not depend on whether recursion is implemented by the compiler or by an explicit stack.

 

Thus, for example, many library implementations of quicksort will switch to a simple loop-based [insertion sort](./Insertion_sort) (or similar) algorithm once the number of items to be sorted is sufficiently small. Note that, if the empty list were the only base case, sorting a list with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) entries would entail maximally     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) quicksort calls that would do nothing but return immediately.  Increasing the base cases to lists of size 2 or less will eliminate most of those do-nothing calls, and more generally a base case larger than 2 is typically used to reduce the fraction of time spent in function-call overhead or stack manipulation.

 

Alternatively, one can employ large base cases that still use a divide-and-conquer algorithm, but implement the algorithm for predetermined set of fixed sizes where the algorithm can be completely [unrolled](./Loop_unwinding) into code that has no recursion, loops, or [conditionals](./Conditional_(programming)) (related to the technique of [partial evaluation](./Partial_evaluation)).  For example, this approach is used in some efficient FFT implementations, where the base cases are unrolled implementations of divide-and-conquer FFT algorithms for a set of fixed sizes.[[13]](./Divide-and-conquer_algorithm#cite_note-fftw-13) [Source-code generation](./Source-code_generation) methods may be used to produce the large number of separate base cases desirable to implement this strategy efficiently.[[13]](./Divide-and-conquer_algorithm#cite_note-fftw-13)

 

The generalized version of this idea is known as recursion "unrolling" or "coarsening", and various techniques have been proposed for automating the procedure of enlarging the base case.[[14]](./Divide-and-conquer_algorithm#cite_note-14)

 

### Dynamic programming for overlapping subproblems

 

For some problems, the branched recursion may end up evaluating the same sub-problem many times over.  In such cases it may be worth identifying and saving the solutions to these overlapping subproblems, a technique which is commonly known as [memoization](./Memoization).  Followed to the limit, it leads to [bottom-up](./Bottom-up_design) divide-and-conquer algorithms such as [dynamic programming](./Dynamic_programming).

 

## See also

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Divide-and-conquer algorithms](https://commons.wikimedia.org/wiki/Category:Divide-and-conquer%20algorithms).  
- [Akra–Bazzi method](./Akra–Bazzi_method) – Method in computer science
- [Decomposable aggregation function](./Decomposable_aggregation_function) – Type of function in database managementPages displaying short descriptions of redirect targets
- ["Divide and conquer"](./Divide_and_conquer) – Strategy in politics and sociology
- [Fork–join model](./Fork–join_model) – Way of setting up and executing parallel computer programs
- [Master theorem (analysis of algorithms)](./Master_theorem_(analysis_of_algorithms)) – Tool for analyzing divide-and-conquer algorithms
- [Mathematical induction](./Mathematical_induction) – Form of mathematical proof
- [MapReduce](./MapReduce) – Parallel programming model
- [Heuristic (computer science)](./Heuristic_(computer_science)) – Type of algorithm, produces approximately correct solutions

 

## References

  
1. [↑](./Divide-and-conquer_algorithm#cite_ref-:0_1-0) [Heule, Marijn J. H.](./Marijn_Heule); Kullmann, Oliver; Wieringa, Siert; Biere, Armin (2012), "Cube and Conquer: Guiding CDCL SAT Solvers by Lookaheads", *Hardware and Software: Verification and Testing*, Lecture Notes in Computer Science, vol. 7261, Springer Berlin Heidelberg, pp. 50–65, [doi](./Doi_(identifier)):[10.1007/978-3-642-34188-5_8](https://doi.org/10.1007%2F978-3-642-34188-5_8), [ISBN](./ISBN_(identifier)) [978-3-642-34187-8](./Special:BookSources/978-3-642-34187-8)`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
2. [↑](./Divide-and-conquer_algorithm#cite_ref-2) [Blahut, Richard](./Richard_Blahut) (14 May 2014). *Fast Algorithms for Signal Processing*. Cambridge University Press. pp. 139–143. [ISBN](./ISBN_(identifier)) [978-0-511-77637-3](./Special:BookSources/978-0-511-77637-3).
3. [↑](./Divide-and-conquer_algorithm#cite_ref-CormenLeiserson2009_3-0) Thomas H. Cormen; Charles E. Leiserson; Ronald L. Rivest; Clifford Stein (31 July 2009). [*Introduction to Algorithms*](https://books.google.com/books?id=aefUBQAAQBAJ&q=%22Divide-and-conquer%22). MIT Press. [ISBN](./ISBN_(identifier)) [978-0-262-53305-8](./Special:BookSources/978-0-262-53305-8).
4. [↑](./Divide-and-conquer_algorithm#cite_ref-4) Brassard, G., and Bratley, P. Fundamental of Algorithmics, Prentice-Hall, 1996.
5. [↑](./Divide-and-conquer_algorithm#cite_ref-5) Anany V. Levitin, *Introduction to the Design and Analysis of Algorithms* (Addison Wesley, 2002).
6. [1](./Divide-and-conquer_algorithm#cite_ref-Knuth3_6-0) [2](./Divide-and-conquer_algorithm#cite_ref-Knuth3_6-1) [3](./Divide-and-conquer_algorithm#cite_ref-Knuth3_6-2) Donald E. Knuth, *The Art of Computer Programming: Volume 3, Sorting and Searching*, second edition (Addison-Wesley, 1998).
7. [↑](./Divide-and-conquer_algorithm#cite_ref-Heideman84_7-0) Heideman, M. T., D. H. Johnson, and C. S. Burrus, "[Gauss and the history of the fast Fourier transform](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.331.4791&rep=rep1&type=pdf)", IEEE ASSP Magazine, 1, (4), 14–21 (1984).
8. [↑](./Divide-and-conquer_algorithm#cite_ref-8) [Knuth, Donald](./Donald_Knuth) (1998). [*The Art of Computer Programming: Volume 3 Sorting and Searching*](https://archive.org/details/artofcomputerpro03knut). Addison-Wesley. p. [159](https://archive.org/details/artofcomputerpro03knut/page/159). [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0).
9. [↑](./Divide-and-conquer_algorithm#cite_ref-9) [Karatsuba, Anatolii A.](./Anatolii_Alexeevitch_Karatsuba); [Yuri P. Ofman](./Yuri_Petrovich_Ofman) (1962). "Умножение многозначных чисел на автоматах". *[Doklady Akademii Nauk SSSR](./Doklady_Akademii_Nauk_SSSR)*. **146**: 293–294. Translated in Karatsuba, A.; Ofman, Yu. (1963). ["Multiplication of Multidigit Numbers on Automata"](https://books.google.com/books?id=MrkOAAAAIAAJ). *Soviet Physics Doklady*. **7**: 595–596. [Bibcode](./Bibcode_(identifier)):[1963SPhD....7..595K](https://ui.adsabs.harvard.edu/abs/1963SPhD....7..595K).
10. [1](./Divide-and-conquer_algorithm#cite_ref-kleinberg&Tardos_10-0) [2](./Divide-and-conquer_algorithm#cite_ref-kleinberg&Tardos_10-1) Kleinberg, Jon; Tardos, Eva (March 16, 2005). [*Algorithm Design*](https://www.pearson.com/en-us/subject-catalog/p/algorithm-design/P200000003259/9780137546350) (1 ed.). [Pearson Education](./Pearson_Education). pp. 214–220. [ISBN](./ISBN_(identifier)) [9780321295354](./Special:BookSources/9780321295354). Retrieved 26 January 2025.
11. [↑](./Divide-and-conquer_algorithm#cite_ref-cahob_11-0) M. Frigo; C. E. Leiserson; H. Prokop (1999). ["Cache-oblivious algorithms"](https://dspace.mit.edu/bitstream/handle/1721.1/80568/43558192-MIT.pdf;sequence=2). *40th Annual Symposium on Foundations of Computer Science (Cat. No.99CB37039)*. pp. 285–297. [doi](./Doi_(identifier)):[10.1109/SFFCS.1999.814600](https://doi.org/10.1109%2FSFFCS.1999.814600). [ISBN](./ISBN_(identifier)) [0-7695-0409-4](./Special:BookSources/0-7695-0409-4). [S2CID](./S2CID_(identifier)) [62758836](https://api.semanticscholar.org/CorpusID:62758836).
12. [↑](./Divide-and-conquer_algorithm#cite_ref-12) Nicholas J. Higham, "[The accuracy of floating-point summation](https://pdfs.semanticscholar.org/5c17/9d447a27c40a54b2bf8b1b2d6819e63c1a69.pdf)", *SIAM J. Scientific Computing* **14** (4), 783–799 (1993).
13. [1](./Divide-and-conquer_algorithm#cite_ref-fftw_13-0) [2](./Divide-and-conquer_algorithm#cite_ref-fftw_13-1) Frigo, M.; Johnson, S. G. (February 2005). ["The design and implementation of FFTW3"](http://www.fftw.org/fftw-paper-ieee.pdf) (PDF). *Proceedings of the IEEE*. **93** (2): 216–231. [Bibcode](./Bibcode_(identifier)):[2005IEEEP..93..216F](https://ui.adsabs.harvard.edu/abs/2005IEEEP..93..216F). [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.66.3097](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.66.3097). [doi](./Doi_(identifier)):[10.1109/JPROC.2004.840301](https://doi.org/10.1109%2FJPROC.2004.840301). [S2CID](./S2CID_(identifier)) [6644892](https://api.semanticscholar.org/CorpusID:6644892).
14. [↑](./Divide-and-conquer_algorithm#cite_ref-14) Radu Rugina and Martin Rinard, "[Recursion unrolling for divide and conquer programs](http://people.csail.mit.edu/rinard/paper/lcpc00.pdf)" in *Languages and Compilers for Parallel Computing*, chapter 3, pp. 34–48.  *Lecture Notes in Computer Science* vol. 2017 (Berlin: Springer, 2001).

| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |

 
| Authority control databases | GND |
| --- | --- |