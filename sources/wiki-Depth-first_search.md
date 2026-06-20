---
source: https://en.wikipedia.org/wiki/Depth-first_search
fetched: 2026-06-19
---

Algorithm to search the nodes of a graph 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Depth-first search"–news·newspapers·books·scholar·JSTOR(July 2010)(Learn how and when to remove this message) |
| --- | --- |

 
| A tree labeled by the order in which DFS expands its nodes |
| --- |
| Class | Search algorithm |
| Data structure | Graph |
| Worst-caseperformance | O(|V|+|E|){\displaystyle O(|V|+|E|)}for explicit graphs traversed without repetition,O(bd){\displaystyle O(b^{d})}for implicit graphs with branching factorbsearched to depthd |
| Worst-casespace complexity | O(|V|){\displaystyle O(|V|)}if entire graph is traversed without repetition, O(longest path length searched) =O(bd){\displaystyle O(bd)}for implicit graphs without elimination of duplicate nodes |
| Optimal | no (does not generally find shortest paths) |

 

**Depth-first search** (**DFS**) is an [algorithm](./Algorithm) for traversing or searching [tree](./Tree_data_structure) or [graph](./Graph_(data_structure)) data structures. The algorithm starts at the [root node](./Tree_(data_structure)#Terminology) (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking. Extra memory, usually a [stack](./Stack_(abstract_data_type)), is needed to keep track of the nodes discovered so far along a specified branch which helps in backtracking of the graph.

 

A version of depth-first search was investigated in the 19th century by French mathematician [Charles Pierre Trémaux](./Charles_Pierre_Trémaux)[[1]](./Depth-first_search#cite_note-1) as a strategy for [solving mazes](./Maze_solving_algorithm).[[2]](./Depth-first_search#cite_note-2)[[3]](./Depth-first_search#cite_note-3)

 

## Properties

 

The [time](./Time_complexity) and [space](./Memory_management) analysis of DFS differs according to its application area. In theoretical computer science, DFS is typically used to traverse an entire graph, and takes time     O (  |  V  |  +  |  E  |  )   {\displaystyle O(|V|+|E|)}  ![{\displaystyle O(|V|+|E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7cf317fbe3965ae3164f28c1f6858696adb23f4),[[4]](./Depth-first_search#cite_note-4) where      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) is the number of [vertices](./Vertex_(graph_theory))  and      |  E  |    {\displaystyle |E|}  ![{\displaystyle |E|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8c2b9637808cf805d411190b4ae017dbd4ef8d8) the number of  [edges](./Edge_(graph_theory)). This is linear in the size of the graph. In these applications it also uses space     O (  |  V  |  )   {\displaystyle O(|V|)}  ![{\displaystyle O(|V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3486d00c2ed0f7eb1db550af8f239ad68241a6c5) in the worst case to store the [stack](./Stack_(abstract_data_type)) of vertices on the current search path as well as the set of already-visited vertices. Thus, in this setting, the time and space bounds are the same as for [breadth-first search](./Breadth-first_search) and the choice of which of these two algorithms to use depends less on their complexity and more on the different properties of the vertex orderings the two algorithms produce.

 

For applications of DFS in relation to specific domains, such as searching for solutions in [artificial intelligence](./Artificial_intelligence) or web-crawling, the graph to be traversed is often either too large to visit in its entirety or infinite (DFS may suffer from [non-termination](./Halting_problem)). In such cases, search is only performed to a [limited depth](./Depth-limited_search); due to limited resources, such as memory or disk space, one typically does not use data structures to keep track of the set of all previously visited vertices. When search is performed to a limited depth, the time is still linear in terms of the number of expanded vertices and edges (although this number is not the same as the size of the entire graph because some vertices may be searched more than once and others not at all) but the space complexity of this variant of DFS is only proportional to the depth limit, and as a result, is much smaller than the space needed for searching to the same depth using breadth-first search. For such applications, DFS also lends itself much better to [heuristic](./Heuristics) methods for choosing a likely-looking branch. When an appropriate depth limit is not known a priori, [iterative deepening depth-first search](./Iterative_deepening_depth-first_search) applies DFS repeatedly with a sequence of increasing limits. In the artificial intelligence mode of analysis, with a [branching factor](./Branching_factor) greater than one, iterative deepening increases the running time by only a constant factor over the case in which the correct depth limit is known due to the geometric growth of the number of nodes per level.

 

DFS may also be used to collect a [sample](./Sample_(statistics)) of graph nodes. However, incomplete DFS, similarly to incomplete [BFS](./Breadth-first_search#Bias_towards_nodes_of_high_degree), is [biased](./Bias) towards nodes of high [degree](./Degree_(graph_theory)).

 

## Example

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/7f/Depth-First-Search.gif/250px-Depth-First-Search.gif)](./File:Depth-First-Search.gif)Animated example of a depth-first search 

For the following graph:

 

[![An undirected graph with edges AB, BD, BF, FE, AC, CG, AE](//upload.wikimedia.org/wikipedia/commons/thumb/6/61/Graph.traversal.example.svg/250px-Graph.traversal.example.svg.png)](./File:Graph.traversal.example.svg)

 

A depth-first search starting at the node A, assuming that the left edges in the shown graph are chosen before right edges, and assuming the search remembers previously visited nodes and will not repeat them (since this is a small graph), will visit the nodes in the following order: A, B, D, F, E, C, G.  The edges traversed in this search form a [Trémaux tree](./Trémaux_tree), a structure with important applications in [graph theory](./Graph_theory).
Performing the same search without remembering previously visited nodes results in visiting the nodes in the order A, B, D, F, E, A, B, D, F, E, etc. forever, caught in the A, B, D, F, E cycle and never reaching C or G.

 

[Iterative deepening](./Iterative_deepening_depth-first_search) is one technique to avoid this infinite loop and would reach all nodes.

 

## Output of a depth-first search

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/57/Tree_edges.svg/330px-Tree_edges.svg.png)](./File:Tree_edges.svg)The four types of edges defined by a spanning tree 

The result of a depth-first search of a graph can be conveniently described in terms of a [spanning tree](./Spanning_tree_(mathematics)) of the vertices reached during the search. Based on this spanning tree, the edges of the original graph can be divided into three classes: **forward edges**, which point from a node of the tree to one of its descendants, **back edges**, which point from a node to one of its ancestors, and **cross edges**, which do neither. Sometimes **tree edges**, edges which belong to the spanning tree itself, are classified separately from forward edges. If the original graph is undirected then all of its edges are tree edges or back edges.

 

### Vertex orderings

 

It is also possible to use depth-first search to linearly order the vertices of a graph or tree. There are four possible ways of doing this:

 
- A **preordering** is a list of the vertices in the order that they were first visited by the depth-first search algorithm. This is a compact and natural way of describing the progress of the search, as was done earlier in this article. A preordering of an [expression tree](./Parse_tree) is the expression in [Polish notation](./Polish_notation).
- A **postordering** is a list of the vertices in the order that they were *last* visited by the algorithm. A postordering of an expression tree is the expression in [reverse Polish notation](./Reverse_Polish_notation).
- A **reverse preordering** is the reverse of a preordering, i.e. a list of the vertices in the opposite order of their first visit. Reverse preordering is not the same as postordering.
- A **reverse postordering** is the reverse of a postordering, i.e. a list of the vertices in the opposite order of their last visit. Reverse postordering is not the same as preordering.

 

For [binary trees](./Binary_trees) there is additionally **in-ordering** and **reverse in-ordering**.

 

For example, when searching the directed graph below beginning at node A, the sequence of traversals is either A B D B A C A or A C D C A B A (choosing to first visit B or C from A is up to the algorithm). Note that repeat visits in the form of backtracking to a node, to check if it has still unvisited neighbors, are included here (even if it is found to have none). Thus the possible preorderings are A B D C and A C D B, while the possible postorderings are D B C A and D C B A, and the possible reverse postorderings are A C B D and A B C D.

 [![A directed graph with edges AB, BD, AC, CD](//upload.wikimedia.org/wikipedia/commons/thumb/6/68/If-then-else-control-flow-graph.svg/250px-If-then-else-control-flow-graph.svg.png)](./File:If-then-else-control-flow-graph.svg) 

Reverse postordering produces a [topological sorting](./Topological_sorting) of any [directed acyclic graph](./Directed_acyclic_graph). This ordering is also useful in [control-flow analysis](./Control-flow_graph) as it often represents a natural linearization of the control flows. The graph above might represent the flow of control in the code fragment below, and it is natural to consider this code in the order A B C D or A C B D but not natural to use the order A B D C or A C D B.

 
```
if (A) then {
    B
} else {
    C
}
D
```
 

## Pseudocode

  
|  |  |  |  |  |  | A |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |
|  |  | B |  |  |  |  |  | C |
|  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
| D |  | E |  | F |
|  |

 

0

 1 Previous node Restart Start Interactive depth-first search demonstration 

A recursive implementation of DFS:[[5]](./Depth-first_search#cite_note-5)

 
```
procedure DFS(G, v) is
    label v as discovered
    for all directed edges from v to w that are in G.adjacentEdges(v) do
        if vertex w is not labeled as discovered then
            recursively call DFS(G, w)
```
 

A non-recursive implementation of DFS with worst-case space complexity     O (  |  E  |  )   {\displaystyle O(|E|)}  ![{\displaystyle O(|E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/976fe7f1e011d0dcdb3d6163754c877aaad5187f), with the possibility of duplicate vertices on the stack:[[6]](./Depth-first_search#cite_note-6)

 
```
procedure DFS_iterative(G, v) is
    let S be a stack
    S.push(v)
    while S is not empty do
        v = S.pop()
        if v is not labeled as discovered then
            label v as discovered
            for all edges from v to w in G.adjacentEdges(v) do 
                S.push(w)
```
 [![An undirected graph with edges AB, BD, BF, FE, AC, CG, AE](//upload.wikimedia.org/wikipedia/commons/thumb/6/61/Graph.traversal.example.svg/250px-Graph.traversal.example.svg.png)](./File:Graph.traversal.example.svg)The example graph, copied from above 

These two variations of DFS visit the neighbors of each vertex in the opposite order from each other: the first neighbor of *v* visited by the recursive variation is  the first one in the list of adjacent edges, while in the iterative variation the first visited neighbor is the last one in the list of adjacent edges. The recursive implementation will visit the nodes from the example graph in the following order: A, B, D, F, E, C, G. The non-recursive implementation will visit the nodes as: A, E, F, B, D, C, G.

 

The non-recursive implementation is similar to [breadth-first search](./Breadth-first_search) but differs from it in two ways: 

 
1. it uses a stack instead of a queue, and
2. it delays checking whether a vertex has been discovered until the vertex is popped from the stack rather than making this check before adding the vertex.

 

If G is a [tree](./Tree_(data_structure)), replacing the queue of the breadth-first search algorithm with a stack will yield a depth-first search algorithm. For general graphs, replacing the stack of the iterative depth-first search implementation with a queue would also produce a breadth-first search algorithm, although a somewhat nonstandard one.[[7]](./Depth-first_search#cite_note-7)

 

Another possible implementation of iterative depth-first search uses a stack of [iterators](./Iterator) of the list of neighbors of a node, instead of a stack of nodes. This yields the same traversal as recursive DFS.[[8]](./Depth-first_search#cite_note-8)

 
```
procedure DFS_iterative(G, v) is
    let S be a stack
    label v as discovered
    S.push(iterator of G.adjacentEdges(v))
    while S is not empty do
        if S.peek().hasNext() then
            w = S.peek().next()
            if w is not labeled as discovered then
                label w as discovered
                S.push(iterator of G.adjacentEdges(w))
        else
            S.pop()
```
 

## Applications

 Randomized algorithm similar to depth-first search used in generating a maze. 

Algorithms that use depth-first search as a building block include:

 
- Finding [connected components](./Connected_component_(graph_theory)).
- [Topological sorting](./Topological_sorting).
- Finding 2-(edge or vertex)-connected components.
- Finding 3-(edge or vertex)-connected components.
- Finding the [bridges](./Bridge_(graph_theory)#Bridge-finding_algorithm) of a graph.
- Generating words in order to plot the [limit set](./Limit_set) of a [group](./Group_(mathematics)).
- Finding [strongly connected components](./Strongly_connected_components).
- Determining whether a species is closer to one species or another in a phylogenetic tree.
- [Planarity testing](./Planarity_testing).[[9]](./Depth-first_search#cite_note-9)[[10]](./Depth-first_search#cite_note-10)
- Solving puzzles with only one solution, such as [mazes](./Maze). (DFS can be adapted to find all solutions to a maze by only including nodes on the current path in the visited set.)
- [Maze generation](./Maze_generation) may use a randomized DFS.
- Finding [biconnectivity in graphs](./Biconnected_graph).
- [Succession](./Primogeniture#Absolute_primogeniture) to the throne shared by the [Commonwealth realms](./Commonwealth_realms).[[11]](./Depth-first_search#cite_note-11)

 

## Complexity

 

The [computational complexity](./Analysis_of_algorithms) of DFS was investigated by [John Reif](./John_Reif). More precisely, given a graph     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b), let     O = (  v  1   , … …  ,  v  n   )   {\displaystyle O=(v_{1},\dots ,v_{n})}  ![{\displaystyle O=(v_{1},\dots ,v_{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/90a47bca827f9a7b1d72f77316d986207d0096ed) be the ordering computed by the standard recursive DFS algorithm. This ordering is called the lexicographic depth-first search ordering. John Reif considered the complexity of computing the lexicographic depth-first search ordering, given a graph and a source. A [decision version](./Decision_problem) of the problem (testing whether some vertex u occurs before some vertex v in this order) is [**P**-complete](./P-complete),[[12]](./Depth-first_search#cite_note-12) meaning that it is "a nightmare for [parallel processing](./Parallel_algorithm)".[[13]](./Depth-first_search#cite_note-mehlhorn-13): 189 

 

A depth-first search ordering (not necessarily the lexicographic one), can be computed by a randomized parallel algorithm in the complexity class [RNC](./NC_(complexity)).[[14]](./Depth-first_search#cite_note-14) As of 1997, it remained unknown whether a depth-first traversal could be constructed by a deterministic parallel algorithm, in the complexity class [NC](./NC_(complexity)).[[15]](./Depth-first_search#cite_note-15)

 

## See also

 
- [Breadth-first search](./Breadth-first_search) – Algorithm to search the nodes of a graph
- [Iterative deepening depth-first search](./Iterative_deepening_depth-first_search) – Tree searching strategy
- [Search game](./Search_game) – Two-person zero-sum game
- [Tree traversal](./Tree_traversal) – For details about pre-order, in-order and post-order depth-first traversal

 

## Notes

  
1. [↑](./Depth-first_search#cite_ref-1) [Charles Pierre Trémaux](./Charles_Pierre_Trémaux) (1859–1882) École polytechnique of Paris (X:1876), French engineer of the telegraph 
 in Public conference, December 2, 2010 – by professor [Jean Pelletier-Thibert](./Jean_Pelletier-Thibert?action=edit&redlink=1) in Académie de Macon (Burgundy – France) – (Abstract published in the Annals academic, March 2011 – [ISSN](./ISSN_(identifier)) [0980-6032](https://search.worldcat.org/issn/0980-6032))
2. [↑](./Depth-first_search#cite_ref-2) [Even, Shimon](./Shimon_Even) (2011), [*Graph Algorithms*](https://books.google.com/books?id=m3QTSMYm5rkC&pg=PA46) (2nd ed.), Cambridge University Press, pp. 46–48, [ISBN](./ISBN_(identifier)) [978-0-521-73653-4](./Special:BookSources/978-0-521-73653-4).
3. [↑](./Depth-first_search#cite_ref-3) Sedgewick, Robert (2002), *Algorithms in C++: Graph Algorithms* (3rd ed.), Pearson Education, [ISBN](./ISBN_(identifier)) [978-0-201-36118-6](./Special:BookSources/978-0-201-36118-6).
4. [↑](./Depth-first_search#cite_ref-4)  Cormen, Thomas H., Charles E. Leiserson, and Ronald L. Rivest. p.606
5. [↑](./Depth-first_search#cite_ref-5) Goodrich and Tamassia; Cormen, Leiserson, Rivest, and Stein
6. [↑](./Depth-first_search#cite_ref-6) Page 93, Algorithm Design, Kleinberg and Tardos
7. [↑](./Depth-first_search#cite_ref-7) ["Stack-based graph traversal ≠ depth first search"](https://11011110.github.io/blog/2013/12/17/stack-based-graph-traversal.html). *11011110.github.io*. Retrieved 2020-06-10.
8. [↑](./Depth-first_search#cite_ref-8) Sedgewick, Robert (2010). [*Algorithms in Java*](http://worldcat.org/oclc/837386973). Addison-Wesley. [ISBN](./ISBN_(identifier)) [978-0-201-36121-6](./Special:BookSources/978-0-201-36121-6). [OCLC](./OCLC_(identifier)) [837386973](https://search.worldcat.org/oclc/837386973).
9. [↑](./Depth-first_search#cite_ref-9) [Hopcroft, John](./John_Hopcroft); [Tarjan, Robert E.](./Robert_Tarjan) (1974), ["Efficient planarity testing"](https://ecommons.cornell.edu/bitstream/1813/6011/1/73-165.pdf) (PDF), *[Journal of the Association for Computing Machinery](./Journal_of_the_ACM)*, **21** (4): 549–568, [doi](./Doi_(identifier)):[10.1145/321850.321852](https://doi.org/10.1145%2F321850.321852), [hdl](./Hdl_(identifier)):[1813/6011](https://hdl.handle.net/1813%2F6011), [S2CID](./S2CID_(identifier)) [6279825](https://api.semanticscholar.org/CorpusID:6279825).
10. [↑](./Depth-first_search#cite_ref-10) de Fraysseix, H.; [Ossona de Mendez, P.](./Patrice_Ossona_de_Mendez); [Rosenstiehl, P.](./Pierre_Rosenstiehl) (2006), "Trémaux Trees and Planarity", *International Journal of Foundations of Computer Science*, **17** (5): 1017–1030, [arXiv](./ArXiv_(identifier)):[math/0610935](https://arxiv.org/abs/math/0610935), [Bibcode](./Bibcode_(identifier)):[2006math.....10935D](https://ui.adsabs.harvard.edu/abs/2006math.....10935D), [doi](./Doi_(identifier)):[10.1142/S0129054106004248](https://doi.org/10.1142%2FS0129054106004248), [S2CID](./S2CID_(identifier)) [40107560](https://api.semanticscholar.org/CorpusID:40107560).
11. [↑](./Depth-first_search#cite_ref-11) Baccelli, Francois; Haji-Mirsadeghi, Mir-Omid; Khezeli, Ali (2018), "Eternal family trees and dynamics on unimodular random graphs", in Sobieczky, Florian (ed.), *Unimodularity in Randomly Generated Graphs: AMS Special Session, October 8–9, 2016, Denver, Colorado*, Contemporary Mathematics, vol. 719, Providence, Rhode Island: American Mathematical Society, pp. 85–127, [arXiv](./ArXiv_(identifier)):[1608.05940](https://arxiv.org/abs/1608.05940), [doi](./Doi_(identifier)):[10.1090/conm/719/14471](https://doi.org/10.1090%2Fconm%2F719%2F14471), [ISBN](./ISBN_(identifier)) [978-1-4704-3914-9](./Special:BookSources/978-1-4704-3914-9), [MR](./MR_(identifier)) [3880014](https://mathscinet.ams.org/mathscinet-getitem?mr=3880014), [S2CID](./S2CID_(identifier)) [119173820](https://api.semanticscholar.org/CorpusID:119173820); see [Example 3.7, p. 93](https://books.google.com/books?id=7dV7DwAAQBAJ&pg=PA93)
12. [↑](./Depth-first_search#cite_ref-12) Reif, John H. (1985). "Depth-first search is inherently sequential". *Information Processing Letters*. **20** (5): 229–234. [doi](./Doi_(identifier)):[10.1016/0020-0190(85)90024-9](https://doi.org/10.1016%2F0020-0190%2885%2990024-9).
13. [↑](./Depth-first_search#cite_ref-mehlhorn_13-0) [Mehlhorn, Kurt](./Kurt_Mehlhorn); [Sanders, Peter](./Peter_Sanders_(computer_scientist)) (2008). [*Algorithms and Data Structures: The Basic Toolbox*](http://people.mpi-inf.mpg.de/~mehlhorn/ftp/Toolbox/GraphTraversal.pdf) (PDF). Springer. [Archived](https://web.archive.org/web/20150908084757/http://people.mpi-inf.mpg.de/~mehlhorn/ftp/Toolbox/GraphTraversal.pdf) (PDF) from the original on 2015-09-08.
14. [↑](./Depth-first_search#cite_ref-14) Aggarwal, A.; Anderson, R. J. (1988), "A random *NC* algorithm for depth first search", *[Combinatorica](./Combinatorica)*, **8** (1): 1–12, [doi](./Doi_(identifier)):[10.1007/BF02122548](https://doi.org/10.1007%2FBF02122548), [MR](./MR_(identifier)) [0951989](https://mathscinet.ams.org/mathscinet-getitem?mr=0951989), [S2CID](./S2CID_(identifier)) [29440871](https://api.semanticscholar.org/CorpusID:29440871).
15. [↑](./Depth-first_search#cite_ref-15) [Karger, David R.](./David_Karger); [Motwani, Rajeev](./Rajeev_Motwani) (1997), "An *NC* algorithm for minimum cuts", *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*, **26** (1): 255–272, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.33.1701](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.33.1701), [doi](./Doi_(identifier)):[10.1137/S0097539794273083](https://doi.org/10.1137%2FS0097539794273083), [MR](./MR_(identifier)) [1431256](https://mathscinet.ams.org/mathscinet-getitem?mr=1431256).

 

## References

  
- [Thomas H. Cormen](./Thomas_H._Cormen), [Charles E. Leiserson](./Charles_E._Leiserson), [Ronald L. Rivest](./Ronald_L._Rivest), and [Clifford Stein](./Clifford_Stein). *[Introduction to Algorithms](./Introduction_to_Algorithms)*, Second Edition. MIT Press and McGraw-Hill, 2001. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). Section 22.3: Depth-first search, pp. 540–549.
- [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2001), *Algorithm Design: Foundations, Analysis, and Internet Examples*, Wiley, [ISBN](./ISBN_(identifier)) [0-471-38365-1](./Special:BookSources/0-471-38365-1)
- [Kleinberg, Jon](./Jon_Kleinberg); [Tardos, Éva](./Éva_Tardos) (2006), *Algorithm Design*, Addison Wesley, pp. 92–94
- [Knuth, Donald E.](./Donald_Knuth) (1997), [*The Art of Computer Programming Vol 1. 3rd ed*](https://web.archive.org/web/20080904163709/http://www-cs-faculty.stanford.edu/~knuth/taocp.html), Boston: Addison-Wesley, [ISBN](./ISBN_(identifier)) [0-201-89683-4](./Special:BookSources/0-201-89683-4), [OCLC](./OCLC_(identifier)) [155842391](https://search.worldcat.org/oclc/155842391), archived from [the original](http://www-cs-faculty.stanford.edu/~knuth/taocp.html) on 2008-09-04, retrieved 2008-02-12

  

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Depth-first search](https://commons.wikimedia.org/wiki/Category:Depth-first%20search).  
- [Open Data Structures - Section 12.3.2 - Depth-First-Search](http://opendatastructures.org/versions/edition-0.1e/ods-java/12_3_Graph_Traversal.html#SECTION001532000000000000000), [Pat Morin](./Pat_Morin)
- [C++ Boost Graph Library: Depth-First Search](http://www.boost.org/libs/graph/doc/depth_first_search.html)
- [Depth-First Search Animation (for a directed graph)](http://www.cs.duke.edu/csed/jawaa/DFSanim.html)
- [Depth First and Breadth First Search: Explanation and Code](http://www.kirupa.com/developer/actionscript/depth_breadth_search.htm)
- [Depth-first search algorithm illustrated explanation (Java and C++ implementations)](http://www.algolist.net/Algorithms/Graph_algorithms/Undirected/Depth-first_search)
- [YAGSBPL – A template-based C++ library for graph search and planning](https://code.google.com/p/yagsbpl/)
- [Depth-First Search Visualization](https://www.cs.usfca.edu/~galles/visualization/DFS.html)

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |