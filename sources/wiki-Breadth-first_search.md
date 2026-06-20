---
source: https://en.wikipedia.org/wiki/Breadth-first_search
fetched: 2026-06-19
---

Algorithm to search the nodes of a graph 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Breadth-first search"–news·newspapers·books·scholar·JSTOR(April 2012)(Learn how and when to remove this message) |
| --- | --- |

 
| Animated example of a breadth-first search. Black = explored, grey = queued to be explored later on |
| --- |
| Class | Search algorithm |
| Data structure | Graph |
| Worst-caseperformance | O(|V|+|E|){\displaystyle O(|V|+|E|)} |
| Worst-casespace complexity | O(|V|){\displaystyle O(|V|)} |
| Optimal | Yes (always finds shortest paths) |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f5/BFS-Algorithm_Search_Way.gif/250px-BFS-Algorithm_Search_Way.gif)](./File:BFS-Algorithm_Search_Way.gif)BFS on [Maze-solving algorithm](./Maze-solving_algorithm) [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/da/Tic-tac-toe-game-tree.svg/250px-Tic-tac-toe-game-tree.svg.png)](./File:Tic-tac-toe-game-tree.svg)Top part of [Tic-tac-toe](./Tic-tac-toe) game tree 

**Breadth-first search** (**BFS**) is an [algorithm](./Algorithm) for searching a [tree](./Tree_(data_structure)) data structure for a node that satisfies a given property. It starts at the [tree root](./Tree_(data_structure)#Terminology) and explores all nodes at the present [depth](./Tree_(data_structure)#Terminology) prior to moving on to the nodes at the next depth level. Extra memory, usually a [queue](./Queue_(data_structure)), is needed to keep track of the child nodes that were encountered but not yet explored. 

 

For example, in a [chess endgame](./Chess_endgame), a [chess engine](./Chess_engine) may build the [game tree](./Game_tree) from the current position by applying all possible moves and use breadth-first search to find a winning position for White. Implicit trees (such as game trees or other problem-solving trees) may be of infinite size; breadth-first search is guaranteed to find a solution node[[1]](./Breadth-first_search#cite_note-1) if one exists.

 

In contrast, (plain) [depth-first search](./Depth-first_search) (DFS), which explores the node branch as far as possible before backtracking and expanding other nodes,[[2]](./Breadth-first_search#cite_note-2) may get lost in an infinite branch and never make it to the solution node. [Iterative deepening depth-first search](./Iterative_deepening_depth-first_search) avoids the latter drawback at the price of exploring the tree's top parts over and over again. On the other hand, both depth-first algorithms typically require far less extra memory than breadth-first search.[[3]](./Breadth-first_search#cite_note-3)

 

Breadth-first search can be generalized to both [undirected graphs](./Undirected_graph) and [directed graphs](./Directed_graph) with a given start node (sometimes referred to as a 'search key').[[4]](./Breadth-first_search#cite_note-4) In [state space search](./State_space_search) in [artificial intelligence](./Artificial_intelligence), repeated searches of vertices are often allowed, while in theoretical analysis of algorithms based on breadth-first search, precautions are typically taken to prevent repetitions.

 

BFS and its application in finding [connected components](./Connected_component_(graph_theory)) of graphs were invented in 1945 by [Konrad Zuse](./Konrad_Zuse), in his (rejected) Ph.D. thesis on the [Plankalkül](./Plankalkül) programming language, but this was not published until 1972.[[5]](./Breadth-first_search#cite_note-:0-5) It was reinvented in 1959 by [Edward F. Moore](./Edward_F._Moore), who used it to find the shortest path out of a maze,[[6]](./Breadth-first_search#cite_note-6)[[7]](./Breadth-first_search#cite_note-skiena-7) and later developed by C. Y. Lee into a [wire routing](./Routing_(electronic_design_automation)) algorithm (published in 1961).[[8]](./Breadth-first_search#cite_note-8)

 

## Pseudocode

 

The below pseudocode finds the [shortest path](./Shortest_path_problem) from a given root vertex to all other vertices in the graph using BFS.

 

**Input**: A graph G and a starting vertex root of G

 

**Output**: Goal state. The *parent* links trace the shortest path back to root[[9]](./Breadth-first_search#cite_note-9)

 
```
 1  procedure BFS(G, root) is
 2      let Q be a queue
 3      label root as explored
 4      Q.enqueue(root)
 5      while Q is not empty do
 6          v := Q.dequeue()
 7          if v is the goal then
 8              return v
 9          for all edges from v to w in G.adjacentEdges(v) do
10              if w is not labeled as explored then
11                  label w as explored
12                  w.parent := v
13                  Q.enqueue(w)
```
 

### More details

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/ad/MapGermanyGraph.svg/250px-MapGermanyGraph.svg.png)](./File:MapGermanyGraph.svg)An example map of [Southern Germany](./Southern_Germany) with some connections between cities [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/63/GermanyBFS.svg/250px-GermanyBFS.svg.png)](./File:GermanyBFS.svg)The breadth-first tree obtained when running BFS on the given map and starting in [Frankfurt](./Frankfurt) 

This non-recursive implementation is similar to the non-recursive implementation of [depth-first search](./Depth-first_search), but differs from it in two ways:

 
1. it uses a [queue](./Queue_(abstract_data_type)) ([First In First Out](./FIFO_(computing_and_electronics))) instead of a [stack](./Stack_(abstract_data_type)) (Last In First Out) and
2. it checks whether a vertex has been explored before enqueueing the vertex rather than delaying this check until the vertex is dequeued from the queue.

 

If G is a [tree](./Tree_(data_structure)), replacing the queue of this breadth-first search algorithm with a stack will yield a depth-first search algorithm. For general graphs, replacing the stack of the iterative depth-first search implementation with a queue would also produce a breadth-first search algorithm, although a somewhat nonstandard one.[[10]](./Breadth-first_search#cite_note-10)

 

The queue Q contains the frontier along which the algorithm is currently searching.

 

Nodes can be labelled as explored by storing them in a set, or by an attribute on each node, depending on the implementation.

 

The *parent* attribute of each node is useful for accessing the nodes in a shortest path, for example by backtracking from the destination node up to the starting node, once the BFS has been run, and the predecessors nodes have been set.

 

Breadth-first search produces a *breadth-first tree*. The diagrams on the right show the breadth-first tree obtained by running a BFS on an example graph of [German](./Germany) cities (upper diagram) starting from *Frankfurt*.

 

## Analysis

 

### Time and space complexity

 

The [time complexity](./Time_complexity) can be expressed as     O (  |  V  |  +  |  E  |  )   {\displaystyle O(|V|+|E|)}  ![{\displaystyle O(|V|+|E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7cf317fbe3965ae3164f28c1f6858696adb23f4), as every vertex and every edge will be explored in the worst case.      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) is the number of vertices and      |  E  |    {\displaystyle |E|}  ![{\displaystyle |E|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8c2b9637808cf805d411190b4ae017dbd4ef8d8) is the number of edges in the graph.
Note that     O (  |  E  |  )   {\displaystyle O(|E|)}  ![{\displaystyle O(|E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/976fe7f1e011d0dcdb3d6163754c877aaad5187f) may vary between     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) and     O (  |  V   |   2   )   {\displaystyle O(|V|^{2})}  ![{\displaystyle O(|V|^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e1e99764e23be92b694aef042c6460ff921357e3), depending on how sparse the input graph is.[[11]](./Breadth-first_search#cite_note-clrs-11)

 

When the number of vertices in the graph is known ahead of time, and additional data structures are used to determine which vertices have already been added to the queue, the [space complexity](./Space_complexity) can be expressed as     O (  |  V  |  )   {\displaystyle O(|V|)}  ![{\displaystyle O(|V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3486d00c2ed0f7eb1db550af8f239ad68241a6c5), where      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) is the number of vertices. This is in addition to the space
required for the graph itself, which may vary depending on the [graph representation](./Graph_(abstract_data_type)) used by an implementation of the algorithm.

 

When working with graphs that are too large to store explicitly (or infinite), it is more practical to describe the complexity of breadth-first search in different terms: to find the nodes that are at distance d from the start node (measured in number of edge traversals), BFS takes *O*(*b**d* + 1) time and memory, where b is the "[branching factor](./Branching_factor)" of the graph (the average out-degree).[[12]](./Breadth-first_search#cite_note-12): 81 

 

### Completeness

 

In the analysis of algorithms, the input to breadth-first search is assumed to be a finite graph, represented as an [adjacency list](./Adjacency_list), [adjacency matrix](./Adjacency_matrix), or similar representation. However, in the application of graph traversal methods in [artificial intelligence](./Artificial_intelligence) the input may be an [implicit representation](./Implicit_graph) of an infinite graph. In this context, a search method is described as being complete if it is guaranteed to find a goal state if one exists. Breadth-first search is complete, but depth-first search is not. When applied to infinite graphs represented implicitly, breadth-first search will eventually find the goal state, but depth first search may get lost in parts of the graph that have no goal state and never return.[[13]](./Breadth-first_search#cite_note-coppin-13)

 

## BFS ordering

 

An enumeration of the vertices of a graph is said to be a BFS ordering if it is a possible output of the application of BFS to this graph.

 

Let     G = ( V , E )   {\displaystyle G=(V,E)}  ![{\displaystyle G=(V,E)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/644a8d85ee410b6159ca2bdb5dcb9097e2c8f182) be a graph  with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) vertices.  Recall that     N ( v )   {\displaystyle N(v)}  ![{\displaystyle N(v)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2846ab53c26104918af619f1d0b77e8f563b77d6) is the set of neighbors of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597).
Let     σ σ  = (  v  1   , … …  ,  v  m   )   {\displaystyle \sigma =(v_{1},\dots ,v_{m})}  ![{\displaystyle \sigma =(v_{1},\dots ,v_{m})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b13202503c7a6dd9f8365417bb508f5311127a0) be a list of distinct elements of     V   {\displaystyle V}  ![{\displaystyle V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0f6064540e84211d0ffe4dac72098adfa52845), for     v ∈ ∈  V ∖ ∖  {  v  1   , … …  ,  v  m   }   {\displaystyle v\in V\setminus \{v_{1},\dots ,v_{m}\}}  ![{\displaystyle v\in V\setminus \{v_{1},\dots ,v_{m}\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/05e8658d9f01aa5d7e04d3e58510340c64199076), let      ν ν   σ σ    ( v )   {\displaystyle \nu _{\sigma }(v)}  ![{\displaystyle \nu _{\sigma }(v)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/467fa0c6c855395761965007256ad810ed2c9748) be the least     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) such that      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) is a neighbor of     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597), if such a     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) exists, and be     ∞ ∞    {\displaystyle \infty }  ![{\displaystyle \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c26c105004f30c27aa7c2a9c601550a4183b1f21) otherwise.

 

Let     σ σ  = (  v  1   , … …  ,  v  n   )   {\displaystyle \sigma =(v_{1},\dots ,v_{n})}  ![{\displaystyle \sigma =(v_{1},\dots ,v_{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5fb622aaee5ddab5f4de64b3fc1f39fed8cfcd15) be an enumeration of the vertices of     V   {\displaystyle V}  ![{\displaystyle V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0f6064540e84211d0ffe4dac72098adfa52845).
The enumeration     σ σ    {\displaystyle \sigma }  ![{\displaystyle \sigma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/59f59b7c3e6fdb1d0365a494b81fb9a696138c36) is said to be a BFS ordering (with source      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a)) if, for all     1 < i ≤ ≤  n   {\displaystyle 1<i\leq n}  ![{\displaystyle 1<i\leq n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7118998ccad2d63c18f98d150ab2bdccdb3cec63),      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) is the vertex     w ∈ ∈  V ∖ ∖  {  v  1   , … …  ,  v  i − −  1   }   {\displaystyle w\in V\setminus \{v_{1},\dots ,v_{i-1}\}}  ![{\displaystyle w\in V\setminus \{v_{1},\dots ,v_{i-1}\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4de4f6f20401fc17db343455a85bf1907df3afa6) such that      ν ν   (  v  1   , … …  ,  v  i − −  1   )   ( w )   {\displaystyle \nu _{(v_{1},\dots ,v_{i-1})}(w)}  ![{\displaystyle \nu _{(v_{1},\dots ,v_{i-1})}(w)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a0482d61c01179c94158fd6cfa9ab0ce52a4098) is minimal. Equivalently,     σ σ    {\displaystyle \sigma }  ![{\displaystyle \sigma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/59f59b7c3e6fdb1d0365a494b81fb9a696138c36) is a BFS ordering if, for all     1 ≤ ≤  i < j < k ≤ ≤  n   {\displaystyle 1\leq i<j<k\leq n}  ![{\displaystyle 1\leq i<j<k\leq n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a03b36f28b8d63a8fcb381ccb9fa1ac06d1a4c9d) with      v  i   ∈ ∈  N (  v  k   ) ∖ ∖  N (  v  j   )   {\displaystyle v_{i}\in N(v_{k})\setminus N(v_{j})}  ![{\displaystyle v_{i}\in N(v_{k})\setminus N(v_{j})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f8faaf5c978027fc2702390643f88d5b465e220), there exists a neighbor       v  m     {\displaystyle v_{m}}  ![{\displaystyle v_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e39c47348c7acfafbf415f12afaaff6e0a0900ca) of      v  j     {\displaystyle v_{j}}  ![{\displaystyle v_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/73fffa4919c0d6268f6a8d9f38c04dd3296fd0a5) such that     m < i   {\displaystyle m<i}  ![{\displaystyle m<i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a1277d6f707546d4f9407c6049004c5cb08d980e).

 

## Applications

 

Breadth-first search can be used to solve many problems in graph theory, for example:

 
- Copying [garbage collection](./Garbage_collection_(computer_science)), [Cheney's algorithm](./Cheney's_algorithm)
- Finding the [shortest path](./Shortest_path) between two nodes *u* and *v*, with path length measured by number of edges (an advantage over [depth-first search](./Depth-first_search))[[14]](./Breadth-first_search#cite_note-14)
- [(Reverse) Cuthill–McKee](./Cuthill–McKee_algorithm) mesh numbering
- [Ford–Fulkerson method](./Ford–Fulkerson_algorithm) for computing the [maximum flow](./Maximum_flow_problem) in a [flow network](./Flow_network)
- Serialization/Deserialization of a binary tree vs serialization in sorted order, allows the tree to be re-constructed in an efficient manner.
- Construction of the *failure function* of the [Aho-Corasick](./Aho-Corasick) pattern matcher.
- Testing [bipartiteness of a graph](./Bipartite_graph#Testing_bipartiteness).[[15]](./Breadth-first_search#cite_note-15)
- Implementing parallel algorithms for computing a graph's transitive closure.[[16]](./Breadth-first_search#cite_note-16)

 

## See also

 
- [Depth-first search](./Depth-first_search) – Algorithm to search the nodes of a graph
- [Dijkstra's algorithm](./Dijkstra's_algorithm) – Algorithm for finding shortest paths
- [Iterative deepening depth-first search](./Iterative_deepening_depth-first_search) – Tree searching strategy
- [Level structure](./Level_structure) – Object in graph theory
- [Lexicographic breadth-first search](./Lexicographic_breadth-first_search) – Partition-based graph traversal method
- [Parallel breadth-first search](./Parallel_breadth-first_search) – Parallel version of breadth-first search algorithm

 

## References

  
1. [↑](./Breadth-first_search#cite_ref-1) that is, a node satisfying the specified property
2. [↑](./Breadth-first_search#cite_ref-2) Cormen Thomas H.; et al. (2009). "22.3". *Introduction to Algorithms*. MIT Press.
3. [↑](./Breadth-first_search#cite_ref-3) [Korf, Richard E.](./Richard_E._Korf) (1985). ["Depth-First Iterative Deepening: An Optimal Admissible Tree Search"](https://doi.org/10.7916/D8HQ46X1). *Artificial Intelligence* (27): 99–100. [doi](./Doi_(identifier)):[10.7916/D8HQ46X1](https://doi.org/10.7916%2FD8HQ46X1).
4. [↑](./Breadth-first_search#cite_ref-4) ["Graph500 benchmark specification (supercomputer performance evaluation)"](https://web.archive.org/web/20150326055019/http://www.graph500.org/specifications#sec-5#sec-5). Graph500.org, 2010. Archived from [the original](http://www.graph500.org/specifications#sec-5) on 2015-03-26. Retrieved 2015-03-15.
5. [↑](./Breadth-first_search#cite_ref-:0_5-0) [Zuse, Konrad](./Konrad_Zuse) (1972), [*Der Plankalkül*](http://zuse.zib.de/item/gHI1cNsUuQweHB6) (in German), Konrad Zuse Internet Archive. See pp. 96–105 of the linked pdf file (internal numbering 2.47–2.56).
6. [↑](./Breadth-first_search#cite_ref-6) [Moore, Edward F.](./Edward_F._Moore) (1959). "The shortest path through a maze". *Proceedings of the International Symposium on the Theory of Switching*. Harvard University Press. pp. 285–292. As cited by Cormen, Leiserson, Rivest, and Stein.
7. [↑](./Breadth-first_search#cite_ref-skiena_7-0) [Skiena, Steven](./Steven_Skiena) (2008). "Sorting and Searching". *The Algorithm Design Manual*. Springer. p. 480. [Bibcode](./Bibcode_(identifier)):[2008adm..book.....S](https://ui.adsabs.harvard.edu/abs/2008adm..book.....S). [doi](./Doi_(identifier)):[10.1007/978-1-84800-070-4_4](https://doi.org/10.1007%2F978-1-84800-070-4_4). [ISBN](./ISBN_(identifier)) [978-1-84800-069-8](./Special:BookSources/978-1-84800-069-8).
8. [↑](./Breadth-first_search#cite_ref-8) Lee, C. Y. (1961). "An Algorithm for Path Connections and Its Applications". *IRE Transactions on Electronic Computers* (3): 346–365. [doi](./Doi_(identifier)):[10.1109/TEC.1961.5219222](https://doi.org/10.1109%2FTEC.1961.5219222). [S2CID](./S2CID_(identifier)) [40700386](https://api.semanticscholar.org/CorpusID:40700386).
9. [↑](./Breadth-first_search#cite_ref-9) Cormen, Thomas H. (January 2010). "22.2 Breadth-first search". [*Introduction to algorithms*](http://worldcat.org/oclc/1006880283). Prentice-Hall Of India Pvt. Limited. [ISBN](./ISBN_(identifier)) [978-81-203-4007-7](./Special:BookSources/978-81-203-4007-7). [OCLC](./OCLC_(identifier)) [1006880283](https://search.worldcat.org/oclc/1006880283).
10. [↑](./Breadth-first_search#cite_ref-10) ["Stack-based graph traversal ≠ depth first search"](https://11011110.github.io/blog/2013/12/17/stack-based-graph-traversal.html). *11011110.github.io*. Retrieved 2020-06-10.
11. [↑](./Breadth-first_search#cite_ref-clrs_11-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. "22.2 Breadth-first search". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 531–539. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
12. [↑](./Breadth-first_search#cite_ref-12) [Russell, Stuart](./Stuart_J._Russell); [Norvig, Peter](./Peter_Norvig) (2003) [1995]. *[Artificial Intelligence: A Modern Approach](./Artificial_Intelligence:_A_Modern_Approach)* (2nd ed.). Prentice Hall. [ISBN](./ISBN_(identifier)) [978-0137903955](./Special:BookSources/978-0137903955).
13. [↑](./Breadth-first_search#cite_ref-coppin_13-0) Coppin, B. (2004). Artificial intelligence illuminated. Jones & Bartlett Learning. pp. 79–80.
14. [↑](./Breadth-first_search#cite_ref-14) Aziz, Adnan; Prakash, Amit (2010). "4. Algorithms on Graphs". *Algorithms for Interviews*. Algorithmsforinterviews.com. p. 144. [ISBN](./ISBN_(identifier)) [978-1453792995](./Special:BookSources/978-1453792995).
15. [↑](./Breadth-first_search#cite_ref-15) [Kleinberg, Jon](./Jon_Kleinberg); [Tardos, Éva](./Éva_Tardos) (2006), *Algorithm Design*, Addison Wesley, pp. 94–97.
16. [↑](./Breadth-first_search#cite_ref-16) Dhulipala, Laxman; Blelloch, Guy E.; Shun, Julian (August 21, 2019). *Theoretically Efficient Parallel Graph Algorithms Can Be Fast and Scalable*. p. 17. [arXiv](./ArXiv_(identifier)):[1805.05208](https://arxiv.org/abs/1805.05208). [doi](./Doi_(identifier)):[10.1145/3210377.3210414](https://doi.org/10.1145%2F3210377.3210414). [ISBN](./ISBN_(identifier)) [9781450357999](./Special:BookSources/9781450357999). [S2CID](./S2CID_(identifier)) [44126609](https://api.semanticscholar.org/CorpusID:44126609).

  
- [Knuth, Donald E.](./Donald_Knuth) (1997), [*The Art of Computer Programming Vol 1. 3rd ed.*](https://web.archive.org/web/20080904163709/http://www-cs-faculty.stanford.edu/~knuth/taocp.html), Boston: Addison-Wesley, [ISBN](./ISBN_(identifier)) [978-0-201-89683-1](./Special:BookSources/978-0-201-89683-1), archived from [the original](http://www-cs-faculty.stanford.edu/~knuth/taocp.html) on 2008-09-04, retrieved 2008-02-09

  

## External links

 
- [Open Data Structures - Section 12.3.1 - Breadth-First Search](https://web.archive.org/web/20141029100806/http://opendatastructures.org/versions/edition-0.1e/ods-java/12_3_Graph_Traversal.html#SECTION001531000000000000000), [Pat Morin](./Pat_Morin)

 
| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |