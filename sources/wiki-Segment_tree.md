---
source: https://en.wikipedia.org/wiki/Segment_tree
fetched: 2026-06-19
---

Computer science data structure Not to be confused with [interval tree](./Interval_tree). 
|  | This article has multiple issues.Please helpimprove itor discuss these issues on thetalk page.(Learn how and when to remove these messages)This articlerelies largely or entirely on asingle source.Relevant discussion may be found on thetalk page. Please helpimprove this articlebyintroducing  citations to additional sources.Find sources:"Segment tree"–news·newspapers·books·scholar·JSTOR(November 2007)This articlemay be too technical for most readers to understand.Pleasehelp improve ittomake it understandable to non-experts, without removing the technical details.(October 2020)(Learn how and when to remove this message)(Learn how and when to remove this message) |  | This articlerelies largely or entirely on asingle source.Relevant discussion may be found on thetalk page. Please helpimprove this articlebyintroducing  citations to additional sources.Find sources:"Segment tree"–news·newspapers·books·scholar·JSTOR(November 2007) |  | This articlemay be too technical for most readers to understand.Pleasehelp improve ittomake it understandable to non-experts, without removing the technical details.(October 2020)(Learn how and when to remove this message) |
| --- | --- | --- | --- | --- | --- |
|  | This articlerelies largely or entirely on asingle source.Relevant discussion may be found on thetalk page. Please helpimprove this articlebyintroducing  citations to additional sources.Find sources:"Segment tree"–news·newspapers·books·scholar·JSTOR(November 2007) |
|  | This articlemay be too technical for most readers to understand.Pleasehelp improve ittomake it understandable to non-experts, without removing the technical details.(October 2020)(Learn how and when to remove this message) |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d1/Segment_tree.svg/330px-Segment_tree.svg.png)](./File:Segment_tree.svg)Graphic example of the structure of the segment tree. This instance is built for the segments shown at the bottom. 

In [computer science](./Computer_science), the **segment tree** is a [data structure](./Data_structure) used for storing information about [intervals](./Interval_(mathematics)) or segments. It allows querying which of the stored segments contain a given point. A similar data structure is the [interval tree](./Interval_tree).

 

A segment tree for a set I of *n* intervals uses [*O*](./Big_O_notation)(*n* log *n*) storage and can be built in *O*(*n* log *n*) time. Segment trees support searching for all the intervals that contain a query point in time *O*(log *n* + *k*), *k* being the number of retrieved intervals or segments.[[1]](./Segment_tree#cite_note-Schwarzkopf1-1)

 

Applications of the segment tree are in the areas of [computational geometry](./Computational_geometry), [geographic information systems](./Geographic_information_systems) and [machine learning](./Machine_learning).

 

The segment tree can be generalized to higher [dimension](./Dimension) spaces.

 

## Definition

 

### Description

 

Let I be a set of intervals, or segments. Let *p*1, *p*2, ..., *pm* be the list of distinct interval endpoints, sorted from left to right. Consider the partitioning of the real line induced by those points. The regions of this partitioning are called *elementary intervals*. Thus, the elementary intervals are, from left to right:

     ( − −  ∞ ∞  ,  p  1   ) , [  p  1   ,  p  1   ] , (  p  1   ,  p  2   ) , [  p  2   ,  p  2   ] , … …  , (  p  m − −  1   ,  p  m   ) , [  p  m   ,  p  m   ] , (  p  m   , + ∞ ∞  )   {\displaystyle (-\infty ,p_{1}),[p_{1},p_{1}],(p_{1},p_{2}),[p_{2},p_{2}],\dots ,(p_{m-1},p_{m}),[p_{m},p_{m}],(p_{m},+\infty )}  ![{\displaystyle (-\infty ,p_{1}),[p_{1},p_{1}],(p_{1},p_{2}),[p_{2},p_{2}],\dots ,(p_{m-1},p_{m}),[p_{m},p_{m}],(p_{m},+\infty )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7d38ca3ad16c39bc9f67a6e0601c8e82ff59358) 

That is, the list of elementary intervals consists of open intervals between two consecutive endpoints *pi* and *p**i*+1, alternated with closed intervals consisting of a single endpoint. Single points are treated themselves as intervals because the answer to a query is not necessarily the same at the interior of an elementary interval and its endpoints.[[2]](./Segment_tree#cite_note-2)

 

Given a set I of intervals, or segments, a segment tree *T* for I is structured as follows:

 
- *T* is a [binary tree](./Binary_tree).
- Its [leaves](./Leaf_node) correspond to the elementary intervals induced by the endpoints in I, in an ordered way: the leftmost leaf corresponds to the leftmost interval, and so on. The elementary interval corresponding to a leaf *v* is denoted Int(*v*).
- The [internal nodes](./Internal_node) of *T*  correspond to intervals that are the [union](./Union_(set_theory))  of elementary intervals: the interval Int(*N*) corresponding to node *N* is the union of the intervals corresponding to the leaves of the tree rooted at *N*. That implies that Int(*N*) is the union of the intervals of its two children.
- Each node or leaf *v* in *T* stores the interval Int(*v*) and a set   of intervals, in some data structure. This canonical subset of node *v* contains the intervals [*x*, *x′*] from I such that [*x*, *x′*] contains Int(*v*) and does not contain Int(parent(*v*)). That is, each node in *T* stores the segments that span through its interval, but do not span through the interval of its parent.[[3]](./Segment_tree#cite_note-3)

  

### Construction

 

A segment tree from the set of segments I, can be built as follows. First, the endpoints of the intervals in I are sorted. The elementary intervals are obtained from that. Then, a balanced binary tree is built on the elementary intervals, and for each node *v* it is determined the interval Int(*v*) it represents. It remains to compute the canonical subsets for the nodes. To achieve this, the intervals in I are inserted one by one into the segment tree. An interval *X* = [*x*, *x′*] can be inserted in a subtree rooted at *T*, using the following procedure:[[4]](./Segment_tree#cite_note-4)

 
- If Int(*T*) is contained in *X* then store *X* at *T*, and finish.
- Else:

- If *X* intersects the interval of the left child of *T*, then insert *X* in that child, recursively.
- If *X* intersects the interval of the right child of *T*, then insert *X* in that child, recursively.

 

The complete construction operation takes *O*(*n* log *n*) time, *n* being the number of segments in I.

 **Proof** Sorting the endpoints takes *O*(*n* log *n*). Building a balanced binary tree from the sorted endpoints, takes linear time on *n*. The insertion of an interval *X* = [*x*, *x′*] into the tree, costs O(log *n*). **Proof** 

Visiting every node takes constant time (assuming that canonical subsets are stored in a simple data structure like a [linked list](./Linked_list)). When we visit node *v*, we either store *X* at *v*, or Int(*v*) contains an endpoint of *X*. As proved above, an interval is stored at most twice at each level of the tree. There is also at most one node at every level whose corresponding interval contains *x*, and one node whose interval contains *x′*. So, at most four nodes per level are visited. Since there are *O*(log *n*) levels, the total cost of the insertion is *O*(log *n*).[[1]](./Segment_tree#cite_note-Schwarzkopf1-1)

   

### Query

 

A query for a segment tree receives a point *qx*(should be one of the leaves of tree), and retrieves a list of all the segments stored which contain the point *qx*.

 

Formally stated; given a node (subtree) *v* and a query point *qx*, the query can be done using the following algorithm:

 
1. Report all the intervals in *I*(*v*).
2. If *v* is not a leaf:

- If *qx* is in Int(left child of *v*) then

- Perform a query in the left child of *v*.

- If *qx* is in Int(right child of *v*) then

- Perform a query in the right child of *v*.

 

In a segment tree that contains *n* intervals, those containing a given query point can be reported in *O*(log *n* + *k*) time, where *k* is the number of reported intervals.

 **Proof** 

The query algorithm visits one node per level of the tree, so *O*(log *n*) nodes in total. On the other hand, at a node *v*, the segments in I are reported in *O*(1 + *kv*) time, where *kv* is the number of intervals at node *v*, reported. The sum of all the *kv* for all nodes *v* visited, is *k*, the number of reported segments.[[5]](./Segment_tree#cite_note-Schwarzkopf2-5)

  

### Storage requirements

 

A segment tree *T* on a set I of *n* intervals uses *O*(*n* log *n*) storage.

  

***Lemma***— Any interval [*x*, *x′*] of I is stored in the canonical set for at most two nodes at the same depth.

  **Proof** 

Let *v*1, *v*2, *v*3 be the three nodes at the same depth, numbered from left to right; and let p(*v*) be the parent node of any given node *v*. Suppose [*x*, *x′*] is stored at *v*1 and *v*3. This means that [*x*, *x′*] spans the whole interval from the left endpoint of Int(*v*1) to the right endpoint of Int(*v*3). Note that all segments at a particular level are non-overlapping and ordered from left to right: this is true by construction for the level containing the leaves, and the property is not lost when moving from any level to the one above it by combining pairs of adjacent segments. Now either parent(*v*2) = parent(*v*1), or the former is to the right of the latter (edges in the tree do not cross). In the first case, Int(parent(*v*2))'s leftmost point is the same as Int(*v*1)'s leftmost point; in the second case, Int(parent(*v*2))'s leftmost point is to the right of Int(parent(*v*1))'s rightmost point, and therefore also to the right of Int(*v*1)'s rightmost point. In both cases, Int(parent(*v*2)) begins at or to the right of Int(*v*1)'s leftmost point. Similar reasoning shows that Int(parent(*v*2)) ends at or to the left of Int(*v*3)'s rightmost point. Int(parent(*v*2)) must therefore be contained in [*x*, *x′*]; hence, [*x*, *x′*] will not be stored at *v*2.

  The set I has at most 4*n* + 1 elementary intervals. Because *T* is a binary balanced tree with at most 4*n* + 1 leaves, its height is O(log *n*). Since any interval is stored at most twice at a given depth of the tree, that the total amount of storage is *O*(*n* log *n*).[[5]](./Segment_tree#cite_note-Schwarzkopf2-5) 

### Generalization for higher dimensions

 

The segment tree can be generalized to higher dimension spaces, in the form of multi-level segment trees. In higher dimensional versions, the segment tree stores a collection of axis-parallel (hyper-)rectangles, and can retrieve the rectangles that contain a given query point. The structure uses *O*(*n* log*d* *n*) storage, and answers queries in *O*(log*d* *n*) time.

 

The use of [fractional cascading](./Fractional_cascading) lowers the query time bound by a logarithmic factor. The use of the [interval tree](./Interval_tree) on the deepest level of associated structures lowers the storage bound by a logarithmic factor.[[6]](./Segment_tree#cite_note-Schwarzkopf3-6)

 

## Notes

 

A query that asks for all the intervals containing a given point is often referred as a *stabbing query*.[[7]](./Segment_tree#cite_note-Schwarzkopf4-7)

 

The segment tree is less efficient than the [interval tree](./Interval_tree) for range queries in one dimension, due to its higher storage requirement: *O*(*n* log *n*) against the O(*n*) of the interval tree. The importance of the segment tree is that the segments within each node's canonical subset can be stored in any arbitrary manner.[[7]](./Segment_tree#cite_note-Schwarzkopf4-7)

 

For *n* intervals whose endpoints are in a small integer range (e.g., in the range [1,...,*O*(*n*)]), optimal data structures[*[which?](./Wikipedia:Avoid_weasel_words)*] exist with a linear preprocessing time and query time *O*(1 + *k*) for reporting all *k* intervals containing a given query point.

 

Another advantage of the segment tree is that it can easily be adapted to counting queries; that is, to report the number of segments containing a given point, instead of reporting the segments themselves. Instead of storing the intervals in the canonical subsets, it can simply store the number of them. Such a segment tree uses linear storage, and requires an *O*(log *n*) query time, so it is optimal.[[8]](./Segment_tree#cite_note-8)

 

Higher dimensional versions of the interval tree and the [priority search tree](./Priority_search_tree) do not exist; that is, there is no clear extension of these structures that solves the analogous problem in higher dimensions. But the structures can be used as associated structure of segment trees.[[6]](./Segment_tree#cite_note-Schwarzkopf3-6)

 

## History

 
|  | This sectionneeds expansion. You can help byadding missing information.(November 2007) |
| --- | --- |

 

The segment tree was invented by [Jon Bentley](./Jon_Bentley_(computer_scientist)) in 1977; in "Solutions to Klee’s rectangle problems".[[7]](./Segment_tree#cite_note-Schwarzkopf4-7)

 

## References

  
1. [1](./Segment_tree#cite_ref-Schwarzkopf1_1-0) [2](./Segment_tree#cite_ref-Schwarzkopf1_1-1) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), p. 227)
2. [↑](./Segment_tree#cite_ref-2) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), p. 224)
3. [↑](./Segment_tree#cite_ref-3) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), pp. 225–226)
4. [↑](./Segment_tree#cite_ref-4) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), pp. 226–227)
5. [1](./Segment_tree#cite_ref-Schwarzkopf2_5-0) [2](./Segment_tree#cite_ref-Schwarzkopf2_5-1) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), p. 226)
6. [1](./Segment_tree#cite_ref-Schwarzkopf3_6-0) [2](./Segment_tree#cite_ref-Schwarzkopf3_6-1) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), p. 230)
7. [1](./Segment_tree#cite_ref-Schwarzkopf4_7-0) [2](./Segment_tree#cite_ref-Schwarzkopf4_7-1) [3](./Segment_tree#cite_ref-Schwarzkopf4_7-2) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), p. 229)
8. [↑](./Segment_tree#cite_ref-8) ([de Berg et al. 2000](./Segment_tree#CITEREFde_Bergvan_KreveldOvermarsSchwarzkopf2000), pp. 229–230)

 

## Sources cited

 
- de Berg, Mark; van Kreveld, Marc; Overmars, Mark; Schwarzkopf, Otfried (2000). "More Geometric Data Structures". [*Computational Geometry: algorithms and applications*](https://archive.org/details/computationalgeo00berg) (2nd ed.). Springer-Verlag Berlin Heidelberg New York. [doi](./Doi_(identifier)):[10.1007/978-3-540-77974-2](https://doi.org/10.1007%2F978-3-540-77974-2). [ISBN](./ISBN_(identifier)) [3-540-65620-0](./Special:BookSources/3-540-65620-0).
- [http://www.cs.nthu.edu.tw/~wkhon/ds/ds10/tutorial/tutorial6.pdf](http://www.cs.nthu.edu.tw/~wkhon/ds/ds10/tutorial/tutorial6.pdf)

 

## External links

 
- [Segment Tree – CP-Algorithms](https://cp-algorithms.com/data_structures/segment_tree.html)

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |