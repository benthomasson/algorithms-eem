---
source: https://en.wikipedia.org/wiki/Counting_sort
fetched: 2026-06-19
---

Sorting algorithm 
| Class | Sorting Algorithm |
| --- | --- |
| Data structure | Array |
| Worst-caseperformance | O(n+k){\displaystyle O(n+k)}, where k is the range of the non-negative key values. |
| Worst-casespace complexity | O(n+k){\displaystyle O(n+k)} |

 

In [computer science](./Computer_science), **counting sort** is an [algorithm](./Algorithm) for [sorting](./Sorting_algorithm) a collection of objects according to keys that are small positive [integers](./Integer); that is, it is an [integer sorting](./Integer_sorting) algorithm. It operates by counting the number of objects that possess distinct key values, and applying prefix sum on those counts to determine the positions of each key value in the output sequence. Its running time is linear in the number of items and the difference between the maximum key value and the minimum key value, so it is only suitable for direct use in situations where the variation in keys is not significantly greater than the number of items. It is often used as a subroutine in [radix sort](./Radix_sort), another sorting algorithm, which can handle larger keys more efficiently.[[1]](./Counting_sort#cite_note-clrs-1)[[2]](./Counting_sort#cite_note-edmonds-2)[[3]](./Counting_sort#cite_note-sedgewick-3)

 

Counting sort is not a [comparison sort](./Comparison_sort); it uses key values as indexes into an array and the [Ω](./Big_O_notation#Family_of_Bachmann–Landau_notations)(*n* log *n*) [lower bound](./Lower_bound) for comparison sorting will not apply.[[1]](./Counting_sort#cite_note-clrs-1) [Bucket sort](./Bucket_sort) may be used in lieu of counting sort, and entails a similar time analysis. However, compared to counting sort, bucket sort requires [linked lists](./Linked_list), [dynamic arrays](./Dynamic_array), or a large amount of pre-allocated memory to hold the sets of items within each bucket, whereas counting sort stores a single number (the count of items) per bucket.[[4]](./Counting_sort#cite_note-knuth-4)

 

## Input and output assumptions

 

In the most general case, the input to counting sort consists of a [collection](./Collection_(abstract_data_type)) of n items, each of which has a non-negative integer key whose maximum value is at most k.[[3]](./Counting_sort#cite_note-sedgewick-3)
In some descriptions of counting sort, the input to be sorted is assumed to be more simply a sequence of integers itself,[[1]](./Counting_sort#cite_note-clrs-1) but this simplification does not accommodate many applications of counting sort. For instance, when used as a subroutine in [radix sort](./Radix_sort), the keys for each call to counting sort are individual digits of larger item keys; it would not suffice to return only a sorted list of the key digits, separated from the items.

 

In applications such as in radix sort, a bound on the maximum key value k will be known in advance, and can be assumed to be part of the input to the algorithm. However, if the value of k is not already known then it may be computed, as a first step, by an additional loop over the data to determine the maximum key value.

 

The output is an [array](./Array_data_structure) of the elements ordered by their keys. Because of its application to radix sorting, counting sort must be a [stable sort](./Stable_sort); that is, if two elements share the same key, their relative order in the output array and their relative order in the input array should match.[[1]](./Counting_sort#cite_note-clrs-1)[[2]](./Counting_sort#cite_note-edmonds-2)

 

## Pseudocode

 

In pseudocode, the algorithm may be expressed as:

 
```
function CountingSort(input, k) is
    
    count ← array of k + 1 zeros
    output ← array of same length as input
    
    for i = 0 to length(input) - 1 do
        j = key(input[i])
        count[j] = count[j] + 1

    for i = 1 to k do
        count[i] = count[i] + count[i - 1]

    for i = length(input) - 1 down to 0 do
        j = key(input[i])
        count[j] = count[j] - 1
        output[count[j]] = input[i]

    return output
```
 

Where `input` is the array to be sorted, `key` returns the numeric key of each item in the input array, `count` is an auxiliary array used first to store the numbers of items with each key, and then (after the second loop) to store the positions where items with each key should be placed,
`k` is the maximum value of the non-negative key values and `output` is the sorted output array.

 

In summary, the algorithm loops over the items in the first loop, computing a [histogram](./Histogram) of the number of times each key occurs within the `input` collection. After that in the second loop, it performs a [prefix sum](./Prefix_sum) computation on `count` in order to determine, for each key, the position range where the items having that key should be placed; i.e. items of key     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) should be placed starting in position `count[

i

{\displaystyle i}

]`. Finally, in the third loop, it loops over the items of `input` again, but in reverse order, moving each item into its sorted position in the `output` array.[[1]](./Counting_sort#cite_note-clrs-1)[[2]](./Counting_sort#cite_note-edmonds-2)[[3]](./Counting_sort#cite_note-sedgewick-3)

 

The relative order of items with equal keys is preserved here; i.e., this is a [stable sort](./Category:Stable_sorts).

 

## Complexity analysis

 

Because the algorithm uses only simple `for` loops, without recursion or subroutine calls, it is straightforward to analyze. The initialization of the count array, and the second for loop which performs a prefix sum on the count array, each iterate at most *k* + 1 times and therefore take *O*(*k*) time. The other two for loops, and the initialization of the output array, each take *O*(*n*) time. Therefore, the time for the whole algorithm is the sum of the times for these steps, *O*(*n* + *k*).[[1]](./Counting_sort#cite_note-clrs-1)[[2]](./Counting_sort#cite_note-edmonds-2)

 

Because it uses arrays of length *k* + 1 and n, the total space usage of the algorithm is also *O*(*n* + *k*).[[1]](./Counting_sort#cite_note-clrs-1) For problem instances in which the maximum key value is significantly smaller than the number of items, counting sort can be highly space-efficient, as the only storage it uses other than its input and output arrays is the Count array which uses space *O*(*k*).[[5]](./Counting_sort#cite_note-5)

 

## Variant algorithms

 

If each item to be sorted is itself an integer, and used as key as well, then the second and third loops of counting sort can be combined; in the second loop, instead of computing the position where items with key `i` should be placed in the output, simply append `Count[i]` copies of the number `i` to the output.

 

This algorithm may also be used to eliminate duplicate keys, by replacing the `Count` array with a [bit vector](./Bit_vector) that stores a `one` for a key that is present in the input and a `zero` for a key that is not present. If additionally the items are the integer keys themselves, both second and third loops can be omitted entirely and the bit vector will itself serve as output, representing the values as offsets of the non-`zero` entries, added to the range's lowest value. Thus the keys are sorted and the duplicates are eliminated in this variant just by being placed into the bit array.

 

For data in which the maximum key size is significantly smaller than the number of data items, counting sort may be [parallelized](./Parallel_algorithm) by splitting the input into subarrays of approximately equal size, processing each subarray in parallel to generate a separate count array for each subarray, and then merging the count arrays. When used as part of a parallel radix sort algorithm, the key size (base of the radix representation) should be chosen to match the size of the split subarrays.[[6]](./Counting_sort#cite_note-6) The simplicity of the counting sort algorithm and its use of the easily parallelizable prefix sum primitive also make it usable in more fine-grained parallel algorithms.[[7]](./Counting_sort#cite_note-7)

 

As described, counting sort is not an [in-place algorithm](./In-place_algorithm); even disregarding the count array, it needs separate input and output arrays. It is possible to modify the algorithm so that it places the items into sorted order within the same array that was given to it as the input, using only the count array as auxiliary storage; however, the modified in-place version of counting sort is not stable.[[3]](./Counting_sort#cite_note-sedgewick-3)

 

## History

 

Although radix sorting itself dates back far longer,
counting sort, and its application to radix sorting, were both invented by [Harold H. Seward](./Harold_H._Seward) in 1954.[[1]](./Counting_sort#cite_note-clrs-1)[[4]](./Counting_sort#cite_note-knuth-4)[[8]](./Counting_sort#cite_note-8)

 

## References

  
1. [1](./Counting_sort#cite_ref-clrs_1-0) [2](./Counting_sort#cite_ref-clrs_1-1) [3](./Counting_sort#cite_ref-clrs_1-2) [4](./Counting_sort#cite_ref-clrs_1-3) [5](./Counting_sort#cite_ref-clrs_1-4) [6](./Counting_sort#cite_ref-clrs_1-5) [7](./Counting_sort#cite_ref-clrs_1-6) [8](./Counting_sort#cite_ref-clrs_1-7) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001), "8.2 Counting Sort", *[Introduction to Algorithms](./Introduction_to_Algorithms)* (2nd ed.), [MIT Press](./MIT_Press) and [McGraw-Hill](./McGraw-Hill), pp. 168–170, [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). See also the historical notes on page 181.
2. [1](./Counting_sort#cite_ref-edmonds_2-0) [2](./Counting_sort#cite_ref-edmonds_2-1) [3](./Counting_sort#cite_ref-edmonds_2-2) [4](./Counting_sort#cite_ref-edmonds_2-3) Edmonds, Jeff (2008), "5.2 Counting Sort (a Stable Sort)", *How to Think about Algorithms*, Cambridge University Press, pp. 72–75, [ISBN](./ISBN_(identifier)) [978-0-521-84931-9](./Special:BookSources/978-0-521-84931-9).
3. [1](./Counting_sort#cite_ref-sedgewick_3-0) [2](./Counting_sort#cite_ref-sedgewick_3-1) [3](./Counting_sort#cite_ref-sedgewick_3-2) [4](./Counting_sort#cite_ref-sedgewick_3-3) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (2003), "6.10 Key-Indexed Counting", *Algorithms in Java, Parts 1-4: Fundamentals, Data Structures, Sorting, and Searching* (3rd ed.), Addison-Wesley, pp. 312–314.
4. [1](./Counting_sort#cite_ref-knuth_4-0) [2](./Counting_sort#cite_ref-knuth_4-1) [Knuth, D. E.](./Donald_Knuth) (1998), *[The Art of Computer Programming](./The_Art_of_Computer_Programming), Volume 3: Sorting and Searching* (2nd ed.), Addison-Wesley, [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0). Section 5.2, Sorting by counting, pp. 75–80, and historical notes, p. 170.
5. [↑](./Counting_sort#cite_ref-5) Burris, David S.; Schember, Kurt (1980), "Sorting sequential files with limited auxiliary storage", *Proceedings of the 18th annual Southeast Regional Conference*, New York, NY, USA: ACM, pp. 23–31, [doi](./Doi_(identifier)):[10.1145/503838.503855](https://doi.org/10.1145%2F503838.503855), [ISBN](./ISBN_(identifier)) [0897910141](./Special:BookSources/0897910141), [S2CID](./S2CID_(identifier)) [5670614](https://api.semanticscholar.org/CorpusID:5670614).
6. [↑](./Counting_sort#cite_ref-6) Zagha, Marco; [Blelloch, Guy E.](./Guy_Blelloch) (1991), "Radix sort for vector multiprocessors", [*Proceedings of Supercomputing '91, November 18-22, 1991, Albuquerque, NM, USA*](https://www.cs.cmu.edu/~scandal/papers/cray-sort-supercomputing91.ps.gz), IEEE Computer Society / ACM, pp. 712–721, [doi](./Doi_(identifier)):[10.1145/125826.126164](https://doi.org/10.1145%2F125826.126164), [ISBN](./ISBN_(identifier)) [0897914597](./Special:BookSources/0897914597).
7. [↑](./Counting_sort#cite_ref-7) [Reif, John H.](./John_Reif) (1985), "An optimal parallel algorithm for integer sorting", *[Proc. 26th Annual Symposium on Foundations of Computer Science (FOCS 1985)](./Symposium_on_Foundations_of_Computer_Science)*, pp. 496–504, [doi](./Doi_(identifier)):[10.1109/SFCS.1985.9](https://doi.org/10.1109%2FSFCS.1985.9), [ISBN](./ISBN_(identifier)) [0-8186-0644-4](./Special:BookSources/0-8186-0644-4), [S2CID](./S2CID_(identifier)) [5694693](https://api.semanticscholar.org/CorpusID:5694693).
8. [↑](./Counting_sort#cite_ref-8) Seward, H. H. (1954), "2.4.6 Internal Sorting by Floating Digital Sort", [*Information sorting in the application of electronic digital computers to business operations*](http://bitsavers.org/pdf/mit/whirlwind/R-series/R-232_Information_Sorting_in_the_Application_of_Electronic_Digital_Computers_to_Business_Operations_May54.pdf) (PDF), Master's thesis, Report R-232, [Massachusetts Institute of Technology](./Massachusetts_Institute_of_Technology), Digital Computer Laboratory, pp. 25–28.

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm implementation](https://en.wikibooks.org/wiki/Algorithm%20implementation)* has a page on the topic of: ***[Counting sort](https://en.wikibooks.org/wiki/Algorithm%20implementation/Sorting/Counting%20sort)***  
- [Counting Sort html5 visualization](http://www.cs.usfca.edu/~galles/visualization/CountingSort.html)
- [Demonstration applet from Cardiff University](http://users.cs.cf.ac.uk/C.L.Mumford/tristan/CountingSort.html) [Archived](https://web.archive.org/web/20130602221151/http://users.cs.cf.ac.uk/C.L.Mumford/tristan/CountingSort.html) 2013-06-02 at the [Wayback Machine](./Wayback_Machine)
- Kagel, Art S. (2 June 2006), "counting sort", in Black, Paul E. (ed.), [*Dictionary of Algorithms and Data Structures*](https://xlinux.nist.gov/dads/HTML/countingsort.html), U.S. National Institute of Standards and Technology, retrieved 2011-04-21.

 
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