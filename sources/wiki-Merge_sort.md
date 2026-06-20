---
source: https://en.wikipedia.org/wiki/Merge_sort
fetched: 2026-06-19
---

Divide and conquer sorting algorithm 
| An example of merge sort. First, divide the list into the smallest unit (1 element), then compare each element with the adjacent list to sort and merge the two adjacent lists. Finally, all the elements are sorted and merged. |
| --- |
| Class | Sorting algorithm |
| Data structure | Array |
| Worst-caseperformance | O(nlog⁡n){\displaystyle O(n\log n)} |
| Best-caseperformance | Ω(nlog⁡n){\displaystyle \Omega (n\log n)}typical,Ω(n){\displaystyle \Omega (n)}natural variant |
| Averageperformance | Θ(nlog⁡n){\displaystyle \Theta (n\log n)} |
| Worst-casespace complexity | O(n){\displaystyle O(n)}total withO(n){\displaystyle O(n)}auxiliary,O(1){\displaystyle O(1)}auxiliary with linked lists[1] |

 

**Merge sort** (also commonly spelled as **mergesort** or **merge-sort**[[2]](./Merge_sort#cite_note-goodrich12-2)) is an efficient, general-purpose, [comparison](./Comparison_sort)-based [sorting algorithm](./Sorting_algorithm). Most implementations of merge sort are [stable](./Sorting_algorithm#Stability), which means that the relative order of equal elements is the same between the input and output. Merge sort is a [divide-and-conquer algorithm](./Divide-and-conquer_algorithm) that was invented by [John von Neumann](./John_von_Neumann) in 1945.[[3]](./Merge_sort#cite_note-3) A detailed description and analysis of bottom-up merge sort appeared in a report by [Goldstine](./Herman_Goldstine) and von Neumann as early as 1948.[[4]](./Merge_sort#cite_note-4)

 

## Algorithm

 

Conceptually, a merge sort works as follows:

 
1. Divide the unsorted list into *n* sub-lists, each containing one element (a list of one element is considered sorted).
2. Repeatedly [merge](./Merge_algorithm) sublists to produce new sorted sublists until there is only one sublist remaining.  This will be the sorted list.

 

Merge sort is efficient because merging and sorting two sublists can be performed in linear time, provided that the sublists are already sorted.

 

### Top-down implementation

 

Example [C-like](./C-like) code using indices for top-down merge sort algorithm that recursively splits the list into sublists (called *runs* in this example) until sublist size is 1, then merges those sublists to produce a sorted list. The copy back step is avoided with alternating the direction of the merge with each level of recursion (except for an initial one-time copy, that can be avoided too). 

 

As a simple example, consider an array with two elements. The elements are copied to `b`, then merged back to `a`. If there are four elements, when the bottom of the recursion level is reached, single element runs from `a` are merged to `b`, and then at the next higher level of recursion, those two-element runs are merged to `a`. This pattern continues with each level of recursion.

 
```
// Copy a section of the array a into array b (from begin to end - 1)
void copyArray(int[] a, int begin, int end, int[] b) {
    for (int k = begin; k < end; ++k) {
        b[k] = a[k];
    }
}

// Merge two sorted halves (from a) into a single sorted run (into b)
void topDownMerge(int[] a, int begin, int middle, int end, int[] b) {
    int i = begin;
    int j = middle;

    // Merge the two sorted runs into b
    for (int k = begin; k < end; ++k) {
        if (i < middle && (j >= end || a[i] <= a[j])) {
            b[k] = a[i]; // Take element from the left run
            i++;
        } else {
            b[k] = a[j]; // Take element from the right run
            j++;
        }
    }
}

// Split the array a into two halves, sort both halves into b,
// and merge the sorted halves back into a
void topDownSplitMerge(int[] a, int begin, int end, int[] b) {
    if (end - begin <= 1) {
        return; // Base case: Run size is 1, so it's already sorted
    }

    int middle = (begin + end) / 2;  // Find the midpoint to split the array

    // Recursively sort the left and right halves into b
    topDownSplitMerge(b, begin, middle, a);
    topDownSplitMerge(b, middle, end, a);

    // Merge the sorted halves back into a
    topDownMerge(b, begin, middle, end, a);
}

void topDownMergeSort(int[] a, int[] b, int n) {
    // Copy the entire array a into b initially
    copyArray(a, 0, n, b);
    // Recursively split and merge the array b into a
    topDownSplitMerge(a, 0, n, b);
}

```
 

Sorting the entire array is accomplished by topDownMergeSort(a, b, a.length).

 

### Bottom-up implementation

 

Example C-like code using indices for bottom-up merge sort algorithm which treats the list as an array of *n* sublists (called *runs* in this example) of size 1, and iteratively merges sub-lists back and forth between two buffers:

 
```
// Copy array b into array a
void copyArray(int[] b, int[] a, int n) {
    for (int i = 0; i < n; i++) {
        a[i] = b[i];
    }
}

// Left run is a[left : right-1].
// Right run is a[right : end-1].
void bottomUpMerge(int[] a, int left, int right, int end, int[] b) {
    int i = left;
    int j = right;

    // While there are elements in the left or right runs...
    for (int k = left; k < end; ++k) {
        // If left run head exists and is <= existing right run head.
        if (i < right && (j >= end || a[i] <= a[j])) {
            b[k] = a[i];
            i = i + 1;
        } else {
            b[k] = a[j];
            j = j + 1;    
        }
    }
}

void bottomUpMergeSort(int[] a, int[] b, int n) {
    // Each 1-element run in a is already "sorted".
    // Make successively longer sorted runs of length 2, 4, 8, 16... until the whole array is sorted.
    for (int width = 1; width < n; width *= 2) {
        // Array a is full of runs of length width.
        for (int i = 0; i < n; i = i + 2 * width) {
            // Merge two runs: a[i:i+width-1] and a[i+width:i+2*width-1] to b[]
            // or copy a[i:n-1] to b[] (if (i+width >= n))
            bottomUpMerge(a, i, Math.min(i + width, n), Math.min(i + 2 * width, n), b);
        }
        // Now work array b is full of runs of length 2 * width.
        // Copy array b to array a for the next iteration.
        // A more efficient implementation would swap the roles of a and b.
        copyArray(b, a, n);
    }
}

```
 

### Top-down implementation using lists

 

[Pseudocode](./Pseudocode) for top-down merge sort algorithm which recursively divides the input list into smaller sublists until the sublists are trivially sorted, and then merges the sublists while returning up the call chain.

 
```
function merge_sort(list m) is
    // Base case. A list of zero or one elements is sorted, by definition.
    if length of m ≤ 1 then
        return m

    // Recursive case. First, divide the list into equal-sized sublists
    // consisting of the first half and second half of the list.
    // This assumes lists start at index 0.
    var left := empty list
    var right := empty list
    for each x with index i in m do
        if i < (length of m)/2 then
            add x to left
        else
            add x to right

    // Recursively sort both sublists.
    left := merge_sort(left)
    right := merge_sort(right)

    // Then merge the now-sorted sublists.
    return merge(left, right)
```
 

In this example, the merge function merges the left and right sublists.

 
```
function merge(left, right) is
    var result := empty list

    while left is not empty and right is not empty do
        if first(left) ≤ first(right) then
            append first(left) to result
            left := rest(left)
        else
            append first(right) to result
            right := rest(right)

    // Either left or right may have elements left; consume them.
    // (Only one of the following loops will actually be entered.)
    while left is not empty do
        append first(left) to result
        left := rest(left)
    while right is not empty do
        append first(right) to result
        right := rest(right)
    return result
```
 

### Bottom-up implementation using lists

 

[Pseudocode](./Pseudocode) for bottom-up merge sort algorithm which uses a small fixed size array of references to nodes, where `array[i]` is either a reference to a list of size 2*i* or *[nil](./Null_pointer)*. *node* is a reference or pointer to a node. The `merge()` function would be similar to the one shown in the top-down merge lists example, it merges two already sorted lists, and handles empty lists. In this case, `merge()` would use *node* for its input parameters and return value.

 
```
function merge_sort(node head) is
    // return if empty list
    if head = nil then
        return nil
    var node array[32]; initially all nil
    var node result
    var node next
    var int  i
    result := head
    // merge nodes into array
    while result ≠ nil do
        next := result.next;
        result.next := nil
        for (i = 0; (i < 32) && (array[i] ≠ nil); i += 1) do
            result := merge(array[i], result)
            array[i] := nil
        // do not go past end of array
        if i = 32 then
            i -= 1
        array[i] := result
        result := next
    // merge array into single list
    result := nil
    for (i = 0; i < 32; i += 1) do
        result := merge(array[i], result)
    return result
```
 

### Top-down implementation in a declarative style

 

[Haskell](./Haskell)-like pseudocode, showing how merge sort can be implemented in such a language using constructs and ideas from [functional programming](./Functional_programming).

 
```
mergeSort :: Ord a => [a] -> [a]
mergeSort []  = []
mergeSort [x] = [x]
mergeSort xs  = merge (mergeSort l, mergeSort r)
  where (l, r) = splitAt (length xs `div` 2) xs

merge :: Ord a => ([a], [a]) -> [a]
merge ([], xs) = xs
merge (xs, []) = xs
merge (x:xs, y:ys) | x <= y    = x : merge(xs, y:ys)
                   | otherwise = y : merge(x:xs, ys)

```
 

## Analysis

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Merge_sort_algorithm_diagram.svg/500px-Merge_sort_algorithm_diagram.svg.png)](./File:Merge_sort_algorithm_diagram.svg)A recursive merge sort algorithm used to sort an array of 7 integer values. These are the steps a human would take to emulate merge sort (top-down). 

In sorting *n* objects, merge sort has an [average](./Average_performance) and [worst-case performance](./Worst-case_performance) of [O](./Big_O_notation)(*n* log *n*) comparisons. If the running time (number of comparisons) of merge sort for a list of length *n* is *T*(*n*), then the [recurrence relation](./Recurrence_relation) *T*(*n*) = 2*T*(*n*/2) + *n* follows from the definition of the algorithm (apply the algorithm to two lists of half the size of the original list, and add the *n* steps taken to merge the resulting two lists).[[5]](./Merge_sort#cite_note-5) The closed form follows from the [master theorem for divide-and-conquer recurrences](./Master_theorem_(analysis_of_algorithms)).

 

The number of comparisons made by merge sort in the worst case is given by the [sorting numbers](./Sorting_number). These numbers are equal to or slightly smaller than (*n* ⌈[lg](./Binary_logarithm) *n*⌉ − 2⌈lg *n*⌉ + 1), which is between (*n* lg *n* − *n* + 1) and (*n* lg *n* + *n* + O(lg *n*)).[[6]](./Merge_sort#cite_note-6) Merge sort's best case takes about half as many iterations as its worst case.[[7]](./Merge_sort#cite_note-:1-7)

 

For large *n* and a randomly ordered input list, merge sort's expected (average) number of comparisons approaches *α*·*n* fewer than the worst case, where     α α  = − −  1 +  ∑ ∑   k = 0   ∞ ∞      1   2  k   + 1    ≈ ≈  0.2645.   {\displaystyle \alpha =-1+\sum _{k=0}^{\infty }{\frac {1}{2^{k}+1}}\approx 0.2645.}  ![{\displaystyle \alpha =-1+\sum _{k=0}^{\infty }{\frac {1}{2^{k}+1}}\approx 0.2645.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d26965fea07d841c85071c791f70ba88a721f280)

 

In the *worst* case, merge sort uses approximately 39% fewer comparisons than [quicksort](./Quicksort) does in its *average* case, and in terms of moves, merge sort's worst case complexity is [O](./Big_O_notation)(*n* log *n*) - the same complexity as quicksort's best case.[[7]](./Merge_sort#cite_note-:1-7)

 

Merge sort is more efficient than quicksort for some types of lists if the data to be sorted can only be efficiently accessed sequentially, and is thus popular in languages such as [Lisp](./Lisp_programming_language), where sequentially accessed data structures are very common. Unlike some (efficient) implementations of quicksort, merge sort is a stable sort.

 

Merge sort's most common implementation does not sort in place;[[8]](./Merge_sort#cite_note-8) therefore, the memory size of the input must be allocated for the sorted output to be stored in (see below for variations that need only *n*/2 extra spaces).

 

## Natural merge sort

 

A natural merge sort is similar to a bottom-up merge sort except that any naturally occurring [runs](./Run_of_a_sequence) (sorted sequences) in the input are exploited. Both monotonic and bitonic (alternating up/down) runs may be exploited, with lists (or equivalently tapes or files) being convenient data structures (used as [FIFO queues](./Queue_(abstract_data_type)) or [LIFO stacks](./Stack_(abstract_data_type))).[[9]](./Merge_sort#cite_note-9) In the bottom-up merge sort, the starting point assumes each run is one item long. In practice, random input data will have many short runs that just happen to be sorted. In the typical case, the natural merge sort may not need as many passes because there are fewer runs to merge. In the best case, the input is already sorted (i.e., is one run), so the natural merge sort need only make one pass through the data. In many practical cases, long natural runs are present, and for that reason natural merge sort is exploited as the key component of [Timsort](./Timsort). Example:

 
```
Start       :  3  4  2  1  7  5  8  9  0  6
Select runs : (3  4)(2)(1  7)(5  8  9)(0  6)
Merge       : (2  3  4)(1  5  7  8  9)(0  6)
Merge       : (1  2  3  4  5  7  8  9)(0  6)
Merge       : (0  1  2  3  4  5  6  7  8  9)
```
 

Formally, the natural merge sort is said to be [Runs](./M-optimal_sorting?action=edit&redlink=1)-optimal, where       R u n s   ( L )   {\displaystyle {\mathtt {Runs}}(L)}  ![{\displaystyle {\mathtt {Runs}}(L)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/66368efa089c48a2a1fcbd6d7655a258a135dd11) is the number of runs in     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8), minus one.

 

[Tournament replacement selection sorts](./Tournament_sort) are used to gather the initial runs for external sorting algorithms.

 

## Ping-pong merge sort

 

Instead of merging two blocks at a time, a ping-pong merge merges four blocks at a time. The four sorted blocks are merged simultaneously to auxiliary space into two sorted blocks, then the two sorted blocks are merged back to main memory. Doing so omits the copy operation and reduces the total number of moves by half. An early public domain implementation of a four-at-once merge was by WikiSort in 2014, the method was later that year described as an optimization for [patience sorting](./Patience_sorting) and named a ping-pong merge.[[10]](./Merge_sort#cite_note-wikisort-10)[[11]](./Merge_sort#cite_note-11) Quadsort implemented the method in 2020 and named it a quad merge.[[12]](./Merge_sort#cite_note-quadsort-12)

 

## In-place merge sort

 

One drawback of merge sort, when implemented on arrays, is its *O*(*n*) working memory requirement. Several methods to reduce memory or make merge sort fully [in-place](./In-place_algorithm) have been suggested:

 
- [Kronrod (1969)](./Merge_sort#CITEREFKronrod1969) suggested an alternative version of merge sort that uses constant additional space.
- Katajainen *et al.* present an algorithm that requires a constant amount of working memory: enough storage space to hold one element of the input array, and additional space to hold *O*(1) pointers into the input array. They achieve an *O*(*n* log *n*) time bound with small constants, but their algorithm is not stable.[[13]](./Merge_sort#cite_note-13)
- Several attempts have been made at producing an *in-place merge* algorithm that can be combined with a standard (top-down or bottom-up) merge sort to produce an in-place merge sort. In this case, the notion of "in-place" can be relaxed to mean "taking logarithmic stack space", because standard merge sort requires that amount of space for its own stack usage. It was shown by Geffert *et al.* that in-place, stable merging is possible in *O*(*n* log *n*) time using a constant amount of scratch space, but their algorithm is complicated and has high constant factors: merging arrays of length n and m can take 5*n* + 12*m* + *o*(*m*) moves.[[14]](./Merge_sort#cite_note-14) This high constant factor and complicated in-place algorithm was made simpler and easier to understand. Bing-Chao Huang and Michael A. Langston[[15]](./Merge_sort#cite_note-Research_Contributions-15) presented a straightforward linear time algorithm *practical in-place merge* to merge a sorted list using fixed amount of additional space. They both have used the work of Kronrod and others. It merges in linear time and constant extra space. The algorithm takes little more average time than standard merge sort algorithms, free to exploit *O*(*n*) temporary extra memory cells, by less than a factor of two. Though the algorithm is much faster in a practical way, it is unstable for some lists. But using similar concepts, they have been able to solve this problem. Other in-place algorithms include SymMerge, which takes *O*((*n* + *m*) log (*n* + *m*)) time in total and is stable.[[16]](./Merge_sort#cite_note-16) Plugging such an algorithm into merge sort increases its complexity to the non-[linearithmic](./Linearithmic), but still [quasilinear](./Quasilinear_time), *O*(*n* (log *n*)2).
- Many applications of [external sorting](./External_sorting) use a form of merge sorting where the input gets split up to a higher number of sublists, ideally to a number for which merging them still makes the currently processed set of [pages](./Page_(computer_memory)) fit into main memory.
- A modern stable, linear, and in-place merge variant is [block merge sort](./Block_merge_sort), which creates a section of unique values to use as swap space.
- The space overhead can be reduced to *O*(√*n*) by using binary searches and rotations.[[17]](./Merge_sort#cite_note-17) This method is employed by the C++ STL library and quadsort.[[12]](./Merge_sort#cite_note-quadsort-12)
- An alternative to reduce the copying into multiple lists is to associate a new field of information with each key (the elements in *m* are called keys). This field will be used to link the keys and any associated information together in a sorted list (a key and its related information is called a record). Then the merging of the sorted lists proceeds by changing the link values; no records need to be moved at all. A field which contains only a link will generally be smaller than an entire record so less space will also be used. This is a standard sorting technique, not restricted to merge sort.
- A simple way to reduce the space overhead to *n*/2 is to maintain *left* and *right* as a combined structure, copy only the *left* part of *m* into temporary space, and to direct the *merge* routine to place the merged output into *m*. With this version it is better to allocate the temporary space outside the *merge* routine, so that only one allocation is needed. The excessive copying mentioned previously is also mitigated, since the last pair of lines before the *return result* statement (function * merge *in the pseudo code above) become superfluous.

 

## Use with tape drives

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6c/IBM_729_Tape_Drives.nasa.jpg/250px-IBM_729_Tape_Drives.nasa.jpg)](./File:IBM_729_Tape_Drives.nasa.jpg)Merge sort type algorithms allowed large data sets to be sorted on early computers that had small random access memories by modern standards. Records were stored on [magnetic tape](./Magnetic_tape) and processed on banks of magnetic tape drives, such as these [IBM 729s](./IBM_729). 

An [external](./External_sorting) merge sort is practical to run using [disk](./Disk_storage) or [tape](./Tape_drive) drives when the data to be sorted is too large to fit into [memory](./Primary_storage). [External sorting](./External_sorting) explains how merge sort is implemented with disk drives. A typical tape drive sort uses four tape drives. All I/O is sequential (except for rewinds at the end of each pass). A minimal implementation can get by with just two record buffers and a few program variables.

 

Naming the four tape drives as A, B, C, D, with the original data on A, and using only two record buffers, the algorithm is similar to [the bottom-up implementation](./Merge_sort#Bottom-up_implementation), using pairs of tape drives instead of arrays in memory. The basic algorithm can be described as follows:

 
1. Merge pairs of records from A; writing two-record sublists alternately to C and D.
2. Merge two-record sublists from C and D into four-record sublists; writing these alternately to A and B.
3. Merge four-record sublists from A and B into eight-record sublists; writing these alternately to C and D
4. Repeat until you have one list containing all the data, sorted—in log2(*n*) passes.

 

Instead of starting with very short runs, usually a [hybrid algorithm](./Hybrid_algorithm) is used, where the initial pass will read many records into memory, do an internal sort to create a long run, and then distribute those long runs onto the output set. The step avoids many early passes. For example, an internal sort of 1024 records will save nine passes. The internal sort is often large because it has such a benefit. In fact, there are techniques that can make the initial runs longer than the available internal memory. One of them, the Knuth's 'snowplow' (based on a [binary min-heap](./Binary_heap)), generates runs twice as long (on average) as a size of memory used.[[18]](./Merge_sort#cite_note-18)

 

With some overhead, the above algorithm can be modified to use three tapes. *O*(*n* log *n*) running time can also be achieved using two [queues](./Queue_(abstract_data_type)), or a [stack](./Stack_(abstract_data_type)) and a queue, or three stacks. In the other direction, using *k* > two tapes (and *O*(*k*) items in memory), we can reduce the number of tape operations in *O*(log *k*) times by using a [k/2-way merge](./K-way_merge_algorithm).

 

A more sophisticated merge sort that optimizes tape (and disk) drive usage is the [polyphase merge sort](./Polyphase_merge_sort).

 

## Optimizing merge sort

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Merge_sort_animation2.gif/250px-Merge_sort_animation2.gif)](./File:Merge_sort_animation2.gif)Tiled merge sort applied to an array of random integers.  The horizontal axis is the array index and the vertical axis is the integer. 

On modern computers, [locality of reference](./Locality_of_reference) can be of paramount importance in [software optimization](./Software_optimization), because multilevel [memory hierarchies](./Memory_hierarchy) are used. [Cache](./Cache_(computing))-aware versions of the merge sort algorithm, whose operations have been specifically chosen to minimize the movement of pages in and out of a machine's memory cache, have been proposed. For example, the **tiled merge sort** algorithm stops partitioning subarrays when subarrays of size S are reached, where S is the number of data items fitting into a CPU's cache. Each of these subarrays is sorted with an in-place sorting algorithm such as [insertion sort](./Insertion_sort), to discourage memory swaps, and normal merge sort is then completed in the standard recursive fashion. This algorithm has demonstrated better performance[*[example needed](./Wikipedia:AUDIENCE)*] on machines that benefit from cache optimization. ([LaMarca & Ladner 1997](./Merge_sort#CITEREFLaMarcaLadner1997))

 

## Parallel merge sort

 

Merge sort parallelizes well due to the use of the [divide-and-conquer](./Divide-and-conquer_algorithm) method. Several different parallel variants of the algorithm have been developed over the years. Some parallel merge sort algorithms are strongly related to the sequential top-down merge algorithm while others have a different general structure and use the [K-way merge](./K-way_merge_algorithm) method.

 

### Merge sort with parallel recursion

 

The sequential merge sort procedure can be described in two phases, the divide phase and the merge phase. The first consists of many recursive calls that repeatedly perform the same division process until the subsequences are trivially sorted (containing one or no element). An intuitive approach is the parallelization of those recursive calls.[[19]](./Merge_sort#cite_note-clrs-19) Following pseudocode describes the merge sort with parallel recursion using the [fork and join](./Fork–join_model) keywords:

 
```
// Sort elements lo through hi (exclusive) of array A.
algorithm mergesort(A, lo, hi) is
    if lo+1 < hi then  // Two or more elements.
        mid := ⌊(lo + hi) / 2⌋
        fork mergesort(A, lo, mid)
        mergesort(A, mid, hi)
        join
        merge(A, lo, mid, hi)
```
 

This algorithm is the trivial modification of the sequential version and does not parallelize well. Therefore, its speedup is not very impressive. It has a [span](./Analysis_of_parallel_algorithms#Overview) of     Θ Θ  ( n )   {\displaystyle \Theta (n)}  ![{\displaystyle \Theta (n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a6351206e27071559aa4472579095994f650d76b), which is only an improvement of     Θ Θ  ( log ⁡ ⁡  n )   {\displaystyle \Theta (\log n)}  ![{\displaystyle \Theta (\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65bac5223de9c91eb3e89a032b5c51fd3041dc66) compared to the sequential version (see [Introduction to Algorithms](./Introduction_to_Algorithms)). This is mainly due to the sequential merge method, as it is the bottleneck of the parallel executions.

 

### Merge sort with parallel merging

 Main article: [Merge algorithm § Parallel merge](./Merge_algorithm#Parallel_merge) 

Better parallelism can be achieved by using a parallel [merge algorithm](./Merge_algorithm). [Cormen et al.](./Introduction_to_Algorithms) present a binary variant that merges two sorted sub-sequences into one sorted output sequence.[[19]](./Merge_sort#cite_note-clrs-19)

 

In one of the sequences (the longer one if unequal length), the element of the middle index is selected. Its position in the other sequence is determined in such a way that this sequence would remain sorted if this element were inserted at this position. Thus, one knows how many other elements from both sequences are smaller and the position of the selected element in the output sequence can be calculated. For the partial sequences of the smaller and larger elements created in this way, the merge algorithm is again executed in parallel until the base case of the recursion is reached.

 

The following pseudocode shows the modified parallel merge sort method using the parallel merge algorithm (adopted from Cormen et al.).

 
```
/**
 * A: Input array
 * B: Output array
 * lo: lower bound
 * hi: upper bound
 * off: offset
 */
algorithm parallelMergesort(A, lo, hi, B, off) is
    len := hi - lo + 1
    if len == 1 then
        B[off] := A[lo]
    else let T[1..len] be a new array
        mid := ⌊(lo + hi) / 2⌋ 
        mid' := mid - lo + 1
        fork parallelMergesort(A, lo, mid, T, 1)
        parallelMergesort(A, mid + 1, hi, T, mid' + 1) 
        join 
        parallelMerge(T, 1, mid', mid' + 1, len, B, off)
```
 

In order to analyze a [recurrence relation](./Recurrence_relation) for the worst case span, the recursive calls of parallelMergesort have to be incorporated only once due to their parallel execution, obtaining

 

     T  ∞ ∞    sort   ( n ) =  T  ∞ ∞    sort    (   n 2   )  +  T  ∞ ∞    merge   ( n ) =  T  ∞ ∞    sort    (   n 2   )  + Θ Θ   (  log ⁡ ⁡  ( n  )  2    )  .   {\displaystyle T_{\infty }^{\text{sort}}(n)=T_{\infty }^{\text{sort}}\left({\frac {n}{2}}\right)+T_{\infty }^{\text{merge}}(n)=T_{\infty }^{\text{sort}}\left({\frac {n}{2}}\right)+\Theta \left(\log(n)^{2}\right).}  ![{\displaystyle T_{\infty }^{\text{sort}}(n)=T_{\infty }^{\text{sort}}\left({\frac {n}{2}}\right)+T_{\infty }^{\text{merge}}(n)=T_{\infty }^{\text{sort}}\left({\frac {n}{2}}\right)+\Theta \left(\log(n)^{2}\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/446e2e4f5e489271939d8eaf24fe315299c68b39)

 

For detailed information about the complexity of the parallel merge procedure, see [Merge algorithm](./Merge_algorithm#Parallel_merge).

 

The solution of this recurrence is given by

 

     T  ∞ ∞    sort   = Θ Θ   (  log ⁡ ⁡  ( n  )  3    )  .   {\displaystyle T_{\infty }^{\text{sort}}=\Theta \left(\log(n)^{3}\right).}  ![{\displaystyle T_{\infty }^{\text{sort}}=\Theta \left(\log(n)^{3}\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a94802e3df993101e31fb68df8651ed02c3be6ba)

 

This parallel merge algorithm reaches a parallelism of     Θ Θ   (   n  ( log ⁡ ⁡  n  )  2      )    {\textstyle \Theta \left({\frac {n}{(\log n)^{2}}}\right)}  ![{\textstyle \Theta \left({\frac {n}{(\log n)^{2}}}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aab65e96974269e9cda055c76ee6fe65d514cc81), which is much higher than the parallelism of the previous algorithm. Such a sort can perform well in practice when combined with a fast stable sequential sort, such as [insertion sort](./Insertion_sort), and a fast sequential merge as a base case for merging small arrays.[[20]](./Merge_sort#cite_note-20)

 

### Parallel multiway merge sort

 

It seems arbitrary to restrict the merge sort algorithms to a binary merge method, since there are usually p > 2 processors available. A better approach may be to use a [K-way merge](./K-way_merge_algorithm) method, a generalization of binary merge, in which     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) sorted sequences are merged. This merge variant is well suited to describe a sorting algorithm on a [PRAM](./Parallel_random-access_machine).[[21]](./Merge_sort#cite_note-21)[[22]](./Merge_sort#cite_note-:0-22)

 

#### Basic idea

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/44/Parallel_multiway_mergesort_process.svg/250px-Parallel_multiway_mergesort_process.svg.png)](./File:Parallel_multiway_mergesort_process.svg)The parallel multiway mergesort process on four processors      t  0     {\displaystyle t_{0}}  ![{\displaystyle t_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/02d3006c4190b1939b04d9b9bb21006fb4e6fa4a) to      t  3     {\displaystyle t_{3}}  ![{\displaystyle t_{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c62226a0dd66a3f9ad5706a365227331d9acb3a5). 

Given an unsorted sequence of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) elements, the goal is to sort the sequence with     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) available [processors](./Processor_(computing)). These elements are distributed equally among all processors and sorted locally using a sequential [Sorting algorithm](./Sorting_algorithm). Hence, the sequence consists of sorted sequences      S  1   , . . . ,  S  p     {\displaystyle S_{1},...,S_{p}}  ![{\displaystyle S_{1},...,S_{p}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d98b2999fbd2e6c533f76352b09fcece9316eaeb) of length     ⌈ ⌈    n p   ⌉ ⌉    {\textstyle \lceil {\frac {n}{p}}\rceil }  ![{\textstyle \lceil {\frac {n}{p}}\rceil }](https://wikimedia.org/api/rest_v1/media/math/render/svg/bef0b6fc196a5bc2a13e5b4e3d8651aac7bd223a). For simplification let     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) be a multiple of     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36), so that      |  S  i   |  =   n p     {\textstyle \left\vert S_{i}\right\vert ={\frac {n}{p}}}  ![{\textstyle \left\vert S_{i}\right\vert ={\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c7e37b02a3bcf6753d826a37c6311d7e6bb28516) for     i = 1 , . . . , p   {\displaystyle i=1,...,p}  ![{\displaystyle i=1,...,p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/97b53491bcccafe28753dede0d028ac1c1a410f6).

 

These sequences will be used to perform a multisequence selection/splitter selection. For     j = 1 , . . . , p   {\displaystyle j=1,...,p}  ![{\displaystyle j=1,...,p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/80fcb44828f4dfb719a067fd2ae1994d420e766f), the algorithm determines splitter elements      v  j     {\displaystyle v_{j}}  ![{\displaystyle v_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/73fffa4919c0d6268f6a8d9f38c04dd3296fd0a5) with global rank     k = j   n p     {\textstyle k=j{\frac {n}{p}}}  ![{\textstyle k=j{\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cba929233aee2ac6ab9083d8ffcf058ea71911b8). Then the corresponding positions of      v  1   , . . . ,  v  p     {\displaystyle v_{1},...,v_{p}}  ![{\displaystyle v_{1},...,v_{p}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5cad190648d7abe67b700e89cac90bbb02093a09) in each sequence      S  i     {\displaystyle S_{i}}  ![{\displaystyle S_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de6e810a93f67802ecb603ee0e3324005c6e583e) are determined with [binary search](./Binary_search_algorithm) and thus the      S  i     {\displaystyle S_{i}}  ![{\displaystyle S_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de6e810a93f67802ecb603ee0e3324005c6e583e) are further partitioned into     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) subsequences      S  i , 1   , . . . ,  S  i , p     {\displaystyle S_{i,1},...,S_{i,p}}  ![{\displaystyle S_{i,1},...,S_{i,p}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7e884989ab2180d064afea30f277951fcc912adc) with      S  i , j   := { x ∈ ∈   S  i    |  r a n k (  v  j − −  1   ) < r a n k ( x ) ≤ ≤  r a n k (  v  j   ) }   {\textstyle S_{i,j}:=\{x\in S_{i}|rank(v_{j-1})<rank(x)\leq rank(v_{j})\}}  ![{\textstyle S_{i,j}:=\{x\in S_{i}|rank(v_{j-1})<rank(x)\leq rank(v_{j})\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ae257169fe55b3307bb4bb0dbd6c67d4402d2a09).

 

Furthermore, the elements of      S  1 , i   , . . . ,  S  p , i     {\displaystyle S_{1,i},...,S_{p,i}}  ![{\displaystyle S_{1,i},...,S_{p,i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f7fbb5e7ae2ed94a4edf5b43f1ac51538e2c1649) are assigned to processor     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), means all elements between rank     ( i − −  1 )   n p     {\textstyle (i-1){\frac {n}{p}}}  ![{\textstyle (i-1){\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5023faab84d4ba6ae405b5db354af11d49486dcb) and rank     i   n p     {\textstyle i{\frac {n}{p}}}  ![{\textstyle i{\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b073387bac8e266ad41c94078ca2df206d8593a1), which are distributed over all      S  i     {\displaystyle S_{i}}  ![{\displaystyle S_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de6e810a93f67802ecb603ee0e3324005c6e583e). Thus, each processor receives a sequence of sorted sequences. The fact that the rank     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) of the splitter elements      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) was chosen globally, provides two important properties: On the one hand,     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) was chosen so that each processor can still operate on     n  /  p   {\textstyle n/p}  ![{\textstyle n/p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/27b9098ab175281940192ef0b2721c28bc1f93dd) elements after assignment. The algorithm is perfectly [load-balanced](./Load_balancing_(computing)). On the other hand, all elements on processor     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) are less than or equal to all elements on processor     i + 1   {\displaystyle i+1}  ![{\displaystyle i+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2fe1bfc8314922e4c3fdb4e8eceb20a00b4f011d). Hence, each processor performs the [*p*-way merge](./K-way_merge_algorithm) locally and thus obtains a sorted sequence from its sub-sequences. Because of the second property, no further *p*-way-merge has to be performed, the results only have to be put together in the order of the processor number.

 

#### Multi-sequence selection

 

In its simplest form, given     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) sorted sequences      S  1   , . . . ,  S  p     {\displaystyle S_{1},...,S_{p}}  ![{\displaystyle S_{1},...,S_{p}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d98b2999fbd2e6c533f76352b09fcece9316eaeb) distributed evenly on     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) processors and a rank     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40), the task is to find an element     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) with a global rank     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) in the union of the sequences. Hence, this can be used to divide each      S  i     {\displaystyle S_{i}}  ![{\displaystyle S_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de6e810a93f67802ecb603ee0e3324005c6e583e) in two parts at a splitter index      l  i     {\displaystyle l_{i}}  ![{\displaystyle l_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48ba35055d00bcaa522bca9247c8857730998759), where the lower part contains only elements which are smaller than     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), while the elements bigger than     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) are located in the upper part.

 

The presented [sequential algorithm](./Sequential_algorithm) returns the indices of the splits in each sequence, e.g. the indices      l  i     {\displaystyle l_{i}}  ![{\displaystyle l_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48ba35055d00bcaa522bca9247c8857730998759) in sequences      S  i     {\displaystyle S_{i}}  ![{\displaystyle S_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de6e810a93f67802ecb603ee0e3324005c6e583e) such that      S  i   [  l  i   ]   {\displaystyle S_{i}[l_{i}]}  ![{\displaystyle S_{i}[l_{i}]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d02331f6b9e8af20f6fa147074ce4ee4cc86833) has a global rank less than     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) and      r a n k   (   S  i   [  l  i   + 1 ]  )  ≥ ≥  k   {\displaystyle \mathrm {rank} \left(S_{i}[l_{i}+1]\right)\geq k}  ![{\displaystyle \mathrm {rank} \left(S_{i}[l_{i}+1]\right)\geq k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/41413e6e418305ec91ddf5335fd28f14ac8dd84f).[[23]](./Merge_sort#cite_note-23)

 
```
algorithm msSelect(S : Array of sorted Sequences [S_1,..,S_p], k : int) is
    for i = 1 to p do 
	(l_i, r_i) = (0, |S_i|-1)
	
    while there exists i: l_i < r_i do
	// pick Pivot Element in S_j[l_j], .., S_j[r_j], chose random j uniformly
	v := pickPivot(S, l, r)
	for i = 1 to p do 
	    m_i = binarySearch(v, S_i[l_i, r_i]) // sequentially
	if m_1 + ... + m_p >= k then // m_1+ ... + m_p is the global rank of v
	    r := m  // vector assignment
	else
	    l := m 
	
    return l
```
 

For the complexity analysis the [PRAM](./Parallel_random-access_machine) model is chosen. If the data is evenly distributed over all     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36), the p-fold execution of the *binarySearch* method has a running time of       O    (  p log ⁡ ⁡   (  n  /  p  )   )    {\displaystyle {\mathcal {O}}\left(p\log \left(n/p\right)\right)}  ![{\displaystyle {\mathcal {O}}\left(p\log \left(n/p\right)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b7dcd979d2caabdf9f1bca9ccf343c18e3fc969). The expected recursion depth is       O    (  log ⁡ ⁡   (   ∑ ∑   i    |   S  i    |   )   )  =   O   ( log ⁡ ⁡  ( n ) )   {\displaystyle {\mathcal {O}}\left(\log \left(\textstyle \sum _{i}|S_{i}|\right)\right)={\mathcal {O}}(\log(n))}  ![{\displaystyle {\mathcal {O}}\left(\log \left(\textstyle \sum _{i}|S_{i}|\right)\right)={\mathcal {O}}(\log(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/37fb27e2c4ff52cb1cba6c01e7b5177011e293f8) as in the ordinary [Quickselect](./Quickselect). Thus the overall expected running time is       O    (  p log ⁡ ⁡  ( n  /  p ) log ⁡ ⁡  ( n )  )    {\displaystyle {\mathcal {O}}\left(p\log(n/p)\log(n)\right)}  ![{\displaystyle {\mathcal {O}}\left(p\log(n/p)\log(n)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0e5c668a0f2628a1a2d3aac2964ab4a5d85b7e33).

 

Applied on the parallel multiway merge sort, this algorithm has to be invoked in parallel such that all splitter elements of rank     i   n p     {\textstyle i{\frac {n}{p}}}  ![{\textstyle i{\frac {n}{p}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b073387bac8e266ad41c94078ca2df206d8593a1) for     i = 1 , . . , p   {\displaystyle i=1,..,p}  ![{\displaystyle i=1,..,p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9107ecf5f7b42e02b16a1042eee2941c8826734a) are found simultaneously. These splitter elements can then be used to partition each sequence in     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) parts, with the same total running time of       O    (  p  log ⁡ ⁡  ( n  /  p ) log ⁡ ⁡  ( n )  )    {\displaystyle {\mathcal {O}}\left(p\,\log(n/p)\log(n)\right)}  ![{\displaystyle {\mathcal {O}}\left(p\,\log(n/p)\log(n)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4a084e4f35a66c26ab7039bead5b1af68c4a7dcb).

 

#### Pseudocode

 

Below, the complete pseudocode of the parallel multiway merge sort algorithm is given. We assume that there is a barrier synchronization before and after the multisequence selection such that every processor can determine the splitting elements and the sequence partition properly.

 
```
/**
 * d: Unsorted Array of Elements
 * n: Number of Elements
 * p: Number of Processors
 * return Sorted Array
 */
algorithm parallelMultiwayMergesort(d : Array, n : int, p : int) is
    o := new Array[0, n]                         // the output array
    for i = 1 to p do in parallel                // each processor in parallel
        S_i := d[(i-1) * n/p, i * n/p] 	         // Sequence of length n/p
	sort(S_i)                                // sort locally
        synch
	v_i := msSelect([S_1,...,S_p], i * n/p)          // element with global rank i * n/p
        synch
	(S_i,1, ..., S_i,p) := sequence_partitioning(si, v_1, ..., v_p) // split s_i into subsequences
	    
	o[(i-1) * n/p, i * n/p] := kWayMerge(s_1,i, ..., s_p,i)  // merge and assign to output array
	
    return o
```
 

#### Analysis

 

Firstly, each processor sorts the assigned     n  /  p   {\displaystyle n/p}  ![{\displaystyle n/p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b40bd0a1d3c9771117157039602170561e5902f) elements locally using a sorting algorithm with complexity       O    (  n  /  p  log ⁡ ⁡  ( n  /  p )  )    {\displaystyle {\mathcal {O}}\left(n/p\;\log(n/p)\right)}  ![{\displaystyle {\mathcal {O}}\left(n/p\;\log(n/p)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b0545dd8cba33df66c8fd8468bcf5c2ad7eae6fa). After that, the splitter elements have to be calculated in time       O    (  p  log ⁡ ⁡  ( n  /  p ) log ⁡ ⁡  ( n )  )    {\displaystyle {\mathcal {O}}\left(p\,\log(n/p)\log(n)\right)}  ![{\displaystyle {\mathcal {O}}\left(p\,\log(n/p)\log(n)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4a084e4f35a66c26ab7039bead5b1af68c4a7dcb). Finally, each group of     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) splits have to be merged in parallel by each processor with a running time of       O   ( log ⁡ ⁡  ( p )  n  /  p )   {\displaystyle {\mathcal {O}}(\log(p)\;n/p)}  ![{\displaystyle {\mathcal {O}}(\log(p)\;n/p)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b9160bd6a9cd77d923eec59b8cecc9d111d9226e) using a sequential [p-way merge algorithm](./Merge_algorithm). Thus, the overall running time is given by

 

      O    (    n p   log ⁡ ⁡   (   n p   )  + p log ⁡ ⁡   (   n p   )  log ⁡ ⁡  ( n ) +   n p   log ⁡ ⁡  ( p )  )    {\displaystyle {\mathcal {O}}\left({\frac {n}{p}}\log \left({\frac {n}{p}}\right)+p\log \left({\frac {n}{p}}\right)\log(n)+{\frac {n}{p}}\log(p)\right)}  ![{\displaystyle {\mathcal {O}}\left({\frac {n}{p}}\log \left({\frac {n}{p}}\right)+p\log \left({\frac {n}{p}}\right)\log(n)+{\frac {n}{p}}\log(p)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f2a556c243ccf13d594b3833b09ccfeb340c6fa0).

 

#### Practical adaption and application

 

The multiway merge sort algorithm is very scalable through its high parallelization capability, which allows the use of many processors. This makes the algorithm a viable candidate for sorting large amounts of data, such as those processed in [computer clusters](./Computer_cluster). Also, since in such systems memory is usually not a limiting resource, the disadvantage of [space complexity](./Space_complexity) of merge sort is negligible. However, other factors become important in such systems, which are not taken into account when modelling on a [PRAM](./Parallel_random-access_machine). Here, the following aspects need to be considered: [Memory hierarchy](./Memory_hierarchy), when the data does not fit into the processors cache, or the communication overhead of exchanging data between processors, which could become a bottleneck when the data can no longer be accessed via the shared memory.

 

[Sanders](./Peter_Sanders_(computer_scientist)) et al. have presented in their paper a [bulk synchronous parallel](./Bulk_synchronous_parallel) algorithm for multilevel multiway mergesort, which divides     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) processors into     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) groups of size      p ′    {\displaystyle p'}  ![{\displaystyle p'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/40e623e3163571a220ed60ecb31aa78c24104b85). All processors sort locally first. Unlike single level multiway mergesort, these sequences are then partitioned into     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) parts and assigned to the appropriate processor groups. These steps are repeated recursively in those groups. This reduces communication and especially avoids problems with many small messages. The hierarchical structure of the underlying real network can be used to define the processor groups (e.g. [racks](./19-inch_rack), [clusters](./Computer_cluster),...).[[22]](./Merge_sort#cite_note-:0-22)

 

### Further variants

 

Merge sort was one of the first sorting algorithms where optimal speed up was achieved, with [Richard Cole](./Richard_J._Cole) using a clever subsampling algorithm to ensure *O*(1) merge.[[24]](./Merge_sort#cite_note-24) Other sophisticated parallel sorting algorithms can achieve the same or better time bounds with a lower constant. For example, in 1991 David Powers described a parallelized [quicksort](./Quicksort) (and a related [radix sort](./Radix_sort)) that can operate in *O*(log *n*) time on a [CRCW](./CRCW) [parallel random-access machine](./Parallel_random-access_machine) (PRAM) with *n* processors by performing partitioning implicitly.[[25]](./Merge_sort#cite_note-25) Powers further shows that a pipelined version of Batcher's [Bitonic Mergesort](./Bitonic_sorter) at *O*((log *n*)2) time on a butterfly [sorting network](./Sorting_network) is in practice actually faster than his *O*(log *n*) sorts on a PRAM, and he provides detailed discussion of the hidden overheads in comparison, radix and parallel sorting.[[26]](./Merge_sort#cite_note-26)

 

## Comparison with other sort algorithms

 

Although [heapsort](./Heapsort) has the same time bounds as merge sort, it requires only Θ(1) auxiliary space instead of merge sort's Θ(*n*). On typical modern architectures, efficient [quicksort](./Quicksort) implementations generally outperform merge sort for sorting RAM-based arrays.[[27]](./Merge_sort#cite_note-:2-27) Quicksorts are preferred when the data size to be sorted is lesser, since the space complexity for quicksort is O(log *n*), it helps in utilizing cache locality better than merge sort (with space complexity O(n)).[[27]](./Merge_sort#cite_note-:2-27) On the other hand, merge sort is a stable sort and is more efficient at handling slow-to-access sequential media. Merge sort is often the best choice for sorting a [linked list](./Linked_list): in this situation it is relatively easy to implement a merge sort in such a way that it requires only Θ(1) extra space, and the slow random-access performance of a linked list makes some other algorithms (such as quicksort) perform poorly, and others (such as heapsort) completely impossible.

 

As of [Perl](./Perl) 5.8, merge sort is its default sorting algorithm (it was quicksort in previous versions of Perl).[[28]](./Merge_sort#cite_note-28) In [Java](./Java_platform), the [Arrays.sort()](https://docs.oracle.com/javase/9/docs/api/java/util/Arrays.html#sort-java.lang.Object:A-) methods use merge sort or a tuned quicksort depending on the datatypes and for implementation efficiency switch to [insertion sort](./Insertion_sort) when fewer than seven array elements are being sorted.[[29]](./Merge_sort#cite_note-29) The [Linux](./Linux) kernel uses merge sort for its linked lists.[[30]](./Merge_sort#cite_note-30)

 

[Timsort](./Timsort), a tuned hybrid of merge sort and insertion sort is used in variety of software platforms and languages including the Java and [Android](./Android_(operating_system)) platforms[[31]](./Merge_sort#cite_note-31) and is used by [Python](./Python_(programming_language)) since version 2.3; since version 3.11, Timsort's merge policy was updated to [Powersort](./Powersort).[[32]](./Merge_sort#cite_note-32)

 

## References

 
1. [↑](./Merge_sort#cite_ref-1) [Skiena (2008](./Merge_sort#CITEREFSkiena2008), p. 122)
2. [↑](./Merge_sort#cite_ref-goodrich12_2-0) Goodrich, Michael T.; Tamassia, Roberto; Goldwasser, Michael H. (2013). "Chapter 12 - Sorting and Selection". *Data structures and algorithms in Python* (1st ed.). Hoboken [NJ]: Wiley. pp. 538–549. [ISBN](./ISBN_(identifier)) [978-1-118-29027-9](./Special:BookSources/978-1-118-29027-9).
3. [↑](./Merge_sort#cite_ref-3) [Knuth (1998](./Merge_sort#CITEREFKnuth1998), p. 158)
4. [↑](./Merge_sort#cite_ref-4) Katajainen, Jyrki; Träff, Jesper Larsson (March 1997). "Algorithms and Complexity". *Proceedings of the 3rd Italian Conference on Algorithms and Complexity*. Italian Conference on Algorithms and Complexity. Lecture Notes in Computer Science. Vol. 1203. Rome. pp. 217–228. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.86.3154](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.86.3154). [doi](./Doi_(identifier)):[10.1007/3-540-62592-5_74](https://doi.org/10.1007%2F3-540-62592-5_74). [ISBN](./ISBN_(identifier)) [978-3-540-62592-6](./Special:BookSources/978-3-540-62592-6).
5. [↑](./Merge_sort#cite_ref-5) [Cormen et al. (2009](./Merge_sort#CITEREFCormenLeisersonRivestStein2009), p. 36)
6. [↑](./Merge_sort#cite_ref-6) The worst case number given here does not agree with that given in [Knuth](./Donald_Knuth)'s *[Art of Computer Programming](./Art_of_Computer_Programming), Vol 3*. The discrepancy is due to Knuth analyzing a variant implementation of merge sort that is slightly sub-optimal
7. [1](./Merge_sort#cite_ref-:1_7-0) [2](./Merge_sort#cite_ref-:1_7-1) Jayalakshmi, N. (2007). *Data structure using C++*. Firewall Media. [ISBN](./ISBN_(identifier)) [978-81-318-0020-1](./Special:BookSources/978-81-318-0020-1). [OCLC](./OCLC_(identifier)) [849900742](https://search.worldcat.org/oclc/849900742).
8. [↑](./Merge_sort#cite_ref-8) [Cormen et al. (2009](./Merge_sort#CITEREFCormenLeisersonRivestStein2009), p. 151)
9. [↑](./Merge_sort#cite_ref-9) Powers, David M. W.; McMahon, Graham B. (1983). "A compendium of interesting prolog programs". DCS Technical Report 8313 (Report). Department of Computer Science, University of New South Wales.
10. [↑](./Merge_sort#cite_ref-wikisort_10-0) ["WikiSort. Fast and stable sort algorithm that uses O(1) memory. Public domain"](https://github.com/BonzaiThePenguin/WikiSort). *[GitHub](./GitHub)*. 14 Apr 2014.
11. [↑](./Merge_sort#cite_ref-11) Chandramouli, Badrish; Goldstein, Jonathan (2014). [*Patience is a Virtue: Revisiting Merge and Sort on Modern Processors*](http://research.microsoft.com/pubs/209622/patsort-sigmod14.pdf) (PDF). SIGMOD/PODS.
12. [1](./Merge_sort#cite_ref-quadsort_12-0) [2](./Merge_sort#cite_ref-quadsort_12-1) ["Quadsort is a branchless stable adaptive merge sort"](https://github.com/scandum/quadsort). *[GitHub](./GitHub)*. 8 Jun 2022.
13. [↑](./Merge_sort#cite_ref-13) [Katajainen, Pasanen & Teuhola (1996)](./Merge_sort#CITEREFKatajainenPasanenTeuhola1996)
14. [↑](./Merge_sort#cite_ref-14) Geffert, Viliam; Katajainen, Jyrki; Pasanen, Tomi (2000). ["Asymptotically efficient in-place merging"](https://doi.org/10.1016%2FS0304-3975%2898%2900162-5). *Theoretical Computer Science*. **237** (1–2): 159–181. [doi](./Doi_(identifier)):[10.1016/S0304-3975(98)00162-5](https://doi.org/10.1016%2FS0304-3975%2898%2900162-5).
15. [↑](./Merge_sort#cite_ref-Research_Contributions_15-0) Huang, Bing-Chao; Langston, Michael A. (March 1988). ["Practical In-Place Merging"](https://doi.org/10.1145%2F42392.42403). *Communications of the ACM*. **31** (3): 348–352. [doi](./Doi_(identifier)):[10.1145/42392.42403](https://doi.org/10.1145%2F42392.42403). [S2CID](./S2CID_(identifier)) [4841909](https://api.semanticscholar.org/CorpusID:4841909).
16. [↑](./Merge_sort#cite_ref-16) Kim, Pok-Son; Kutzner, Arne (2004). "Stable Minimum Storage Merging by Symmetric Comparisons". *Algorithms – ESA 2004*. European Symp. Algorithms. Lecture Notes in Computer Science. Vol. 3221. pp. 714–723. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.102.4612](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.102.4612). [doi](./Doi_(identifier)):[10.1007/978-3-540-30140-0_63](https://doi.org/10.1007%2F978-3-540-30140-0_63). [ISBN](./ISBN_(identifier)) [978-3-540-23025-0](./Special:BookSources/978-3-540-23025-0).
17. [↑](./Merge_sort#cite_ref-17) Kim, Pok-Son; Kutzner, Arne (1 Sep 2003). ["A New Method for Efficient in-Place Merging"](https://koreascience.kr/article/CFKO200311922203087.page). *Proceedings of the Korean Institute of Intelligent Systems Conference*: 392–394.
18. [↑](./Merge_sort#cite_ref-18) Ferragina, Paolo (2009–2019), ["5. Sorting Atomic Items"](http://didawiki.cli.di.unipi.it/lib/exe/fetch.php/magistraleinformaticanetworking/ae/ae2018/ferragina_notes_algoeng_2019_vers_5_.pdf) (PDF), *The magic of Algorithms!*, p. 5-4, [archived](https://web.archive.org/web/20210512230253/http://didawiki.cli.di.unipi.it/lib/exe/fetch.php/magistraleinformaticanetworking/ae/ae2018/ferragina_notes_algoeng_2019_vers_5_.pdf) (PDF) from the original on 2021-05-12
19. [1](./Merge_sort#cite_ref-clrs_19-0) [2](./Merge_sort#cite_ref-clrs_19-1) [Cormen et al. (2009](./Merge_sort#CITEREFCormenLeisersonRivestStein2009), pp. 797–805)
20. [↑](./Merge_sort#cite_ref-20) Victor J. Duvanenko "Parallel Merge Sort" Dr. Dobb's Journal & blog [](https://duvanenko.tech.blog/2018/01/13/parallel-merge-sort/) and GitHub repo C++ implementation [](https://github.com/DragonSpit/ParallelAlgorithms)
21. [↑](./Merge_sort#cite_ref-21) Peter Sanders; Johannes Singler (2008). ["Lecture *Parallel algorithms*"](http://algo2.iti.kit.edu/sanders/courses/paralg08/singler.pdf) (PDF). Retrieved 2020-05-02.
22. [1](./Merge_sort#cite_ref-:0_22-0) [2](./Merge_sort#cite_ref-:0_22-1) Axtmann, Michael; Bingmann, Timo; Sanders, Peter; Schulz, Christian (2015). ["Practical Massively Parallel Sorting"](https://publikationen.bibliothek.kit.edu/1000050651/37296033). *Proceedings of the 27th ACM symposium on Parallelism in Algorithms and Architectures*. pp. 13–23. [arXiv](./ArXiv_(identifier)):[1410.6754](https://arxiv.org/abs/1410.6754). [doi](./Doi_(identifier)):[10.1145/2755573.2755595](https://doi.org/10.1145%2F2755573.2755595). [ISBN](./ISBN_(identifier)) [9781450335881](./Special:BookSources/9781450335881). [S2CID](./S2CID_(identifier)) [18249978](https://api.semanticscholar.org/CorpusID:18249978).
23. [↑](./Merge_sort#cite_ref-23) Peter Sanders (2019). ["Lecture *Parallel algorithms*"](http://algo2.iti.kit.edu/sanders/courses/paralg19/vorlesung.pdf) (PDF). Retrieved 2020-05-02.
24. [↑](./Merge_sort#cite_ref-24) Cole, Richard (August 1988). "Parallel merge sort". *SIAM J. Comput*. **17** (4): 770–785. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.464.7118](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.464.7118). [doi](./Doi_(identifier)):[10.1137/0217049](https://doi.org/10.1137%2F0217049). [S2CID](./S2CID_(identifier)) [2416667](https://api.semanticscholar.org/CorpusID:2416667).
25. [↑](./Merge_sort#cite_ref-25) Powers, David M. W. (1991). ["Parallelized Quicksort and Radixsort with Optimal Speedup"](https://web.archive.org/web/20070525234405/http://citeseer.ist.psu.edu/327487.html). *Proceedings of International Conference on Parallel Computing Technologies, Novosibirsk*. Archived from [the original](http://citeseer.ist.psu.edu/327487.html) on 2007-05-25.
26. [↑](./Merge_sort#cite_ref-26) Powers, David M. W. (January 1995). [*Parallel Unification: Practical Complexity*](http://david.wardpowers.info/Research/AI/papers/199501-ACAW-PUPC.pdf) (PDF). Australasian Computer Architecture Workshop Flinders University.
27. [1](./Merge_sort#cite_ref-:2_27-0) [2](./Merge_sort#cite_ref-:2_27-1) Oladipupo, Esau Taiwo; Abikoye, Oluwakemi Christianah (2020). ["Comparison of quicksort and mergesort"](https://www.sciencedirect.com/science/article/pii/S1877050920312667/pdf). *Third International Conference on Computing and Network Communications (CoCoNet 2019)*. **2020** (2020): 9. Retrieved 2024-01-20 – via Elsevier Science Direct.
28. [↑](./Merge_sort#cite_ref-28) ["Sort – Perl 5 version 8.8 documentation"](https://perldoc.perl.org/5.8.8/sort.html). Retrieved 2020-08-23.
29. [↑](./Merge_sort#cite_ref-29) coleenp (22 Feb 2019). ["src/java.base/share/classes/java/util/Arrays.java @ 53904:9c3fe09f69bc"](https://hg.openjdk.java.net/jdk/jdk/file/9c3fe09f69bc/src/java.base/share/classes/java/util/Arrays.java#l1331). *OpenJDK*.
30. [↑](./Merge_sort#cite_ref-30) [linux kernel /lib/list_sort.c](https://github.com/torvalds/linux/blob/master/lib/list_sort.c)
31. [↑](./Merge_sort#cite_ref-31) University of Liverpool (2022-12-12). ["Computer scientists improve Python sorting function"](https://techxplore.com/news/2022-12-scientists-python-function.html). *Tech Xplore*. Retrieved 2024-05-08.
32. [↑](./Merge_sort#cite_ref-32) James, Mike (2022-12-21). ["Python Now Uses Powersort"](https://www.i-programmer.info/news/216-python/15954-python-now-uses-powersort.html). *i-programmer.info*. Retrieved 2024-05-08.

 

## Bibliography

  
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009) [1990]. [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03384-4](./Special:BookSources/0-262-03384-4). This causes "Harv and Sfn no&#x2D;target errors" 
- Katajainen, Jyrki; Pasanen, Tomi; Teuhola, Jukka (1996). ["Practical in-place mergesort"](https://web.archive.org/web/20110807033704/http://www.diku.dk/hjemmesider/ansatte/jyrki/Paper/mergesort_NJC.ps). *Nordic Journal of Computing*. **3** (1): 27–40. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.22.8523](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.22.8523). [ISSN](./ISSN_(identifier)) [1236-6064](https://search.worldcat.org/issn/1236-6064). Archived from [the original](http://www.diku.dk/hjemmesider/ansatte/jyrki/Paper/mergesort_NJC.ps) on 2011-08-07. Retrieved 2009-04-04.. Also [Practical In-Place Mergesort](http://citeseer.ist.psu.edu/katajainen96practical.html). Also [](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.22.8523)
- [Knuth, Donald](./Donald_Knuth) (1998). "Section 5.2.4: Sorting by Merging". *Sorting and Searching*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 3 (2nd ed.). Addison-Wesley. pp. 158–168. [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0).
- Kronrod, M. A. (1969). "Optimal ordering algorithm without operational field". *Soviet Mathematics - Doklady*. **10**: 744.
- LaMarca, A.; Ladner, R. E. (1997). "The influence of caches on the performance of sorting". *Proc. 8th Ann. ACM-SIAM Symp. On Discrete Algorithms (SODA97)*: 370–379. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.31.1153](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.31.1153).
- [Skiena, Steven S.](./Steven_Skiena) (2008). "4.5: Mergesort: Sorting by Divide-and-Conquer". *The Algorithm Design Manual* (2nd ed.). Springer. pp. 120–125. [ISBN](./ISBN_(identifier)) [978-1-84800-069-8](./Special:BookSources/978-1-84800-069-8).
- Sun Microsystems. ["Arrays API (Java SE 6)"](http://java.sun.com/javase/6/docs/api/java/util/Arrays.html). Retrieved 2007-11-19.
- Oracle Corp. ["Arrays (Java SE 10 & JDK 10)"](https://docs.oracle.com/javase/10/docs/api/java/util/Arrays.html). Retrieved 2018-07-23.

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm implementation](https://en.wikibooks.org/wiki/Algorithm%20implementation)* has a page on the topic of: ***[Merge sort](https://en.wikibooks.org/wiki/Algorithm%20implementation/Sorting/Merge_sort)***  
- [Animated Sorting Algorithms: Merge Sort](https://web.archive.org/web/20150306071601/http://www.sorting-algorithms.com/merge-sort) at the [Wayback Machine](./Wayback_Machine) (archived 6 March 2015) – graphical demonstration
- [Open Data Structures - Section 11.1.1 - Merge Sort](http://opendatastructures.org/versions/edition-0.1e/ods-java/11_1_Comparison_Based_Sorti.html#SECTION001411000000000000000), [Pat Morin](./Pat_Morin)
- [C Program to Implement Merge Sort Algorithm](https://www.sanfoundry.com/c-program-merge-sort-using-recursion/)
- [Merge Sort Code with Java](https://javachallengers.com/merge-sort-with-java/)
- [C++ Program for Merge Sort](https://www.ccbp.in/blog/articles/merge-sort-cpp)

 
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