---
source: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
fetched: 2026-06-19
---

Data structure for storing non-overlapping sets 
| Disjoint-set/Union-find Forest |
| --- |
| Type | multiway tree |
| Invented | 1964 |
| Invented by | Bernard A. GallerandMichael J. Fischer |
| Time complexityinbig O notationOperationAverageWorst caseSearchO(α(n))[1](amortized)O(α(n))[1](amortized)InsertO(1)[1]O(1)[1]Space complexitySpaceO(n)[1]O(n)[1] | Time complexityinbig O notation | Operation | Average | Worst case | Search | O(α(n))[1](amortized) | O(α(n))[1](amortized) | Insert | O(1)[1] | O(1)[1] | Space complexity | Space | O(n)[1] | O(n)[1] |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Search | O(α(n))[1](amortized) | O(α(n))[1](amortized) |
| Insert | O(1)[1] | O(1)[1] |
| Space complexity |
| Space | O(n)[1] | O(n)[1] |

 

In [computer science](./Computer_science), a **disjoint-set data structure**, also called a **union–find data structure** or **merge–find set**, is a [data structure](./Data_structure) that stores a collection of [disjoint](./Disjoint_sets) (non-overlapping) [sets](./Set_(mathematics)). Equivalently, it stores a [partition of a set](./Partition_of_a_set) into disjoint [subsets](./Subset). It provides operations for adding new sets, merging sets (replacing them with their [union](./Union_(set_theory))), and finding a representative member of a set. The last operation makes it possible to determine efficiently whether any two elements belong to the same set or to different sets.

 

While there are several ways of implementing disjoint-set data structures, in practice they are often identified with a particular implementation known as a **disjoint-set forest**. This specialized type of [forest](./Forest_(graph_theory)) performs union and find operations in near-constant [amortized time](./Amortized_analysis). For a sequence of m addition, union, or find operations on a disjoint-set forest with n nodes, the total time required is [*O*](./Big_O_notation)(*m*α(*n*)), where α(*n*) is the extremely slow-growing [inverse Ackermann function](./Inverse_Ackermann_function). Although disjoint-set forests do not guarantee this time per operation, each operation rebalances the structure (via tree compression) so that subsequent operations become faster. As a result, disjoint-set forests are both [asymptotically optimal](./Asymptotically_optimal) and practically efficient.

 

Disjoint-set data structures play a key role in [Kruskal's algorithm](./Kruskal's_algorithm) for finding the [minimum spanning tree](./Minimum_spanning_tree) of a graph. The importance of minimum spanning trees means that disjoint-set data structures support a wide variety of algorithms. In addition, these data structures find applications in symbolic computation and in compilers, especially for [register allocation](./Register_allocation) problems.

 

## History

 

Disjoint-set forests were first described by [Bernard A. Galler](./Bernard_A._Galler) and [Michael J. Fischer](./Michael_J._Fischer) in 1964.[[2]](./Disjoint-set_data_structure#cite_note-Galler1964-2) In 1973, their time complexity was bounded to     O (  log  ∗ ∗    ⁡ ⁡  ( n ) )   {\displaystyle O(\log ^{*}(n))}  ![{\displaystyle O(\log ^{*}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ad0ea4627a692443b1bffbddaacd44f3a4b46b9), the [iterated logarithm](./Iterated_logarithm) of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), by [Hopcroft](./John_Hopcroft) and [Ullman](./Jeffrey_Ullman).[[3]](./Disjoint-set_data_structure#cite_note-Hopcroft1973-3) In 1975, [Robert Tarjan](./Robert_Tarjan) was the first to prove the     O ( m α α  ( n ) )   {\displaystyle O(m\alpha (n))}  ![{\displaystyle O(m\alpha (n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e6ad711ac62a46c824c01e205f32a2fab557ceb) ([inverse Ackermann function](./Ackermann_function#Inverse)) upper bound on the algorithm's time complexity.[[4]](./Disjoint-set_data_structure#cite_note-Tarjan1984-4) He also proved it to be tight. In 1979, he showed that this was the lower bound for a certain class of algorithms, [pointer algorithms](./Pointer_algorithm), that include the Galler-Fischer structure.[[5]](./Disjoint-set_data_structure#cite_note-Tarjan1979-5) In 1989, [Fredman](./Michael_Fredman) and [Saks](./Michael_Saks_(mathematician)) showed that     Ω Ω  ( α α  ( n ) )   {\displaystyle \Omega (\alpha (n))}  ![{\displaystyle \Omega (\alpha (n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9bfdfd41667be083aff4b7c292a9f35884b654b8) (amortized) words of     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) bits must be accessed by *any* disjoint-set data structure per operation,[[6]](./Disjoint-set_data_structure#cite_note-Fredman1989-6) thereby proving the optimality of the data structure in this model.

 

In 1991, Galil and Italiano published a survey of data structures for disjoint-sets.[[7]](./Disjoint-set_data_structure#cite_note-Galil1991-7)

 

In 1994, Richard J. Anderson and Heather Woll described a parallelized version of Union–Find that never needs to block.[[8]](./Disjoint-set_data_structure#cite_note-Anderson1994-8)

 

In 2007, Sylvain Conchon and Jean-Christophe Filliâtre developed a semi-[persistent](./Persistent_data_structure) version of the disjoint-set forest data structure and formalized its correctness using the [proof assistant](./Proof_assistant) [Rocq](./Rocq) (then: *Coq*).[[9]](./Disjoint-set_data_structure#cite_note-Conchon2007-9) "Semi-persistent" means that previous versions of the structure are efficiently retained, but accessing previous versions of the data structure invalidates later ones. Their fastest implementation achieves performance almost as efficient as the non-persistent algorithm. They do not perform a complexity analysis.

 

Variants of disjoint-set data structures with better performance on a restricted class of problems have also been considered.  Gabow and Tarjan showed that if the possible unions are restricted in certain ways, then a truly linear time algorithm is possible.[[10]](./Disjoint-set_data_structure#cite_note-10) In particular, linear time is achievable if a "union tree" is given a priori. This is a tree that includes all elements of the sets. Let p[*v*] denote the parent in the tree, then the assumption is that union operations must have the form **union**(*v*,p[*v*]) for some *v*.

 

## Representation

 

In this and the following section we describe the most common implementation of the disjoint-set data structure, as a forest of
[parent pointer trees](./Parent_pointer_tree). This representation is known as **Galler-Fischer trees**.

 

Each node in a disjoint-set forest consists of a pointer and some auxiliary information, either a size or a rank (but not both).  The pointers are used to make [parent pointer trees](./Parent_pointer_tree), where each node that is not the root of a tree points to its parent.  To distinguish root nodes from others, their parent pointers have invalid values, such as a [circular reference](./Circular_reference) to the node or a [sentinel value](./Sentinel_value).  Each tree represents a set stored in the forest, with the members of the set being the nodes in the tree.  Root nodes provide set representatives: Two nodes are in the same set if and only if the roots of the trees containing the nodes are equal.

 

Nodes in the forest can be stored in any way convenient to the application, but a common technique is to store them in an array.  In this case, parents can be indicated by their array index.  Every array entry requires Θ(log *n*) bits of storage for the parent pointer.  A comparable or lesser amount of storage is required for the rest of the entry, so the number of bits required to store the forest is Θ(*n* log *n*).  If an implementation uses fixed size nodes (thereby limiting the maximum size of the forest that can be stored), then the necessary storage is linear in n.

 

## Operations

 

Disjoint-set data structures support three operations: Making a new set containing a new element; Finding the representative of the set containing a given element; and Merging two sets.

 

### Making new sets

 

The `MakeSet` operation adds a new element into a new set containing only the new element, and the new set is added to the data structure.  If the data structure is instead viewed as a partition of a set, then the `MakeSet` operation enlarges the set by adding the new element, and it extends the existing partition by putting the new element into a new subset containing only the new element.

 

In a disjoint-set forest, `MakeSet` initializes the node's parent pointer and the node's size or rank.  If a root is represented by a node that points to itself, then adding an element can be described using the following [pseudocode](./Pseudocode):

 
```
function MakeSet(x) is
    if x is not already in the forest then
        x.parent := x
        x.size := 1     // if nodes store size
        x.rank := 0     // if nodes store rank
    end if
end function
```
 

This operation has linear time complexity.  In particular, initializing a
disjoint-set forest with n nodes requires *O*(*n*)
time.

 

Lack of a parent assigned to the node implies that the node is not present in the forest.

 

In practice, `MakeSet` must be preceded by an operation that allocates memory to hold x.  As long as memory allocation is an amortized constant-time operation, as it is for a good [dynamic array](./Dynamic_array) implementation, it does not change the asymptotic performance of the random-set forest.

 

### Finding set representatives

 

The `Find` operation follows the chain of parent pointers from a specified query node x until it reaches a root element.  This root element represents the set to which x belongs and may be x itself.  `Find` returns the root element it reaches.

 

Performing a `Find` operation presents an important opportunity for improving the forest.  The time in a `Find` operation is spent chasing parent pointers, so a flatter tree leads to faster `Find` operations.  When a `Find` is executed, there is no faster way to reach the root than by following each parent pointer in succession.  However, the parent pointers visited during this search can be updated to point closer to the root.  Because every element visited on the way to a root is part of the same set, this does not change the sets stored in the forest.  But it makes future `Find` operations faster, not only for the nodes between the query node and the root, but also for their descendants.  This updating is an important part of the disjoint-set forest's amortized performance guarantee.

 

There are several algorithms for `Find` that achieve the asymptotically optimal time complexity.  One family of algorithms, known as **path compression**, makes every node between the query node and the root point to the root.  Path compression can be implemented using a simple recursion as follows:

 
```
function Find(x) is
    if x.parent ≠ x then
        x.parent := Find(x.parent)
        return x.parent
    else
        return x
    end if
end function
```
 

This implementation makes two passes, one up the tree and one back down.  It requires enough scratch memory to store the path from the query node to the root (in the above pseudocode, the path is implicitly represented using the [call stack](./Call_stack)).  This can be decreased to a constant amount of memory by performing both passes in the same direction.  The constant memory implementation walks from the query node to the root twice, once to find the root and once to update pointers:

 
```
function Find(x) is
    root := x
    while root.parent ≠ root do
        root := root.parent
    end while

    while x.parent ≠ root do
        parent := x.parent
        x.parent := root
        x := parent
    end while

    return root
end function
```
 

[Tarjan](./Robert_E._Tarjan) and [Van Leeuwen](./Jan_van_Leeuwen) also developed one-pass `Find` algorithms that retain the same [worst-case complexity](./Worst-case_complexity) but are more efficient in practice.[[4]](./Disjoint-set_data_structure#cite_note-Tarjan1984-4)  These are called path splitting and path halving.  Both of these update the parent pointers of nodes on the path between the query node and the root.  **Path splitting** replaces every parent pointer on that path by a pointer to the node's grandparent:

 
```
function Find(x) is
    while x.parent ≠ x do
        (x, x.parent) := (x.parent, x.parent.parent)
    end while
    return x
end function
```
 

**Path halving** works similarly but replaces only every other parent pointer:

 
```
function Find(x) is
    while x.parent ≠ x do
        x.parent := x.parent.parent
        x := x.parent
    end while
    return x
end function
```
 

### Merging two sets

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/67/Dsu_disjoint_sets_init.svg/500px-Dsu_disjoint_sets_init.svg.png)](./File:Dsu_disjoint_sets_init.svg)`MakeSet` creates 8 singletons.[![](//upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Dsu_disjoint_sets_final.svg/500px-Dsu_disjoint_sets_final.svg.png)](./File:Dsu_disjoint_sets_final.svg)After some operations of `Union`, some sets are grouped together. 

The operation `Union(x, y)` replaces the set containing x and the set containing y with their union.  `Union` first uses `Find` to determine the roots of the trees containing x and y.  If the roots are the same, there is nothing more to do.  Otherwise, the two trees must be merged.  This is done by either setting the parent pointer of x's root to y's, or setting the parent pointer of y's root to x's.

 

The choice of which node becomes the parent has consequences for the complexity of future operations on the tree. If it is done carelessly, trees can become excessively tall.  For example, suppose that `Union` always made the tree containing x a subtree of the tree containing y.  Begin with a forest that has just been initialized with elements     1 , 2 , 3 , … …  , n ,   {\displaystyle 1,2,3,\ldots ,n,}  ![{\displaystyle 1,2,3,\ldots ,n,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5a3d8fe63a83d104e561694135d73b64ec3c6fb) and execute `Union(1, 2)`, `Union(2, 3)`, ..., `Union(n - 1, n)`.  The resulting forest contains a single tree whose root is n, and the path from 1 to n passes through every node in the tree.  For this forest, the time to run `Find(1)` is *O*(*n*).

 

In an efficient implementation, tree height is controlled using **union by size** or **union by rank**.  Both of these require a node to store information besides just its parent pointer.  This information is used to decide which root becomes the new parent.  Both strategies ensure that trees do not become too deep.

 

#### Union by size

 

In the case of union by size, a node stores its size, which is simply its number of descendants (including the node itself).  When the trees with roots x and y are merged, the node with more descendants becomes the parent.  If the two nodes have the same number of descendants, then either one can become the parent.  In both cases, the size of the new parent node is set to its new total number of descendants.

 
```
function Union(x, y) is
    // Replace nodes by roots
    x := Find(x)
    y := Find(y)

    if x = y then
        return  // x and y are already in the same set
    end if

    // If necessary, swap variables to ensure that
    // x has at least as many descendants as y
    if x.size < y.size then
        (x, y) := (y, x)
    end if

    // Make x the new root
    y.parent := x
    // Update the size of x
    x.size := x.size + y.size
end function
```
 

The number of bits necessary to store the size is clearly the number of bits necessary to store n.  This adds a constant factor to the forest's required storage.

 

#### Union by rank

 

For union by rank, a node stores its *rank*, which is an upper bound for its height.  When a node is initialized, its rank is set to zero.  To merge trees with roots x and y, first compare their ranks.  If the ranks are different, then the larger rank tree becomes the parent, and the ranks of x and y do not change.  If the ranks are the same, then either one can become the parent, but the new parent's rank is incremented by one.  While the rank of a node is clearly related to its height, storing ranks is more efficient than storing heights.  The height of a node can change during a `Find` operation, so storing ranks avoids the extra effort of keeping the height correct.  In pseudocode, union by rank is:

 
```
function Union(x, y) is
    // Replace nodes by roots
    x := Find(x)
    y := Find(y)

    if x = y then
        return  // x and y are already in the same set
    end if

    // If necessary, rename variables to ensure that
    // x has rank at least as large as that of y
    if x.rank < y.rank then
        (x, y) := (y, x)
    end if

    // Make x the new root
    y.parent := x
    // If necessary, increment the rank of x
    if x.rank = y.rank then
        x.rank := x.rank + 1
    end if
end function
```
 

It can be shown that every node has rank     ⌊ ⌊  log ⁡ ⁡  n ⌋ ⌋    {\displaystyle \lfloor \log n\rfloor }  ![{\displaystyle \lfloor \log n\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/2691a5620da37c1f740a04a8fd226072143455c9) or less.[[11]](./Disjoint-set_data_structure#cite_note-Cormen2009-11)  Consequently, each rank can be stored in *O*(log log *n*) bits and all the ranks can be stored in *O*(*n* log log *n*) bits. This makes the ranks an asymptotically negligible portion of the forest's size.

 

It is clear from the above implementations that the size and rank of a node do not matter unless a node is the root of a tree.  Once a node becomes a child, its size and rank are never accessed again.

 

There is a variant of the `Union` operation in which the user determines the representative of the formed set. It is not hard to add this functionality to the above algorithms without losing efficiency.

 

## Time complexity

 

A disjoint-set forest implementation in which `Find` does not update parent pointers, and in which `Union` does not attempt to control tree heights, can have trees with height *O*(*n*).  In such a situation, the `Find` and `Union` operations require *O*(*n*) time.

 

If an implementation uses path compression alone, then a sequence of n `MakeSet` operations, followed by up to *n* − 1 `Union` operations and *f* `Find` operations, has a worst-case running time of     Θ Θ  ( n + f ⋅ ⋅   (  1 +  log  2 + f  /  n   ⁡ ⁡  n  )  )   {\displaystyle \Theta (n+f\cdot \left(1+\log _{2+f/n}n\right))}  ![{\displaystyle \Theta (n+f\cdot \left(1+\log _{2+f/n}n\right))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e209b18c4cd57bd8f29a3d84d3911a9c708155e).[[11]](./Disjoint-set_data_structure#cite_note-Cormen2009-11)

 

Using union by rank, but without updating parent pointers during `Find`, gives a running time of     Θ Θ  ( m log ⁡ ⁡  n )   {\displaystyle \Theta (m\log n)}  ![{\displaystyle \Theta (m\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1dc4a519eddba0d1d9242936a7ca0422c3f33a30) for m operations of any type, up to n of which are `MakeSet` operations.[[11]](./Disjoint-set_data_structure#cite_note-Cormen2009-11)

 

The combination of path compression, splitting, or halving, with union by size or by rank, reduces the running time for m operations of any type, up to n of which are `MakeSet` operations, to     Θ Θ  ( m α α  ( n ) )   {\displaystyle \Theta (m\alpha (n))}  ![{\displaystyle \Theta (m\alpha (n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ef73db523155adccdb88ef38828472de6c31294).[[4]](./Disjoint-set_data_structure#cite_note-Tarjan1984-4)[[5]](./Disjoint-set_data_structure#cite_note-Tarjan1979-5)  This makes the [amortized running time](./Amortized_analysis) of each operation     Θ Θ  ( α α  ( n ) )   {\displaystyle \Theta (\alpha (n))}  ![{\displaystyle \Theta (\alpha (n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc86ca978bb6d4e7a6c466ec8829a0010c968982).  This is asymptotically optimal, meaning that every disjoint set data structure must use     Ω Ω  ( α α  ( n ) )   {\displaystyle \Omega (\alpha (n))}  ![{\displaystyle \Omega (\alpha (n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9bfdfd41667be083aff4b7c292a9f35884b654b8) amortized time per operation.[[6]](./Disjoint-set_data_structure#cite_note-Fredman1989-6)  Here, the function     α α  ( n )   {\displaystyle \alpha (n)}  ![{\displaystyle \alpha (n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/74c1642d9e2f86b9e5c86c0f18ee5377507da827) is the [inverse Ackermann function](./Ackermann_function#Inverse).  The inverse Ackermann function grows extraordinarily slowly, so this factor is 4 or less for any n that can actually be written in the physical universe.  This makes disjoint-set operations practically amortized constant time.

 

### Proof of O(m log* n) time complexity of Union-Find

 

The precise analysis of the performance of a disjoint-set forest is somewhat intricate.  However, there is a much simpler analysis that proves that the amortized time for any m `Find` or `Union` operations on a disjoint-set forest containing n objects is *O*(*m* log* *n*), where log* denotes the [iterated logarithm](./Iterated_logarithm).[[12]](./Disjoint-set_data_structure#cite_note-12)[[13]](./Disjoint-set_data_structure#cite_note-13)[[14]](./Disjoint-set_data_structure#cite_note-14)[[15]](./Disjoint-set_data_structure#cite_note-15)

 

Lemma 1: As the [find function](./Disjoint-set_data_structure#Disjoint-set_forests) follows the path along to the root, the rank of node it encounters is increasing.

 **Proof** 

We claim that as Find and Union operations are applied to the data set, this fact remains true over time. Initially when each node is the root of its own tree, it's trivially true. The only case when the rank of a node might be changed is when the [Union by Rank](./Disjoint-set_data_structure#Disjoint-set_forests) operation is applied. In this case, a tree with smaller rank will be attached to a tree with greater rank, rather than vice versa. And during the find operation, all nodes visited along the path will be attached to the root, which has larger rank than its children, so this operation won't change this fact either.

  

Lemma 2: A node u which is root of a subtree with rank r has at least      2  r     {\displaystyle 2^{r}}  ![{\displaystyle 2^{r}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c7f5f9125e1c1d0ac48d810ee16bfe95c6dabcad) nodes.

 **Proof** 

Initially when each node is the root of its own tree, it's trivially true. Assume that a node u with rank r has at least 2*r* nodes. Then when two trees with rank r are merged using the operation [Union by Rank](./Disjoint-set_data_structure#Disjoint-set_forests), a tree with rank *r* + 1 results, the root of which has at least      2  r   +  2  r   =  2  r + 1     {\displaystyle 2^{r}+2^{r}=2^{r+1}}  ![{\displaystyle 2^{r}+2^{r}=2^{r+1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f050b8962a385242f91c28ff7dc16835c1a7a6) nodes.

  [![](//upload.wikimedia.org/wikipedia/en/4/4d/ProofOflogstarnRank.jpg)](./File:ProofOflogstarnRank.jpg) 

Lemma 3: The maximum number of nodes of rank r is at most       n  2  r     .   {\displaystyle {\frac {n}{2^{r}}}.}  ![{\displaystyle {\frac {n}{2^{r}}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/73c408491edd68f7fceefc447ecccdb2919423b0)

 **Proof** 

From [lemma 2](./Disjoint-set_data_structure#min_subtree_size_lemma), we know that a node u which is root of a subtree with rank r has at least      2  r     {\displaystyle 2^{r}}  ![{\displaystyle 2^{r}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c7f5f9125e1c1d0ac48d810ee16bfe95c6dabcad) nodes. We will get the maximum number of nodes of rank r when each node with rank r is the root of a tree that has exactly      2  r     {\displaystyle 2^{r}}  ![{\displaystyle 2^{r}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c7f5f9125e1c1d0ac48d810ee16bfe95c6dabcad) nodes. In this case, the number of nodes of rank r is       n  2  r     .   {\displaystyle {\frac {n}{2^{r}}}.}  ![{\displaystyle {\frac {n}{2^{r}}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/73c408491edd68f7fceefc447ecccdb2919423b0)

  

At any particular point in the execution, we can  group the vertices of the graph into "buckets", according to their rank. We define the buckets' ranges inductively, as follows: Bucket 0 contains vertices of rank 0. Bucket 1 contains vertices of rank 1. Bucket 2 contains vertices of ranks 2 and 3. 
In general, if the B-th bucket contains vertices with ranks from interval      [  r ,  2  r   − −  1  ]  = [ r , R − −  1 ]   {\displaystyle \left[r,2^{r}-1\right]=[r,R-1]}  ![{\displaystyle \left[r,2^{r}-1\right]=[r,R-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49aa6ca95d184c363386c5c5aaa6c8932934e9b2), then the (B+1)st bucket will contain vertices with ranks from interval      [  R ,  2  R   − −  1  ]  .   {\displaystyle \left[R,2^{R}-1\right].}  ![{\displaystyle \left[R,2^{R}-1\right].}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe254e2d62c18dbe3ed168f4417653d5afd1ed23)

 

For     B ∈ ∈   N    {\displaystyle B\in \mathbb {N} }  ![{\displaystyle B\in \mathbb {N} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b61c9034faef7d7729254ebfc51ce247955a165), let      tower  ( B ) =     2   2   ⋯ ⋯   2       ⏟ ⏟     B   times      {\displaystyle {\text{tower}}(B)=\underbrace {2^{2^{\cdots ^{2}}}} _{B{\text{ times}}}}  ![{\displaystyle {\text{tower}}(B)=\underbrace {2^{2^{\cdots ^{2}}}} _{B{\text{ times}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2db06cffcc90a9f0c2ab78e90eb36c40e8219ae6). Then
bucket     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) will have vertices with ranks in the interval     [  tower  ( B − −  1 ) ,  tower  ( B ) − −  1 ]   {\displaystyle [{\text{tower}}(B-1),{\text{tower}}(B)-1]}  ![{\displaystyle [{\text{tower}}(B-1),{\text{tower}}(B)-1]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ef0146c95ec30ab5e27b2ea4d6925435b79595de).

 [![](//upload.wikimedia.org/wikipedia/commons/d/d5/Proof_of_O%28log%2An%29_Union_Find.jpg)](./File:Proof_of_O(log*n)_Union_Find.jpg)Proof of     O (  log  ∗ ∗    ⁡ ⁡  n )   {\displaystyle O(\log ^{*}n)}  ![{\displaystyle O(\log ^{*}n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ba846ca61ce56540d44c487534367163945ad17d) Union Find 

We can make two observations about the buckets' sizes.

 
1. The total number of buckets is at most log**n*.
Proof: Since no vertex can have rank greater than     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), only the first      log  ∗ ∗    ⁡ ⁡  ( n )   {\displaystyle \log ^{*}(n)}  ![{\displaystyle \log ^{*}(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bf706147043580232b6e19d25c80a0f73bb2d525) buckets can have vertices, where      log  ∗ ∗      {\displaystyle \log ^{*}}  ![{\displaystyle \log ^{*}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e19ae183e78de19eeba18aa7281720cedf5e620b) denotes the inverse of the      tower    {\displaystyle {\text{tower}}}  ![{\displaystyle {\text{tower}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/513308f09a89c4c867fe9478a2046cfb311a6595) function defined above.
2. The maximum number of elements in bucket      [  B ,  2  B   − −  1  ]    {\displaystyle \left[B,2^{B}-1\right]}  ![{\displaystyle \left[B,2^{B}-1\right]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/70d4053472d64e0df71dcc2afcd0a3612a0d0ec8) is at most        2 n   2  B       {\displaystyle {\frac {2n}{2^{B}}}}  ![{\displaystyle {\frac {2n}{2^{B}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b683d9326a268636904f987d7790ac7411659770).
Proof: The maximum number of elements in bucket      [  B ,  2  B   − −  1  ]    {\displaystyle \left[B,2^{B}-1\right]}  ![{\displaystyle \left[B,2^{B}-1\right]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/70d4053472d64e0df71dcc2afcd0a3612a0d0ec8) is at most       n  2  B     +   n  2  B + 1     +   n  2  B + 2     + ⋯ ⋯  +   n  2   2  B   − −  1     ≤ ≤     2 n   2  B     .   {\displaystyle {\frac {n}{2^{B}}}+{\frac {n}{2^{B+1}}}+{\frac {n}{2^{B+2}}}+\cdots +{\frac {n}{2^{2^{B}-1}}}\leq {\frac {2n}{2^{B}}}.}  ![{\displaystyle {\frac {n}{2^{B}}}+{\frac {n}{2^{B+1}}}+{\frac {n}{2^{B+2}}}+\cdots +{\frac {n}{2^{2^{B}-1}}}\leq {\frac {2n}{2^{B}}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63c4bd9a5b92a47caf6fc4cad79021fe08f0da86)

 

Let F represent the list of "find" operations performed, and let

 

     T  1   =  ∑ ∑   F    (link to the root)    {\displaystyle T_{1}=\sum _{F}{\text{(link to the root)}}}  ![{\displaystyle T_{1}=\sum _{F}{\text{(link to the root)}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/46d02c8c920e47add454150f29940618341b2c0a)      T  2   =  ∑ ∑   F    (number of links traversed where the buckets are different)    {\displaystyle T_{2}=\sum _{F}{\text{(number of links traversed where the buckets are different)}}}  ![{\displaystyle T_{2}=\sum _{F}{\text{(number of links traversed where the buckets are different)}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/15dc94f376bdb48b3ad7d1dd1f6efc7e6bb64939)      T  3   =  ∑ ∑   F    (number of links traversed where the buckets are the same).    {\displaystyle T_{3}=\sum _{F}{\text{(number of links traversed where the buckets are the same).}}}  ![{\displaystyle T_{3}=\sum _{F}{\text{(number of links traversed where the buckets are the same).}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e51e81e137aeca61ba3174dbeb6f55ee6f84046)

 

Then the total cost of m finds is     T =  T  1   +  T  2   +  T  3   .   {\displaystyle T=T_{1}+T_{2}+T_{3}.}  ![{\displaystyle T=T_{1}+T_{2}+T_{3}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e3ff11b91349544dee273c5d937271b0cb613be5)

 

Since each find operation makes exactly one traversal that leads to a root, we have *T*1 = *O*(*m*).

 

Also, from the bound above on the number of buckets, we have *T*2 = *O*(*m*log**n*).

 

For T3, suppose we are traversing an edge from u to v, where u and v have rank in the bucket [*B*, 2*B* − 1] and v is not the root (at the time of this traversing, otherwise the traversal would be accounted for in T1). Fix u and consider the sequence      v  1   ,  v  2   , … …  ,  v  k     {\displaystyle v_{1},v_{2},\ldots ,v_{k}}  ![{\displaystyle v_{1},v_{2},\ldots ,v_{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0f4cea5f36d7a84bb76f2dc891a9498d856b2851) that take the role of v in different find operations. Because of path compression and not accounting for the edge to a root, this sequence contains only different nodes and because of [Lemma 1](./Disjoint-set_data_structure#increasing_rank_lemma) we know that the ranks of the nodes in this sequence are strictly increasing. By both of the nodes being in the bucket we can conclude that the length k of the sequence (the number of times node u is attached to a different root in the same bucket) is at most the number of ranks in the buckets B, that is, at most      2  B   − −  1 − −  B <  2  B   .   {\displaystyle 2^{B}-1-B<2^{B}.}  ![{\displaystyle 2^{B}-1-B<2^{B}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/db28624639513ee601384d1ebe7774e1c2a50d86)

 

Therefore,      T  3   ≤ ≤   ∑ ∑   [ B ,  2  B   − −  1 ]    ∑ ∑   u    2  B   .   {\displaystyle T_{3}\leq \sum _{[B,2^{B}-1]}\sum _{u}2^{B}.}  ![{\displaystyle T_{3}\leq \sum _{[B,2^{B}-1]}\sum _{u}2^{B}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6f85cd493fd0596a25595537c645fc839d9ebf0)

 

From Observations [1](./Disjoint-set_data_structure#max_buckets) and [2](./Disjoint-set_data_structure#max_bucket_size), we can conclude that      T  3   ≤ ≤   ∑ ∑   B    2  B      2 n   2  B     ≤ ≤  2 n  log  ∗ ∗    ⁡ ⁡  n .   {\textstyle T_{3}\leq \sum _{B}2^{B}{\frac {2n}{2^{B}}}\leq 2n\log ^{*}n.}  ![{\textstyle T_{3}\leq \sum _{B}2^{B}{\frac {2n}{2^{B}}}\leq 2n\log ^{*}n.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bae8a83684fb38b41e393d1edd84e3488873a1c5)

 

Therefore,     T =  T  1   +  T  2   +  T  3   = O ( m  log  ∗ ∗    ⁡ ⁡  n ) .   {\displaystyle T=T_{1}+T_{2}+T_{3}=O(m\log ^{*}n).}  ![{\displaystyle T=T_{1}+T_{2}+T_{3}=O(m\log ^{*}n).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49c0ecafaa451f4f32aed4a06035feb3797777a3)

 

## Other structures

 

### Better worst-case time per operation

 

The worst-case time of the `Find` operation in trees with **Union by rank** or **Union by weight** is     Θ Θ  ( log ⁡ ⁡  n )   {\displaystyle \Theta (\log n)}  ![{\displaystyle \Theta (\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65bac5223de9c91eb3e89a032b5c51fd3041dc66) (i.e., it is     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) and this bound is tight). 
In 1985, N. Blum gave an implementation of the operations that does not use path compression, but compresses trees during     u n i o n   {\displaystyle union}  ![{\displaystyle union}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c47ba3e46bce1b4aefaabf75f8b0036161820a7). His implementation runs in     O ( log ⁡ ⁡  n  /  log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(\log n/\log \log n)}  ![{\displaystyle O(\log n/\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc17efd2d66135a2972e35ab7680ec720efc8d5b) time per operation,[[16]](./Disjoint-set_data_structure#cite_note-16) and thus in comparison with Galler and Fischer's structure it has a better worst-case time per operation, but inferior amortized time. In 1999, Alstrup et al. gave a structure that has optimal worst-case
time     O ( log ⁡ ⁡  n  /  log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(\log n/\log \log n)}  ![{\displaystyle O(\log n/\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc17efd2d66135a2972e35ab7680ec720efc8d5b) together with inverse-Ackermann amortized time.[[17]](./Disjoint-set_data_structure#cite_note-17)

 

### Deletion

 

The regular implementation as disjoint-set forests does not react favorably to the deletion of elements,
in the sense that the time for `Find` will not improve as a result of the decrease in the number of elements. However, there exist modern implementations that allow for constant-time deletion and where the time-bound for `Find` depends on the *current* number of elements[[18]](./Disjoint-set_data_structure#cite_note-18)[[19]](./Disjoint-set_data_structure#cite_note-19)

 

## Backtracking

 

It is possible to extend certain disjoint-set forest structures to allow [backtracking](./Backtracking). The basic form of backtracking is to allow a 
`Backtrack(1)` operation, that undoes the last `Union`. A more advanced form allows `Backtrack(i)`,
which undoes the last i unions. The following complexity result is known: there is a data structure which supports `Union`
and `Find` in     O ( log ⁡ ⁡  n  /  log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(\log n/\log \log n)}  ![{\displaystyle O(\log n/\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc17efd2d66135a2972e35ab7680ec720efc8d5b) time per operation, and `Backtrack` in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time.[[20]](./Disjoint-set_data_structure#cite_note-WT-20) In this result, the freedom of `Union` to choose the representative of the formed set is essential.
Better amortized time cannot be achieved within the class of separable [pointer algorithms](./Pointer_algorithm).[[20]](./Disjoint-set_data_structure#cite_note-WT-20)

 

## Applications

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a3/UnionFindKruskalDemo.gif/250px-UnionFindKruskalDemo.gif)](./File:UnionFindKruskalDemo.gif)A demo for Union-Find when using Kruskal's algorithm to find minimum spanning tree. 

Disjoint-set data structures model the [partitioning of a set](./Partition_of_a_set), for example to keep track of the [connected components](./Connected_component_(graph_theory)) of an [undirected graph](./Undirected_graph). This model can then be used to determine whether two vertices belong to the same component, or whether adding an edge between them would result in a cycle.  The Union–Find algorithm is used in high-performance implementations of [unification](./Unification_(computer_science)).[[21]](./Disjoint-set_data_structure#cite_note-Knight1989-21)

 

This data structure is used by the [Boost Graph Library](./Boost_Graph_Library) to implement its [Incremental Connected Components](http://www.boost.org/libs/graph/doc/incremental_components.html) functionality. It is also a key component in implementing [Kruskal's algorithm](./Kruskal's_algorithm) to find the [minimum spanning tree](./Minimum_spanning_tree) of a graph.

 

The [Hoshen-Kopelman algorithm](./Hoshen–Kopelman_algorithm) uses a Union-Find.

 

Union-find can be used to implement reasonably performant [Type inference](./Type_inference) algorithms.

 

## See also

 
- [Partition refinement](./Partition_refinement), a different data structure for maintaining disjoint sets, with updates that split sets apart rather than merging them together
- [Dynamic connectivity](./Dynamic_connectivity) – Data structure that maintains info about the connected components of a graph

 

## References

 
1. [1](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-0) [2](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-1) [3](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-2) [4](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-3) [5](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-4) [6](./Disjoint-set_data_structure#cite_ref-tarjan1975_1-5) [Tarjan, Robert Endre](./Robert_E._Tarjan) (1975). "Efficiency of a Good But Not Linear Set Union Algorithm". *Journal of the ACM*. **22** (2): 215–225. [doi](./Doi_(identifier)):[10.1145/321879.321884](https://doi.org/10.1145%2F321879.321884). [hdl](./Hdl_(identifier)):[1813/5942](https://hdl.handle.net/1813%2F5942). [S2CID](./S2CID_(identifier)) [11105749](https://api.semanticscholar.org/CorpusID:11105749).
2. [↑](./Disjoint-set_data_structure#cite_ref-Galler1964_2-0) [Galler, Bernard A.](./Bernard_A._Galler); [Fischer, Michael J.](./Michael_J._Fischer) (May 1964). ["An improved equivalence algorithm"](https://doi.org/10.1145%2F364099.364331). *[Communications of the ACM](./Communications_of_the_ACM)*. **7** (5): 301–303. [doi](./Doi_(identifier)):[10.1145/364099.364331](https://doi.org/10.1145%2F364099.364331). [S2CID](./S2CID_(identifier)) [9034016](https://api.semanticscholar.org/CorpusID:9034016).. The paper originating disjoint-set forests.
3. [↑](./Disjoint-set_data_structure#cite_ref-Hopcroft1973_3-0) [Hopcroft, J. E.](./John_Hopcroft); [Ullman, J. D.](./Jeffrey_Ullman) (1973). "Set Merging Algorithms". *SIAM Journal on Computing*. **2** (4): 294–303. [doi](./Doi_(identifier)):[10.1137/0202024](https://doi.org/10.1137%2F0202024).
4. [1](./Disjoint-set_data_structure#cite_ref-Tarjan1984_4-0) [2](./Disjoint-set_data_structure#cite_ref-Tarjan1984_4-1) [3](./Disjoint-set_data_structure#cite_ref-Tarjan1984_4-2) [Tarjan, Robert E.](./Robert_E._Tarjan); [van Leeuwen, Jan](./Jan_van_Leeuwen) (1984). ["Worst-case analysis of set union algorithms"](https://doi.org/10.1145%2F62.2160). *Journal of the ACM*. **31** (2): 245–281. [doi](./Doi_(identifier)):[10.1145/62.2160](https://doi.org/10.1145%2F62.2160). [S2CID](./S2CID_(identifier)) [5363073](https://api.semanticscholar.org/CorpusID:5363073).
5. [1](./Disjoint-set_data_structure#cite_ref-Tarjan1979_5-0) [2](./Disjoint-set_data_structure#cite_ref-Tarjan1979_5-1) [Tarjan, Robert Endre](./Robert_E._Tarjan) (1979). ["A class of algorithms which require non-linear time to maintain disjoint sets"](https://doi.org/10.1016%2F0022-0000%2879%2990042-4). *Journal of Computer and System Sciences*. **18** (2): 110–127. [doi](./Doi_(identifier)):[10.1016/0022-0000(79)90042-4](https://doi.org/10.1016%2F0022-0000%2879%2990042-4).
6. [1](./Disjoint-set_data_structure#cite_ref-Fredman1989_6-0) [2](./Disjoint-set_data_structure#cite_ref-Fredman1989_6-1) [Fredman, M.](./Michael_Fredman); Saks, M. (May 1989). "The cell probe complexity of dynamic data structures". *Proceedings of the twenty-first annual ACM symposium on Theory of computing - STOC '89*. pp. 345–354. [doi](./Doi_(identifier)):[10.1145/73007.73040](https://doi.org/10.1145%2F73007.73040). [ISBN](./ISBN_(identifier)) [0897913078](./Special:BookSources/0897913078). [S2CID](./S2CID_(identifier)) [13470414](https://api.semanticscholar.org/CorpusID:13470414). Theorem 5: Any CPROBE(log *n*) implementation of the set union problem requires Ω(*m* α(*m*, *n*)) time to execute *m* Find's and *n*−1 Union's, beginning with *n* singleton sets.
7. [↑](./Disjoint-set_data_structure#cite_ref-Galil1991_7-0) Galil, Z.; Italiano, G. (1991). "Data structures and algorithms for disjoint set union problems". *ACM Computing Surveys*. **23** (3): 319–344. [doi](./Doi_(identifier)):[10.1145/116873.116878](https://doi.org/10.1145%2F116873.116878). [S2CID](./S2CID_(identifier)) [207160759](https://api.semanticscholar.org/CorpusID:207160759).
8. [↑](./Disjoint-set_data_structure#cite_ref-Anderson1994_8-0) Anderson, Richard J.; Woll, Heather (1994). *Wait-free Parallel Algorithms for the Union-Find Problem*. 23rd ACM Symposium on Theory of Computing. pp. 370–380. [doi](./Doi_(identifier)):[10.1145/103418.103458](https://doi.org/10.1145%2F103418.103458).
9. [↑](./Disjoint-set_data_structure#cite_ref-Conchon2007_9-0) Conchon, Sylvain; Filliâtre, Jean-Christophe (October 2007). "A Persistent Union-Find Data Structure". [*ACM SIGPLAN Workshop on ML*](https://www.lri.fr/~filliatr/puf/). Freiburg, Germany.
10. [↑](./Disjoint-set_data_structure#cite_ref-10) Harold N. Gabow, Robert Endre Tarjan, "A linear-time algorithm for a special case of disjoint set union," Journal of Computer and System Sciences, Volume 30, Issue 2, 1985, pp. 209–221, ISSN 0022-0000, [https://doi.org/10.1016/0022-0000(85)90014-5](https://doi.org/10.1016/0022-0000(85)90014-5)
11. [1](./Disjoint-set_data_structure#cite_ref-Cormen2009_11-0) [2](./Disjoint-set_data_structure#cite_ref-Cormen2009_11-1) [3](./Disjoint-set_data_structure#cite_ref-Cormen2009_11-2) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2009). "Chapter 21: Data structures for Disjoint Sets". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (Third ed.). MIT Press. pp. 571–572. [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8).
12. [↑](./Disjoint-set_data_structure#cite_ref-12) [Raimund Seidel](./Raimund_Seidel), Micha Sharir. "Top-down analysis of path compression", SIAM J. Comput. 34(3):515–525, 2005
13. [↑](./Disjoint-set_data_structure#cite_ref-13) Tarjan, Robert Endre (1975). ["Efficiency of a Good But Not Linear Set Union Algorithm"](http://portal.acm.org/citation.cfm?id=321884). *Journal of the ACM*. **22** (2): 215–225. [doi](./Doi_(identifier)):[10.1145/321879.321884](https://doi.org/10.1145%2F321879.321884). [hdl](./Hdl_(identifier)):[1813/5942](https://hdl.handle.net/1813%2F5942). [S2CID](./S2CID_(identifier)) [11105749](https://api.semanticscholar.org/CorpusID:11105749).
14. [↑](./Disjoint-set_data_structure#cite_ref-14) Hopcroft, J. E.; Ullman, J. D. (1973). "Set Merging Algorithms". *SIAM Journal on Computing*. **2** (4): 294–303. [doi](./Doi_(identifier)):[10.1137/0202024](https://doi.org/10.1137%2F0202024).
15. [↑](./Disjoint-set_data_structure#cite_ref-15) [Robert E. Tarjan](./Robert_E._Tarjan) and [Jan van Leeuwen](./Jan_van_Leeuwen). Worst-case analysis of set union algorithms. Journal of the ACM, 31(2):245–281, 1984.
16. [↑](./Disjoint-set_data_structure#cite_ref-16) Blum, Norbert (1985). "On the Single-Operation Worst-Case Time Complexity of the Disjoint Set Union Problem". *2nd Symp. On Theoretical Aspects of Computer Science*: 32–38.
17. [↑](./Disjoint-set_data_structure#cite_ref-17) Alstrup, Stephen; Ben-Amram, Amir M.; Rauhe, Theis (1999). "Worst-case and amortised optimality in union-find (Extended abstract)". *Proceedings of the thirty-first annual ACM symposium on Theory of Computing*. pp. 499–506. [doi](./Doi_(identifier)):[10.1145/301250.301383](https://doi.org/10.1145%2F301250.301383). [ISBN](./ISBN_(identifier)) [1581130678](./Special:BookSources/1581130678). [S2CID](./S2CID_(identifier)) [100111](https://api.semanticscholar.org/CorpusID:100111).
18. [↑](./Disjoint-set_data_structure#cite_ref-18) Alstrup, Stephen; Thorup, Mikkel; Gørtz, Inge Li; Rauhe, Theis; Zwick, Uri (2014). "Union-Find with Constant Time Deletions". *ACM Transactions on Algorithms*. **11** (1): 6:1–6:28. [doi](./Doi_(identifier)):[10.1145/2636922](https://doi.org/10.1145%2F2636922). [S2CID](./S2CID_(identifier)) [12767012](https://api.semanticscholar.org/CorpusID:12767012).
19. [↑](./Disjoint-set_data_structure#cite_ref-19) Ben-Amram, Amir M.; Yoffe, Simon (2011). "A simple and efficient Union-Find-Delete algorithm". *Theoretical Computer Science*. **412** (4–5): 487–492. [doi](./Doi_(identifier)):[10.1016/j.tcs.2010.11.005](https://doi.org/10.1016%2Fj.tcs.2010.11.005).
20. [1](./Disjoint-set_data_structure#cite_ref-WT_20-0) [2](./Disjoint-set_data_structure#cite_ref-WT_20-1) Westbrook, Jeffery R.; Tarjan, Robert E. (1989). "Amortized Analysis of Algorithms for Set Union with Backtracking". *SIAM Journal on Computing*. **18** (1): 1–11. [doi](./Doi_(identifier)):[10.1137/0218001](https://doi.org/10.1137%2F0218001).
21. [↑](./Disjoint-set_data_structure#cite_ref-Knight1989_21-0) Knight, Kevin (1989). ["Unification: A multidisciplinary survey"](http://www.isi.edu/natural-language/people/unification-knight.pdf) (PDF). *ACM Computing Surveys*. **21**: 93–124. [doi](./Doi_(identifier)):[10.1145/62029.62030](https://doi.org/10.1145%2F62029.62030). [S2CID](./S2CID_(identifier)) [14619034](https://api.semanticscholar.org/CorpusID:14619034).

 

## External links

 
- [C++ implementation](https://www.boost.org/doc/libs/1_31_0/libs/disjoint_sets/disjoint_sets.html), part of the [Boost C++ libraries](./Boost_C++_libraries)
- [Java implementation](https://github.com/jgrapht/jgrapht/blob/master/jgrapht-core/src/main/java/org/jgrapht/alg/util/UnionFind.java), part of [JGraphT library](https://jgrapht.org/)
- [Javascript implementation](https://the-algorithms.com/algorithm/union-find)
- [Python implementation](http://code.activestate.com/recipes/215912-union-find-data-structure/)

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |