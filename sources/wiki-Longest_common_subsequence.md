---
source: https://en.wikipedia.org/wiki/Longest_common_subsequence
fetched: 2026-06-19
---

Algorithmic problem on pairs of sequences Not to be confused with [Longest common substring](./Longest_common_substring). [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/25/Nubio_Diff_Screenshot3.png/250px-Nubio_Diff_Screenshot3.png)](./File:Nubio_Diff_Screenshot3.png)Comparison of two revisions of an example file, based on their longest common subsequence  (black) 

A **longest common subsequence** (**LCS**) is the longest [subsequence](./Subsequence) common to all sequences in a set of sequences (often just two sequences). It differs from the [longest common substring](./Longest_common_substring): unlike substrings, subsequences are not required to occupy consecutive positions within the original sequences. The problem of computing longest common subsequences is a classic [computer science](./Computer_science) problem. Because it is [polynomial](./Polynomial-time_algorithm) and has an efficient algorithm to solve it, it is employed to [compare data](./Data_comparison) and [merge changes to files](./Merge_(revision_control)) in programs such as the [`diff` utility](./Diff_utility) and [revision control systems](./Revision_control) such as [Git](./Git_(software)). It has similar applications in [computational linguistics](./Computational_linguistics) and [bioinformatics](./Bioinformatics).

  todo: add definition and example  

For example, consider the sequences (ABCD) and (ACBAD). They have five length-2 common subsequences: (AB), (AC), (AD), (BD), and (CD); two length-3 common subsequences: (ABD) and (ACD); and no longer common subsequences. So (ABD) and (ACD) are their longest common subsequences.

 

## Complexity

 

For the general case of an arbitrary number of input sequences, the problem is [NP-hard](./NP-hard).[[1]](./Longest_common_subsequence#cite_note-1) When the number of sequences is constant, the problem is solvable in polynomial time by [dynamic programming](./Dynamic_programming).

 

Given     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) sequences of lengths      n  1   , . . . ,  n  N     {\displaystyle n_{1},...,n_{N}}  ![{\displaystyle n_{1},...,n_{N}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec085dde9be59e50d0722ed02d67dd321f244374), a naive search would test each of the      2   n  1       {\displaystyle 2^{n_{1}}}  ![{\displaystyle 2^{n_{1}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fcd2a5b23a5eed70ef3cfe60dba878ab9943f76b) subsequences of the first sequence to determine whether they are also subsequences of the remaining sequences; each subsequence may be tested in time linear in the lengths of the remaining sequences, so the time for this algorithm would be

     O  (   2   n  1      ∑ ∑   i > 1    n  i    )  .   {\displaystyle O\left(2^{n_{1}}\sum _{i>1}n_{i}\right).}  ![{\displaystyle O\left(2^{n_{1}}\sum _{i>1}n_{i}\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/feb8e3bedc5867dd897fed772931631f768f7d7e) 

For the case of two sequences of *n* and *m* elements, the running time of the dynamic programming approach is [O](./Big_O_notation)(*n* × *m*).[[2]](./Longest_common_subsequence#cite_note-2) For an arbitrary number of input sequences, the dynamic programming approach gives a solution in

     O  (  N  ∏ ∏   i = 1   N    n  i    )  .   {\displaystyle O\left(N\prod _{i=1}^{N}n_{i}\right).}  ![{\displaystyle O\left(N\prod _{i=1}^{N}n_{i}\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/61ba5c780ea20f9a9e61cf04529535082069dff8) 

There exist methods with lower complexity,[[3]](./Longest_common_subsequence#cite_note-BHR00-3)
which often depend on the length of the LCS, the size of the alphabet, or both.

 

The LCS is not necessarily unique; in the worst case, the number of common subsequences is exponential in the lengths of the inputs, so the algorithmic complexity of listing *all* common subsequences must be at least exponential.[[4]](./Longest_common_subsequence#cite_note-4)

 

## Solution for two sequences

 

The LCS problem has an [optimal substructure](./Optimal_substructure): the problem can be broken down into smaller, simpler subproblems, which can, in turn, be broken down into simpler subproblems, and so on, until, finally, the solution becomes trivial. LCS in particular has [overlapping subproblems](./Overlapping_subproblems): the solutions to high-level subproblems often reuse solutions to lower level subproblems. Problems with these two properties are amenable to [dynamic programming](./Dynamic_programming) approaches, in which subproblem solutions are [memoized](./Memoization), that is, the solutions of subproblems are saved for reuse.

 

### Prefixes

 

The prefix *S**n* of *S* is defined as the first *n* characters of *S*.[[5]](./Longest_common_subsequence#cite_note-5)  For example, the prefixes of *S* = (AGCA) are

 *S*0 = () *S*1 = (A) *S*2 = (AG) *S*3 = (AGC) *S*4 = (AGCA). 

Let *LCS*(*X*, *Y*) be a function that computes a longest subsequence common to *X* and *Y*.  Such a function has two interesting properties.

 

### First property

 

*LCS*(*X*^*A*,*Y*^*A*) = *LCS*(*X*,*Y*)^*A*, for all strings *X*, *Y* and all symbols *A*, where ^ denotes string concatenation. This allows one to simplify the *LCS* computation for two sequences ending in the same symbol.
For example, *LCS*("BANANA","ATANA") = *LCS*("BANAN","ATAN")^"A",  Continuing for the remaining common symbols, *LCS*("BANANA","ATANA") = *LCS*("BAN","AT")^"ANA".

 

### Second property

 

If *A* and *B* are distinct symbols (*A*≠*B*), then *LCS*(X^A,Y^B) is one of the maximal-length strings in the set { *LCS*(*X*^*A*,*Y*), *LCS*(*X*,*Y*^*B*) }, for all strings *X*, *Y*.

 

For example, 
*LCS*("ABCDEFG","BCDGK") is the longest string among *LCS*("ABCDEFG","BCDG") and *LCS*("ABCDEF","BCDGK"); if both happened to be of equal length, one of them could be chosen arbitrarily.

 

To realize the property, distinguish two cases:

 
- If  *LCS*("ABCDEFG","BCDGK") ends with a "G", then the final "K" cannot be in the LCS, hence *LCS*("ABCDEFG","BCDGK") = *LCS*("ABCDEFG","BCDG").
- If  *LCS*("ABCDEFG","BCDGK") does not end with a "G", then the final "G" cannot be in the LCS, hence *LCS*("ABCDEFG","BCDGK") = *LCS*("ABCDEF","BCDGK").

 

### *LCS* function defined

 

Let two sequences be defined as follows:      X = (  x  1    x  2   ⋯ ⋯   x  m   )   {\displaystyle X=(x_{1}x_{2}\cdots x_{m})}  ![{\displaystyle X=(x_{1}x_{2}\cdots x_{m})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5dae0351fb8263d4b24e8ef14fb144a492310fdc) and     Y = (  y  1    y  2   ⋯ ⋯   y  n   )   {\displaystyle Y=(y_{1}y_{2}\cdots y_{n})}  ![{\displaystyle Y=(y_{1}y_{2}\cdots y_{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/94cf7f5939ad09bf3f7635b4d72c06a6f63ca17e).  The prefixes of     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) are      X  0   ,  X  1   ,  X  2   , … …  ,  X  m     {\displaystyle X_{0},X_{1},X_{2},\dots ,X_{m}}  ![{\displaystyle X_{0},X_{1},X_{2},\dots ,X_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eba4d09d3e7e7bef987d5fc3d8a7f99cd3fa333b); the prefixes of     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) are      Y  0   ,  Y  1   ,  Y  2   , … …  ,  Y  n     {\displaystyle Y_{0},Y_{1},Y_{2},\dots ,Y_{n}}  ![{\displaystyle Y_{0},Y_{1},Y_{2},\dots ,Y_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f9955e0f295f813a6e500741f325ac2154fe8417).  Let       L C S   (  X  i   ,  Y  j   )   {\displaystyle {\mathit {LCS}}(X_{i},Y_{j})}  ![{\displaystyle {\mathit {LCS}}(X_{i},Y_{j})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fb77d6542d97a11759707fe585b6b376f8c3744) represent the set of longest common subsequence of prefixes      X  i     {\displaystyle X_{i}}  ![{\displaystyle X_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af4a0955af42beb5f85aa05fb8c07abedc13990d) and      Y  j     {\displaystyle Y_{j}}  ![{\displaystyle Y_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6607501d77a93f3806fbb4990421973765481059).  This set of sequences is given by the following.

       L C S   (  X  i   ,  Y  j   ) =   {    ϵ ϵ      if    i = 0    or    j = 0       L C S   (  X  i − −  1   ,  Y  j − −  1   )     ^ ^      x  i       if    i , j > 0    and     x  i   =  y  j        max  ⁡ ⁡  {   L C S   (  X  i   ,  Y  j − −  1   ) ,   L C S   (  X  i − −  1   ,  Y  j   ) }     if    i , j > 0    and     x  i   ≠ ≠   y  j   .         {\displaystyle {\mathit {LCS}}(X_{i},Y_{j})={\begin{cases}\epsilon &{\mbox{if }}i=0{\mbox{ or }}j=0\\{\mathit {LCS}}(X_{i-1},Y_{j-1}){\hat {}}x_{i}&{\mbox{if }}i,j>0{\mbox{ and }}x_{i}=y_{j}\\\operatorname {\max } \{{\mathit {LCS}}(X_{i},Y_{j-1}),{\mathit {LCS}}(X_{i-1},Y_{j})\}&{\mbox{if }}i,j>0{\mbox{ and }}x_{i}\neq y_{j}.\end{cases}}}  ![{\displaystyle {\mathit {LCS}}(X_{i},Y_{j})={\begin{cases}\epsilon &{\mbox{if }}i=0{\mbox{ or }}j=0\\{\mathit {LCS}}(X_{i-1},Y_{j-1}){\hat {}}x_{i}&{\mbox{if }}i,j>0{\mbox{ and }}x_{i}=y_{j}\\\operatorname {\max } \{{\mathit {LCS}}(X_{i},Y_{j-1}),{\mathit {LCS}}(X_{i-1},Y_{j})\}&{\mbox{if }}i,j>0{\mbox{ and }}x_{i}\neq y_{j}.\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/83d2b5614b44cfcb96c1342646f133d3d2598605) 

To find the LCS of      X  i     {\displaystyle X_{i}}  ![{\displaystyle X_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af4a0955af42beb5f85aa05fb8c07abedc13990d) and      Y  j     {\displaystyle Y_{j}}  ![{\displaystyle Y_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6607501d77a93f3806fbb4990421973765481059), compare      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158) and      y  j     {\displaystyle y_{j}}  ![{\displaystyle y_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8df4e372390588acb968986cfc388e50b930b3a).  If they are equal, then the sequence       L C S   (  X  i − −  1   ,  Y  j − −  1   )   {\displaystyle {\mathit {LCS}}(X_{i-1},Y_{j-1})}  ![{\displaystyle {\mathit {LCS}}(X_{i-1},Y_{j-1})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c85af2f42b24edabae3467a947090afcf4355e1) is extended by that element,      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158).  If they are not equal, then the longest among the two sequences,       L C S   (  X  i   ,  Y  j − −  1   )   {\displaystyle {\mathit {LCS}}(X_{i},Y_{j-1})}  ![{\displaystyle {\mathit {LCS}}(X_{i},Y_{j-1})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ef8a34cf3104c10f0a9a3ae1ca51839b5606beb), and       L C S   (  X  i − −  1   ,  Y  j   )   {\displaystyle {\mathit {LCS}}(X_{i-1},Y_{j})}  ![{\displaystyle {\mathit {LCS}}(X_{i-1},Y_{j})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/94bc4ede92b87a62a12af54b0a24b88ea40cd918), is retained.  (If they are the same length, but not identical, then both are retained.) The base case, when either      X  i     {\displaystyle X_{i}}  ![{\displaystyle X_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af4a0955af42beb5f85aa05fb8c07abedc13990d) or      Y  i     {\displaystyle Y_{i}}  ![{\displaystyle Y_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d57be496fff95ee2a97ee43c7f7fe244b4dbf8ae) is empty, is the [empty string](./Empty_string),     ϵ ϵ    {\displaystyle \epsilon }  ![{\displaystyle \epsilon }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3837cad72483d97bcdde49c85d3b7b859fb3fd2).

 

### Worked example

 

The longest subsequence common to *R* = (GAC), and *C* = (AGCAT) will be found.  Because the *LCS* function uses a "zeroth" element, it is convenient to define zero prefixes that are empty for these sequences:  *R*0 =  ε; and *C*0 =  ε.  All the prefixes are placed in a table with *C* in the first row (making it a column header) and *R* in the first column (making it a row header).

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | ε | ε | ε | ε | ε | ε |
| G | ε |  |  |  |  |  |
| A | ε |  |  |  |  |  |
| C | ε |  |  |  |  |  |
|  |

 

This table is used to store the LCS sequence for each step of the calculation.  The second column and second row have been filled in with ε, because when an empty sequence is compared with a non-empty sequence, the longest common subsequence is always an empty sequence.

 

*LCS*(*R*1, *C*1) is determined by comparing the first elements in each sequence.  G and A are not the same, so this LCS gets (using the "second property") the longest of the two sequences, *LCS*(*R*1, *C*0) and  *LCS*(*R*0, *C*1).  According to the table, both of these are empty, so *LCS*(*R*1, *C*1) is also empty, as shown in the table below.  The arrows indicate that the sequence comes from both the cell above, *LCS*(*R*0, *C*1) and the cell on the left, *LCS*(*R*1, *C*0).

 

*LCS*(*R*1, *C*2) is determined by comparing G and G.  They match, so G is appended to the upper left sequence, *LCS*(*R*0, *C*1), which is (ε), giving (εG), which is (G).

 

For *LCS*(*R*1, *C*3), G and C do not match.  The sequence above is empty; the one to the left contains one element, G.  Selecting the longest of these, *LCS*(*R*1, *C*3) is (G).  The arrow points to the left, since that is the longest of the two sequences.

 

*LCS*(*R*1, *C*4), likewise, is (G).

 

*LCS*(*R*1, *C*5), likewise, is (G).

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | ε | ε | ε | ε | ε | ε |
| G | ε | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}ε | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) |
| A | ε |  |  |  |  |  |
| C | ε |  |  |  |  |  |
|  |

 

For *LCS*(*R*2, *C*1), A is compared with A.  The two elements match, so A is appended to ε, giving (A).

 

For *LCS*(*R*2, *C*2), A and G do not match, so the longest of *LCS*(*R*1, *C*2), which is (G), and *LCS*(*R*2, *C*1), which is (A), is used.  In this case, they each contain one element, so this LCS is given two subsequences:  (A) and (G).

 

For *LCS*(*R*2, *C*3), A does not match C.  *LCS*(*R*2, *C*2) contains sequences (A) and (G); LCS(*R*1, *C*3) is (G), which is already contained in *LCS*(*R*2, *C*2).  The result is that *LCS*(*R*2, *C*3) also contains the two subsequences, (A) and (G).

 

For *LCS*(*R*2, *C*4), A matches A, which is appended to the upper left cell, giving (GA).

 

For *LCS*(*R*2, *C*5), A does not match T.  Comparing the two sequences, (GA) and (G), the longest is (GA), so *LCS*(*R*2, *C*5) is (GA).

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | ε | ε | ε | ε | ε | ε |
| G | ε | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}ε | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) |
| A | ε | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(A) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(A) & (G) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(A) & (G) | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(GA) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(GA) |
| C | ε |  |  |  |  |  |
|  |

 

For *LCS*(*R*3, *C*1), C and A do not match, so *LCS*(*R*3, *C*1) gets the longest of the two sequences, (A).

 

For *LCS*(*R*3, *C*2), C and G do not match.  Both *LCS*(*R*3, *C*1) and *LCS*(*R*2, *C*2) have one element.  The result is that *LCS*(*R*3, *C*2) contains the two subsequences, (A) and (G).

 

For *LCS*(*R*3, *C*3), C and C match, so C is appended to *LCS*(*R*2, *C*2), which contains the two subsequences, (A) and (G), giving (AC) and (GC).

 

For *LCS*(*R*3, *C*4), C and A do not match.  Combining *LCS*(*R*3, *C*3), which contains (AC) and (GC), and *LCS*(*R*2, *C*4), which contains (GA), gives a total of three sequences:  (AC), (GC), and (GA).

 

Finally, for *LCS*(*R*3, *C*5), C and T do not match.  The result is that *LCS*(*R*3, *C*5) also contains the three sequences, (AC), (GC), and (GA).

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | ε | ε | ε | ε | ε | ε |
| G | ε | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}ε | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(G) |
| A | ε | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(A) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(A) & (G) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(A) & (G) | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(GA) | ←{\displaystyle {\overset {\ }{\leftarrow }}}(GA) |
| C | ε | ↑{\displaystyle {\overset {\ \uparrow }{\ }}}(A) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(A) & (G) | ↖{\displaystyle {\overset {\nwarrow }{\ }}}(AC) & (GC) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(AC) & (GC) & (GA) | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}(AC) & (GC) & (GA) |
|  |

 

The final result is that the last cell contains all the longest subsequences common to (AGCAT) and (GAC); these are (AC), (GC), and (GA).  The table also shows the longest common subsequences for every possible pair of prefixes.  For example, for (AGC) and (GA), the longest common subsequence are (A) and (G).

 

### Traceback approach

 

Calculating the LCS of a row of the LCS table requires only the solutions to the current row and the previous row.  Still, for long sequences, these sequences can get numerous and long, requiring a lot of storage space.  Storage space can be saved by saving not the actual subsequences, but the length of the subsequence and the direction of the arrows, as in the table below.

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | 0 | 0 | 0 | 0 | 0 | 0 |
| G | 0 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}0 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 |
| A | 0 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}2 | ←{\displaystyle {\overset {\ }{\leftarrow }}}2 |
| C | 0 | ↑{\displaystyle {\overset {\ \uparrow }{\ }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}2 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}2 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}2 |
|  |

 

The actual subsequences are deduced in a "traceback" procedure that follows the arrows backwards, starting from the last cell in the table.  When the length decreases, the sequences must have had a common element.  Several paths are possible when two arrows are shown in a cell.  Below is the table for such an analysis, with numbers colored in cells where the length is about to decrease.  The bold numbers trace out the sequence, (GA).[[6]](./Longest_common_subsequence#cite_note-6)

 
|  | ε | A | G | C | A | T |
| --- | --- | --- | --- | --- | --- | --- |
| ε | 0 | 0 | 0 | 0 | 0 | 0 |
| G | 0 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}0 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 | ←{\displaystyle {\overset {\ }{\leftarrow }}}1 |
| A | 0 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}2 | ←{\displaystyle {\overset {\ }{\leftarrow }}}2 |
| C | 0 | ↑{\displaystyle {\overset {\ \uparrow }{\ }}}1 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}1 | ↖{\displaystyle {\overset {\nwarrow }{\ }}}2 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}2 | ←↑{\displaystyle {\overset {\ \ \uparrow }{\leftarrow }}}2 |
|  |

 

## Relation to other problems

 

For two strings      X  1 … …  m     {\displaystyle X_{1\dots m}}  ![{\displaystyle X_{1\dots m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/91f533afde39c7382266c5d9052eff5a34be037a) and      Y  1 … …  n     {\displaystyle Y_{1\dots n}}  ![{\displaystyle Y_{1\dots n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e3fe6342e85a88f5f35c7996a3837f912794af2), the length of the [shortest common supersequence](./Shortest_common_supersequence_problem) is related to the length of the LCS by[[3]](./Longest_common_subsequence#cite_note-BHR00-3)

      |  S C S ( X , Y )  |  = n + m − −   |  L C S ( X , Y )  |  .   {\displaystyle \left|SCS(X,Y)\right|=n+m-\left|LCS(X,Y)\right|.}  ![{\displaystyle \left|SCS(X,Y)\right|=n+m-\left|LCS(X,Y)\right|.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/718744d8f0ec7df7bb875696d28335ed8077cae7) 

The [edit distance](./Edit_distance) when only insertion and deletion is allowed (no substitution), or when the cost of the substitution is the double of the cost of an insertion or  deletion, is:

      d ′  ( X , Y ) = n + m − −  2 ⋅ ⋅   |  L C S ( X , Y )  |  .   {\displaystyle d'(X,Y)=n+m-2\cdot \left|LCS(X,Y)\right|.}  ![{\displaystyle d'(X,Y)=n+m-2\cdot \left|LCS(X,Y)\right|.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26d498dc03e6191acede91c81b2089b5065e8fa5) 

## Code for the dynamic programming solution

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(March 2013)(Learn how and when to remove this message) |
| --- | --- |

 

### Computing the length of the LCS

 

The function below takes as input sequences `X[1..m]` and `Y[1..n]`, computes the LCS between `X[1..i]` and `Y[1..j]` for all `1 ≤ i ≤ m` and `1 ≤ j ≤ n`, and stores it in `C[i,j]`. `C[m,n]` will contain the length of the LCS of `X` and `Y`.[[7]](./Longest_common_subsequence#cite_note-:1-7)

 
```
function LCSLength(X[1..m], Y[1..n])
    C = array(0..m, 0..n)
    for i := 0..m
        C[i,0] = 0
    for j := 0..n
        C[0,j] = 0
    for i := 1..m
        for j := 1..n
            if X[i] = Y[j]
                C[i,j] := C[i-1,j-1] + 1
            else
                C[i,j] := max(C[i,j-1], C[i-1,j])
    return C[m,n]
```
 

Alternatively, [memoization](./Memoization) could be used.

 

### Reading out a LCS

 

The following function [backtracks](./Backtracking) the choices taken when computing the `C` table. If the last characters in the prefixes are equal, they must be in an LCS. If not, check what gave the largest LCS of keeping      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158) and      y  j     {\displaystyle y_{j}}  ![{\displaystyle y_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8df4e372390588acb968986cfc388e50b930b3a), and make the same choice. Just choose one if they were equally long. Call the function with `i=m` and `j=n`.

 
```
function backtrack(C[0..m,0..n], X[1..m], Y[1..n], i, j)
    if i = 0 or j = 0
        return ""
    if  X[i] = Y[j]
        return backtrack(C, X, Y, i-1, j-1) + X[i]
    if C[i,j-1] > C[i-1,j]
        return backtrack(C, X, Y, i, j-1)
    return backtrack(C, X, Y, i-1, j)
```
 

### Reading out all LCSs

 

If choosing      x  i     {\displaystyle x_{i}}  ![{\displaystyle x_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e87000dd6142b81d041896a30fe58f0c3acb2158) and      y  j     {\displaystyle y_{j}}  ![{\displaystyle y_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8df4e372390588acb968986cfc388e50b930b3a) would give an equally long result, read out both resulting subsequences. This is returned as a set by this function. Notice that this function is not polynomial, as it might branch in almost every step if the strings are similar.

 
```
function backtrackAll(C[0..m,0..n], X[1..m], Y[1..n], i, j)
    if i = 0 or j = 0
        return {""}
    if X[i] = Y[j]
        return {Z + X[i] for all Z in backtrackAll(C, X, Y, i-1, j-1)}
    R := {}
    if C[i,j-1] ≥ C[i-1,j]
        R := backtrackAll(C, X, Y, i, j-1)
    if C[i-1,j] ≥ C[i,j-1]
        R := R ∪ backtrackAll(C, X, Y, i-1, j)
    return R
```
 

### Print the diff

 

This function will backtrack through the C matrix, and print the [diff](./Diff) between the two sequences. Notice that you will get a different answer if you exchange `≥` and `<`, with `>` and `≤` below.

 
```
function printDiff(C[0..m,0..n], X[1..m], Y[1..n], i, j)
    if i >= 0 and j >= 0 and X[i] = Y[j]
        printDiff(C, X, Y, i-1, j-1)
        print "  " + X[i]
    else if j > 0 and (i = 0 or C[i,j-1] ≥ C[i-1,j])
        printDiff(C, X, Y, i, j-1)
        print "+ " + Y[j]
    else if i > 0 and (j = 0 or C[i,j-1] < C[i-1,j])
        printDiff(C, X, Y, i-1, j)
        print "- " + X[i]
    else
        print ""
```
 

### Example

 

Let     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) be "`XMJYAUZ`" and     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) be "`MZJAWXU`". The longest common subsequence between     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) and     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) is "`MJAU`". The table `C` shown below, which is generated by the function `LCSLength`, shows the lengths of the longest common subsequences between prefixes of     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) and     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f). The     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)th row and     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)th column shows the length of the LCS between      X  1.. i     {\displaystyle X_{1..i}}  ![{\displaystyle X_{1..i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/802a465215e19e6d562200849484bd659639bdc4) and      Y  1.. j     {\displaystyle Y_{1..j}}  ![{\displaystyle Y_{1..j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0020793d4eef7b32e7c4607a28a1b7596ca74c8e).

 
|  | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ε | M | Z | J | A | W | X | U |
| 0 | ε | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | X | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 2 | M | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 3 | J | 0 | 1 | 1 | 2 | 2 | 2 | 2 | 2 |
| 4 | Y | 0 | 1 | 1 | 2 | 2 | 2 | 2 | 2 |
| 5 | A | 0 | 1 | 1 | 2 | 3 | 3 | 3 | 3 |
| 6 | U | 0 | 1 | 1 | 2 | 3 | 3 | 3 | 4 |
| 7 | Z | 0 | 1 | 2 | 2 | 3 | 3 | 3 | 4 |

 

The highlighted numbers show the path the function `backtrack` would follow from the bottom right to the top left corner, when reading out an LCS. If the current symbols in     X   {\displaystyle X}  ![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) and     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) are equal, they are part of the LCS, and we go both up and left (shown in **bold**). If not, we go up or left, depending on which cell has a higher number. This corresponds to either taking the LCS between      X  1.. i − −  1     {\displaystyle X_{1..i-1}}  ![{\displaystyle X_{1..i-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a77c34dfaeb2e6b836fdb069db0d3d30808d3b63) and      Y  1.. j     {\displaystyle Y_{1..j}}  ![{\displaystyle Y_{1..j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0020793d4eef7b32e7c4607a28a1b7596ca74c8e), or      X  1.. i     {\displaystyle X_{1..i}}  ![{\displaystyle X_{1..i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/802a465215e19e6d562200849484bd659639bdc4) and      Y  1.. j − −  1     {\displaystyle Y_{1..j-1}}  ![{\displaystyle Y_{1..j-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/30f547ba08a4c0e836e6d62bcc616d9c18efab25).

 

## Code optimization

 

Several optimizations can be made to the algorithm above to speed it up for real-world cases.

 

### Reduce the problem set

 

The C matrix in the naive algorithm [grows quadratically](./Quadratic_growth) with the lengths of the sequences.  For two 100-item sequences, a 10,000-item matrix would be needed, and 10,000 comparisons would need to be done.  In most real-world cases, especially source code diffs and patches, the beginnings and ends of files rarely change, and almost certainly not both at the same time.  If only a few items have changed in the middle of the sequence, the beginning and end can be eliminated.  This reduces not only the memory requirements for the matrix, but also the number of comparisons that must be done.

 
```
function LCS(X[1..m], Y[1..n])
    start := 1
    m_end := m
    n_end := n
    trim off the matching items at the beginning
    while start ≤ m_end and start ≤ n_end and X[start] = Y[start]
        start := start + 1
    trim off the matching items at the end
    while start ≤ m_end and start ≤ n_end and X[m_end] = Y[n_end]
        m_end := m_end - 1
        n_end := n_end - 1
    C = array(start-1..m_end, start-1..n_end)
    only loop over the items that have changed
    for i := start..m_end
        for j := start..n_end
            the algorithm continues as before ...
```
 

In the best-case scenario, a sequence with no changes, this optimization would eliminate the need for the C matrix.  In the worst-case scenario, a change to the very first and last items in the sequence, only two additional comparisons are performed.

 

### Reduce the comparison time

 

Most of the time taken by the naive algorithm is spent performing comparisons between items in the sequences.  For textual sequences such as source code, you want to view lines as the sequence elements instead of single characters.  This can mean comparisons of relatively long strings for each step in the algorithm.  Two optimizations can be made that can help to reduce the time these comparisons consume.

 

### Reduce strings to hashes

 

A [hash function](./Hash_function) or [checksum](./Checksum) can be used to reduce the size of the strings in the sequences.  That is, for source code where the average line is 60 or more characters long, the hash or checksum for that line might be only 8 to 40 characters long.  Additionally, the randomized nature of hashes and checksums would guarantee that comparisons would short-circuit faster, as lines of source code will rarely be changed at the beginning.

 

There are three primary drawbacks to this optimization.  First, an amount of time needs to be spent beforehand to precompute the hashes for the two sequences.  Second, additional memory needs to be allocated for the new hashed sequences.  However, in comparison to the naive algorithm used here, both of these drawbacks are relatively minimal.

 

The third drawback is that of [collisions](./Hash_collision).  Since the checksum or hash is not guaranteed to be unique, there is a small chance that two different items could be reduced to the same hash.  This is unlikely in source code, but it is possible.  A cryptographic hash would therefore be far better suited for this optimization, as its entropy is going to be significantly greater than that of a simple checksum.  However, the benefits may not be worth the setup and computational requirements of a cryptographic hash for small sequence lengths.

 

### Reduce the required space

 

If only the length of the LCS is required, the matrix can be reduced to a     2 × ×  min ( n , m )   {\displaystyle 2\times \min(n,m)}  ![{\displaystyle 2\times \min(n,m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/74eb0ff417c0f04134453a947de7bc4ff65e792e) matrix, or to a     min ( m , n ) + 1   {\displaystyle \min(m,n)+1}  ![{\displaystyle \min(m,n)+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8c6d94e51651291f4daaa17f56ee08b32739d12) vector as the dynamic programming approach requires only the current and previous columns of the matrix. [Hirschberg's algorithm](./Hirschberg's_algorithm) allows the construction of the optimal sequence itself in the same quadratic time and linear space bounds.[[8]](./Longest_common_subsequence#cite_note-8)

 

### Reduce cache misses

 

Chowdhury and Ramachandran devised a quadratic-time linear-space algorithm[[9]](./Longest_common_subsequence#cite_note-CR-06-9)[[10]](./Longest_common_subsequence#cite_note-CLR-08-10) for finding the LCS length along with an optimal sequence which runs faster than Hirschberg's algorithm in practice due to its superior cache performance.[[9]](./Longest_common_subsequence#cite_note-CR-06-9) The algorithm has an asymptotically optimal cache complexity under the [Ideal cache model](./Cache-oblivious#Idealized_cache_model).[[11]](./Longest_common_subsequence#cite_note-FLPR-12-11) Interestingly, the algorithm itself is [cache-oblivious](./Cache-oblivious)[[11]](./Longest_common_subsequence#cite_note-FLPR-12-11) meaning that it does not make any choices based on the cache parameters (e.g., cache size and cache line size) of the machine.

 

### Further optimized algorithms

 

Several algorithms exist that run faster than the presented dynamic programming approach. One of them is [Hunt–Szymanski algorithm](./Hunt–Szymanski_algorithm), which typically runs in     O ( ( n + r ) log ⁡ ⁡  ( n ) )   {\displaystyle O((n+r)\log(n))}  ![{\displaystyle O((n+r)\log(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c0d7ca56ee0f885f03b0a5ed115642c4666b4c2f) time (for     n > m   {\displaystyle n>m}  ![{\displaystyle n>m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e64e2a4a5b6cb58f1553c6a65551b4898bb82403)), where     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is the number of matches between the two sequences.[[12]](./Longest_common_subsequence#cite_note-12) For problems with a bounded alphabet size, the [Method of Four Russians](./Method_of_Four_Russians) can be used to reduce the running time of the dynamic programming algorithm by a logarithmic factor.[[13]](./Longest_common_subsequence#cite_note-13)

 

## Behavior on random strings

 Main article: [Chvátal–Sankoff constants](./Chvátal–Sankoff_constants) 

Beginning with [Chvátal & Sankoff (1975)](./Longest_common_subsequence#CITEREFChvátalSankoff1975),[[14]](./Longest_common_subsequence#cite_note-14) a number of researchers have investigated the behavior of the longest common subsequence length when the two given strings are drawn randomly from the same alphabet. When the alphabet size is constant, the expected length of the LCS is proportional to the length of the two strings, and the constants of proportionality (depending on alphabet size) are known as the [Chvátal–Sankoff constants](./Chvátal–Sankoff_constants). Their exact values are not known, but upper and lower bounds on their values have been proven,[[15]](./Longest_common_subsequence#cite_note-15) and it is known that they grow inversely proportionally to the square root of the alphabet size.[[16]](./Longest_common_subsequence#cite_note-16) Simplified mathematical models of the longest common subsequence problem have been shown to be controlled by the [Tracy–Widom distribution](./Tracy–Widom_distribution).[[17]](./Longest_common_subsequence#cite_note-17)

 

## Computing the longest palindromic subsequence of a string

 

For decades, it had been considered folklore that the longest palindromic subsequence of a string could be computed by finding the longest common subsequence between the string and its reversal, using the classical dynamic programming approach introduced by Wagner and Fischer. However, a formal proof of the correctness of this method was only established in 2024 by Brodal, Fagerberg, and Moldrup Rysgaard.[[18]](./Longest_common_subsequence#cite_note-18)

 

## See also

 
- [Longest increasing subsequence](./Longest_increasing_subsequence)
- [Longest alternating subsequence](./Longest_alternating_subsequence)
- [Levenshtein distance](./Levenshtein_distance)

 

## References

  
1. [↑](./Longest_common_subsequence#cite_ref-1) David Maier (1978). ["The Complexity of Some Problems on Subsequences and Supersequences"](https://doi.org/10.1145%2F322063.322075). *J. ACM*. **25** (2). ACM Press: 322–336. [doi](./Doi_(identifier)):[10.1145/322063.322075](https://doi.org/10.1145%2F322063.322075). [S2CID](./S2CID_(identifier)) [16120634](https://api.semanticscholar.org/CorpusID:16120634).
2. [↑](./Longest_common_subsequence#cite_ref-2) Wagner, Robert; Fischer, Michael (January 1974). "The string-to-string correction problem". *[Journal of the ACM](./Journal_of_the_ACM)*. **21** (1): 168–173. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.367.5281](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.367.5281). [doi](./Doi_(identifier)):[10.1145/321796.321811](https://doi.org/10.1145%2F321796.321811). [S2CID](./S2CID_(identifier)) [13381535](https://api.semanticscholar.org/CorpusID:13381535).
3. [1](./Longest_common_subsequence#cite_ref-BHR00_3-0) [2](./Longest_common_subsequence#cite_ref-BHR00_3-1)  L. Bergroth and H. Hakonen and T. Raita (7–29 September 2000). *A survey of longest common subsequence algorithms*. Proceedings Seventh International Symposium on String Processing and Information Retrieval. SPIRE 2000. A Curuna, Spain: IEEE Computer Society. pp. 39–48. [doi](./Doi_(identifier)):[10.1109/SPIRE.2000.878178](https://doi.org/10.1109%2FSPIRE.2000.878178). [ISBN](./ISBN_(identifier)) [0-7695-0746-8](./Special:BookSources/0-7695-0746-8). [S2CID](./S2CID_(identifier)) [10375334](https://api.semanticscholar.org/CorpusID:10375334).
4. [↑](./Longest_common_subsequence#cite_ref-4) Ronald I. Greenberg (2003-08-06). "Bounds on the Number of Longest Common Subsequences". [arXiv](./ArXiv_(identifier)):[cs.DM/0301030](https://arxiv.org/abs/cs.DM/0301030).
5. [↑](./Longest_common_subsequence#cite_ref-5) Xia, Xuhua (2007). [*Bioinformatics and the Cell: Modern Computational Approaches in Genomics, Proteomics and Transcriptomics*](https://archive.org/details/bioinformaticsce00xiax_984). New York: Springer. p. [24](https://archive.org/details/bioinformaticsce00xiax_984/page/n38). [ISBN](./ISBN_(identifier)) [978-0-387-71336-6](./Special:BookSources/978-0-387-71336-6).
6. [↑](./Longest_common_subsequence#cite_ref-6) [Thomas H. Cormen](./Thomas_H._Cormen), [Charles E. Leiserson](./Charles_E._Leiserson), [Ronald L. Rivest](./Ronald_L._Rivest) and [Clifford Stein](./Clifford_Stein) (2001). "15.4". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 350–355. [ISBN](./ISBN_(identifier)) [0-262-53196-8](./Special:BookSources/0-262-53196-8).`{{cite book}}`:  CS1 maint: multiple names: authors list ([link](./Category:CS1_maint:_multiple_names:_authors_list))
7. [↑](./Longest_common_subsequence#cite_ref-:1_7-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009) [1990]. "Dynamic Programming". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.). MIT Press and McGraw-Hill. p. 394. [ISBN](./ISBN_(identifier)) [0-262-03384-4](./Special:BookSources/0-262-03384-4).
8. [↑](./Longest_common_subsequence#cite_ref-8) [Hirschberg, D. S.](./Dan_Hirschberg) (1975). ["A linear space algorithm for computing maximal common subsequences"](https://doi.org/10.1145%2F360825.360861). *Communications of the ACM*. **18** (6): 341–343. [doi](./Doi_(identifier)):[10.1145/360825.360861](https://doi.org/10.1145%2F360825.360861). [S2CID](./S2CID_(identifier)) [207694727](https://api.semanticscholar.org/CorpusID:207694727).
9. [1](./Longest_common_subsequence#cite_ref-CR-06_9-0) [2](./Longest_common_subsequence#cite_ref-CR-06_9-1) Chowdhury, Rezaul; Ramachandran, Vijaya (January 2006). ["Cache-oblivious dynamic programming"](https://dl.acm.org/doi/10.5555/1109557.1109622). *Proceedings of the seventeenth annual ACM-SIAM symposium on Discrete algorithm - SODA '06*. pp. 591–600. [doi](./Doi_(identifier)):[10.1145/1109557.1109622](https://doi.org/10.1145%2F1109557.1109622). [ISBN](./ISBN_(identifier)) [0-89871-605-5](./Special:BookSources/0-89871-605-5). [S2CID](./S2CID_(identifier)) [9650418](https://api.semanticscholar.org/CorpusID:9650418).
10. [↑](./Longest_common_subsequence#cite_ref-CLR-08_10-0) Chowdhury, Rezaul; Le, Hai-Son; Ramachandran, Vijaya (July 2010). "Cache-oblivious dynamic programming for bioinformatics". *IEEE/ACM Transactions on Computational Biology and Bioinformatics*. **7** (3): 495–510. [Bibcode](./Bibcode_(identifier)):[2010ITCBB...7..495C](https://ui.adsabs.harvard.edu/abs/2010ITCBB...7..495C). [doi](./Doi_(identifier)):[10.1109/TCBB.2008.94](https://doi.org/10.1109%2FTCBB.2008.94). [PMID](./PMID_(identifier)) [20671320](https://pubmed.ncbi.nlm.nih.gov/20671320). [S2CID](./S2CID_(identifier)) [2532039](https://api.semanticscholar.org/CorpusID:2532039).
11. [1](./Longest_common_subsequence#cite_ref-FLPR-12_11-0) [2](./Longest_common_subsequence#cite_ref-FLPR-12_11-1) Frigo, Matteo; Leiserson, Charles E.; Prokop, Harald; Ramachandran, Sridhar (January 2012). ["Cache-oblivious algorithms"](https://dl.acm.org/doi/10.1145/2071379.2071383). *ACM Transactions on Algorithms*. **8** (1): 1–22. [doi](./Doi_(identifier)):[10.1145/2071379.2071383](https://doi.org/10.1145%2F2071379.2071383).
12. [↑](./Longest_common_subsequence#cite_ref-12) Apostolico, Alberto; Galil, Zvi (1997-05-29). [*Pattern Matching Algorithms*](https://books.google.com/books?id=mFd_grFyiT4C&q=hunt+szymanski+algorithm&pg=PA132). Oxford University Press. [ISBN](./ISBN_(identifier)) [978-0-19-535434-8](./Special:BookSources/978-0-19-535434-8).
13. [↑](./Longest_common_subsequence#cite_ref-13) Masek, William J.; [Paterson, Michael S.](./Mike_Paterson) (1980), "A faster algorithm computing string edit distances", *Journal of Computer and System Sciences*, **20** (1): 18–31, [doi](./Doi_(identifier)):[10.1016/0022-0000(80)90002-1](https://doi.org/10.1016%2F0022-0000%2880%2990002-1), [hdl](./Hdl_(identifier)):[1721.1/148933](https://hdl.handle.net/1721.1%2F148933), [MR](./MR_(identifier)) [0566639](https://mathscinet.ams.org/mathscinet-getitem?mr=0566639).
14. [↑](./Longest_common_subsequence#cite_ref-14) [Chvátal, Václáv](./Václav_Chvátal); [Sankoff, David](./David_Sankoff) (1975), "Longest common subsequences of two random sequences", *Journal of Applied Probability*, **12** (2): 306–315, [doi](./Doi_(identifier)):[10.2307/3212444](https://doi.org/10.2307%2F3212444), [JSTOR](./JSTOR_(identifier)) [3212444](https://www.jstor.org/stable/3212444), [MR](./MR_(identifier)) [0405531](https://mathscinet.ams.org/mathscinet-getitem?mr=0405531), [S2CID](./S2CID_(identifier)) [250345191](https://api.semanticscholar.org/CorpusID:250345191).
15. [↑](./Longest_common_subsequence#cite_ref-15) Lueker, George S. (2009), "Improved bounds on the average length of longest common subsequences", *[Journal of the ACM](./Journal_of_the_ACM)*, **56** (3), A17, [doi](./Doi_(identifier)):[10.1145/1516512.1516519](https://doi.org/10.1145%2F1516512.1516519), [MR](./MR_(identifier)) [2536132](https://mathscinet.ams.org/mathscinet-getitem?mr=2536132), [S2CID](./S2CID_(identifier)) [7232681](https://api.semanticscholar.org/CorpusID:7232681).
16. [↑](./Longest_common_subsequence#cite_ref-16) Kiwi, Marcos; Loebl, Martin; [Matoušek, Jiří](./Jiří_Matoušek_(mathematician)) (2005), "Expected length of the longest common subsequence for large alphabets", *[Advances in Mathematics](./Advances_in_Mathematics)*, **197** (2): 480–498, [arXiv](./ArXiv_(identifier)):[math/0308234](https://arxiv.org/abs/math/0308234), [doi](./Doi_(identifier)):[10.1016/j.aim.2004.10.012](https://doi.org/10.1016%2Fj.aim.2004.10.012), [MR](./MR_(identifier)) [2173842](https://mathscinet.ams.org/mathscinet-getitem?mr=2173842).
17. [↑](./Longest_common_subsequence#cite_ref-17) Majumdar, Satya N.; Nechaev, Sergei (2005), "Exact asymptotic results for the Bernoulli matching model of sequence alignment", *Physical Review E*, **72** (2): 020901, 4, [arXiv](./ArXiv_(identifier)):[q-bio/0410012](https://arxiv.org/abs/q-bio/0410012), [Bibcode](./Bibcode_(identifier)):[2005PhRvE..72b0901M](https://ui.adsabs.harvard.edu/abs/2005PhRvE..72b0901M), [doi](./Doi_(identifier)):[10.1103/PhysRevE.72.020901](https://doi.org/10.1103%2FPhysRevE.72.020901), [MR](./MR_(identifier)) [2177365](https://mathscinet.ams.org/mathscinet-getitem?mr=2177365), [PMID](./PMID_(identifier)) [16196539](https://pubmed.ncbi.nlm.nih.gov/16196539), [S2CID](./S2CID_(identifier)) [11390762](https://api.semanticscholar.org/CorpusID:11390762).
18. [↑](./Longest_common_subsequence#cite_ref-18) Brodal, G. S.; Fagerberg, R.; Rysgaard, C. M. (2024). *On Finding Longest Palindromic Subsequences Using Longest Common Subsequences*. Schloss Dagstuhl – Leibniz-Zentrum für Informatik. pp. 35:1–35:16. [doi](./Doi_(identifier)):[10.4230/lipics.esa.2024.35](https://doi.org/10.4230%2Flipics.esa.2024.35).

  Dead note "GJ78": {{cite book|author = [[Michael R. Garey]] and [[David S. Johnson]] | year = 1979 | title = Computers and Intractability: A Guide to the Theory of NP&#x2D;Completeness|url = https://archive.org/details/computersintract00gare_180 |url&#x2D;access = limited | publisher = W.H. Freeman | isbn = 0&#x2D;7167&#x2D;1045&#x2D;5| pages = [https://archive.org/details/computersintract00gare_180/page/n238 228]}} A421: SR10.  

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm implementation](https://en.wikibooks.org/wiki/Algorithm%20implementation)* has a page on the topic of: ***[Longest common subsequence](https://en.wikibooks.org/wiki/Algorithm%20implementation/Strings/Longest%20common%20subsequence)***  
- [Dictionary of Algorithms and Data Structures: longest common subsequence](https://xlinux.nist.gov/dads/HTML/longestCommonSubsequence.html)
- [A collection of implementations of the longest common subsequence in many programming languages](https://rosettacode.org/wiki/Longest_common_subsequence)
- [Find Longest Common Subsequence in Python](https://www.codespeedy.com/find-longest-common-subsequence-in-python/)

 

  case of fixed number of input strings   case of arbitrary number of input strings  

 
| vteStrings |
| --- |
| String metric | Approximate string matchingBitap algorithmDamerau–Levenshtein distanceEdit distanceGestalt pattern matchingHamming distanceJaro–Winkler distanceLee distanceLevenshtein automatonLevenshtein distanceWagner–Fischer algorithm |
| String-searching algorithm | Apostolico–Giancarlo algorithmBoyer–Moore string-search algorithmBoyer–Moore–Horspool algorithmKnuth–Morris–Pratt algorithmRabin–Karp algorithmRaita algorithmTrigram searchTwo-way string-matching algorithmZhu–Takaoka string matching algorithm |
| Multiple string searching | Aho–CorasickCommentz-Walter algorithm |
| Regular expression | Comparison of regular-expression enginesRegular grammarThompson's constructionNondeterministic finite automaton |
| Sequence alignment | BLASTHirschberg's algorithmNeedleman–Wunsch algorithmSmith–Waterman algorithm |
| Data structure | DAFSASubstring indexSuffix arraySuffix automatonSuffix treeCompressed suffix arrayLCP arrayFM-indexGeneralized suffix treeRopeTernary search treeTrie |
| Other | ParsingPattern matchingCompressed pattern matchingLongest common subsequenceLongest common substringSequential pattern miningSortingString rewriting systemsString operations |