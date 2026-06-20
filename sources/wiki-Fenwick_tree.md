---
source: https://en.wikipedia.org/wiki/Fenwick_tree
fetched: 2026-06-19
---

Data structure 
| Fenwick treeBinary indexed tree |
| --- |
|  |
| Type | Binomial tree |
| Invented | 1989 |
| Invented by | Boris Ryabko |
| Time complexityinbig O notationOperationAverageWorst caseSearchO(logn)O(logn)InsertO(logn)O(logn)Space complexitySpaceO(n)O(n) | Time complexityinbig O notation | Operation | Average | Worst case | Search | O(logn) | O(logn) | Insert | O(logn) | O(logn) | Space complexity | Space | O(n) | O(n) |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Search | O(logn) | O(logn) |
| Insert | O(logn) | O(logn) |
| Space complexity |
| Space | O(n) | O(n) |

 

A **Fenwick tree** or **binary indexed tree** **(BIT)** is a data structure that stores an array of values and can efficiently compute [prefix sums](./Prefix_sum) of the values *and* update the values.  It also supports an efficient rank-search operation for finding the longest prefix whose sum is no more than a specified value.  Its primary use is operating on the [cumulative distribution function](./Cumulative_distribution_function) of a [statistical frequency](./Statistical_frequency) table which is updated often.

 

This structure was proposed by Boris Ryabko in 1989[[1]](./Fenwick_tree#cite_note-1)
with a further modification published in 1992.[[2]](./Fenwick_tree#cite_note-2)
It has subsequently become known under the name Fenwick tree after Peter Fenwick, who described this structure in his 1994 article.[[3]](./Fenwick_tree#cite_note-:0-3)

 

A simple array of values is trivial (constant-time) to update but requires     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time to compute a prefix sum or search for a prefix length.

 

An array of prefix sums can return a prefix sum in constant time, and search for a prefix length in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, but requires     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time to update one of the values.

 

A Fenwick tree allows all three operations to be performed in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time.  This is achieved by representing the values as a [tree](./Tree_(data_structure)) with     n + 1   {\displaystyle n+1}  ![{\displaystyle n+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a135e65a42f2d73cccbfc4569523996ca0036f1) nodes where each node in the tree stores the sum of the values from the index of its parent (exclusive) up to the index of the node (inclusive). The tree itself is [implicit](./Implicit_data_structure) and can be stored as an array of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) values, with the implicit root node omitted from the array. The tree structure allows the operations of value retrieval, value update, prefix sum, and range sum to be performed using only     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) node accesses.

 

## Motivation

 Main article: [Prefix sums § Applications](./Prefix_sums#Applications) 

Given an array of values, it is sometimes desirable to calculate the [running total](./Running_total) of values up to each index according to some [associative](./Associative_property) [binary operation](./Binary_operation) (addition on integers being by far the most common). Fenwick trees provide a method to query the running total at any index, or prefix sum, while allowing changes to the underlying value array and having all further queries reflect those changes.

 

Fenwick trees are particularly designed to implement [adaptive arithmetic coding](./Arithmetic_coding#Adaptive_arithmetic_coding), which maintains counts of each symbol produced and needs to convert those to the [cumulative probability](./Cumulative_probability) of a symbol less than a given symbol.  Development of operations it supports were primarily motivated by use in that case.[*[citation needed](./Wikipedia:Citation_needed)*]

 

## Description

 

A Fenwick tree is an [implicit tree](./Implicit_data_structure) where nodes are consecutively numbered, and parent-child relationships are determined by arithmetic on the node indexes.

 

An important function in this index arithmetic is the *least significant set bit*.  This is the greatest [power of two](./Power_of_two) which divides an index     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20).  This is the power of two (1, 2, 4, 8, ...) and not the exponent (0, 1, 2, 3, ...).  It can be efficiently computed in [two's complement](./Two's_complement) arithmetic as     lsb ⁡ ⁡  ( i ) = i  & &   − −  i   {\displaystyle \operatorname {lsb} (i)=i\mathbin {\&} -i}  ![{\displaystyle \operatorname {lsb} (i)=i\mathbin {\&} -i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4d5068ef2f1b50008c7c306209f8582447088287) (where & denotes [bitwise AND](./Bitwise_AND#AND)).

 

A Fenwick tree is most easily understood using a [one-based array](./One-based_indexing)     A [ n ]   {\displaystyle A[n]}  ![{\displaystyle A[n]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cfee88a7c9f8b8114d883b3586b5f1c239fbddf8) with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) values.  Using [half-open interval](./Half-open_interval#Definitions_and_terminology) syntax, let     A ( i , j ] = { A [ k ]  }  k = i + 1   j   ,   {\displaystyle A(i,j]=\{A[k]\}_{k=i+1}^{j},}  ![{\displaystyle A(i,j]=\{A[k]\}_{k=i+1}^{j},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a5397bb913673d144021a26260d660dbf41c5bb) the range from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) (exclusive) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) (inclusive).  The corresponding Fenwick array     F [ n ]   {\displaystyle F[n]}  ![{\displaystyle F[n]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ffefdbddd63e319908aa7e0825bdf9f50f3e6f5) stores the [range sums](./Range_query_(computer_science))      F [ i ] = ∑ ∑  A ( i − −  lsb ⁡ ⁡  ( i ) , i ]    {\displaystyle \textstyle F[i]=\sum A(i-\operatorname {lsb} (i),i]}  ![{\displaystyle \textstyle F[i]=\sum A(i-\operatorname {lsb} (i),i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49e17d582f03104a29fd82528d88e08db87976ce).  That is, the sum of     lsb ⁡ ⁡  ( i )   {\displaystyle \operatorname {lsb} (i)}  ![{\displaystyle \operatorname {lsb} (i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a0fb5b29dca359fa0737d878fcc6975b581df99) values ending with and including     A [ i ]   {\displaystyle A[i]}  ![{\displaystyle A[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a0d7a8a3371fad84f7032042e8d1e1caf6aa15e).

 

A fictitious node 0 is used in some descriptions, but is never actually accessed and need not be explicitly stored.      lsb ⁡ ⁡  ( 0 ) = ∞ ∞  ,   {\displaystyle \operatorname {lsb} (0)=\infty ,}  ![{\displaystyle \operatorname {lsb} (0)=\infty ,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ed2fbdaf8f76453215cfbbab246c43d19d3ace6) but the value is never actually needed.      F [ 0 ]   {\displaystyle F[0]}  ![{\displaystyle F[0]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b3fdacfc59c64d094ad6b32ceda08d6f351ca84) may be considered to contain the sum of the empty range     A ( 0 , 0 ] = { }   {\displaystyle A(0,0]=\{\}}  ![{\displaystyle A(0,0]=\{\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e487ed00e2afb588e336992edc92a99d2d061663) with value 0.

 

A "Fenwick tree" is actually *three* implicit trees over the same array: the *interrogation tree* used for translating indexes to prefix sums, the *update* tree used for updating elements, and the *search tree* for translating prefix sums to indexes (rank queries).[[4]](./Fenwick_tree#cite_note-4)  The first two are normally walked upwards, while the third is usually walked downwards.

 

### The interrogation tree

 

The interrogation tree is defined so that the parent of node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is     i − −  lsb ⁡ ⁡  ( i ) = i  & &   ( i − −  1 )   {\displaystyle i-\operatorname {lsb} (i)=i\mathbin {\&} (i-1)}  ![{\displaystyle i-\operatorname {lsb} (i)=i\mathbin {\&} (i-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8f86430e8e2a2232ee91995083730913ba2e210e).  For example, the parent of 6 = 1102 is 4 = 1002.  Implicit node 0 is the root.

 

Each level     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) of the tree contains nodes with indices corresponding to sums of     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) distinct powers of 2 (with     k = 0   {\displaystyle k=0}  ![{\displaystyle k=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6307c8a99dad7d0bcb712352ae0a748bd99a038b) representing an empty sum 0). For example, level     k = 1   {\displaystyle k=1}  ![{\displaystyle k=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c035ffa69b5bca8bf2d16c3da3aaad79a8bcbfa) contains nodes     1 =  2  0   , 2 =  2  1   , 4 =  2  2   , . . .   {\displaystyle 1=2^{0},2=2^{1},4=2^{2},...}  ![{\displaystyle 1=2^{0},2=2^{1},4=2^{2},...}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b287102f65d1f46b8b001bdf670bb906a2f654ee) and level     k = 2   {\displaystyle k=2}  ![{\displaystyle k=2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0bd301789e1f25a3da4be297ff637754ebee5f5d) contains nodes     3 =  2  1   +  2  0   , 5 =  2  2   +  2  0   , 6 =  2  2   +  2  1   , . . .   {\displaystyle 3=2^{1}+2^{0},5=2^{2}+2^{0},6=2^{2}+2^{1},...}  ![{\displaystyle 3=2^{1}+2^{0},5=2^{2}+2^{0},6=2^{2}+2^{1},...}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d676f2e3601a5f5e1d5c04601939078eeb782a7)

 

Node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) has      log  2   ⁡ ⁡  ( lsb ⁡ ⁡  ( i ) )   {\displaystyle \log _{2}(\operatorname {lsb} (i))}  ![{\displaystyle \log _{2}(\operatorname {lsb} (i))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/32528af42b80c6d69df0653b6c0596ece4dc7634) children (    i + 1 , i + 2 , i + 4 , . . . , i + lsb ⁡ ⁡  ( i )  /  2   {\displaystyle i+1,i+2,i+4,...,i+\operatorname {lsb} (i)/2}  ![{\displaystyle i+1,i+2,i+4,...,i+\operatorname {lsb} (i)/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/60df1c8659d1ea0a2ebdce78e9f2d2a7ac11a8e5)), and     lsb ⁡ ⁡  ( i )   {\displaystyle \operatorname {lsb} (i)}  ![{\displaystyle \operatorname {lsb} (i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a0fb5b29dca359fa0737d878fcc6975b581df99) total descendants.  (These numbers include nodes greater than     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), which are omitted and never accessed.)

 

The below diagram shows the structure of a 16-node Fenwick tree's interrogation tree, including the root, so it corresponds to a 15-element array A:

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/70/16-node_Fenwick_tree.svg/500px-16-node_Fenwick_tree.svg.png)](./File:16-node_Fenwick_tree.svg)Depiction of a 16-node Fenwick interrogation tree containing range sums of a 15-node array A 

To find the prefix sum     A [ 1 ] + ⋯ ⋯  + A [ i ]   {\displaystyle A[1]+\cdots +A[i]}  ![{\displaystyle A[1]+\cdots +A[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d15a22ceaeac29c80817541c26bc02238c55ccb0), sum the values in     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), its parent, its parent's parent, and so on up to (but not including) the root.  To compute a range sum     A [ i ] + ⋯ ⋯  + A [ j ]   {\displaystyle A[i]+\cdots +A[j]}  ![{\displaystyle A[i]+\cdots +A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce9a7a1d7259eb0056fc37f9bed9219049cb8cde), subtract the prefix sums for     i − −  1   {\displaystyle i-1}  ![{\displaystyle i-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2ca5c639f26340e0e80f5883cc93a00254513c) and     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0).

 

This can be optimized by stopping at their first common ancestor.  An extreme example is asking for a single entry     A [ j ]   {\displaystyle A[j]}  ![{\displaystyle A[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c385fd9b0f771529e587f216f3f15d52bb85ef6).  In this case, the common ancestor of     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) and     i = j − −  1   {\displaystyle i=j-1}  ![{\displaystyle i=j-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/908d968f4aae99bc3aecc3000fb2c11361e90204) is     j − −  lsb ⁡ ⁡  ( j )   {\displaystyle j-\operatorname {lsb} (j)}  ![{\displaystyle j-\operatorname {lsb} (j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7916dd9872016f17f2a066b8f51ed89a649c0b4), so start with     F [ j ]   {\displaystyle F[j]}  ![{\displaystyle F[j]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/968ca52db4022a8e1fffef47585ab82f81a35af9) and then, as long as     i ≠ ≠  j − −  lsb ⁡ ⁡  ( j )   {\displaystyle i\neq j-\operatorname {lsb} (j)}  ![{\displaystyle i\neq j-\operatorname {lsb} (j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/300df256a236ccfd0bf87fe0753f331c36a93824), subtract     F [ i ]   {\displaystyle F[i]}  ![{\displaystyle F[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad0a35222782e478aa3b0aad79d235c125965c73) and update `i := i - lsb(i)`.

 

### The update tree

 

The update tree is the mirror image of the interrogation tree.  The parent of node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) is     i + lsb ⁡ ⁡  ( i ) = ( i   |   ( i − −  1 ) ) + 1   {\displaystyle i+\operatorname {lsb} (i)=(i\mathbin {|} (i-1))+1}  ![{\displaystyle i+\operatorname {lsb} (i)=(i\mathbin {|} (i-1))+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/725c88bf3afea3ea060576e3c3610cfc29acf1ac) (where | denotes [bitwise OR](./Bitwise_OR#OR)).  For example, the parent of 6 = 1102 is 8 = 10002.

 

This conceptual tree is infinite, but only the part with indexes up to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is stored or used.  Excluding the fictitious nodes with indexes greater than     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) it will be a forest of disjoint trees, one for each bit set in the binary representation of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b).

 

Here, a node's ancestors are all nodes whose range sums include its own.  For example,     F [ 6 ]   {\displaystyle F[6]}  ![{\displaystyle F[6]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ab5a1b91678ae3b065d0e95dd2411bb5cfa6d9b5) holds the sum of     A ( 4 , 6 ]   {\displaystyle A(4,6]}  ![{\displaystyle A(4,6]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cd0bc5db2d85ad20553e156c65404af258d51822),     F [ 8 ]   {\displaystyle F[8]}  ![{\displaystyle F[8]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c0e534e2617fff2a4cefb0d5d89e4b5bf28e516b) holds the sum of     A ( 0 , 8 ]   {\displaystyle A(0,8]}  ![{\displaystyle A(0,8]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c447eb67cce62457e1af2ddf905df30ed6e1bd21), and so on.

 

To modify one of the values     A [ i ]   {\displaystyle A[i]}  ![{\displaystyle A[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a0d7a8a3371fad84f7032042e8d1e1caf6aa15e), add the change to     F [ i ]   {\displaystyle F[i]}  ![{\displaystyle F[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad0a35222782e478aa3b0aad79d235c125965c73), then     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)'s parent, then its grandparent, and so on, until the index exceeds     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b).

 

### The search tree

 

Unlike the other two trees, the search tree is a [binary tree](./Binary_tree), arranged in an order [Knuth](./Donald_Knuth) calls a "sideways heap".[[5]](./Fenwick_tree#cite_note-5)   Each node is assigned a height equal to the number of trailing zeros in the binary representation of its index, with the parent and children being the numerically closest index(es) of the adjacent height.  Nodes with odd indexes (    lsb ⁡ ⁡  ( i ) = 1   {\displaystyle \operatorname {lsb} (i)=1}  ![{\displaystyle \operatorname {lsb} (i)=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fcb7b3d10c38649b9ce750720b65cf18ea61e80b)) are leaves.  Nodes with even indexes have the closest two nodes of the next-lowest index as children,     i ± ±  lsb ⁡ ⁡  ( i )  /  2   {\displaystyle i\pm \operatorname {lsb} (i)/2}  ![{\displaystyle i\pm \operatorname {lsb} (i)/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bcc4a9853432929bfaa79865d5c98fe5ec5cc122).    Node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)'s parent in the search tree is     ( i − −  lsb ⁡ ⁡  ( i ) )   |   ( 2 ⋅ ⋅  lsb ⁡ ⁡  ( i ) )   {\displaystyle (i-\operatorname {lsb} (i))\mathbin {|} (2\cdot \operatorname {lsb} (i))}  ![{\displaystyle (i-\operatorname {lsb} (i))\mathbin {|} (2\cdot \operatorname {lsb} (i))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26eed4aba655ec17e3e0851222bf0fb4316f3a11).

 

For example, the children of 6 = 1102 are 5 = 1012 and 7 = 1112, and its parent is 4 = 1002.

 

Although this tree is potentially infinite, we may define its root to be the highest *existing* node, whose index is the greatest power of 2 less than or equal to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b).

 

It is possible for a node to have a fictitious parent with an index greater than     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) yet still have an existing grandparent.  If the example above applied to a 5-node tree, then node 5 would have a fictitious parent 6, but an existing grandparent 4.

 

The search tree may be considered a combination of the previous two trees.  A node's left subtree contains all of its descendants in the update tree, while its right subtree contains all of its descendants in the interrogation tree.  A node's parent in the search tree is either its interrogation or update parent (depending on whether the node is a right or left child, respectively), and the other type of parent may be found by multiple upward steps in the search tree.

 

However, upward traversals in the search tree are uncommon; its primary use is to perform rank queries: given a prefix sum, at what index does it appear?  This is done by a *downward* traversal through the search tree.  During the traversal, three variables are maintained: The current node's index, the rank being sought in the subtree rooted at the current node, and a "fallback index" to be returned if the rank sought is greater than can be found in the subtree.

 

Initially, the current node is the root, the rank sought is the original query, and the fallback index is a [special "overflow" value](./Sentinel_value) indicating that the rank is not in the tree.  (Depending on the application,     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) or     n + 1   {\displaystyle n+1}  ![{\displaystyle n+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a135e65a42f2d73cccbfc4569523996ca0036f1) might be used for this purpose.)

 

Each step, either the current node is a fictitious node (index greater than     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)), or we must decide if the position sought is to the left or right of the end of the current node.  If the rank sought is less than the Fenwick array value     F [ i ]   {\displaystyle F[i]}  ![{\displaystyle F[i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad0a35222782e478aa3b0aad79d235c125965c73) for the current node, we must search its left subtree.  If it is greater, search its right subtree.  If it is equal, the direction chosen depends on how you wish to handle searches for sums lying exactly between two nodes.

 

These three possibilities are then further divided based on whether the current node is a leaf or not:

 
- If the current node is a leaf and:

- the target is in its (empty) left subtree, return the current index.
- it is fictitious *or* the target is in its right subtree, return the fallback index.

- If the current node is *not* a leaf and:

- it is fictitious, search for the same rank in its left subtree with an unchanged fallback index.
- the target is in its left subtree, search for the same rank in its left subtree with the current index as the fallback index.
- the target is in its right subtree, search for the target rank minus the current node's value in the right subtree, with an unchanged fallback index.

 

## Pseudocode

 

A simple [pseudocode](./Pseudocode) implementation of the two main operations on a Fenwick tree—query and update—is as following:

 
```
function query(tree, index) is
    sum := 0
    while index > 0 do
        sum += tree[index]
        index -= lsb(index)
    return sum

function update(tree, index, value) is
    while index < size(tree) do
        tree[index] += value
        index += lsb(index)
```
 

The function      lsb  ( n )   {\displaystyle {\text{lsb}}(n)}  ![{\displaystyle {\text{lsb}}(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/796a23e8aa317a53fbd181181f2395a32f1faab9) computes the *least significant set bit* of the given     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) or, equivalently, the largest [power of two](./Power_of_two) that is also a divisor of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b). For example,      lsb  ( 20 ) = 4   {\displaystyle {\text{lsb}}(20)=4}  ![{\displaystyle {\text{lsb}}(20)=4}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e68e1e531e301310900e5378bc7f59bd8332e7f), as shown in its binary representation:      lsb  ( 10   1    00  2   ) =  100  2   = 4   {\displaystyle {\text{lsb}}(10{\textbf {1}}00_{2})=100_{2}=4}  ![{\displaystyle {\text{lsb}}(10{\textbf {1}}00_{2})=100_{2}=4}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47470cb96e60da408fd9f4844d3f7d615970de38). This function can be simply implemented in code through a [bitwise AND](./Bitwise_AND) operation: `lsb(n) = n & (-n)`, assuming [two's complement](./Two's_complement) negation.[[3]](./Fenwick_tree#cite_note-:0-3)

 

### Construction

 

One naïve algorithm to construct a Fenwick tree consists of initializing the tree with null values and updating each index individually. This solution works in     O ( n log ⁡ ⁡   n  )   {\displaystyle O(n\log {n})}  ![{\displaystyle O(n\log {n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b5ea2d55d8c31feb17ce14f35da4c93f94982b3) time, but an     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) construction is possible:[[6]](./Fenwick_tree#cite_note-cp4-6)

 
```
function construct(values) is
    tree := values
    for index from 1 to size(tree) do
        parentIndex := index + lsb(index)
        if parentIndex ≤ size(tree) then
            tree[parentIndex] += tree[index]
    return tree
```
 

## See also

 
- [Order statistic tree](./Order_statistic_tree)
- [Prefix sums](./Prefix_sums)
- [Segment tree](./Segment_tree)

 

## References

  
1. [↑](./Fenwick_tree#cite_ref-1) Boris Ryabko (1989). ["A fast on-line code"](http://boris.ryabko.net/dan1989.pdf) (PDF). *Soviet Math. Dokl*. **39** (3): 533–537. [Archived](https://web.archive.org/web/20190717074430/http://boris.ryabko.net/dan1989.pdf) (PDF) from the original on 2019-07-17. Retrieved 2019-07-17.
2. [↑](./Fenwick_tree#cite_ref-2) Boris Ryabko (1992). ["A fast on-line adaptive code"](http://boris.ryabko.net/ryabko1992.pdf) (PDF). *IEEE Transactions on Information Theory*. **28** (1): 1400–1404. [Archived](https://web.archive.org/web/20190714141801/http://boris.ryabko.net/ryabko1992.pdf) (PDF) from the original on 2019-07-14. Retrieved 2019-07-14.
3. [1](./Fenwick_tree#cite_ref-:0_3-0) [2](./Fenwick_tree#cite_ref-:0_3-1) Peter M. Fenwick (1994). "A new data structure for cumulative frequency tables". *Software: Practice and Experience*. **24** (3): 327–336. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.14.8917](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.14.8917). [doi](./Doi_(identifier)):[10.1002/spe.4380240306](https://doi.org/10.1002%2Fspe.4380240306). [S2CID](./S2CID_(identifier)) [7519761](https://api.semanticscholar.org/CorpusID:7519761).
4. [↑](./Fenwick_tree#cite_ref-4) Marchini, Stefano; [Vigna, Sebastiano](./Sebastiano_Vigna) (14 October 2019). "Compact Fenwick trees for dynamic ranking and selection". [arXiv](./ArXiv_(identifier)):[1904.12370](https://arxiv.org/abs/1904.12370) [[cs.DS](https://arxiv.org/archive/cs.DS)].  Extensive discussion of practical implementation details.
5. [↑](./Fenwick_tree#cite_ref-5) [Knuth, Donald](./Donald_Knuth) (2011). *Combinatorial Algorithms, Part 1*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 4A. Upper Saddle River, NJ: Addison-Wesley Professional. pp. 164–165.
6. [↑](./Fenwick_tree#cite_ref-cp4_6-0) Halim, Steven; Halim, Felix; Effendy, Suhendry (3 December 2018). *Competitive Programming 4*. Vol. 1. Lulu Press, Incorporated. [ISBN](./ISBN_(identifier)) [978-1-716-74552-2](./Special:BookSources/978-1-716-74552-2).

 

## External links

 
- [A tutorial on Fenwick Trees on TopCoder](https://www.topcoder.com/community/data-science/data-science-tutorials/binary-indexed-trees/)
- [An article on Fenwick Trees on Algorithmist](http://www.algorithmist.com/index.php/Fenwick_tree)
- [An entry on Fenwick Trees on Polymath wiki](http://michaelnielsen.org/polymath1/index.php?title=Updating_partial_sums_with_Fenwick_tree)
- [stack exchange](https://cs.stackexchange.com/q/10538)

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |