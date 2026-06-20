---
source: https://en.wikipedia.org/wiki/Bucket_sort
fetched: 2026-06-19
---

Sorting algorithm 
| Class | Sorting algorithm |
| --- | --- |
| Data structure | Array |
| Worst-caseperformance | O(n2){\displaystyle O\left(n^{2}\right)} |
| Averageperformance | O(n+n2k+k){\displaystyle O\left(n+{\frac {n^{2}}{k}}+k\right)}, where k is the number of buckets.O(n),whenk≈n{\displaystyle O(n),{\text{when }}k\approx n}. |
| Worst-casespace complexity | O(n+k){\displaystyle O(n+k)} |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/61/Bucket_sort_1.svg/330px-Bucket_sort_1.svg.png)](./File:Bucket_sort_1.svg)Elements are distributed among bins [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Bucket_sort_2.svg/330px-Bucket_sort_2.svg.png)](./File:Bucket_sort_2.svg)Then, elements are sorted within each bin 

**Bucket sort**, or **bin sort**, is a [sorting algorithm](./Sorting_algorithm) that works by distributing the elements of an [array](./Array_data_structure) into a number of buckets. Each bucket is then sorted individually, either using a different sorting algorithm, or by recursively applying the bucket sorting algorithm. It is a [distribution sort](./Distribution_sort),  a generalization of [pigeonhole sort](./Pigeonhole_sort) that allows multiple keys per bucket, and is a cousin of [radix sort](./Radix_sort) in the most-to-least significant digit flavor. Bucket sort can be implemented with comparisons and therefore can also be considered a [comparison sort](./Comparison_sort) algorithm. The [computational complexity](./Analysis_of_algorithms) depends on the algorithm used to sort each bucket, the number of buckets to use, and whether the input is uniformly distributed.

 

Bucket sort works as follows:

 
1. Set up an array of initially empty "buckets".
2. **Scatter**: Go over the original array, putting each object in its bucket.
3. Sort each non-empty bucket.
4. **Gather**: Visit the buckets in order and put all elements back into the original array.

 

## Pseudocode

 
```
function bucketSort(array, k) is
    buckets ← new array of k empty lists
    M ← 1 + the maximum key value in the array
    for i = 0 to length(array) do
        insert array[i] into buckets[floor(k × array[i] / M)]
    for i = 0 to k do 
        nextSort(buckets[i])
    return the concatenation of buckets[0], ...., buckets[k]
```
 

Let *array* denote the array to be sorted and *k* denote the number of buckets to use. One can compute the maximum key value in [linear time](./Linear_time) by iterating over all the keys once. The [floor function](./Floor_function) must be used to convert a floating number to an integer ( and possibly casting of datatypes too ). The function *nextSort* is a sorting function used to sort each bucket. Conventionally, [insertion sort](./Insertion_sort) is used due to its relatively high performance with small numbers of elements, but other algorithms could be used as well, such as *[selection sort](./Selection_sort)* or *[merge sort](./Merge_sort)*. Using *bucketSort* itself as *nextSort* produces a relative of [radix sort](./Radix_sort); in particular, the case *n = 2* corresponds to [quicksort](./Quicksort) (although potentially with poor pivot choices).

 

## Analysis

 

### Worst-case analysis

 

When the input contains several keys that are close to each other (clustering), those elements are likely to be placed in the same bucket, which results in some buckets containing more elements than average. The worst-case scenario occurs when all the elements are placed in a single bucket. The overall performance would then be dominated by the algorithm used to sort each bucket, for example     O (  n  2   )   {\displaystyle O(n^{2})}  ![{\displaystyle O(n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cd9594a16cb898b8f2a2dff9227a385ec183392) [insertion sort](./Insertion_sort) or     O ( n log ⁡ ⁡  ( n ) )   {\displaystyle O(n\log(n))}  ![{\displaystyle O(n\log(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/85994022c28e938772bd858cd8281328643e8b3f) [comparison sort](./Comparison_sort) algorithms, such as [merge sort](./Merge_sort).

 

### Average-case analysis

 

Consider the case that the input is uniformly distributed. The first step, which is **initialize** the buckets and **find the maximum key value** in the array, can be done in     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time. If division and multiplication can be done in constant time, then **scattering** each element to its bucket also costs     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a). Assume insertion sort is used to sort each bucket, then the third step costs     O (   ∑ ∑   i = 1   k     n  i   2   )     {\displaystyle O(\textstyle \sum _{i=1}^{k}\displaystyle n_{i}^{2})}  ![{\displaystyle O(\textstyle \sum _{i=1}^{k}\displaystyle n_{i}^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a1891a6ceadfdefd58b61942db4fcc94eb656dcb), where      n  i     {\displaystyle n_{i}}  ![{\displaystyle n_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/57f87f905ba5a4d8c691ccaecd65fc47bd007ba4) is the length of the bucket indexed     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20). Since we are concerning the average time, the expectation     E (  n  i   2   )   {\displaystyle E(n_{i}^{2})}  ![{\displaystyle E(n_{i}^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f410c66150c60bad54943819f269ae1b2d72a084) has to be evaluated instead. Let      X  i j     {\displaystyle X_{ij}}  ![{\displaystyle X_{ij}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5a3501695fc03e54ae7d33791d3fd08a5bfb9645) be the random variable that is     1   {\displaystyle 1}  ![{\displaystyle 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92d98b82a3778f043108d4e20960a9193df57cbf) if element     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) is placed in bucket     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), and     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) otherwise. We have      n  i   =  ∑ ∑   j = 1   n    X  i j     {\displaystyle n_{i}=\sum _{j=1}^{n}X_{ij}}  ![{\displaystyle n_{i}=\sum _{j=1}^{n}X_{ij}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a279ca859bc258ff931d916fdaa563388fd0f946). Therefore,

         E (  n  i   2   )    = E  (   ∑ ∑   j = 1   n    X  i j    ∑ ∑   l = 1   n    X  i l    )        = E  (   ∑ ∑   j = 1   n    ∑ ∑   l = 1   n    X  i j    X  i l    )        = E  (   ∑ ∑   j = 1   n    X  i j   2    )  + E  (   ∑ ∑   1 ≤ ≤  j , l ≤ ≤  n    ∑ ∑   j ≠ ≠  l    X  i j    X  i l    )  .       {\displaystyle {\begin{aligned}E(n_{i}^{2})&=E\left(\sum _{j=1}^{n}X_{ij}\sum _{l=1}^{n}X_{il}\right)\\&=E\left(\sum _{j=1}^{n}\sum _{l=1}^{n}X_{ij}X_{il}\right)\\&=E\left(\sum _{j=1}^{n}X_{ij}^{2}\right)+E\left(\sum _{1\leq j,l\leq n}\sum _{j\neq l}X_{ij}X_{il}\right).\end{aligned}}}  ![{\displaystyle {\begin{aligned}E(n_{i}^{2})&=E\left(\sum _{j=1}^{n}X_{ij}\sum _{l=1}^{n}X_{il}\right)\\&=E\left(\sum _{j=1}^{n}\sum _{l=1}^{n}X_{ij}X_{il}\right)\\&=E\left(\sum _{j=1}^{n}X_{ij}^{2}\right)+E\left(\sum _{1\leq j,l\leq n}\sum _{j\neq l}X_{ij}X_{il}\right).\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ca0d91b993caf93ff043324d9f0054a4d8bf894) 

The last line separates the summation into the case     j = l   {\displaystyle j=l}  ![{\displaystyle j=l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b087e6e2398e6626b654f5230cb3d7a5e0098b4d) and the case     j ≠ ≠  l   {\displaystyle j\neq l}  ![{\displaystyle j\neq l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c957d7b5fcce14aac90f09687cd5424c7eef2b0b). Since the chance of an object distributed to bucket     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is     1  /  k   {\displaystyle 1/k}  ![{\displaystyle 1/k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7e9fedad8c70c6331b2640b56c23cef8c884e1f),      X  i j     {\displaystyle X_{ij}}  ![{\displaystyle X_{ij}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5a3501695fc03e54ae7d33791d3fd08a5bfb9645) is 1 with probability     1  /  k   {\displaystyle 1/k}  ![{\displaystyle 1/k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7e9fedad8c70c6331b2640b56c23cef8c884e1f) and 0 otherwise.

     E (  X  i j   2   ) =  1  2   ⋅ ⋅   (   1 k   )  +  0  2   ⋅ ⋅   (  1 − −    1 k    )  =   1 k     {\displaystyle E(X_{ij}^{2})=1^{2}\cdot \left({\frac {1}{k}}\right)+0^{2}\cdot \left(1-{\frac {1}{k}}\right)={\frac {1}{k}}}  ![{\displaystyle E(X_{ij}^{2})=1^{2}\cdot \left({\frac {1}{k}}\right)+0^{2}\cdot \left(1-{\frac {1}{k}}\right)={\frac {1}{k}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/97177a2868f681d377a938bbf478751a4a7e9749)     E (  X  i j    X  i k   ) = 1 ⋅ ⋅   (   1 k   )   (   1 k   )  =   1  k  2       {\displaystyle E(X_{ij}X_{ik})=1\cdot \left({\frac {1}{k}}\right)\left({\frac {1}{k}}\right)={\frac {1}{k^{2}}}}  ![{\displaystyle E(X_{ij}X_{ik})=1\cdot \left({\frac {1}{k}}\right)\left({\frac {1}{k}}\right)={\frac {1}{k^{2}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07f3b2c9db78aeee91dbb1e24c60f5156da998f) 

With the summation, it would be

     E  (   ∑ ∑   j = 1   n    X  i j   2    )  + E  (   ∑ ∑   1 ≤ ≤  j , k ≤ ≤  n    ∑ ∑   j ≠ ≠  k    X  i j    X  i k    )  = n ⋅ ⋅    1 k   + n ( n − −  1 ) ⋅ ⋅    1  k  2     =     n  2   + n k − −  n   k  2       {\displaystyle E\left(\sum _{j=1}^{n}X_{ij}^{2}\right)+E\left(\sum _{1\leq j,k\leq n}\sum _{j\neq k}X_{ij}X_{ik}\right)=n\cdot {\frac {1}{k}}+n(n-1)\cdot {\frac {1}{k^{2}}}={\frac {n^{2}+nk-n}{k^{2}}}}  ![{\displaystyle E\left(\sum _{j=1}^{n}X_{ij}^{2}\right)+E\left(\sum _{1\leq j,k\leq n}\sum _{j\neq k}X_{ij}X_{ik}\right)=n\cdot {\frac {1}{k}}+n(n-1)\cdot {\frac {1}{k^{2}}}={\frac {n^{2}+nk-n}{k^{2}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/386a9750396304e4b2841f4041c89704358837a1) 

Finally, the complexity would be     O  (   ∑ ∑   i = 1   k   E (  n  i   2   )  )  = O  (   ∑ ∑   i = 1   k       n  2   + n k − −  n   k  2      )  = O  (     n  2   k   + n  )    {\displaystyle O\left(\sum _{i=1}^{k}E(n_{i}^{2})\right)=O\left(\sum _{i=1}^{k}{\frac {n^{2}+nk-n}{k^{2}}}\right)=O\left({\frac {n^{2}}{k}}+n\right)}  ![{\displaystyle O\left(\sum _{i=1}^{k}E(n_{i}^{2})\right)=O\left(\sum _{i=1}^{k}{\frac {n^{2}+nk-n}{k^{2}}}\right)=O\left({\frac {n^{2}}{k}}+n\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bfaed7ffbbf26bc62bbae0fd3bbbbc475b4541c1).

 

The last step of bucket sort, which is **concatenating** all the sorted objects in each bucket, requires     O ( k )   {\displaystyle O(k)}  ![{\displaystyle O(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5ec39041121b14e8c2b1a986c9b04547b223e3c) time. Therefore, the total complexity is     O  (  n +    n  2   k   + k  )    {\displaystyle O\left(n+{\frac {n^{2}}{k}}+k\right)}  ![{\displaystyle O\left(n+{\frac {n^{2}}{k}}+k\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b508fd973073e5379c61e04adfc2476a5f4803ad). Note that if k is chosen to be     k = Θ Θ  ( n )   {\displaystyle k=\Theta (n)}  ![{\displaystyle k=\Theta (n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7e92eda13b9a26a0c7cdac8057a5464868ee5c33), then bucket sort runs in     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) average time, given a uniformly distributed input.[[1]](./Bucket_sort#cite_note-lfcs-1)

 

## Optimizations

 

A common optimization is to put the unsorted elements of the buckets back in the original array *first*, then run [insertion sort](./Insertion_sort) over the complete array; because insertion sort's runtime is based on how far each element is from its final position, the number of comparisons remains relatively small, and the memory hierarchy is better exploited by storing the list contiguously in memory.[[2]](./Bucket_sort#cite_note-2)

 

If the input distribution is known or can be estimated, buckets can often be chosen which contain constant density (rather than merely having constant size). This allows     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) average time complexity even without uniformly distributed input.

 

## Variants

 

### Generic bucket sort

 

The most common variant of bucket sort operates on a list of *n* numeric inputs between zero and some maximum value *M* and divides the value range into *b* buckets each of size *M*/*b*. If each bucket is sorted using [insertion sort](./Insertion_sort), the sort can be shown to run in expected linear time (where the average is taken over all possible inputs).[[3]](./Bucket_sort#cite_note-3) However, the performance of this sort degrades with clustering; if many values occur close together, they will all fall into a single bucket and be sorted slowly.  This performance degradation is avoided in the original bucket sort algorithm by assuming that the input is generated by a random process that distributes elements uniformly over the interval *[0,1)*.[[1]](./Bucket_sort#cite_note-lfcs-1)

 

### ProxmapSort

 Main article: [Proxmap sort](./Proxmap_sort) 

Similar to generic bucket sort as described above, **ProxmapSort** works by dividing an array of keys into subarrays via the use of a "map key" function that preserves a partial ordering on the keys; as each key is added to its subarray, insertion sort is used to keep that subarray sorted, resulting in the entire array being in sorted order when ProxmapSort completes. ProxmapSort differs from bucket sorts in its use of the map key to place the data approximately where it belongs in sorted order, producing a "proxmap" — a proximity mapping — of the keys.

 

### Histogram sort

 

Another variant of bucket sort known as histogram sort or [counting sort](./Counting_sort) adds an initial pass that counts the number of elements that will fall into each bucket using a count array.[[4]](./Bucket_sort#cite_note-4) Using this information, the array values can be arranged into a sequence of buckets in-place by a sequence of exchanges, leaving no space overhead for bucket storage.[*[failed verification](./Wikipedia:Verifiability)*]

 

### Postman's sort

 This section is linked from [[Radix sort]]  

The **Postman's sort** is a variant of bucket sort that takes advantage of a hierarchical structure of elements, typically described by a set of attributes. This is the algorithm used by letter-sorting machines in [post offices](./Post_office): mail is sorted first between domestic and international; then by state, province or territory; then by destination post office; then by routes, etc. Since keys are not compared against each other, sorting time is O(*cn*), where *c* depends on the size of the key and number of buckets. This is similar to a [radix sort](./Radix_sort) that works "top down," or "most significant digit first."[[5]](./Bucket_sort#cite_note-Black2011-5)[[6]](./Bucket_sort#cite_note-Ramey1992-6)

 

### Shuffle sort

 This section is linked from [[J sort]]  Main article: [Shuffle sort](./Shuffle_sort) 

The **shuffle sort**[[7]](./Bucket_sort#cite_note-7) is a variant of bucket sort that begins by removing the first 1/8 of the *n* items to be sorted, sorts them recursively, and puts them in an array. This creates *n*/8 "buckets" to which the remaining 7/8 of the items are distributed. Each "bucket" is then sorted, and the "buckets" are concatenated into a sorted array.

 

## Comparison with other sorting algorithms

 

Bucket sort can be seen as a generalization of [counting sort](./Counting_sort); in fact, if each bucket has size 1 then bucket sort degenerates to counting sort. The variable bucket size of bucket sort allows it to use O(*n*) memory instead of O(*M*) memory, where *M* is the number of distinct values; in exchange, it gives up counting sort's O(*n* + *M*) worst-case behavior.

 

Bucket sort with two buckets is effectively a version of [quicksort](./Quicksort) where the pivot value is always selected to be the middle value of the value range. While this choice is effective for uniformly distributed inputs, other means of choosing the pivot in quicksort such as randomly selected pivots make it more resistant to clustering in the input distribution.

 

The *n*-way [mergesort](./Mergesort) algorithm also begins by distributing the list into *n* sublists and sorting each one; however, the sublists created by mergesort have overlapping value ranges and so cannot be recombined by simple concatenation as in bucket sort. Instead, they must be interleaved by a merge algorithm. However, this added expense is counterbalanced by the simpler scatter phase and the ability to ensure that each sublist is the same size, providing a good worst-case time bound.

 

Top-down [radix sort](./Radix_sort) can be seen as a special case of bucket sort where both the range of values and the number of buckets is constrained to be a power of two. Consequently, each bucket's size is also a power of two, and the procedure can be applied recursively. This approach can accelerate the scatter phase, since we only need to examine a prefix of the bit representation of each element to determine its bucket.

 

## References

 
1. [1](./Bucket_sort#cite_ref-lfcs_1-0) [2](./Bucket_sort#cite_ref-lfcs_1-1) [Thomas H. Cormen](./Thomas_H._Cormen); [Charles E. Leiserson](./Charles_E._Leiserson); [Ronald L. Rivest](./Ronald_L._Rivest) & [Clifford Stein](./Clifford_Stein). *[Introduction to Algorithms](./Introduction_to_Algorithms)*. Bucket sort runs in linear time on the average. Like counting sort, bucket sort is fast because it assumes something about the input. Whereas counting sort assumes that the input consists of integers in a small range, bucket sort assumes that the input is generated by a random process that distributes elements uniformly over the interval *[0,1)*. The idea of bucket sort is to divide the interval *[0, 1)* into *n* equal-sized subintervals, or buckets, and then distribute the *n* input numbers into the buckets. Since the inputs are uniformly distributed over *[0, 1)*, we don't expect many numbers to fall into each bucket. To produce the output, we simply sort the numbers in each bucket and then go through the buckets in order, listing the elements in each.
2. [↑](./Bucket_sort#cite_ref-2) Corwin, E. and Logar, A. "Sorting in linear time — variations on the bucket sort". *Journal of Computing Sciences in Colleges*, 20, 1, pp.197–202. October 2004.
3. [↑](./Bucket_sort#cite_ref-3) [Thomas H. Cormen](./Thomas_H._Cormen), [Charles E. Leiserson](./Charles_E._Leiserson), [Ronald L. Rivest](./Ronald_L._Rivest), and [Clifford Stein](./Clifford_Stein). *[Introduction to Algorithms](./Introduction_to_Algorithms)*, Second Edition. MIT Press and McGraw-Hill, 2001. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). Section 8.4: Bucket sort, pp.174–177.
4. [↑](./Bucket_sort#cite_ref-4) [NIST's Dictionary of Algorithms and Data Structures: histogram sort](https://xlinux.nist.gov/dads/HTML/histogramSort.html)
5. [↑](./Bucket_sort#cite_ref-Black2011_5-0) Black, Paul E., ed. (20 June 2011). ["postman's sort"](https://xlinux.nist.gov/dads/HTML/postmansort.html). *Dictionary of Algorithms and Data Structures*. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Retrieved 31 March 2026. ![Public Domain](//upload.wikimedia.org/wikipedia/en/thumb/6/62/PD-icon.svg/20px-PD-icon.svg.png) This article incorporates text from this source, which is in the [public domain](./Public_domain).
6. [↑](./Bucket_sort#cite_ref-Ramey1992_6-0) Ramey, Robert (August 1992). ["The Postman's Sort"](http://web.archive.org/web/20090628192742/https://rrsd.com/software_development/postmans_sort/cuj/cuj.htm). *[C/C++ Users Journal](./C/C++_Users_Journal)*. Archived from [the original](http://www.rrsd.com/psort/cuj/cuj.htm) on 28 June 2009.
7. [↑](./Bucket_sort#cite_ref-7) [A revolutionary new sort from John Cohen Nov 26, 1997](https://groups.google.com/group/fido7.ru.algorithms/msg/26084cdb04008ab3)

 
- [NIST's Dictionary of Algorithms and Data Structures: bucket sort](https://xlinux.nist.gov/dads/HTML/bucketsort.html)

 

## External links

 
- [Bucket Sort Code for Ansi C](http://www.dcc.uchile.cl/~rbaeza/handbook/algs/4/423.sort.c.html)
- [Variant of Bucket Sort with Demo](http://www1bpt.bridgeport.edu/~dichter/lilly/bucketsort.htm)

 
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