---
source: https://en.wikipedia.org/wiki/AVL_tree
fetched: 2026-06-19
---

Self-balancing binary search tree 
|  | This article needs editing tocomply with Wikipedia'sManual of Style.Please helpimprove the content.(November 2021)(Learn how and when to remove this message) |
| --- | --- |

 
| AVL tree |
| --- |
| Type | Tree |
| Invented | 1962 |
| Invented by | Georgy Adelson-VelskyandEvgenii Landis |
| Complexities inbig O notation |
| Space complexitySpaceO(n){\displaystyle {\text{O}}(n)}Time complexityFunctionAmortizedWorst caseSearchO(log⁡n){\displaystyle {\text{O}}(\log n)}[1]O(log⁡n){\displaystyle {\text{O}}(\log n)}[1]InsertO(log⁡n){\displaystyle {\text{O}}(\log n)}[1]O(log⁡n){\displaystyle {\text{O}}(\log n)}[1]DeleteO(log⁡n){\displaystyle {\text{O}}(\log n)}[1]O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | Space complexity | Space |  | O(n){\displaystyle {\text{O}}(n)} |  | Time complexity | Function |  | Amortized | Worst case | Search |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | Insert |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | Delete |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] |
| Space complexity |
| Space |  | O(n){\displaystyle {\text{O}}(n)} |  |
| Time complexity |
| Function |  | Amortized | Worst case |
| Search |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] |
| Insert |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] |
| Delete |  | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] | O(log⁡n){\displaystyle {\text{O}}(\log n)}[1] |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fd/AVL_Tree_Example.gif/250px-AVL_Tree_Example.gif)](./File:AVL_Tree_Example.gif)Animation showing the insertion of several elements into an AVL tree. It includes left, right, left-right and right-left rotations. [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/ad/AVL-tree-wBalance_K.svg/330px-AVL-tree-wBalance_K.svg.png)](./File:AVL-tree-wBalance_K.svg)Fig. 1: AVL tree with balance factors (green) 

In [computer science](./Computer_science), an **AVL tree** (named after inventors **A**delson-**V**elsky and **L**andis) is a [self-balancing binary search tree](./Self-balancing_binary_search_tree). In an AVL tree, the heights of the two [child](./Child_nodes) subtrees of any node differ by not more than one; if at any time they differ by more than one, rebalancing is done to restore this property. Lookup, insertion, and deletion all take [O](./Big_O_notation)(log *n*) time in both the average and worst cases, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of nodes in the tree prior to the operation. Insertions and deletions may require the tree to be rebalanced by one or more [tree rotations](./Tree_rotation).

 

The AVL tree is named after its two [Soviet](./Soviet_Union) inventors, [Georgy Adelson-Velsky](./Georgy_Adelson-Velsky) and [Evgenii Landis](./Evgenii_Landis), who published it in their 1962 paper "An algorithm for the organization of information".[[2]](./AVL_tree#cite_note-2)  It is the first self-balancing binary search tree [data structure](./Data_structure) to be invented.[[3]](./AVL_tree#cite_note-3)

 

AVL trees are often compared with [red–black trees](./Red–black_tree) because both support the same set of operations and take      O  ( log ⁡ ⁡  n )   {\displaystyle {\text{O}}(\log n)}  ![{\displaystyle {\text{O}}(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67697a0b44080bbf967c00d60bf4aac79f9ce385) time for the basic operations. For lookup-intensive applications, AVL trees are faster than red–black trees because they are more strictly balanced.[[4]](./AVL_tree#cite_note-Pfaff1-4) Similar to red–black trees, AVL trees are height-balanced. Both are, in general, neither [weight-balanced](./Weight-balanced_tree) nor     μ μ    {\displaystyle \mu }  ![{\displaystyle \mu }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fd47b2a39f7a7856952afec1f1db72c67af6161)-balanced for any     μ μ  ≤ ≤     1 2      {\displaystyle \mu \leq {\tfrac {1}{2}}}  ![{\displaystyle \mu \leq {\tfrac {1}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e5641d5a805f727ffe5bb450abd59582f57b729);[[5]](./AVL_tree#cite_note-5) that is, sibling nodes can have hugely differing numbers of descendants.

 

## Definition

 

### Balance factor

 

In a [binary tree](./Binary_tree) the *balance factor* of a node *X* is defined to be the height difference

      B F  ( X ) :=  H e i g h t  (  R i g h t S u b t r e e  ( X ) ) − −   H e i g h t  (  L e f t S u b t r e e  ( X ) )   {\displaystyle \mathrm {BF} (X):=\mathrm {Height} (\mathrm {RightSubtree} (X))-\mathrm {Height} (\mathrm {LeftSubtree} (X))}  ![{\displaystyle \mathrm {BF} (X):=\mathrm {Height} (\mathrm {RightSubtree} (X))-\mathrm {Height} (\mathrm {LeftSubtree} (X))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/94f569fe4963054b930cd9711632a419dcf7302c)[[6]](./AVL_tree#cite_note-Knuth-6): 459  

of its two child sub-trees rooted by node *X*.

 

A binary tree is defined to be an *AVL tree* if

      B F  ( X ) ∈ ∈  { − −  1 , 0 , 1 }   {\displaystyle \mathrm {BF} (X)\in \{-1,0,1\}}  ![{\displaystyle \mathrm {BF} (X)\in \{-1,0,1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/35a6035e1e72cfa0f1ce381ad40dd0667702c801) 

holds for every node *X* in the tree.

 

A node *X* with      B F  ( X ) < 0   {\displaystyle \mathrm {BF} (X)<0}  ![{\displaystyle \mathrm {BF} (X)<0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4e13c74c4dc9cef9f2eff704a2ad158bfce8618) is called "left-heavy", one with      B F  ( X ) > 0   {\displaystyle \mathrm {BF} (X)>0}  ![{\displaystyle \mathrm {BF} (X)>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/678446e4fef5fdbbe1793f6026ef16427be064bf) is called "right-heavy", and one with      B F  ( X ) = 0   {\displaystyle \mathrm {BF} (X)=0}  ![{\displaystyle \mathrm {BF} (X)=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c012e26462394ab5913f73af7a223df107eb1c5c) is sometimes simply called "balanced".

 

### Properties

 

Balance factors can be kept up-to-date by knowing the previous balance factors and the change in height – it is not necessary to know the absolute height. For holding the AVL balance information, two bits per node are sufficient.[[7]](./AVL_tree#cite_note-7)

 

The height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) (counted as the maximal number of levels) of an AVL tree with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) nodes lies in the interval:[[6]](./AVL_tree#cite_note-Knuth-6): 460 

      log  2   ⁡ ⁡  ( n + 1 ) ≤ ≤  h <  log  φ φ    ⁡ ⁡  ( n + 2 ) + b   {\displaystyle \log _{2}(n+1)\leq h<\log _{\varphi }(n+2)+b}  ![{\displaystyle \log _{2}(n+1)\leq h<\log _{\varphi }(n+2)+b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2fd9a7db05780c8576235500834aa15b0d341dfd) 

where     φ φ  :=     1 +   5    2    ≈ ≈  1.618   {\displaystyle \varphi :={\tfrac {1+{\sqrt {5}}}{2}}\approx 1.618}  ![{\displaystyle \varphi :={\tfrac {1+{\sqrt {5}}}{2}}\approx 1.618}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48d4e4826360b780d733e8a0fa97caf8452423a4)  is the [golden ratio](./Golden_ratio) and     b :=     log  2   ⁡ ⁡  5   2  log  2   ⁡ ⁡  φ φ     − −  2 ≈ ≈   − −  0.3277.   {\displaystyle b:={\frac {\log _{2}5}{2\log _{2}\varphi }}-2\approx \;-0.3277.}  ![{\displaystyle b:={\frac {\log _{2}5}{2\log _{2}\varphi }}-2\approx \;-0.3277.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a2f6b70e5bdce693c11fc1adeaa86e37b87373f)
This is because an AVL tree of height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) contains at least      F  h + 2   − −  1   {\displaystyle F_{h+2}-1}  ![{\displaystyle F_{h+2}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce70a208f6cdc09c06950e5550ccfb1ff9bbc1d3) nodes where     {  F  n    }  n ∈ ∈   N      {\displaystyle \{F_{n}\}_{n\in \mathbb {N} }}  ![{\displaystyle \{F_{n}\}_{n\in \mathbb {N} }}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5d4c26770bdfae8e3102d1f96418c4d2380070ee) is the [Fibonacci sequence](./Fibonacci_number) with the seed values      F  1   =  F  2   = 1.   {\displaystyle F_{1}=F_{2}=1.}  ![{\displaystyle F_{1}=F_{2}=1.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/12fe8fa5eea968e7d0e72ec5e604074aca6215f6)

 

## Operations

 

Read-only operations of an AVL tree involve carrying out the same actions as would be carried out on an unbalanced [binary search tree](./Binary_search_tree), but modifications have to observe and restore the height balance of the sub-trees.

 

### Searching

 

Searching for a specific key in an AVL tree can be done the same way as that of any balanced or unbalanced [binary search tree](./Binary_search_tree#Searching).[[8]](./AVL_tree#cite_note-dixit-mastering-data-structures-8): ch. 8  In order for search to work effectively it has to employ a comparison function which establishes a [total order](./Total_order) (or at least a [total preorder](./Weak_ordering#Total_preorders)) on the set of keys.[[9]](./AVL_tree#cite_note-brass-advanced-data-structures-9): 23  The number of comparisons required for successful search is limited by the height *h* and for unsuccessful search is very close to *h*, so both are in O(log *n*), where n is the number of nodes in the tree.[[10]](./AVL_tree#cite_note-hubbard-outline-theory-problems-10): 216 

 

### Traversal

 

As a read-only operation the traversal of an AVL tree functions the same way as on any other binary tree. Exploring all *n* nodes of the tree visits each link exactly twice: one downward visit to enter the subtree rooted by that node, another visit upward to leave that node's subtree after having explored it.

 

Once a node has been found in an AVL tree, the *next* or *previous* node can be accessed in [amortized](./Amortized_complexity) constant time.[[11]](./AVL_tree#cite_note-Pfaff-11): 58  Some instances of exploring these "nearby" nodes require traversing up to *h* ∝ log(*n*) links (particularly when navigating from the rightmost leaf of the root's left subtree to the root or from the root to the leftmost leaf of the root's right subtree; in the AVL tree of figure 1, navigating from node P to the next-to-the-right node Q takes 3 steps). Since there are *n*−1 links in any tree, the amortized cost is 2×(*n*−1)/*n*, or approximately 2.

 

### Insert

 

When inserting a node into an AVL tree, you initially follow the same process as inserting into a [Binary Search Tree](./Binary_Search_Tree). If the tree is empty, then the node is inserted as the root of the tree. If the tree is not empty, then we go down the root, and recursively go down the tree searching for the location to insert the new node. This traversal is guided by the comparison function. In this case, the node always replaces a NULL reference (left or right) of an external node in the tree i.e., the node is either made a left-child or a right-child of the external node.

 

After this insertion, if a tree becomes unbalanced, only ancestors of the newly inserted node are unbalanced. This is because only those nodes have their sub-trees altered.[[12]](./AVL_tree#cite_note-12) So it is necessary to check each of the node's ancestors for consistency with the invariants of AVL trees: this is called "retracing". This is achieved by considering the [balance factor](./AVL_tree#Balance_factor) of each node.[[6]](./AVL_tree#cite_note-Knuth-6): 458–481  [[11]](./AVL_tree#cite_note-Pfaff-11): 108 

 

Since with a single insertion the height of an AVL subtree cannot increase by more than one, the temporary balance factor of a node after an insertion will be in the range [–2,+2]. For each node checked, if the temporary balance factor remains in the range from –1 to +1 then only an update of the balance factor and no rotation is necessary. However, if the temporary balance factor is ±2, the subtree rooted at this node is AVL unbalanced, and a rotation is needed.[[9]](./AVL_tree#cite_note-brass-advanced-data-structures-9): 52  With insertion as the code below shows, the adequate rotation immediately perfectly [rebalances](./AVL_tree#Rebalancing) the tree.

 

In figure 1, by inserting the new node Z as a child of node X the height of that subtree Z increases from 0 to 1.

 [Invariant](./Loop_invariant) of the retracing loop for an insertion 

The height of the subtree rooted by Z has increased by 1. It is already in AVL shape.

  
| Example code for an insert operation |
| --- |
| for(X=parent(Z);X!=null;X=parent(Z)){// Loop (possibly up to the root)// BF(X) has to be updated:if(Z==right_child(X)){// The right subtree increasesif(BF(X)>0){// X is right-heavy// ==> the temporary BF(X) == +2// ==> rebalancing is required.G=parent(X);// Save parent of X around rotationsif(BF(Z)<0)// Right Left Case  (see figure 3)N=rotate_RightLeft(X,Z);// Double rotation: Right(Z) then Left(X)else// Right Right Case (see figure 2)N=rotate_Left(X,Z);// Single rotation Left(X)// After rotation adapt parent link}else{if(BF(X)<0){BF(X)=0;// Z’s height increase is absorbed at X.break;// Leave the loop}BF(X)=+1;Z=X;// Height(Z) increases by 1continue;}}else{// Z == left_child(X): the left subtree increasesif(BF(X)<0){// X is left-heavy// ==> the temporary BF(X) == -2// ==> rebalancing is required.G=parent(X);// Save parent of X around rotationsif(BF(Z)>0)// Left Right CaseN=rotate_LeftRight(X,Z);// Double rotation: Left(Z) then Right(X)else// Left Left CaseN=rotate_Right(X,Z);// Single rotation Right(X)// After rotation adapt parent link}else{if(BF(X)>0){BF(X)=0;// Z’s height increase is absorbed at X.break;// Leave the loop}BF(X)=-1;Z=X;// Height(Z) increases by 1continue;}}// After a rotation adapt parent link:// N is the new root of the rotated subtree// Height does not change: Height(N) == old Height(X)parent(N)=G;if(G!=null){if(X==left_child(G))left_child(G)=N;elseright_child(G)=N;}elsetree->root=N;// N is the new root of the total treebreak;// There is no fall thru, only break; or continue;}// Unless loop is left via break, the height of the total tree increases by 1. |

 

In order to update the balance factors of all nodes, first observe that all nodes requiring correction lie from child to parent along the path of the inserted leaf. If the above procedure is applied to nodes along this path, starting from the leaf, then every node in the tree will again have a balance factor of −1, 0, or 1.

 

The retracing can stop if the balance factor becomes 0 implying that the height of that subtree remains unchanged.

 

If the balance factor becomes ±1 then the height of the subtree increases by one and the retracing needs to continue.

 

If the balance factor temporarily becomes ±2, this has to be repaired by an appropriate rotation after which the subtree has the same height as before (and its root the balance factor 0).

 

The time required is O(log *n*) for lookup, plus a maximum of O(log *n*) retracing levels (O(1) on average) on the way back to the root, so the operation can be completed in O(log *n*) time.[[9]](./AVL_tree#cite_note-brass-advanced-data-structures-9): 53 

 

### Delete

 

The preliminary steps for deleting a node are the same as for a [Binary search tree](./Binary_search_tree#Deletion).
There, the effective deletion of the subject node or the replacement node decreases the height of the corresponding child tree either from 1 to 0 or from 2 to 1, if that node had a child.

 

Starting at this subtree, it is necessary to check each of the ancestors for consistency with the invariants of AVL trees. This is called "retracing".

 

Since with a single deletion the height of an AVL subtree cannot decrease by more than one, the temporary balance factor of a node will be in the range from −2 to +2.
If the balance factor remains in the range from −1 to +1 it can be adjusted in accord with the AVL rules. If it becomes ±2 then the subtree is unbalanced and needs to be rotated. (Unlike insertion where a rotation always balances the tree, after delete, there may be BF(Z) ≠ 0 (see figures 2 and 3), so that after the appropriate single or double rotation the height of the rebalanced subtree decreases by one meaning that the tree has to be rebalanced again on the next higher level.) The various cases of rotations are described in section [Rebalancing](./AVL_tree#Rebalancing).

 Invariant of the retracing loop for a deletion 

The height of the subtree rooted by N has decreased by 1. It is already in AVL shape.

  
| Example code for a delete operation |
| --- |
| for(X=parent(N);X!=null;X=G){// Loop (possibly up to the root)G=parent(X);// Save parent of X around rotations// BF(X) has not yet been updated!if(N==left_child(X)){// the left subtree decreasesif(BF(X)>0){// X is right-heavy// ==> the temporary BF(X) == +2// ==> rebalancing is required.Z=right_child(X);// Sibling of N (higher by 2)b=BF(Z);if(b<0)// Right Left Case  (see figure 3)N=rotate_RightLeft(X,Z);// Double rotation: Right(Z) then Left(X)else// Right Right Case (see figure 2)N=rotate_Left(X,Z);// Single rotation Left(X)// After rotation adapt parent link}else{if(BF(X)==0){BF(X)=+1;// N’s height decrease is absorbed at X.break;// Leave the loop}N=X;BF(N)=0;// Height(N) decreases by 1continue;}}else{// (N == right_child(X)): The right subtree decreasesif(BF(X)<0){// X is left-heavy// ==> the temporary BF(X) == -2// ==> rebalancing is required.Z=left_child(X);// Sibling of N (higher by 2)b=BF(Z);if(b>0)// Left Right CaseN=rotate_LeftRight(X,Z);// Double rotation: Left(Z) then Right(X)else// Left Left CaseN=rotate_Right(X,Z);// Single rotation Right(X)// After rotation adapt parent link}else{if(BF(X)==0){BF(X)=-1;// N’s height decrease is absorbed at X.break;// Leave the loop}N=X;BF(N)=0;// Height(N) decreases by 1continue;}}// After a rotation adapt parent link:// N is the new root of the rotated subtreeparent(N)=G;if(G!=null){if(X==left_child(G))left_child(G)=N;elseright_child(G)=N;}elsetree->root=N;// N is the new root of the total treeif(b==0)break;// Height does not change: Leave the loop// Height(N) decreases by 1 (== old Height(X)-1)}// If (b != 0) the height of the total tree decreases by 1. |

 

The retracing can stop if the balance factor becomes ±1 (it must have been 0) meaning that the height of that subtree remains unchanged.

 

If the balance factor becomes 0 (it must have been ±1) then the height of the subtree decreases by one and the retracing needs to continue.

 

If the balance factor temporarily becomes ±2, this has to be repaired by an appropriate rotation. It depends on the balance factor of the sibling Z (the higher child tree in figure 2) whether the height of the subtree decreases by one –and the retracing needs to continue– or does not change (if Z has the balance factor 0) and the whole tree is in AVL-shape.

 

The time required is O(log *n*) for lookup, plus a maximum of O(log *n*) retracing levels (O(1) on average) on the way back to the root, so the operation can be completed in O(log *n*) time.

 

### Set operations and bulk operations

 

In addition to the single-element insert, delete and lookup operations, several set operations have been defined on AVL trees: [union](./Union_(set_theory)), [intersection](./Intersection_(set_theory)) and [set difference](./Set_difference). Then fast *bulk* operations on insertions or deletions can be implemented based on these set functions. These set operations rely on two helper operations, *Split* and *Join*. With the new operations, the implementation of AVL trees can be more efficient and highly-parallelizable.[[13]](./AVL_tree#cite_note-join-based-13)

 

The function *Join* on two AVL trees *t*1 and *t*2 and a key k will return a tree containing all elements in *t*1, *t*2 as well as k. It requires k to be greater than all keys in *t*1 and smaller than all keys in *t*2. If the two trees differ by height at most one, *Join* simply create a new node with left subtree *t*1, root k and right subtree *t*2. Otherwise, suppose that *t*1 is higher than *t*2 for more than one (the other case is symmetric). *Join* follows the right spine of *t*1 until a node c which is balanced with *t*2. At this point a new node with left child c, root k and right child *t*2 is created to replace c. The new node satisfies the AVL invariant, and its height is one greater than c. The increase in height can increase the height of its ancestors, possibly invalidating the AVL invariant of those nodes. This can be fixed either with a double rotation if invalid at the parent or a single left rotation if invalid higher in the tree, in both cases restoring the height for any further ancestor nodes. *Join* will therefore require at most two rotations. The cost of this function is the difference of the heights between the two input trees.

  
| Pseudocode implementation for the Join algorithm |
| --- |
| functionJoinRightAVL(TL, k, TR)
    (l, k', c) = expose(TL)if(Height(c) <= Height(TR)+1)
       T' = Node(c, k, TR)
       if (Height(T') <= Height(l)+1) thenreturnNode(l, k', T')
       elsereturnrotateLeft(Node(l, k', rotateRight(T')))elseT' = JoinRightAVL(c, k, TR)
        T'' = Node(l, k', T')if(Height(T') <= Height(l)+1)returnT''elsereturnrotateLeft(T'')functionJoinLeftAVL(TL, k, TR)
  /* symmetric to JoinRightAVL */functionJoin(TL, k, TR)if(Height(TL)>Height(TR)+1)returnJoinRightAVL(TL, k, TR)if(Height(TR)>Height(TL)+1)returnJoinLeftAVL(TL, k, TR)returnNode(TL, k, TR)Here Height(v) is the height of a subtree (node)v. (l,k,r) = expose(v) extractsv's left childl, the keykofv's root, and the right childr. Node(l,k,r) means to create a node of left childl, keyk, and right childr. |

 

To split an AVL tree into two smaller trees, those smaller than key k, and those greater than key k, first draw a path from the root by inserting k into the AVL. After this insertion, all values less than k will be found on the left of the path, and all values greater than k will be found on the right. By applying *Join*, all the subtrees on the left side are merged bottom-up using keys on the path as intermediate nodes from bottom to top to form the left tree, and the right part is asymmetric. The cost of *Split* is O(log *n*), order of the height of the tree.

  
| Pseudocode implementation for the Split algorithm |
| --- |
| functionSplit(T, k)if(T = nil) return (nil, false, nil)
    (L,m,R) = expose(T)if(k = m) return (L, true, R)if(k<m) 
       (L',b,R') = Split(L,k)return(L', b, Join(R', m, R))if(k>m) 
       (L',b,R') = Split(R, k)return(Join(L, m, L'), b, R')) |

 

The union of two AVL trees *t*1 and *t*2 representing sets A and B, is an AVL *t* that represents *A* ∪ *B*.

  
| Pseudocode implementation for the Union algorithm |
| --- |
| functionUnion(t1, t2):ift1= nil:returnt2ift2= nil:returnt1(t<, b, t>) = Split(t2, t1.root)returnJoin(Union(left(t1), t<), t1.root, Union(right(t1), t>))Here,Splitis presumed to return two trees: one holding the keys less its input key, one holding the greater keys. (The algorithm isnon-destructive, but an in-place destructive version exists as well.) |

 

The algorithm for intersection or difference is similar, but requires the *Join2* helper routine that is the same as *Join* but without the middle key. Based on the new functions for union, intersection or difference, either one key or multiple keys can be inserted to or deleted from the AVL tree. Since *Split* calls *Join* but does not deal with the balancing criteria of AVL trees directly, such an implementation is usually called the ["join-based" implementation](./Join-based_tree_algorithms).

 

The complexity of each of union, intersection and difference is      O   (  m log ⁡ ⁡   (    n m   + 1  )   )    {\displaystyle {\text{O}}\left(m\log \left({n \over m}+1\right)\right)}  ![{\displaystyle {\text{O}}\left(m\log \left({n \over m}+1\right)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/28e1b08290893e7c422b3c1f9fd947d702537019) for AVL trees of sizes     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) and     n  ( ≥ ≥  m )   {\displaystyle n\;(\geq m)}  ![{\displaystyle n\;(\geq m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a50642fb35bf03f2b430fa54c5a3838978b45f1). More importantly, since the recursive calls to union, intersection or difference are independent of each other, they can be executed [in parallel](./Parallel_programming) with a [parallel depth](./Analysis_of_parallel_algorithms)      O  ( log ⁡ ⁡  m log ⁡ ⁡  n )   {\displaystyle {\text{O}}(\log m\log n)}  ![{\displaystyle {\text{O}}(\log m\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f671b33d469696e8cc69445987eeedce0f5dff21).[[13]](./AVL_tree#cite_note-join-based-13) When     m = 1   {\displaystyle m=1}  ![{\displaystyle m=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6100c5ebd48c6fd848709f2be624465203eb173), the join-based implementation has the same computational DAG as single-element insertion and deletion.

 

## Rebalancing

 

If during a modifying operation the height difference between two child subtrees changes, this may, as long as it is < 2, be reflected by an adaption of the balance information at the parent. During insert and delete operations a (temporary) height difference of 2 may arise, which means that the parent subtree has to be "rebalanced". The given repair tools are the so-called [tree rotations](./Tree_rotation), because they move the keys only "vertically", so that the ("horizontal") in-order sequence of the keys is fully preserved (which is essential for a binary-search tree).[[6]](./AVL_tree#cite_note-Knuth-6): 458–481  [[11]](./AVL_tree#cite_note-Pfaff-11): 33 

 

Let X be the node that has a (temporary) balance factor of −2 or +2. Its left or right subtree was modified. Let Z be the child with the higher subtree (see figures 2 and 3). Note that both children are in AVL shape by [induction hypothesis](./Mathematical_induction).

 

In case of insertion this insertion has happened to one of Z's children in a way that Z's height has increased.
In case of deletion this deletion has happened to the sibling t1 of Z in a way so that t1's height being already lower has decreased. (This is the only case where Z's balance factor may also be 0.)

 

There are four possible variants of the violation:

 
|  | Right Right | ⟹ Z is aright | child of its parent X and BF(Z) ≥ 0 |
| --- | --- | --- | --- |
|  | Left Left | ⟹ Z is aleft | child of its parent X and BF(Z) ≤ 0 |
|  | Right Left | ⟹ Z is aright | child of its parent X and BF(Z) < 0 |
|  | Left Right | ⟹ Z is aleft | child of its parent X and BF(Z) > 0 |

 

And the rebalancing is performed differently:

 
|  | Right Right | ⟹ X is rebalanced with a | simple | rotationrotate_Left | (see figure 2) |
| --- | --- | --- | --- | --- | --- |
|  | Left Left | ⟹ X is rebalanced with a | simple | rotationrotate_Right | (mirror-image of figure 2) |
|  | Right Left | ⟹ X is rebalanced with a | double | rotationrotate_RightLeft | (see figure 3) |
|  | Left Right | ⟹ X is rebalanced with a | double | rotationrotate_LeftRight | (mirror-image of figure 3) |

 

Thereby, the situations are denoted as *C B*, where *C* (= child direction) and *B* (= balance) come from the set { *Left*, *Right* } with *Right* := −*Left*. The balance violation of case *C* == *B* is repaired by a simple rotation `rotate_`(−*C*), whereas the case *C* != *B* is repaired by a double rotation `rotate_`*CB*.

 

The cost of a rotation, either simple or double, is constant.

 

### Simple rotation

 

Figure 2 shows a Right Right situation. In its upper half, node X has two child trees with a balance factor of +2. Moreover, the inner child t23 of Z (i.e., left child when Z is right child, or right child when Z is left child) is not higher than its sibling t4. This can happen by a height increase of subtree t4 or by a height decrease of subtree t1. In the latter case, also the pale situation where t23 has the same height as t4 may occur.

 

The result of the left rotation is shown in the lower half of the figure. Three links (thick edges in figure 2) and two balance factors are to be updated.

 

As the figure shows, before an insertion, the leaf layer was at level h+1, temporarily at level h+2 and after the rotation again at level h+1. In case of a deletion, the leaf layer was at level h+2, where it is again, when t23 and t4 were of same height. Otherwise the leaf layer reaches level h+1, so that the height of the rotated tree decreases.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/76/AVL-simple-left_K.svg/250px-AVL-simple-left_K.svg.png)](./File:AVL-simple-left_K.svg)Fig. 2: Simple rotation
*rotate_Left*(*X*,*Z*) Code snippet of a simple left rotation 
| Input: | X = root of subtree to be rotated left |
| --- | --- |
|  | Z = right child of X, Z is right-heavy |
|  | with height ==Height(LeftSubtree(X))+2 |
| Result: | new root of rebalanced subtree |

 
```
node *rotate_Left(node *X, node *Z) {
    // Z is by 2 higher than its sibling
    t23 = left_child(Z); // Inner child of Z
    right_child(X) = t23;
    if (t23 != null)
        parent(t23) = X;
    left_child(Z) = X;
    parent(X) = Z;
    // 1st case, BF(Z) == 0,
    //   only happens with deletion, not insertion:
    if (BF(Z) == 0) { // t23 has been of same height as t4
        BF(X) = +1;   // t23 now higher
        BF(Z) = –1;   // t4 now lower than X
    } else
    { // 2nd case happens with insertion or deletion:
        BF(X) = 0;
        BF(Z) = 0;
    }
    return Z; // return new root of rotated subtree
}

```
 

### Double rotation

 

Figure 3 shows a Right Left situation. In its upper third, node X has two child trees with a balance factor of +2. But unlike figure 2, the inner child Y of Z is higher than its sibling t4. This can happen by the insertion of Y itself or a height increase of one of its subtrees t2 or t3 (with the consequence that they are of different height) or by a height decrease of subtree t1. In the latter case, it may also occur that t2 and t3 are of the same height.

 

The result of the first, the right, rotation is shown in the middle third of the figure. (With respect to the balance factors, this rotation is not of the same kind as the other AVL single rotations, because the height difference between Y and t4 is only 1.) The result of the final left rotation is shown in the lower third of the figure. Five links (thick edges in figure 3) and three balance factors are to be updated.

 

As the figure shows, before an insertion, the leaf layer was at level h+1, temporarily at level h+2 and after the double rotation again at level h+1. In case of a deletion, the leaf layer was at level h+2 and after the double rotation it is at level h+1, so that the height of the rotated tree decreases.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f9/AVL-double-rl_K.svg/330px-AVL-double-rl_K.svg.png)](./File:AVL-double-rl_K.svg)Fig. 3: Double rotation *rotate_RightLeft*(*X*,*Z*)
= *rotate_Right* around *Z* followed by
*rotate_Left* around *X* Code snippet of a right-left double rotation 
| Input: | X = root of subtree to be rotated |
| --- | --- |
|  | Z = its right child, left-heavy |
|  | with height ==Height(LeftSubtree(X))+2 |
| Result: | new root of rebalanced subtree |

 
```
node *rotate_RightLeft(node *X, node *Z) {
    // Z is by 2 higher than its sibling
    Y = left_child(Z); // Inner child of Z
    // Y is by 1 higher than sibling
    t3 = right_child(Y);
    left_child(Z) = t3;
    if (t3 != null)
        parent(t3) = Z;
    right_child(Y) = Z;
    parent(Z) = Y;
    t2 = left_child(Y);
    right_child(X) = t2;
    if (t2 != null)
        parent(t2) = X;
    left_child(Y) = X;
    parent(X) = Y;
    // 1st case, BF(Y) == 0
    if (BF(Y) == 0) {
        BF(X) = 0;
        BF(Z) = 0;
    } else if (BF(Y) > 0) {
        // t3 was higher
        BF(X) = –1;  // t1 now higher
        BF(Z) = 0;
    } else {
        // t2 was higher
        BF(X) = 0;
        BF(Z) = +1;  // t4 now higher
    }
    BF(Y) = 0;
    return Y; // return new root of rotated subtree
}

```
 

## Comparison to other structures

 

Both AVL trees and red–black (RB) trees are self-balancing binary search trees and they are related mathematically. Indeed, every AVL tree can be colored red–black,[[14]](./AVL_tree#cite_note-14) but there are RB trees which are not AVL balanced. For maintaining the AVL (or RB) tree's invariants, rotations play an important role. In the worst case, even without rotations, AVL or RB insertions or deletions require O(log *n*) inspections and/or updates to AVL balance factors (or RB colors). RB insertions and deletions and AVL insertions require from zero to three [tail-recursive](./Tail_call) rotations and run in [amortized](./Amortized_analysis) O(1) time,[[15]](./AVL_tree#cite_note-15): pp.165, 158  [[16]](./AVL_tree#cite_note-Dinesh-16) thus equally constant on average. AVL deletions requiring O(log *n*) rotations in the worst case are also O(1) on average. RB trees require storing one bit of information (the color) in each node, while AVL trees mostly use two bits for the balance factor, although, when stored at the children, one bit with meaning «lower than sibling» suffices. The bigger difference between the two data structures is their height limit.

 

For a tree of size *n* ≥ 1

 
- an AVL tree's height is at most
        h   ≦ ≦   c  log  2   ⁡ ⁡  ( n + d ) + b      <  c  log  2   ⁡ ⁡  ( n + 2 ) + b       {\displaystyle {\begin{array}{ll}h&\leqq \;c\log _{2}(n+d)+b\\&<\;c\log _{2}(n+2)+b\end{array}}}  ![{\displaystyle {\begin{array}{ll}h&\leqq \;c\log _{2}(n+d)+b\\&<\;c\log _{2}(n+2)+b\end{array}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/09edfe84ed94719e98bad3af597203ffc1803f77)

 where     φ φ  :=     1 +   5    2    ≈ ≈  1.618   {\displaystyle \varphi :={\tfrac {1+{\sqrt {5}}}{2}}\approx 1.618}  ![{\displaystyle \varphi :={\tfrac {1+{\sqrt {5}}}{2}}\approx 1.618}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48d4e4826360b780d733e8a0fa97caf8452423a4)  the [golden ratio](./Golden_ratio),     c :=    1   log  2   ⁡ ⁡  φ φ      ≈ ≈  1.440 ,   {\displaystyle c:={\tfrac {1}{\log _{2}\varphi }}\approx 1.440,}  ![{\displaystyle c:={\tfrac {1}{\log _{2}\varphi }}\approx 1.440,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f957081e84565e9d8dd4862c0a6749c4ac7304cf)       b :=    c 2     log  2   ⁡ ⁡  5 − −  2 ≈ ≈   − −  0.328 ,   {\displaystyle b:={\tfrac {c}{2}}\log _{2}5-2\approx \;-0.328,}  ![{\displaystyle b:={\tfrac {c}{2}}\log _{2}5-2\approx \;-0.328,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8345e477024d6067c86e02b45b4bea4b985da54) and      d := 1 +    1   φ φ   4     5       ≈ ≈  1.065   {\displaystyle d:=1+{\tfrac {1}{\varphi ^{4}{\sqrt {5}}}}\approx 1.065}  ![{\displaystyle d:=1+{\tfrac {1}{\varphi ^{4}{\sqrt {5}}}}\approx 1.065}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f89769f886c02e13ca20417916612b37fefbcd85). 
- a RB tree's height is at most 
        h   ≦ ≦   2  log  2   ⁡ ⁡  ( n + 1 )       {\displaystyle {\begin{array}{ll}h&\leqq \;2\log _{2}(n+1)\end{array}}}  ![{\displaystyle {\begin{array}{ll}h&\leqq \;2\log _{2}(n+1)\end{array}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b6a5f7b037429ded219b161bd1b07a495c03450) .[[17]](./AVL_tree#cite_note-17)

 

AVL trees are more rigidly balanced than RB trees with an [asymptotic](./Asymptotic_analysis) relation AVL/RB ≈0.720 of the maximal heights. For insertions and deletions, Ben Pfaff shows in 79 measurements a relation of AVL/RB between 0.677 and 1.077 with [median](./Median) ≈0.947 and [geometric mean](./Geometric_mean) ≈0.910.[[4]](./AVL_tree#cite_note-Pfaff1-4)

 

## See also

 
- [WAVL tree](./WAVL_tree)
- [Weight-balanced tree](./Weight-balanced_tree)
- [Splay tree](./Splay_tree)
- [Scapegoat tree](./Scapegoat_tree)
- [B-tree](./B-tree)
- [T-tree](./T-tree)
- [List of data structures](./List_of_data_structures)

 

## References

 
1. [1](./AVL_tree#cite_ref-wiscurl_1-0) [2](./AVL_tree#cite_ref-wiscurl_1-1) [3](./AVL_tree#cite_ref-wiscurl_1-2) [4](./AVL_tree#cite_ref-wiscurl_1-3) [5](./AVL_tree#cite_ref-wiscurl_1-4) [6](./AVL_tree#cite_ref-wiscurl_1-5) Eric Alexander. ["AVL Trees"](https://web.archive.org/web/20190731124716/https://pages.cs.wisc.edu/~ealexand/cs367/NOTES/AVL-Trees/index.html). Archived from [the original](http://pages.cs.wisc.edu/~ealexand/cs367/NOTES/AVL-Trees/index.html) on July 31, 2019.
2. [↑](./AVL_tree#cite_ref-2) Adelson-Velsky, Georgy; Landis, Evgenii (1962). "An algorithm for the organization of information". *[Proceedings of the USSR Academy of Sciences](./Proceedings_of_the_USSR_Academy_of_Sciences)* (in Russian). **146**: 263–266. [English translation](https://zhjwpku.com/assets/pdf/AED2-10-avl-paper.pdf) by Myron J. Ricci in *Soviet Mathematics - Doklady*, 3:1259–1263, 1962.
3. [↑](./AVL_tree#cite_ref-3) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1983). ["Balanced Trees"](https://archive.org/details/algorithms00sedg/page/199). *Algorithms*. Addison-Wesley. p. [199](https://archive.org/details/algorithms00sedg/page/199). [ISBN](./ISBN_(identifier)) [0-201-06672-6](./Special:BookSources/0-201-06672-6).
4. [1](./AVL_tree#cite_ref-Pfaff1_4-0) [2](./AVL_tree#cite_ref-Pfaff1_4-1) Pfaff, Ben (June 2004). ["Performance Analysis of BSTs in System Software"](http://www.stanford.edu/~blp/papers/libavl.pdf) (PDF). [Stanford University](./Stanford_University).
5. [↑](./AVL_tree#cite_ref-5) [AVL trees are not weight-balanced? (meaning: AVL trees are not μ-balanced?)](https://cs.stackexchange.com/q/421) 
Thereby: A Binary Tree is called     μ μ    {\displaystyle \mu }  ![{\displaystyle \mu }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fd47b2a39f7a7856952afec1f1db72c67af6161)-balanced, with     0 ≤ ≤  μ μ  ≤ ≤     1 2      {\displaystyle 0\leq \mu \leq {\tfrac {1}{2}}}  ![{\displaystyle 0\leq \mu \leq {\tfrac {1}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/362fa84e29a67eff22997a1a78ed8f00d47b86f0), if for every node     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3), the inequality

       1 2    − −  μ μ  ≤ ≤       |   N  l    |     |  N  |  + 1     ≤ ≤     1 2    + μ μ    {\displaystyle {\tfrac {1}{2}}-\mu \leq {\tfrac {|N_{l}|}{|N|+1}}\leq {\tfrac {1}{2}}+\mu }  ![{\displaystyle {\tfrac {1}{2}}-\mu \leq {\tfrac {|N_{l}|}{|N|+1}}\leq {\tfrac {1}{2}}+\mu }](https://wikimedia.org/api/rest_v1/media/math/render/svg/e594c5f5e1fcccb3d865e9ba16764e532ea44695)
holds and     μ μ    {\displaystyle \mu }  ![{\displaystyle \mu }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fd47b2a39f7a7856952afec1f1db72c67af6161) is minimal with this property.      |  N  |    {\displaystyle |N|}  ![{\displaystyle |N|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f9becad1e12f3234bef53f3d619b7c9c8dfc2b5a) is the number of nodes below the tree with     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) as root (including the root) and      N  l     {\displaystyle N_{l}}  ![{\displaystyle N_{l}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/571866e3b0d26d5062cb02156e70ce35189137e9) is the left child node of     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3).
6. [1](./AVL_tree#cite_ref-Knuth_6-0) [2](./AVL_tree#cite_ref-Knuth_6-1) [3](./AVL_tree#cite_ref-Knuth_6-2) [4](./AVL_tree#cite_ref-Knuth_6-3) [Knuth, Donald E.](./Donald_Knuth) (2000). *Sorting and searching* (2. ed., 6. printing, newly updated and rev. ed.). Boston [u.a.]: Addison-Wesley. [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0).
7. [↑](./AVL_tree#cite_ref-7) However, the balance information can be kept in the child nodes as one bit indicating whether the parent is higher by 1 or by 2; thereby higher by 2 cannot occur for both children. This way the AVL tree is a ["rank balanced" tree](./WAVL_tree), as coined by [Haeupler, Sen and Tarjan](./AVL_tree#Haeupler).
8. [↑](./AVL_tree#cite_ref-dixit-mastering-data-structures_8-0) Dixit, J. B. (2010). *Mastering data structures through 'C' language*. New Delhi, India: University Science Press, an imprint of Laxmi Publications Pvt. Ltd. [ISBN](./ISBN_(identifier)) [9789380386720](./Special:BookSources/9789380386720). [OCLC](./OCLC_(identifier)) [939446542](https://search.worldcat.org/oclc/939446542).
9. [1](./AVL_tree#cite_ref-brass-advanced-data-structures_9-0) [2](./AVL_tree#cite_ref-brass-advanced-data-structures_9-1) [3](./AVL_tree#cite_ref-brass-advanced-data-structures_9-2) Brass, Peter (2008). *Advanced data structures*. Cambridge: Cambridge University Press. [ISBN](./ISBN_(identifier)) [9780511438202](./Special:BookSources/9780511438202). [OCLC](./OCLC_(identifier)) [312435417](https://search.worldcat.org/oclc/312435417).
10. [↑](./AVL_tree#cite_ref-hubbard-outline-theory-problems_10-0) Hubbard, John Rast (2000). [*Schaum's outline of theory and problems of data structures with Java*](https://archive.org/details/schaumsoutlineof0000hubb). New York: McGraw-Hill. [ISBN](./ISBN_(identifier)) [0071378707](./Special:BookSources/0071378707). [OCLC](./OCLC_(identifier)) [48139308](https://search.worldcat.org/oclc/48139308).
11. [1](./AVL_tree#cite_ref-Pfaff_11-0) [2](./AVL_tree#cite_ref-Pfaff_11-1) [3](./AVL_tree#cite_ref-Pfaff_11-2) Pfaff, Ben (2004). *An Introduction to Binary Search Trees and Balanced Trees*. Free Software Foundation, Inc.
12. [↑](./AVL_tree#cite_ref-12) Weiss, Mark Allen (2006). *Data structures and algorithm analysis in C++* (3rd ed.). Boston: Pearson Addison-Wesley. p. 145. [ISBN](./ISBN_(identifier)) [0-321-37531-9](./Special:BookSources/0-321-37531-9). [OCLC](./OCLC_(identifier)) [61278554](https://search.worldcat.org/oclc/61278554).
13. [1](./AVL_tree#cite_ref-join-based_13-0) [2](./AVL_tree#cite_ref-join-based_13-1) Blelloch, Guy E.; Ferizovic, Daniel; Sun, Yihan (2016), "Just join for parallel ordered sets", *Symposium on Parallel Algorithms and Architectures*, ACM, pp. 253–264, [arXiv](./ArXiv_(identifier)):[1602.02120](https://arxiv.org/abs/1602.02120), [doi](./Doi_(identifier)):[10.1145/2935764.2935768](https://doi.org/10.1145%2F2935764.2935768), [ISBN](./ISBN_(identifier)) [978-1-4503-4210-0](./Special:BookSources/978-1-4503-4210-0), [S2CID](./S2CID_(identifier)) [2897793](https://api.semanticscholar.org/CorpusID:2897793).
14. [↑](./AVL_tree#cite_ref-14) Paul E. Black (2015-04-13). ["AVL tree"](https://xlinux.nist.gov/dads/HTML/avltree.html). *Dictionary of Algorithms and Data Structures*. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Retrieved 2016-07-02.
15. [↑](./AVL_tree#cite_ref-15) Mehlhorn, Kurt; Sanders, Peter (2008). [*Algorithms and Data Structures*](http://link.springer.com/10.1007/978-3-540-77978-0). Berlin, Heidelberg: Springer Berlin Heidelberg. [doi](./Doi_(identifier)):[10.1007/978-3-540-77978-0](https://doi.org/10.1007%2F978-3-540-77978-0). [ISBN](./ISBN_(identifier)) [978-3-540-77977-3](./Special:BookSources/978-3-540-77977-3).
16. [↑](./AVL_tree#cite_ref-Dinesh_16-0) Dinesh P. Mehta; Sartaj Sahni, eds. (2017-12-15). [*Handbook of Data Structures and Applications*](https://www.taylorfrancis.com/books/edit/10.1201/9781315119335/handbook-data-structures-applications-dinesh-mehta-sartaj-sahni) (2 ed.). New York: Chapman and Hall/CRC. [doi](./Doi_(identifier)):[10.1201/9781315119335](https://doi.org/10.1201%2F9781315119335). [ISBN](./ISBN_(identifier)) [978-1-315-11933-5](./Special:BookSources/978-1-315-11933-5).
17. [↑](./AVL_tree#cite_ref-17) [Red–black tree#Proof of bounds](./Red–black_tree#Proof_of_bounds)

 

## Further reading

 
- [Donald Knuth](./Donald_Knuth). *[The Art of Computer Programming](./The_Art_of_Computer_Programming)*, Volume 3: *Sorting and Searching*, Third Edition. Addison-Wesley, 1997. [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0). Pages 458–475 of section 6.2.3: Balanced Trees.
- Haeupler, Bernhard; Sen, Siddhartha; [Tarjan, Robert E.](./Robert_Tarjan) (2015), ["Rank-balanced trees"](http://sidsen.azurewebsites.net/papers/rb-trees-talg.pdf) (PDF), *ACM Transactions on Algorithms*, **11** (4): Art. 30, 26, [doi](./Doi_(identifier)):[10.1145/2689412](https://doi.org/10.1145%2F2689412), [MR](./MR_(identifier)) [3361215](https://mathscinet.ams.org/mathscinet-getitem?mr=3361215), [S2CID](./S2CID_(identifier)) [1407290](https://api.semanticscholar.org/CorpusID:1407290).

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Algorithm Implementation](https://en.wikibooks.org/wiki/Algorithm%20Implementation)* has a page on the topic of: ***[AVL tree](https://en.wikibooks.org/wiki/Algorithm%20Implementation/Trees/AVL%20tree)***    [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [AVL-trees](https://commons.wikimedia.org/wiki/Category:AVL-trees).  
- ![Public Domain](//upload.wikimedia.org/wikipedia/en/thumb/6/62/PD-icon.svg/20px-PD-icon.svg.png) This article incorporates [public domain material](./Copyright_status_of_works_by_the_federal_government_of_the_United_States) from Paul E. Black. ["AVL Tree"](https://xlinux.nist.gov/dads/HTML/avltree.html). *[Dictionary of Algorithms and Data Structures](./Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)*. [NIST](./National_Institute_of_Standards_and_Technology).

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |