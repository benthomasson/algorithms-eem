---
source: https://en.wikipedia.org/wiki/Prim%27s_algorithm
fetched: 2026-06-19
---

Method for finding minimum spanning trees [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/9b/PrimAlgDemo.gif/250px-PrimAlgDemo.gif)](./File:PrimAlgDemo.gif)A demo for Prim's algorithm based on Euclidean distance 

In [computer science](./Computer_science), **Prim's algorithm** is a [greedy algorithm](./Greedy_algorithm) that finds a [minimum spanning tree](./Minimum_spanning_tree) for a [weighted](./Weighted_graph) [undirected graph](./Undirected_graph). This means it finds a subset of the [edges](./Edge_(graph_theory)) that forms a [tree](./Tree_(graph_theory)) that includes every [vertex](./Vertex_(graph_theory)), where the total weight of all the [edges](./Graph_theory) in the tree is minimized. The algorithm operates by building this tree one vertex at a time, from an arbitrary starting vertex, at each step adding the cheapest possible connection from the tree to another vertex.

 

The algorithm was developed in 1930 by [Czech](./Czech_people) mathematician [Vojtěch Jarník](./Vojtěch_Jarník)[[1]](./Prim's_algorithm#cite_note-1) and later rediscovered and republished by [computer scientists](./Computer_scientist) [Robert C. Prim](./Robert_C._Prim) in 1957[[2]](./Prim's_algorithm#cite_note-2) and [Edsger W. Dijkstra](./Edsger_W._Dijkstra) in 1959.[[3]](./Prim's_algorithm#cite_note-3) Therefore, it is also sometimes called **Jarník's algorithm**,[[4]](./Prim's_algorithm#cite_note-4) the **Prim–Jarník algorithm**,[[5]](./Prim's_algorithm#cite_note-5) the **Prim–Dijkstra algorithm**[[6]](./Prim's_algorithm#cite_note-chertar-6)
or the **DJP algorithm**.[[7]](./Prim's_algorithm#cite_note-pr02-7)

 

Other well-known algorithms for this problem include [Kruskal's algorithm](./Kruskal's_algorithm) and [Borůvka's algorithm](./Borůvka's_algorithm).[[8]](./Prim's_algorithm#cite_note-8) These algorithms find the minimum spanning forest in a possibly disconnected graph; in contrast, the most basic form of Prim's algorithm only finds minimum spanning trees in connected graphs. However, running Prim's algorithm separately for each [connected component](./Connected_component_(graph_theory)) of the graph, it can also be used to find the minimum spanning forest.[[9]](./Prim's_algorithm#cite_note-9) In terms of their asymptotic [time complexity](./Time_complexity), these three algorithms are equally fast for [sparse graphs](./Sparse_graph), but slower than other more sophisticated algorithms.[[7]](./Prim's_algorithm#cite_note-pr02-7)[[6]](./Prim's_algorithm#cite_note-chertar-6)
However, for graphs that are sufficiently dense, Prim's algorithm can be made to run in [linear time](./Linear_time), meeting or improving the time bounds for other algorithms.[[10]](./Prim's_algorithm#cite_note-tarjan83p77-10)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Prim%27s_algorithm.svg/120px-Prim%27s_algorithm.svg.png)](./File:Prim's_algorithm.svg)Prim's algorithm starting at vertex A. In the third step, edges BD and AB both have weight 2, so BD is chosen arbitrarily. After that step, AB is no longer a candidate for addition to the tree because it links two nodes that are already in the tree. 

## Description

 

The algorithm may informally be described as performing the following steps:

 
1. Initialize a tree with a single vertex, chosen arbitrarily from the graph.
2. Grow the tree by one edge: Of the edges that connect the tree to vertices not yet in the tree, find the minimum-weight edge, and transfer it to the tree.
3. Repeat step 2 (until all vertices are in the tree).

 

In more detail, it may be implemented following the [pseudocode](./Pseudocode) below.

 
```
function Prim(vertices, edges) is
    for each vertex in vertices do
        cheapestCost[vertex] ← ∞
        cheapestEdge[vertex] ← null

    explored ← empty set
    unexplored ← set containing all vertices

    startVertex ← any element of vertices
    cheapestCost[startVertex] ← 0

    while unexplored is not empty do
        // Select vertex in unexplored with minimum cost
        currentVertex ← vertex in unexplored with minimum cheapestCost[vertex]
        unexplored.remove(currentVertex)
        explored.add(currentVertex)

        for each edge (currentVertex, neighbor) in edges do
            if neighbor in unexplored and weight(currentVertex, neighbor) < cheapestCost[neighbor] then
                cheapestCost[neighbor] ← weight(currentVertex, neighbor)
                cheapestEdge[neighbor] ← (currentVertex, neighbor)

    resultEdges ← empty list
    for each vertex in vertices do
        if cheapestEdge[vertex] ≠ null then
            resultEdges.append(cheapestEdge[vertex])

    return resultEdges
```
 

As described above, the starting vertex for the algorithm will be chosen arbitrarily, because the first iteration of the main loop of the algorithm will have a set of vertices in *Q* that all have equal weights, and the algorithm will automatically start a new tree in *F* when it completes a spanning tree of each connected component of the input graph. The algorithm may be modified to start with any particular vertex *s* by setting *C*[*s*] to be a number smaller than the other values of *C* (for instance, zero), and it may be modified to only find a single spanning tree rather than an entire spanning forest (matching more closely the informal description) by stopping whenever it encounters another vertex flagged as having no associated edge.

 

Different variations of the algorithm differ from each other in how the set *Q* is implemented: as a simple [linked list](./Linked_list) or [array](./Array_data_structure) of vertices, or as a more complicated [priority queue](./Priority_queue) data structure. This choice leads to differences in the [time complexity](./Time_complexity) of the algorithm. In general, a priority queue will be quicker at finding the vertex *v* with minimum cost, but will entail more expensive updates when the value of *C*[*w*] changes.

 

## Time complexity

 Prim's algorithm has many applications, such as in the [generation](./Maze_generation) of this maze, which applies Prim's algorithm to a randomly weighted [grid graph](./Grid_graph). 

The time complexity of Prim's algorithm depends on the data structures used for the graph and for ordering the edges by weight, which can be done using a [priority queue](./Priority_queue). The following table shows the typical choices:

 
| Minimum edge weight data structure | Time complexity (total) |
| --- | --- |
| adjacency matrix, searching | O(|V|2){\displaystyle O(|V|^{2})} |
| binary heapandadjacency list | O((|V|+|E|)log⁡|V|)=O(|E|log⁡|V|){\displaystyle O((|V|+|E|)\log |V|)=O(|E|\log |V|)} |
| Fibonacci heapandadjacency list | O(|E|+|V|log⁡|V|){\displaystyle O(|E|+|V|\log |V|)} |

 

A simple implementation of Prim's, using an [adjacency matrix](./Adjacency_matrix) or an [adjacency list](./Adjacency_list) graph representation and linearly searching an array of weights to find the minimum weight edge to add, requires [O](./Big-O_notation)(|V|2) running time. However, this running time can be greatly improved by using [heaps](./Heap_(data_structure)) to implement finding minimum weight edges in the algorithm's inner loop.

 

A first improved version uses a heap to store all edges of the input graph, ordered by their weight. This leads to an O(|E| log |E|) worst-case running time. But storing vertices instead of edges can improve it still further. The heap should order the vertices by the smallest edge-weight that connects them to any vertex in the partially constructed [minimum spanning tree](./Minimum_spanning_tree) (MST) (or infinity if no such edge exists). Every time a vertex *v* is chosen and added to the MST, a decrease-key operation is performed on all vertices *w* outside the partial MST such that *v* is connected to *w*, setting the key to the minimum of its previous value and the edge cost of (*v*,*w*).

 

Using a simple [binary heap](./Binary_heap) data structure, Prim's algorithm can now be shown to run in time [O](./Big-O_notation)(|E| log |V|) where |E| is the number of edges and |V| is the number of vertices. Using a more sophisticated [Fibonacci heap](./Fibonacci_heap), this can be brought down to [O](./Big-O_notation)(|E| + |V| log |V|), which is [asymptotically faster](./Asymptotic_computational_complexity) when the graph is [dense](./Dense_graph) enough that |E| is [ω](./Big-O_notation#Family_of_Bachmann.E2.80.93Landau_notations)(|V|), and [linear time](./Linear_time) when |E| is at least |V| log |V|. For graphs of even greater density (having at least |V|*c* edges for some *c* > 1), Prim's algorithm can be made to run in linear time even more simply, by using a [*d*-ary heap](./D-ary_heap) in place of a Fibonacci heap.[[10]](./Prim's_algorithm#cite_note-tarjan83p77-10)[[11]](./Prim's_algorithm#cite_note-11)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Prim%27s_algorithm_proof.svg/250px-Prim%27s_algorithm_proof.svg.png)](./File:Prim's_algorithm_proof.svg)Demonstration of proof. In this case, the graph *Y1* = *Y* − *f* + *e* is already equal to *Y*. In general, the process may need to be repeated. 

## Proof of correctness

 

Let *P* be a connected, weighted [graph](./Graph_theory).  At every iteration of Prim's algorithm, an edge must be found that connects a vertex in a subgraph to a vertex outside the subgraph.  Since  *P* is connected, there will always be a path to every vertex.  The output *Y* of Prim's algorithm is a [tree](./Tree_(graph_theory)), because the edge and vertex added to tree *Y* are connected. 

 

Let *Y1* be a minimum spanning tree of graph P. If *Y1*=*Y* then *Y* is a minimum spanning tree. Otherwise, let *e* be the first edge added during the construction of tree *Y* that is not in tree *Y1*, and *V* be the set of vertices connected by the edges added before edge *e*.  Then one endpoint of edge *e* is in set *V* and the other is not.  Since tree *Y1* is a spanning tree of graph *P*, there is a path in tree *Y1* joining the two endpoints.  As one travels along the path, one must encounter an edge *f* joining a vertex in set *V* to one that is not in set *V*.  Now, at the iteration when edge *e* was added to tree *Y*, edge *f* could also have been added and it would be added instead of edge *e* if its weight was less than *e*, and since edge *f* was not added, we conclude that

     w ( f ) ≥ ≥  w ( e ) .   {\displaystyle w(f)\geq w(e).}  ![{\displaystyle w(f)\geq w(e).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cedd55ba247aa96d262dc181d9233cbcdd2fdc56) 

Let tree *Y2* be the graph obtained by removing edge *f* from and adding edge *e* to tree *Y1*.  It is easy to show that tree *Y2* is connected, has the same number of edges as tree *Y1*, and the total weights of its edges is not larger than that of tree *Y1*, therefore it is also a minimum spanning tree of graph *P* and it contains edge *e* and all the edges added before it during the construction of set *V*.  Repeat the steps above and we will eventually obtain a minimum spanning tree of graph *P* that is identical to tree *Y*.  This shows *Y* is a minimum spanning tree. The minimum spanning tree allows for the first subset of the sub-region to be expanded into a larger subset *X*, which we assume to be the minimum.

 

## Parallel algorithm

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/27/Distributed_adjacency_matrix_for_parallel_prim.png/250px-Distributed_adjacency_matrix_for_parallel_prim.png)](./File:Distributed_adjacency_matrix_for_parallel_prim.png)The adjacency matrix distributed between multiple processors for parallel Prim's algorithm. In each iteration of the algorithm, every processor updates its part of *C* by inspecting the row of the newly inserted vertex in its set of columns in the adjacency matrix. The results are then collected and the next vertex to include in the MST is selected globally. 

The main loop of Prim's algorithm is inherently sequential and thus not [parallelizable](./Parallel_algorithm). However, the [inner loop](./Prim's_algorithm#step3c), which determines the next edge of minimum weight that does not form a cycle, can be parallelized by dividing the vertices and edges between the available processors.[[12]](./Prim's_algorithm#cite_note-grama2003-12) The following [pseudocode](./Pseudocode) demonstrates this.

 
1. Assign each processor      P  i     {\displaystyle P_{i}}  ![{\displaystyle P_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3ba1396129f7be3c7f828a571b6649e6807d10d3) a set      V  i     {\displaystyle V_{i}}  ![{\displaystyle V_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f300b83673e961a9d48f3862216b167f94e5668c) of consecutive vertices of length          |  V  |     |  P  |        {\displaystyle {\tfrac {|V|}{|P|}}}  ![{\displaystyle {\tfrac {|V|}{|P|}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7049f2c4d5fc53261b3b1b414127e917fdbe36fa).
2. Create C, E, F, and Q as in the [sequential algorithm](./Prim's_algorithm#sequential_algorithm) and divide C, E, as well as the graph between all processors such that each processor holds the incoming edges to its set of vertices. Let      C  i     {\displaystyle C_{i}}  ![{\displaystyle C_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc49dc02c0ec8c86b67e7d10518ac791eda0bf22),      E  i     {\displaystyle E_{i}}  ![{\displaystyle E_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ba9f6e3041b052cf13a0ede4ecf35fb4c9cd16c) denote the parts of *C*, *E* stored on processor      P  i     {\displaystyle P_{i}}  ![{\displaystyle P_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3ba1396129f7be3c7f828a571b6649e6807d10d3).
3. Repeat the following steps until *Q* is empty:

1. On every processor: find the vertex      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) having the minimum value in      C  i     {\displaystyle C_{i}}  ![{\displaystyle C_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc49dc02c0ec8c86b67e7d10518ac791eda0bf22)[     v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127)] (local solution).
2. [Min-reduce](./Reduction_Operator) the local solutions to find the vertex *v* having the minimum possible value of *C*[*v*] (global solution).
3. [Broadcast](./Broadcasting_(computing)) the selected node to every processor.
4. Add *v* to *F* and, if *E*[*v*] is not the special flag value, also add *E*[*v*] to *F*.
5. On every processor: update      C  i     {\displaystyle C_{i}}  ![{\displaystyle C_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc49dc02c0ec8c86b67e7d10518ac791eda0bf22) and      E  i     {\displaystyle E_{i}}  ![{\displaystyle E_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ba9f6e3041b052cf13a0ede4ecf35fb4c9cd16c) as in the sequential algorithm.

4. Return *F*

 

This algorithm can generally be implemented on distributed machines[[12]](./Prim's_algorithm#cite_note-grama2003-12) as well as on shared memory machines.[[13]](./Prim's_algorithm#cite_note-13) The running time is     O (      |  V   |   2      |  P  |      ) + O (  |  V  |  log ⁡ ⁡   |  P  |  )   {\displaystyle O({\tfrac {|V|^{2}}{|P|}})+O(|V|\log |P|)}  ![{\displaystyle O({\tfrac {|V|^{2}}{|P|}})+O(|V|\log |P|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18b01ce4136f7723979797e6b8ea4303e28de358), assuming that the *reduce* and *broadcast* operations can be performed in     O ( log ⁡ ⁡   |  P  |  )   {\displaystyle O(\log |P|)}  ![{\displaystyle O(\log |P|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/45a349d595f6b6189539caf1a888107c5d8022c1).[[12]](./Prim's_algorithm#cite_note-grama2003-12) A variant of Prim's algorithm for shared memory machines, in which Prim's sequential algorithm is being run in parallel, starting from different vertices, has also been explored.[[14]](./Prim's_algorithm#cite_note-14) It should, however, be noted that more sophisticated algorithms exist to solve the [distributed minimum spanning tree](./Distributed_minimum_spanning_tree) problem in a more efficient manner.

 

## See also

 
- [Dijkstra's algorithm](./Dijkstra's_algorithm), a very similar algorithm for the [shortest path problem](./Shortest_path_problem)
- [Greedoids](./Greedoid) offer a general way to understand the correctness of Prim's algorithm

 

## References

 
1. [↑](./Prim's_algorithm#cite_ref-1) [Jarník, V.](./Vojtěch_Jarník) (1930), "O jistém problému minimálním" [About a certain minimal problem], *Práce Moravské Přírodovědecké Společnosti* (in Czech), **6** (4): 57–63, [hdl](./Hdl_(identifier)):[10338.dmlcz/500726](https://hdl.handle.net/10338.dmlcz%2F500726).
2. [↑](./Prim's_algorithm#cite_ref-2) [Prim, R. C.](./Robert_C._Prim) (November 1957), ["Shortest connection networks And some generalizations"](https://archive.org/details/bstj36-6-1389), *[Bell System Technical Journal](./Bell_System_Technical_Journal)*, **36** (6): 1389–1401, [Bibcode](./Bibcode_(identifier)):[1957BSTJ...36.1389P](https://ui.adsabs.harvard.edu/abs/1957BSTJ...36.1389P), [doi](./Doi_(identifier)):[10.1002/j.1538-7305.1957.tb01515.x](https://doi.org/10.1002%2Fj.1538-7305.1957.tb01515.x).
3. [↑](./Prim's_algorithm#cite_ref-3) [Dijkstra, E. W.](./Edsger_W._Dijkstra) (December 1959), ["A note on two problems in connexion with graphs"](https://www-m3.ma.tum.de/twiki/pub/MN0506/WebHome/dijkstra.pdf) (PDF), *Numerische Mathematik*, **1** (1): 269–271, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.165.7577](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.165.7577), [doi](./Doi_(identifier)):[10.1007/BF01386390](https://doi.org/10.1007%2FBF01386390), [S2CID](./S2CID_(identifier)) [123284777](https://api.semanticscholar.org/CorpusID:123284777).
4. [↑](./Prim's_algorithm#cite_ref-4) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Wayne, Kevin Daniel (2011), [*Algorithms*](https://books.google.com/books?id=MTpsAQAAQBAJ&pg=PA628) (4th ed.), Addison-Wesley, p. 628, [ISBN](./ISBN_(identifier)) [978-0-321-57351-3](./Special:BookSources/978-0-321-57351-3).
5. [↑](./Prim's_algorithm#cite_ref-5) Rosen, Kenneth (2011), [*Discrete Mathematics and Its Applications*](https://books.google.com/books?id=6EJOCAAAQBAJ&pg=PA798) (7th ed.), McGraw-Hill Science, p. 798.
6. [1](./Prim's_algorithm#cite_ref-chertar_6-0) [2](./Prim's_algorithm#cite_ref-chertar_6-1) [Cheriton, David](./David_Cheriton); [Tarjan, Robert Endre](./Robert_Tarjan) (1976), "Finding minimum spanning trees", *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*, **5** (4): 724–742, [doi](./Doi_(identifier)):[10.1137/0205051](https://doi.org/10.1137%2F0205051), [MR](./MR_(identifier)) [0446458](https://mathscinet.ams.org/mathscinet-getitem?mr=0446458).
7. [1](./Prim's_algorithm#cite_ref-pr02_7-0) [2](./Prim's_algorithm#cite_ref-pr02_7-1) Pettie, Seth; [Ramachandran, Vijaya](./Vijaya_Ramachandran) (January 2002), ["An optimal minimum spanning tree algorithm"](http://www.cs.utexas.edu/~vlr/papers/optmsf-jacm.pdf) (PDF), *Journal of the ACM*, **49** (1): 16–34, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.110.7670](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.110.7670), [doi](./Doi_(identifier)):[10.1145/505241.505243](https://doi.org/10.1145%2F505241.505243), [MR](./MR_(identifier)) [2148431](https://mathscinet.ams.org/mathscinet-getitem?mr=2148431), [S2CID](./S2CID_(identifier)) [5362916](https://api.semanticscholar.org/CorpusID:5362916).
8. [↑](./Prim's_algorithm#cite_ref-8) [Tarjan, Robert Endre](./Robert_Tarjan) (1983), "Chapter 6. Minimum spanning trees. 6.2. Three classical algorithms", *Data Structures and Network Algorithms*, CBMS-NSF Regional Conference Series in Applied Mathematics, vol. 44, [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics), pp. 72–77.
9. [↑](./Prim's_algorithm#cite_ref-9) Kepner, Jeremy; Gilbert, John (2011), [*Graph Algorithms in the Language of Linear Algebra*](https://books.google.com/books?id=JBXDc83jRBwC&pg=PA55), Software, Environments, and Tools, vol. 22, [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics), p. 55, [ISBN](./ISBN_(identifier)) [9780898719901](./Special:BookSources/9780898719901).
10. [1](./Prim's_algorithm#cite_ref-tarjan83p77_10-0) [2](./Prim's_algorithm#cite_ref-tarjan83p77_10-1) [Tarjan (1983)](./Prim's_algorithm#CITEREFTarjan1983), p. 77.
11. [↑](./Prim's_algorithm#cite_ref-11) [Johnson, Donald B.](./Donald_B._Johnson) (December 1975), "Priority queues with update and finding minimum spanning trees", *Information Processing Letters*, **4** (3): 53–57, [doi](./Doi_(identifier)):[10.1016/0020-0190(75)90001-0](https://doi.org/10.1016%2F0020-0190%2875%2990001-0).
12. [1](./Prim's_algorithm#cite_ref-grama2003_12-0) [2](./Prim's_algorithm#cite_ref-grama2003_12-1) [3](./Prim's_algorithm#cite_ref-grama2003_12-2) Grama, Ananth; Gupta, Anshul; Karypis, George; Kumar, Vipin (2003), *Introduction to Parallel Computing*, Addison-Wesley, pp. 444–446, [ISBN](./ISBN_(identifier)) [978-0201648652](./Special:BookSources/978-0201648652)
13. [↑](./Prim's_algorithm#cite_ref-13) Quinn, Michael J.; Deo, Narsingh (1984), "Parallel graph algorithms", *ACM Computing Surveys*, **16** (3): 319–348, [doi](./Doi_(identifier)):[10.1145/2514.2515](https://doi.org/10.1145%2F2514.2515), [S2CID](./S2CID_(identifier)) [6833839](https://api.semanticscholar.org/CorpusID:6833839)
14. [↑](./Prim's_algorithm#cite_ref-14) Setia, Rohit (2009), ["A new parallel algorithm for minimum spanning tree problem"](https://ncit-cluster.grid.pub.ro/trac/PP2009/export/157/proiecte/pgraph/Documentation/parallelspannintree.pdf) (PDF), *Proc. International Conference on High Performance Computing (HiPC)*

 

## External links

 
- [Prim's Algorithm progress on randomly distributed points](https://meyavuz.wordpress.com/2017/03/10/prims-algorithm-animation-for-randomly-distributed-points)
- [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/20px-Commons-logo.svg.png)](./File:Commons-logo.svg) Media related to [Prim's algorithm](https://commons.wikimedia.org/wiki/Category:Prim's%20algorithm) at Wikimedia Commons

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |