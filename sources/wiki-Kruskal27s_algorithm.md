---
source: https://en.wikipedia.org/wiki/Kruskal%27s_algorithm
fetched: 2026-06-19
---

Minimum spanning forest algorithm that greedily adds edges Not to be confused with [Kruskal's principle](./Kruskal's_principle). 
| Animation of Kruskal's algorithm on acomplete graphwith weights based on Euclidean distance |
| --- |
| Class | Minimum spanning tree algorithm |
| Data structure | Graph |
| Worst-caseperformance | O(|E|log⁡|V|){\displaystyle O(|E|\log |V|)} |

 

**Kruskal's algorithm**[[1]](./Kruskal's_algorithm#cite_note-1) finds a [minimum spanning forest](./Minimum_spanning_tree) of an undirected [edge-weighted graph](./Weighted_graph). If the graph is [connected](./Connectivity_(graph_theory)), it finds a [minimum spanning tree](./Minimum_spanning_tree). It is a [greedy algorithm](./Greedy_algorithm) that in each step adds to the forest the lowest-weight edge that will not form a [cycle](./Cycle_(graph_theory)).[[2]](./Kruskal's_algorithm#cite_note-:0-2) The key steps of the algorithm are [sorting](./Sorting) and the use of a [disjoint-set data structure](./Disjoint-set_data_structure) to detect cycles. Its running time is dominated by the time to sort all of the graph edges by their weight.

 

A minimum spanning tree of a connected weighted graph is a connected subgraph, without cycles, for which the sum of the weights of all the edges in the subgraph is minimal. For a disconnected graph, a minimum spanning forest is composed of a minimum spanning tree for each [connected component](./Connected_component_(graph_theory)).

 

This algorithm was first published by [Joseph Kruskal](./Joseph_Kruskal) in 1956,[[3]](./Kruskal's_algorithm#cite_note-3) and was rediscovered soon afterward by [Loberman & Weinberger (1957)](./Kruskal's_algorithm#CITEREFLobermanWeinberger1957).[[4]](./Kruskal's_algorithm#cite_note-4) Other algorithms for this problem include [Prim's algorithm](./Prim's_algorithm), [Borůvka's algorithm](./Borůvka's_algorithm), and the [reverse-delete algorithm](./Reverse-delete_algorithm).

 

## Algorithm

 

The algorithm performs the following steps:

 
- Create a forest (a set of trees) initially consisting of a separate single-vertex tree for each vertex in the input graph.
- Sort the graph edges by weight.
- Loop through the edges of the graph, in ascending sorted order by their weight. For each edge:

- Test whether adding the edge to the current forest would create a cycle.
- If not, add the edge to the forest, combining two trees into a single tree.

 

At the termination of the algorithm, the forest forms a minimum spanning forest of the graph. If the graph is connected, the forest has a single component and forms a minimum spanning tree.

 

## Pseudocode

 

The following code is implemented with a [disjoint-set data structure](./Disjoint-set_data_structure). It represents the forest *F* as a set of undirected edges, and uses the disjoint-set data structure to efficiently determine whether two vertices are part of the same tree.

 
```
function Kruskal(Graph G) is
    F:= ∅
    for each v in G.Vertices do
        MAKE-SET(v)

    for each {u, v} in G.Edges ordered by increasing weight({u, v}) do
        if FIND-SET(u) ≠ FIND-SET(v) then
            F := F ∪ { {u, v} }
            UNION(FIND-SET(u), FIND-SET(v))
    return F
```
 

## Complexity

 

For a graph with E edges and V vertices, Kruskal's algorithm can be shown to run in time *O*(*E* log *E*) time, with simple data structures. This time bound is often written instead as *O*(*E* log *V*), which is equivalent for graphs with no isolated vertices, because for these graphs *V* / 2 ≤ *E* < *V*2 and the logarithms of V and V2 are again within a constant factor of each other.

 

To achieve this bound, first sort the edges by weight using a [comparison sort](./Comparison_sort) in *O*(*E* log *E*) time. Once sorted, it is possible to loop through the edges in sorted order in constant time per edge. Next, use a [disjoint-set data structure](./Disjoint-set_data_structure), with a set of vertices for each component, to keep track of which vertices are in which components. Creating this structure, with a separate set for each vertex, takes V operations and *O*(*V*) time. The final iteration through all edges performs two find operations and possibly one union operation per edge. These operations take [amortized time](./Amortized_time) *O*(*α*(*V*)) time per operation, giving worst-case total time *O*(*E* *α*(*V*)) for this loop, where α is the extremely slowly growing [inverse Ackermann function](./Inverse_Ackermann_function). This part of the time bound is much smaller than the time for the sorting step, so the total time for the algorithm can be simplified to the time for the sorting step.

 

In cases where the edges are already sorted, or where they have small enough integer weight to allow [integer sorting](./Integer_sorting) algorithms such as [counting sort](./Counting_sort) or [radix sort](./Radix_sort) to sort them in linear time, the disjoint set operations are the slowest remaining part of the algorithm and the total time is *O*(*E* *α*(*V*)).

 

## Example

 
| Image | Description |
| --- | --- |
|  | ADandCEare the shortest edges, with length 5, andADhas beenarbitrarilychosen, so it is highlighted. |
|  | CEis now the shortest edge that does not form a cycle, with length 5, so it is highlighted as the second edge. |
|  | The next edge,DFwith length 6, is highlighted using much the same method. |
|  | The next-shortest edges areABandBE, both with length 7.ABis chosen arbitrarily, and is highlighted. The edgeBDhas been highlighted in red, because there already exists a path (in green) betweenBandD, so it would form a cycle (ABD) if it were chosen. |
|  | The process continues to highlight the next-smallest edge,BEwith length 7. Many more edges are highlighted in red at this stage:BCbecause it would form the loopBCE,DEbecause it would form the loopDEBA, andFEbecause it would formFEBAD. |
|  | Finally, the process finishes with the edgeEGof length 9, and the minimum spanning tree is found. |

 

## Proof of correctness

 

The proof consists of two parts. First, it is proved that the algorithm produces a [spanning tree](./Spanning_tree). Second, it is proved that the constructed spanning tree is of minimal weight.

 

### Spanning tree

 

Let     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b) be a connected, weighted graph and let     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) be the subgraph of     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b) produced by the algorithm.     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) cannot have a cycle, as by definition an edge is not added if it results in a cycle.     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) cannot be disconnected, since the first encountered edge that joins two components of     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) would have been added by the algorithm. Thus,     Y   {\displaystyle Y}  ![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f) is a spanning tree of     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b).

 

### Minimality

 

We show that the following proposition ***P*** is true by [induction](./Mathematical_induction): If *F* is the set of edges chosen at any stage of the algorithm, then there is some minimum spanning tree that contains *F* and none of the edges rejected by the algorithm.

 
- Clearly ***P*** is true at the beginning, when *F* is empty: any minimum spanning tree will do, and there exists one because a weighted connected graph always has a minimum spanning tree.
- Now assume ***P*** is true for some non-final edge set *F* and let *T* be a minimum spanning tree that contains *F*.

- If the next chosen edge *e* is also in *T*, then ***P*** is true for *F* + *e*.
- Otherwise, if *e* is not in *T* then *T* + *e* has a cycle *C*. The cycle *C* contains edges which do not belong to  *F* + *e*, since *e* does not form a cycle when added to *F* but does in *T*.  Let *f* be an edge which is in *C* but not in *F* + *e*.  Note that *f* also belongs to *T*, since *f* belongs to *T* + *e* but not *F* + *e*. By  ***P***, *f* has not been considered by the algorithm. *f* must therefore have a weight at least as large as *e*. Then *T* − *f* + *e* is a tree, and it has the same or less weight as *T*. However since *T* is a minimum spanning tree then *T* − *f* + *e* has the same weight as *T*, otherwise we get a contradiction and *T* would not be a minimum spanning tree. So *T* − *f* + *e* is a minimum spanning tree containing *F* + *e* and again ***P*** holds.

- Therefore, by the principle of induction, ***P*** holds when *F* has become a spanning tree, which is only possible if *F* is a minimum spanning tree itself.

 

## Parallel algorithm

 

Kruskal's algorithm is inherently sequential and hard to parallelize. It is, however, possible to perform the initial sorting of the edges in parallel or, alternatively, to use a parallel implementation of a [binary heap](./Binary_heap) to extract the minimum-weight edge in every iteration.[[5]](./Kruskal's_algorithm#cite_note-5)
As parallel sorting is possible in time     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) on     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) processors,[[6]](./Kruskal's_algorithm#cite_note-6) the runtime of Kruskal's algorithm can be reduced to *O*(*E* α(*V*)), where α again is the inverse of the single-valued [Ackermann function](./Ackermann_function).

 

A variant of Kruskal's algorithm, named Filter-Kruskal, has been described by Osipov et al.[[7]](./Kruskal's_algorithm#cite_note-osipov2009-7) and is better suited for parallelization. The basic idea behind Filter-Kruskal is to partition the edges in a similar way to [quicksort](./Quicksort) and filter out edges that connect vertices of the same tree to reduce the cost of sorting. The following [pseudocode](./Pseudocode) demonstrates this.

 
```
function filter_kruskal(G) is
    if |G.E| < kruskal_threshold:
        return kruskal(G)
    pivot = choose_random(G.E)
    E≤, E> = partition(G.E, pivot)
    A = filter_kruskal(E≤)
    E> = filter(E>)
    A = A ∪ filter_kruskal(E>)
    return A

function partition(E, pivot) is
    E≤ = ∅, E> = ∅
    foreach (u, v) in E do
        if weight(u, v) ≤ pivot then
            E≤ = E≤ ∪ {(u, v)}
        else
            E> = E> ∪ {(u, v)}
    return E≤, E>

function filter(E) is
    Ef = ∅
    foreach (u, v) in E do
        if find_set(u) ≠ find_set(v) then
            Ef = Ef ∪ {(u, v)}
    return Ef
```
 

Filter-Kruskal lends itself better to parallelization as sorting, filtering, and partitioning can easily be performed in parallel by distributing the edges between the processors.[[7]](./Kruskal's_algorithm#cite_note-osipov2009-7)

 

Finally, other variants of a parallel implementation of Kruskal's algorithm have been explored. Examples include a scheme that uses helper threads to remove edges that are definitely not part of the MST in the background,[[8]](./Kruskal's_algorithm#cite_note-8) and a variant which runs the sequential algorithm on *p* subgraphs, then merges those subgraphs until only one, the final MST, remains.[[9]](./Kruskal's_algorithm#cite_note-9)

 

## See also

 
- [Dijkstra's algorithm](./Dijkstra's_algorithm)
- [Greedy geometric spanner](./Greedy_geometric_spanner)
- [Single-linkage clustering](./Single-linkage_clustering)

 

## References

  
1. [↑](./Kruskal's_algorithm#cite_ref-1) Kleinberg, Jon (2006). *Algorithm design*. Éva Tardos. Boston: Pearson/Addison-Wesley. pp. 142–151. [ISBN](./ISBN_(identifier)) [0-321-29535-8](./Special:BookSources/0-321-29535-8). [OCLC](./OCLC_(identifier)) [57422612](https://search.worldcat.org/oclc/57422612).
2. [↑](./Kruskal's_algorithm#cite_ref-:0_2-0) Cormen, Thomas; Charles E Leiserson, Ronald L Rivest, Clifford Stein (2009). [*Introduction To Algorithms*](https://archive.org/details/introductiontoal00corm_805) (Third ed.). MIT Press. pp. [631](https://archive.org/details/introductiontoal00corm_805/page/n651). [ISBN](./ISBN_(identifier)) [978-0262258104](./Special:BookSources/978-0262258104).`{{cite book}}`:  CS1 maint: multiple names: authors list ([link](./Category:CS1_maint:_multiple_names:_authors_list))
3. [↑](./Kruskal's_algorithm#cite_ref-3) [Kruskal, J. B.](./Joseph_Kruskal) (1956). ["On the shortest spanning subtree of a graph and the traveling salesman problem"](https://doi.org/10.1090%2FS0002-9939-1956-0078686-7). *[Proceedings of the American Mathematical Society](./Proceedings_of_the_American_Mathematical_Society)*. **7** (1): 48–50. [doi](./Doi_(identifier)):[10.1090/S0002-9939-1956-0078686-7](https://doi.org/10.1090%2FS0002-9939-1956-0078686-7). [JSTOR](./JSTOR_(identifier)) [2033241](https://www.jstor.org/stable/2033241).
4. [↑](./Kruskal's_algorithm#cite_ref-4) Loberman, H.; Weinberger, A. (October 1957). ["Formal Procedures for connecting terminals with a minimum total wire length"](https://doi.org/10.1145%2F320893.320896). *Journal of the ACM*. **4** (4): 428–437. [doi](./Doi_(identifier)):[10.1145/320893.320896](https://doi.org/10.1145%2F320893.320896). [S2CID](./S2CID_(identifier)) [7320964](https://api.semanticscholar.org/CorpusID:7320964).
5. [↑](./Kruskal's_algorithm#cite_ref-5) Quinn, Michael J.; Deo, Narsingh (1984). ["Parallel graph algorithms"](https://doi.org/10.1145%2F2514.2515). *ACM Computing Surveys*. **16** (3): 319–348. [doi](./Doi_(identifier)):[10.1145/2514.2515](https://doi.org/10.1145%2F2514.2515). [S2CID](./S2CID_(identifier)) [6833839](https://api.semanticscholar.org/CorpusID:6833839).
6. [↑](./Kruskal's_algorithm#cite_ref-6) Grama, Ananth; Gupta, Anshul; Karypis, George; Kumar, Vipin (2003). *Introduction to Parallel Computing*. Addison-Wesley. pp. 412–413. [ISBN](./ISBN_(identifier)) [978-0201648652](./Special:BookSources/978-0201648652).
7. [1](./Kruskal's_algorithm#cite_ref-osipov2009_7-0) [2](./Kruskal's_algorithm#cite_ref-osipov2009_7-1) Osipov, Vitaly; Sanders, Peter; Singler, Johannes (2009). ["The filter-kruskal minimum spanning tree algorithm"](https://doi.org/10.1137%2F1.9781611972894.5). *Proceedings of the Eleventh Workshop on Algorithm Engineering and Experiments (ALENEX). Society for Industrial and Applied Mathematics*: 52–61. [doi](./Doi_(identifier)):[10.1137/1.9781611972894.5](https://doi.org/10.1137%2F1.9781611972894.5). [ISBN](./ISBN_(identifier)) [978-0-89871-930-7](./Special:BookSources/978-0-89871-930-7).
8. [↑](./Kruskal's_algorithm#cite_ref-8) Katsigiannis, Anastasios; Anastopoulos, Nikos; Konstantinos, Nikas; Koziris, Nectarios (2012). "An Approach to Parallelize Kruskal's Algorithm Using Helper Threads". [*2012 IEEE 26th International Parallel and Distributed Processing Symposium Workshops & PhD Forum*](http://tarjomefa.com/wp-content/uploads/2017/10/7793-English-TarjomeFa.pdf) (PDF). pp. 1601–1610. [doi](./Doi_(identifier)):[10.1109/IPDPSW.2012.201](https://doi.org/10.1109%2FIPDPSW.2012.201). [ISBN](./ISBN_(identifier)) [978-1-4673-0974-5](./Special:BookSources/978-1-4673-0974-5). [S2CID](./S2CID_(identifier)) [14430930](https://api.semanticscholar.org/CorpusID:14430930).
9. [↑](./Kruskal's_algorithm#cite_ref-9) Lončar, Vladimir; Škrbić, Srdjan; Balaž, Antun (2014). ["Parallelization of Minimum Spanning Tree Algorithms Using Distributed Memory Architectures"](https://www.researchgate.net/publication/235994104). *Transactions on Engineering Technologies*. pp. 543–554. [doi](./Doi_(identifier)):[10.1007/978-94-017-8832-8_39](https://doi.org/10.1007%2F978-94-017-8832-8_39). [ISBN](./ISBN_(identifier)) [978-94-017-8831-1](./Special:BookSources/978-94-017-8831-1).

 
- [Thomas H. Cormen](./Thomas_H._Cormen), [Charles E. Leiserson](./Charles_E._Leiserson), [Ronald L. Rivest](./Ronald_L._Rivest), and [Clifford Stein](./Clifford_Stein). *[Introduction to Algorithms](./Introduction_to_Algorithms)*, Second Edition. MIT Press and McGraw-Hill, 2001. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). Section 23.2: The algorithms of Kruskal and Prim, pp. 567–574.
- [Michael T. Goodrich](./Michael_T._Goodrich) and [Roberto Tamassia](./Roberto_Tamassia). *Data Structures and Algorithms in Java*, Fourth Edition. John Wiley & Sons, Inc., 2006. [ISBN](./ISBN_(identifier)) [0-471-73884-0](./Special:BookSources/0-471-73884-0). Section 13.7.1: Kruskal's Algorithm, pp. 632..

 

## External links

 
- [Data for the article's example](https://github.com/carlschroedl/kruskals-minimum-spanning-tree-algorithm-example-data).
- [Gephi Plugin For Calculating a Minimum Spanning Tree](https://gephi.org/plugins/#/plugin/spanning-tree-plugin) [source code](https://github.com/carlschroedl/gephi-plugins/tree/minimum-spanning-tree-plugin/modules/MinimumSpanningTree).
- [Kruskal's Algorithm with example and program in c++](http://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-using-stl-in-c/)
- [Kruskal's Algorithm code in C++ as applied to random numbers](https://meyavuz.wordpress.com/2017/03/11/how-does-kruskals-algorithm-progress/)
- [Kruskal's Algorithm code in Python with explanation](https://gist.github.com/DanilAndreev/e519d77eff91f03f09616c9170db7941)
- [Kruskal's Algorithm code in C with Explanation and Example](https://www.ccbp.in/blog/articles/kruskal-algorithm-in-c)
- [The Implementation of Kruskal’s Algorithm for Minimum Spanning Tree in a Graph](//doi.org/10.1051/matecconf/202134801001)
- [Comparative Performance Analysis of Kruskal and Prim MST Algorithms](https://web.archive.org/web/20210916154538/https://ripublication.com/irph/ijert20/ijertv13n12_181.pdf)

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |