---
source: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm
fetched: 2026-06-19
---

Algorithm in graph theory 

 "Floyd's algorithm" redirects here. For cycle detection, see [Floyd's cycle-finding algorithm](./Floyd's_cycle-finding_algorithm). For computer graphics, see [Floyd–Steinberg dithering](./Floyd–Steinberg_dithering). 
| Class | All-pairs shortest path problem(for weighted graphs) |
| --- | --- |
| Data structure | Graph |
| Worst-caseperformance | Θ(|V|3){\displaystyle \Theta (|V|^{3})} |
| Best-caseperformance | Θ(|V|3){\displaystyle \Theta (|V|^{3})} |
| Averageperformance | Θ(|V|3){\displaystyle \Theta (|V|^{3})} |
| Worst-casespace complexity | Θ(|V|2){\displaystyle \Theta (|V|^{2})} |

 

In [computer science](./Computer_science), the **Floyd–Warshall algorithm** (also known as **Floyd's algorithm**, the **Roy–Warshall algorithm**, the **Roy–Floyd algorithm**, or the **WFI algorithm**) is an [algorithm](./Algorithm) for finding [shortest paths](./Shortest_path_problem) in a directed [weighted graph](./Weighted_graph) with positive or negative edge weights (but with no negative cycles).[[1]](./Floyd–Warshall_algorithm#cite_note-:0-1)[[2]](./Floyd–Warshall_algorithm#cite_note-2) A single execution of the algorithm will find the lengths (summed weights) of shortest paths between all pairs of vertices. Although it does not return details of the paths themselves, it is possible to reconstruct the paths with simple modifications to the algorithm. Versions of the algorithm can also be used for finding the [transitive closure](./Transitive_closure) of a relation, or (in connection with the [Schulze voting system](./Schulze_method)) [widest paths](./Widest_path_problem) between all pairs of vertices in a weighted graph.

 

## History and naming

 

The Floyd–Warshall algorithm is an example of [dynamic programming](./Dynamic_programming), and was published in its currently recognized form by [Robert Floyd](./Robert_W._Floyd) in 1962.[[3]](./Floyd–Warshall_algorithm#cite_note-3)  However, it is essentially the same as algorithms previously published by [Bernard Roy](./Bernard_Roy) in 1959[[4]](./Floyd–Warshall_algorithm#cite_note-4) and also by [Stephen Warshall](./Stephen_Warshall) in 1962[[5]](./Floyd–Warshall_algorithm#cite_note-5) for finding the transitive closure of a graph,[[6]](./Floyd–Warshall_algorithm#cite_note-6) and is closely related to [Kleene's algorithm](./Kleene's_algorithm) (published in 1956) for converting a [deterministic finite automaton](./Deterministic_finite_automaton) into a [regular expression](./Regular_expression), with the difference being the use of a min-plus [semiring](./Semiring).[[7]](./Floyd–Warshall_algorithm#cite_note-7) The modern formulation of the algorithm as three nested for-loops was first described by Peter Ingerman, also in 1962.[[8]](./Floyd–Warshall_algorithm#cite_note-8)

 

## Algorithm

 

The Floyd–Warshall algorithm compares many possible paths through the graph between each pair of vertices. It is guaranteed to find all shortest paths and is able to do this with     Θ Θ  (  |  V   |   3   )   {\displaystyle \Theta (|V|^{3})}  ![{\displaystyle \Theta (|V|^{3})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b89800bb4f210f469a91b23b045aa481e5fd176e) comparisons in a graph,[[1]](./Floyd–Warshall_algorithm#cite_note-:0-1)[[9]](./Floyd–Warshall_algorithm#cite_note-:1-9) even though there may be     Θ Θ  (  |  V   |   2   )   {\displaystyle \Theta (|V|^{2})}  ![{\displaystyle \Theta (|V|^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5dbb38dcf2365c1dbf786871f4014dd1a2762df7) edges in the graph.  It does so by incrementally improving an estimate on the shortest path between two vertices, until the estimate is optimal.

 

Consider a graph     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b) with vertices     V   {\displaystyle V}  ![{\displaystyle V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0f6064540e84211d0ffe4dac72098adfa52845) numbered 1 through     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3). Further consider a function      s h o r t e s t P a t h  ( i , j , k )   {\displaystyle \mathrm {shortestPath} (i,j,k)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da0a72bd3bd16adcff4b3ef0baa061643a38393c) that returns the length of the shortest possible path (if one exists) from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) using vertices only from the set     { 1 , 2 , … …  , k }   {\displaystyle \{1,2,\ldots ,k\}}  ![{\displaystyle \{1,2,\ldots ,k\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e3836453b6a15e5c6ca10a0408fe82de44322fb3) as intermediate points along the way.  Now, given this function, our goal is to find the length of the shortest path from each     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to each     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) using *any* vertex in     { 1 , 2 , … …  , N }   {\displaystyle \{1,2,\ldots ,N\}}  ![{\displaystyle \{1,2,\ldots ,N\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18d7b4ef5cabdf43044424420855eeaf363f0c09). By definition, this is the value      s h o r t e s t P a t h  ( i , j , N )   {\displaystyle \mathrm {shortestPath} (i,j,N)}  ![{\displaystyle \mathrm {shortestPath} (i,j,N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/10b7cee0e900c6d0dfdd2ca265c4e0b396ebd5a1), which we will find [recursively](./Recursion).

 

Observe that      s h o r t e s t P a t h  ( i , j , k )   {\displaystyle \mathrm {shortestPath} (i,j,k)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da0a72bd3bd16adcff4b3ef0baa061643a38393c) must be less than or equal to      s h o r t e s t P a t h  ( i , j , k − −  1 )   {\displaystyle \mathrm {shortestPath} (i,j,k-1)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5997ae5bc81aeb05219d13a566255d3953c08c9): we have *more* flexibility if we are allowed to use the vertex     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). If      s h o r t e s t P a t h  ( i , j , k )   {\displaystyle \mathrm {shortestPath} (i,j,k)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da0a72bd3bd16adcff4b3ef0baa061643a38393c) is in fact less than      s h o r t e s t P a t h  ( i , j , k − −  1 )   {\displaystyle \mathrm {shortestPath} (i,j,k-1)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5997ae5bc81aeb05219d13a566255d3953c08c9), then there must be a path from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) using the vertices     { 1 , 2 , … …  , k }   {\displaystyle \{1,2,\ldots ,k\}}  ![{\displaystyle \{1,2,\ldots ,k\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e3836453b6a15e5c6ca10a0408fe82de44322fb3) that is shorter than any such path that does not use the vertex     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). Since there are no negative cycles this path can be decomposed as:

 (1) a path from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) that uses the vertices     { 1 , 2 , … …  , k − −  1 }   {\displaystyle \{1,2,\ldots ,k-1\}}  ![{\displaystyle \{1,2,\ldots ,k-1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e31a80ba97c78f8fac9a97a7780d85f90a8619b), followed by (2) a path from     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) that uses the vertices     { 1 , 2 , … …  , k − −  1 }   {\displaystyle \{1,2,\ldots ,k-1\}}  ![{\displaystyle \{1,2,\ldots ,k-1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e31a80ba97c78f8fac9a97a7780d85f90a8619b). 

And of course, these must be a *shortest* such path (or several of them), otherwise we could further decrease the length. In other words, we have arrived at the recursive formula:

      s h o r t e s t P a t h  ( i , j , k ) =   {\displaystyle \mathrm {shortestPath} (i,j,k)=}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)=}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f9b75e25063384ccca499c56f9a279abf661ad3b)      m i n    (    s h o r t e s t P a t h  ( i , j , k − −  1 ) ,   {\displaystyle \mathrm {min} {\Big (}\mathrm {shortestPath} (i,j,k-1),}  ![{\displaystyle \mathrm {min} {\Big (}\mathrm {shortestPath} (i,j,k-1),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34ac7c89bbb18df3fd660225fd38997079e5e513)      s h o r t e s t P a t h  ( i , k , k − −  1 ) +  s h o r t e s t P a t h  ( k , j , k − −  1 )   )     {\displaystyle \mathrm {shortestPath} (i,k,k-1)+\mathrm {shortestPath} (k,j,k-1){\Big )}}  ![{\displaystyle \mathrm {shortestPath} (i,k,k-1)+\mathrm {shortestPath} (k,j,k-1){\Big )}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0326d6c14def89269c029da59eba012d0f2edc9d). 

The base case is given by

      s h o r t e s t P a t h  ( i , j , 0 ) = w ( i , j ) ,   {\displaystyle \mathrm {shortestPath} (i,j,0)=w(i,j),}  ![{\displaystyle \mathrm {shortestPath} (i,j,0)=w(i,j),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/23862c8ea0f4a4f00a00dded1176557e4f33b84c) 

where     w ( i , j )   {\displaystyle w(i,j)}  ![{\displaystyle w(i,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/860cd28acf764c9e3a8955c71ba6ee4e6c831b88) denotes the weight of the edge from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) if one exists and ∞ (infinity) otherwise.

 

These formulas are the heart of the Floyd–Warshall algorithm. The algorithm works by first computing      s h o r t e s t P a t h  ( i , j , k )   {\displaystyle \mathrm {shortestPath} (i,j,k)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da0a72bd3bd16adcff4b3ef0baa061643a38393c) for all     ( i , j )   {\displaystyle (i,j)}  ![{\displaystyle (i,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ef21910f980c6fca2b15bee102a7a0d861ed712) pairs for     k = 0   {\displaystyle k=0}  ![{\displaystyle k=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6307c8a99dad7d0bcb712352ae0a748bd99a038b), then     k = 1   {\displaystyle k=1}  ![{\displaystyle k=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c035ffa69b5bca8bf2d16c3da3aaad79a8bcbfa), then     k = 2   {\displaystyle k=2}  ![{\displaystyle k=2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0bd301789e1f25a3da4be297ff637754ebee5f5d), and so on.  This process continues until     k = N   {\displaystyle k=N}  ![{\displaystyle k=N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e302b20f7f5064ac2ebb7734304fd430ad737a7), and we have found the shortest path for all     ( i , j )   {\displaystyle (i,j)}  ![{\displaystyle (i,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ef21910f980c6fca2b15bee102a7a0d861ed712) pairs using any intermediate vertices. Pseudocode for this basic version follows.

 

### Pseudocode

 
```
let dist be a |V| × |V| array of minimum distances initialized to ∞ (infinity)
for each edge (u, v) do
    dist[u][v] = w(u, v)  // The weight of the edge (u, v)
for each vertex v do
    dist[v][v] = 0
for k from 1 to |V|
    for i from 1 to |V|
        for j from 1 to |V|
            if dist[i][j] > dist[i][k] + dist[k][j] 
                dist[i][j] = dist[i][k] + dist[k][j]
            end if
```
 

Note: A common mistake in implementing the Floyd–Warshall algorithm is to misorder the triply nested loops (The correct order is `KIJ`). The incorrect `IJK` and `IKJ` algorithms do not give correct solutions for some instance. However, we can prove that if these are repeated three times, we obtain the correct solutions.[[10]](./Floyd–Warshall_algorithm#cite_note-10)

 

## Example

 

The algorithm above is executed on the graph on the left below:

 

[![](//upload.wikimedia.org/wikipedia/commons/thumb/2/2e/Floyd-Warshall_example.svg/960px-Floyd-Warshall_example.svg.png)](./File:Floyd-Warshall_example.svg)

 

Prior to the first recursion of the outer loop, labeled *k* = 0 above, the only known paths correspond to the single edges in the graph. At *k* = 1, paths that go through the vertex 1 are found: in particular, the path [2,1,3] is found, replacing the path [2,3] which has fewer edges but is longer (in terms of weight). At *k* = 2, paths going through the vertices {1,2} are found. The red and blue boxes show how the path [4,2,1,3] is assembled from the two known paths [4,2] and [2,1,3] encountered in previous iterations, with 2 in the intersection. The path [4,2,3] is not considered, because [2,1,3] is the shortest path encountered so far from 2 to 3. At *k* = 3, paths going through the vertices {1,2,3} are found. Finally, at *k* = 4, all shortest paths are found.

 

The distance matrix at each iteration of k, with the updated distances in **bold**, will be:

 
| k= 0 | j |
| --- | --- |
| 1 | 2 | 3 | 4 |
| i | 1 | 0 | ∞ | −2 | ∞ |
| 2 | 4 | 0 | 3 | ∞ |
| 3 | ∞ | ∞ | 0 | 2 |
| 4 | ∞ | −1 | ∞ | 0 |

 
| k= 1 | j |
| --- | --- |
| 1 | 2 | 3 | 4 |
| i | 1 | 0 | ∞ | −2 | ∞ |
| 2 | 4 | 0 | 2 | ∞ |
| 3 | ∞ | ∞ | 0 | 2 |
| 4 | ∞ | −1 | ∞ | 0 |

 
| k= 2 | j |
| --- | --- |
| 1 | 2 | 3 | 4 |
| i | 1 | 0 | ∞ | −2 | ∞ |
| 2 | 4 | 0 | 2 | ∞ |
| 3 | ∞ | ∞ | 0 | 2 |
| 4 | 3 | −1 | 1 | 0 |

 
| k= 3 | j |
| --- | --- |
| 1 | 2 | 3 | 4 |
| i | 1 | 0 | ∞ | −2 | 0 |
| 2 | 4 | 0 | 2 | 4 |
| 3 | ∞ | ∞ | 0 | 2 |
| 4 | 3 | −1 | 1 | 0 |

 
| k= 4 | j |
| --- | --- |
| 1 | 2 | 3 | 4 |
| i | 1 | 0 | −1 | −2 | 0 |
| 2 | 4 | 0 | 2 | 4 |
| 3 | 5 | 1 | 0 | 2 |
| 4 | 3 | −1 | 1 | 0 |

  

## Behavior with negative cycles

 

A negative cycle is a cycle whose edges sum to a negative value.  There is no shortest path between any pair of vertices     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20),     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) which form part of a negative cycle,  because path-lengths from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) to     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) can be arbitrarily small (negative).  For numerically meaningful output, the Floyd–Warshall algorithm assumes that there are no negative cycles.  Nevertheless, if there are negative cycles, the Floyd–Warshall algorithm can be used to detect them.  The intuition is as follows:

 
- The Floyd–Warshall algorithm iteratively revises path lengths between all pairs of vertices     ( i , j )   {\displaystyle (i,j)}  ![{\displaystyle (i,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ef21910f980c6fca2b15bee102a7a0d861ed712), including where     i = j   {\displaystyle i=j}  ![{\displaystyle i=j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/706e0928b2bf0f24076b0c90bb20616ff2068343);
- Initially, the length of the path     ( i , i )   {\displaystyle (i,i)}  ![{\displaystyle (i,i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/899c08ccec9bf245d850a44ba8a5275bee6b3b8d) is zero;
- A path     [ i , k , … …  , i ]   {\displaystyle [i,k,\ldots ,i]}  ![{\displaystyle [i,k,\ldots ,i]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/19877ceaf724fa3a7dcc51b9853630a0f31b33c3) can only improve upon this if it has length less than zero, i.e. denotes a negative cycle;
- Thus, after the algorithm,     ( i , i )   {\displaystyle (i,i)}  ![{\displaystyle (i,i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/899c08ccec9bf245d850a44ba8a5275bee6b3b8d) will be negative if there exists a negative-length path from     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) back to     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20).

 

Hence, to detect negative [cycles](./Cycle_(graph_theory)) using the Floyd–Warshall algorithm, one can inspect the diagonal of the path matrix, and the presence of a negative number indicates that the graph contains at least one negative cycle.[[9]](./Floyd–Warshall_algorithm#cite_note-:1-9) However, when a negative cycle is present, during the execution of the algorithm exponentially large numbers on the order of     Ω Ω  (  6  n   ⋅ ⋅   w  m a x   )   {\displaystyle \Omega (6^{n}\cdot w_{max})}  ![{\displaystyle \Omega (6^{n}\cdot w_{max})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5ed0ab02dc9958f492b34481e7c84022e68608a2) can appear, where      w  m a x     {\displaystyle w_{max}}  ![{\displaystyle w_{max}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/985bd43745ee322dbfee514b0fb5863dfe102a3c) is the largest absolute value edge weight in the graph. To avoid integer underflow problems, one should check for a negative cycle within the innermost for loop of the algorithm.[[11]](./Floyd–Warshall_algorithm#cite_note-11)

 

## Path reconstruction

 

The Floyd–Warshall algorithm typically only provides the lengths of the paths between all pairs of vertices. With simple modifications, it is possible to create a method to reconstruct the actual path between any two endpoint vertices. While one may be inclined to store the actual path from each vertex to each other vertex, this is not necessary, and in fact, is very costly in terms of memory. Instead, we can use the [shortest-path tree](./Shortest-path_tree), which can be calculated for each node in     Θ Θ  (  |  E  |  )   {\displaystyle \Theta (|E|)}  ![{\displaystyle \Theta (|E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fee8b4657c1eb491bc9d05378522ddc12ddac5fc) time using     Θ Θ  (  |  V  |  )   {\displaystyle \Theta (|V|)}  ![{\displaystyle \Theta (|V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d6859084635373622fc54329d559928d0d564d42) memory, and allows us to efficiently reconstruct a directed path between any two connected vertices.

 

### Pseudocode

 

The array `prev[u][v]` holds the penultimate vertex on the path from `u` to `v` (except in the case of `prev[v][v]`, where it always contains `v` even if there is no self-loop on `v`):[[12]](./Floyd–Warshall_algorithm#cite_note-12)

 
```
let dist be a 
  
    
      
        
          |
        
        V
        
          |
        
        ×
        
          |
        
        V
        
          |
        
      
    
    {\displaystyle |V|\times |V|}
  
 array of minimum distances initialized to 
  
    
      
        ∞
      
    
    {\displaystyle \infty }
  
 (infinity)
let prev be a 
  
    
      
        
          |
        
        V
        
          |
        
        ×
        
          |
        
        V
        
          |
        
      
    
    {\displaystyle |V|\times |V|}
  
 array of vertex indices initialized to null

procedure FloydWarshallWithPathReconstruction() is
    for each edge (u, v) do
        dist[u][v] = w(u, v)  // The weight of the edge (u, v)
        prev[u][v] = u
    for each vertex v do
        dist[v][v] = 0
        prev[v][v] = v
    for k from 1 to |V| do // standard Floyd-Warshall implementation
        for i from 1 to |V|
            for j from 1 to |V|
                if dist[i][j] > dist[i][k] + dist[k][j] then
                    dist[i][j] = dist[i][k] + dist[k][j]
                    prev[i][j] = prev[k][j]
```
 
```
procedure Path(u, v) is
    if prev[u][v] = null then
        return []
    path = [v]
    while u ≠ v do
        v = prev[u][v]
        path.prepend(v)
    return path
```
 

## Time complexity

 

Let     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) be      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7), the number of vertices. To find all      n  2     {\displaystyle n^{2}}  ![{\displaystyle n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ac9810bbdafe4a6a8061338db0f74e25b7952620) of 
     s h o r t e s t P a t h  ( i , j , k )   {\displaystyle \mathrm {shortestPath} (i,j,k)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/da0a72bd3bd16adcff4b3ef0baa061643a38393c) (for all     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) and     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0)) from those of
     s h o r t e s t P a t h  ( i , j , k − −  1 )   {\displaystyle \mathrm {shortestPath} (i,j,k-1)}  ![{\displaystyle \mathrm {shortestPath} (i,j,k-1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5997ae5bc81aeb05219d13a566255d3953c08c9) requires [    Θ Θ  (  n  2   )   {\displaystyle \Theta (n^{2})}  ![{\displaystyle \Theta (n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/215877752c4f392a7276328d4d37709bf7c3f55d)](./Big_theta) operations. Since we begin with
     s h o r t e s t P a t h  ( i , j , 0 ) =  e d g e C o s t  ( i , j )   {\displaystyle \mathrm {shortestPath} (i,j,0)=\mathrm {edgeCost} (i,j)}  ![{\displaystyle \mathrm {shortestPath} (i,j,0)=\mathrm {edgeCost} (i,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d3d4efe797fa90aa43cf20fd20a1562ca4160d5) and compute the sequence of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) matrices      s h o r t e s t P a t h  ( i , j , 1 )   {\displaystyle \mathrm {shortestPath} (i,j,1)}  ![{\displaystyle \mathrm {shortestPath} (i,j,1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d579582db8fe3121bb4ee775f60a77e9d3131bf),      s h o r t e s t P a t h  ( i , j , 2 )   {\displaystyle \mathrm {shortestPath} (i,j,2)}  ![{\displaystyle \mathrm {shortestPath} (i,j,2)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/449ff862e43e958555fc9f8a78f2ce80df0db396),     … …    {\displaystyle \ldots }  ![{\displaystyle \ldots }](https://wikimedia.org/api/rest_v1/media/math/render/svg/3b8619532e44ee1ccae3ab03405a6885260d09ed),      s h o r t e s t P a t h  ( i , j , n )   {\displaystyle \mathrm {shortestPath} (i,j,n)}  ![{\displaystyle \mathrm {shortestPath} (i,j,n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ece65972ee8c39a8be2c1a760ebab5a5159889d7), each having a cost of     Θ Θ  (  n  2   )   {\displaystyle \Theta (n^{2})}  ![{\displaystyle \Theta (n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/215877752c4f392a7276328d4d37709bf7c3f55d),
the total [time complexity](./Time_complexity) of the algorithm is     n ⋅ ⋅  Θ Θ  (  n  2   ) = Θ Θ  (  n  3   )   {\displaystyle n\cdot \Theta (n^{2})=\Theta (n^{3})}  ![{\displaystyle n\cdot \Theta (n^{2})=\Theta (n^{3})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/764feb1180d30cfe91fc716ba4011f05f50e4f2a).[[9]](./Floyd–Warshall_algorithm#cite_note-:1-9)[[13]](./Floyd–Warshall_algorithm#cite_note-13)

 

## Applications and generalizations

 

The Floyd–Warshall algorithm can be used to solve the following problems:

 
- [Transitive closure](./Transitive_closure) of directed graphs (Warshall's algorithm). In Warshall's original formulation of the algorithm, the graph is unweighted and represented by a Boolean [adjacency matrix](./Adjacency_matrix). Then the addition operation is replaced by [logical conjunction](./Logical_conjunction) (AND) and the minimum operation by [logical disjunction](./Logical_disjunction) (OR).
- Finding a [regular expression](./Regular_expression) denoting the [regular language](./Regular_language) accepted by a [finite automaton](./Finite_automaton) ([Kleene's algorithm](./Kleene's_algorithm), a closely related generalization of the Floyd–Warshall algorithm)[[14]](./Floyd–Warshall_algorithm#cite_note-14)
- [Inversion](./Invertible_matrix) of [real](./Real_number) [matrices](./Matrix_(mathematics)) ([Gauss–Jordan algorithm](./Gauss–Jordan_elimination))[[15]](./Floyd–Warshall_algorithm#cite_note-15)
- Optimal routing. In this application one is interested in finding the path with the maximum flow between two vertices. This means that, rather than taking minima as in the pseudocode above, one instead takes maxima. The edge weights represent fixed constraints on flow. Path weights represent bottlenecks; so the addition operation above is replaced by the minimum operation.
- Fast computation of [Pathfinder networks](./Pathfinder_network).
- [Widest paths/Maximum bandwidth paths](./Widest_path_problem)
- Computing canonical form of difference bound matrices (DBMs)
- Computing the similarity between graphs
- Transitive closure in AND/OR/threshold graphs.[[16]](./Floyd–Warshall_algorithm#cite_note-16)

 

## Implementations

 

Implementations are available for many [programming languages](./Programming_language).

 
- For [C++](./C++), in the [boost::graph](http://www.boost.org/libs/graph/doc/) library
- For [C#](./C_Sharp_(programming_language)), at [QuikGraph](https://github.com/KeRNeLith/QuikGraph)
- For [C#](./C_Sharp_(programming_language)), at [QuickGraphPCL](https://www.nuget.org/packages/QuickGraphPCL/3.6.61114.2) (A fork of QuickGraph with better compatibility with projects using Portable Class Libraries.)
- For [Java](./Java_(programming_language)), in the [Apache Commons Graph](https://commons.apache.org/sandbox/commons-graph/) library
- For [JavaScript](./JavaScript), in the [Cytoscape](./Cytoscape) library
- For [Julia](./Julia_(programming_language)), in the [Graphs.jl](https://docs.juliahub.com/Graphs/VJ6vx/1.7.0/algorithms/shortestpaths/#Graphs.floyd_warshall_shortest_paths-Union{Tuple{AbstractGraph{U}},%20Tuple{T},%20Tuple{U},%20Tuple{AbstractGraph{U},%20AbstractMatrix{T}}}%20where%20{U%3C:Integer,%20T%3C:Real}) package
- For [MATLAB](./MATLAB), in the [Matlab_bgl](http://www.mathworks.com/matlabcentral/fileexchange/10922) [Archived](https://web.archive.org/web/20130817093138/http://www.mathworks.com/matlabcentral/fileexchange/10922) 2013-08-17 at the [Wayback Machine](./Wayback_Machine) package
- For [Perl](./Perl), in the [Graph](https://metacpan.org/module/Graph) module
- For [Python](./Python_(programming_language)), in the [SciPy](./SciPy) library (module [scipy.sparse.csgraph](http://docs.scipy.org/doc/scipy/reference/generated/scipy.sparse.csgraph.floyd_warshall.html#scipy.sparse.csgraph.floyd_warshall)) or [NetworkX](./NetworkX) library
- For [R](./R_programming_language), in packages [e1071](https://cran.r-project.org/web/packages/e1071/index.html) and [Rfast](https://cran.r-project.org/web/packages/Rfast/index.html)
- For [C](./C_(programming_language)), a [pthreads](./Pthreads), [parallelized](https://moorejs.github.io/APSP-in-parallel/), implementation including a [SQLite](./SQLite) interface to the data at [floydWarshall.h](https://github.com/gdavidbutler/pthreadChannel/blob/master/example/floydWarshall.h)

 

## Comparison with other shortest path algorithms

 

For graphs with non-negative edge weights, [Dijkstra's algorithm](./Dijkstra's_algorithm) can be used to find all shortest paths from a *single* vertex with running time     Θ Θ  (  |  E  |  +  |  V  |  log ⁡ ⁡   |  V  |  )   {\displaystyle \Theta (|E|+|V|\log |V|)}  ![{\displaystyle \Theta (|E|+|V|\log |V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e22162be85d06b346f3b7f7aad9746da0c1019c9). Thus, running Dijkstra starting at *each* vertex takes time     Θ Θ  (  |  E  |   |  V  |  +  |  V   |   2   log ⁡ ⁡   |  V  |  )   {\displaystyle \Theta (|E||V|+|V|^{2}\log |V|)}  ![{\displaystyle \Theta (|E||V|+|V|^{2}\log |V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a62bd0a9e63328e60dcea3f0ec8a585fcff3e68d). Since      |  E  |  = O (  |  V   |   2   )   {\displaystyle |E|=O(|V|^{2})}  ![{\displaystyle |E|=O(|V|^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2721551edc09c244a2619b38791552dfe65928c0), this yields a worst-case running time of repeated Dijkstra of     O (  |  V   |   3   )   {\displaystyle O(|V|^{3})}  ![{\displaystyle O(|V|^{3})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/04ad8b53a2cea864c6d746895cc7397971f72912). While this matches the asymptotic worst-case running time of the Floyd-Warshall algorithm, the constants involved matter quite a lot. When a [graph is dense](./Dense_graph) (i.e.,      |  E  |  ≈ ≈   |  V   |   2     {\displaystyle |E|\approx |V|^{2}}  ![{\displaystyle |E|\approx |V|^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/000d44adc1b18a1e707edbe33c3dba6385bcae5c)), the Floyd-Warshall algorithm tends to perform better in practice. When the graph is sparse (i.e.,      |  E  |    {\displaystyle |E|}  ![{\displaystyle |E|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8c2b9637808cf805d411190b4ae017dbd4ef8d8) is significantly smaller than      |  V   |   2     {\displaystyle |V|^{2}}  ![{\displaystyle |V|^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3e2a7aad37527c097101c39b0b7724fe4e1cafb1)), Dijkstra tends to dominate.

 

For sparse graphs with negative edges but no negative cycles, [Johnson's algorithm](./Johnson's_algorithm) can be used, with the same asymptotic running time as the repeated Dijkstra approach.

 

There are also known algorithms using [fast matrix multiplication](./Fast_matrix_multiplication) to speed up all-pairs shortest path computation in dense graphs, but these typically make extra assumptions on the edge weights (such as requiring them to be small integers).[[17]](./Floyd–Warshall_algorithm#cite_note-17)[[18]](./Floyd–Warshall_algorithm#cite_note-18) In addition, because of the high constant factors in their running time, they would only provide a speedup over the Floyd–Warshall algorithm for very large graphs.

 

## References

  
1. [1](./Floyd–Warshall_algorithm#cite_ref-:0_1-0) [2](./Floyd–Warshall_algorithm#cite_ref-:0_1-1) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest) (1990). [*Introduction to Algorithms*](./Introduction_to_Algorithms) (1st ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03141-8](./Special:BookSources/0-262-03141-8). See in particular Section 26.2, "The Floyd–Warshall algorithm", pp. 558–565 and Section 26.4, "A general framework for solving path problems in directed graphs", pp. 570–576.
2. [↑](./Floyd–Warshall_algorithm#cite_ref-2) Kenneth H. Rosen (2003). *Discrete Mathematics and Its Applications, 5th Edition*. Addison Wesley. [ISBN](./ISBN_(identifier)) [978-0-07-119881-3](./Special:BookSources/978-0-07-119881-3).
3. [↑](./Floyd–Warshall_algorithm#cite_ref-3) [Floyd, Robert W.](./Robert_W._Floyd) (June 1962). ["Algorithm 97: Shortest Path"](https://doi.org/10.1145%2F367766.368168). *[Communications of the ACM](./Communications_of_the_ACM)*. **5** (6): 345. [doi](./Doi_(identifier)):[10.1145/367766.368168](https://doi.org/10.1145%2F367766.368168). [S2CID](./S2CID_(identifier)) [2003382](https://api.semanticscholar.org/CorpusID:2003382).
4. [↑](./Floyd–Warshall_algorithm#cite_ref-4) [Roy, Bernard](./Bernard_Roy) (1959). ["Transitivité et connexité"](https://gallica.bnf.fr/ark:/12148/bpt6k3201c/f222.image). *[C. R. Acad. Sci. Paris](./C._R._Acad._Sci._Paris)* (in French). **249**: 216–218. 
5. [↑](./Floyd–Warshall_algorithm#cite_ref-5) Warshall, Stephen (January 1962). ["A theorem on Boolean matrices"](https://doi.org/10.1145%2F321105.321107). *[Journal of the ACM](./Journal_of_the_ACM)*. **9** (1): 11–12. [doi](./Doi_(identifier)):[10.1145/321105.321107](https://doi.org/10.1145%2F321105.321107). [S2CID](./S2CID_(identifier)) [33763989](https://api.semanticscholar.org/CorpusID:33763989).
6. [↑](./Floyd–Warshall_algorithm#cite_ref-6) [Weisstein, Eric W.](./Eric_W._Weisstein) ["Floyd-Warshall Algorithm"](https://mathworld.wolfram.com/Floyd-WarshallAlgorithm.html). *[MathWorld](./MathWorld)*.
7. [↑](./Floyd–Warshall_algorithm#cite_ref-7) [Kleene, S. C.](./Stephen_Cole_Kleene) (1956). "Representation of events in nerve nets and finite automata". In [C. E. Shannon](./Claude_Elwood_Shannon) and [J. McCarthy](./John_McCarthy_(computer_scientist)) (ed.). *Automata Studies*. Princeton University Press. pp. 3–42.
8. [↑](./Floyd–Warshall_algorithm#cite_ref-8) Ingerman, Peter Z. (November 1962). ["Algorithm 141: Path Matrix"](https://doi.org/10.1145%2F368996.369016). *[Communications of the ACM](./Communications_of_the_ACM)*. **5** (11): 556. [doi](./Doi_(identifier)):[10.1145/368996.369016](https://doi.org/10.1145%2F368996.369016). [S2CID](./S2CID_(identifier)) [29010500](https://api.semanticscholar.org/CorpusID:29010500).
9. [1](./Floyd–Warshall_algorithm#cite_ref-:1_9-0) [2](./Floyd–Warshall_algorithm#cite_ref-:1_9-1) [3](./Floyd–Warshall_algorithm#cite_ref-:1_9-2) [Hochbaum, Dorit](./Dorit_S._Hochbaum) (2014). ["Section 8.9: Floyd-Warshall algorithm for all pairs shortest paths"](http://www.ieor.berkeley.edu/~hochbaum/files/ieor266-2014.pdf) (PDF). *Lecture Notes for IEOR 266: Graph Algorithms and Network Flows*. Department of Industrial Engineering and Operations Research, [University of California, Berkeley](./University_of_California,_Berkeley). pp. 41–42.
10. [↑](./Floyd–Warshall_algorithm#cite_ref-10) Hide, Ikumi (2019). "Incorrect implementations of the Floyd--Warshall algorithm give correct solutions after three repeats". [arXiv](./ArXiv_(identifier)):[1904.01210](https://arxiv.org/abs/1904.01210) [[cs.DS](https://arxiv.org/archive/cs.DS)].
11. [↑](./Floyd–Warshall_algorithm#cite_ref-11)  Stefan Hougardy (April 2010). "The Floyd–Warshall algorithm on graphs with negative cycles". *Information Processing Letters*. **110** (8–9): 279–281. [doi](./Doi_(identifier)):[10.1016/j.ipl.2010.02.001](https://doi.org/10.1016%2Fj.ipl.2010.02.001).
12. [↑](./Floyd–Warshall_algorithm#cite_ref-12) ["Free Algorithms Book"](https://books.goalkicker.com/AlgorithmsBook/).
13. [↑](./Floyd–Warshall_algorithm#cite_ref-13) Baras, John; Theodorakopoulos, George (2022). *Path Problems in Networks*. Springer International Publishing. [ISBN](./ISBN_(identifier)) [9783031799839](./Special:BookSources/9783031799839).
14. [↑](./Floyd–Warshall_algorithm#cite_ref-14) Gross, Jonathan L.; Yellen, Jay (2003). [*Handbook of Graph Theory*](https://books.google.com/books?id=mKkIGIea_BkC&pg=PA65). Discrete Mathematics and Its Applications. CRC Press. p. 65. [ISBN](./ISBN_(identifier)) [9780203490204](./Special:BookSources/9780203490204)..
15. [↑](./Floyd–Warshall_algorithm#cite_ref-15) Peñaloza, Rafael. ["Algebraic Structures for Transitive Closure"](https://web.archive.org/web/20091022202353/http://geocities.com/rpenalozan/ps/graphalg2005.ps). *Seminar "Graph Algorithms"*. Dresden University of Technology, Department of Computer Science, Institute for Theoretical Computer Science. Archived from [the original](http://geocities.com/rpenalozan/ps/graphalg2005.ps) on 2009-10-22.
16. [↑](./Floyd–Warshall_algorithm#cite_ref-16) Gillies, Donald (1993). [Scheduling Tasks with AND/OR precedence contraints (PhD Thesis, Appendix B)](http://www.ece.ubc.ca/~gillies/download/Donald_W_Gillies_PhD_1993_Scheduling_With_AND_OR_Precedence.pdf) (PDF) (Report).
17. [↑](./Floyd–Warshall_algorithm#cite_ref-17) [Zwick, Uri](./Uri_Zwick) (May 2002). "All pairs shortest paths using bridging sets and rectangular matrix multiplication". *[Journal of the ACM](./Journal_of_the_ACM)*. **49** (3): 289–317. [arXiv](./ArXiv_(identifier)):[cs/0008011](https://arxiv.org/abs/cs/0008011). [doi](./Doi_(identifier)):[10.1145/567112.567114](https://doi.org/10.1145%2F567112.567114). [S2CID](./S2CID_(identifier)) [1065901](https://api.semanticscholar.org/CorpusID:1065901)..
18. [↑](./Floyd–Warshall_algorithm#cite_ref-18) [Chan, Timothy M.](./Timothy_M._Chan) (January 2010). "More algorithms for all-pairs shortest paths in weighted graphs". *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **39** (5): 2075–2089. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.153.6864](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.153.6864). [doi](./Doi_(identifier)):[10.1137/08071990x](https://doi.org/10.1137%2F08071990x)..

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Floyd-Warshall algorithm](https://commons.wikimedia.org/wiki/Category:Floyd-Warshall%20algorithm).  
- [Interactive animation of the Floyd–Warshall algorithm](http://www.pms.informatik.uni-muenchen.de/lehre/compgeometry/Gosper/shortest_path/shortest_path.html#visualization)
- [Interactive animation of the Floyd–Warshall algorithm (Technical University of Munich)](https://algorithms.discrete.ma.tum.de/graph-algorithms/spp-floyd-warshall/index_en.html)

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |

 
| vteOptimization:Algorithms,methods, andheuristics |
| --- |
| Unconstrained nonlinearFunctionsGolden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolationGradientsConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated NewtonHessiansNewton's method | Unconstrained nonlinear | FunctionsGolden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolationGradientsConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated NewtonHessiansNewton's method | Functions | Golden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolation | Gradients | ConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton | Convergence | Trust regionWolfe conditions | Quasi–Newton | Berndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1) | Other methods | Conjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton | Hessians | Newton's method | Optimization computes maxima and minima. |
| Unconstrained nonlinear |
| FunctionsGolden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolationGradientsConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated NewtonHessiansNewton's method | Functions | Golden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolation | Gradients | ConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton | Convergence | Trust regionWolfe conditions | Quasi–Newton | Berndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1) | Other methods | Conjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton | Hessians | Newton's method |
| Functions | Golden-section searchPowell's methodLine searchNelder–Mead methodSuccessive parabolic interpolation |
| Gradients | ConvergenceTrust regionWolfe conditionsQuasi–NewtonBerndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1)Other methodsConjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton | Convergence | Trust regionWolfe conditions | Quasi–Newton | Berndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1) | Other methods | Conjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton |
| Convergence | Trust regionWolfe conditions |
| Quasi–Newton | Berndt–Hall–Hall–HausmanBroyden–Fletcher–Goldfarb–ShannoandL-BFGSDavidon–Fletcher–PowellSymmetric rank-one (SR1) |
| Other methods | Conjugate gradientGauss–NewtonGradientMirrorLevenberg–MarquardtPowell's dog leg methodTruncated Newton |
| Hessians | Newton's method |
| Constrained nonlinearGeneralBarrier methodsPenalty methodsDifferentiableAugmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming | Constrained nonlinear | GeneralBarrier methodsPenalty methodsDifferentiableAugmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming | General | Barrier methodsPenalty methods | Differentiable | Augmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming |
| Constrained nonlinear |
| GeneralBarrier methodsPenalty methodsDifferentiableAugmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming | General | Barrier methodsPenalty methods | Differentiable | Augmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming |
| General | Barrier methodsPenalty methods |
| Differentiable | Augmented Lagrangian methodsSequential quadratic programmingSuccessive linear programming |
| Convex optimizationConvexminimizationCutting-plane methodReduced gradient (Frank–Wolfe)Subgradient methodLinearandquadraticInterior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Convex optimization | ConvexminimizationCutting-plane methodReduced gradient (Frank–Wolfe)Subgradient methodLinearandquadraticInterior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Convexminimization | Cutting-plane methodReduced gradient (Frank–Wolfe)Subgradient method | Linearandquadratic | Interior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Interior point | Affine scalingEllipsoid algorithm of KhachiyanProjective algorithm of Karmarkar | Basis-exchange | Simplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method |
| Convex optimization |
| ConvexminimizationCutting-plane methodReduced gradient (Frank–Wolfe)Subgradient methodLinearandquadraticInterior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Convexminimization | Cutting-plane methodReduced gradient (Frank–Wolfe)Subgradient method | Linearandquadratic | Interior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Interior point | Affine scalingEllipsoid algorithm of KhachiyanProjective algorithm of Karmarkar | Basis-exchange | Simplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method |
| Convexminimization | Cutting-plane methodReduced gradient (Frank–Wolfe)Subgradient method |
| Linearandquadratic | Interior pointAffine scalingEllipsoid algorithm of KhachiyanProjective algorithm of KarmarkarBasis-exchangeSimplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method | Interior point | Affine scalingEllipsoid algorithm of KhachiyanProjective algorithm of Karmarkar | Basis-exchange | Simplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method |
| Interior point | Affine scalingEllipsoid algorithm of KhachiyanProjective algorithm of Karmarkar |
| Basis-exchange | Simplex algorithm of DantzigRevised simplex algorithmCriss-cross algorithmPrincipal pivoting algorithm of LemkeActive-set method |
| CombinatorialParadigmsApproximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cutGraphalgorithmsMinimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–WarshallNetwork flowsDinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow | Combinatorial | ParadigmsApproximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cutGraphalgorithmsMinimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–WarshallNetwork flowsDinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow | Paradigms | Approximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cut | Graphalgorithms | Minimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–Warshall | Minimumspanning tree | BorůvkaPrimKruskal | Shortest path | Bellman–FordSPFADijkstraFloyd–Warshall | Network flows | DinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow |
| Combinatorial |
| ParadigmsApproximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cutGraphalgorithmsMinimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–WarshallNetwork flowsDinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow | Paradigms | Approximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cut | Graphalgorithms | Minimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–Warshall | Minimumspanning tree | BorůvkaPrimKruskal | Shortest path | Bellman–FordSPFADijkstraFloyd–Warshall | Network flows | DinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow |
| Paradigms | Approximation algorithmDynamic programmingGreedy algorithmInteger programmingBranch and bound/cut |
| Graphalgorithms | Minimumspanning treeBorůvkaPrimKruskalShortest pathBellman–FordSPFADijkstraFloyd–Warshall | Minimumspanning tree | BorůvkaPrimKruskal | Shortest path | Bellman–FordSPFADijkstraFloyd–Warshall |
| Minimumspanning tree | BorůvkaPrimKruskal |
| Shortest path | Bellman–FordSPFADijkstraFloyd–Warshall |
| Network flows | DinicEdmonds–KarpFord–FulkersonPush–relabel maximum flow |
| MetaheuristicsEvolutionary algorithmHill climbingLocal searchParallel metaheuristicsSimulated annealingSpiral optimization algorithmTabu search | Metaheuristics | Evolutionary algorithmHill climbingLocal searchParallel metaheuristicsSimulated annealingSpiral optimization algorithmTabu search |
| Metaheuristics |
| Evolutionary algorithmHill climbingLocal searchParallel metaheuristicsSimulated annealingSpiral optimization algorithmTabu search |
| Software |