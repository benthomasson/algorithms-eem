---
source: https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
fetched: 2026-06-19
---

Abstract data type in computer science [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Directed.svg/250px-Directed.svg.png)](./File:Directed.svg)A [directed graph](./Directed_graph) with three [vertices](./Vertex_(graph_theory)) (blue circles) and three [edges](./Edge_(graph_theory)) (black arrows). 

In [computer science](./Computer_science), a **graph** is an [abstract data type](./Abstract_data_type) that is meant to implement the [undirected graph](./Graph_(discrete_mathematics)) and [directed graph](./Directed_graph) concepts from the field of [graph theory](./Graph_theory) within [mathematics](./Mathematics).

 

A graph data structure consists of a finite (and possibly mutable) [set](./Set_(computer_science)) of *vertices* (also called *nodes* or *points*), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as *edges* (also called *links* or *lines*), and for a directed graph are also known as *edges* but also sometimes *arrows* or *arcs*. The vertices may be part of the graph structure, or may be external entities represented by integer indices or [references](./Reference_(computer_science)).

 

A graph data structure may also associate to each edge some *edge value*, such as a symbolic label or a numeric attribute (cost, capacity, length, etc.).

 

## Operations

 [![UML class diagram of a Graph (abstract data type)](//upload.wikimedia.org/wikipedia/commons/thumb/d/d7/UML_graph_ADT.svg/250px-UML_graph_ADT.svg.png)](./File:UML_graph_ADT.svg)UML class diagram of a Graph (abstract data type) 

The basic operations provided by a graph data structure *G* usually include:[[1]](./Graph_(abstract_data_type)#cite_note-gt-ops-1)

 
- adjacent(*G*, *x*, *y*): tests whether there is an edge from the vertex *x* to the vertex *y*;
- neighbors(*G*, *x*): lists all vertices *y* such that there is an edge from the vertex *x* to the vertex *y*;
- add_vertex(*G*, *x*): adds the vertex *x*, if it is not there;
- remove_vertex(*G*, *x*): removes the vertex *x*, if it is there;
- add_edge(*G*, *x*, *y*, *z*): adds the edge *z* from the vertex *x* to the vertex *y*, if it is not there;
- remove_edge(*G*, *x*, *y*): removes the edge from the vertex *x* to the vertex *y*, if it is there;
- get_vertex_value(*G*, *x*): returns the value associated with the vertex *x*;
- set_vertex_value(*G*, *x*, *v*): sets the value associated with the vertex *x* to *v*.

 

Structures that associate values to the edges usually also provide:[[1]](./Graph_(abstract_data_type)#cite_note-gt-ops-1)

 
- get_edge_value(*G*, *x*, *y*): returns the value associated with the edge (*x*, *y*);
- set_edge_value(*G*, *x*, *y*, *v*): sets the value associated with the edge (*x*, *y*) to *v*.

 

## Common data structures for graph representation

 [Adjacency list](./Adjacency_list)[[2]](./Graph_(abstract_data_type)#cite_note-2) Vertices are stored as records or objects, and every vertex stores a [list](./List_(computing)) of adjacent vertices. This data structure allows the storage of additional data on the vertices. Additional data can be stored if edges are also stored as objects, in which case each vertex stores its incident edges and each edge stores its incident vertices. [Adjacency matrix](./Adjacency_matrix)[[3]](./Graph_(abstract_data_type)#cite_note-3) A two-dimensional matrix, in which the rows represent source vertices and columns represent destination vertices. Data on edges and vertices must be stored externally. Only the cost for one edge can be stored between each pair of vertices. [Incidence matrix](./Incidence_matrix)[[4]](./Graph_(abstract_data_type)#cite_note-4) A two-dimensional matrix, in which the rows represent the vertices and columns represent the edges. The entries indicate the incidence relation between the vertex at a row and edge at a column. 

The following table gives the [time complexity](./Time_complexity) cost of performing various operations on graphs, for each of these representations, with |*V*| the number of vertices and |*E*| the number of edges.[*[citation needed](./Wikipedia:Citation_needed)*] In the matrix representations, the entries encode the cost of following an edge. The cost of edges that are not present are assumed to be ∞.

 
|  | Adjacency list | Adjacency matrix | Incidence matrix |
| --- | --- | --- | --- |
| Store graph | O(|V|+|E|){\displaystyle O(|V|+|E|)} | O(|V|2){\displaystyle O(|V|^{2})} | O(|V|⋅|E|){\displaystyle O(|V|\cdot |E|)} |
| Add vertex | O(1){\displaystyle O(1)} | O(|V|2){\displaystyle O(|V|^{2})} | O(|V|⋅|E|){\displaystyle O(|V|\cdot |E|)} |
| Add edge | O(1){\displaystyle O(1)} | O(1){\displaystyle O(1)} | O(|V|⋅|E|){\displaystyle O(|V|\cdot |E|)} |
| Remove vertex | O(|E|){\displaystyle O(|E|)} | O(|V|2){\displaystyle O(|V|^{2})} | O(|V|⋅|E|){\displaystyle O(|V|\cdot |E|)} |
| Remove edge | O(|V|){\displaystyle O(|V|)} | O(1){\displaystyle O(1)} | O(|V|⋅|E|){\displaystyle O(|V|\cdot |E|)} |
| Are verticesxandyadjacent (assuming that their storage positions are known)? | O(|V|){\displaystyle O(|V|)} | O(1){\displaystyle O(1)} | O(|E|){\displaystyle O(|E|)} |
| Remarks | Slow to remove vertices and edges, because it needs to find all vertices or edges | Slow to add or remove vertices, because matrix must be resized/copied | Slow to add or remove vertices and edges, because matrix must be resized/copied |

 

Adjacency lists are generally preferred for the representation of [sparse graphs](./Sparse_graph), while an adjacency matrix is preferred if the graph is dense; that is, the number of edges      |  E  |    {\displaystyle |E|}  ![{\displaystyle |E|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8c2b9637808cf805d411190b4ae017dbd4ef8d8) is close to the number of vertices squared,      |  V   |   2     {\displaystyle |V|^{2}}  ![{\displaystyle |V|^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3e2a7aad37527c097101c39b0b7724fe4e1cafb1), or if one must be able to quickly look up if there is an edge connecting two vertices.[[5]](./Graph_(abstract_data_type)#cite_note-clrs-5)[[6]](./Graph_(abstract_data_type)#cite_note-gt-6)

 

### More efficient representation of adjacency sets

 

The time complexity of operations in the adjacency list representation can be improved by storing the sets of adjacent vertices in more efficient data structures, such as [hash tables](./Hash_table) or [balanced binary search trees](./Binary_search_tree#Balanced_binary_search_trees) (the latter representation requires that vertices are identified by elements of a linearly ordered set, such as integers or character strings). A representation of adjacent vertices via hash tables leads to an [amortized](./Amortized_analysis) average time complexity of     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) to test adjacency of two given vertices and to remove an edge and an [amortized](./Amortized_analysis) average time complexity[[7]](./Graph_(abstract_data_type)#cite_note-Cormen_et_al_p253-280_(hashtable)-7) of     O ( deg ⁡ ⁡  ( x ) )   {\displaystyle O(\deg(x))}  ![{\displaystyle O(\deg(x))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68696b084459852b1345e760abcc5caea7533da7) to remove a given vertex x of degree     deg ⁡ ⁡  ( x )   {\displaystyle \deg(x)}  ![{\displaystyle \deg(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/24fe4626e8be1ee6fa50f8e790ecee7f81cfb090). The time complexity of the other operations and the asymptotic space requirement do not change.

 

## Parallel representations

 

The parallelization of graph problems faces significant challenges: Data-driven computations, unstructured problems, poor locality and high data access to computation ratio.[[8]](./Graph_(abstract_data_type)#cite_note-Bader2013-8)[[9]](./Graph_(abstract_data_type)#cite_note-9) The graph representation used for parallel architectures plays a significant role in facing those challenges. Poorly chosen representations may unnecessarily drive up the communication cost of the algorithm, which will decrease its [scalability](./Scalability). In the following, shared and distributed memory architectures are considered.

 

### Shared memory

 

In the case of a [shared memory](./Shared_memory) model, the graph representations used for parallel processing are the same as in the sequential case,[[10]](./Graph_(abstract_data_type)#cite_note-Sanders2019-10) since parallel read-only access to the graph representation (e.g. an [adjacency list](./Adjacency_list)) is efficient in shared memory.

 

### Distributed memory

 

In the [distributed memory](./Distributed_memory) model, the usual approach is to [partition](./Graph_partition) the vertex set     V   {\displaystyle V}  ![{\displaystyle V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0f6064540e84211d0ffe4dac72098adfa52845) of the graph into     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) sets      V  0   , … …  ,  V  p − −  1     {\displaystyle V_{0},\dots ,V_{p-1}}  ![{\displaystyle V_{0},\dots ,V_{p-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3ec712b424f36d440d8b39fce54f4cbb2480af77). Here,     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) is the amount of available processing elements (PE). The vertex set partitions are then distributed to the PEs with matching index, additionally to the corresponding edges. Every PE has its own [subgraph](./Subgraph_(graph_theory)) representation, where edges with an endpoint in another partition require special attention. For standard communication interfaces like [MPI](./Message_Passing_Interface), the ID of the PE owning the other endpoint has to be identifiable. During computation in a distributed graph algorithms, passing information along these edges implies communication.[[10]](./Graph_(abstract_data_type)#cite_note-Sanders2019-10)

 

[Partitioning the graph](./Graph_partition) needs to be done carefully - there is a trade-off between low communication and even size partitioning[[11]](./Graph_(abstract_data_type)#cite_note-11) But partitioning a graph is a NP-hard problem, so it is not feasible to calculate them. Instead, the following heuristics are used.

 

1D partitioning: Every processor gets     n  /  p   {\displaystyle n/p}  ![{\displaystyle n/p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b40bd0a1d3c9771117157039602170561e5902f) vertices and the corresponding outgoing edges. This can be understood as a row-wise or column-wise decomposition of the adjacency matrix. For algorithms operating on this representation, this requires an All-to-All communication step as well as       O   ( m )   {\displaystyle {\mathcal {O}}(m)}  ![{\displaystyle {\mathcal {O}}(m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/089694843af30c69c8b1d6287c3d8f0e2868499c) message buffer sizes, as each PE potentially has outgoing edges to every other PE.[[12]](./Graph_(abstract_data_type)#cite_note-Buluc2011-12)

 

2D partitioning: Every processor gets a submatrix of the adjacency matrix. Assume the processors are aligned in a rectangle     p =  p  r   × ×   p  c     {\displaystyle p=p_{r}\times p_{c}}  ![{\displaystyle p=p_{r}\times p_{c}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33481094a10f6ec7bd472b95b2eb02ad92e8d193), where      p  r     {\displaystyle p_{r}}  ![{\displaystyle p_{r}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4149f4cd1c5d1087bd8409c84cb0b40f166259a1) and      p  c     {\displaystyle p_{c}}  ![{\displaystyle p_{c}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/836639c3805ca867b1ff24dc6db7a6b24fc69158) are the amount of processing elements in each row and column, respectively. Then each processor gets a [submatrix](./Submatrix) of the adjacency matrix of dimension     ( n  /   p  r   ) × ×  ( n  /   p  c   )   {\displaystyle (n/p_{r})\times (n/p_{c})}  ![{\displaystyle (n/p_{r})\times (n/p_{c})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f1dab29ea131d1dc2beceeeb841b0cbf9f0ad150). This can be visualized as a [checkerboard](./Checkerboard) pattern in a matrix.[[12]](./Graph_(abstract_data_type)#cite_note-Buluc2011-12) Therefore, each processing unit can only have outgoing edges to PEs in the same row and column. This bounds the amount of communication partners for each PE to      p  r   +  p  c   − −  1   {\displaystyle p_{r}+p_{c}-1}  ![{\displaystyle p_{r}+p_{c}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/952452e1b7084c93e48a8769cfb95eb17870a450) out of     p =  p  r   × ×   p  c     {\displaystyle p=p_{r}\times p_{c}}  ![{\displaystyle p=p_{r}\times p_{c}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33481094a10f6ec7bd472b95b2eb02ad92e8d193) possible ones.

 

## Compressed representations

 

Graphs with trillions of edges occur in [machine learning](./Machine_learning), [social network analysis](./Social_network_analysis), and other areas. [Compressed](./Data_compression) graph representations have been developed to reduce I/O and memory requirements. General techniques such as [Huffman coding](./Huffman_coding) are applicable, but the adjacency list or adjacency matrix can be processed in specific ways to increase efficiency.[[13]](./Graph_(abstract_data_type)#cite_note-13)

 

## Applications of Graphs

 

### Breadth first search and depth first search

 

[Breadth-first search](./Breadth-first_search) (BFS) and [depth-first search](./Depth-first_search) (DFS) are two closely related approaches that are used for exploring all of the nodes in a given [connected component](./Connected_component_(graph_theory)). Both start with an arbitrary node, the "[root](./Root_(graph_theory))".[[14]](./Graph_(abstract_data_type)#cite_note-Purti-14) [Strongly connected components](./Strongly_connected_component) can also be found using graph traversals using algorithms such as [Kosaraju's algorithm](./Kosaraju's_algorithm), which is a modified DFS.

 

### Pathfinding

 

[Dijkstra's Algorithm](./Dijkstra's_algorithm) is a [Pathfinding Algorithm](./Pathfinding) that can be used on a positively-weighted (meaning all edge weights must be greater than or equal to 0) and/or directed graphs. This can be used to find the shortest path between two arbitrarily chosen nodes which is commonly applied in  routing problems.

 

## See also

 
- [Graph traversal](./Graph_traversal) for more information on graph walking strategies
- [Graph database](./Graph_database) for graph (data structure) persistency
- [Graph rewriting](./Graph_rewriting) for rule based transformations of graphs (graph data structures)
- [Graph drawing software](./Graph_drawing_software) for software, systems, and providers of systems for drawing graphs
- [Graph neural network](./Graph_neural_network) for machine learning on graphs with deep neural networks.

 

## References

  
1. [1](./Graph_(abstract_data_type)#cite_ref-gt-ops_1-0) [2](./Graph_(abstract_data_type)#cite_ref-gt-ops_1-1) See, e.g. [Goodrich & Tamassia (2015)](./Graph_(abstract_data_type)#CITEREFGoodrichTamassia2015), Section 13.1.2: Operations on graphs, p. 360. For a more detailed set of operations, see [Mehlhorn, K.](./Kurt_Mehlhorn); Näher, S. (1999). "Chapter 6: Graphs and their data structures". [*LEDA: A platform for combinatorial and geometric computing*](https://people.mpi-inf.mpg.de/~mehlhorn/ftp/LEDAbook/Graphs.pdf) (PDF). Cambridge University Press. pp. 240–282.
2. [↑](./Graph_(abstract_data_type)#cite_ref-2) [Cormen et al. (2001)](./Graph_(abstract_data_type)#CITEREFCormenLeisersonRivestStein2001), pp. 528–529; [Goodrich & Tamassia (2015)](./Graph_(abstract_data_type)#CITEREFGoodrichTamassia2015), pp. 361-362.
3. [↑](./Graph_(abstract_data_type)#cite_ref-3) [Cormen et al. (2001)](./Graph_(abstract_data_type)#CITEREFCormenLeisersonRivestStein2001), pp. 529–530; [Goodrich & Tamassia (2015)](./Graph_(abstract_data_type)#CITEREFGoodrichTamassia2015), p. 363.
4. [↑](./Graph_(abstract_data_type)#cite_ref-4) [Cormen et al. (2001)](./Graph_(abstract_data_type)#CITEREFCormenLeisersonRivestStein2001), Exercise 22.1-7, p. 531.
5. [↑](./Graph_(abstract_data_type)#cite_ref-clrs_5-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). "Section 22.1: Representations of graphs". *[Introduction to Algorithms](./Introduction_to_Algorithms)* (Second ed.). MIT Press and McGraw-Hill. pp. 527–531. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
6. [↑](./Graph_(abstract_data_type)#cite_ref-gt_6-0) [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2015). "Section 13.1: Graph terminology and representations". *Algorithm Design and Applications*. Wiley. pp. 355–364. [ISBN](./ISBN_(identifier)) [978-1-118-33591-8](./Special:BookSources/978-1-118-33591-8).
7. [↑](./Graph_(abstract_data_type)#cite_ref-Cormen_et_al_p253-280_(hashtable)_7-0)  [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2009). [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.). Massachusetts Institute of Technology. pp. 253–280. [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8). 
8. [↑](./Graph_(abstract_data_type)#cite_ref-Bader2013_8-0) Bader, David; Meyerhenke, Henning; Sanders, Peter; Wagner, Dorothea (January 2013). [*Graph Partitioning and Graph Clustering*](https://www.ams.org/conm/588/). Contemporary Mathematics. Vol. 588. American Mathematical Society. [doi](./Doi_(identifier)):[10.1090/conm/588/11709](https://doi.org/10.1090%2Fconm%2F588%2F11709). [ISBN](./ISBN_(identifier)) [978-0-8218-9038-7](./Special:BookSources/978-0-8218-9038-7).
9. [↑](./Graph_(abstract_data_type)#cite_ref-9) Lumsdaine, Andrew; Gregor, Douglas; Hendrickson, Bruce; Berry, Jonathan (March 2007). "Challenges in Parallel Graph Processing". *Parallel Processing Letters*. **17** (1): 5–20. [doi](./Doi_(identifier)):[10.1142/s0129626407002843](https://doi.org/10.1142%2Fs0129626407002843). [ISSN](./ISSN_(identifier)) [0129-6264](https://search.worldcat.org/issn/0129-6264).
10. [1](./Graph_(abstract_data_type)#cite_ref-Sanders2019_10-0) [2](./Graph_(abstract_data_type)#cite_ref-Sanders2019_10-1) Sanders, Peter; Mehlhorn, Kurt; Dietzfelbinger, Martin; Dementiev, Roman (2019). [*Sequential and Parallel Algorithms and Data Structures: The Basic Toolbox*](https://www.springer.com/gp/book/9783030252083). Springer International Publishing. [ISBN](./ISBN_(identifier)) [978-3-030-25208-3](./Special:BookSources/978-3-030-25208-3).
11. [↑](./Graph_(abstract_data_type)#cite_ref-11) ["Parallel Processing of Graphs"](https://web.archive.org/web/20210825121127/https://www.graphengine.io/downloads/papers/ParallelProcessingOfGraphs.pdf) (PDF). Archived from [the original](https://www.graphengine.io/downloads/papers/ParallelProcessingOfGraphs.pdf) (PDF) on 2021-08-25. Retrieved 2020-03-09.
12. [1](./Graph_(abstract_data_type)#cite_ref-Buluc2011_12-0) [2](./Graph_(abstract_data_type)#cite_ref-Buluc2011_12-1) Buluç, A.; Madduri, Kamesh (2011). "Applications". *Parallel breadth-first search on distributed memory systems*. 2011 International Conference for High Performance Computing, Networking, Storage and Analysis. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.767.5248](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.767.5248). [doi](./Doi_(identifier)):[10.1145/2063384.2063471](https://doi.org/10.1145%2F2063384.2063471). [ISBN](./ISBN_(identifier)) [978-1-4503-0771-0](./Special:BookSources/978-1-4503-0771-0). [S2CID](./S2CID_(identifier)) [6540738](https://api.semanticscholar.org/CorpusID:6540738).
13. [↑](./Graph_(abstract_data_type)#cite_ref-13) Besta, Maciej; Hoefler, Torsten (27 April 2019). "Survey and Taxonomy of Lossless Graph Compression and Space-Efficient Graph Representations". [arXiv](./ArXiv_(identifier)):[1806.01799](https://arxiv.org/abs/1806.01799) [[cs.DS](https://arxiv.org/archive/cs.DS)].
14. [↑](./Graph_(abstract_data_type)#cite_ref-Purti_14-0) Purti (July–September 2018). ["Graph Traversals and its Applications"](http://ijrar.com/upload_issue/ijrar_issue_1836.pdf) (PDF). *International Journal of Research and Analytical Reviews*. **5** (3): 2.

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Graph (abstract data type)](https://commons.wikimedia.org/wiki/Category:Graph%20(abstract%20data%20type)).  
- [Boost Graph Library: a powerful C++ graph library](http://www.boost.org/libs/graph) s.a. [Boost (C++ libraries)](./Boost_(C++_libraries))
- [Networkx: a Python graph library](https://networkx.org/)
- [GraphMatcher](http://www.graphmatcher.com) a java program to align directed/undirected graphs.
- [GraphBLAS](http://graphblas.org) A specification for a library interface for operations on graphs, with a particular focus on sparse graphs.

 
| vteGraph representations |
| --- |
| Data structures | Graph (abstract data type)Adjacency listEdge listAdjacency matrixIncidence matrix |
| XML-based formats | DGMLDotMLGEXFGraphMLGXLXGMML |
| Text-based formats | DOTGraph Modelling Language(GML)LCF notationfor cubic Hamiltonian graphsNewick formatfor treesTrivial Graph Format |
| Related concepts | Graph databaseGraph drawingLinked data |

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |