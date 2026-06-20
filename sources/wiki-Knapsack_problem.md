---
source: https://en.wikipedia.org/wiki/Knapsack_problem
fetched: 2026-06-19
---

Problem in combinatorial optimization [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/68/Knapsack_Problem_Illustration.svg/330px-Knapsack_Problem_Illustration.svg.png)](./File:Knapsack_Problem_Illustration.svg)Example of a one-dimensional (constraint) knapsack problem: which books should be chosen to maximize the books' value while still keeping the overall weight under or equal to 15 kg? A [multiple constrained problem](./List_of_knapsack_problems#Multiple_constraints) could consider both the weight and volume of the books. 
(Solution: if any number of each book is available, then three yellow books and three grey books; if only the shown books are available, then all except for the green book.) 

The **knapsack problem** is the following problem in [combinatorial optimization](./Combinatorial_optimization):

 *Given a set of items, each with a weight and a value, determine which items to include in the collection so that the total weight is less than or equal to a given limit and the total value is as large as possible.* 

It derives its name from the problem faced by someone who is constrained by a fixed-size [knapsack](./Knapsack) and must fill it with the most valuable items. The problem often arises in [resource allocation](./Resource_allocation) where the decision-makers have to choose from a set of non-divisible projects or tasks under a fixed budget or time constraint, respectively.

 

The knapsack problem has been studied for more than a century, with early works dating back to 1897.[[1]](./Knapsack_problem#cite_note-1)

 

The [subset sum problem](./Subset_sum_problem) is a special case of the decision and 0-1 problems where for each kind of item, the weight equals the value:      w  i   =  v  i     {\displaystyle w_{i}=v_{i}}  ![{\displaystyle w_{i}=v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5d3d122e68e9e655b00d819401bfde5983100797). In the field of [cryptography](./Cryptography), the term *knapsack problem* is often used to refer specifically to the subset sum problem. The subset sum problem is one of [Karp's 21 NP-complete problems](./Karp's_21_NP-complete_problems).[[2]](./Knapsack_problem#cite_note-2)

 

## Applications

 

Knapsack problems appear in real-world decision-making processes in a wide variety of fields, such as finding the least wasteful way to cut raw materials,[[3]](./Knapsack_problem#cite_note-3) selection of [investments](./Fixed_investment) and [portfolios](./Portfolio_(finance)),[[4]](./Knapsack_problem#cite_note-4) selection of assets for [asset-backed securitization](./Securitization),[[5]](./Knapsack_problem#cite_note-5) and generating keys for the [Merkle–Hellman](./Merkle–Hellman_knapsack_cryptosystem)[[6]](./Knapsack_problem#cite_note-6) and other [knapsack cryptosystems](./Knapsack_cryptosystems).

 

One early application of knapsack algorithms was in the construction and scoring of tests in which the test-takers have a choice as to which questions they answer. For small examples, it is a fairly simple process to provide the test-takers with such a choice. For example, if an exam contains 12 questions each worth 10 points, the test-taker need only answer 10 questions to achieve a maximum possible score of 100 points. However, on tests with a heterogeneous distribution of point values, it is more difficult to provide choices. Feuerman and Weiss proposed a system in which students are given a heterogeneous test with a total of 125 possible points. The students are asked to answer all of the questions to the best of their abilities. Of the possible subsets of problems whose total point values add up to 100, a knapsack algorithm would determine which subset gives each student the highest possible score.[[7]](./Knapsack_problem#cite_note-7)

 

A 1999 study of the Stony Brook University Algorithm Repository showed that, out of 75 algorithmic problems related to the field of combinatorial algorithms and algorithm engineering, the knapsack problem was the 19th most popular and the third most needed after [suffix trees](./Suffix_tree) and the [bin packing problem](./Bin_packing_problem).[[8]](./Knapsack_problem#cite_note-8)

 

## Definition

 

The most common problem being solved is the **0-1 knapsack problem**, which restricts the number *     x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158)* of copies of each kind of item to zero or one. Given a set of *    n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)* items numbered from 1 up to *    n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)*, each with a weight *     w  i     {\displaystyle w_{i}}  ![{\displaystyle w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe22f0329d3ecb2e1880d44d191aba0e5475db68)* and a value *     v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127)*, along with a maximum weight capacity *    W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7)*,

 maximize      ∑ ∑   i = 1   n    v  i    x  i     {\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}  ![{\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b) subject to      ∑ ∑   i = 1   n    w  i    x  i   ≤ ≤  W   {\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}  ![{\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176) and      x  i   ∈ ∈  { 0 , 1 }   {\displaystyle x_{i}\in \{0,1\}}  ![{\displaystyle x_{i}\in \{0,1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/07dda71da2a630762c7b21b51ea54f86f422f951). 

Here *     x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158)* represents the number of instances of item *    i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)* to include in the knapsack. Informally, the problem is to maximize the sum of the values of the items in the knapsack so that the sum of the weights is less than or equal to the knapsack's capacity.

 

The **bounded knapsack problem** (**BKP**) removes the restriction that there is only one of each item, but restricts the number      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158) of copies of each kind of item to a maximum non-negative integer value     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455):

 maximize      ∑ ∑   i = 1   n    v  i    x  i     {\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}  ![{\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b) subject to      ∑ ∑   i = 1   n    w  i    x  i   ≤ ≤  W   {\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}  ![{\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176) and      x  i   ∈ ∈  { 0 , 1 , 2 , … …  , c } .   {\displaystyle x_{i}\in \{0,1,2,\dots ,c\}.}  ![{\displaystyle x_{i}\in \{0,1,2,\dots ,c\}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67d086ac9e491ea240621847e94bdc3b2a1d2b7f) 

The **unbounded knapsack problem** (**UKP**) places no upper bound on the number of copies of each kind of item and can be formulated as above except that the only restriction on      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158) is that it is a non-negative integer.

 maximize      ∑ ∑   i = 1   n    v  i    x  i     {\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}  ![{\displaystyle \sum _{i=1}^{n}v_{i}x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/85620037d368d2136fb3361702df6a489416931b) subject to      ∑ ∑   i = 1   n    w  i    x  i   ≤ ≤  W   {\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}  ![{\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dd6e7c9bca4397980976ea6d19237500ce3b8176) and      x  i   ∈ ∈   N  .   {\displaystyle x_{i}\in \mathbb {N} .}  ![{\displaystyle x_{i}\in \mathbb {N} .}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f18ad3ffce3ee207e753e1ce76aab40434225416) 

One example of the unbounded knapsack problem is given using the figure shown at the beginning of this article and the text "if any number of each book is available" in the caption of that figure.

 

## Computational complexity

 

The knapsack problem is interesting from the perspective of computer science for many reasons:

 
- The [decision problem](./Decision_problem) form of the knapsack problem (*Can a value of at least *V* be achieved without exceeding the weight *W*?*) is [NP-complete](./NP-complete), thus there is no known algorithm that is both correct and fast (polynomial-time) in all cases.
- There is no known polynomial algorithm which can tell, given a solution, whether it is optimal (which would mean that there is no solution with a larger *V*). This problem is [co-NP-complete](./Co-NP-complete).
- There is a [pseudo-polynomial time](./Pseudo-polynomial_time) algorithm using [dynamic programming](./Dynamic_programming).
- There is a [fully polynomial-time approximation scheme](./Polynomial-time_approximation_scheme), which uses the pseudo-polynomial time algorithm as a subroutine, described below.
- Many cases that arise in practice, and "random instances" from some distributions, can nonetheless be solved exactly.

 

There is a link between the "decision" and "optimization" problems in that if there exists a polynomial algorithm that solves the  "decision" problem, then one can find the maximum value for the optimization problem in polynomial time by applying this algorithm iteratively while increasing the value of k. On the other hand, if an algorithm finds the optimal value of the optimization problem in polynomial time, then the decision problem can be solved in polynomial time by comparing the value of the solution output by this algorithm with the value of k. Thus, both versions of the problem are of similar difficulty.

 

One theme in research literature is to identify what the "hard" instances of the knapsack problem look like,[[9]](./Knapsack_problem#cite_note-pisinger200308-9)[[10]](./Knapsack_problem#cite_note-Cacetta2001-10) or viewed another way, to identify what properties of instances in practice might make them more amenable than their worst-case NP-complete behaviour suggests.[[11]](./Knapsack_problem#cite_note-poirriez_et_all_2009-11) The goal in finding these "hard" instances is for their use in [public-key cryptography](./Public-key_cryptography) systems, such as the [Merkle–Hellman knapsack cryptosystem](./Merkle–Hellman_knapsack_cryptosystem). More generally, better understanding of the structure of the space of instances of an optimization problem helps to advance the study of the particular problem and can improve algorithm selection.

 

Furthermore, notable is the fact that the hardness of the knapsack problem depends on the form of the input. If the weights and profits are given as integers, it is [weakly NP-complete](./Weakly_NP-complete), while it is [strongly NP-complete](./Strongly_NP-complete) if the weights and profits are given as rational numbers.[[12]](./Knapsack_problem#cite_note-Wojtczak18-12) However, in the case of rational weights and profits it still admits a [fully polynomial-time approximation scheme](./Polynomial-time_approximation_scheme).

 

### Unit-cost models

 

The NP-hardness of the Knapsack problem relates to computational models in which the size of integers matters (such as the [Turing machine](./Turing_machine)). In contrast, [decision trees](./Decision_tree_model) count each decision as a single step. Dobkin and Lipton[[13]](./Knapsack_problem#cite_note-13) show an       1 2    n  2     {\displaystyle {1 \over 2}n^{2}}  ![{\displaystyle {1 \over 2}n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3124d56fdcb27cfad21eff35ccb1f98ed39357b6) lower bound on linear decision trees for the knapsack problem, that is, trees where decision nodes test the sign of [affine functions](./Affine_function).[[14]](./Knapsack_problem#cite_note-14) This was generalized to algebraic decision trees by Steele and Yao.[[15]](./Knapsack_problem#cite_note-15)
If the elements in the problem are [real numbers](./Real_number) or [rationals](./Rationals), the decision-tree lower bound extends to the [real random-access machine](./Real_RAM) model with an instruction set that includes addition, subtraction and multiplication of real numbers, as well as comparison and either division or remaindering ("floor").[[16]](./Knapsack_problem#cite_note-16) This model covers more algorithms than the algebraic decision-tree model, as it encompasses algorithms that use indexing into tables. However, in this model all program steps are counted, not just decisions.
An *upper bound* for a decision-tree model was given by Meyer auf der Heide[[17]](./Knapsack_problem#cite_note-17) who showed that for every *n* there exists an *O*(*n*4)-deep linear decision tree that solves the [subset-sum problem](./Knapsack_problem#Subset-sum_problem) with *n* items. Note that this does not imply any upper bound for an algorithm that should solve the problem for *any given n*.

 

## Solving

 

Several algorithms are available to solve knapsack problems, based on the dynamic programming approach,[[18]](./Knapsack_problem#cite_note-eduk2000-18) the [branch and bound](./Branch_and_bound) approach[[19]](./Knapsack_problem#cite_note-martellototh90-19) or [hybridizations](./Hybrid_algorithm) of both approaches.[[11]](./Knapsack_problem#cite_note-poirriez_et_all_2009-11)[[20]](./Knapsack_problem#cite_note-martellopisingertoth99a-20)[[21]](./Knapsack_problem#cite_note-plateau85-21)[[22]](./Knapsack_problem#cite_note-martellotothe99-22)

 

### Dynamic programming in-advance algorithm

 

The **unbounded knapsack problem** (**UKP**) places no restriction on the number of copies of each kind of item. Besides, here we assume that      x  i   > 0   {\displaystyle x_{i}>0}  ![{\displaystyle x_{i}>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7ca010976c6eb10a9e66a4ec495766452bfe828)

     m [  w ′  ] = max  (   ∑ ∑   i = 1   n    v  i    x  i    )    {\displaystyle m[w']=\max \left(\sum _{i=1}^{n}v_{i}x_{i}\right)}  ![{\displaystyle m[w']=\max \left(\sum _{i=1}^{n}v_{i}x_{i}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0fb212a278752e5096827e4169957b9f97deeed7) subject to      ∑ ∑   i = 1   n    w  i    x  i   ≤ ≤   w ′    {\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq w'}  ![{\displaystyle \sum _{i=1}^{n}w_{i}x_{i}\leq w'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/71537a75e5abf64e1e6f19be93db861ef4e0222a) and      x  i   > 0   {\displaystyle x_{i}>0}  ![{\displaystyle x_{i}>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7ca010976c6eb10a9e66a4ec495766452bfe828) 

Observe that     m [ w ]   {\displaystyle m[w]}  ![{\displaystyle m[w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4f989722f439db408fa230d5a4a0e92841c6f088) has the following properties:

 

1.     m [ 0 ] = 0     {\displaystyle m[0]=0\,\!}  ![{\displaystyle m[0]=0\,\!}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fcb874d3e0ee718ca8002fc877af1b94a1e46c2e) (the sum of zero items, i.e., the summation of the [empty set](./Empty_set)).

 

2.     m [ w ] = max (  v  1   + m [ w − −   w  1   ] ,  v  2   + m [ w − −   w  2   ] , . . . ,  v  n   + m [ w − −   w  n   ] )   {\displaystyle m[w]=\max(v_{1}+m[w-w_{1}],v_{2}+m[w-w_{2}],...,v_{n}+m[w-w_{n}])}  ![{\displaystyle m[w]=\max(v_{1}+m[w-w_{1}],v_{2}+m[w-w_{2}],...,v_{n}+m[w-w_{n}])}](https://wikimedia.org/api/rest_v1/media/math/render/svg/762ebe580061e8b68803f8527f719650733a3ea2)
,      w  i   ≤ ≤  w   {\displaystyle w_{i}\leq w}  ![{\displaystyle w_{i}\leq w}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9918f9014b516f236f28c3dc9dda17e946033d5b), where      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) is the value of the     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th kind of item.

 

The second property needs to be explained in detail. During the process of the running of this method, how do we get the weight     w   {\displaystyle w}  ![{\displaystyle w}](https://wikimedia.org/api/rest_v1/media/math/render/svg/88b1e0c8e1be5ebe69d18a8010676fa42d7961e6)? There are only     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) ways and the previous weights are     w − −   w  1   , w − −   w  2   , . . . , w − −   w  i     {\displaystyle w-w_{1},w-w_{2},...,w-w_{i}}  ![{\displaystyle w-w_{1},w-w_{2},...,w-w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/93973016e85b824be2d07387f55829705a4a86f2) where there are total     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) kinds of different item (by saying different, we mean that the weight and the value are not completely the same). If we know each value of these     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) items and the related maximum value previously, we just compare them to each other and get the maximum value ultimately and we are done.

 

Here the maximum of the empty set is taken to be zero. Tabulating the results from     m [ 0 ]   {\displaystyle m[0]}  ![{\displaystyle m[0]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/420ffeb7cf30d5b19e19175a4ac404b6253bf780) up through     m [ W ]   {\displaystyle m[W]}  ![{\displaystyle m[W]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/00874bc364aa5a8b086b929be26181924d5a6e20) gives the solution. Since the calculation of each     m [ w ]   {\displaystyle m[w]}  ![{\displaystyle m[w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4f989722f439db408fa230d5a4a0e92841c6f088) involves examining at most     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) items, and there are at most     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7) values of     m [ w ]   {\displaystyle m[w]}  ![{\displaystyle m[w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4f989722f439db408fa230d5a4a0e92841c6f088) to calculate, the running time of the dynamic programming solution is [    O ( n W )   {\displaystyle O(nW)}  ![{\displaystyle O(nW)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e748dd6992ec4d942b90c5d6edb8fdd63b93688)](./Big_O_notation). Dividing      w  1   ,   w  2   ,  … …  ,   w  n   ,  W   {\displaystyle w_{1},\,w_{2},\,\ldots ,\,w_{n},\,W}  ![{\displaystyle w_{1},\,w_{2},\,\ldots ,\,w_{n},\,W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/696c0fc9828c2cdee9ad6352fb0e99b87b6c63ff) by their [greatest common divisor](./Greatest_common_divisor) is a way to improve the running time.

 

Even if [P≠NP](./P_versus_NP_problem), the     O ( n W )   {\displaystyle O(nW)}  ![{\displaystyle O(nW)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e748dd6992ec4d942b90c5d6edb8fdd63b93688) complexity does not contradict the fact that the knapsack problem is [NP-complete](./NP-complete), since     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7), unlike     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), is not polynomial in the length of the input to the problem. The length of the     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7) input to the problem is proportional to the number of bits in     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7),     log ⁡ ⁡  W   {\displaystyle \log W}  ![{\displaystyle \log W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c9b1e72cccb9d6e0bb4f2c4402754265e3e1a553), not to     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7) itself. However, since this runtime is [pseudopolynomial](./Pseudopolynomial), this makes the (decision version of the) knapsack problem a [weakly NP-complete problem](./Weak_NP-completeness).

 

#### 0-1 knapsack problem

 [![A demonstration of the dynamic programming approach.](//upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Knapsack_problem_dynamic_programming.gif/250px-Knapsack_problem_dynamic_programming.gif)](./File:Knapsack_problem_dynamic_programming.gif)A demonstration of the dynamic programming approach. 

A similar dynamic programming solution for the 0-1 knapsack problem also runs in pseudo-polynomial time. Assume      w  1   ,   w  2   ,  … …  ,   w  n   ,  W   {\displaystyle w_{1},\,w_{2},\,\ldots ,\,w_{n},\,W}  ![{\displaystyle w_{1},\,w_{2},\,\ldots ,\,w_{n},\,W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/696c0fc9828c2cdee9ad6352fb0e99b87b6c63ff) are strictly positive integers. Define     m [ i , w ]   {\displaystyle m[i,w]}  ![{\displaystyle m[i,w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8508d64cc83cae95ff73fa5a6e1a2bf4bfa43ca0) to be the maximum value that can be attained with weight less than or equal to     w   {\displaystyle w}  ![{\displaystyle w}](https://wikimedia.org/api/rest_v1/media/math/render/svg/88b1e0c8e1be5ebe69d18a8010676fa42d7961e6) using items up to     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) (first     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) items).

 

We can define     m [ i , w ]   {\displaystyle m[i,w]}  ![{\displaystyle m[i,w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8508d64cc83cae95ff73fa5a6e1a2bf4bfa43ca0) recursively as follows: **(Definition A)**

 
-     m [ 0 ,  w ] = 0   {\displaystyle m[0,\,w]=0}  ![{\displaystyle m[0,\,w]=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0f06328f369607d3af8d34792f350ac073b5180b)
-     m [ i ,  w ] = m [ i − −  1 ,  w ]   {\displaystyle m[i,\,w]=m[i-1,\,w]}  ![{\displaystyle m[i,\,w]=m[i-1,\,w]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/029b42757e9374349e8b6d7229040d11a8b5c544) if      w  i   > w     {\displaystyle w_{i}>w\,\!}  ![{\displaystyle w_{i}>w\,\!}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9135ba545782f152ca4c833311af638b13cc6aee) (the new item is more than the current weight limit)
-     m [ i ,  w ] = max ( m [ i − −  1 ,  w ] ,  m [ i − −  1 , w − −   w  i   ] +  v  i   )   {\displaystyle m[i,\,w]=\max(m[i-1,\,w],\,m[i-1,w-w_{i}]+v_{i})}  ![{\displaystyle m[i,\,w]=\max(m[i-1,\,w],\,m[i-1,w-w_{i}]+v_{i})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/10fe14457efe32c1e4adaee59f3d4dbd7b5c547a) if      w  i   ⩽ ⩽  w   {\displaystyle w_{i}\leqslant w}  ![{\displaystyle w_{i}\leqslant w}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f4a3366092785d6927733a4d40082ba7ea29e90).

 

The solution can then be found by calculating     m [ n , W ]   {\displaystyle m[n,W]}  ![{\displaystyle m[n,W]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f7f1046af8319a84c25c874bde6bcaf24bee4489). To do this efficiently, we can use a table to store previous computations.

 

The following is [pseudocode](./Pseudocode) for the dynamic program:

 
```
// Input:
// Values (stored in array v)
// Weights (stored in array w)
// Number of distinct items (n)
// Knapsack capacity (W)
// NOTE: The array "v" and array "w" are assumed to store all relevant values starting at index 1.

array m[0..n, 0..W];
for j from 0 to W do:
    m[0, j] := 0
for i from 1 to n do:
    m[i, 0] := 0

for i from 1 to n do:
    for j from 1 to W do:
        if w[i] > j then:
            m[i, j] := m[i-1, j]
        else:
            m[i, j] := max(m[i-1, j], m[i-1, j-w[i]] + v[i])

```
 

This solution will therefore run in     O ( n W )   {\displaystyle O(nW)}  ![{\displaystyle O(nW)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e748dd6992ec4d942b90c5d6edb8fdd63b93688) time and     O ( n W )   {\displaystyle O(nW)}  ![{\displaystyle O(nW)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e748dd6992ec4d942b90c5d6edb8fdd63b93688) space. 
(If we only need the value m[n,W], we can modify the code so that the amount of memory required is O(W) which stores the recent two lines of the array "m".)

 

However, if we take it a step or two further, we should know that the method will run in the time between     O ( n W )   {\displaystyle O(nW)}  ![{\displaystyle O(nW)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e748dd6992ec4d942b90c5d6edb8fdd63b93688) and     O (  2  n   )   {\displaystyle O(2^{n})}  ![{\displaystyle O(2^{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4b1a4ff0bc4f81ebf79f28260c6fb54ee08ff8d). From **Definition A**, we know that there is no need to compute all the weights when the number of items and the items themselves that we chose are fixed. That is to say, the program above computes more than necessary because the weight changes from 0 to W often. From this perspective, we can program this method so that it runs recursively.

 
```
// Input:
// Values (stored in array v)
// Weights (stored in array w)
// Number of distinct items (n)
// Knapsack capacity (W)
// NOTE: The array "v" and array "w" are assumed to store all relevant values starting at index 1.

Define value[n, W]

Initialize all value[i, j] = -1

Define m:=(i,j)         // Define function m so that it represents the maximum value we can get under the condition: use first i items, total weight limit is j
{
    if i == 0 or j <= 0 then:
        value[i, j] = 0
        return

    if (value[i-1, j] == -1) then:     // m[i-1, j] has not been calculated, we have to call function m
        m(i-1, j)

    if w[i] > j then:                      // item cannot fit in the bag
        value[i, j] = value[i-1, j]
    else: 
        if (value[i-1, j-w[i]] == -1) then:     // m[i-1,j-w[i]] has not been calculated, we have to call function m
            m(i-1, j-w[i])
        value[i, j] = max(value[i-1,j], value[i-1, j-w[i]] + v[i])
}

Run m(n, W)

```
 

For example, there are 10 different items and the weight limit is 67. So,
         w [ 1 ] = 23 , w [ 2 ] = 26 , w [ 3 ] = 20 , w [ 4 ] = 18 , w [ 5 ] = 32 , w [ 6 ] = 27 , w [ 7 ] = 29 , w [ 8 ] = 26 , w [ 9 ] = 30 , w [ 10 ] = 27      v [ 1 ] = 505 , v [ 2 ] = 352 , v [ 3 ] = 458 , v [ 4 ] = 220 , v [ 5 ] = 354 , v [ 6 ] = 414 , v [ 7 ] = 498 , v [ 8 ] = 545 , v [ 9 ] = 473 , v [ 10 ] = 543       {\displaystyle {\begin{aligned}&w[1]=23,w[2]=26,w[3]=20,w[4]=18,w[5]=32,w[6]=27,w[7]=29,w[8]=26,w[9]=30,w[10]=27\\&v[1]=505,v[2]=352,v[3]=458,v[4]=220,v[5]=354,v[6]=414,v[7]=498,v[8]=545,v[9]=473,v[10]=543\\\end{aligned}}}  ![{\displaystyle {\begin{aligned}&w[1]=23,w[2]=26,w[3]=20,w[4]=18,w[5]=32,w[6]=27,w[7]=29,w[8]=26,w[9]=30,w[10]=27\\&v[1]=505,v[2]=352,v[3]=458,v[4]=220,v[5]=354,v[6]=414,v[7]=498,v[8]=545,v[9]=473,v[10]=543\\\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/52b4c8149a5b2e88869f5c4bbf61c4e287abc79c)
If you use above method to compute for     m ( 10 , 67 )   {\displaystyle m(10,67)}  ![{\displaystyle m(10,67)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b26bc3ec3190ee9808e126b791c1ead2b310487), you will get this, excluding calls that produce     m ( i , j ) = 0   {\displaystyle m(i,j)=0}  ![{\displaystyle m(i,j)=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bc8c37b1fea7c10f5489833873189f9130d798fd):
         m ( 10 , 67 ) = 1270      m ( 9 , 67 ) = 1270 , m ( 9 , 40 ) = 678      m ( 8 , 67 ) = 1270 , m ( 8 , 40 ) = 678 , m ( 8 , 37 ) = 545      m ( 7 , 67 ) = 1183 , m ( 7 , 41 ) = 725 , m ( 7 , 40 ) = 678 , m ( 7 , 37 ) = 505      m ( 6 , 67 ) = 1183 , m ( 6 , 41 ) = 725 , m ( 6 , 40 ) = 678 , m ( 6 , 38 ) = 678 , m ( 6 , 37 ) = 505      m ( 5 , 67 ) = 1183 , m ( 5 , 41 ) = 725 , m ( 5 , 40 ) = 678 , m ( 5 , 38 ) = 678 , m ( 5 , 37 ) = 505      m ( 4 , 67 ) = 1183 , m ( 4 , 41 ) = 725 , m ( 4 , 40 ) = 678 , m ( 4 , 38 ) = 678 , m ( 4 , 37 ) = 505 , m ( 4 , 35 ) = 505      m ( 3 , 67 ) = 963 , m ( 3 , 49 ) = 963 , m ( 3 , 41 ) = 505 , m ( 3 , 40 ) = 505 , m ( 3 , 38 ) = 505 , m ( 3 , 37 ) = 505 , m ( 3 , 35 ) = 505 , m ( 3 , 23 ) = 505 , m ( 3 , 22 ) = 458 , m ( 3 , 20 ) = 458      m ( 2 , 67 ) = 857 , m ( 2 , 49 ) = 857 , m ( 2 , 47 ) = 505 , m ( 2 , 41 ) = 505 , m ( 2 , 40 ) = 505 , m ( 2 , 38 ) = 505 , m ( 2 , 37 ) = 505 , m ( 2 , 35 ) = 505 , m ( 2 , 29 ) = 505 , m ( 2 , 23 ) = 505      m ( 1 , 67 ) = 505 , m ( 1 , 49 ) = 505 , m ( 1 , 47 ) = 505 , m ( 1 , 41 ) = 505 , m ( 1 , 40 ) = 505 , m ( 1 , 38 ) = 505 , m ( 1 , 37 ) = 505 , m ( 1 , 35 ) = 505 , m ( 1 , 29 ) = 505 , m ( 1 , 23 ) = 505       {\displaystyle {\begin{aligned}&m(10,67)=1270\\&m(9,67)=1270,m(9,40)=678\\&m(8,67)=1270,m(8,40)=678,m(8,37)=545\\&m(7,67)=1183,m(7,41)=725,m(7,40)=678,m(7,37)=505\\&m(6,67)=1183,m(6,41)=725,m(6,40)=678,m(6,38)=678,m(6,37)=505\\&m(5,67)=1183,m(5,41)=725,m(5,40)=678,m(5,38)=678,m(5,37)=505\\&m(4,67)=1183,m(4,41)=725,m(4,40)=678,m(4,38)=678,m(4,37)=505,m(4,35)=505\\&m(3,67)=963,m(3,49)=963,m(3,41)=505,m(3,40)=505,m(3,38)=505,m(3,37)=505,m(3,35)=505,m(3,23)=505,m(3,22)=458,m(3,20)=458\\&m(2,67)=857,m(2,49)=857,m(2,47)=505,m(2,41)=505,m(2,40)=505,m(2,38)=505,m(2,37)=505,m(2,35)=505,m(2,29)=505,m(2,23)=505\\&m(1,67)=505,m(1,49)=505,m(1,47)=505,m(1,41)=505,m(1,40)=505,m(1,38)=505,m(1,37)=505,m(1,35)=505,m(1,29)=505,m(1,23)=505\\\end{aligned}}}  ![{\displaystyle {\begin{aligned}&m(10,67)=1270\\&m(9,67)=1270,m(9,40)=678\\&m(8,67)=1270,m(8,40)=678,m(8,37)=545\\&m(7,67)=1183,m(7,41)=725,m(7,40)=678,m(7,37)=505\\&m(6,67)=1183,m(6,41)=725,m(6,40)=678,m(6,38)=678,m(6,37)=505\\&m(5,67)=1183,m(5,41)=725,m(5,40)=678,m(5,38)=678,m(5,37)=505\\&m(4,67)=1183,m(4,41)=725,m(4,40)=678,m(4,38)=678,m(4,37)=505,m(4,35)=505\\&m(3,67)=963,m(3,49)=963,m(3,41)=505,m(3,40)=505,m(3,38)=505,m(3,37)=505,m(3,35)=505,m(3,23)=505,m(3,22)=458,m(3,20)=458\\&m(2,67)=857,m(2,49)=857,m(2,47)=505,m(2,41)=505,m(2,40)=505,m(2,38)=505,m(2,37)=505,m(2,35)=505,m(2,29)=505,m(2,23)=505\\&m(1,67)=505,m(1,49)=505,m(1,47)=505,m(1,41)=505,m(1,40)=505,m(1,38)=505,m(1,37)=505,m(1,35)=505,m(1,29)=505,m(1,23)=505\\\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33576ad0db77298eb7d7116472294383b556e745)

 

Besides, we can break the recursion and convert it into a tree. Then we can cut some leaves and use [parallel computing](./Parallel_computing) to expedite the running of this method.

To find the actual subset of items, rather than just their total value, we can run this after running the function above:

```
/**
 * Returns the indices of the items of the optimal knapsack.
 * i: We can include items 1 through i in the knapsack
 * j: maximum weight of the knapsack
 */
function knapsack(i: int, j: int): Set<int> {
    if i == 0 then:
        return {}
    if m[i, j] > m[i-1, j] then:
        return {i} ∪ knapsack(i-1, j-w[i])
    else:
        return knapsack(i-1, j)
}

knapsack(n, W)

```
 

### Meet-in-the-middle

 

Another algorithm for 0-1 knapsack, discovered in 1974[[23]](./Knapsack_problem#cite_note-23) and sometimes called "meet-in-the-middle" due to parallels to [a similarly named algorithm in cryptography](./Meet-in-the-middle_attack), is exponential in the number of different items but may be preferable to the DP algorithm when     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7) is large compared to *n*. In particular, if the      w  i     {\displaystyle w_{i}}  ![{\displaystyle w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe22f0329d3ecb2e1880d44d191aba0e5475db68) are nonnegative but not integers, we could still use the dynamic programming algorithm by scaling and rounding (i.e. using [fixed-point arithmetic](./Fixed-point_arithmetic)), but if the problem requires     d   {\displaystyle d}  ![{\displaystyle d}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e85ff03cbe0c7341af6b982e47e9f90d235c66ab) fractional digits of precision to arrive at the correct answer,     W   {\displaystyle W}  ![{\displaystyle W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54a9c4c547f4d6111f81946cad242b18298d70b7) will need to be scaled by      10  d     {\displaystyle 10^{d}}  ![{\displaystyle 10^{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/533c9080b4667d18d8685fbf8a3e6ec4b5b5e79e), and the DP algorithm will require     O ( W  10  d   )   {\displaystyle O(W10^{d})}  ![{\displaystyle O(W10^{d})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d1c50fe4d63b706b21c606c67ae541f7bf58e0c) space and     O ( n W  10  d   )   {\displaystyle O(nW10^{d})}  ![{\displaystyle O(nW10^{d})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe772579a33a6fd4a464d34e5ef63dc9138a54aa) time.

 
```
algorithm Meet-in-the-middle is
    input: A set of items with weights and values.
    output: The greatest combined value of a subset.

    partition the set {1...n} into two sets A and B of approximately equal size
    compute the weights and values of all subsets of each set

    for each subset of A do
        find the subset of B of greatest value such that the combined weight is less than W

    keep track of the greatest combined value seen so far
```
 

The algorithm takes     O (  2  n  /  2   )   {\displaystyle O(2^{n/2})}  ![{\displaystyle O(2^{n/2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fbb200a043616b13f8622ec89c8901f838f692f) space, and efficient implementations of step 3 (for instance, sorting the subsets of B by weight, discarding subsets of B which weigh more than other subsets of B of greater or equal value, and using [binary search](./Binary_search) to find the best match) result in a runtime of     O ( n  2  n  /  2   )   {\displaystyle O(n2^{n/2})}  ![{\displaystyle O(n2^{n/2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/805791a36032ea1befe32e2a9218d9664aa336f4). As with the [meet in the middle attack](./Meet-in-the-middle_attack) in cryptography, this improves on the     O ( n  2  n   )   {\displaystyle O(n2^{n})}  ![{\displaystyle O(n2^{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c02f556173ce8363d5e2b411cdb57ee5d9c9646) runtime of a naive brute force approach (examining all subsets of     { 1... n }   {\displaystyle \{1...n\}}  ![{\displaystyle \{1...n\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b2102a85d491c66b010463dae395439a926791c)), at the cost of using exponential rather than constant space (see also [baby-step giant-step](./Baby-step_giant-step)). The current state of the art improvement to the meet-in-the-middle algorithm, using insights from Schroeppel and Shamir's Algorithm for Subset Sum, provides as a corollary a [randomized algorithm](./Randomized_algorithm) for Knapsack which preserves the      O  ∗ ∗    (  2  n  /  2   )   {\displaystyle O^{*}(2^{n/2})}  ![{\displaystyle O^{*}(2^{n/2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/58dc74b649d4ff03053421d5006e66a54932d18d) (up to polynomial factors) running time and reduces the space requirements to      O  ∗ ∗    (  2  0.249999 n   )   {\displaystyle O^{*}(2^{0.249999n})}  ![{\displaystyle O^{*}(2^{0.249999n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5b4af651f5033176ad66b6b37d0cb81c70e9230) (see [[24]](./Knapsack_problem#cite_note-24) Corollary 1.4). In contrast, the best known [deterministic algorithm](./Deterministic_algorithm) runs in      O  ∗ ∗    (  2  n  /  2   )   {\displaystyle O^{*}(2^{n/2})}  ![{\displaystyle O^{*}(2^{n/2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/58dc74b649d4ff03053421d5006e66a54932d18d) time with a slightly worse space complexity of      O  ∗ ∗    (  2  n  /  4   )   {\displaystyle O^{*}(2^{n/4})}  ![{\displaystyle O^{*}(2^{n/4})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/519a8d89a30e0e9707fb21fd2d9b39507f42ba9a).[[25]](./Knapsack_problem#cite_note-25)

 

### Approximation Algorithms

 

As for most NP-complete problems, it may be enough to find workable solutions even if they are not optimal. Preferably, however, the approximation comes with a guarantee of the difference between the value of the solution found and the value of the optimal solution.

 

As with many useful but computationally complex algorithms, there has been substantial research on creating and analyzing algorithms that approximate a solution. The knapsack problem, though NP-Hard, is one of a collection of algorithms that can still be approximated to any specified degree. This means that the problem has a polynomial time approximation scheme. To be exact, the knapsack problem has a [fully polynomial time approximation scheme](./Fully_polynomial_time_approximation_scheme) (FPTAS).[[26]](./Knapsack_problem#cite_note-Vazirani,_Vijay_2003-26)

 

#### Greedy approximation algorithm

 

[George Dantzig](./George_Dantzig) proposed a [greedy](./Greedy_algorithm) [approximation algorithm](./Approximation_algorithm) to solve the unbounded knapsack problem.[[27]](./Knapsack_problem#cite_note-dantzig1957-27) His version sorts the items in decreasing order of value per unit of weight,      v  1    /   w  1   ≥ ≥  ⋯ ⋯  ≥ ≥   v  n    /   w  n     {\displaystyle v_{1}/w_{1}\geq \cdots \geq v_{n}/w_{n}}  ![{\displaystyle v_{1}/w_{1}\geq \cdots \geq v_{n}/w_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/50533bfcdf1002d51319ba2bde6f8fe31467b72f). It then proceeds to insert them into the sack, starting with as many copies as possible of the first kind of item until there is no longer space in the sack for more. Provided that there is an unlimited supply of each kind of item, if     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the maximum value of items that fit into the sack, then the greedy algorithm is guaranteed to achieve at least a value of     m  /  2   {\displaystyle m/2}  ![{\displaystyle m/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d6af4e80f7ef59ed62ebada0b02f1ef4b2a2016).

 

For the bounded problem, where the supply of each kind of item is limited, the above algorithm may be far from optimal. Nevertheless, a simple modification allows us to solve this case: Assume for simplicity that all items individually fit in the sack (     w  i   ≤ ≤  W   {\displaystyle w_{i}\leq W}  ![{\displaystyle w_{i}\leq W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7b0ae396f312826064ccd1483844114eaa11a00f) for all     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)). Construct a solution      S  1     {\displaystyle S_{1}}  ![{\displaystyle S_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5bf84e7fd4fb8259a9b37f956afdf83ee2a020f9) by packing items greedily as long as possible, i.e.      S  1   =  {  1 , … …  , k  }    {\displaystyle S_{1}=\left\{1,\ldots ,k\right\}}  ![{\displaystyle S_{1}=\left\{1,\ldots ,k\right\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fdd06388dd62aebe8fca9239d1f2cb9e023b4048) where     k =   max  1 ≤ ≤   k ′  ≤ ≤  n     ∑ ∑   i = 1    k ′     w  i   ≤ ≤  W     {\displaystyle k=\textstyle \max _{1\leq k'\leq n}\textstyle \sum _{i=1}^{k'}w_{i}\leq W}  ![{\displaystyle k=\textstyle \max _{1\leq k'\leq n}\textstyle \sum _{i=1}^{k'}w_{i}\leq W}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f021d8acd04ca4c3e736a3bfb42793e8ec729f8e). Furthermore, construct a second solution      S  2   =  {  k + 1  }    {\displaystyle S_{2}=\left\{k+1\right\}}  ![{\displaystyle S_{2}=\left\{k+1\right\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2001ad20b4d59342fba29148a2e9bafdf9705aa4) containing the first item that did not fit. Since      S  1   ∪ ∪   S  2     {\displaystyle S_{1}\cup S_{2}}  ![{\displaystyle S_{1}\cup S_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49c5d6dd06bbc5498df9695e84a95d1325ce99b7) provides an upper bound for the [LP relaxation](./Linear_programming_relaxation) of the problem, one of the sets must have value at least     m  /  2   {\displaystyle m/2}  ![{\displaystyle m/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d6af4e80f7ef59ed62ebada0b02f1ef4b2a2016); we thus return whichever of      S  1     {\displaystyle S_{1}}  ![{\displaystyle S_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5bf84e7fd4fb8259a9b37f956afdf83ee2a020f9) and      S  2     {\displaystyle S_{2}}  ![{\displaystyle S_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1143e284d5f25cef778ab482edf6617a523ddd9f) has better value to obtain a     1  /  2   {\displaystyle 1/2}  ![{\displaystyle 1/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e308a3a46b7fdce07cc09dcab9e8d8f73e37d935)-approximation.

 

It can be shown that the average performance converges to the optimal solution in distribution at the error rate      n  − −  1  /  2     {\displaystyle n^{-1/2}}  ![{\displaystyle n^{-1/2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7bebf90fd2f3a51acbf990a52169d362e821d9f2) [[28]](./Knapsack_problem#cite_note-28)

 

#### Fully polynomial time approximation scheme

 

The [fully polynomial time approximation scheme](./Fully_polynomial_time_approximation_scheme) (FPTAS) for the knapsack problem takes advantage of the fact that the reason the problem has no known polynomial time solutions is because the profits associated with the items are not restricted. If one rounds off some of the least significant digits of the profit values then they will be bounded by a polynomial and 1/ε where ε is a bound on the correctness of the solution. This restriction then means that an algorithm can find a solution in polynomial time that is correct within a factor of (1-ε) of the optimal solution.[[26]](./Knapsack_problem#cite_note-Vazirani,_Vijay_2003-26)

 
```
algorithm FPTAS is 
    input: ε ∈ (0,1]
           a list A of n items, specified by their values, 
  
    
      
        
          v
          
            i
          
        
      
    
    {\displaystyle v_{i}}
  
, and weights
    output: S' the FPTAS solution

    P := max 
  
    
      
        {
        
          v
          
            i
          
        
        ∣
        1
        ≤
        i
        ≤
        n
        }
      
    
    {\displaystyle \{v_{i}\mid 1\leq i\leq n\}}
  
  // the highest item value
    K := ε 
  
    
      
        
          
            P
            n
          
        
      
    
    {\displaystyle {\frac {P}{n}}}
  

    for i from 1 to n do
        
  
    
      
        
          v
          
            i
          
          ′
        
      
    
    {\displaystyle v'_{i}}
  
 := 
  
    
      
        
          ⌊
          
            
              
                v
                
                  i
                
              
              K
            
          
          ⌋
        
      
    
    {\displaystyle \left\lfloor {\frac {v_{i}}{K}}\right\rfloor }
  

    end for

    return the solution, S', using the 
  
    
      
        
          v
          
            i
          
          ′
        
      
    
    {\displaystyle v'_{i}}
  
 values in the dynamic program outlined above
```
 

**Theorem:** The set      S ′    {\displaystyle S'}  ![{\displaystyle S'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bf9961844d1f539adee019e432dc18aa2a7ede59) computed by the algorithm above satisfies      p r o f i t  (  S ′  ) ≥ ≥  ( 1 − −  ε ε  ) ⋅ ⋅   p r o f i t  (  S  ∗ ∗    )   {\displaystyle \mathrm {profit} (S')\geq (1-\varepsilon )\cdot \mathrm {profit} (S^{*})}  ![{\displaystyle \mathrm {profit} (S')\geq (1-\varepsilon )\cdot \mathrm {profit} (S^{*})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/511f3c7c30133672cfb9f62c9e8983a0da87eeaa), where      S  ∗ ∗      {\displaystyle S^{*}}  ![{\displaystyle S^{*}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b059338b0f6bc81c4edf97c51ce987e98f4bf23e) is an optimal solution.

 

#### Quantum approximate optimization

 

[Quantum approximate optimization algorithm](./Quantum_approximate_optimization_algorithm) (QAOA) can be employed to solve Knapsack problem using [quantum computation](./Quantum_computation) by minimizing the [Hamiltonian](./Hamiltonian_(quantum_mechanics)) of the problem. The Knapsack Hamiltonian is constructed via embedding the constraint condition to the cost function of the problem with a penalty term.[[29]](./Knapsack_problem#cite_note-29)     H  = − −   ∑ ∑   i = 1   n    v  i    x  i   + P   (   ∑ ∑   i = 1   n    w  i    x  i   − −  W  )   2   ,   {\displaystyle {H}=-\sum _{i=1}^{n}v_{i}x_{i}+P\left(\sum _{i=1}^{n}w_{i}x_{i}-W\right)^{2},}  ![{\displaystyle {H}=-\sum _{i=1}^{n}v_{i}x_{i}+P\left(\sum _{i=1}^{n}w_{i}x_{i}-W\right)^{2},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f3d204fc7649981aba3f4bfd27e1e38cc4c52248)where     P   {\displaystyle P}  ![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) is the penalty constant which is determined by case-specific fine-tuning.

 

### Dominance relations

 

Solving the unbounded knapsack problem can be made easier by throwing away items which will never be needed.  For a given item     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), suppose we could find a set of items     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053) such that their total weight is less than the weight of     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), and their total value is greater than the value of     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20).  Then     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) cannot appear in the optimal solution, because we could always improve any potential solution containing     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) by replacing     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) with the set     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053).  Therefore, we can disregard the     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th item altogether.  In such cases,     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053) is said to **dominate**     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20).  (Note that this does not apply to bounded knapsack problems, since we may have already used up the items in     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053).)

 

Finding dominance relations allows us to significantly reduce the size of the search space.  There are several different types of [dominance relations](./Dominance_relations?action=edit&redlink=1),[[11]](./Knapsack_problem#cite_note-poirriez_et_all_2009-11) which all satisfy an inequality of the form:

 

      ∑ ∑   j ∈ ∈  J    w  j     x  j     ≤ ≤  α α    w  i     {\displaystyle \qquad \sum _{j\in J}w_{j}\,x_{j}\ \leq \alpha \,w_{i}}  ![{\displaystyle \qquad \sum _{j\in J}w_{j}\,x_{j}\ \leq \alpha \,w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2cd7c4b942e77bf73b8531d019d71bcf4994568), and      ∑ ∑   j ∈ ∈  J    v  j     x  j     ≥ ≥  α α    v  i      {\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq \alpha \,v_{i}\,}  ![{\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq \alpha \,v_{i}\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/04c541084d185add19ce96fb8946d0d080ca6a4f) for some     x ∈ ∈   Z  +   n     {\displaystyle x\in Z_{+}^{n}}  ![{\displaystyle x\in Z_{+}^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5efb76db4a440369dbeb077e65930e44a4c88dcb)

 

where
    α α  ∈ ∈   Z  +    , J ⊊ ⊊  N   {\displaystyle \alpha \in Z_{+}\,,J\subsetneq N}  ![{\displaystyle \alpha \in Z_{+}\,,J\subsetneq N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/46549937c6c98b93ff346a2f73f8efcb09cd7f93) and     i ∉ J   {\displaystyle i\not \in J}  ![{\displaystyle i\not \in J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec8794a92e81fb103ef1e5cf2163986c5d69c938).  The vector     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) denotes the number of copies of each member of     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053).

 Collective dominanceThe     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th item is  **collectively dominated** by     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053), written as     i ≪ ≪  J   {\displaystyle i\ll J}  ![{\displaystyle i\ll J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f58df4fa0608a4fa93a399c9050c0ad5c0870c0b), if the total weight of some combination of items in     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053) is less than *wi* and their total value is greater than *vi*.  Formally,      ∑ ∑   j ∈ ∈  J    w  j     x  j     ≤ ≤   w  i     {\displaystyle \sum _{j\in J}w_{j}\,x_{j}\ \leq w_{i}}  ![{\displaystyle \sum _{j\in J}w_{j}\,x_{j}\ \leq w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d256af517158bde38a4603e0123203d416a1c80) and      ∑ ∑   j ∈ ∈  J    v  j     x  j     ≥ ≥   v  i     {\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq v_{i}}  ![{\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a8ecef93d36a8e72125449842cd3fc7f4432941) for some     x ∈ ∈   Z  +   n     {\displaystyle x\in Z_{+}^{n}}  ![{\displaystyle x\in Z_{+}^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5efb76db4a440369dbeb077e65930e44a4c88dcb), i.e.     α α  = 1   {\displaystyle \alpha =1}  ![{\displaystyle \alpha =1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/03d67a45a44be8b8f15e99b7def2b0cf0aba1717).  Verifying this dominance is computationally hard, so it can only be used with a dynamic programming approach.  In fact, this is equivalent to solving a smaller knapsack decision problem where     V =  v  i     {\displaystyle V=v_{i}}  ![{\displaystyle V=v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/78c151c780148ad29c273b2f49bd4094eb145f37),     W =  w  i     {\displaystyle W=w_{i}}  ![{\displaystyle W=w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7db5b660c5bb6f101dccd69721366ac801f4bfa3), and the items are restricted to     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053). Threshold dominanceThe     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th item is **threshold dominated**  by     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053), written as     i ≺ ≺ ≺ ≺  J   {\displaystyle i\prec \prec J}  ![{\displaystyle i\prec \prec J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5331d5c5e05b74fb489ec4e3cbc2bba4e3d0201), if some number of copies of     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) are dominated by     J   {\displaystyle J}  ![{\displaystyle J}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359e4f407b49910e02c27c2f52e87a36cd74c053).  Formally,      ∑ ∑   j ∈ ∈  J    w  j     x  j     ≤ ≤  α α    w  i     {\displaystyle \sum _{j\in J}w_{j}\,x_{j}\ \leq \alpha \,w_{i}}  ![{\displaystyle \sum _{j\in J}w_{j}\,x_{j}\ \leq \alpha \,w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e852c27c88d48e5bb94a2a232eaf8ec547c4b7bd), and      ∑ ∑   j ∈ ∈  J    v  j     x  j     ≥ ≥  α α    v  i      {\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq \alpha \,v_{i}\,}  ![{\displaystyle \sum _{j\in J}v_{j}\,x_{j}\ \geq \alpha \,v_{i}\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/04c541084d185add19ce96fb8946d0d080ca6a4f) for some     x ∈ ∈   Z  +   n     {\displaystyle x\in Z_{+}^{n}}  ![{\displaystyle x\in Z_{+}^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5efb76db4a440369dbeb077e65930e44a4c88dcb) and     α α  ≥ ≥  1   {\displaystyle \alpha \geq 1}  ![{\displaystyle \alpha \geq 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/810dcd1d13dc817a9a6e5dc25ed3ceca99b457d4).  This is a generalization of collective dominance, first introduced in[[18]](./Knapsack_problem#cite_note-eduk2000-18) and used in the EDUK algorithm.  The smallest such     α α    {\displaystyle \alpha }  ![{\displaystyle \alpha }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79333175c8b3f0840bfb4ec41b8072c83ea88d3) defines the **threshold** of the item     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), written       t  i   = ( α α  − −  1 )  w  i     {\displaystyle t_{i}=(\alpha -1)w_{i}}  ![{\displaystyle t_{i}=(\alpha -1)w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82db9c6c69bd5f668a97f29dc1fc92e69e0ca0f1).  In this case, the optimal solution could contain at most     α α  − −  1   {\displaystyle \alpha -1}  ![{\displaystyle \alpha -1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6be20746eff1825a942441a53ffb32ef178193a8) copies of     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20). Multiple dominanceThe     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th item is  **multiply dominated** by a single item     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0), written as     i  ≪ ≪   m   j   {\displaystyle i\ll _{m}j}  ![{\displaystyle i\ll _{m}j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e529970bf733a90f75a6bbf53bbaa740e4bd11e0), if     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is dominated by some number of copies of     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0).  Formally,      w  j     x  j     ≤ ≤   w  i     {\displaystyle w_{j}\,x_{j}\ \leq w_{i}}  ![{\displaystyle w_{j}\,x_{j}\ \leq w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bf0ae48f0a8011aab68a84abdd2f6244eb2abec1), and      v  j     x  j     ≥ ≥   v  i     {\displaystyle v_{j}\,x_{j}\ \geq v_{i}}  ![{\displaystyle v_{j}\,x_{j}\ \geq v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/22af7b42e0b618dd6c02ac1f8a22b60d8da79823) for some      x  j   ∈ ∈   Z  +     {\displaystyle x_{j}\in Z_{+}}  ![{\displaystyle x_{j}\in Z_{+}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7ccf203d7dedfe6957a2c841b9e1ec16378d820) i.e.     J = { j } , α α  = 1 ,  x  j   = ⌊ ⌊     w  i    w  j     ⌋ ⌋    {\displaystyle J=\{j\},\alpha =1,x_{j}=\lfloor {\frac {w_{i}}{w_{j}}}\rfloor }  ![{\displaystyle J=\{j\},\alpha =1,x_{j}=\lfloor {\frac {w_{i}}{w_{j}}}\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/3db7a544cd0b0f4491cf6759ec85da3a74103129). This dominance could be efficiently used during preprocessing because it can be detected relatively easily. Modular dominanceLet     b   {\displaystyle b}  ![{\displaystyle b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3) be the *best item*, i.e.        v  b    w  b     ≥ ≥     v  i    w  i        {\displaystyle {\frac {v_{b}}{w_{b}}}\geq {\frac {v_{i}}{w_{i}}}\,}  ![{\displaystyle {\frac {v_{b}}{w_{b}}}\geq {\frac {v_{i}}{w_{i}}}\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/43732a7674af555e1b81f1ce71f65c528cc997ee) for all     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20).  This is the item with the greatest density of value. The     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th item is **modularly dominated** by a single item     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0), written as     i  ≪ ≪   ≡ ≡    j   {\displaystyle i\ll _{\equiv }j}  ![{\displaystyle i\ll _{\equiv }j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bedf9947972f9349badf386c6e89ccf9e9188d15), if     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is dominated by     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) plus several copies of     b   {\displaystyle b}  ![{\displaystyle b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3).  Formally,      w  j   + t  w  b   ≤ ≤   w  i     {\displaystyle w_{j}+tw_{b}\leq w_{i}}  ![{\displaystyle w_{j}+tw_{b}\leq w_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/13e54206d9ed4cf44410e9092015b2ad45a4a039), and       v  j   + t  v  b   ≥ ≥   v  i     {\displaystyle v_{j}+tv_{b}\geq v_{i}}  ![{\displaystyle v_{j}+tv_{b}\geq v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe303b8bea29a607d6b79896471057be2002c33d) i.e.     J = { b , j } , α α  = 1 ,  x  b   = t ,  x  j   = 1   {\displaystyle J=\{b,j\},\alpha =1,x_{b}=t,x_{j}=1}  ![{\displaystyle J=\{b,j\},\alpha =1,x_{b}=t,x_{j}=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bc5f83839a1dde46cc1865b7089af3401aa548bc). 

## Variations

 Main article: [List of knapsack problems](./List_of_knapsack_problems) 

There are many variations of the knapsack problem that have arisen from the vast number of applications of the basic problem. The main variations occur by changing the number of some problem parameter such as the number of items, number of objectives, or even the number of knapsacks.

 

### Multi-dimensional objective

 

Here, instead of a single objective (e.g. maximizing the monetary profit from the items in the knapsack), there can be several objectives. For example, there could be environmental or social concerns as well as economic goals. Problems frequently addressed include portfolio and transportation logistics optimizations.[[30]](./Knapsack_problem#cite_note-30)[[31]](./Knapsack_problem#cite_note-31)

 

As an example, suppose you run a cruise ship. You have to decide how many famous comedians to hire. This boat can handle no more than one ton of passengers and the entertainers must weigh less than 1000 lbs. Each comedian has a weight, brings in business based on their popularity and asks for a specific salary. In this example, you have multiple objectives. You want, of course, to maximize the popularity of your entertainers while minimizing their salaries. Also, you want to have as many entertainers as possible.

 

### Multi-dimensional weight

 

Here, the weight of knapsack item     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is given by a D-dimensional vector        w  i   ¯ ¯    = (  w  i 1   , … …  ,  w  i D   )   {\displaystyle {\overline {w_{i}}}=(w_{i1},\ldots ,w_{iD})}  ![{\displaystyle {\overline {w_{i}}}=(w_{i1},\ldots ,w_{iD})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/96d4a31f2c8766e806655a75ee18ca3f11bb847a) and the knapsack has a D-dimensional capacity vector     (  W  1   , … …  ,  W  D   )   {\displaystyle (W_{1},\ldots ,W_{D})}  ![{\displaystyle (W_{1},\ldots ,W_{D})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47a732a0c02c8c2add7849fc51d6d139474eadc7). The target is to maximize the sum of the values of the items in the knapsack so that the sum of weights in each dimension     d   {\displaystyle d}  ![{\displaystyle d}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e85ff03cbe0c7341af6b982e47e9f90d235c66ab) does not exceed      W  d     {\displaystyle W_{d}}  ![{\displaystyle W_{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4276175ed1435c1c81fe805bf2e499f64ec773cd).

 

Multi-dimensional knapsack is computationally harder than knapsack; even for     D = 2   {\displaystyle D=2}  ![{\displaystyle D=2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ac67967f48b21969a5fc88b231b13e11394278d), the problem does not have [EPTAS](./EPTAS) unless P    =   {\displaystyle =}  ![{\displaystyle =}](https://wikimedia.org/api/rest_v1/media/math/render/svg/505a4ceef454c69dffd23792c84b90f488543743)NP.[[32]](./Knapsack_problem#cite_note-32) However, the algorithm in[[33]](./Knapsack_problem#cite_note-CohenGrebla-33) is shown to solve sparse instances efficiently. An instance of multi-dimensional knapsack is sparse if there is a set     J = { 1 , 2 , … …  , m }   {\displaystyle J=\{1,2,\ldots ,m\}}  ![{\displaystyle J=\{1,2,\ldots ,m\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3b3f3511f57eabb746dd4e385d52c2d04cfc0890) for     m < D   {\displaystyle m<D}  ![{\displaystyle m<D}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cb194618098a9bea1cb7c67291572630a714f982) such that for every knapsack item     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20),     ∃ ∃  z > m   {\displaystyle \exists z>m}  ![{\displaystyle \exists z>m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ca38ed867e171d564a0cb209375f85274015a534) such that     ∀ ∀  j ∈ ∈  J ∪ ∪  { z } ,    w  i j   ≥ ≥  0   {\displaystyle \forall j\in J\cup \{z\},\ w_{ij}\geq 0}  ![{\displaystyle \forall j\in J\cup \{z\},\ w_{ij}\geq 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/119653a68738e1f10cf864046d8116317ef2e1d1) and     ∀ ∀  y ∉ ∉  J ∪ ∪  { z } ,  w  i y   = 0   {\displaystyle \forall y\notin J\cup \{z\},w_{iy}=0}  ![{\displaystyle \forall y\notin J\cup \{z\},w_{iy}=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/275c260f57c4a82893051498aae9cc0ba3e6ae91). Such instances occur, for example, when scheduling packets in a wireless network with relay nodes.[[33]](./Knapsack_problem#cite_note-CohenGrebla-33) The algorithm from[[33]](./Knapsack_problem#cite_note-CohenGrebla-33) also solves sparse instances of the multiple choice variant, multiple-choice multi-dimensional knapsack.

 

The IHS (Increasing Height Shelf) algorithm is optimal for 2D knapsack (packing squares into a two-dimensional unit size square): when there are at most five squares in an optimal packing.[[34]](./Knapsack_problem#cite_note-34)

 

### Multiple knapsacks

 Main article: [Multiple knapsack problem](./Multiple_knapsack_problem) 

Here, there are multiple knapsacks. This may seem like a trivial change, but it is not equivalent to adding to the capacity of the initial knapsack, as each knapsack has its own capacity constraint. This variation is used in many loading and scheduling problems in Operations Research and has a [Polynomial-time approximation scheme](./Polynomial-time_approximation_scheme).[[35]](./Knapsack_problem#cite_note-35)   This variation is similar to the [Bin Packing Problem](./Bin_packing_problem). It differs from the Bin Packing Problem in that a subset of items can be selected, whereas, in the Bin Packing Problem, all items have to be packed to certain bins. 

 

### Quadratic

 Main article: [Quadratic knapsack problem](./Quadratic_knapsack_problem) 

The **quadratic knapsack problem** maximizes a quadratic objective function subject to binary and linear capacity constraints.[[36]](./Knapsack_problem#cite_note-QKP-36) The problem was introduced by Gallo, Hammer, and Simeone  in 1980,[[37]](./Knapsack_problem#cite_note-37) however the first treatment of the problem dates back to Witzgall in 1975.[[38]](./Knapsack_problem#cite_note-38)

 

### Geometric

 

In the **geometric knapsack problem**, there is a set of rectangles with different values, and a rectangular knapsack. The goal is to pack the largest possible value into the knapsack.[[39]](./Knapsack_problem#cite_note-39)

 

### Online

 

In the **online knapsack problem**, the items come one by one. Whenever an item arrives, we must decide immediately whether to put it in the knapsack or discard it. There are two variants: (a) non-removable - an inserted item remains in the knapsack forever; (b) removable - an inserted item may be removed later, to make room for a new item.

 

Han, Kawase and Makino[[40]](./Knapsack_problem#cite_note-40) present a randomized algorithm for the unweighted non-removable setting. It is 2-competitive, which is the best possible. For the weighted removable setting, they give a 2-competitive algorithm, prove a lower bound of ~1.368 for randomized algorithms, and prove that no deterministic algorithm can have a constant competitive ratio. For the unweighted removable setting, they give an 10/7-competitive-ratio algorithm, and prove a lower  bound of 1.25. 

 

There are several other papers on the online knapsack problem.[[41]](./Knapsack_problem#cite_note-41)[[42]](./Knapsack_problem#cite_note-42)[[43]](./Knapsack_problem#cite_note-43)

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Octicons-terminal.svg/40px-Octicons-terminal.svg.png)](./File:Octicons-terminal.svg)[Computer programming portal](./Portal:Computer_programming)

  
- [Bin packing problem](./Bin_packing_problem) – Mathematical and computational problem
- [Change-making problem](./Change-making_problem) – Choosing the fewest coins to make a given amount of money
- [Combinatorial auction](./Combinatorial_auction)
- [Combinatorial optimization](./Combinatorial_optimization) – Subfield of mathematical optimization
- [Continuous knapsack problem](./Continuous_knapsack_problem) – Algorithmic problem in computer science
- [Cutting stock problem](./Cutting_stock_problem) – Mathematical problem in operations research
- [Knapsack auction](./Knapsack_auction)
- [List of knapsack problems](./List_of_knapsack_problems)
- [Packing problem](./Packing_problem) – Problems which attempt to find the most efficient way to pack objects into containersPages displaying short descriptions of redirect targets

  

## Notes

 
1. [↑](./Knapsack_problem#cite_ref-1) Mathews, G. B. (25 June 1897). ["On the partition of numbers"](http://plms.oxfordjournals.org/content/s1-28/1/486.full.pdf) (PDF). *Proceedings of the London Mathematical Society*. **28**: 486–490. [doi](./Doi_(identifier)):[10.1112/plms/s1-28.1.486](https://doi.org/10.1112%2Fplms%2Fs1-28.1.486).
2. [↑](./Knapsack_problem#cite_ref-2) Richard M. Karp (1972). "[Reducibility Among Combinatorial Problems](https://web.archive.org/web/20190608032217/https://pdfs.semanticscholar.org/a3c3/7657822859549cd6b12b0d1f76f8ee3680a0.pdf)". In R. E. Miller and J. W. Thatcher (editors). Complexity of Computer Computations. New York: Plenum. pp. 85–103
3. [↑](./Knapsack_problem#cite_ref-3) Kellerer, Hans; Pferschy, Ulrich; Pisinger, David (2004). [*Knapsack problems*](https://books.google.com/books?id=u5DB7gck08YC). Berlin: Springer. p. 449. [ISBN](./ISBN_(identifier)) [978-3-540-40286-2](./Special:BookSources/978-3-540-40286-2). Retrieved 5 May 2022.
4. [↑](./Knapsack_problem#cite_ref-4) Kellerer, Hans; Pferschy, Ulrich; Pisinger, David (2004). [*Knapsack problems*](https://books.google.com/books?id=u5DB7gck08YC). Berlin: Springer. p. 461. [ISBN](./ISBN_(identifier)) [978-3-540-40286-2](./Special:BookSources/978-3-540-40286-2). Retrieved 5 May 2022.
5. [↑](./Knapsack_problem#cite_ref-5) Kellerer, Hans; Pferschy, Ulrich; Pisinger, David (2004). [*Knapsack problems*](https://books.google.com/books?id=u5DB7gck08YC). Berlin: Springer. p. 465. [ISBN](./ISBN_(identifier)) [978-3-540-40286-2](./Special:BookSources/978-3-540-40286-2). Retrieved 5 May 2022.
6. [↑](./Knapsack_problem#cite_ref-6) Kellerer, Hans; Pferschy, Ulrich; Pisinger, David (2004). [*Knapsack problems*](https://books.google.com/books?id=u5DB7gck08YC). Berlin: Springer. p. 472. [ISBN](./ISBN_(identifier)) [978-3-540-40286-2](./Special:BookSources/978-3-540-40286-2). Retrieved 5 May 2022.
7. [↑](./Knapsack_problem#cite_ref-7) Feuerman, Martin; Weiss, Harvey (April 1973). "A Mathematical Programming Model for Test Construction and Scoring". *Management Science*. **19** (8): 961–966. [doi](./Doi_(identifier)):[10.1287/mnsc.19.8.961](https://doi.org/10.1287%2Fmnsc.19.8.961). [JSTOR](./JSTOR_(identifier)) [2629127](https://www.jstor.org/stable/2629127).
8. [↑](./Knapsack_problem#cite_ref-8) Skiena, S. S. (September 1999). "Who is Interested in Algorithms and Why? Lessons from the Stony Brook Algorithm Repository". *ACM SIGACT News*. **30** (3): 65–74. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.41.8357](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.41.8357). [doi](./Doi_(identifier)):[10.1145/333623.333627](https://doi.org/10.1145%2F333623.333627). [ISSN](./ISSN_(identifier)) [0163-5700](https://search.worldcat.org/issn/0163-5700). [S2CID](./S2CID_(identifier)) [15619060](https://api.semanticscholar.org/CorpusID:15619060).
9. [↑](./Knapsack_problem#cite_ref-pisinger200308_9-0) Pisinger, D. 2003. [Where are the hard knapsack problems?](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.87.7431&rep=rep1&type=pdf) Technical Report 2003/08, Department of Computer Science, University of Copenhagen, Copenhagen, Denmark.
10. [↑](./Knapsack_problem#cite_ref-Cacetta2001_10-0) Caccetta, L.; Kulanoot, A. (2001). "Computational Aspects of Hard Knapsack Problems". *Nonlinear Analysis*. **47** (8): 5547–5558. [doi](./Doi_(identifier)):[10.1016/s0362-546x(01)00658-7](https://doi.org/10.1016%2Fs0362-546x%2801%2900658-7).
11. [1](./Knapsack_problem#cite_ref-poirriez_et_all_2009_11-0) [2](./Knapsack_problem#cite_ref-poirriez_et_all_2009_11-1) [3](./Knapsack_problem#cite_ref-poirriez_et_all_2009_11-2) Poirriez, Vincent; Yanev, Nicola; Andonov, Rumen (2009). ["A hybrid algorithm for the unbounded knapsack problem"](https://doi.org/10.1016%2Fj.disopt.2008.09.004). *Discrete Optimization*. **6** (1): 110–124. [doi](./Doi_(identifier)):[10.1016/j.disopt.2008.09.004](https://doi.org/10.1016%2Fj.disopt.2008.09.004). [ISSN](./ISSN_(identifier)) [1572-5286](https://search.worldcat.org/issn/1572-5286). [S2CID](./S2CID_(identifier)) [8820628](https://api.semanticscholar.org/CorpusID:8820628).
12. [↑](./Knapsack_problem#cite_ref-Wojtczak18_12-0) Wojtczak, Dominik (2018). "On Strong NP-Completeness of Rational Problems". *Computer Science – Theory and Applications*. Lecture Notes in Computer Science. Vol. 10846. pp. 308–320. [arXiv](./ArXiv_(identifier)):[1802.09465](https://arxiv.org/abs/1802.09465). [doi](./Doi_(identifier)):[10.1007/978-3-319-90530-3_26](https://doi.org/10.1007%2F978-3-319-90530-3_26). [ISBN](./ISBN_(identifier)) [978-3-319-90529-7](./Special:BookSources/978-3-319-90529-7). [S2CID](./S2CID_(identifier)) [3637366](https://api.semanticscholar.org/CorpusID:3637366).
13. [↑](./Knapsack_problem#cite_ref-13) Dobkin, David; Lipton, Richard J. (1978). ["A lower bound of ½*n*2 on linear search programs for the Knapsack problem"](https://dx.doi.org/10.1016/0022-0000%2878%2990026-0). *Journal of Computer and System Sciences*. **16** (3): 413–417. [doi](./Doi_(identifier)):[10.1016/0022-0000(78)90026-0](https://doi.org/10.1016%2F0022-0000%2878%2990026-0).
14. [↑](./Knapsack_problem#cite_ref-14) In fact, the lower bound applies to the subset sum problem, which is a special case of Knapsack.
15. [↑](./Knapsack_problem#cite_ref-15) Michael Steele, J; Yao, Andrew C (1 March 1982). ["Lower bounds for algebraic decision trees"](https://dx.doi.org/10.1016%2F0196-6774%2882%2990002-5). *Journal of Algorithms*. **3** (1): 1–8. [doi](./Doi_(identifier)):[10.1016/0196-6774(82)90002-5](https://doi.org/10.1016%2F0196-6774%2882%2990002-5). [ISSN](./ISSN_(identifier)) [0196-6774](https://search.worldcat.org/issn/0196-6774).
16. [↑](./Knapsack_problem#cite_ref-16) Ben-Amram, Amir M.; [Galil, Zvi](./Zvi_Galil) (2001), "Topological Lower Bounds on Algebraic Random Access Machines", *SIAM Journal on Computing*, **31** (3): 722–761, [doi](./Doi_(identifier)):[10.1137/S0097539797329397](https://doi.org/10.1137%2FS0097539797329397).
17. [↑](./Knapsack_problem#cite_ref-17) auf der Heide, Meyer (1984), "A Polynomial Linear Search Algorithm for the *n*-Dimensional Knapsack Problem", *Journal of the ACM*, **31** (3): 668–676, [doi](./Doi_(identifier)):[10.1145/828.322450](https://doi.org/10.1145%2F828.322450)
18. [1](./Knapsack_problem#cite_ref-eduk2000_18-0) [2](./Knapsack_problem#cite_ref-eduk2000_18-1) Andonov, Rumen; Poirriez, Vincent; Rajopadhye, Sanjay (2000). "Unbounded Knapsack Problem : dynamic programming revisited". *European Journal of Operational Research*. **123** (2): 168–181. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.41.2135](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.41.2135). [doi](./Doi_(identifier)):[10.1016/S0377-2217(99)00265-9](https://doi.org/10.1016%2FS0377-2217%2899%2900265-9).
19. [↑](./Knapsack_problem#cite_ref-martellototh90_19-0) S. Martello, P. Toth, Knapsack Problems: Algorithms and Computer Implementations,
John Wiley and Sons, 1990
20. [↑](./Knapsack_problem#cite_ref-martellopisingertoth99a_20-0) S. Martello, D. Pisinger, P. Toth, [Dynamic programming and strong bounds for the 0-1 knapsack problem](https://www.jstor.org/stable/pdf/2634886.pdf), *Manag. Sci.*, 45:414–424, 1999.
21. [↑](./Knapsack_problem#cite_ref-plateau85_21-0) Plateau, G.; Elkihel, M. (1985). "A hybrid algorithm for the 0-1 knapsack problem". *Methods of Oper. Res*. **49**: 277–293.
22. [↑](./Knapsack_problem#cite_ref-martellotothe99_22-0) Martello, S.; Toth, P. (1984). "A mixture of dynamic programming and branch-and-bound for the subset-sum problem". *Manag. Sci*. **30** (6): 765–771. [doi](./Doi_(identifier)):[10.1287/mnsc.30.6.765](https://doi.org/10.1287%2Fmnsc.30.6.765).
23. [↑](./Knapsack_problem#cite_ref-23) Horowitz, Ellis; [Sahni, Sartaj](./Sartaj_Sahni) (1974), "Computing partitions with applications to the knapsack problem", *Journal of the Association for Computing Machinery*, **21** (2): 277–292, [doi](./Doi_(identifier)):[10.1145/321812.321823](https://doi.org/10.1145%2F321812.321823), [hdl](./Hdl_(identifier)):[1813/5989](https://hdl.handle.net/1813%2F5989), [MR](./MR_(identifier)) [0354006](https://mathscinet.ams.org/mathscinet-getitem?mr=0354006), [S2CID](./S2CID_(identifier)) [16866858](https://api.semanticscholar.org/CorpusID:16866858)
24. [↑](./Knapsack_problem#cite_ref-24) Nederlof, Jesper; Węgrzycki, Karol (12 April 2021). "Improving Schroeppel and Shamir's Algorithm for Subset Sum via Orthogonal Vectors". [arXiv](./ArXiv_(identifier)):[2010.08576](https://arxiv.org/abs/2010.08576) [[cs.DS](https://arxiv.org/archive/cs.DS)].
25. [↑](./Knapsack_problem#cite_ref-25) Schroeppel, Richard; Shamir, Adi (August 1981). ["A $T = O(2^{n/2} )$, $S = O(2^{n/4} )$ Algorithm for Certain NP-Complete Problems"](http://epubs.siam.org/doi/10.1137/0210033). *SIAM Journal on Computing*. **10** (3): 456–464. [doi](./Doi_(identifier)):[10.1137/0210033](https://doi.org/10.1137%2F0210033). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397).
26. [1](./Knapsack_problem#cite_ref-Vazirani,_Vijay_2003_26-0) [2](./Knapsack_problem#cite_ref-Vazirani,_Vijay_2003_26-1) Vazirani, Vijay. Approximation Algorithms. Springer-Verlag Berlin Heidelberg, 2003.
27. [↑](./Knapsack_problem#cite_ref-dantzig1957_27-0) [Dantzig, George B.](./George_Dantzig) (1957). "Discrete-Variable Extremum Problems". *Operations Research*. **5** (2): 266–288. [doi](./Doi_(identifier)):[10.1287/opre.5.2.266](https://doi.org/10.1287%2Fopre.5.2.266).
28. [↑](./Knapsack_problem#cite_ref-28) Calvin, James M.; Leung, Joseph Y. -T. (1 May 2003). "Average-case analysis of a greedy algorithm for the 0/1 knapsack problem". *Operations Research Letters*. **31** (3): 202–210. [doi](./Doi_(identifier)):[10.1016/S0167-6377(02)00222-5](https://doi.org/10.1016%2FS0167-6377%2802%2900222-5).
29. [↑](./Knapsack_problem#cite_ref-29) Lucas, Andrew (2014). ["Ising formulations of many NP problems"](https://doi.org/10.3389%2Ffphy.2014.00005). *Frontiers in Physics*. **2**: 5. [arXiv](./ArXiv_(identifier)):[1302.5843](https://arxiv.org/abs/1302.5843). [Bibcode](./Bibcode_(identifier)):[2014FrP.....2....5L](https://ui.adsabs.harvard.edu/abs/2014FrP.....2....5L). [doi](./Doi_(identifier)):[10.3389/fphy.2014.00005](https://doi.org/10.3389%2Ffphy.2014.00005). [ISSN](./ISSN_(identifier)) [2296-424X](https://search.worldcat.org/issn/2296-424X).
30. [↑](./Knapsack_problem#cite_ref-30) Chang, T. J., et al. [Heuristics for Cardinality Constrained Portfolio Optimization](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.109.6698&rep=rep1&type=pdf).
Technical Report, London SW7 2AZ, England: The Management School, Imperial
College, May 1998
31. [↑](./Knapsack_problem#cite_ref-31) Chang, C. S., et al. "[Genetic Algorithm Based Bicriterion Optimization for Traction Substations in DC Railway System](https://scholarbank.nus.edu.sg/handle/10635/72660)." In Fogel [102], 11-16.
32. [↑](./Knapsack_problem#cite_ref-32) Kulik, A.; [Shachnai, H.](./Hadas_Shachnai) (2010). ["There is no EPTAS for two dimensional knapsack"](https://www.cs.technion.ac.il/~hadas/PUB/multi_knap.pdf) (PDF). *Inf. Process. Lett*. **110** (16): 707–712. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.161.5838](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.161.5838). [doi](./Doi_(identifier)):[10.1016/j.ipl.2010.05.031](https://doi.org/10.1016%2Fj.ipl.2010.05.031).
33. [1](./Knapsack_problem#cite_ref-CohenGrebla_33-0) [2](./Knapsack_problem#cite_ref-CohenGrebla_33-1) [3](./Knapsack_problem#cite_ref-CohenGrebla_33-2) Cohen, R. and Grebla, G. 2014. ["Multi-Dimensional OFDMA Scheduling in a Wireless Network with Relay Nodes"](http://wimnet.ee.columbia.edu/wp-content/uploads/2013/03/paper_short.pdf). in *Proc. IEEE INFOCOM'14*, 2427–2435.
34. [↑](./Knapsack_problem#cite_ref-34) Yan Lan, György Dósa, Xin Han, Chenyang Zhou, Attila Benkő [](https://scholar.google.com/citations?user=txyI5aAAAAAJ): *2D knapsack: Packing squares*, Theoretical Computer Science Vol. 508, pp. 35–40.
35. [↑](./Knapsack_problem#cite_ref-35) Chandra Chekuri and Sanjeev Khanna (2005). "A PTAS for the multiple knapsack problem". *SIAM Journal on Computing*. **35** (3): 713–728. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.226.3387](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.226.3387). [doi](./Doi_(identifier)):[10.1137/s0097539700382820](https://doi.org/10.1137%2Fs0097539700382820).
36. [↑](./Knapsack_problem#cite_ref-QKP_36-0) Wu, Z. Y.; Yang, Y. J.; Bai, F. S.; Mammadov, M. (2011). "Global Optimality Conditions and Optimization Methods for Quadratic Knapsack Problems". *J Optim Theory Appl*. **151** (2): 241–259. [doi](./Doi_(identifier)):[10.1007/s10957-011-9885-4](https://doi.org/10.1007%2Fs10957-011-9885-4). [S2CID](./S2CID_(identifier)) [31208118](https://api.semanticscholar.org/CorpusID:31208118).
37. [↑](./Knapsack_problem#cite_ref-37) Gallo, G.; Hammer, P. L.; Simeone, B. (1980). "Quadratic knapsack problems". *Combinatorial Optimization*. Mathematical Programming Studies. Vol. 12. pp. 132–149. [doi](./Doi_(identifier)):[10.1007/BFb0120892](https://doi.org/10.1007%2FBFb0120892). [ISBN](./ISBN_(identifier)) [978-3-642-00801-6](./Special:BookSources/978-3-642-00801-6).
38. [↑](./Knapsack_problem#cite_ref-38) Witzgall, C. (1975). "Mathematical methods of site selection for Electronic Message Systems (EMS)". *NASA Sti/Recon Technical Report N*. **76**. NBS Internal report: 18321. [Bibcode](./Bibcode_(identifier)):[1975STIN...7618321W](https://ui.adsabs.harvard.edu/abs/1975STIN...7618321W).
39. [↑](./Knapsack_problem#cite_ref-39) Galvez, Waldo; Grandoni, Fabrizio; Ingala, Salvatore; Heydrich, Sandy; Khan, Arindam; Wiese, Andreas (2021). ["Approximating Geometric Knapsack via L-packings"](https://doi.org/10.1145/3473713). *ACM Trans. Algorithms*. **17** (4): 33:1–33:67. [arXiv](./ArXiv_(identifier)):[1711.07710](https://arxiv.org/abs/1711.07710). [doi](./Doi_(identifier)):[10.1145/3473713](https://doi.org/10.1145%2F3473713).
40. [↑](./Knapsack_problem#cite_ref-40) Han, Xin; Kawase, Yasushi; Makino, Kazuhisa (11 January 2015). ["Randomized algorithms for online knapsack problems"](https://www.sciencedirect.com/science/article/pii/S0304397514007798). *Theoretical Computer Science*. **562**: 395–405. [doi](./Doi_(identifier)):[10.1016/j.tcs.2014.10.017](https://doi.org/10.1016%2Fj.tcs.2014.10.017). [ISSN](./ISSN_(identifier)) [0304-3975](https://search.worldcat.org/issn/0304-3975).
41. [↑](./Knapsack_problem#cite_ref-41) Han, Xin; Kawase, Yasushi; Makino, Kazuhisa (1 September 2014). ["Online Unweighted Knapsack Problem with Removal Cost"](https://link.springer.com/article/10.1007/s00453-013-9822-z). *Algorithmica*. **70** (1): 76–91. [doi](./Doi_(identifier)):[10.1007/s00453-013-9822-z](https://doi.org/10.1007%2Fs00453-013-9822-z). [ISSN](./ISSN_(identifier)) [1432-0541](https://search.worldcat.org/issn/1432-0541).
42. [↑](./Knapsack_problem#cite_ref-42) Han, Xin; Kawase, Yasushi; Makino, Kazuhisa; Guo, He (26 June 2014). ["Online removable knapsack problem under convex function"](https://doi.org/10.1016%2Fj.tcs.2013.09.013). *Theoretical Computer Science*. Combinatorial Optimization: Theory of algorithms and Complexity. 540–541: 62–69. [doi](./Doi_(identifier)):[10.1016/j.tcs.2013.09.013](https://doi.org/10.1016%2Fj.tcs.2013.09.013). [ISSN](./ISSN_(identifier)) [0304-3975](https://search.worldcat.org/issn/0304-3975).
43. [↑](./Knapsack_problem#cite_ref-43) Han, Xin; Kawase, Yasushi; Makino, Kazuhisa; Yokomaku, Haruki (22 September 2019), *Online Knapsack Problems with a Resource Buffer*, [arXiv](./ArXiv_(identifier)):[1909.10016](https://arxiv.org/abs/1909.10016)

 

## References

 
- [Garey, Michael R.](./Michael_R._Garey); [David S. Johnson](./David_S._Johnson) (1979). [*Computers and Intractability: A Guide to the Theory of NP-Completeness*](./Computers_and_Intractability:_A_Guide_to_the_Theory_of_NP-Completeness). W.H. Freeman. [ISBN](./ISBN_(identifier)) [978-0-7167-1045-5](./Special:BookSources/978-0-7167-1045-5). A6: MP9, pg.247.
- Kellerer, Hans; Pferschy, Ulrich; Pisinger, David (2004). *Knapsack Problems*. Springer. [doi](./Doi_(identifier)):[10.1007/978-3-540-24777-7](https://doi.org/10.1007%2F978-3-540-24777-7). [ISBN](./ISBN_(identifier)) [978-3-540-40286-2](./Special:BookSources/978-3-540-40286-2). [MR](./MR_(identifier)) [2161720](https://mathscinet.ams.org/mathscinet-getitem?mr=2161720). [S2CID](./S2CID_(identifier)) [28836720](https://api.semanticscholar.org/CorpusID:28836720).
- Martello, Silvano; Toth, Paolo (1990). [*Knapsack problems: Algorithms and computer implementations*](http://www.or.deis.unibo.it/knapsack.html). Wiley-Interscience. [ISBN](./ISBN_(identifier)) [978-0-471-92420-3](./Special:BookSources/978-0-471-92420-3). [MR](./MR_(identifier)) [1086874](https://mathscinet.ams.org/mathscinet-getitem?mr=1086874).

 

## External links

 
- [Lecture slides on the knapsack problem](http://www.cse.unl.edu/~goddard/Courses/CSCE310J/Lectures/Lecture8-DynamicProgramming.pdf)
- [PYAsUKP: Yet Another solver for the Unbounded Knapsack Problem](https://web.archive.org/web/20111006142943/http://download.gna.org/pyasukp/), with code taking advantage of the dominance relations in an hybrid algorithm, benchmarks and downloadable copies of some papers.
- [Home page of David Pisinger](http://www.diku.dk/~pisinger/) with downloadable copies of some papers on the publication list (including  "Where are the hard knapsack problems?")
- [Knapsack Problem solutions in many languages](http://rosettacode.org/wiki/Knapsack_Problem) at [Rosetta Code](./Rosetta_Code)
- [Dynamic Programming algorithm to 0/1 Knapsack problem](http://www.personal.kent.edu/~rmuhamma/Algorithms/MyAlgorithms/Dynamic/knapsackdyn.htm)
- [Knapsack Problem solver (online)](https://web.archive.org/web/20140223114908/http://karaffeltut.com/NEWKaraffeltutCom/Knapsack/knapsack.html)
- [Solving 0-1-KNAPSACK with Genetic Algorithms in Ruby](http://www.nils-haldenwang.de/computer-science/computational-intelligence/genetic-algorithm-vs-0-1-knapsack) [Archived](https://web.archive.org/web/20110523210824/http://www.nils-haldenwang.de/computer-science/computational-intelligence/genetic-algorithm-vs-0-1-knapsack) 23 May 2011 at the [Wayback Machine](./Wayback_Machine)
- [Codes for Quadratic Knapsack Problem](http://www.adaptivebox.net/CILib/code/qkpcodes_link.html) [Archived](https://web.archive.org/web/20150214020941/http://www.adaptivebox.net/CILib/code/qkpcodes_link.html) 14 February 2015 at the [Wayback Machine](./Wayback_Machine)

 

 
- [Optimizing Three-Dimensional Bin Packing](https://web.archive.org/web/20190303205438/http://pdfs.semanticscholar.org/bb99/86af2f26f7726fcef1bc684eac8239c9b853.pdf)
- [Knapsack Integer Programming Solution in Python](http://apmonitor.com/me575/index.php/Main/KnapsackOptimization) [Gekko (optimization software)](./Gekko_(optimization_software))