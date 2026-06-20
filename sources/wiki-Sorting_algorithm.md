---
source: https://en.wikipedia.org/wiki/Sorting_algorithm
fetched: 2026-06-19
---

Algorithm that arranges lists in order 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Merge_sort_animation.gif/250px-Merge_sort_animation.gif)](./File:Merge_sort_animation.gif)[Merge sort](./Merge_sort) 

In [computer science](./Computer_science), a **sorting algorithm** is an [algorithm](./Algorithm) that puts elements of a [list](./List_(computing)) into an [order](./Total_order). The most frequently used orders are [numerical order](./Numerical_order) and [lexicographical order](./Lexicographical_order), and either ascending order or descending order. Efficient [sorting](./Sorting) is important for optimizing the [efficiency](./Algorithmic_efficiency) of other algorithms (such as [search](./Search_algorithm) and [merge](./Merge_algorithm) algorithms) that require input data to be in sorted lists. Sorting is also often useful for [canonicalizing](./Canonicalization) data and for producing human-readable output.

 

Formally, the output of any sorting algorithm must satisfy two conditions:

 
1. The output is in [monotonic](./Monotonic) order (each element is no smaller/larger than the previous element, according to the required order).
2. The output is a [permutation](./Permutation) (a reordering, yet retaining all of the original elements) of the input.

 

Although some algorithms are designed for [sequential access](./Sequential_access), the highest-performing algorithms assume data is stored in a [data structure](./Data_structure) which allows [random access](./Random_access).

 

## History and concepts

 

From the beginning of computing, the sorting problem has attracted a great deal of research, perhaps due to the complexity of solving it efficiently despite its simple, familiar statement. Among the authors of early sorting algorithms around 1951 was [Betty Holberton](./Betty_Holberton), who worked on [ENIAC](./ENIAC) and [UNIVAC](./UNIVAC).[[1]](./Sorting_algorithm#cite_note-refrigerator-1)[[2]](./Sorting_algorithm#cite_note-NYTimes-2) [Bubble sort](./Bubble_sort) was analyzed as early as 1956.[[3]](./Sorting_algorithm#cite_note-3) Asymptotically optimal algorithms have been known since the mid-20th century –  new algorithms are still being invented, with the widely used [Timsort](./Timsort) dating to 2002, and the [library sort](./Library_sort) being first published in 2006.

 

Comparison sorting algorithms have a fundamental requirement of     n log ⁡ ⁡   n  − −  1.4427 n + O ( log ⁡ ⁡   n  )   {\displaystyle n\log {n}-1.4427n+O(\log {n})}  ![{\displaystyle n\log {n}-1.4427n+O(\log {n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c125442dbaf49240c610a93e2ff11a412757c2d) comparisons. Algorithms not based on comparisons, such as [counting sort](./Counting_sort), can have better performance.

 

Sorting algorithms are prevalent in introductory [computer science](./Computer_science) classes, where the abundance of algorithms for the problem provides a gentle introduction to a variety of core algorithm concepts, such as [big O notation](./Big_O_notation), [divide-and-conquer algorithms](./Divide-and-conquer_algorithm), [data structures](./Data_structure) such as [heaps](./Heap_(data_structure)) and [binary trees](./Binary_tree), [randomized algorithms](./Randomized_algorithm), [best, worst and average case](./Best,_worst_and_average_case) analysis, [time–space tradeoffs](./Time–space_tradeoff), and [upper and lower bounds](./Upper_and_lower_bounds).

 

Sorting small arrays optimally (in the fewest comparisons and swaps) or fast (i.e. taking into account machine-specific details) is still an open research problem, with solutions only known for very small arrays (fewer than 20 elements). Similarly optimal (by various definitions) sorting on a [parallel machine](./Parallel_computing) is an open research topic.

 

## Classification

 This section is linked from [[Merge sort]]  

Sorting algorithms can be classified by:

 
- [Computational complexity](./Computational_complexity_theory) 
- [Best, worst and average case](./Best,_worst_and_average_case) behavior in terms of the size of the list. For typical serial sorting algorithms, good behavior is O(*n* log *n*), with parallel sort in O(log2 *n*), and bad behavior is O(*n*2). Ideal behavior for a serial sort is O(*n*), but this is not possible in the average case. Optimal parallel sorting is O(log *n*).
- Swaps for "in-place" algorithms.

- [Memory](./Memory_(computing)) usage (and use of other computer resources). In particular, some sorting algorithms are "[in-place](./In-place)". Strictly, an in-place sort needs only O(1) memory beyond the items being sorted; sometimes O(log *n*) additional memory is considered "in-place".
- Recursion: Some algorithms are either typically recursive or typically non-recursive, while others may typically be both (e.g., merge sort).
- Stability: [stable sorting algorithms](./Sorting_algorithm#Stability) maintain the relative order of records with equal keys (i.e., values).
- Whether or not they are a [comparison sort](./Comparison_sort). A comparison sort examines the data only by comparing two elements with a comparison operator.
- General method: insertion, exchange, selection, merging, *etc.* Exchange sorts include bubble sort and quicksort. Selection sorts include cycle sort and heapsort.
- Whether the algorithm is serial or parallel. The remainder of this discussion almost exclusively concentrates on serial algorithms and assumes serial operation.
- Adaptability: Whether or not the presortedness of the input affects the running time.  Algorithms that take this into account are known to be [adaptive](./Adaptive_sort).
- Online: An algorithm such as Insertion Sort that is online can sort a constant stream of input.

 

### Stability

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/82/Sorting_stability_playing_cards.svg/250px-Sorting_stability_playing_cards.svg.png)](./File:Sorting_stability_playing_cards.svg)An example of stable sort on playing cards. When the cards are sorted by rank with a stable sort, the two 5s must remain in the same order in the sorted output that they were originally in. When they are sorted with a non-stable sort, the 5s may end up in the opposite order in the sorted output. 

**Stable sorting algorithms** sort equal elements in the same order that they appear in the input. For example, in the card sorting example to the right, the cards are being sorted by their rank, and their suit is being ignored. This allows the possibility of multiple different correctly sorted versions of the original list. Stable sorting algorithms choose one of these, according to the following rule: if two items compare as equal (like the two 5 cards), then their relative order will be preserved, i.e. if one comes before the other in the input, it will come before the other in the output.

 

Stability is important to preserve order over multiple sorts on the same [data set](./Data_set). For example, say that student records consisting of name and class section are sorted dynamically, first by name, then by class section. If a stable sorting algorithm is used in both cases, the sort-by-class-section operation will not change the name order; with an unstable sort, it could be that sorting by section shuffles the name order, resulting in a nonalphabetical list of students.

 

More formally, the data being sorted can be represented as a record or tuple of values, and the part of the data that is used for sorting is called the *key*. In the card example, cards are represented as a record (rank, suit), and the key is the rank. A sorting algorithm is stable if whenever there are two records R and S with the same key, and R appears before S in the original list, then R will always appear before S in the sorted list.

 

When equal elements are indistinguishable, such as with integers, or more generally, any data where the entire element is the key, stability is not an issue. Stability is also not an issue if all keys are different.

 

Unstable sorting algorithms can be specially implemented to be stable. One way of doing this is to artificially extend the key comparison so that comparisons between two objects with otherwise equal keys are decided using the order of the entries in the original input list as a tie-breaker. Remembering this order, however, may require additional time and space.

 

One application for stable sorting algorithms is sorting a list using a primary and secondary key. For example, suppose we wish to sort a hand of cards such that the suits are in the order clubs (♣), diamonds (♦), hearts (♥), spades (♠), and within each suit, the cards are sorted by rank. This can be done by first sorting the cards by rank (using any sort), and then doing a stable sort by suit:

 

[![](//upload.wikimedia.org/wikipedia/commons/thumb/7/79/Sorting_playing_cards_using_stable_sort.svg/500px-Sorting_playing_cards_using_stable_sort.svg.png)](./File:Sorting_playing_cards_using_stable_sort.svg)

 

Within each suit, the stable sort preserves the ordering by rank that was already done. This idea can be extended to any number of keys and is utilised by [radix sort](./Radix_sort). The same effect can be achieved with an unstable sort by using a lexicographic key comparison, which, e.g., compares first by suit, and then compares by rank if the suits are the same.

 

## Comparison of algorithms

 

This analysis assumes that the length of each key is constant and that all comparisons, swaps and other operations can proceed in constant time.

 

Legend:

 
- n is the number of records to be sorted.
- Comparison column has the following ranking classifications: "Best", "Average" and "Worst" if the [time complexity](./Time_complexity) is given for each case.
- "Memory" denotes the amount of additional storage required by the algorithm.
- The run times and the memory requirements listed are inside [big O notation](./Big_O_notation), hence the base of the logarithms does not matter.
- The notation log2 *n* means (log *n*)2.

 

### Comparison sorts

 

Below is a table of [comparison sorts](./Comparison_sort). [Mathematical analysis](./Analysis_of_algorithms) demonstrates a comparison sort cannot perform better than *O*(*n* log *n*) on average.[[4]](./Sorting_algorithm#cite_note-4)

 
| Name | Best | Average | Worst | Memory | Stable | In-place | Method | Other notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Heapsort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | 1 | No | Yes | Selection | An optimized version of selection sort. Performs selection sort by constructing and maintaining a max heap to find the maximum inO(log⁡n){\displaystyle O(\log n)}time. |
| Introsort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | log⁡n{\displaystyle \log n} | No | Yes | Partitioning & Selection | Used in severalSTLimplementations. Performs a combination of Quicksort, Heapsort, and Insertion sort. |
| Merge sort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | Yes | No | Merging | Highly parallelizable(up toO(logn)using the Three Hungarians' Algorithm).[5] |
| In-Place Merge Sort | n{\displaystyle n} | nlog2⁡n{\displaystyle n\log ^{2}n} | nlog2⁡n{\displaystyle n\log ^{2}n} | log⁡n{\displaystyle \log n} | Yes | Yes | Merging | Variation of Mergesort which uses anO(nlog⁡n){\displaystyle O(n\log n)}in-place stable merge algorithm, such as rotate merge or symmerge. |
| Tournament sort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | Yes | No | Selection | An optimization of Selection Sort, which uses a tournament tree to select the min/max. |
| Tree sort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n}(balanced) | n | Yes | No | Insertion | When using aself-balancing binary search tree. |
| Block sort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | 1 | Yes | Yes | Insertion & Merging | Combine a block-based⁠O(n){\displaystyle O(n)}⁠in-place merge algorithm[6]with abottom-up merge sort. |
| Smoothsort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | 1 | No | Yes | Selection | Adaptivevariant of heapsort based on theLeonardo sequenceinstead of abinary heap. |
| Timsort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | Yes | No | Insertion & Merging | Makesn−1{\displaystyle n-1}comparisons when the data is already sorted or reverse sorted. |
| Patience sorting | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | No | No | Insertion & Selection | Finds all thelongest increasing subsequencesinO(nlogn). |
| Cubesort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | Yes | No | Insertion | Makesn−1{\displaystyle n-1}comparisons when the data is already sorted or reverse sorted. |
| Quicksort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n2{\displaystyle n^{2}} | log⁡n{\displaystyle \log n} | No | Yes | Partitioning | Quicksort can be done in-place withO(logn)stack space.[7][8] |
| Fluxsort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n | Yes | No | Partitioning & Merging | An adaptive branchless stable introsort. |
| Crumsort | n | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | log⁡n{\displaystyle \log n} | No | Yes | Partitioning & Merging | An in-place, but unstable variant of Fluxsort. |
| Library sort | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | n2{\displaystyle n^{2}} | n | No | No | Insertion | Similar to a gapped insertion sort. |
| Shellsort | nlog⁡n{\displaystyle n\log n} | Ω(nlog⁡n){\displaystyle \Omega (n\log n)} | O(n1+1/k){\displaystyle O(n^{1+1/k})}(Geometric)nlog2⁡n{\displaystyle n\log ^{2}n}(Pratt) | 1 | No | Yes | Insertion | Small code size. Complexity is influenced by the gap sequence used. Pratt's sequence is worst caseΘ(nlog2⁡n){\displaystyle \Theta (n\log ^{2}n)}which is the best known. Tight bounds for the average and worst case remain open problems. |
| Comb sort | nlog⁡n{\displaystyle n\log n} | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | No | Yes | Exchanging | Faster than bubble sort on average. |
| Insertion sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | Yes | Yes | Insertion | O(n+d), in the worst case over sequences that havedinversions. |
| Bubble sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | Yes | Yes | Exchanging | Tiny code size. |
| Cocktail shaker sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | Yes | Yes | Exchanging | A bi-directional variant of Bubblesort. |
| Gnome sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | Yes | Yes | Exchanging | Tiny code size. |
| Odd–even sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | Yes | Yes | Exchanging | Can be run on parallel processors easily. |
| Strand sort | n | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | n | Yes | No | Selection |  |
| Selection sort | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | No | Yes | Selection | Tiny code size. Noted for its simplicity and small number of element moves. Makes exactlyn−1{\displaystyle n-1}swaps. |
| Cycle sort | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | 1 | No | Yes | Selection | In-place with theoretically optimal number of writes. |

 

### Non-comparison sorts

 

The following table describes [integer sorting](./Integer_sorting) algorithms and other sorting algorithms that are not [comparison sorts](./Comparison_sort). These algorithms are not limited to [*Ω*(*n* log *n*)](./Big_O_notation) unless meet unit-cost [random-access machine](./Random-access_machine) model as described below.[[9]](./Sorting_algorithm#cite_note-9)

 
- Complexities below assume n items to be sorted, with keys of size k, digit size d, and r the range of numbers to be sorted.
- Many of them are based on the assumption that the key size is large enough that all entries have unique key values, and hence that *n* ≪ 2*k*, where  ≪ means "much less than".
- In the unit-cost [random-access machine](./Random-access_machine) model, algorithms with running time of     n ⋅ ⋅    k d     {\displaystyle n\cdot {\frac {k}{d}}}  ![{\displaystyle n\cdot {\frac {k}{d}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/53166c305a8b1af047f2e4c916c4fd8a304d40d0), such as radix sort, still take time proportional to Θ(*n* log *n*), because n is limited to be not more than      2   k d      {\displaystyle 2^{\frac {k}{d}}}  ![{\displaystyle 2^{\frac {k}{d}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c2794020402241e71c6f34e7b8ee37c363c2426), and a larger number of elements to sort would require a bigger k in order to store them in the memory.[[10]](./Sorting_algorithm#cite_note-10)

 
| Name | Best | Average | Worst | Memory | Stable | n≪ 2k | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pigeonhole sort | — | n+2k{\displaystyle n+2^{k}} | n+2k{\displaystyle n+2^{k}} | 2k{\displaystyle 2^{k}} | Yes | Yes | Cannot sort non-integers. |
| Bucket sort(uniform keys) | — | n+k{\displaystyle n+k} | n2⋅k{\displaystyle n^{2}\cdot k} | n⋅k{\displaystyle n\cdot k} | Yes | No | Assumes uniform distribution of elements from the domain in the array.[11]Also cannot sort non-integers. |
| Bucket sort(integer keys) | — | n+r{\displaystyle n+r} | n+r{\displaystyle n+r} | n+r{\displaystyle n+r} | Yes | Yes | Ifris⁠O(n){\displaystyle O(n)}⁠, then average time complexity is⁠O(n){\displaystyle O(n)}⁠.[12] |
| Counting sort | — | n+r{\displaystyle n+r} | n+r{\displaystyle n+r} | n+r{\displaystyle n+r} | Yes | Yes | Ifris⁠O(n){\displaystyle O(n)}⁠, then average time complexity is⁠O(n){\displaystyle O(n)}⁠.[11] |
| LSD Radix Sort | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n+2d{\displaystyle n+2^{d}} | Yes | No | kd{\displaystyle {\frac {k}{d}}}recursion levels, 2dfor count array.[11][12]Unlike most distribution sorts, this can sort non-integers. |
| MSD Radix Sort | n{\displaystyle n} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n+2d{\displaystyle n+2^{d}} | Yes | No | Stable version uses an external array of sizento hold all of the bins.Same as the LSD variant, it can sort non-integers. |
| MSD Radix Sort(in-place) | n{\displaystyle n} | n⋅k1{\displaystyle n\cdot {\frac {k}{1}}} | n⋅k1{\displaystyle n\cdot {\frac {k}{1}}} | 21{\displaystyle 2^{1}} | No | No | d=1 for in-place,k/1{\displaystyle k/1}recursion levels, no count array. |
| Spreadsort | n | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅(ks+d){\displaystyle n\cdot \left({{\frac {k}{s}}+d}\right)} | kd⋅2d{\displaystyle {\frac {k}{d}}\cdot 2^{d}} | No | No | Asymptotic are based on the assumption thatn≪ 2k, but the algorithm does not require this. |
| Burstsort | — | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | n⋅kd{\displaystyle n\cdot {\frac {k}{d}}} | No | No | Has better constant factor than radix sort for sorting strings. Though relies somewhat on specifics of commonly encountered strings. |
| Flashsort | n | n+r{\displaystyle n+r} | n2{\displaystyle n^{2}} | n | No | No | Requires uniform distribution of elements from the domain in the array to run in linear time. If distribution is extremely skewed then it can go quadratic if underlying sort is quadratic (it is usually an insertion sort). In-place version is not stable. |

 

[Samplesort](./Samplesort) can be used to parallelize any of the non-comparison sorts, by efficiently distributing data into several buckets and then passing down sorting to several processors, with no need to merge as buckets are already sorted between each other.

 

### Others

 

Some algorithms are slow compared to those discussed above, such as the [bogosort](./Bogosort) with unbounded run time and the [stooge sort](./Stooge_sort) which has *O*(*n*2.7) run time. These sorts are usually described for educational purposes to demonstrate how the run time of algorithms is estimated. The following table describes some sorting algorithms that are impractical for real-life use in traditional software contexts due to extremely poor performance or specialized hardware requirements.

 
| Name | Best | Average | Worst | Memory | Stable | Comparison | Other notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Bead sort | n | S | S | n2{\displaystyle n^{2}} | —N/a | No | Works only with positive integers. Requires specialized hardware for it to run in guaranteed⁠O(n){\displaystyle O(n)}⁠time. There is a possibility for software implementation, but running time will be⁠O(S){\displaystyle O(S)}⁠, whereSis the sum of all integers to be sorted; in the case of small integers, it can be considered to be linear. |
| Merge-insertion sort | nlog⁡n{\displaystyle n\log n}comparisons | nlog⁡n{\displaystyle n\log n}comparisons | nlog⁡n{\displaystyle n\log n}comparisons | Varies | No | Yes | Makes very few comparisons worst case compared to other sorting algorithms.Mostly of theoretical interest due to implementational complexity and suboptimal data moves. |
| Spaghetti (Poll) sort | n | n | n | n2{\displaystyle n^{2}} | Yes | Polling | This is a linear-time, analog algorithm for sorting a sequence of items, requiringO(n) stack space, and the sort is stable. This requiresnparallel processors. Seespaghetti sort §Analysis. |
| Sorting network | Varies | Varies | Varies | Varies | Varies (stable sorting networks require more comparisons) | Yes | Order of comparisons are set in advance based on a fixed network size. |
| Bitonic sorter | log2⁡n{\displaystyle \log ^{2}n}parallel | log2⁡n{\displaystyle \log ^{2}n}parallel | nlog2⁡n{\displaystyle n\log ^{2}n}non-parallel | 1 | No | Yes | An effective variation of Sorting networks.[disputed–discuss] |
| Bogosort | n | (n×n!){\displaystyle (n\times n!)} | Unbounded | 1 | No | Yes | Random shuffling. Used for example purposes only, as even the expected best-case runtime is awful.[13]Worst case is unbounded when using randomization, but a deterministic version guaranteesO(n×n!){\displaystyle O(n\times n!)}worst case. |
| Stooge sort | nlog⁡3/log⁡1.5{\displaystyle n^{\log 3/\log 1.5}} | nlog⁡3/log⁡1.5{\displaystyle n^{\log 3/\log 1.5}} | nlog⁡3/log⁡1.5{\displaystyle n^{\log 3/\log 1.5}} | log⁡n{\displaystyle \log n} | No | Yes | Slower than most of the sorting algorithms (even naive ones) with a time complexity ofO(nlog 3 / log 1.5) =O(n2.7095...)Can be made stable, and is also asorting network. |
| Slowsort | o(nlog2⁡(n)/2){\displaystyle o\left(n^{\log _{2}(n)/2}\right)} | o(nlog2⁡(n)/2){\displaystyle o\left(n^{\log _{2}(n)/2}\right)} | o(nlog2⁡(n)/2){\displaystyle o\left(n^{\log _{2}(n)/2}\right)} | n | No | Yes | A multiply and surrender algorithm, antonymous withdivide-and-conquer algorithm. |

 

Theoretical computer scientists have invented other sorting algorithms that provide better than *O*(*n* log *n*) time complexity assuming certain constraints, including:

 
- Thorup's algorithm,[[14]](./Sorting_algorithm#cite_note-:0-14) a randomized [integer sorting](./Integer_sorting) algorithm, taking *O*(*n* log log *n*) time and *O*(*n*) space.[[14]](./Sorting_algorithm#cite_note-:0-14)
- AHNR algorithm,[[15]](./Sorting_algorithm#cite_note-15) an [integer sorting](./Integer_sorting) algorithm which runs in     O ( n log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(n\log \log n)}  ![{\displaystyle O(n\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8147032e355336e05cf34c58407bd2380afb6f22) time deterministically, and also has a randomized version which runs in linear time when words are large enough, specifically     w ≥ ≥  ( log ⁡ ⁡  n  )  2 + ε ε      {\displaystyle w\geq (\log n)^{2+\varepsilon }}  ![{\displaystyle w\geq (\log n)^{2+\varepsilon }}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c232f5b420d3c2eeff465ca157711353a824177) (where *w* is the word size).
- A randomized [integer sorting](./Integer_sorting) algorithm taking     O  (  n   log ⁡ ⁡  log ⁡ ⁡  n    )    {\displaystyle O\left(n{\sqrt {\log \log n}}\right)}  ![{\displaystyle O\left(n{\sqrt {\log \log n}}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d2991c1899c53d189273f14cd055a14cf5d7f70e) expected time and *O*(*n*) space.[[16]](./Sorting_algorithm#cite_note-16)

 

## Popular sorting algorithms

 

While there are a large number of sorting algorithms, in practical implementations a few algorithms predominate. Insertion sort is widely used for small data sets, while for large data sets an asymptotically efficient sort is used, primarily heapsort, merge sort, or quicksort. Efficient implementations generally use a [hybrid algorithm](./Hybrid_algorithm), combining an asymptotically efficient algorithm for the overall sort with insertion sort for small lists at the bottom of a recursion. Highly tuned implementations use more sophisticated variants, such as [Timsort](./Timsort) (merge sort, insertion sort, and additional logic), used in [Android](./Android_(operating_system)), [Java](./Java_(programming_language)), and [Python](./Python_(programming_language)), and [introsort](./Introsort) (quicksort and heapsort), used (in variant forms) in some [C++ sort](./Sort_(C++)) implementations and in [.NET](./.NET).

 

For more restricted data, such as numbers in a fixed interval, [distribution sorts](./Sorting_algorithm#Distribution_sorts) such as counting sort or radix sort are widely used. Bubble sort and variants are rarely used in practice, but are commonly found in teaching and theoretical discussions.

 

When physically sorting objects (such as alphabetizing papers, tests or books) people intuitively generally use insertion sorts for small sets. For larger sets, people often first bucket, such as by initial letter, and multiple bucketing allows practical sorting of very large sets. Often space is relatively cheap, such as by spreading objects out on the floor or over a large area, but operations are expensive, particularly moving an object a large distance – [locality of reference](./Locality_of_reference) is important. Merge sorts are also practical for physical objects, particularly as two hands can be used, one for each list to merge, while other algorithms, such as heapsort or quicksort, are poorly suited for human use. Other algorithms, such as [library sort](./Library_sort), a variant of insertion sort that leaves spaces, are also practical for physical use.

 

### Simple sorts

 

Two of the simplest sorts are insertion sort and selection sort, both of which are efficient on small data, due to low overhead, but not efficient on large data. Insertion sort is generally faster than selection sort in practice, due to fewer comparisons and good performance on almost-sorted data, and thus is preferred in practice, but selection sort uses fewer writes, and thus is used when write performance is a limiting factor.

 

#### Insertion sort

 Main article: [Insertion sort](./Insertion_sort) 

*[Insertion sort](./Insertion_sort)* is a simple sorting algorithm that is relatively efficient for small lists and mostly sorted lists, and is often used as part of more sophisticated algorithms. It works by taking elements from the list one by one and inserting them in their correct position into a new sorted list similar to how one puts money in their wallet.[[17]](./Sorting_algorithm#cite_note-17) In arrays, the new list and the remaining elements can share the array's space, but insertion is expensive, requiring shifting all following elements over by one. [Shellsort](./Shellsort) is a variant of insertion sort that is more efficient for larger lists.

 

#### Selection sort

 Main article: [Selection sort](./Selection_sort) 

*Selection sort* is an [in-place](./In-place) [comparison sort](./Comparison_sort). It has [O](./Big_O_notation)(*n*2) complexity, making it inefficient on large lists, and generally performs worse than the similar [insertion sort](./Insertion_sort). Selection sort is noted for its simplicity and also has performance advantages over more complicated algorithms in certain situations.

 

The algorithm finds the minimum value, swaps it with the value in the first position, and repeats these steps for the remainder of the list.[[18]](./Sorting_algorithm#cite_note-18) It does no more than *n* swaps and thus is useful where swapping is very expensive.

 

### Efficient sorts

 

Practical general sorting algorithms are almost always based on an algorithm with average time complexity (and generally worst-case complexity) O(*n* log *n*), of which the most common are heapsort, merge sort, and quicksort. Each has advantages and drawbacks, with the most significant being that simple implementation of merge sort uses O(*n*) additional space, and simple implementation of quicksort has O(*n*2) worst-case complexity. These problems can be solved or ameliorated at the cost of a more complex algorithm.

 

While these algorithms are asymptotically efficient on random data, for practical efficiency on real-world data various modifications are used. First, the overhead of these algorithms becomes significant on smaller data, so often a hybrid algorithm is used, commonly switching to insertion sort once the data is small enough. Second, the algorithms often perform poorly on already sorted data or almost sorted data – these are common in real-world data and can be sorted in O(*n*) time by appropriate algorithms. Finally, they may also be [unstable](./Unstable_sort), and stability is often a desirable property in a sort. Thus more sophisticated algorithms are often employed, such as [Timsort](./Timsort) (based on merge sort) or [introsort](./Introsort) (based on quicksort, falling back to heapsort).

 

#### Merge sort

 Main article: [Merge sort](./Merge_sort) 

*Merge sort* takes advantage of the ease of merging already sorted lists into a new sorted list. It starts by comparing every two elements (i.e., 1 with 2, then 3 with 4...) and swapping them if the first should come after the second. It then merges each of the resulting lists of two into lists of four, then merges those lists of four, and so on; until at last two lists are merged into the final sorted list.[[19]](./Sorting_algorithm#cite_note-19) Of the algorithms described here, this is the first that scales well to very large lists, because its worst-case running time is O(*n* log *n*). It is also easily applied to lists, not only arrays, as it only requires sequential access, not random access. When sorting arrays, it has additional O(*n*) space complexity, and involves a large number of copies in simple implementations; however, [linked lists](./Linked_lists) can be merge sorted with constant extra space, as such it is the algorithm of choice for sorting linked lists.

 

Merge sort has seen a relatively recent surge in popularity for practical implementations, due to its use in the sophisticated algorithm [Timsort](./Timsort), which is used for the standard sort routine in the programming languages [Python](./Python_(programming_language))[[20]](./Sorting_algorithm#cite_note-20) and [Java](./Java_(programming_language)) (as of [JDK7](./JDK7)[[21]](./Sorting_algorithm#cite_note-21)). Merge sort itself is the standard routine in [Perl](./Perl),[[22]](./Sorting_algorithm#cite_note-22) among others, and has been used in Java at least since 2000 in [JDK1.3](./Java_version_history#J2SE_1.3).[[23]](./Sorting_algorithm#cite_note-mergesort_in_jdk13-23)

 

#### Heapsort

 Main article: [Heapsort](./Heapsort) 

*Heapsort* is a much more efficient version of [selection sort](./Selection_sort). It also works by determining the largest (or smallest) element of the list, placing that at the end (or beginning) of the list, then continuing with the rest of the list, but accomplishes this task efficiently by using a data structure called a [heap](./Heap_(data_structure)), a special type of [binary tree](./Binary_tree).[[24]](./Sorting_algorithm#cite_note-24) Once the data list has been made into a heap, the root node is guaranteed to be the largest (or smallest) element. When it is removed and placed at the end of the list, the heap is rearranged so the largest element remaining moves to the root. Using the heap, finding the next largest element takes O(log *n*) time, instead of O(*n*) for a linear scan as in simple selection sort. This allows Heapsort to run in O(*n* log *n*) time, and this is also the worst-case complexity.

 

#### Quicksort

 Main article: [Quicksort](./Quicksort) 

*Quicksort* is a [divide-and-conquer algorithm](./Divide-and-conquer_algorithm) which relies on a *partition* operation: to partition an array, an element called a *pivot* is selected.[[25]](./Sorting_algorithm#cite_note-25)[[26]](./Sorting_algorithm#cite_note-26) All elements smaller than the pivot are moved before it and all greater elements are moved after it. This can be done efficiently in linear time and [in-place](./In-place). The lesser and greater sublists are then recursively sorted. This yields an average time complexity of O(*n* log *n*), with low overhead, and thus this is a popular algorithm. Efficient implementations of quicksort (with in-place partitioning) are typically unstable sorts and somewhat complex but are among the fastest sorting algorithms in practice. Together with its modest O(log *n*) space usage, quicksort is one of the most popular sorting algorithms and is available in many standard programming libraries.

 

The important caveat about quicksort is that its worst-case performance is O(*n*2); while this is rare, in naive implementations (choosing the first or last element as pivot) this occurs for sorted data, which is a common case. The most complex issue in quicksort is thus choosing a good pivot element, as consistently poor choices of pivots can result in drastically slower O(*n*2) performance, but good choice of pivots yields O(*n* log *n*) performance, which is asymptotically optimal. For example, if at each step the [median](./Median) is chosen as the pivot then the algorithm works in O(*n* log *n*). Finding the median, such as by the [median of medians](./Median_of_medians) [selection algorithm](./Selection_algorithm) is however an O(*n*) operation on unsorted lists and therefore exacts significant overhead with sorting. In practice choosing a random pivot almost certainly yields O(*n* log *n*) performance.

 

If a guarantee of O(*n* log *n*) performance is important, there is a simple modification to achieve that. The idea, due to Musser, is to set a limit on the maximum depth of recursion.[[27]](./Sorting_algorithm#cite_note-27) If that limit is exceeded, then sorting is continued using the heapsort algorithm. Musser proposed that the limit should be     1 + 2 ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋    {\displaystyle 1+2\lfloor \log _{2}(n)\rfloor }  ![{\displaystyle 1+2\lfloor \log _{2}(n)\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c143f3d80f13928534fa8c5837e42bd4e9a2bd58), which is approximately twice the maximum recursion depth one would expect on average with a randomly [ordered array](./Ordered_array?action=edit&redlink=1).

 

#### Shellsort

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Shell_sorting_algorithm_color_bars.svg/250px-Shell_sorting_algorithm_color_bars.svg.png)](./File:Shell_sorting_algorithm_color_bars.svg)A Shellsort, different from bubble sort in that it moves elements to numerous [swapping positions](./Swap_(computer_science)) Main article: [Shellsort](./Shellsort) 

*Shellsort* was invented by [Donald Shell](./Donald_Shell) in 1959.[[28]](./Sorting_algorithm#cite_note-Shell-28) It improves upon insertion sort by moving out of order elements more than one position at a time. The concept behind Shellsort is that insertion sort performs in ⁠    O ( k n )   {\displaystyle O(kn)}  ![{\displaystyle O(kn)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ef610f176fc2b47d4e52605ae0a86d0a16cb67f)⁠ time, where k is the greatest distance between two out-of-place elements. This means that generally, they perform in *O*(*n*2), but for data that is mostly sorted, with only a few elements out of place, they perform faster. So, by first sorting elements far away, and progressively shrinking the gap between the elements to sort, the final sort computes much faster. One implementation can be described as arranging the data sequence in a two-dimensional array and then sorting the columns of the array using insertion sort.

 

The worst-case time complexity of Shellsort is an [open problem](./Open_problem) and depends on the gap sequence used, with known complexities ranging from *O*(*n*2) to *O*(*n*4/3) and Θ(*n* log2 *n*). This, combined with the fact that Shellsort is [in-place](./In-place), only needs a relatively small amount of code, and does not require use of the [call stack](./Call_stack), makes it is useful in situations where memory is at a premium, such as in [embedded systems](./Embedded_system) and [operating system kernels](./Operating_system_kernel).

 

### Bubble sort and variants

 

Bubble sort, and variants such as the [Comb sort](./Comb_sort) and [cocktail sort](./Cocktail_sort), are simple, highly inefficient sorting algorithms. They are frequently seen in introductory texts due to ease of analysis, but they are rarely used in practice.

 

#### Bubble sort

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/83/Bubblesort-edited-color.svg/250px-Bubblesort-edited-color.svg.png)](./File:Bubblesort-edited-color.svg)A bubble sort, a sorting algorithm that continuously steps through a list, [swapping](./Swap_(computer_science)) items until they appear in the correct order Main article: [Bubble sort](./Bubble_sort) 

*Bubble sort* is a simple sorting algorithm. The algorithm starts at the beginning of the data set. It compares the first two elements, and if the first is greater than the second, it swaps them. It continues doing this for each pair of adjacent elements to the end of the data set. It then starts again with the first two elements, repeating until no swaps have occurred on the last pass.[[29]](./Sorting_algorithm#cite_note-29) This algorithm's average time and worst-case performance is O(*n*2), so it is rarely used to sort large, unordered data sets. Bubble sort can be used to sort a small number of items (where its asymptotic inefficiency is not a high penalty). Bubble sort can also be used efficiently on a list of any length that is nearly sorted (that is, the elements are not significantly out of place). For example, if any number of elements are out of place by only one position (e.g. 0123546789 and 1032547698), bubble sort's exchange will get them in order on the first pass, the second pass will find all elements in order, so the sort will take only 2*n* time.

 

#### Comb sort

 Main article: [Comb sort](./Comb_sort) 

*Comb sort* is a relatively simple sorting algorithm based on [bubble sort](./Bubble_sort) and originally designed by Włodzimierz Dobosiewicz in 1980.[[30]](./Sorting_algorithm#cite_note-BB-30) It was later rediscovered and popularized by Stephen Lacey and Richard Box with a [*Byte* Magazine](./Byte_Magazine) article published in April 1991. The basic idea is to eliminate *turtles*, or small values near the end of the list, since in a bubble sort these slow the sorting down tremendously. (*Rabbits*, large values around the beginning of the list, do not pose a problem in bubble sort) It accomplishes this by initially swapping elements that are a certain distance from one another in the array, rather than only swapping elements if they are adjacent to one another, and then shrinking the chosen distance until it is operating as a normal bubble sort. Thus, if Shellsort can be thought of as a generalized version of insertion sort that swaps elements spaced a certain distance away from one another, comb sort can be thought of as the same generalization applied to bubble sort.

 

### Distribution sorts

 See also: [External sorting](./External_sorting) 

*Distribution sort* refers to any sorting algorithm where data is distributed from their input to multiple intermediate structures which are then gathered and placed on the output. For example, both [bucket sort](./Bucket_sort) and [flashsort](./Flashsort) are distribution-based sorting algorithms. Distribution sorting algorithms can be used on a single processor, or they can be a [distributed algorithm](./Distributed_algorithm), where individual subsets are separately sorted on different processors, then combined. This allows [external sorting](./External_sorting) of data too large to fit into a single computer's memory.

 

#### Counting sort

 Main article: [Counting sort](./Counting_sort) 

Counting sort is applicable when each input is known to belong to a particular set, *S*, of possibilities.  The algorithm runs in O(|*S*| + *n*) time and O(|*S*|) memory where *n* is the length of the input.  It works by creating an integer array of size |*S*| and using the *i*th bin to count the occurrences of the *i*th member of *S* in the input.  Each input is then counted by incrementing the value of its corresponding bin.  Afterward, the counting array is looped through to arrange all of the inputs in order.  This sorting algorithm often cannot be used because *S* needs to be reasonably small for the algorithm to be efficient, but it is extremely fast and demonstrates great asymptotic behavior as *n* increases.  It also can be modified to provide stable behavior.

 

#### Bucket sort

 Main article: [Bucket sort](./Bucket_sort) 

Bucket sort is a [divide-and-conquer](./Divide-and-conquer_algorithm) sorting algorithm that generalizes [counting sort](./Counting_sort) by partitioning an array into a finite number of buckets.  Each bucket is then sorted individually, either using a different sorting algorithm or by recursively applying the bucket sorting algorithm.

 

A bucket sort works best when the elements of the data set are evenly distributed across all buckets.

 

#### Radix sort

 Main article: [Radix sort](./Radix_sort) 

*Radix sort* is an algorithm that sorts numbers by processing individual digits. *n* numbers consisting of *k* digits each are sorted in O(*n* · *k*) time.  Radix sort can process digits of each number either starting from the [least significant digit](./Least_significant_digit) (LSD) or starting from the [most significant digit](./Most_significant_digit) (MSD).  The LSD algorithm first sorts the list by the least significant digit while preserving their relative order using a stable sort. Then it sorts them by the next digit, and so on from the least significant to the most significant, ending up with a sorted list. While the LSD radix sort requires the use of a stable sort, the MSD radix sort algorithm does not (unless stable sorting is desired).  In-place MSD radix sort is not stable.  It is common for the [counting sort](./Counting_sort) algorithm to be used internally by the radix sort.  A [hybrid](./Hybrid_algorithm) sorting approach, such as using [insertion sort](./Insertion_sort) for small bins, improves performance of radix sort significantly.

 

### Table of running times of popular algorithms

 

In [*Algorithms and Data Structures*](./Algorithms_+_Data_Structures_=_Programs) [Niklaus Wirth](./Niklaus_Wirth) gives a comparison of the running time of several of the popular algorithms on the [Lilith](./Lilith_(computer)) computer.[[31]](./Sorting_algorithm#cite_note-FOOTNOTEWirth1986100-31)

 
| Algorithm | Time (seconds) |
| --- | --- |
| Bubble sort | 128.84 |
| Shaker sort | 104.44 |
| Selection sort | 58.34 |
| Insertion sort | 50.74 |
| Binary insertion sort | 37.66 |
| Shell sort | 7.08 |
| Heap sort | 2.22 |
| Merge sort | 2.06 |
| Non-recursive quicksort | 1.32 |
| Recursive quicksort | 1.22 |

 

## Memory usage patterns and index sorting

 

When the size of the array to be sorted approaches or exceeds the available primary memory, so that (much slower) disk or swap space must be employed, the memory usage pattern of a sorting algorithm becomes important, and an algorithm that might have been fairly efficient when the array fit easily in RAM may become impractical. In this scenario, the total number of comparisons becomes (relatively) less important, and the number of times sections of memory must be copied or swapped to and from the disk can dominate the performance characteristics of an algorithm. Thus, the number of passes and the localization of comparisons can be more important than the raw number of comparisons, since comparisons of nearby elements to one another happen at [system bus](./Computer_bus) speed (or, with caching, even at [CPU](./CPU) speed), which, compared to disk speed, is virtually instantaneous.

 

For example, the popular recursive [quicksort](./Quicksort) algorithm provides quite reasonable performance with adequate RAM, but due to the recursive way that it copies portions of the array it becomes much less practical when the array does not fit in RAM, because it may cause a number of slow copy or move operations to and from disk. In that scenario, another algorithm may be preferable even if it requires more total comparisons.

 

One way to work around this problem, which works well when complex records (such as in a [relational database](./Relational_database)) are being sorted by a relatively small key field, is to create an index into the array and then sort the index, rather than the entire array. (A sorted version of the entire array can then be produced with one pass, reading from the index, but often even that is unnecessary, as having the sorted index is adequate.)  Because the index is much smaller than the entire array, it may fit easily in memory where the entire array would not, effectively eliminating the disk-swapping problem. This procedure is sometimes called "tag sort".[[32]](./Sorting_algorithm#cite_note-32)

 

Another technique for overcoming the memory-size problem is using [external sorting](./External_sorting), for example, one of the ways is to combine two algorithms in a way that takes advantage of the strength of each to improve overall performance. For instance, the array might be subdivided into chunks of a size that will fit in RAM, the contents of each chunk sorted using an efficient algorithm (such as [quicksort](./Quicksort)), and the results merged using a *k*-way merge similar to that used in [merge sort](./Merge_sort). This is faster than performing either merge sort or quicksort over the entire list.[[33]](./Sorting_algorithm#cite_note-33)[[34]](./Sorting_algorithm#cite_note-34)

 

Techniques can also be combined. For sorting very large sets of data that vastly exceed system memory, even the index may need to be sorted using an algorithm or combination of algorithms designed to perform reasonably with [virtual memory](./Virtual_memory), i.e., to reduce the amount of swapping required.

 

## Related algorithms

 

Related problems include [approximate sorting](./K-sorted_sequence#Algorithms) (sorting a sequence to within a certain [amount](./Rank_correlation) of the correct order), [partial sorting](./Partial_sorting) (sorting only the *k* smallest elements of a list, or finding the *k* smallest elements, but unordered) and [selection](./Selection_algorithm) (computing the *k*th smallest element). These can be solved inefficiently by a total sort, but more efficient algorithms exist, often derived by generalizing a sorting algorithm. The most notable example is [quickselect](./Quickselect), which is related to [quicksort](./Quicksort). Conversely, some sorting algorithms can be derived by repeated application of a selection algorithm; quicksort and quickselect can be seen as the same pivoting move, differing only in whether one recurses on both sides (quicksort, [divide-and-conquer](./Divide-and-conquer_algorithm)) or one side (quickselect, [decrease-and-conquer](./Decrease-and-conquer)).

 

A kind of opposite of a sorting algorithm is a [shuffling algorithm](./Shuffling_algorithm). These are fundamentally different because they require a source of random numbers. Shuffling can also be implemented by a sorting algorithm, namely by a random sort: assigning a random number to each element of the list and then sorting based on the random numbers. This is generally not done in practice, however, and there is a well-known simple and efficient algorithm for shuffling: the [Fisher–Yates shuffle](./Fisher–Yates_shuffle).

 

Sorting algorithms are ineffective for finding an order in many situations. Usually, when elements have no reliable comparison function (crowdsourced preferences like [voting systems](./Voting_systems)), comparisons are very costly ([sports](./Group_tournament_ranking_system)), or when it would be impossible to pairwise compare all elements for all criteria ([search engines](./Ranking_(information_retrieval))). In these cases, the problem is usually referred to as *ranking* and the goal is to find the "best" result for some criteria according to probabilities inferred from comparisons or rankings. A common example is in chess, where players are ranked with the [Elo rating system](./Elo_rating_system), and rankings are determined by a [tournament system](./Category:Tournament_systems) instead of a sorting algorithm.

 

There are sorting algorithms for a "noisy" (potentially incorrect) comparator and sorting algorithms for a pair of "fast and dirty" (i.e. "noisy") and "clean" comparators. This can be useful when the full comparison function is costly.[[35]](./Sorting_algorithm#cite_note-35)

 

## See also

 
- [Collation](./Collation) – Assembly of written information into a standard order
- [K-sorted sequence](./K-sorted_sequence)
- [Schwartzian transform](./Schwartzian_transform) – Programming idiom for efficiently sorting a list by a computed key
- [Search algorithm](./Search_algorithm) – Any algorithm which solves the search problem
- [Quantum sort](./Quantum_sort) – Sorting algorithms for quantum computers

 

## References

 
1. [↑](./Sorting_algorithm#cite_ref-refrigerator_1-0) ["Meet the 'Refrigerator Ladies' Who Programmed the ENIAC"](http://mentalfloss.com/article/53160/meet-refrigerator-ladies-who-programmed-eniac). *Mental Floss*. 2013-10-13. [Archived](https://web.archive.org/web/20181008094658/http://mentalfloss.com/article/53160/meet-refrigerator-ladies-who-programmed-eniac) from the original on 2018-10-08. Retrieved 2016-06-16.
2. [↑](./Sorting_algorithm#cite_ref-NYTimes_2-0) Lohr, Steve (Dec 17, 2001). ["Frances E. Holberton, 84, Early Computer Programmer"](https://www.nytimes.com/2001/12/17/business/frances-e-holberton-84-early-computer-programmer.html). NYTimes. [Archived](https://web.archive.org/web/20141216015437/http://www.nytimes.com/2001/12/17/business/frances-e-holberton-84-early-computer-programmer.html) from the original on 16 December 2014. Retrieved 16 December 2014.
3. [↑](./Sorting_algorithm#cite_ref-3) Demuth, Howard B. (1956). *Electronic Data Sorting* (PhD thesis). Stanford University. [ProQuest](./ProQuest) [301940891](https://www.proquest.com/docview/301940891).
4. [↑](./Sorting_algorithm#cite_ref-4) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009), "8", [*Introduction To Algorithms*](https://books.google.com/books?id=NLngYyWFl_YC) (3rd ed.), Cambridge, MA: The MIT Press, p. 167, [ISBN](./ISBN_(identifier)) [978-0-262-03293-3](./Special:BookSources/978-0-262-03293-3)
5. [↑](./Sorting_algorithm#cite_ref-5) [Ajtai, M.](./Miklós_Ajtai); [Komlós, J.](./János_Komlós_(mathematician)); [Szemerédi, E.](./Endre_Szemerédi) (1983). *An O(n log n) sorting network*. [STOC](./Symposium_on_Theory_of_Computing) '83. *Proceedings of the fifteenth annual ACM symposium on Theory of computing*. pp. 1–9. [doi](./Doi_(identifier)):[10.1145/800061.808726](https://doi.org/10.1145%2F800061.808726). [ISBN](./ISBN_(identifier)) [0-89791-099-0](./Special:BookSources/0-89791-099-0).
6. [↑](./Sorting_algorithm#cite_ref-6) Kim, P. S.; Kutzner, A. (2008). *Ratio Based Stable In-Place Merging*. [TAMC](./International_Conference_on_Theory_and_Applications_of_Models_of_Computation?action=edit&redlink=1) 2008. *Theory and Applications of Models of Computation*. [LNCS](./LNCS). Vol. 4978. pp. 246–257. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.330.2641](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.330.2641). [doi](./Doi_(identifier)):[10.1007/978-3-540-79228-4_22](https://doi.org/10.1007%2F978-3-540-79228-4_22). [ISBN](./ISBN_(identifier)) [978-3-540-79227-7](./Special:BookSources/978-3-540-79227-7).
7. [↑](./Sorting_algorithm#cite_ref-7) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1 September 1998). [*Algorithms In C: Fundamentals, Data Structures, Sorting, Searching, Parts 1-4*](https://books.google.com/books?id=ylAETlep0CwC) (3 ed.). Pearson Education. [ISBN](./ISBN_(identifier)) [978-81-317-1291-7](./Special:BookSources/978-81-317-1291-7). Retrieved 27 November 2012.
8. [↑](./Sorting_algorithm#cite_ref-sedgewickQsortPaper_8-0) [Sedgewick, R.](./Robert_Sedgewick_(computer_scientist)) (1978). "Implementing Quicksort programs". *[Comm. ACM](./Comm._ACM)*. **21** (10): 847–857. [doi](./Doi_(identifier)):[10.1145/359619.359631](https://doi.org/10.1145%2F359619.359631). [S2CID](./S2CID_(identifier)) [10020756](https://api.semanticscholar.org/CorpusID:10020756).
9. [↑](./Sorting_algorithm#cite_ref-9) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001), "8", [*Introduction To Algorithms*](https://books.google.com/books?id=NLngYyWFl_YC) (2nd ed.), Cambridge, MA: The MIT Press, p. 165, [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7)
10. [↑](./Sorting_algorithm#cite_ref-10) Nilsson, Stefan (2000). ["The Fastest Sorting Algorithm?"](http://www.drdobbs.com/architecture-and-design/the-fastest-sorting-algorithm/184404062). *[Dr. Dobb's](./Dr._Dobb's)*. [Archived](https://web.archive.org/web/20190608084350/http://www.drdobbs.com/architecture-and-design/the-fastest-sorting-algorithm/184404062) from the original on 2019-06-08. Retrieved 2015-11-23.
11. [1](./Sorting_algorithm#cite_ref-clrs_11-0) [2](./Sorting_algorithm#cite_ref-clrs_11-1) [3](./Sorting_algorithm#cite_ref-clrs_11-2) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
12. [1](./Sorting_algorithm#cite_ref-gt_12-0) [2](./Sorting_algorithm#cite_ref-gt_12-1) [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2002). "4.5 Bucket-Sort and Radix-Sort". *Algorithm Design: Foundations, Analysis, and Internet Examples*. John Wiley & Sons. pp. 241–243. [ISBN](./ISBN_(identifier)) [978-0-471-38365-9](./Special:BookSources/978-0-471-38365-9).
13. [↑](./Sorting_algorithm#cite_ref-Fun07_13-0) Gruber, H.; Holzer, M.; Ruepp, O. (2007), "Sorting the slow way: an analysis of perversely awful randomized sorting algorithms", [*4th International Conference on Fun with Algorithms, Castiglioncello, Italy, 2007*](http://www.hermann-gruber.com/pdf/fun07-final.pdf) (PDF), Lecture Notes in Computer Science, vol. 4475, Springer-Verlag, pp. 183–197, [doi](./Doi_(identifier)):[10.1007/978-3-540-72914-3_17](https://doi.org/10.1007%2F978-3-540-72914-3_17), [ISBN](./ISBN_(identifier)) [978-3-540-72913-6](./Special:BookSources/978-3-540-72913-6), [archived](https://web.archive.org/web/20200929161057/http://www.hermann-gruber.com/pdf/fun07-final.pdf) (PDF) from the original on 2020-09-29, retrieved 2020-06-27.
14. [1](./Sorting_algorithm#cite_ref-:0_14-0) [2](./Sorting_algorithm#cite_ref-:0_14-1) [Thorup, M.](./Mikkel_Thorup) (February 2002). "Randomized Sorting in O(n log log n) Time and Linear Space Using Addition, Shift, and Bit-wise Boolean Operations". *Journal of Algorithms*. **42** (2): 205–230. [doi](./Doi_(identifier)):[10.1006/jagm.2002.1211](https://doi.org/10.1006%2Fjagm.2002.1211). [S2CID](./S2CID_(identifier)) [9700543](https://api.semanticscholar.org/CorpusID:9700543).
15. [↑](./Sorting_algorithm#cite_ref-15) Andersson, Arne; Hagerup, Torben; Nilsson, Stefan; Raman, Rajeev (1995). "Sorting in linear time?". *Proceedings of the twenty-seventh annual ACM symposium on Theory of computing*. ACM. pp. 427–436.
16. [↑](./Sorting_algorithm#cite_ref-16) Han, Yijie; [Thorup, M.](./Mikkel_Thorup) (2002). *Integer sorting in O(n√(log log n)) expected time and linear space*. The 43rd Annual IEEE [Symposium on Foundations of Computer Science](./Symposium_on_Foundations_of_Computer_Science). pp. 135–144. [doi](./Doi_(identifier)):[10.1109/SFCS.2002.1181890](https://doi.org/10.1109%2FSFCS.2002.1181890). [ISBN](./ISBN_(identifier)) [0-7695-1822-2](./Special:BookSources/0-7695-1822-2).
17. [↑](./Sorting_algorithm#cite_ref-17) [Wirth, Niklaus](./Niklaus_Wirth) (1986). *Algorithms & Data Structures*. Upper Saddle River, NJ: Prentice-Hall. pp. 76–77. [ISBN](./ISBN_(identifier)) [978-0130220059](./Special:BookSources/978-0130220059).
18. [↑](./Sorting_algorithm#cite_ref-18) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), pp. 79–80
19. [↑](./Sorting_algorithm#cite_ref-19) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), pp. 101–102
20. [↑](./Sorting_algorithm#cite_ref-20) ["Tim Peters's original description of timsort"](http://svn.python.org/projects/python/trunk/Objects/listsort.txt). *python.org*. [Archived](https://web.archive.org/web/20180122024335/http://svn.python.org/projects/python/trunk/Objects/listsort.txt) from the original on 22 January 2018. Retrieved 14 April 2018.
21. [↑](./Sorting_algorithm#cite_ref-21) ["OpenJDK's TimSort.java"](https://web.archive.org/web/20110814013719/http://cr.openjdk.java.net/~martin/webrevs/openjdk7/timsort/raw_files/new/src/share/classes/java/util/TimSort.java). *java.net*. Archived from [the original](http://cr.openjdk.java.net/~martin/webrevs/openjdk7/timsort/raw_files/new/src/share/classes/java/util/TimSort.java) on 14 August 2011. Retrieved 14 April 2018.
22. [↑](./Sorting_algorithm#cite_ref-22) ["sort – perldoc.perl.org"](http://perldoc.perl.org/functions/sort.html). *perldoc.perl.org*. [Archived](https://web.archive.org/web/20180414233802/http://perldoc.perl.org/functions/sort.html) from the original on 14 April 2018. Retrieved 14 April 2018.
23. [↑](./Sorting_algorithm#cite_ref-mergesort_in_jdk13_23-0) [Merge sort in Java 1.3](http://java.sun.com/j2se/1.3/docs/api/java/util/Arrays.html#sort(java.lang.Object%5B%5D)), Sun. [Archived](https://web.archive.org/web/20090304021927/http://java.sun.com/j2se/1.3/docs/api/java/util/Arrays.html#sort(java.lang.Object%5B%5D)) 2009-03-04 at the [Wayback Machine](./Wayback_Machine)
24. [↑](./Sorting_algorithm#cite_ref-24) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), pp. 87–89
25. [↑](./Sorting_algorithm#cite_ref-25) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), p. 93
26. [↑](./Sorting_algorithm#cite_ref-26) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009), *Introduction to Algorithms* (3rd ed.), Cambridge, MA: The MIT Press, pp. 171–172, [ISBN](./ISBN_(identifier)) [978-0262033848](./Special:BookSources/978-0262033848)
27. [↑](./Sorting_algorithm#cite_ref-27) Musser, David R. (1997), "Introspective Sorting and Selection Algorithms", *Software: Practice and Experience*, **27** (8): 983–993, [doi](./Doi_(identifier)):[10.1002/(SICI)1097-024X(199708)27:8<983::AID-SPE117>3.0.CO;2-#](https://doi.org/10.1002%2F%28SICI%291097-024X%28199708%2927%3A8%3C983%3A%3AAID-SPE117%3E3.0.CO%3B2-%23)
28. [↑](./Sorting_algorithm#cite_ref-Shell_28-0) Shell, D. L. (1959). ["A High-Speed Sorting Procedure"](https://web.archive.org/web/20170830020037/http://penguin.ewu.edu/cscd300/Topic/AdvSorting/p30-shell.pdf) (PDF). *Communications of the ACM*. **2** (7): 30–32. [doi](./Doi_(identifier)):[10.1145/368370.368387](https://doi.org/10.1145%2F368370.368387). [S2CID](./S2CID_(identifier)) [28572656](https://api.semanticscholar.org/CorpusID:28572656). Archived from [the original](http://penguin.ewu.edu/cscd300/Topic/AdvSorting/p30-shell.pdf) (PDF) on 2017-08-30. Retrieved 2020-03-23.
29. [↑](./Sorting_algorithm#cite_ref-29) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), pp. 81–82
30. [↑](./Sorting_algorithm#cite_ref-BB_30-0) Brejová, B. (15 September 2001). "Analyzing variants of Shellsort". *[Inf. Process. Lett.](./Inf._Process._Lett.)* **79** (5): 223–227. [doi](./Doi_(identifier)):[10.1016/S0020-0190(00)00223-4](https://doi.org/10.1016%2FS0020-0190%2800%2900223-4).
31. [↑](./Sorting_algorithm#cite_ref-FOOTNOTEWirth1986100_31-0) [Wirth 1986](./Sorting_algorithm#CITEREFWirth1986), p. 100.
32. [↑](./Sorting_algorithm#cite_ref-32) ["tag sort Definition from PC Magazine Encyclopedia"](https://www.pcmag.com/encyclopedia_term/0%2C2542%2Ct%3Dtag+sort%26i%3D52532%2C00.asp). *Pcmag.com*. [Archived](https://web.archive.org/web/20121006015634/http://www.pcmag.com/encyclopedia_term/0%2C2542%2Ct%3Dtag+sort%26i%3D52532%2C00.asp) from the original on 6 October 2012. Retrieved 14 April 2018.
33. [↑](./Sorting_algorithm#cite_ref-33) [Donald Knuth](./Donald_Knuth), *[The Art of Computer Programming](./The_Art_of_Computer_Programming)*, Volume 3: *Sorting and Searching*, Second Edition. Addison-Wesley, 1998, [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0), Section 5.4: External Sorting, pp. 248–379.
34. [↑](./Sorting_algorithm#cite_ref-34) [Ellis Horowitz](./Ellis_Horowitz) and [Sartaj Sahni](./Sartaj_Sahni), *Fundamentals of Data Structures*, H. Freeman & Co., [ISBN](./ISBN_(identifier)) [0-7167-8042-9](./Special:BookSources/0-7167-8042-9).
35. [↑](./Sorting_algorithm#cite_ref-35) Bai, Xingjian; Coester, Christian (2023). [*Sorting with Predictions*](https://proceedings.neurips.cc/paper_files/paper/2023/hash/544696ef4847c903376ed6ec58f3a703-Abstract-Conference.html). NeurIPS. p. 5.

 

## Further reading

 
- [Knuth, Donald E.](./Donald_Knuth) (1998), *Sorting and Searching*, The Art of Computer Programming, vol. 3 (2nd ed.), Boston: Addison-Wesley, [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0)
- [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1980), ["Efficient Sorting by Computer: An Introduction"](https://archive.org/details/computationalpro00actu/page/101), *Computational Probability*, New York: Academic Press, pp. [101–130](https://archive.org/details/computationalpro00actu/page/101), [ISBN](./ISBN_(identifier)) [0-12-394680-8](./Special:BookSources/0-12-394680-8)

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm implementation](https://en.wikibooks.org/wiki/Algorithm%20implementation)* has a page on the topic of: ***[Sorting algorithms](https://en.wikibooks.org/wiki/Algorithm%20implementation/Sorting)***    [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[A-level Mathematics](https://en.wikibooks.org/wiki/A-level%20Mathematics)* has a page on the topic of: ***[Sorting algorithms](https://en.wikibooks.org/wiki/A-level%20Mathematics/OCR/D1/Algorithms#Sorting_Algorithms)***    [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Sorting algorithms](https://commons.wikimedia.org/wiki/Category:Sort%20algorithms).  
- [Sorting Algorithm Animations](https://web.archive.org/web/20150303022622/http://www.sorting-algorithms.com/) at the [Wayback Machine](./Wayback_Machine) (archived 3 March 2015).
- [Sequential and parallel sorting algorithms](https://www.iti.fh-flensburg.de/lang/algorithmen/sortieren/algoen.htm) – Explanations and analyses of many sorting algorithms.
- [Dictionary of Algorithms, Data Structures, and Problems](https://www.nist.gov/dads/) – Dictionary of algorithms, techniques, common functions, and problems.
- [Slightly Skeptical View on Sorting Algorithms](https://www.softpanorama.org/Algorithms/sorting.shtml) – Discusses several classic algorithms and promotes alternatives to the [quicksort](./Quicksort) algorithm.
- [15 Sorting Algorithms in 6 Minutes (Youtube)](https://www.youtube.com/watch?v=kPRA0W1kECg&t=0) – Visualization and "audibilization" of 15 Sorting Algorithms in 6 Minutes.
- [A036604 sequence in OEIS database titled "Sorting numbers: minimal number of comparisons needed to sort n elements"](https://oeis.org/A036604) – Performed by [Ford–Johnson algorithm](./Ford–Johnson_algorithm).
- [Sorting Algorithms Used on Famous Paintings (Youtube)](https://www.youtube.com/watch?v=d2d0r1bArUQ&t=0) – Visualization of Sorting Algorithms on Many Famous Paintings.
- [A Comparison of Sorting Algorithms](https://coderslegacy.com/comparison-of-sorting-algorithms/) – Runs a series of tests of 9 of the main sorting algorithms using Python timeit and [Google Colab](./Google_Colab).

 
| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |

| vteSorting algorithms |
| --- |
| Theory | Computational complexity theoryBig O notationTotal orderListsInplacementStabilityComparison sortAdaptive sortSorting networkInteger sortingX + Y sortingTransdichotomous modelQuantum sort |
| Exchange sorts | Bubble sortCocktail shaker sortOdd–even sortComb sortGnome sortProportion extend sortQuicksort |
| Selection sorts | Selection sortHeapsortSmoothsortCartesian tree sortTournament sortCycle sortWeak-heap sort |
| Insertion sorts | Insertion sortShellsortSplaysortTree sortLibrary sortPatience sorting |
| Merge sorts | Merge sortCascade merge sortOscillating merge sortPolyphase merge sort |
| Distribution sorts | American flag sortBead sortBucket sortBurstsortCounting sortInterpolation sortPigeonhole sortProxmap sortRadix sortFlashsort |
| Concurrentsorts | Bitonic sorterBatcher odd–even mergesortPairwise sorting networkSamplesort |
| Hybrid sorts | Block merge sortIntrosortKirkpatrick–Reisch sortMerge-insertion sortPowersortTimsortSpreadsort |
| Other | Topological sortingPre-topological orderPancake sortingSpaghetti sort |
| Impractical sorts | Stooge sortSlowsortBogosort |