---
source: https://en.wikipedia.org/wiki/Binary_search
fetched: 2026-06-19
---

Search algorithm finding the position of a target value within a sorted array This article is about searching a finite sorted array. For searching continuous function values, see [bisection method](./Bisection_method). 

 

 
| Visualization of the binary search algorithm where 7 is the target value |
| --- |
| Class | Search algorithm |
| Data structure | Array |
| Worst-caseperformance | O(logn) |
| Best-caseperformance | O(1) |
| Averageperformance | O(logn) |
| Worst-casespace complexity | O(1) |
| Optimal | Yes |

 

In [computer science](./Computer_science), **binary search**, also known as **half-interval search**,[[1]](./Binary_search#cite_note-Williams1976-1) **logarithmic search**,[[2]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Binary_search"-2) or **binary chop**,[[3]](./Binary_search#cite_note-FOOTNOTEButterfieldNgondi201646-3) is a [search algorithm](./Search_algorithm) that finds the position of a target value within a [sorted array](./Sorted_array).[[4]](./Binary_search#cite_note-FOOTNOTECormenLeisersonRivestStein200939-4)[[5]](./Binary_search#cite_note-5) Binary search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target value, and repeating this until the target value is found. If the search ends with the remaining half being empty, the target is not in the array.

 

Binary search runs in [logarithmic time](./Time_complexity#Logarithmic_time) in the [worst case](./Best,_worst_and_average_case), making     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) comparisons, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of elements in the array.[[a]](./Binary_search#cite_note-6)[[6]](./Binary_search#cite_note-FloresMadpis1971-7) Binary search is faster than [linear search](./Linear_search) except for small arrays. However, the array must be sorted first to be able to apply binary search. There are specialized [data structures](./Data_structures) designed for fast searching, such as [hash tables](./Hash_tables), that can be searched more efficiently than binary search. However, binary search can be used to solve a wider range of problems, such as finding the next-smallest or next-largest element in the array relative to the target even if it is absent from the array.

 

There are numerous variations of binary search. In particular, [fractional cascading](./Fractional_cascading) speeds up binary searches for the same value in multiple arrays. Fractional cascading efficiently solves a number of search problems in [computational geometry](./Computational_geometry) and in numerous other fields. [Exponential search](./Exponential_search) extends binary search to unbounded lists. The [binary search tree](./Binary_search_tree) and [B-tree](./B-tree) data structures are based on binary search.

 

## Algorithm

 

Binary search works on sorted arrays. Binary search begins by comparing an element in the middle of the array with the target value. If the target value matches the element, its position in the array is returned. If the target value is less than the element, the search continues in the lower half of the array. If the target value is greater than the element, the search continues in the upper half of the array. By doing this, the algorithm eliminates the half in which the target value cannot lie in each iteration.[[7]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"-8)

 

### Procedure

 

Given an array     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) elements with values or [records](./Record_(computer_science))      A  0   ,  A  1   ,  A  2   , … …  ,  A  n − −  1     {\displaystyle A_{0},A_{1},A_{2},\ldots ,A_{n-1}}  ![{\displaystyle A_{0},A_{1},A_{2},\ldots ,A_{n-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d8d813e3e6d50ef13e04948e72fcacaf43b7d5c)sorted such that      A  0   ≤ ≤   A  1   ≤ ≤   A  2   ≤ ≤  ⋯ ⋯  ≤ ≤   A  n − −  1     {\displaystyle A_{0}\leq A_{1}\leq A_{2}\leq \cdots \leq A_{n-1}}  ![{\displaystyle A_{0}\leq A_{1}\leq A_{2}\leq \cdots \leq A_{n-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/13c473f721041f872e852b4ad816f5ee77b1681d), and target value     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0), the following [subroutine](./Subroutine) uses binary search to find the index of     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) in     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3).[[7]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"-8)

 
1. Set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     n − −  1   {\displaystyle n-1}  ![{\displaystyle n-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521).
2. If     L > R   {\displaystyle L>R}  ![{\displaystyle L>R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/145ce1d631364a50d19ac5264c7dc09d4e158b0a), the search terminates as unsuccessful.
3. Set     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the position of the middle element) to     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) plus the [floor](./Floor_and_ceiling_functions) of        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521), which is the greatest integer less than or equal to        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521).
4. If      A  m   < T   {\displaystyle A_{m}<T}  ![{\displaystyle A_{m}<T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3f302eb8600e5c6930a74778a3232e4a1c8d91bc), set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     m + 1   {\displaystyle m+1}  ![{\displaystyle m+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6f7ed29a2b4a62d3b6af05cd91a58ffc6094201) and go to step 2.
5. If      A  m   > T   {\displaystyle A_{m}>T}  ![{\displaystyle A_{m}>T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8f333a047adf793929566dda96ffdf4493cf3b7), set     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     m − −  1   {\displaystyle m-1}  ![{\displaystyle m-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecbbd201e0d8f1ccc91cb46362c4b72fa1bbe6c2) and go to step 2.
6. Now      A  m   = T   {\displaystyle A_{m}=T}  ![{\displaystyle A_{m}=T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0e65e98f38acc1a2a6e07c43495b3a0058255c6d), the search is done; return     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc).

 

This iterative procedure keeps track of the search boundaries with the two variables     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33). The procedure may be expressed in [pseudocode](./Pseudocode) as follows, where the variable names and types remain the same as above, `floor` is the [floor function](./Floor_function), and `unsuccessful` refers to a specific value that conveys the failure of the search.[[7]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"-8)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c1/Binary-search-work.gif/250px-Binary-search-work.gif)](./File:Binary-search-work.gif)binary-search 
```
function binary_search(A, n, T) is
    L := 0
    R := n − 1
    while L ≤ R do
        m := L + floor((R - L) / 2)
        if A[m] < T then
            L := m + 1
        else if A[m] > T then
            R := m − 1
        else:
            return m
    return unsuccessful
```
 

Alternatively, the algorithm may take the [ceiling](./Floor_and_ceiling_functions) of        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521). This may change the result if the target value appears more than once in the array.

 

#### Alternative procedure

 

In the above procedure, the algorithm checks whether the middle element (    m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc)) is equal to the target (    T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0)) in every iteration. Some implementations leave out this check during each iteration. The algorithm would perform this check only when one element is left (when     L = R   {\displaystyle L=R}  ![{\displaystyle L=R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c86913dc0a2e9c004d477017bccd932a5dc00d59)). This results in a faster comparison loop, as one comparison is eliminated per iteration, while it requires only one more iteration on average.[[8]](./Binary_search#cite_note-Bottenbruch1962-9)

 

[Hermann Bottenbruch](./Hermann_Bottenbruch) published the first implementation to leave out this check in 1962.[[8]](./Binary_search#cite_note-Bottenbruch1962-9)[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10)

 
1. Set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     n − −  1   {\displaystyle n-1}  ![{\displaystyle n-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521).
2. While     L ≠ ≠  R   {\displaystyle L\neq R}  ![{\displaystyle L\neq R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49051c2ce267152ac0a4262cbda350c22d108752),

1. Set     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the position of the middle element) to     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) plus the [ceiling](./Floor_and_ceiling_functions) of        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521), which is the least integer greater than or equal to        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521).
2. If      A  m   > T   {\displaystyle A_{m}>T}  ![{\displaystyle A_{m}>T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8f333a047adf793929566dda96ffdf4493cf3b7), set     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     m − −  1   {\displaystyle m-1}  ![{\displaystyle m-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecbbd201e0d8f1ccc91cb46362c4b72fa1bbe6c2).
3. Else,      A  m   ≤ ≤  T   {\displaystyle A_{m}\leq T}  ![{\displaystyle A_{m}\leq T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e031ef07d462e74d03758bcac4adb1a1a117ab32); set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc).

3. Now     L = R   {\displaystyle L=R}  ![{\displaystyle L=R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c86913dc0a2e9c004d477017bccd932a5dc00d59), the search is done. If      A  L   = T   {\displaystyle A_{L}=T}  ![{\displaystyle A_{L}=T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a4373e3e18ed6b51e3b76011bf80faebbe2cc93), return     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8). Otherwise, the search terminates as unsuccessful.

 

Where `ceil` is the ceiling function, the pseudocode for this version is:

 
```
function binary_search_alternative(A, n, T) is
    L := 0
    R := n − 1
    while L != R do
        m := L + ceil((R - L) / 2)
        if A[m] > T then
            R := m − 1
        else:
            L := m
    if A[L] = T then
        return L
    return unsuccessful
```
 

### Duplicate elements

 

The procedure may return any index whose element is equal to the target value, even if there are duplicate elements in the array. For example, if the array to be searched was     [ 1 , 2 , 3 , 4 , 4 , 5 , 6 , 7 ]   {\displaystyle [1,2,3,4,4,5,6,7]}  ![{\displaystyle [1,2,3,4,4,5,6,7]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d3a10b0250aafff08cc862bc99b5f3b4f7c33f3) and the target was     4   {\displaystyle 4}  ![{\displaystyle 4}](https://wikimedia.org/api/rest_v1/media/math/render/svg/295b4bf1de7cd3500e740e0f4f0635db22d87b42), then it would be correct for the algorithm to either return the 4th (index 3) or 5th (index 4) element. The regular procedure would return the 4th element (index 3) in this case. It does not always return the first duplicate (consider     [ 1 , 2 , 4 , 4 , 4 , 5 , 6 , 7 ]   {\displaystyle [1,2,4,4,4,5,6,7]}  ![{\displaystyle [1,2,4,4,4,5,6,7]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5867073891e85c24ad16f2e0df8a93bd487cdec3) which still returns the 4th element). However, it is sometimes necessary to find the leftmost element or the rightmost element for a target value that is duplicated in the array. In the above example, the 4th element is the leftmost element of the value 4, while the 5th element is the rightmost element of the value 4. The alternative procedure above will always return the index of the rightmost element if such an element exists.[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10)

 

#### Procedure for finding the leftmost element

 

To find the leftmost element, the following procedure can be used:[[10]](./Binary_search#cite_note-FOOTNOTEKasaharaMorishita20068–9-11)

 
1. Set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b).
2. While     L < R   {\displaystyle L<R}  ![{\displaystyle L<R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f7d11a3c4de7c898169e7e7fc8f48b920317ce0f),

1. Set     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the position of the middle element) to     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) plus the [floor](./Floor_and_ceiling_functions) of        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521), which is the greatest integer less than or equal to        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521).
2. If      A  m   < T   {\displaystyle A_{m}<T}  ![{\displaystyle A_{m}<T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3f302eb8600e5c6930a74778a3232e4a1c8d91bc), set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     m + 1   {\displaystyle m+1}  ![{\displaystyle m+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6f7ed29a2b4a62d3b6af05cd91a58ffc6094201).
3. Else,      A  m   ≥ ≥  T   {\displaystyle A_{m}\geq T}  ![{\displaystyle A_{m}\geq T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3cd57cf37953f42385f4fd9f29f0f399df6933c7); set *    R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33)* to     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc).

3. Return     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8).

 

If     L < n   {\displaystyle L<n}  ![{\displaystyle L<n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3bb3bae6c384daab0d9cd7208aba6f7a743c221d) and      A  L   = T   {\displaystyle A_{L}=T}  ![{\displaystyle A_{L}=T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a4373e3e18ed6b51e3b76011bf80faebbe2cc93), then      A  L     {\displaystyle A_{L}}  ![{\displaystyle A_{L}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/543968f6cc63f97109c5ba70d7dfe9bc23176442) is the leftmost element that equals     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0). Even if     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) is not in the array,     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) is the [rank](./Binary_search#Approximate_matches) of     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) in the array, or the number of elements in the array that are less than     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0).

 

Where `floor` is the floor function, the pseudocode for this version is:

 
```
function binary_search_leftmost(A, n, T):
    L := 0
    R := n
    while L < R:
        m := L + floor((R - L) / 2)
        if A[m] < T:
            L := m + 1
        else:
            R := m
    return L
```
 

#### Procedure for finding the rightmost element

 

To find the rightmost element, the following procedure can be used:[[10]](./Binary_search#cite_note-FOOTNOTEKasaharaMorishita20068–9-11)

 
1. Set     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) to     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b).
2. While     L < R   {\displaystyle L<R}  ![{\displaystyle L<R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f7d11a3c4de7c898169e7e7fc8f48b920317ce0f),

1. Set     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the position of the middle element) to     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) plus the [floor](./Floor_and_ceiling_functions) of        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521), which is the greatest integer less than or equal to        R − −  L  2     {\displaystyle {\frac {R-L}{2}}}  ![{\displaystyle {\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/801f3c2d241b36a59832f085772765bea3956521).
2. If      A  m   > T   {\displaystyle A_{m}>T}  ![{\displaystyle A_{m}>T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8f333a047adf793929566dda96ffdf4493cf3b7), set     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) to     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc).
3. Else,      A  m   ≤ ≤  T   {\displaystyle A_{m}\leq T}  ![{\displaystyle A_{m}\leq T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e031ef07d462e74d03758bcac4adb1a1a117ab32); set *    L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8)* to     m + 1   {\displaystyle m+1}  ![{\displaystyle m+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6f7ed29a2b4a62d3b6af05cd91a58ffc6094201).

3. Return     R − −  1   {\displaystyle R-1}  ![{\displaystyle R-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b753e9a143e573930c3b756cd21b27a5f33f6a1).

 

If     R > 0   {\displaystyle R>0}  ![{\displaystyle R>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/57914127d03a5cea02c60a32cfbb22f34904f00d) and      A  R − −  1   = T   {\displaystyle A_{R-1}=T}  ![{\displaystyle A_{R-1}=T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4af970b83da631be1036b4923e59669cca3c253), then      A  R − −  1     {\displaystyle A_{R-1}}  ![{\displaystyle A_{R-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bc9841052e04d66c14d4cf1ac1d653438a2ad6a1) is the rightmost element that equals     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0). Even if *    T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0)* is not in the array,     n − −  R   {\displaystyle n-R}  ![{\displaystyle n-R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/237932bba5fe0a0dbf98410bbb454475fd52a065) is the number of elements in the array that are greater than *    T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0)*.

 

Where `floor` is the floor function, the pseudocode for this version is:

 
```
function binary_search_rightmost(A, n, T):
    L := 0
    R := n
    while L < R:
        m := L + floor((R - L) / 2)
        if A[m] > T:
            R := m
        else:
            L := m + 1
    return R - 1
```
 

### Approximate matches

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Approximate-binary-search.svg/500px-Approximate-binary-search.svg.png)](./File:Approximate-binary-search.svg)Binary search can be adapted to compute approximate matches. In the example above, the rank, predecessor, successor, and nearest neighbor are shown for the target value     5   {\displaystyle 5}  ![{\displaystyle 5}](https://wikimedia.org/api/rest_v1/media/math/render/svg/29483407999b8763f0ea335cf715a6a5e809f44b), which is not in the array. 

The above procedure only performs *exact* matches, finding the position of a target value. However, it is trivial to extend binary search to perform approximate matches because binary search operates on sorted arrays. For example, binary search can be used to compute, for a given value, its rank (the number of smaller elements), predecessor (next-smallest element), successor (next-largest element), and [nearest neighbor](./Nearest_neighbor_search). [Range queries](./Range_query_(data_structures)) seeking the number of elements between two values can be performed with two rank queries.[[11]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"-12)

 
- Rank queries can be performed with the [procedure for finding the leftmost element](./Binary_search#Procedure_for_finding_the_leftmost_element). The number of elements *less than* the target value is returned by the procedure.[[11]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"-12)
- Predecessor queries can be performed with rank queries. If the rank of the target value is     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538), its predecessor is     r − −  1   {\displaystyle r-1}  ![{\displaystyle r-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ad04896104e929da32fad148e240b3fd8dfa874).[[12]](./Binary_search#cite_note-FOOTNOTEGoldmanGoldman2008461–463-13)
- For successor queries, the [procedure for finding the rightmost element](./Binary_search#Procedure_for_finding_the_rightmost_element) can be used. If the result of running the procedure for the target value is *    r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538)*, then the successor of the target value is     r + 1   {\displaystyle r+1}  ![{\displaystyle r+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7bf1b7e1e8ed2801660c299494ed10e6f18f790d).[[12]](./Binary_search#cite_note-FOOTNOTEGoldmanGoldman2008461–463-13)
- The nearest neighbor of the target value is either its predecessor or successor, whichever is closer.
- Range queries are also straightforward.[[12]](./Binary_search#cite_note-FOOTNOTEGoldmanGoldman2008461–463-13) Once the ranks of the two values are known, the number of elements greater than or equal to the first value and less than the second is the difference of the two ranks. This count can be adjusted up or down by one according to whether the endpoints of the range should be considered to be part of the range and whether the array contains entries matching those endpoints.[[13]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Range_queries"-14)

 

## Performance

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Binary_search_example_tree.svg/250px-Binary_search_example_tree.svg.png)](./File:Binary_search_example_tree.svg)A [tree](./Tree_(data_structure)) representing binary search. The array being searched here is     [ 20 , 30 , 40 , 50 , 80 , 90 , 100 ]   {\displaystyle [20,30,40,50,80,90,100]}  ![{\displaystyle [20,30,40,50,80,90,100]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a2a762c441505aff6153082ad4c7863a26f52962), and the target value is     40   {\displaystyle 40}  ![{\displaystyle 40}](https://wikimedia.org/api/rest_v1/media/math/render/svg/686d435c2512a705c6680b84e9d172f259941f7a). [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Binary_search_complexity.svg/500px-Binary_search_complexity.svg.png)](./File:Binary_search_complexity.svg)The worst case is reached when the search reaches the deepest level of the tree, while the best case is reached when the target value is the middle element. 

In terms of the number of comparisons, the performance of binary search can be analyzed by viewing the run of the procedure on a binary tree. The root node of the tree is the middle element of the array. The middle element of the lower half is the left child node of the root, and the middle element of the upper half is the right child node of the root. The rest of the tree is built in a similar fashion. Starting from the root node, the left or right subtrees are traversed depending on whether the target value is less or more than the node under consideration.[[6]](./Binary_search#cite_note-FloresMadpis1971-7)[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

In the worst case, binary search makes     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}(n)+1\rfloor }  ![{\textstyle \lfloor \log _{2}(n)+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/7928b7b7af618a0184d934219526c5c5e2b6fc06) iterations of the comparison loop, where the     ⌊ ⌊  ⋅ ⋅  ⌋ ⌋    {\textstyle \lfloor \cdot \rfloor }  ![{\textstyle \lfloor \cdot \rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/4008aeac65a4d0dcb42b26d5309528f73b37a64d) notation denotes the [floor function](./Floor_function) that yields the greatest integer less than or equal to the argument, and      log  2     {\textstyle \log _{2}}  ![{\textstyle \log _{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a493f09c50f545ad47dba794bf06b66a94893d1) is the [binary logarithm](./Binary_logarithm). This is because the worst case is reached when the search reaches the deepest level of the tree, and there are always     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}(n)+1\rfloor }  ![{\textstyle \lfloor \log _{2}(n)+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/7928b7b7af618a0184d934219526c5c5e2b6fc06) levels in the tree for any binary search.

 

The worst case may also be reached when the target element is not in the array. If     n   {\textstyle n}  ![{\textstyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc6e1f880981346a604257ebcacdef24c0aca2d6) is one less than a [power of two](./Power_of_two), then this is always the case. Otherwise, the search may perform     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}(n)+1\rfloor }  ![{\textstyle \lfloor \log _{2}(n)+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/7928b7b7af618a0184d934219526c5c5e2b6fc06)iterations if the search reaches the deepest level of the tree. However, it may make     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋    {\textstyle \lfloor \log _{2}(n)\rfloor }  ![{\textstyle \lfloor \log _{2}(n)\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/22ca7cce146baea017de6b182d3aaff99af0c8bd) iterations, which is one less than the worst case, if the search ends at the second-deepest level of the tree.[[15]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_"Theorem_B"-16)

 

On average, assuming that each element is equally likely to be searched, binary search makes     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1 − −  (  2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1   − −  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  − −  2 )  /  n   {\displaystyle \lfloor \log _{2}(n)\rfloor +1-(2^{\lfloor \log _{2}(n)\rfloor +1}-\lfloor \log _{2}(n)\rfloor -2)/n}  ![{\displaystyle \lfloor \log _{2}(n)\rfloor +1-(2^{\lfloor \log _{2}(n)\rfloor +1}-\lfloor \log _{2}(n)\rfloor -2)/n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/29b723650fef7fc47b8ebe3f1d93c109cdb5d12b) iterations when the target element is in the array. This is approximately equal to      log  2   ⁡ ⁡  ( n ) − −  1   {\displaystyle \log _{2}(n)-1}  ![{\displaystyle \log _{2}(n)-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5c75208a76daad7c09420b4a19d784c45530a87) iterations. When the target element is not in the array, binary search makes     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 2 − −   2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1    /  ( n + 1 )   {\displaystyle \lfloor \log _{2}(n)\rfloor +2-2^{\lfloor \log _{2}(n)\rfloor +1}/(n+1)}  ![{\displaystyle \lfloor \log _{2}(n)\rfloor +2-2^{\lfloor \log _{2}(n)\rfloor +1}/(n+1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8076f066d54334bbaf1ecfe396ad494c86d5446a) iterations on average, assuming that the range between and outside elements is equally likely to be searched.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

In the best case, where the target value is the middle element of the array, its position is returned after one iteration.[[16]](./Binary_search#cite_note-FOOTNOTEChang2003169-17)

 

In terms of iterations, no search algorithm that works only by comparing elements can exhibit better average and worst-case performance than binary search. The comparison tree representing binary search has the fewest levels possible as every level above the lowest level of the tree is filled completely.[[b]](./Binary_search#cite_note-18) Otherwise, the search algorithm can eliminate few elements in an iteration, increasing the number of iterations required in the average and worst case. This is the case for other search algorithms based on comparisons, as while they may work faster on some target values, the average performance over *all* elements is worse than binary search. By dividing the array in half, binary search ensures that the size of both subarrays are as similar as possible.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

### Space complexity

 

Binary search requires three pointers to elements, which may be array indices or pointers to memory locations, regardless of the size of the array. Therefore, the [space complexity](./Space_complexity) of binary search is     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) in the [word RAM](./Word_RAM) [model of computation](./Model_of_computation).

 

### Derivation of average case

 

The average number of iterations performed by binary search depends on the probability of each element being searched. The average case is different for successful searches and unsuccessful searches. It will be assumed that each element is equally likely to be searched for successful searches. For unsuccessful searches, it will be assumed that the [intervals](./Interval_(mathematics)) between and outside elements are equally likely to be searched. The average case for successful searches is the number of iterations required to search every element exactly once, divided by     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), the number of elements. The average case for unsuccessful searches is the number of iterations required to search an element within every interval exactly once, divided by the     n + 1   {\displaystyle n+1}  ![{\displaystyle n+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a135e65a42f2d73cccbfc4569523996ca0036f1) intervals.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

#### Successful searches

  E stands for "expected"  

In the binary tree representation, a successful search can be represented by a path from the root to the target node, called an *internal path*. The length of a path is the number of edges (connections between nodes) that the path passes through. The number of iterations performed by a search, given that the corresponding path has length l, is     l + 1   {\displaystyle l+1}  ![{\displaystyle l+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b611b61103606b988023375dc7dc44046d1e7f9d) counting the initial iteration. The *internal path length* is the sum of the lengths of all unique internal paths. Since there is only one path from the root to any single node, each internal path represents a search for a specific element. If there are n elements, which is a positive integer, and the internal path length is     I ( n )   {\displaystyle I(n)}  ![{\displaystyle I(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ae81bd86e4a3bb04199358dc26325d3889e7b93), then the average number of iterations for a successful search     T ( n ) = 1 +    I ( n )  n     {\displaystyle T(n)=1+{\frac {I(n)}{n}}}  ![{\displaystyle T(n)=1+{\frac {I(n)}{n}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7384199e6eba1f9257188bd3440622f5a3b7fea1), with the one iteration added to count the initial iteration.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

Since binary search is the optimal algorithm for searching with comparisons, this problem is reduced to calculating the minimum internal path length of all binary trees with n nodes, which is equal to:[[17]](./Binary_search#cite_note-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")-19)

 

    I ( n ) =  ∑ ∑   k = 1   n    ⌊   log  2   ⁡ ⁡  ( k )  ⌋    {\displaystyle I(n)=\sum _{k=1}^{n}\left\lfloor \log _{2}(k)\right\rfloor }  ![{\displaystyle I(n)=\sum _{k=1}^{n}\left\lfloor \log _{2}(k)\right\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd31bd3da2406b50deae2a55a2f85c920d3437db)

 

For example, in a 7-element array, the root requires one iteration, the two elements below the root require two iterations, and the four elements below require three iterations. In this case, the internal path length is:[[17]](./Binary_search#cite_note-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")-19)

 

     ∑ ∑   k = 1   7    ⌊   log  2   ⁡ ⁡  ( k )  ⌋  = 0 + 2 ( 1 ) + 4 ( 2 ) = 2 + 8 = 10   {\displaystyle \sum _{k=1}^{7}\left\lfloor \log _{2}(k)\right\rfloor =0+2(1)+4(2)=2+8=10}  ![{\displaystyle \sum _{k=1}^{7}\left\lfloor \log _{2}(k)\right\rfloor =0+2(1)+4(2)=2+8=10}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e9fe3bdbc0672707e8a54ea46c75c0606568dad)

 

The average number of iterations would be     1 +   10 7   = 2   3 7     {\displaystyle 1+{\frac {10}{7}}=2{\frac {3}{7}}}  ![{\displaystyle 1+{\frac {10}{7}}=2{\frac {3}{7}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/24b4a392be5c5feaa883e3ea1a432fc9bc966613) based on the equation for the average case. The sum for     I ( n )   {\displaystyle I(n)}  ![{\displaystyle I(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ae81bd86e4a3bb04199358dc26325d3889e7b93) can be simplified to:[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

    I ( n ) =  ∑ ∑   k = 1   n    ⌊   log  2   ⁡ ⁡  ( k )  ⌋  = ( n + 1 )  ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  − −   2   ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  + 1   + 2   {\displaystyle I(n)=\sum _{k=1}^{n}\left\lfloor \log _{2}(k)\right\rfloor =(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2}  ![{\displaystyle I(n)=\sum _{k=1}^{n}\left\lfloor \log _{2}(k)\right\rfloor =(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a7bcd9b31e894139312fb84b8a879b21e615bf0)

 

Substituting the equation for     I ( n )   {\displaystyle I(n)}  ![{\displaystyle I(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ae81bd86e4a3bb04199358dc26325d3889e7b93) into the equation for     T ( n )   {\displaystyle T(n)}  ![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002):[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

    T ( n ) = 1 +    ( n + 1 )  ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  − −   2   ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  + 1   + 2  n   = ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1 − −  (  2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1   − −  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  − −  2 )  /  n   {\displaystyle T(n)=1+{\frac {(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2}{n}}=\lfloor \log _{2}(n)\rfloor +1-(2^{\lfloor \log _{2}(n)\rfloor +1}-\lfloor \log _{2}(n)\rfloor -2)/n}  ![{\displaystyle T(n)=1+{\frac {(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2}{n}}=\lfloor \log _{2}(n)\rfloor +1-(2^{\lfloor \log _{2}(n)\rfloor +1}-\lfloor \log _{2}(n)\rfloor -2)/n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7243dc7974c37c7291a32e04b67ac422ba01e3eb)

 

For integer n, this is equivalent to the equation for the average case on a successful search specified above.

 

#### Unsuccessful searches

 

Unsuccessful searches can be represented by augmenting the tree with *external nodes*, which forms an *extended binary tree*. If an internal node, or a node present in the tree, has fewer than two child nodes, then additional child nodes, called external nodes, are added so that each internal node has two children. By doing so, an unsuccessful search can be represented as a path to an external node, whose parent is the single element that remains during the last iteration. An *external path* is a path from the root to an external node. The *external path length* is the sum of the lengths of all unique external paths. If there are     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) elements, which is a positive integer, and the external path length is     E ( n )   {\displaystyle E(n)}  ![{\displaystyle E(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a8b3b6ec0effe4cf5a6a54bd424fb04984dbe97d), then the average number of iterations for an unsuccessful search is      T ′  ( n ) =    E ( n )   n + 1      {\displaystyle T'(n)={\frac {E(n)}{n+1}}}  ![{\displaystyle T'(n)={\frac {E(n)}{n+1}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a09900d9732d45fd9535343216926c82af02103), with the one iteration added to count the initial iteration. The external path length is divided by     n + 1   {\displaystyle n+1}  ![{\displaystyle n+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a135e65a42f2d73cccbfc4569523996ca0036f1) instead of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) because there are     n + 1   {\displaystyle n+1}  ![{\displaystyle n+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a135e65a42f2d73cccbfc4569523996ca0036f1) external paths, representing the intervals between and outside the elements of the array.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

This problem can similarly be reduced to determining the minimum external path length of all binary trees with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) nodes. For all binary trees, the external path length is equal to the internal path length plus     2 n   {\displaystyle 2n}  ![{\displaystyle 2n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/134afa8ff09fdddd24b06f289e92e3a045092bd1).[[17]](./Binary_search#cite_note-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")-19) Substituting the equation for     I ( n )   {\displaystyle I(n)}  ![{\displaystyle I(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ae81bd86e4a3bb04199358dc26325d3889e7b93):[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

    E ( n ) = I ( n ) + 2 n =  [  ( n + 1 )  ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  − −   2   ⌊   log  2   ⁡ ⁡  ( n + 1 )  ⌋  + 1   + 2  ]  + 2 n = ( n + 1 ) ( ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 2 ) − −   2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1     {\displaystyle E(n)=I(n)+2n=\left[(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2\right]+2n=(n+1)(\lfloor \log _{2}(n)\rfloor +2)-2^{\lfloor \log _{2}(n)\rfloor +1}}  ![{\displaystyle E(n)=I(n)+2n=\left[(n+1)\left\lfloor \log _{2}(n+1)\right\rfloor -2^{\left\lfloor \log _{2}(n+1)\right\rfloor +1}+2\right]+2n=(n+1)(\lfloor \log _{2}(n)\rfloor +2)-2^{\lfloor \log _{2}(n)\rfloor +1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/edbb46592a2cfed4a5d626d6080fd530bf7693b5)

 

Substituting the equation for     E ( n )   {\displaystyle E(n)}  ![{\displaystyle E(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a8b3b6ec0effe4cf5a6a54bd424fb04984dbe97d) into the equation for      T ′  ( n )   {\displaystyle T'(n)}  ![{\displaystyle T'(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/72db032f4b261d03ccc74a13424b43eb1ca804a7), the average case for unsuccessful searches can be determined:[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)

 

     T ′  ( n ) =    ( n + 1 ) ( ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 2 ) − −   2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1     ( n + 1 )    = ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 2 − −   2  ⌊ ⌊   log  2   ⁡ ⁡  ( n ) ⌋ ⌋  + 1    /  ( n + 1 )   {\displaystyle T'(n)={\frac {(n+1)(\lfloor \log _{2}(n)\rfloor +2)-2^{\lfloor \log _{2}(n)\rfloor +1}}{(n+1)}}=\lfloor \log _{2}(n)\rfloor +2-2^{\lfloor \log _{2}(n)\rfloor +1}/(n+1)}  ![{\displaystyle T'(n)={\frac {(n+1)(\lfloor \log _{2}(n)\rfloor +2)-2^{\lfloor \log _{2}(n)\rfloor +1}}{(n+1)}}=\lfloor \log _{2}(n)\rfloor +2-2^{\lfloor \log _{2}(n)\rfloor +1}/(n+1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7312163a205d560b11fc77424d457f78b1d58df4)

 

#### Performance of alternative procedure

 

Each iteration of the binary search procedure defined above makes one or two comparisons, checking if the middle element is equal to the target in each iteration. Assuming that each element is equally likely to be searched, each iteration makes 1.5 comparisons on average. A variation of the algorithm checks whether the middle element is equal to the target at the end of the search. On average, this eliminates half a comparison from each iteration. This slightly cuts the time taken per iteration on most computers. However, it guarantees that the search takes the maximum number of iterations, on average adding one iteration to the search. Because the comparison loop is performed only     ⌊ ⌊   log  2   ⁡ ⁡  ( n ) + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}(n)+1\rfloor }  ![{\textstyle \lfloor \log _{2}(n)+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/7928b7b7af618a0184d934219526c5c5e2b6fc06) times in the worst case, the slight increase in efficiency per iteration does not compensate for the extra iteration for all but very large     n   {\textstyle n}  ![{\textstyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc6e1f880981346a604257ebcacdef24c0aca2d6).[[c]](./Binary_search#cite_note-21)[[18]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_23"-20)[[19]](./Binary_search#cite_note-22)

 

### Additional considerations

 

#### Cost of comparison

 

In analyzing the performance of binary search, another consideration is the time required to compare two elements. For integers and strings, the time required increases linearly as the encoding length (usually the number of [bits](./Bit)) of the elements increase. For example, comparing a pair of 64-bit unsigned integers would require comparing up to double the bits as comparing a pair of 32-bit unsigned integers. The worst case is achieved when the integers are equal. This can be significant when the encoding lengths of the elements are large, such as with large integer types or long strings, which makes comparing elements expensive. Furthermore, comparing [floating-point](./Floating-point_arithmetic) values (the most common digital representation of [real numbers](./Real_number)) is often more expensive than comparing integers or short strings.

 

Fast floating point comparison is possible via comparing as an integer. However, this kind of comparison forms a [total order](./Total_order), which makes *every* floating-point value compare differently from each other and the same as itself. This is different from the typical comparison where -0.0 should be the same as 0.0 and NaN should not compare the same as any other value including itself.[[20]](./Binary_search#cite_note-Herf_2001-23)[[21]](./Binary_search#cite_note-rust_total_cmp-24)

 

#### Branch prediction

 

According to [Steel Bank Common Lisp](./Steel_Bank_Common_Lisp) contributor Paul Khuong, binary search leads to very few [branch mispredictions](./Branch_misprediction) despite its data-dependent nature. This is in part because most of it can be expressed as [conditional moves](./Conditional_move) instead of branches. The same applies to most logarithmic divide-and-conquer search algorithms.[[22]](./Binary_search#cite_note-25)

 

#### Cache usage

 

On most computer architectures, the [processor](./Central_processing_unit) has a hardware [cache](./Cache_(computing)) separate from [RAM](./Random-access_memory). Since they are located within the processor itself, caches are much faster to access but usually store much less data than RAM. Therefore, most processors store memory locations that have been accessed recently, along with memory locations close to it. For example, when an array element is accessed, the element itself may be stored along with the elements that are stored close to it in RAM, making it faster to sequentially access array elements that are close in index to each other ([locality of reference](./Locality_of_reference)). On a sorted array, binary search can jump to distant memory locations if the array is large, unlike algorithms (such as [linear search](./Linear_search) and [linear probing](./Linear_probing) in [hash tables](./Hash_tables)) which access elements in sequence. This adds slightly to the running time of binary search for large arrays on most systems.[[23]](./Binary_search#cite_note-26)

 

Paul Khuong has noted that binary search on large (≥ 512 KiB) arrays of exactly a power-of-two size tends to cause an additional problem with how CPU caches are implemented. Specifically, the [translation lookaside buffer](./Translation_lookaside_buffer) (TLB) is often implemented as a [content-addressable memory](./Content-addressable_memory) (CAM), with the "key" usually being the lower bits of a requested address. When searching on an array of exactly a power-of-two size, [memory address](./Memory_address) with the same lower bits tend to be accessed, causing collisions ("aliasing") with the "key" used to fetch the CAM. The typical TLB is 4-way associative, meaning it can handle at most four addresses hitting the same "key", after which [TLB thrashing](./Thrashing_(computer_science)#TLB_thrashing) happens. (Although the other levels of CPU caches also use a similar setup, they manage smaller areas with a higher way count, usually 8 or 16, so they are less affected.) This can be prevented by offsetting the split point of the binary search so it divides at 31⁄64 instead of exactly the middle.[[24]](./Binary_search#cite_note-27)

 

## Binary search versus other schemes

 

Sorted arrays with binary search are a very inefficient solution when insertion and deletion operations are interleaved with retrieval, taking     O ( n )   {\textstyle O(n)}  ![{\textstyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e73234cd485b947e68d1d78823313db65ef226d7) time for each such operation. In addition, sorted arrays can complicate memory use especially when elements are often inserted into the array.[[25]](./Binary_search#cite_note-FOOTNOTEKnuth1997§2.2.2_("Sequential_Allocation")-28) There are other data structures that support much more efficient insertion and deletion. Binary search can be used to perform exact matching and [set membership](./Set_(abstract_data_type)) (determining whether a target value is in a collection of values). There are data structures that support faster exact matching and set membership. However, unlike many other searching schemes, binary search can be used for efficient approximate matching, usually performing such matches in     O ( log ⁡ ⁡  n )   {\textstyle O(\log n)}  ![{\textstyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/652bcc1f7bfa43527824017e3948b78c4ef942c4) time regardless of the type or structure of the values themselves.[[26]](./Binary_search#cite_note-pred-29) In addition, there are some operations, like finding the smallest and largest element, that can be performed efficiently on a sorted array.[[11]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"-12)

 

### Linear search

 

[Linear search](./Linear_search) is a simple search algorithm that checks every record until it finds the target value. Linear search can be done on a [linked list](./Linked_list), which allows for faster insertion and deletion than an array. Binary search is faster than linear search for sorted arrays except if the array is short, although the array needs to be sorted beforehand.[[d]](./Binary_search#cite_note-31)[[28]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table")-32) All [sorting algorithms](./Sorting_algorithm) based on comparing elements, such as [quicksort](./Quicksort) and [merge sort](./Merge_sort), require at least     O ( n log ⁡ ⁡  n )   {\textstyle O(n\log n)}  ![{\textstyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e300e6b542c2c33ac12df0f02c5047db8ee8e1ca) comparisons in the worst case.[[29]](./Binary_search#cite_note-FOOTNOTEKnuth1998§5.3.1_("Minimum-Comparison_sorting")-33) Unlike linear search, binary search can be used for efficient approximate matching. There are operations such as finding the smallest and largest element that can be done efficiently on a sorted array but not on an unsorted array.[[30]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.2_("Ordered_symbol_tables")-34)

 

### Trees

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/92/Binary_search_tree_search_4.svg/250px-Binary_search_tree_search_4.svg.png)](./File:Binary_search_tree_search_4.svg)[Binary search trees](./Binary_search_tree) are searched using an algorithm similar to binary search. 

A [binary search tree](./Binary_search_tree) is a [binary tree](./Binary_tree) data structure that works based on the principle of binary search. The records of the tree are arranged in sorted order, and each record in the tree can be searched using an algorithm similar to binary search, taking on average logarithmic time. Insertion and deletion also require on average logarithmic time in binary search trees. This can be faster than the linear time insertion and deletion of sorted arrays, and binary trees retain the ability to perform all the operations possible on a sorted array, including range and approximate queries.[[26]](./Binary_search#cite_note-pred-29)[[31]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.2_("Binary_Search_Trees"),_subsection_"Order-based_methods_and_deletion"-35)

 

However, binary search is usually more efficient for searching as binary search trees will most likely be imperfectly balanced, resulting in slightly worse performance than binary search. This even applies to [balanced binary search trees](./Self-balancing_binary_search_tree), binary search trees that balance their own nodes, because they rarely produce the tree with the fewest possible levels. Except for balanced binary search trees, the tree may be severely imbalanced with few internal nodes with two children, resulting in the average and worst-case search time approaching     n   {\textstyle n}  ![{\textstyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc6e1f880981346a604257ebcacdef24c0aca2d6) comparisons.[[e]](./Binary_search#cite_note-37) Binary search trees take more space than sorted arrays.[[33]](./Binary_search#cite_note-FOOTNOTESedgewickWayne2011§3.5_("Applications"),_"Which_symbol-table_implementation_should_I_use?"-38)

 

Binary search trees lend themselves to fast searching in external memory stored in hard disks, as binary search trees can be efficiently structured in filesystems. The [B-tree](./B-tree) generalizes this method of tree organization. B-trees are frequently used to organize long-term storage such as [databases](./Database) and [filesystems](./Filesystem).[[34]](./Binary_search#cite_note-FOOTNOTEKnuth1998§5.4.9_("Disks_and_Drums")-39)[[35]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.4_("Multiway_trees")-40)

 

### Hashing

 

For implementing [associative arrays](./Associative_arrays), [hash tables](./Hash_table), a data structure that maps keys to [records](./Record_(computer_science)) using a [hash function](./Hash_function), are generally faster than binary search on a sorted array of records.[[36]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.4_("Hashing")-41) Most hash table implementations require only [amortized](./Amortized_analysis) constant time on average.[[f]](./Binary_search#cite_note-43)[[38]](./Binary_search#cite_note-44) However, hashing is not useful for approximate matches, such as computing the next-smallest, next-largest, and nearest key, as the only information given on a failed search is that the target is not present in any record.[[39]](./Binary_search#cite_note-45) Binary search is ideal for such matches, performing them in logarithmic time. Binary search also supports approximate matches. Some operations, like finding the smallest and largest element, can be done efficiently on sorted arrays but not on hash tables.[[26]](./Binary_search#cite_note-pred-29)

 

### Set membership algorithms

 

A related problem to search is [set membership](./Set_(abstract_data_type)). Any algorithm that does lookup, like binary search, can also be used for set membership. There are other algorithms that are more specifically suited for set membership. A [bit array](./Bit_array) is the simplest, useful when the range of keys is limited. It compactly stores a collection of [bits](./Bit), with each bit representing a single key within the range of keys. Bit arrays are very fast, requiring only     O ( 1 )   {\textstyle O(1)}  ![{\textstyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/55a2cd47ca6554fafc21bbef3331256c7e1631ad) time.[[40]](./Binary_search#cite_note-FOOTNOTEKnuth2011§7.1.3_("Bitwise_Tricks_and_Techniques")-46)  The Judy1 type of [Judy array](./Judy_array) handles 64-bit keys efficiently.[[41]](./Binary_search#cite_note-judyarray-47)

 

For approximate results, [Bloom filters](./Bloom_filter), another probabilistic data structure based on hashing, store a [set](./Set_(mathematics)) of keys by encoding the keys using a [bit array](./Bit_array) and multiple hash functions. Bloom filters are much more space-efficient than bit arrays in most cases and not much slower: with     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) hash functions, membership queries require only     O ( k )   {\textstyle O(k)}  ![{\textstyle O(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d08f0e82ab18b57881692bb358acf93c3b77aa08) time. However, Bloom filters suffer from [false positives](./False_positives_and_false_negatives).[[g]](./Binary_search#cite_note-49)[[h]](./Binary_search#cite_note-50)[[43]](./Binary_search#cite_note-51)

 

### Other data structures

 

There exist data structures that may improve on binary search in some cases for both searching and other operations available for sorted arrays. For example, searches, approximate matches, and the operations available to sorted arrays can be performed more efficiently than binary search on specialized data structures such as [van Emde Boas trees](./Van_Emde_Boas_tree), [fusion trees](./Fusion_tree), [tries](./Trie), and [bit arrays](./Bit_array). These specialized data structures are usually only faster because they take advantage of the properties of keys with a certain attribute (usually keys that are small integers), and thus will be time or space consuming for keys that lack that attribute.[[26]](./Binary_search#cite_note-pred-29) As long as the keys can be ordered, these operations can always be done at least efficiently on a sorted array regardless of the keys. Some structures, such as Judy arrays, use a combination of approaches to mitigate this while retaining efficiency and the ability to perform approximate matching.[[41]](./Binary_search#cite_note-judyarray-47)

 

## Variations

 

### Uniform binary search

 Main article: [Uniform binary search](./Uniform_binary_search) [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Uniform_binary_search.svg/250px-Uniform_binary_search.svg.png)](./File:Uniform_binary_search.svg)[Uniform binary search](./Uniform_binary_search) stores the difference between the current and the two next possible middle elements instead of specific bounds. 

Uniform binary search stores, instead of the lower and upper bounds, the difference in the index of the middle element from the current iteration to the next iteration. A [lookup table](./Lookup_table) containing the differences is computed beforehand. For example, if the array to be searched is [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11], the middle element (    m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc)) would be 6. In this case, the middle element of the left subarray ([1, 2, 3, 4, 5]) is 3 and the middle element of the right subarray ([7, 8, 9, 10, 11]) is 9. Uniform binary search would store the value of 3 as both indices differ from 6 by this same amount.[[44]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"An_important_variation"-52) To reduce the search space, the algorithm either adds or subtracts this change from the index of the middle element. Uniform binary search may be faster on systems where it is inefficient to calculate the midpoint, such as on [decimal computers](./Decimal_computer).[[45]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_U"-53)

 

### Exponential search

 Main article: [Exponential search](./Exponential_search) [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/45/Exponential_search.svg/500px-Exponential_search.svg.png)](./File:Exponential_search.svg)Visualization of [exponential searching](./Exponential_search) finding the upper bound for the subsequent binary search 

Exponential search extends binary search to unbounded lists. It starts by finding the first element with an index that is both a power of two and greater than the target value. Afterwards, it sets that index as the upper bound, and switches to binary search. A search takes     ⌊ ⌊   log  2   ⁡ ⁡  x + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}x+1\rfloor }  ![{\textstyle \lfloor \log _{2}x+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/3f22b947af227cc3bf67bf716279f1faeeaca49c) iterations before binary search is started and at most     ⌊ ⌊   log  2   ⁡ ⁡  x ⌋ ⌋    {\textstyle \lfloor \log _{2}x\rfloor }  ![{\textstyle \lfloor \log _{2}x\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3330ca73e282147eb14b8e1d97c7f188a66b086) iterations of the binary search, where     x   {\textstyle x}  ![{\textstyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d951e0f3b54b6a3d73bb9a0a005749046cbce781) is the position of the target value. Exponential search works on bounded lists, but becomes an improvement over binary search only if the target value lies near the beginning of the array.[[46]](./Binary_search#cite_note-FOOTNOTEMoffatTurpin200233-54)

 

### Interpolation search

 Main article: [Interpolation search](./Interpolation_search) [![](//upload.wikimedia.org/wikipedia/commons/thumb/1/16/Interpolation_search.svg/500px-Interpolation_search.svg.png)](./File:Interpolation_search.svg)Visualization of [interpolation search](./Interpolation_search) using linear interpolation. In this case, no searching is needed because the estimate of the target's location within the array is correct. Other implementations may specify another function for estimating the target's location. 

Instead of calculating the midpoint, interpolation search estimates the position of the target value, taking into account the lowest and highest elements in the array as well as length of the array. It works on the basis that the midpoint is not the best guess in many cases. For example, if the target value is close to the highest element in the array, it is likely to be located near the end of the array.[[47]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"-55)

 

A common interpolation function is [linear interpolation](./Linear_interpolation). If     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) is the array,     L , R   {\displaystyle L,R}  ![{\displaystyle L,R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d6c07b5723438aabd50dc952b85f3f9aa79c2de7) are the lower and upper bounds respectively, and     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0) is the target, then the target is estimated to be about     ( T − −   A  L   )  /  (  A  R   − −   A  L   )   {\displaystyle (T-A_{L})/(A_{R}-A_{L})}  ![{\displaystyle (T-A_{L})/(A_{R}-A_{L})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/24317709d4900d0cc4663ff3429320bb22f4b98b) of the way between     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33). When linear interpolation is used, and the distribution of the array elements is uniform or near uniform, interpolation search makes     O ( log ⁡ ⁡  log ⁡ ⁡  n )   {\textstyle O(\log \log n)}  ![{\textstyle O(\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95438767f239d566148a43a8f7bfdf1287f0a4ff) comparisons.[[47]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"-55)[[48]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_22"-56)[[49]](./Binary_search#cite_note-57)

 

In practice, interpolation search is slower than binary search for small arrays, as interpolation search requires extra computation. Its time complexity grows more slowly than binary search, but this only compensates for the extra computation for large arrays.[[47]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"-55)

 

### Fractional cascading

 Main article: [Fractional cascading](./Fractional_cascading) [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/39/Fractional_cascading.svg/500px-Fractional_cascading.svg.png)](./File:Fractional_cascading.svg)In [fractional cascading](./Fractional_cascading), each array has pointers to every second element of another array, so only one binary search has to be performed to search all the arrays. 

Fractional cascading is a technique that speeds up binary searches for the same element in multiple sorted arrays. Searching each array separately requires     O ( k log ⁡ ⁡  n )   {\textstyle O(k\log n)}  ![{\textstyle O(k\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/39c2b84b1be09a3add49fd9ea23d0dabab53d146) time, where     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) is the number of arrays. Fractional cascading reduces this to     O ( k + log ⁡ ⁡  n )   {\textstyle O(k+\log n)}  ![{\textstyle O(k+\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/66ca6397616818018288f8e2407ab6d18a1a3a88) by storing specific information in each array about each element and its position in the other arrays.[[50]](./Binary_search#cite_note-ChazelleLiu2001-58)[[51]](./Binary_search#cite_note-ChazelleLiu2004-59)

 

Fractional cascading was originally developed to efficiently solve various [computational geometry](./Computational_geometry) problems. Fractional cascading has been applied elsewhere, such as in [data mining](./Data_mining) and [Internet Protocol](./Internet_Protocol) routing.[[50]](./Binary_search#cite_note-ChazelleLiu2001-58)

 

### Generalization to graphs

 

Binary search has been generalized to work on certain types of graphs, where the target value is stored in a vertex instead of an array element. Binary search trees are one such generalization—when a vertex (node) in the tree is queried, the algorithm either learns that the vertex is the target, or otherwise which subtree the target would be located in. However, this can be further generalized as follows: given an undirected, positively weighted graph and a target vertex, the algorithm learns upon querying a vertex that it is equal to the target, or it is given an incident edge that is on the shortest path from the queried vertex to the target. The standard binary search algorithm is simply the case where the graph is a path. Similarly, binary search trees are the case where the edges to the left or right subtrees are given when the queried vertex is unequal to the target. For all undirected, positively weighted graphs, there is an algorithm that finds the target vertex in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) queries in the worst case.[[52]](./Binary_search#cite_note-60)

 

### Noisy binary search

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/1/13/Noisy_binary_search.svg/250px-Noisy_binary_search.svg.png)](./File:Noisy_binary_search.svg)In noisy binary search, there is a certain probability that a comparison is incorrect. 

Noisy binary search algorithms solve the case where the algorithm cannot reliably compare elements of the array. For each pair of elements, there is a certain probability that the algorithm makes the wrong comparison. Noisy binary search can find the correct position of the target with a given probability that controls the reliability of the yielded position. Every noisy binary search procedure must make at least     ( 1 − −  τ τ  )     log  2   ⁡ ⁡  ( n )   H ( p )    − −    10  H ( p )      {\displaystyle (1-\tau ){\frac {\log _{2}(n)}{H(p)}}-{\frac {10}{H(p)}}}  ![{\displaystyle (1-\tau ){\frac {\log _{2}(n)}{H(p)}}-{\frac {10}{H(p)}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2488e67cf3ce89fb8faf5b074ae64df3373b15) comparisons on average, where     H ( p ) = − −  p  log  2   ⁡ ⁡  ( p ) − −  ( 1 − −  p )  log  2   ⁡ ⁡  ( 1 − −  p )   {\displaystyle H(p)=-p\log _{2}(p)-(1-p)\log _{2}(1-p)}  ![{\displaystyle H(p)=-p\log _{2}(p)-(1-p)\log _{2}(1-p)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/945c8d9679ffac5ca4a9fa8bf1b9cf85fff3a8b3) Attribution of LaTeX code: see history of https://en.wikipedia.org/wiki/Binary_entropy_function  is the [binary entropy function](./Binary_entropy_function) and     τ τ    {\displaystyle \tau }  ![{\displaystyle \tau }](https://wikimedia.org/api/rest_v1/media/math/render/svg/38a7dcde9730ef0853809fefc18d88771f95206c) is the probability that the procedure yields the wrong position.[[53]](./Binary_search#cite_note-61)[[54]](./Binary_search#cite_note-pelc1989-62)[[55]](./Binary_search#cite_note-63) The noisy binary search problem can be considered as a case of the [Rényi-Ulam game](./Ulam's_game),[[56]](./Binary_search#cite_note-64) a variant of [Twenty Questions](./Twenty_Questions) where the answers may be wrong.[[57]](./Binary_search#cite_note-65)

 

### Quantum binary search

 

Classical computers are bounded to the worst case of exactly     ⌊ ⌊   log  2   ⁡ ⁡  n + 1 ⌋ ⌋    {\textstyle \lfloor \log _{2}n+1\rfloor }  ![{\textstyle \lfloor \log _{2}n+1\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/2dcdfd1bb04a57761e9372df04573ffcf93b2ed5) iterations when performing binary search. [Quantum algorithms](./Quantum_algorithm) for binary search are still bounded to a proportion of      log  2   ⁡ ⁡  n   {\textstyle \log _{2}n}  ![{\textstyle \log _{2}n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9dcce2c1282e57533d2237877e524f8d35f066bb) queries (representing iterations of the classical procedure), but the constant factor is less than one, providing for a lower time complexity on [quantum computers](./Quantum_computing). Any *exact* quantum binary search procedure—that is, a procedure that always yields the correct result—requires at least       1 π π    ( ln ⁡ ⁡  n − −  1 ) ≈ ≈  0.22  log  2   ⁡ ⁡  n   {\textstyle {\frac {1}{\pi }}(\ln n-1)\approx 0.22\log _{2}n}  ![{\textstyle {\frac {1}{\pi }}(\ln n-1)\approx 0.22\log _{2}n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f55f2452d4b5ac206b7056c14858f386604b96e) queries in the worst case, where     ln   {\textstyle \ln }  ![{\textstyle \ln }](https://wikimedia.org/api/rest_v1/media/math/render/svg/cdd7b7526af7e98c8fe0882db3cc04e7f2b1958e) is the [natural logarithm](./Natural_logarithm).[[58]](./Binary_search#cite_note-66) There is an exact quantum binary search procedure that runs in     4  log  605   ⁡ ⁡  n ≈ ≈  0.433  log  2   ⁡ ⁡  n   {\textstyle 4\log _{605}n\approx 0.433\log _{2}n}  ![{\textstyle 4\log _{605}n\approx 0.433\log _{2}n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/84ec720b48d21c6902cb23c7cf4d5c967372c037) queries in the worst case.[[59]](./Binary_search#cite_note-quantumalgo-67) In comparison, [Grover's algorithm](./Grover's_algorithm) is the optimal quantum algorithm for searching an unordered list of elements, and it requires     O (   n   )   {\displaystyle O({\sqrt {n}})}  ![{\displaystyle O({\sqrt {n}})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5526ab1252c0f682bbe07c0ad67c0f29de5522b) queries.[[60]](./Binary_search#cite_note-68)

 

## History

 

The idea of sorting a list of items to allow for faster searching dates back to antiquity. The earliest known example was the Inakibit-Anu tablet from Babylon dating back to c. 200 BCE. The tablet contained about 500 [sexagesimal](./Sexagesimal) numbers and their [reciprocals](./Multiplicative_inverse) sorted in [lexicographical order](./Lexicographical_order), which made searching for a specific entry easier. In addition, several lists of names that were sorted by their first letter were discovered on the [Aegean Islands](./Aegean_Islands). *[Catholicon](./Catholicon_(1286))*, a Latin dictionary finished in 1286 CE, was the first work to describe rules for sorting words into alphabetical order, as opposed to just the first few letters.[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10)

 

In 1946, [John Mauchly](./John_Mauchly) made the first mention of binary search as part of the [Moore School Lectures](./Moore_School_Lectures), a seminal and foundational college course in computing.[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10) In 1957, [William Wesley Peterson](./W._Wesley_Peterson) published the first method for interpolation search.[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10)[[61]](./Binary_search#cite_note-69) Every published binary search algorithm worked only for arrays whose length is one less than a power of two[[i]](./Binary_search#cite_note-71) until 1960, when [Derrick Henry Lehmer](./Derrick_Henry_Lehmer) published a binary search algorithm that worked on all arrays.[[63]](./Binary_search#cite_note-72) In 1962, Hermann Bottenbruch presented an [ALGOL 60](./ALGOL_60) implementation of binary search that placed the [comparison for equality at the end](./Binary_search#Alternative_procedure), increasing the average number of iterations by one, but reducing to one the number of comparisons per iteration.[[8]](./Binary_search#cite_note-Bottenbruch1962-9) The [uniform binary search](./Binary_search#Uniform_binary_search) was developed by A. K. Chandra of [Stanford University](./Stanford_University) in 1971.[[9]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"-10) In 1986, [Bernard Chazelle](./Bernard_Chazelle) and [Leonidas J. Guibas](./Leonidas_J._Guibas) introduced [fractional cascading](./Fractional_cascading) as a method to solve numerous search problems in [computational geometry](./Computational_geometry).[[50]](./Binary_search#cite_note-ChazelleLiu2001-58)[[64]](./Binary_search#cite_note-73)[[65]](./Binary_search#cite_note-74)

 

## Implementation issues

 

Although the basic idea of binary search is comparatively straightforward, the details can be surprisingly tricky

— [Donald Knuth](./Donald_Knuth)[[2]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Binary_search"-2)

 

When [Jon Bentley](./Jon_Bentley_(computer_scientist)) assigned binary search as a problem in a course for professional programmers, he found that ninety percent failed to provide a correct solution after several hours of working on it, mainly because the incorrect implementations failed to run or returned a wrong answer in rare [edge cases](./Edge_case).[[66]](./Binary_search#cite_note-FOOTNOTEBentley2000§4.1_("The_Challenge_of_Binary_Search")-75) A study published in 1988 shows that accurate code for it is only found in five out of twenty textbooks.[[67]](./Binary_search#cite_note-textbook-76) Furthermore, Bentley's own implementation of binary search, published in his 1986 book *Programming Pearls*, contained an [overflow error](./Integer_overflow) that remained undetected for over twenty years.  The [Java programming language](./Java_(programming_language)) library implementation of binary search had the same overflow bug for more than nine years.[[68]](./Binary_search#cite_note-77)

 

In a practical implementation, the variables used to represent the indices will often be of fixed size (integers), and this can result in an [arithmetic overflow](./Integer_overflow) for very large arrays. If the midpoint of the span is calculated as        L + R  2     {\displaystyle {\frac {L+R}{2}}}  ![{\displaystyle {\frac {L+R}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ed7e052f47e5069015943e2ad3c12363ac155250), then the value of     L + R   {\displaystyle L+R}  ![{\displaystyle L+R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4376f415a5386b515d0103e13244ab901b2ff345) may exceed the range of integers of the [data type](./Data_type) used to store the midpoint, even if     L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) and     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) are within the range. If *    L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8)* and *    R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33)* are nonnegative, this can be avoided by calculating the midpoint as     L +    R − −  L  2     {\displaystyle L+{\frac {R-L}{2}}}  ![{\displaystyle L+{\frac {R-L}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/317132c8914b591c0a0323149b9971033f534eab).[[69]](./Binary_search#cite_note-semisum-78)

 

An infinite loop may occur if the exit conditions for the loop are not defined correctly. Once *    L   {\displaystyle L}  ![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8)* exceeds *    R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33)*, the search has failed and must convey the failure of the search. In addition, the loop must be exited when the target element is found, or in the case of an implementation where this check is moved to the end, checks for whether the search was successful or failed at the end must be in place. Bentley found that most of the programmers who incorrectly implemented binary search made an error in defining the exit conditions.[[8]](./Binary_search#cite_note-Bottenbruch1962-9)[[70]](./Binary_search#cite_note-FOOTNOTEBentley2000§4.4_("Principles")-79)

 

## Library support

 

Many languages' [standard libraries](./Standard_library) include binary search routines:

 
- [C](./C_(programming_language)) provides the [function](./Subroutine) `bsearch()` in its [standard library](./C_standard_library), which is typically implemented via binary search, although the official standard does not require it to do so.[[71]](./Binary_search#cite_note-80)
- [C++](./C++)'s [standard library](./C++_Standard_Library) provides the functions `binary_search()`, `lower_bound()`, `upper_bound()` and `equal_range()`.[[72]](./Binary_search#cite_note-FOOTNOTEStroustrup2013945-81) Using the [C++20](./C++20) `std::ranges` library, it can be applied over a [range](./Range_(computer_programming)) as `std::ranges::binary_search()`.
- [D](./D_(programming_language))'s standard library Phobos, in `std.range` module provides a type `SortedRange` (returned by `sort()` and `assumeSorted()` functions) with methods `contains()`, `equalRange()`, `lowerBound()` and `trisect()`, that use binary search techniques by default for ranges that offer random access.[[73]](./Binary_search#cite_note-82)
- [COBOL](./COBOL) provides the `SEARCH ALL` verb for performing binary searches on COBOL ordered tables.[[74]](./Binary_search#cite_note-83)
- [Go](./Go_(programming_language))'s `sort` standard library package contains the functions `Search`, `SearchInts`, `SearchFloat64s`, and `SearchStrings`, which implement general binary search, as well as specific implementations for searching slices of integers, floating-point numbers, and strings, respectively.[[75]](./Binary_search#cite_note-84)
- [Java](./Java_(programming_language)) offers a set of [overloaded](./Function_overloading) `binarySearch()` static methods in the classes `Arrays` and `Collections` in the standard `java.util` package for performing binary searches on Java arrays and on `List`s, respectively.[[76]](./Binary_search#cite_note-85)[[77]](./Binary_search#cite_note-86)
- [Microsoft](./Microsoft)'s [.NET Framework](./.NET_Framework) 2.0 offers static [generic](./Generic_programming) versions of the binary search algorithm in its collection base classes. An example would be `System.Array`'s method `BinarySearch<T>(T[] array, T value)`.[[78]](./Binary_search#cite_note-87)
- For [Objective-C](./Objective-C), the [Cocoa](./Cocoa_(API)) framework provides the [`NSArray -indexOfObject:inSortedRange:options:usingComparator:`](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/NSArray.html#//apple_ref/occ/instm/NSArray/indexOfObject:inSortedRange:options:usingComparator:) method in Mac OS X 10.6+.[[79]](./Binary_search#cite_note-88) Apple's [Core Foundation](./Core_Foundation) C framework also contains a `CFArrayBSearchValues()` function.[[80]](./Binary_search#cite_note-89)
- [Python](./Python_(programming_language)) provides the `bisect` module that keeps a list in sorted order without having to sort the list after each insertion.[[81]](./Binary_search#cite_note-90)
- [Ruby](./Ruby_(programming_language))'s Array class includes a `bsearch` method with built-in approximate matching.[[82]](./Binary_search#cite_note-FOOTNOTEFitzgerald2015152-91)
- [Rust](./Rust_(programming_language))'s slice primitive provides `binary_search()`, `binary_search_by()`, `binary_search_by_key()`, and `partition_point()`.[[83]](./Binary_search#cite_note-92)

 

## See also

 
- [Bisection method](./Bisection_method) – Algorithm for finding a zero of a function – the same idea used to solve equations in the real numbers
- [Multiplicative binary search](./Multiplicative_binary_search) – Binary search variation with simplified midpoint calculation

 

## Notes and references

  Referencing conventions for this article: use CS1 templates, add book and monograph sources to the Sources section and then cite them using Harvard citations, directly cite other sources. Source titles are in sentence case, but the first letter of proper nouns (e.g., "Bayesian") is capitalized.  

[![](//upload.wikimedia.org/wikipedia/commons/thumb/7/77/Open_Access_logo_PLoS_transparent.svg/20px-Open_Access_logo_PLoS_transparent.svg.png)](./File:Open_Access_logo_PLoS_transparent.svg) This article was submitted to *WikiJournal of Science* for external [academic peer review](./Scholarly_peer_review) in 2018 ([reviewer reports](https://en.wikiversity.org/wiki/Talk:WikiJournal_of_Science/Binary_search_algorithm)). The updated content was reintegrated into the Wikipedia page under a [CC-BY-SA-3.0](//creativecommons.org/licenses/by-sa/3.0/) license ([2019](https://en.wikipedia.org/w/index.php?title=Binary_search&action=history&date-range-to=2019-07-23)). The version of record as reviewed is: Anthony Lin; et al. (2 July 2019). ["Binary search algorithm"](https://upload.wikimedia.org/wikiversity/en/e/ea/Binary_search_algorithm.pdf) (PDF). *[WikiJournal of Science](./WikiJournal_of_Science)*. **2** (1): 5. [doi](./Doi_(identifier)):[10.15347/WJS/2019.005](https://doi.org/10.15347%2FWJS%2F2019.005). [ISSN](./ISSN_(identifier)) [2470-6345](https://search.worldcat.org/issn/2470-6345). [Wikidata](./WDQ_(identifier)) [Q81434400](https://www.wikidata.org/wiki/Q81434400).     

 

### Notes

  
1. [↑](./Binary_search#cite_ref-6) The     O   {\displaystyle O}  ![{\displaystyle O}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d70e1d0d87e2ef1092ea1ffe2923d9933ff18fc) is [Big O notation](./Big_O_notation), and     log   {\displaystyle \log }  ![{\displaystyle \log }](https://wikimedia.org/api/rest_v1/media/math/render/svg/79e4debd0ab1c6ce342d0172a7643733305c37bc) is the [logarithm](./Logarithm). In Big O notation, the base of the logarithm does not matter since every logarithm of a given base is a constant factor of another logarithm of another base. That is,      log  b   ⁡ ⁡  ( n ) =  log  k   ⁡ ⁡  ( n ) ÷ ÷   log  k   ⁡ ⁡  ( b )   {\displaystyle \log _{b}(n)=\log _{k}(n)\div \log _{k}(b)}  ![{\displaystyle \log _{b}(n)=\log _{k}(n)\div \log _{k}(b)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da5102ac7bd4539728fbdf6f8c23f2eb98b553d7), where      log  k   ⁡ ⁡  ( b )   {\displaystyle \log _{k}(b)}  ![{\displaystyle \log _{k}(b)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63e929496cace60c50a8a8eedc92993a8bc30d4b) is a constant.
2. [↑](./Binary_search#cite_ref-18) Any search algorithm based solely on comparisons can be represented using a binary comparison tree. An *internal path* is any path from the root to an existing node. Let     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f) be the *internal path length*, the sum of the lengths of all internal paths. If each element is equally likely to be searched, the average case is     1 +   I n     {\displaystyle 1+{\frac {I}{n}}}  ![{\displaystyle 1+{\frac {I}{n}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad4e4aa70f23c3919bd5d83fb65c67a36e54ab44) or simply one plus the average of all the internal path lengths of the tree. This is because internal paths represent the elements that the search algorithm compares to the target. The lengths of these internal paths represent the number of iterations *after* the root node. Adding the average of these lengths to the one iteration at the root yields the average case. Therefore, to minimize the average number of comparisons, the internal path length     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f) must be minimized. It turns out that the tree for binary search minimizes the internal path length. [Knuth 1998](./Binary_search#CITEREFKnuth1998) proved that the *external path* length (the path length over all nodes where both children are present for each already-existing node) is minimized when the external nodes (the nodes with no children) lie within two consecutive levels of the tree. This also applies to internal paths as internal path length     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f) is linearly related to external path length     E   {\displaystyle E}  ![{\displaystyle E}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4232c9de2ee3eec0a9c0a19b15ab92daa6223f9b). For any tree of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) nodes,     I = E − −  2 n   {\displaystyle I=E-2n}  ![{\displaystyle I=E-2n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/507d78ce4d44e7bc5a4b99a5024e85e821713279). When each subtree has a similar number of nodes, or equivalently the array is divided into halves in each iteration, the external nodes as well as their interior parent nodes lie within two levels. It follows that binary search minimizes the number of average comparisons as its comparison tree has the lowest possible internal path length.[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)
3. [↑](./Binary_search#cite_ref-21) [Knuth 1998](./Binary_search#CITEREFKnuth1998) showed on his [MIX](./MIX_(abstract_machine)) computer model, which Knuth designed as a representation of an ordinary computer, that the average running time of this variation for a successful search is     17.5  log  2   ⁡ ⁡  n + 17   {\textstyle 17.5\log _{2}n+17}  ![{\textstyle 17.5\log _{2}n+17}](https://wikimedia.org/api/rest_v1/media/math/render/svg/61425ee6b9fe1b0cc62bcac7ce5bb6b20cb13c24) units of time compared to     18  log  2   ⁡ ⁡  n − −  16   {\textstyle 18\log _{2}n-16}  ![{\textstyle 18\log _{2}n-16}](https://wikimedia.org/api/rest_v1/media/math/render/svg/290043acdab1e70e7acfb46b10f88624fb1d5a09) units for regular binary search. The time complexity for this variation grows slightly more slowly, but at the cost of higher initial complexity.[[18]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_23"-20)
4. [↑](./Binary_search#cite_ref-31) [Knuth 1998](./Binary_search#CITEREFKnuth1998) performed a formal time performance analysis of both of these search algorithms. On Knuth's [MIX](./MIX_(abstract_machine)) computer, which Knuth designed as a representation of an ordinary computer, binary search takes on average     18 log ⁡ ⁡  n − −  16   {\textstyle 18\log n-16}  ![{\textstyle 18\log n-16}](https://wikimedia.org/api/rest_v1/media/math/render/svg/66d8b8ac66336d407ae0677f6af421c61d286aa3) units of time for a successful search, while linear search with a sentinel node at the end of the list takes     1.75 n + 8.5 − −     n   mod   2   4 n      {\textstyle 1.75n+8.5-{\frac {n{\text{ mod }}2}{4n}}}  ![{\textstyle 1.75n+8.5-{\frac {n{\text{ mod }}2}{4n}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a6ab3a254ea8de00da3703661b13e7edcce24e46) units. Linear search has lower initial complexity because it requires minimal computation, but it quickly outgrows binary search in complexity. On the MIX computer, binary search only outperforms linear search with a sentinel if     n > 44   {\textstyle n>44}  ![{\textstyle n>44}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67217b345947354e08a28826652cd0914113ab88).[[14]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"-15)[[27]](./Binary_search#cite_note-FOOTNOTEKnuth1998Answers_to_Exercises_(§6.2.1)_for_"Exercise_5"-30)
5. [↑](./Binary_search#cite_ref-37) Inserting the values in sorted order or in an alternating lowest-highest key pattern will result in a binary search tree that maximizes the average and worst-case search time.[[32]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.2.2_("Binary_tree_searching"),_subsection_"But_what_about_the_worst_case?"-36)
6. [↑](./Binary_search#cite_ref-43) It is possible to search some hash table implementations in guaranteed constant time.[[37]](./Binary_search#cite_note-FOOTNOTEKnuth1998§6.4_("Hashing"),_subsection_"History"-42)
7. [↑](./Binary_search#cite_ref-49) This is because simply setting all of the bits which the hash functions point to for a specific key can affect queries for other keys which have a common hash location for one or more of the functions.[[42]](./Binary_search#cite_note-cuckoofilter-48)
8. [↑](./Binary_search#cite_ref-50) There exist improvements of the Bloom filter which improve on its complexity or support deletion; for example, the cuckoo filter exploits [cuckoo hashing](./Cuckoo_hashing) to gain these advantages.[[42]](./Binary_search#cite_note-cuckoofilter-48)
9. [↑](./Binary_search#cite_ref-71) That is, arrays of length 1, 3, 7, 15, 31 ...[[62]](./Binary_search#cite_note-70)

 

### Citations

  
1. [↑](./Binary_search#cite_ref-Williams1976_1-0) Williams, Jr., Louis F. (22 April 1976). [*A modification to the half-interval search (binary search) method*](https://dl.acm.org/citation.cfm?doid=503561.503582). Proceedings of the 14th ACM Southeast Conference. ACM. pp. 95–101. [doi](./Doi_(identifier)):[10.1145/503561.503582](https://doi.org/10.1145%2F503561.503582). [Archived](https://web.archive.org/web/20170312215255/http://dl.acm.org/citation.cfm?doid=503561.503582) from the original on 12 March 2017. Retrieved 29 June 2018.
2. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Binary_search"_2-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Binary_search"_2-1) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Binary search".
3. [↑](./Binary_search#cite_ref-FOOTNOTEButterfieldNgondi201646_3-0) [Butterfield & Ngondi 2016](./Binary_search#CITEREFButterfieldNgondi2016), p. 46.
4. [↑](./Binary_search#cite_ref-FOOTNOTECormenLeisersonRivestStein200939_4-0) [Cormen et al. 2009](./Binary_search#CITEREFCormenLeisersonRivestStein2009), p. 39.
5. [↑](./Binary_search#cite_ref-5) [Weisstein, Eric W.](./Eric_W._Weisstein) ["Binary search"](https://mathworld.wolfram.com/BinarySearch.html). *[MathWorld](./MathWorld)*.
6. [1](./Binary_search#cite_ref-FloresMadpis1971_7-0) [2](./Binary_search#cite_ref-FloresMadpis1971_7-1) Flores, Ivan; Madpis, George (1 September 1971). ["Average binary search length for dense ordered lists"](https://doi.org/10.1145%2F362663.362752). *[Communications of the ACM](./Communications_of_the_ACM)*. **14** (9): 602–603. [doi](./Doi_(identifier)):[10.1145/362663.362752](https://doi.org/10.1145%2F362663.362752). [ISSN](./ISSN_(identifier)) [0001-0782](https://search.worldcat.org/issn/0001-0782). [S2CID](./S2CID_(identifier)) [43325465](https://api.semanticscholar.org/CorpusID:43325465).
7. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"_8-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"_8-1) [3](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_B"_8-2) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Algorithm B".
8. [1](./Binary_search#cite_ref-Bottenbruch1962_9-0) [2](./Binary_search#cite_ref-Bottenbruch1962_9-1) [3](./Binary_search#cite_ref-Bottenbruch1962_9-2) [4](./Binary_search#cite_ref-Bottenbruch1962_9-3) Bottenbruch, Hermann (1 April 1962). ["Structure and use of ALGOL 60"](https://doi.org/10.1145%2F321119.321120). *[Journal of the ACM](./Journal_of_the_ACM)*. **9** (2): 161–221. [doi](./Doi_(identifier)):[10.1145/321119.321120](https://doi.org/10.1145%2F321119.321120). [ISSN](./ISSN_(identifier)) [0004-5411](https://search.worldcat.org/issn/0004-5411). [S2CID](./S2CID_(identifier)) [13406983](https://api.semanticscholar.org/CorpusID:13406983). Procedure is described at p. 214 (§43), titled "Program for Binary Search".
9. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-1) [3](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-2) [4](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-3) [5](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-4) [6](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"History_and_bibliography"_10-5) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "History and bibliography".
10. [1](./Binary_search#cite_ref-FOOTNOTEKasaharaMorishita20068–9_11-0) [2](./Binary_search#cite_ref-FOOTNOTEKasaharaMorishita20068–9_11-1) [Kasahara & Morishita 2006](./Binary_search#CITEREFKasaharaMorishita2006), pp. 8–9.
11. [1](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"_12-0) [2](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"_12-1) [3](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Rank_and_selection"_12-2) [Sedgewick & Wayne 2011](./Binary_search#CITEREFSedgewickWayne2011), §3.1, subsection "Rank and selection".
12. [1](./Binary_search#cite_ref-FOOTNOTEGoldmanGoldman2008461–463_13-0) [2](./Binary_search#cite_ref-FOOTNOTEGoldmanGoldman2008461–463_13-1) [3](./Binary_search#cite_ref-FOOTNOTEGoldmanGoldman2008461–463_13-2) [Goldman & Goldman 2008](./Binary_search#CITEREFGoldmanGoldman2008), pp. 461–463.
13. [↑](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.1,_subsection_"Range_queries"_14-0) [Sedgewick & Wayne 2011](./Binary_search#CITEREFSedgewickWayne2011), §3.1, subsection "Range queries".
14. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-1) [3](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-2) [4](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-3) [5](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-4) [6](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-5) [7](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-6) [8](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-7) [9](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-8) [10](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-9) [11](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-10) [12](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Further_analysis_of_binary_search"_15-11) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Further analysis of binary search".
15. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_"Theorem_B"_16-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), "Theorem B".
16. [↑](./Binary_search#cite_ref-FOOTNOTEChang2003169_17-0) [Chang 2003](./Binary_search#CITEREFChang2003), p. 169.
17. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")_19-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")_19-1) [3](./Binary_search#cite_ref-FOOTNOTEKnuth1997§2.3.4.5_("Path_length")_19-2) [Knuth 1997](./Binary_search#CITEREFKnuth1997), §2.3.4.5 ("Path length").
18. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_23"_20-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_23"_20-1) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Exercise 23".
19. [↑](./Binary_search#cite_ref-22) Rolfe, Timothy J. (1997). ["Analytic derivation of comparisons in binary search"](https://doi.org/10.1145%2F289251.289255). *ACM SIGNUM Newsletter*. **32** (4): 15–19. [doi](./Doi_(identifier)):[10.1145/289251.289255](https://doi.org/10.1145%2F289251.289255). [S2CID](./S2CID_(identifier)) [23752485](https://api.semanticscholar.org/CorpusID:23752485).
20. [↑](./Binary_search#cite_ref-Herf_2001_23-0) Herf, Michael (December 2001). ["radix tricks"](http://stereopsis.com/radix.html). *stereopsis: graphics*.
21. [↑](./Binary_search#cite_ref-rust_total_cmp_24-0) ["Implement total_cmp for f32, f64 by golddranks · Pull Request #72568 · rust-lang/rust"](https://github.com/rust-lang/rust/pull/72568). *GitHub*. – contains relevant quotations from IEEE 754-2008 and -2019. Contains a type-pun implementation and explanation.
22. [↑](./Binary_search#cite_ref-25) ["Binary search *eliminates* branch mispredictions - Paul Khuong: some Lisp"](https://pvk.ca/Blog/2012/07/03/binary-search-star-eliminates-star-branch-mispredictions/). *pvk.ca*.
23. [↑](./Binary_search#cite_ref-26) Khuong, Paul-Virak; [Morin, Pat](./Pat_Morin) (2017). "Array Layouts for Comparison-Based Searching". *Journal of Experimental Algorithmics*. **22**. Article 1.3. [arXiv](./ArXiv_(identifier)):[1509.05053](https://arxiv.org/abs/1509.05053). [doi](./Doi_(identifier)):[10.1145/3053370](https://doi.org/10.1145%2F3053370). [S2CID](./S2CID_(identifier)) [23752485](https://api.semanticscholar.org/CorpusID:23752485).
24. [↑](./Binary_search#cite_ref-27) ["Binary search is a pathological case for caches - Paul Khuong: some Lisp"](https://pvk.ca/Blog/2012/07/30/binary-search-is-a-pathological-case-for-caches/). *pvk.ca*.
25. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1997§2.2.2_("Sequential_Allocation")_28-0) [Knuth 1997](./Binary_search#CITEREFKnuth1997), §2.2.2 ("Sequential Allocation").
26. [1](./Binary_search#cite_ref-pred_29-0) [2](./Binary_search#cite_ref-pred_29-1) [3](./Binary_search#cite_ref-pred_29-2) [4](./Binary_search#cite_ref-pred_29-3) Beame, Paul; [Fich, Faith E.](./Faith_Ellen) (2001). ["Optimal bounds for the predecessor problem and related problems"](https://doi.org/10.1006%2Fjcss.2002.1822). *[Journal of Computer and System Sciences](./Journal_of_Computer_and_System_Sciences)*. **65** (1): 38–72. [doi](./Doi_(identifier)):[10.1006/jcss.2002.1822](https://doi.org/10.1006%2Fjcss.2002.1822).
27. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998Answers_to_Exercises_(§6.2.1)_for_"Exercise_5"_30-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), Answers to Exercises (§6.2.1) for "Exercise 5".
28. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table")_32-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table").
29. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§5.3.1_("Minimum-Comparison_sorting")_33-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §5.3.1 ("Minimum-Comparison sorting").
30. [↑](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.2_("Ordered_symbol_tables")_34-0) [Sedgewick & Wayne 2011](./Binary_search#CITEREFSedgewickWayne2011), §3.2 ("Ordered symbol tables").
31. [↑](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.2_("Binary_Search_Trees"),_subsection_"Order-based_methods_and_deletion"_35-0) [Sedgewick & Wayne 2011](./Binary_search#CITEREFSedgewickWayne2011), §3.2 ("Binary Search Trees"), subsection "Order-based methods and deletion".
32. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.2_("Binary_tree_searching"),_subsection_"But_what_about_the_worst_case?"_36-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.2 ("Binary tree searching"), subsection "But what about the worst case?".
33. [↑](./Binary_search#cite_ref-FOOTNOTESedgewickWayne2011§3.5_("Applications"),_"Which_symbol-table_implementation_should_I_use?"_38-0) [Sedgewick & Wayne 2011](./Binary_search#CITEREFSedgewickWayne2011), §3.5 ("Applications"), "Which symbol-table implementation should I use?".
34. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§5.4.9_("Disks_and_Drums")_39-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §5.4.9 ("Disks and Drums").
35. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.4_("Multiway_trees")_40-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.4 ("Multiway trees").
36. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.4_("Hashing")_41-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.4 ("Hashing").
37. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.4_("Hashing"),_subsection_"History"_42-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.4 ("Hashing"), subsection "History".
38. [↑](./Binary_search#cite_ref-44) Dietzfelbinger, Martin; [Karlin, Anna](./Anna_Karlin); [Mehlhorn, Kurt](./Kurt_Mehlhorn); Meyer auf der Heide, Friedhelm; Rohnert, Hans; [Tarjan, Robert E.](./Robert_Tarjan) (August 1994). "Dynamic perfect hashing: upper and lower bounds". *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **23** (4): 738–761. [doi](./Doi_(identifier)):[10.1137/S0097539791194094](https://doi.org/10.1137%2FS0097539791194094).
39. [↑](./Binary_search#cite_ref-45) Morin, Pat. ["Hash tables"](http://cglab.ca/~morin/teaching/5408/notes/hashing.pdf) (PDF). p. 1. [Archived](https://ghostarchive.org/archive/20221009/http://cglab.ca/~morin/teaching/5408/notes/hashing.pdf) (PDF) from the original on 9 October 2022. Retrieved 28 March 2016.
40. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth2011§7.1.3_("Bitwise_Tricks_and_Techniques")_46-0) [Knuth 2011](./Binary_search#CITEREFKnuth2011), §7.1.3 ("Bitwise Tricks and Techniques").
41. [1](./Binary_search#cite_ref-judyarray_47-0) [2](./Binary_search#cite_ref-judyarray_47-1) Silverstein, Alan, [*Judy IV shop manual*](https://judy.sourceforge.net/doc/shop_interm.pdf) (PDF), [Hewlett-Packard](./Hewlett-Packard), pp. 80–81, [archived](https://ghostarchive.org/archive/20221009/http://judy.sourceforge.net/doc/shop_interm.pdf) (PDF) from the original on 9 October 2022
42. [1](./Binary_search#cite_ref-cuckoofilter_48-0) [2](./Binary_search#cite_ref-cuckoofilter_48-1) Fan, Bin; Andersen, Dave G.; Kaminsky, Michael; Mitzenmacher, Michael D. (2014). *Cuckoo filter: practically better than Bloom*. Proceedings of the 10th ACM International on Conference on Emerging Networking Experiments and Technologies. pp. 75–88. [doi](./Doi_(identifier)):[10.1145/2674005.2674994](https://doi.org/10.1145%2F2674005.2674994).
43. [↑](./Binary_search#cite_ref-51) Bloom, Burton H. (1970). "Space/time trade-offs in hash coding with allowable errors". *[Communications of the ACM](./Communications_of_the_ACM)*. **13** (7): 422–426. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.641.9096](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.641.9096). [doi](./Doi_(identifier)):[10.1145/362686.362692](https://doi.org/10.1145%2F362686.362692). [S2CID](./S2CID_(identifier)) [7931252](https://api.semanticscholar.org/CorpusID:7931252).
44. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"An_important_variation"_52-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "An important variation".
45. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Algorithm_U"_53-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Algorithm U".
46. [↑](./Binary_search#cite_ref-FOOTNOTEMoffatTurpin200233_54-0) [Moffat & Turpin 2002](./Binary_search#CITEREFMoffatTurpin2002), p. 33.
47. [1](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"_55-0) [2](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"_55-1) [3](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Interpolation_search"_55-2) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Interpolation search".
48. [↑](./Binary_search#cite_ref-FOOTNOTEKnuth1998§6.2.1_("Searching_an_ordered_table"),_subsection_"Exercise_22"_56-0) [Knuth 1998](./Binary_search#CITEREFKnuth1998), §6.2.1 ("Searching an ordered table"), subsection "Exercise 22".
49. [↑](./Binary_search#cite_ref-57) Perl, Yehoshua; Itai, Alon; Avni, Haim (1978). ["Interpolation search—a log log *n* search"](https://doi.org/10.1145%2F359545.359557). *[Communications of the ACM](./Communications_of_the_ACM)*. **21** (7): 550–553. [doi](./Doi_(identifier)):[10.1145/359545.359557](https://doi.org/10.1145%2F359545.359557). [S2CID](./S2CID_(identifier)) [11089655](https://api.semanticscholar.org/CorpusID:11089655).
50. [1](./Binary_search#cite_ref-ChazelleLiu2001_58-0) [2](./Binary_search#cite_ref-ChazelleLiu2001_58-1) [3](./Binary_search#cite_ref-ChazelleLiu2001_58-2) [Chazelle, Bernard](./Bernard_Chazelle); Liu, Ding (6 July 2001). [*Lower bounds for intersection searching and fractional cascading in higher dimension*](https://dl.acm.org/citation.cfm?doid=380752.380818). 33rd [ACM Symposium on Theory of Computing](./Symposium_on_Theory_of_Computing). ACM. pp. 322–329. [doi](./Doi_(identifier)):[10.1145/380752.380818](https://doi.org/10.1145%2F380752.380818). [ISBN](./ISBN_(identifier)) [978-1-58113-349-3](./Special:BookSources/978-1-58113-349-3). Retrieved 30 June 2018.
51. [↑](./Binary_search#cite_ref-ChazelleLiu2004_59-0) [Chazelle, Bernard](./Bernard_Chazelle); Liu, Ding (1 March 2004). ["Lower bounds for intersection searching and fractional cascading in higher dimension"](http://www.cs.princeton.edu/~chazelle/pubs/FClowerbounds.pdf) (PDF). *Journal of Computer and System Sciences*. **68** (2): 269–284. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.298.7772](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.298.7772). [doi](./Doi_(identifier)):[10.1016/j.jcss.2003.07.003](https://doi.org/10.1016%2Fj.jcss.2003.07.003). [ISSN](./ISSN_(identifier)) [0022-0000](https://search.worldcat.org/issn/0022-0000). [Archived](https://ghostarchive.org/archive/20221009/http://www.cs.princeton.edu/~chazelle/pubs/FClowerbounds.pdf) (PDF) from the original on 9 October 2022. Retrieved 30 June 2018.
52. [↑](./Binary_search#cite_ref-60) Emamjomeh-Zadeh, Ehsan; Kempe, David; Singhal, Vikrant (2016). *Deterministic and probabilistic binary search in graphs*. 48th [ACM Symposium on Theory of Computing](./Symposium_on_Theory_of_Computing). pp. 519–532. [arXiv](./ArXiv_(identifier)):[1503.00805](https://arxiv.org/abs/1503.00805). [doi](./Doi_(identifier)):[10.1145/2897518.2897656](https://doi.org/10.1145%2F2897518.2897656).
53. [↑](./Binary_search#cite_ref-61) Ben-Or, Michael; Hassidim, Avinatan (2008). ["The Bayesian learner is optimal for noisy binary search (and pretty good for quantum as well)"](http://www2.lns.mit.edu/~avinatan/research/search-full.pdf) (PDF). *49th [Symposium on Foundations of Computer Science](./Annual_IEEE_Symposium_on_Foundations_of_Computer_Science)*. pp. 221–230. [doi](./Doi_(identifier)):[10.1109/FOCS.2008.58](https://doi.org/10.1109%2FFOCS.2008.58). [ISBN](./ISBN_(identifier)) [978-0-7695-3436-7](./Special:BookSources/978-0-7695-3436-7). [Archived](https://ghostarchive.org/archive/20221009/http://www2.lns.mit.edu/~avinatan/research/search-full.pdf) (PDF) from the original on 9 October 2022.
54. [↑](./Binary_search#cite_ref-pelc1989_62-0) Pelc, Andrzej (1989). ["Searching with known error probability"](https://doi.org/10.1016%2F0304-3975%2889%2990077-7). *Theoretical Computer Science*. **63** (2): 185–202. [doi](./Doi_(identifier)):[10.1016/0304-3975(89)90077-7](https://doi.org/10.1016%2F0304-3975%2889%2990077-7).
55. [↑](./Binary_search#cite_ref-63) [Rivest, Ronald L.](./Ronald_Rivest); [Meyer, Albert R.](./Albert_R._Meyer); [Kleitman, Daniel J.](./Daniel_Kleitman); Winklmann, K. *Coping with errors in binary search procedures*. 10th [ACM Symposium on Theory of Computing](./Symposium_on_Theory_of_Computing). [doi](./Doi_(identifier)):[10.1145/800133.804351](https://doi.org/10.1145%2F800133.804351).
56. [↑](./Binary_search#cite_ref-64) Pelc, Andrzej (2002). ["Searching games with errors—fifty years of coping with liars"](https://doi.org/10.1016%2FS0304-3975%2801%2900303-6). *Theoretical Computer Science*. **270** (1–2): 71–109. [doi](./Doi_(identifier)):[10.1016/S0304-3975(01)00303-6](https://doi.org/10.1016%2FS0304-3975%2801%2900303-6).
57. [↑](./Binary_search#cite_ref-65) Rényi, Alfréd (1961). "On a problem in information theory". *Magyar Tudományos Akadémia Matematikai Kutató Intézetének Közleményei*. **6**: 515–516. [MR](./MR_(identifier)) [0143666](https://mathscinet.ams.org/mathscinet-getitem?mr=0143666).
58. [↑](./Binary_search#cite_ref-66) Høyer, Peter; Neerbek, Jan; Shi, Yaoyun (2002). "Quantum complexities of ordered searching, sorting, and element distinctness". *[Algorithmica](./Algorithmica)*. **34** (4): 429–448. [arXiv](./ArXiv_(identifier)):[quant-ph/0102078](https://arxiv.org/abs/quant-ph/0102078). [doi](./Doi_(identifier)):[10.1007/s00453-002-0976-3](https://doi.org/10.1007%2Fs00453-002-0976-3). [S2CID](./S2CID_(identifier)) [13717616](https://api.semanticscholar.org/CorpusID:13717616).
59. [↑](./Binary_search#cite_ref-quantumalgo_67-0) Childs, Andrew M.; Landahl, Andrew J.; Parrilo, Pablo A. (2007). "Quantum algorithms for the ordered search problem via semidefinite programming". *Physical Review A*. **75** (3). 032335. [arXiv](./ArXiv_(identifier)):[quant-ph/0608161](https://arxiv.org/abs/quant-ph/0608161). [Bibcode](./Bibcode_(identifier)):[2007PhRvA..75c2335C](https://ui.adsabs.harvard.edu/abs/2007PhRvA..75c2335C). [doi](./Doi_(identifier)):[10.1103/PhysRevA.75.032335](https://doi.org/10.1103%2FPhysRevA.75.032335). [S2CID](./S2CID_(identifier)) [41539957](https://api.semanticscholar.org/CorpusID:41539957).
60. [↑](./Binary_search#cite_ref-68) [Grover, Lov K.](./Lov_Grover) (1996). *A fast quantum mechanical algorithm for database search*. 28th [ACM Symposium on Theory of Computing](./Symposium_on_Theory_of_Computing). Philadelphia, PA. pp. 212–219. [arXiv](./ArXiv_(identifier)):[quant-ph/9605043](https://arxiv.org/abs/quant-ph/9605043). [doi](./Doi_(identifier)):[10.1145/237814.237866](https://doi.org/10.1145%2F237814.237866).
61. [↑](./Binary_search#cite_ref-69) [Peterson, William Wesley](./W._Wesley_Peterson) (1957). "Addressing for random-access storage". *IBM Journal of Research and Development*. **1** (2): 130–146. [doi](./Doi_(identifier)):[10.1147/rd.12.0130](https://doi.org/10.1147%2Frd.12.0130).
62. [↑](./Binary_search#cite_ref-70) "2*n*−1". [OEIS](./On-Line_Encyclopedia_of_Integer_Sequences) [A000225](http://oeis.org/A000225) [Archived](https://web.archive.org/web/20160608084228/http://oeis.org/A000225) 8 June 2016 at the [Wayback Machine](./Wayback_Machine).  Retrieved 7 May 2016.
63. [↑](./Binary_search#cite_ref-72) Lehmer, Derrick (1960). "Teaching combinatorial tricks to a computer". *Combinatorial Analysis*. Proceedings of Symposia in Applied Mathematics. Vol. 10. pp. 180–181. [doi](./Doi_(identifier)):[10.1090/psapm/010/0113289](https://doi.org/10.1090%2Fpsapm%2F010%2F0113289). [ISBN](./ISBN_(identifier)) [9780821813102](./Special:BookSources/9780821813102). [MR](./MR_(identifier)) [0113289](https://mathscinet.ams.org/mathscinet-getitem?mr=0113289). `{{cite book}}`: ISBN / Date incompatibility ([help](./Help:CS1_errors#invalid_isbn_date))
64. [↑](./Binary_search#cite_ref-73) [Chazelle, Bernard](./Bernard_Chazelle); [Guibas, Leonidas J.](./Leonidas_J._Guibas) (1986). ["Fractional cascading: I. A data structuring technique"](http://www.cs.princeton.edu/~chazelle/pubs/FractionalCascading1.pdf) (PDF). *[Algorithmica](./Algorithmica)*. **1** (1–4): 133–162. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.117.8349](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.117.8349). [doi](./Doi_(identifier)):[10.1007/BF01840440](https://doi.org/10.1007%2FBF01840440). [S2CID](./S2CID_(identifier)) [12745042](https://api.semanticscholar.org/CorpusID:12745042).
65. [↑](./Binary_search#cite_ref-74) [Chazelle, Bernard](./Bernard_Chazelle); [Guibas, Leonidas J.](./Leonidas_J._Guibas) (1986), ["Fractional cascading: II. Applications"](http://www.cs.princeton.edu/~chazelle/pubs/FractionalCascading2.pdf) (PDF), *[Algorithmica](./Algorithmica)*, **1** (1–4): 163–191, [doi](./Doi_(identifier)):[10.1007/BF01840441](https://doi.org/10.1007%2FBF01840441), [S2CID](./S2CID_(identifier)) [11232235](https://api.semanticscholar.org/CorpusID:11232235)
66. [↑](./Binary_search#cite_ref-FOOTNOTEBentley2000§4.1_("The_Challenge_of_Binary_Search")_75-0) [Bentley 2000](./Binary_search#CITEREFBentley2000), §4.1 ("The Challenge of Binary Search").
67. [↑](./Binary_search#cite_ref-textbook_76-0) [Pattis, Richard E.](./Richard_E._Pattis) (1988). "Textbook errors in binary searching". *SIGCSE Bulletin*. **20**: 190–194. [doi](./Doi_(identifier)):[10.1145/52965.53012](https://doi.org/10.1145%2F52965.53012).
68. [↑](./Binary_search#cite_ref-77) [Bloch, Joshua](./Joshua_Bloch) (2 June 2006). ["Extra, extra – read all about it: nearly all binary searches and mergesorts are broken"](http://googleresearch.blogspot.com/2006/06/extra-extra-read-all-about-it-nearly.html). *Google Research Blog*. [Archived](https://web.archive.org/web/20160401140544/http://googleresearch.blogspot.com/2006/06/extra-extra-read-all-about-it-nearly.html) from the original on 1 April 2016. Retrieved 21 April 2016.
69. [↑](./Binary_search#cite_ref-semisum_78-0) Ruggieri, Salvatore (2003). ["On computing the semi-sum of two integers"](http://www.di.unipi.it/~ruggieri/Papers/semisum.pdf) (PDF). *[Information Processing Letters](./Information_Processing_Letters)*. **87** (2): 67–71. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.13.5631](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.13.5631). [doi](./Doi_(identifier)):[10.1016/S0020-0190(03)00263-1](https://doi.org/10.1016%2FS0020-0190%2803%2900263-1). [Archived](https://web.archive.org/web/20060703173514/http://www.di.unipi.it/~ruggieri/Papers/semisum.pdf) (PDF) from the original on 3 July 2006. Retrieved 19 March 2016.
70. [↑](./Binary_search#cite_ref-FOOTNOTEBentley2000§4.4_("Principles")_79-0) [Bentley 2000](./Binary_search#CITEREFBentley2000), §4.4 ("Principles").
71. [↑](./Binary_search#cite_ref-80) ["bsearch – binary search a sorted table"](http://pubs.opengroup.org/onlinepubs/9699919799/functions/bsearch.html). *The Open Group Base Specifications* (7th ed.). [The Open Group](./The_Open_Group). 2013. [Archived](https://web.archive.org/web/20160321211605/http://pubs.opengroup.org/onlinepubs/9699919799/functions/bsearch.html) from the original on 21 March 2016. Retrieved 28 March 2016.
72. [↑](./Binary_search#cite_ref-FOOTNOTEStroustrup2013945_81-0) [Stroustrup 2013](./Binary_search#CITEREFStroustrup2013), p. 945.
73. [↑](./Binary_search#cite_ref-82) ["std.range - D Programming Language"](https://dlang.org/phobos/std_range.html#SortedRange). *dlang.org*. Retrieved 29 April 2020.
74. [↑](./Binary_search#cite_ref-83) [Unisys](./Unisys) (2012), *COBOL ANSI-85 programming reference manual*, vol. 1, pp. 598–601
75. [↑](./Binary_search#cite_ref-84) ["Package sort"](https://golang.org/pkg/sort/). *The Go Programming Language*. [Archived](https://web.archive.org/web/20160425055919/https://golang.org/pkg/sort/) from the original on 25 April 2016. Retrieved 28 April 2016.
76. [↑](./Binary_search#cite_ref-85) ["java.util.Arrays"](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html). *Java Platform Standard Edition 8 Documentation*. [Oracle Corporation](./Oracle_Corporation). [Archived](https://web.archive.org/web/20160429064301/http://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html) from the original on 29 April 2016. Retrieved 1 May 2016.
77. [↑](./Binary_search#cite_ref-86) ["java.util.Collections"](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html). *Java Platform Standard Edition 8 Documentation*. [Oracle Corporation](./Oracle_Corporation). [Archived](https://web.archive.org/web/20160423092424/https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html) from the original on 23 April 2016. Retrieved 1 May 2016.
78. [↑](./Binary_search#cite_ref-87) ["List<T>.BinarySearch method (T)"](https://msdn.microsoft.com/en-us/library/w4e7fxsh%28v=vs.110%29.aspx). *Microsoft Developer Network*. [Archived](https://web.archive.org/web/20160507141014/https://msdn.microsoft.com/en-us/library/w4e7fxsh%28v=vs.110%29.aspx) from the original on 7 May 2016. Retrieved 10 April 2016.
79. [↑](./Binary_search#cite_ref-88) ["NSArray"](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/index.html#//apple_ref/occ/instm/NSArray/indexOfObject:inSortedRange:options:usingComparator:). *Mac Developer Library*. [Apple Inc.](./Apple_Inc.) [Archived](https://web.archive.org/web/20160417163718/https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/index.html#//apple_ref/occ/instm/NSArray/indexOfObject:inSortedRange:options:usingComparator:) from the original on 17 April 2016. Retrieved 1 May 2016.
80. [↑](./Binary_search#cite_ref-89) ["CFArray"](https://developer.apple.com/library/mac/documentation/CoreFoundation/Reference/CFArrayRef/index.html#//apple_ref/c/func/CFArrayBSearchValues). *Mac Developer Library*. [Apple Inc.](./Apple_Inc.) [Archived](https://web.archive.org/web/20160420193823/https://developer.apple.com/library/mac/documentation/CoreFoundation/Reference/CFArrayRef/index.html#//apple_ref/c/func/CFArrayBSearchValues) from the original on 20 April 2016. Retrieved 1 May 2016.
81. [↑](./Binary_search#cite_ref-90) ["8.6. bisect — Array bisection algorithm"](https://docs.python.org/3.6/library/bisect.html#module-bisect). *The Python Standard Library*. Python Software Foundation. [Archived](https://web.archive.org/web/20180325105932/https://docs.python.org/3.6/library/bisect.html#module-bisect) from the original on 25 March 2018. Retrieved 26 March 2018.
82. [↑](./Binary_search#cite_ref-FOOTNOTEFitzgerald2015152_91-0) [Fitzgerald 2015](./Binary_search#CITEREFFitzgerald2015), p. 152.
83. [↑](./Binary_search#cite_ref-92) ["Primitive Type `slice`"](https://doc.rust-lang.org/std/primitive.slice.html). *The Rust Standard Library*. [The Rust Foundation](./The_Rust_Foundation?action=edit&redlink=1). 2024. Retrieved 25 May 2024.

 

### Sources

  
- [Bentley, Jon](./Jon_Bentley_(computer_scientist)) (2000). *Programming pearls* (2nd ed.). [Addison-Wesley](./Addison-Wesley). [ISBN](./ISBN_(identifier)) [978-0-201-65788-3](./Special:BookSources/978-0-201-65788-3).
- Butterfield, Andrew; Ngondi, Gerard E. (2016). *A dictionary of computer science* (7th ed.). Oxford, UK: [Oxford University Press](./Oxford_University_Press). [ISBN](./ISBN_(identifier)) [978-0-19-968897-5](./Special:BookSources/978-0-19-968897-5).
- Chang, Shi-Kuo (2003). *Data structures and algorithms*. Software Engineering and Knowledge Engineering. Vol. 13. Singapore: [World Scientific](./World_Scientific). [ISBN](./ISBN_(identifier)) [978-981-238-348-8](./Special:BookSources/978-981-238-348-8).
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009). [*Introduction to algorithms*](./Introduction_to_Algorithms) (3rd ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8).
- Fitzgerald, Michael (2015). *Ruby pocket reference*. Sebastopol, California: [O'Reilly Media](./O'Reilly_Media). [ISBN](./ISBN_(identifier)) [978-1-4919-2601-7](./Special:BookSources/978-1-4919-2601-7).
- [Goldman, Sally A.](./Sally_Goldman); Goldman, Kenneth J. (2008). *A practical guide to data structures and algorithms using Java*. Boca Raton, Florida: [CRC Press](./CRC_Press). [ISBN](./ISBN_(identifier)) [978-1-58488-455-2](./Special:BookSources/978-1-58488-455-2).
- Kasahara, Masahiro; Morishita, Shinichi (2006). *Large-scale genome sequence processing*. London, UK: Imperial College Press. [ISBN](./ISBN_(identifier)) [978-1-86094-635-6](./Special:BookSources/978-1-86094-635-6).
- [Knuth, Donald](./Donald_Knuth) (1997). *Fundamental algorithms*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 1 (3rd ed.). Reading, MA: Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-201-89683-1](./Special:BookSources/978-0-201-89683-1).
- [Knuth, Donald](./Donald_Knuth) (1998). *Sorting and searching*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 3 (2nd ed.). Reading, MA: Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-201-89685-5](./Special:BookSources/978-0-201-89685-5).
- [Knuth, Donald](./Donald_Knuth) (2011). *Combinatorial algorithms*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 4A (1st ed.). Reading, MA: Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-201-03804-0](./Special:BookSources/978-0-201-03804-0).
- Moffat, Alistair; Turpin, Andrew (2002). *Compression and coding algorithms*. Hamburg, Germany: Kluwer Academic Publishers. [doi](./Doi_(identifier)):[10.1007/978-1-4615-0935-6](https://doi.org/10.1007%2F978-1-4615-0935-6). [ISBN](./ISBN_(identifier)) [978-0-7923-7668-2](./Special:BookSources/978-0-7923-7668-2).
- [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Wayne, Kevin (2011). [*Algorithms*](http://algs4.cs.princeton.edu/home/) (4th ed.). Upper Saddle River, New Jersey: Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-321-57351-3](./Special:BookSources/978-0-321-57351-3). Condensed web version [![Open access icon](//upload.wikimedia.org/wikipedia/commons/thumb/7/77/Open_Access_logo_PLoS_transparent.svg/20px-Open_Access_logo_PLoS_transparent.svg.png)](./Open_access); book version [![Closed access icon](//upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Closed_Access_logo_transparent.svg/20px-Closed_Access_logo_transparent.svg.png)](./Paywall).
- [Stroustrup, Bjarne](./Bjarne_Stroustrup) (2013). *The C++ programming language* (4th ed.). Upper Saddle River, New Jersey: Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-321-56384-2](./Special:BookSources/978-0-321-56384-2).

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm implementation](https://en.wikibooks.org/wiki/Algorithm%20implementation)* has a page on the topic of: ***[Binary search](https://en.wikibooks.org/wiki/Algorithm%20implementation/Search/Binary%20search)***  
- [NIST Dictionary of Algorithms and Data Structures: binary search](https://web.archive.org/web/20161104005739/https://xlinux.nist.gov/dads/HTML/binarySearch.html)
- [Comparisons and benchmarks of a variety of binary search implementations in C](https://sites.google.com/site/binarysearchcube/binary-search) [Archived](https://web.archive.org/web/20190925012527/https://sites.google.com/site/binarysearchcube/binary-search) 25 September 2019 at the [Wayback Machine](./Wayback_Machine)

 
| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |