---
source: https://en.wikipedia.org/wiki/Kadane%27s_algorithm
fetched: 2026-06-19
---

Problem in computer science [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/25/Maximum_Subarray_Visualization.svg/250px-Maximum_Subarray_Visualization.svg.png)](./File:Maximum_Subarray_Visualization.svg)Visualization of how sub-arrays change based on start and end positions of a sub-array. Each colored line corresponds to a fixed starting index in the array. The leftmost point of a line represents the single-element sub-array starting at that index, and each subsequent point extends the sub-array by one element to the right. The x-coordinate of a point is the index of the last element in the sub-array, and the y-coordinate is the sum of the sub-array. In this case, the original array from which sub-arrays are taken is [2, 3, -1, -20, 5, 10]. 

In [computer science](./Computer_science), the **maximum sum subarray problem**, also known as the **maximum segment sum problem**, is the task of finding a contiguous subarray with the largest sum, within a given one-dimensional [array](./Array_data_structure) A[1...n] of numbers. It can be solved in     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time and     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) space.

 

Formally, the task is to find indices     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) and     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) with     1 ≤ ≤  i ≤ ≤  j ≤ ≤  n   {\displaystyle 1\leq i\leq j\leq n}  ![{\displaystyle 1\leq i\leq j\leq n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95763b48b784f1cd453a4dc4a2c2f39e22997a43), such that the sum

      ∑ ∑   x = i   j   A [ x ]   {\displaystyle \sum _{x=i}^{j}A[x]}  ![{\displaystyle \sum _{x=i}^{j}A[x]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3f4ae4590a685044ab6ba7cc8b23cc7c57f5689e) 

is as large as possible. (Some formulations of the problem also allow the empty subarray to be considered; by convention, [the sum of all values of the empty subarray](./Empty_sum) is zero.)  Each number in the input array A could be positive, negative, or zero.[[1]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198969-1)

 

For example, for the array of values [−2, 1, −3, 4, −1, 2, 1, −5, 4], the contiguous subarray with the largest sum is [4, −1, 2, 1], with sum 6.

 

Some properties of this problem are: 

 
1. If the array contains all non-negative numbers, then the problem is trivial; a maximum subarray is the entire array.
2. If the array contains all non-positive numbers, then a solution is any subarray of size 1 containing the maximal value of the array (or the empty subarray, if it is permitted).
3. Several different sub-arrays may have the same maximum sum.

 

Although this problem can be solved using several different algorithmic techniques, including [brute force](./Brute-force_search),[[2]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198970-2) [divide and conquer](./Divide-and-conquer_algorithm),[[3]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198973-3) [dynamic programming](./Dynamic_programming),[[4]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198974-4) and reduction to shortest paths, a simple single-pass algorithm known as Kadane's algorithm solves it efficiently.

 

## History

 

The maximum subarray problem was proposed by [Ulf Grenander](./Ulf_Grenander) in 1977 as a simplified model for [maximum likelihood estimation](./Maximum_likelihood_estimation) of patterns in digitized images.[[5]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley1984868-869-5)

 

Grenander was looking to find a rectangular subarray with maximum sum, in a two-dimensional array of real numbers.  A brute-force algorithm for the two-dimensional problem runs in *O*(*n*6) time; because this was prohibitively slow, Grenander proposed the one-dimensional problem to gain insight into its structure.  Grenander derived an algorithm that solves the one-dimensional problem in *O*(*n*2) time using [prefix sums](./Prefix_sum)[[note 1]](./Maximum_subarray_problem#cite_note-6), improving the brute force running time of *O*(*n*3). When [Michael Shamos](./Michael_Shamos) heard about the problem, he overnight devised an *O*(*n* log *n*) [divide-and-conquer algorithm](./Divide-and-conquer_algorithm) for it.
Soon after, Shamos described the one-dimensional problem and its history at a [Carnegie Mellon University](./Carnegie_Mellon_University) seminar attended by [Jay Kadane](./Jay_Kadane), who designed within a minute an *O*(*n*)-time algorithm,[[5]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley1984868-869-5)[[6]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198976-77-7)[[7]](./Maximum_subarray_problem#cite_note-FOOTNOTEGries1982211-8) which is as fast as possible.[[note 2]](./Maximum_subarray_problem#cite_note-9) In 1982, [David Gries](./David_Gries) obtained the same *O*(*n*)-time algorithm by applying [Dijkstra](./Edsger_W._Dijkstra)'s "standard strategy";[[8]](./Maximum_subarray_problem#cite_note-FOOTNOTEGries1982209-211-10) in 1989, [Richard Bird](./Richard_Bird_(computer_scientist)) derived it by purely algebraic manipulation of the brute-force algorithm using the [Bird–Meertens formalism](./Bird–Meertens_formalism).[[9]](./Maximum_subarray_problem#cite_note-FOOTNOTEBird1989Sect.8,_p.126-11)

 

Grenander's two-dimensional generalization can be solved in O(*n*3) time either by using Kadane's algorithm as a subroutine, or through a divide-and-conquer approach.  Slightly faster algorithms based on [distance matrix multiplication](./Min-plus_matrix_multiplication) have been proposed by [Tamaki & Tokuyama (1998)](./Maximum_subarray_problem#CITEREFTamakiTokuyama1998) and by [Takaoka (2002)](./Maximum_subarray_problem#CITEREFTakaoka2002). There is some evidence that no significantly faster algorithm exists; an algorithm that solves the two-dimensional maximum subarray problem in O(*n*3−ε) time, for any ε>0, would imply a similarly fast algorithm for the [all-pairs shortest paths](./Shortest_path_problem#All-pairs_shortest_paths) problem.[[10]](./Maximum_subarray_problem#cite_note-FOOTNOTEBackursDikkalaTzamos2016-12)

 

## Applications

 

Maximum subarray problems arise in many fields, such as genomic [sequence analysis](./Sequence_analysis) and [computer vision](./Computer_vision).

 

Genomic sequence analysis employs maximum subarray algorithms to identify important biological segments of protein sequences that have unusual properties, by assigning scores to points within the sequence that are positive when a motif to be recognized is present, and negative when it is not, and then seeking the maximum subarray among these scores. These problems include conserved segments, GC-rich regions, tandem repeats, low-complexity filter, DNA binding domains, and regions of high charge.[[11]](./Maximum_subarray_problem#cite_note-13)

 

In [computer vision](./Computer_vision), bitmap images generally consist only of positive values, for which the maximum subarray problem is trivial: the result is always the whole array. However, after subtracting a threshold value (such as the average pixel value) from each pixel, so that above-average pixels will be positive and below-average pixels will be negative, the maximum subarray problem can be applied to the modified image to detect bright areas within it.[[12]](./Maximum_subarray_problem#cite_note-14)

 

## Kadane's algorithm

 

### No empty subarrays admitted

 

[Kadane's](./Joseph_Born_Kadane) algorithm scans the given array     A [ 1 … …  n ]   {\displaystyle A[1\ldots n]}  ![{\displaystyle A[1\ldots n]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e3d1923568ccfdc916c6cd1c84cb282a32af9074) from left to right. 
In the     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)th step, it computes the subarray with the largest sum ending at     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0); this sum is maintained in variable `current_sum`.[[note 3]](./Maximum_subarray_problem#cite_note-15)
Moreover, it computes the subarray with the largest sum anywhere in     A [ 1 … …  j ]   {\displaystyle A[1\ldots j]}  ![{\displaystyle A[1\ldots j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f81bf04402d996fbf9efe4c9e68c68d804022adf), maintained in variable `best_sum`,[[note 4]](./Maximum_subarray_problem#cite_note-16)
and easily obtained as the maximum of all values of `current_sum` seen so far, cf. line 7 of the algorithm.

 

As a [loop invariant](./Loop_invariant), in the     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)th step, the old value of `current_sum` holds the maximum over all     i ∈ ∈  { 1 , … …  , j − −  1 }   {\displaystyle i\in \{1,\ldots ,j-1\}}  ![{\displaystyle i\in \{1,\ldots ,j-1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98fd84c4688669f1ab56401080bd566b4be35ba6) of the sum     A [ i ] + ⋯ ⋯  + A [ j − −  1 ]   {\displaystyle A[i]+\cdots +A[j-1]}  ![{\displaystyle A[i]+\cdots +A[j-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d953b5c43fc85b567297a449586a6aa761a6c83).
Therefore, `current_sum`    + A [ j ]   {\displaystyle +A[j]}  ![{\displaystyle +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f276f74cd74ae67e23c51b1e9ef3764c5798adfd)[[note 5]](./Maximum_subarray_problem#cite_note-17)
is the maximum over all     i ∈ ∈  { 1 , … …  , j − −  1 }   {\displaystyle i\in \{1,\ldots ,j-1\}}  ![{\displaystyle i\in \{1,\ldots ,j-1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98fd84c4688669f1ab56401080bd566b4be35ba6) of the sum     A [ i ] + ⋯ ⋯  + A [ j ]   {\displaystyle A[i]+\cdots +A[j]}  ![{\displaystyle A[i]+\cdots +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce9a7a1d7259eb0056fc37f9bed9219049cb8cde). To extend the latter maximum to also cover the case     i = j   {\displaystyle i=j}  ![{\displaystyle i=j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/706e0928b2bf0f24076b0c90bb20616ff2068343), it is sufficient to also consider the singleton subarray     A [ j  … …   j ]   {\displaystyle A[j\;\ldots \;j]}  ![{\displaystyle A[j\;\ldots \;j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/551bbbcd4e8a7a11d988f828dc1c574b73d32c59). This is done in line 6 by assigning     max ( A [ j ] ,   {\displaystyle \max(A[j],}  ![{\displaystyle \max(A[j],}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a855fb0a19d2d6af178dffdd6b9160523d0f4647)`current_sum`    + A [ j ] )   {\displaystyle +A[j])}  ![{\displaystyle +A[j])}](https://wikimedia.org/api/rest_v1/media/math/render/svg/188c430a18abd0a38d9b527d13d3abd631d0d51e) as the new value of `current_sum`, which after that holds the maximum over all     i ∈ ∈  { 1 , … …  , j }   {\displaystyle i\in \{1,\ldots ,j\}}  ![{\displaystyle i\in \{1,\ldots ,j\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8304cdc726f60e272d99f7c4f36a6ab651370d9) of the sum     A [ i ] + ⋯ ⋯  + A [ j ]   {\displaystyle A[i]+\cdots +A[j]}  ![{\displaystyle A[i]+\cdots +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce9a7a1d7259eb0056fc37f9bed9219049cb8cde).

 

Thus, the problem can be solved with the following code,[[13]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198978,171-18) expressed in [Python](./Python_(programming_language)). 

 
```
def max_subarray(numbers):
    """Find the largest sum of any contiguous subarray."""
    best_sum = float('-inf')
    current_sum = 0
    for x in numbers:
        current_sum = max(x, current_sum + x)
        best_sum = max(best_sum, current_sum)
    return best_sum

```
 

If the input contains no positive element, the returned value is that of the largest element (i.e., the value closest to 0), or negative infinity if the input was empty. For correctness, an exception should be raised when the input array is empty, since an empty array has no maximum nonempty subarray. If the array is nonempty, its first element could be used in place of negative infinity, if needed to avoid mixing numeric and non-numeric values.

 

The algorithm can be adapted to the case which allows empty subarrays or to keep track of the starting and ending indices of the maximum subarray.

 

This algorithm calculates the maximum subarray ending at each position from the maximum subarray ending at the previous position, so it can be viewed as a case of [dynamic programming](./Dynamic_programming).

 

### Empty subarrays admitted

 
| Example run |
| --- |
| Execution of Kadane's algorithm on theaboveexample array.Blue:subarray with largest sum ending ati;green:subarray with largest sum encountered so far; a lower case letter indicates an empty array; variableiis left implicit in Python code. |

 

Kadane's algorithm, as originally published, is for solving the problem variant which allows empty subarrays.[[4]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198974-4)[[7]](./Maximum_subarray_problem#cite_note-FOOTNOTEGries1982211-8) 
In such a variant, the answer is 0 when the input contains no positive elements (including when the input is empty).
The variant is obtained with two changes in code: in line 3, `best_sum` should be initialized to 0 to account for the empty subarray     A [ 0 … …  − −  1 ]   {\displaystyle A[0\ldots -1]}  ![{\displaystyle A[0\ldots -1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82f6afaff54a6e361dfa24af514883b91fe5967f)

 
```
    best_sum = 0;

```
 

and line 6 in the for loop `current_sum` should be updated to `max(0, current_sum + x)`.[[note 6]](./Maximum_subarray_problem#cite_note-19)

 
```
        current_sum = max(0, current_sum + x)

```
 

As a [loop invariant](./Loop_invariant), in the     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)th step, the old value of `current_sum` holds the maximum over all     i ∈ ∈  { 1 , … …  , j }   {\displaystyle i\in \{1,\ldots ,j\}}  ![{\displaystyle i\in \{1,\ldots ,j\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8304cdc726f60e272d99f7c4f36a6ab651370d9) of the sum     A [ i ] + ⋯ ⋯  + A [ j − −  1 ]   {\displaystyle A[i]+\cdots +A[j-1]}  ![{\displaystyle A[i]+\cdots +A[j-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d953b5c43fc85b567297a449586a6aa761a6c83).[[note 7]](./Maximum_subarray_problem#cite_note-20)
Therefore, `current_sum`    + A [ j ]   {\displaystyle +A[j]}  ![{\displaystyle +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f276f74cd74ae67e23c51b1e9ef3764c5798adfd)
is the maximum over all     i ∈ ∈  { 1 , … …  , j }   {\displaystyle i\in \{1,\ldots ,j\}}  ![{\displaystyle i\in \{1,\ldots ,j\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8304cdc726f60e272d99f7c4f36a6ab651370d9) of the sum     A [ i ] + ⋯ ⋯  + A [ j ]   {\displaystyle A[i]+\cdots +A[j]}  ![{\displaystyle A[i]+\cdots +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce9a7a1d7259eb0056fc37f9bed9219049cb8cde). To extend the latter maximum to also cover the case     i = j + 1   {\displaystyle i=j+1}  ![{\displaystyle i=j+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c929824b3149ba99292d6c5e04e9e22262c78295), it is sufficient to also consider the empty subarray     A [ j + 1  … …   j ]   {\displaystyle A[j+1\;\ldots \;j]}  ![{\displaystyle A[j+1\;\ldots \;j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4e7cbec3c9700cbffc27f7452cc996629800229e). This is done in line 6 by assigning     max ( 0 ,   {\displaystyle \max(0,}  ![{\displaystyle \max(0,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/90441ccc647a71d730f3b2c3db44e04784fbe6e9)`current_sum`    + A [ j ] )   {\displaystyle +A[j])}  ![{\displaystyle +A[j])}](https://wikimedia.org/api/rest_v1/media/math/render/svg/188c430a18abd0a38d9b527d13d3abd631d0d51e) as the new value of `current_sum`, which after that holds the maximum over all     i ∈ ∈  { 1 , … …  , j + 1 }   {\displaystyle i\in \{1,\ldots ,j+1\}}  ![{\displaystyle i\in \{1,\ldots ,j+1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d13ec7bc1287e6f265cff33a15a440c57c92bb5) of the sum     A [ i ] + ⋯ ⋯  + A [ j ]   {\displaystyle A[i]+\cdots +A[j]}  ![{\displaystyle A[i]+\cdots +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce9a7a1d7259eb0056fc37f9bed9219049cb8cde). Machine-verified [C](./C_(programming_language)) / [Frama-C](./Frama-C) code of both variants can be found [here](https://commons.wikimedia.org/wiki/File:Kadane%20run%20−2,1,−3,4,−1,2,1,−5,4.gif#Source_code).

 

### Computing the best subarray's position

 

The algorithm can be modified to keep track of the starting and ending indices of the maximum subarray as well.

 

Because of the way this algorithm uses optimal substructures (the maximum subarray ending at each position is calculated in a simple way from a related but smaller and [overlapping subproblem](./Overlapping_subproblems): the maximum subarray ending at the previous position) this algorithm can be viewed as a simple/trivial example of [dynamic programming](./Dynamic_programming).

 

### Complexity

 

The runtime complexity of Kadane's algorithm is     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) and its [space complexity](./Space_complexity) is     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21).[[4]](./Maximum_subarray_problem#cite_note-FOOTNOTEBentley198974-4)[[7]](./Maximum_subarray_problem#cite_note-FOOTNOTEGries1982211-8)

 

## Generalizations

 

Similar problems may be posed for higher-dimensional arrays, but their solutions are more complicated; see, e.g., [Takaoka (2002)](./Maximum_subarray_problem#CITEREFTakaoka2002). [Brodal & Jørgensen (2007)](./Maximum_subarray_problem#CITEREFBrodalJørgensen2007) showed how to find the *k* largest subarray sums in a one-dimensional array, in the optimal time bound     O ( n + k )   {\displaystyle O(n+k)}  ![{\displaystyle O(n+k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cebd2e4442e56daa59f3fab79339f952122c29e8).

 

The Maximum sum *k*-disjoint subarrays can also be computed in the optimal time bound     O ( n + k )   {\displaystyle O(n+k)}  ![{\displaystyle O(n+k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cebd2e4442e56daa59f3fab79339f952122c29e8) 
.[[14]](./Maximum_subarray_problem#cite_note-FOOTNOTEBengtssonChen2007-21)

 

## See also

 
- [Subset sum problem](./Subset_sum_problem)

 

## Notes

 
1. [↑](./Maximum_subarray_problem#cite_ref-6) By using a precomputed table of cumulative sums     S [ k ] =  ∑ ∑   x = 1   k   A [ x ]   {\displaystyle S[k]=\sum _{x=1}^{k}A[x]}  ![{\displaystyle S[k]=\sum _{x=1}^{k}A[x]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ec8da87a55750ee8f1489589facd90c9bb8bfee) to compute the subarray sum      ∑ ∑   x = i   j   A [ x ] = S [ j ] − −  S [ i − −  1 ]   {\displaystyle \sum _{x=i}^{j}A[x]=S[j]-S[i-1]}  ![{\displaystyle \sum _{x=i}^{j}A[x]=S[j]-S[i-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a5eaeb881301c21c223bcda980954ff927f9f6b9) in constant time

2. [↑](./Maximum_subarray_problem#cite_ref-9) since every algorithm must at least scan the array once which already takes *O*(*n*) time
3. [↑](./Maximum_subarray_problem#cite_ref-15) named `MaxEndingHere` in [Bentley (1989)](./Maximum_subarray_problem#CITEREFBentley1989), and `c` in [Gries (1982)](./Maximum_subarray_problem#CITEREFGries1982) 
4. [↑](./Maximum_subarray_problem#cite_ref-16) named `MaxSoFar` in [Bentley (1989)](./Maximum_subarray_problem#CITEREFBentley1989), and `s` in [Gries (1982)](./Maximum_subarray_problem#CITEREFGries1982) 
5. [↑](./Maximum_subarray_problem#cite_ref-17) 
In the Python code below,     A [ j ]   {\displaystyle A[j]}  ![{\displaystyle A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c385fd9b0f771529e587f216f3f15d52bb85ef6) is expressed as `x`, with the index     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) left implicit.

6. [↑](./Maximum_subarray_problem#cite_ref-19) While [Bentley (1989)](./Maximum_subarray_problem#CITEREFBentley1989) does not mention this difference, using `x` instead of `0` in the [above](./Maximum_subarray_problem#No_empty_subarrays_admitted) version without empty subarrays achieves maintaining its loop invariant `current_sum`    =  max  i ∈ ∈  { 1 , . . . , j − −  1 }   A [ i ] + . . . + A [ j − −  1 ]   {\displaystyle =\max _{i\in \{1,...,j-1\}}A[i]+...+A[j-1]}  ![{\displaystyle =\max _{i\in \{1,...,j-1\}}A[i]+...+A[j-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ae4f8fa152635b5691ae02d4a939fdf55c0c460a) at the beginning of the     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)th step.

7. [↑](./Maximum_subarray_problem#cite_ref-20) This sum is     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) when     i = j   {\displaystyle i=j}  ![{\displaystyle i=j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/706e0928b2bf0f24076b0c90bb20616ff2068343), corresponding to the empty subarray     A [ j … …  j − −  1 ]   {\displaystyle A[j\ldots j-1]}  ![{\displaystyle A[j\ldots j-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aacd5b052234fec25693efb7c84dd6839025a9fc).

 

## Notes

  
1. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198969_1-0) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 69.
2. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198970_2-0) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 70.
3. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198973_3-0) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 73.
4. [1](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198974_4-0) [2](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198974_4-1) [3](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198974_4-2) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 74.
5. [1](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley1984868-869_5-0) [2](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley1984868-869_5-1) [Bentley 1984](./Maximum_subarray_problem#CITEREFBentley1984), p. 868-869.
6. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198976-77_7-0) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 76-77.
7. [1](./Maximum_subarray_problem#cite_ref-FOOTNOTEGries1982211_8-0) [2](./Maximum_subarray_problem#cite_ref-FOOTNOTEGries1982211_8-1) [3](./Maximum_subarray_problem#cite_ref-FOOTNOTEGries1982211_8-2) [Gries 1982](./Maximum_subarray_problem#CITEREFGries1982), p. 211.
8. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEGries1982209-211_10-0) [Gries 1982](./Maximum_subarray_problem#CITEREFGries1982), p. 209-211.
9. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBird1989Sect.8,_p.126_11-0) [Bird 1989](./Maximum_subarray_problem#CITEREFBird1989), Sect.8, p.126.
10. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBackursDikkalaTzamos2016_12-0) [Backurs, Dikkala & Tzamos 2016](./Maximum_subarray_problem#CITEREFBackursDikkalaTzamos2016).
11. [↑](./Maximum_subarray_problem#cite_ref-13) [Ruzzo & Tompa (1999)](./Maximum_subarray_problem#CITEREFRuzzoTompa1999); [Alves, Cáceres & Song (2004)](./Maximum_subarray_problem#CITEREFAlvesCáceresSong2004)
12. [↑](./Maximum_subarray_problem#cite_ref-14) [Bae & Takaoka (2006)](./Maximum_subarray_problem#CITEREFBaeTakaoka2006); [Weddell et al. (2013)](./Maximum_subarray_problem#CITEREFWeddellReadThaherTakaoka2013)
13. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBentley198978,171_18-0) [Bentley 1989](./Maximum_subarray_problem#CITEREFBentley1989), p. 78,171. Bentley, like Gries, first introduces the variant admitting empty subarrays, see [below](./Maximum_subarray_problem#Empty_subarrays_admitted), and describes only the changes.
14. [↑](./Maximum_subarray_problem#cite_ref-FOOTNOTEBengtssonChen2007_21-0) [Bengtsson & Chen 2007](./Maximum_subarray_problem#CITEREFBengtssonChen2007).

 

## References

 
- Alves, Carlos E. R.; Cáceres, Edson; Song, Siang W. (2004), "BSP/CGM Algorithms for Maximum Subsequence and Maximum Subarray", in Kranzlmüller, Dieter; Kacsuk, Péter; Dongarra, Jack J. (eds.), *Recent Advances in Parallel Virtual Machine and Message Passing Interface, 11th European PVM/MPI Users' Group Meeting, Budapest, Hungary, September 19-22, 2004, Proceedings*, Lecture Notes in Computer Science, vol. 3241, Springer, pp. 139–146, [doi](./Doi_(identifier)):[10.1007/978-3-540-30218-6_24](https://doi.org/10.1007%2F978-3-540-30218-6_24), [ISBN](./ISBN_(identifier)) [978-3-540-23163-9](./Special:BookSources/978-3-540-23163-9)
- Backurs, Arturs; Dikkala, Nishanth; Tzamos, Christos (2016), "Tight Hardness Results for Maximum Weight Rectangles", *43rd International Colloquium on Automata, Languages, and Programming (ICALP 2016)*, Leibniz International Proceedings in Informatics (LIPIcs), vol. 55, Schloss Dagstuhl – Leibniz-Zentrum für Informatik, pp. 81:1–81:13, [doi](./Doi_(identifier)):[10.4230/LIPIcs.ICALP.2016.81](https://doi.org/10.4230%2FLIPIcs.ICALP.2016.81), [ISBN](./ISBN_(identifier)) [978-3-95977-013-2](./Special:BookSources/978-3-95977-013-2), [S2CID](./S2CID_(identifier)) [12720136](https://api.semanticscholar.org/CorpusID:12720136)
- Bae, Sung Eun (2007), [*Sequential and Parallel Algorithms for the Generalized Maximum Subarray Problem*](https://web.archive.org/web/20171026110814/https://pdfs.semanticscholar.org/bea4/1795adaf240b9db4195b9dc511bd8d46bff1.pdf) (PDF) (Ph.D. thesis), University of Canterbury, [S2CID](./S2CID_(identifier)) [2681670](https://api.semanticscholar.org/CorpusID:2681670), archived from [the original](https://pdfs.semanticscholar.org/bea4/1795adaf240b9db4195b9dc511bd8d46bff1.pdf) (PDF) on 2017-10-26.
- Bae, Sung Eun; Takaoka, Tadao (2006), "Improved Algorithms for the \emph{K}-Maximum Subarray Problem", *The Computer Journal*, **49** (3): 358–374, [doi](./Doi_(identifier)):[10.1093/COMJNL/BXL007](https://doi.org/10.1093%2FCOMJNL%2FBXL007)
- Bengtsson, Fredrik; Chen, Jingsen (2007), [*Computing maximum-scoring segments optimally*](http://ltu.diva-portal.org/smash/get/diva2:995901/FULLTEXT01.pdf) (PDF) (Research report), Luleå University of Technology
- [Bentley, Jon](./Jon_Bentley_(computer_scientist)) (1984), "Programming Pearls: Algorithm Design Techniques", *[Communications of the ACM](./Communications_of_the_ACM)*, **27** (9): 865–873, [doi](./Doi_(identifier)):[10.1145/358234.381162](https://doi.org/10.1145%2F358234.381162), [S2CID](./S2CID_(identifier)) [207565329](https://api.semanticscholar.org/CorpusID:207565329)
- Bentley, Jon (May 1989), [*Programming Pearls*](https://archive.org/details/programmingpearl00bent) (2nd? ed.), Reading, MA: Addison Wesley, [ISBN](./ISBN_(identifier)) [0-201-10331-1](./Special:BookSources/0-201-10331-1)
- [Bird, Richard S.](./Richard_S._Bird) (1989), "Algebraic Identities for Program Calculation", *[The Computer Journal](./The_Computer_Journal)*, **32** (2): 122–126, [doi](./Doi_(identifier)):[10.1093/comjnl/32.2.122](https://doi.org/10.1093%2Fcomjnl%2F32.2.122)
- Brodal, Gerth Stølting; Jørgensen, Allan Grønlund (2007), "A linear time algorithm for the *k* maximal sums problem", *Mathematical Foundations of Computer Science 2007*, Lecture Notes in Computer Science, vol. 4708, Springer-Verlag, pp. 442–453, [doi](./Doi_(identifier)):[10.1007/978-3-540-74456-6_40](https://doi.org/10.1007%2F978-3-540-74456-6_40), [ISBN](./ISBN_(identifier)) [978-3-540-74455-9](./Special:BookSources/978-3-540-74455-9).
- Gries, David (1982), ["A Note on the Standard Strategy for Developing Loop Invariants and Loops"](https://www.sciencedirect.com/science/article/pii/0167642383900151), *Science of Computer Programming*, **2** (3): 207–241, [doi](./Doi_(identifier)):[10.1016/0167-6423(83)90015-1](https://doi.org/10.1016%2F0167-6423%2883%2990015-1), [hdl](./Hdl_(identifier)):[1813/6370](https://hdl.handle.net/1813%2F6370)
- Ruzzo, Walter L.; Tompa, Martin (1999), ["A Linear Time Algorithm for Finding All Maximal Scoring Subsequences"](https://www.aaai.org/Library/ISMB/1999/ismb99-027.php), in Lengauer, Thomas; Schneider, Reinhard; Bork, Peer; Brutlag, Douglas L.; Glasgow, Janice I.; Mewes, Hans-Werner; Zimmer, Ralf (eds.), *Proceedings of the Seventh International Conference on Intelligent Systems for Molecular Biology, August 6–10, 1999, Heidelberg, Germany*, AAAI, pp. 234–241
- Takaoka, Tadao (2002), "Efficient algorithms for the maximum subarray problem by distance matrix multiplication", *Electronic Notes in Theoretical Computer Science*, **61**: 191–200, [doi](./Doi_(identifier)):[10.1016/S1571-0661(04)00313-5](https://doi.org/10.1016%2FS1571-0661%2804%2900313-5).
- Tamaki, Hisao; Tokuyama, Takeshi (1998), ["Algorithms for the Maximum Subarray Problem Based on Matrix Multiplication"](http://dl.acm.org/citation.cfm?id=314613.314823), *Proceedings of the 9th Symposium on Discrete Algorithms (SODA)*: 446–452, [ISBN](./ISBN_(identifier)) [978-0-89871-410-4](./Special:BookSources/978-0-89871-410-4), retrieved November 17, 2018`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
- Weddell, Stephen John; Read, Tristan; Thaher, Mohammed; Takaoka, Tadao (2013), "Maximum subarray algorithms for use in astronomical imaging", *Journal of Electronic Imaging*, **22** (4) 043011, [Bibcode](./Bibcode_(identifier)):[2013JEI....22d3011W](https://ui.adsabs.harvard.edu/abs/2013JEI....22d3011W), [doi](./Doi_(identifier)):[10.1117/1.JEI.22.4.043011](https://doi.org/10.1117%2F1.JEI.22.4.043011)

 

## External links

 
- TAN, Lirong. ["Maximum Contiguous Subarray Sum Problems"](https://web.archive.org/web/20151010072051/http://www.picb.ac.cn/~xiaohang/vimwiki/study/tanlirong/Algorithm/project/Report.pdf) (PDF). Archived from [the original](http://www.picb.ac.cn/~xiaohang/vimwiki/study/tanlirong/Algorithm/project/Report.pdf) (PDF) on 2015-10-10. Retrieved 2017-10-26.
- Mu, Shin-Cheng (2010). ["The Maximum Segment Sum Problem: Its Origin, and a Derivation"](https://www.iis.sinica.edu.tw/~scm/2010/maximum-segment-sum-origin-and-derivation).
- ["Notes on Maximum Subarray Problem"](http://cs.slu.edu/~goldwamh/courses/slu/csci314/2012_Fall/lectures/maxsubarray/). 2012.
- [www.algorithmist.com](http://www.algorithmist.com/index.php/Kadane's_Algorithm)
- [alexeigor.wikidot.com](http://alexeigor.wikidot.com/kadane)
- [greatest subsequential sum problem on Rosetta Code](http://rosettacode.org/wiki/Greatest_subsequential_sum)
- [geeksforgeeks page on Kadane's Algorithm](https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/)