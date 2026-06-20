---
source: https://en.wikipedia.org/wiki/Topological_sorting
fetched: 2026-06-19
---

Node ordering for directed acyclic graphs "Dependency resolution" redirects here. For other uses, see [Dependency (disambiguation)](./Dependency_(disambiguation)). 

In [computer science](./Computer_science), a **topological sort** or **topological ordering** of a [directed graph](./Directed_graph) is a [linear ordering](./Total_order) of its [vertices](./Vertex_(graph_theory)) such that for every directed edge *(u,v)* from vertex *u* to vertex *v*, *u* comes before *v* in the ordering. For instance, the vertices of the graph may represent tasks to be performed, and the edges may represent constraints that one task must be performed before another; in this application, a topological ordering is just a valid sequence for the tasks. 

 

Precisely, a topological sort is a graph traversal in which each node *v* is visited only after all its dependencies are visited*.* A topological ordering is possible if and only if the graph has no [directed cycles](./Directed_cycle), that is, if it is a [directed acyclic graph](./Directed_acyclic_graph) (DAG). Any DAG has at least one topological ordering, and there are  [linear time](./Linear_time) [algorithms](./Algorithm) for constructing it. Topological sorting has many applications, especially in ranking problems such as [feedback arc set](./Feedback_arc_set). Topological sorting is also possible when the DAG has [disconnected components](./Connectivity_(graph_theory)).

 

## Examples

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/03/Directed_acyclic_graph_2.svg/500px-Directed_acyclic_graph_2.svg.png)](./File:Directed_acyclic_graph_2.svg)This graph has many valid topological sorts, including:

- 5, 7, 3, 11, 8, 2, 9, 10 (visual left-to-right, top-to-bottom)
- 3, 5, 7, 8, 11, 2, 9, 10 (smallest-numbered available vertex first)
- 3, 5, 7, 8, 11, 2, 10, 9 ([lexicographic by incoming neighbors](./Coffman–Graham_algorithm))
- 5, 7, 3, 8, 11, 2, 10, 9 (fewest edges first)
- 7, 5, 11, 3, 10, 8, 9, 2 (largest-numbered available vertex first)
- 5, 7, 11, 2, 3, 8, 9, 10 (attempting top-to-bottom, left-to-right)
- 3, 7, 8, 5, 11, 10, 2, 9 (arbitrary)

 

The canonical application of topological sorting is in [scheduling](./Job_shop_scheduling) a sequence of jobs or tasks based on their [dependencies](./Dependency_graph). The jobs are represented by vertices, and there is an edge from *x* to *y* if job *x* must be completed before job *y* can be started (for example, when washing clothes, the washing machine must finish before we put the clothes in the dryer). Then, a topological sort gives an order in which to perform the jobs.  A closely related application of topological sorting algorithms was first studied in the early 1960s in the context of the [PERT](./Program_Evaluation_and_Review_Technique) technique for scheduling in [project management](./Project_management).[[1]](./Topological_sorting#cite_note-Jarnagin-1) In this application, the vertices of a graph represent the milestones of a project, and the edges represent tasks that must be performed between one milestone and another. Topological sorting forms the basis of linear-time algorithms for finding the [critical path](./Critical_path_method) of the project, a sequence of milestones and tasks that controls the length of the overall project schedule.

 

In computer science, applications of this type arise in [instruction scheduling](./Instruction_scheduling), ordering of formula cell evaluation when recomputing formula values in [spreadsheets](./Spreadsheet), [logic synthesis](./Logic_synthesis), determining the order of compilation tasks to perform in [makefiles](./Makefile), data [serialization](./Serialization), and resolving symbol dependencies in [linkers](./Linker_(computing)). It is also used to decide in which order to load tables with foreign keys in databases.

 

## Algorithms

 

The usual algorithms for topological sorting have running time linear in the number of nodes plus the number of edges, asymptotically,     O (  |  V  |  +  |  E  |  ) .   {\displaystyle O(\left|{V}\right|+\left|{E}\right|).}  ![{\displaystyle O(\left|{V}\right|+\left|{E}\right|).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f40de423f10d77a2da65bcc82f0f94944de04ef1)

 

### Kahn's algorithm

 Not to be confused with [Kuhn's algorithm](./Kuhn's_algorithm). 

One of these algorithms, first described by [Kahn (1962)](./Topological_sorting#CITEREFKahn1962), works by choosing vertices in the same order as the eventual topological sort.[[2]](./Topological_sorting#cite_note-Kahn-2) First, find a list of "start nodes" that have no incoming edges and insert them into a set S; at least one such node must exist in a non-empty (finite) acyclic graph. Then:

 
```
L ← Empty list that will contain the sorted elements
S ← Set of all nodes with no incoming edge

while S is not empty do
    remove a node n from S
    add n to L
    for each node m with an edge e from n to m do
        remove edge e from the graph
        if m has no other incoming edges then
            insert m into S

if graph has edges then
    return error   (graph has at least one cycle)
else 
    return L   (a topologically sorted order)
```
 

If the graph is a [DAG](./Directed_acyclic_graph), a solution will be contained in the list L (although the solution is not necessarily unique). Otherwise, the graph must have at least one cycle and therefore a topological sort is impossible.

 

Reflecting the non-uniqueness of the resulting sort, the structure S can be simply a set or a queue or a stack. Depending on the order that nodes n are removed from set S, a different solution is created. A variation of Kahn's algorithm that breaks ties [lexicographically](./Lexicographic_order) forms a key component of the [Coffman–Graham algorithm](./Coffman–Graham_algorithm) for parallel scheduling and [layered graph drawing](./Layered_graph_drawing).

 

### Depth-first search

 

An alternative algorithm for topological sorting is based on [depth-first search](./Depth-first_search). The algorithm loops through each node of the graph, in an arbitrary order, initiating a depth-first search that terminates when it hits any node that has already been visited since the beginning of the topological sort or the node has no outgoing edges (i.e., a leaf node):

 
```
L ← Empty list that will contain the sorted nodes
while exists nodes without a permanent mark do
    select an unmarked node n
    visit(n)

function visit(node n)
    if n has a permanent mark then
        return
    if n has a temporary mark then
        stop   (graph has at least one cycle)

    mark n with a temporary mark

    for each node m with an edge from n to m do
        visit(m)

    mark n with a permanent mark
    add n to head of L
```
 

Each node *n* gets *prepended* to the output list L only after considering all other nodes that depend on *n* (all descendants of *n* in the graph).  Specifically, when the algorithm adds node *n*, we are guaranteed that all nodes that depend on *n* are already in the output list L: they were added to L either by the recursive call to visit() that ended before the call to visit *n*, or by a call to visit() that started even before the call to visit *n*.  Since each edge and node is visited once, the algorithm runs in linear time. This depth-first-search-based algorithm is the one described by [Cormen et al. (2001)](./Topological_sorting#CITEREFCormenLeisersonRivestStein2001);[[3]](./Topological_sorting#cite_note-CLRS-3) it seems to have been first described in print by Tarjan in 1976.[[4]](./Topological_sorting#cite_note-Tarjan-4)

 

### Parallel algorithms

 

On a [parallel random-access machine](./Parallel_random-access_machine), a topological ordering can be constructed in *O*((log *n*)2) time using a polynomial number of processors, putting the problem into the complexity class **[NC](./NC_(complexity))2**.[[5]](./Topological_sorting#cite_note-Cook-5)
One method for doing this is to repeatedly square the [adjacency matrix](./Adjacency_matrix) of the given graph, logarithmically many times, using [min-plus matrix multiplication](./Min-plus_matrix_multiplication) with maximization in place of minimization. The resulting matrix describes the [longest path](./Longest_path_problem) distances in the graph. Sorting the vertices by the lengths of their longest incoming paths produces a topological ordering.[[6]](./Topological_sorting#cite_note-DNS-6)

 

An algorithm for parallel topological sorting on [distributed memory](./Distributed_memory) machines parallelizes the algorithm of Kahn for a [DAG](./Directed_acyclic_graph)     G = ( V , E )   {\displaystyle G=(V,E)}  ![{\displaystyle G=(V,E)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/644a8d85ee410b6159ca2bdb5dcb9097e2c8f182).[[7]](./Topological_sorting#cite_note-SMDD-7) On a high level, the algorithm of Kahn repeatedly removes the vertices of indegree 0 and adds them to the topological sorting in the order in which they were removed. Since the outgoing edges of the removed vertices are also removed, there will be a new set of vertices of indegree 0, where the procedure is repeated until no vertices are left. This algorithm performs     D + 1   {\displaystyle D+1}  ![{\displaystyle D+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6a2a5ae5a26d2595babc37427927b0cf26f9235f) iterations, where D is the longest path in G. Each iteration can be parallelized, which is the idea of the following algorithm.

 

In the following, it is assumed that the graph partition is stored on p processing elements (PE), which are labeled     0 , … …  , p − −  1   {\displaystyle 0,\dots ,p-1}  ![{\displaystyle 0,\dots ,p-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/350871b5980d758f5a36ecc7b1dba63c20724f0d). Each PE i initializes a set of local vertices      Q  i   1     {\displaystyle Q_{i}^{1}}  ![{\displaystyle Q_{i}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c3ac9c76e43c749c88818ace54d0ce79c4ebc23) with [indegree](./Indegree) 0, where the upper index represents the current iteration. Since all vertices in the local sets      Q  0   1   , … …  ,  Q  p − −  1   1     {\displaystyle Q_{0}^{1},\dots ,Q_{p-1}^{1}}  ![{\displaystyle Q_{0}^{1},\dots ,Q_{p-1}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a13fb14f805a8fe8b5f2f6b929539fdb6f4bbe5) have indegree 0, i.e., they are not adjacent, they can be given in an arbitrary order for a valid topological sorting. To assign a global index to each vertex, a [prefix sum](./Prefix_sum) is calculated over the sizes of      Q  0   1   , … …  ,  Q  p − −  1   1     {\displaystyle Q_{0}^{1},\dots ,Q_{p-1}^{1}}  ![{\displaystyle Q_{0}^{1},\dots ,Q_{p-1}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a13fb14f805a8fe8b5f2f6b929539fdb6f4bbe5). So, each step, there are      ∑ ∑   i = 0   p − −  1    |   Q  i    |    {\textstyle \sum _{i=0}^{p-1}|Q_{i}|}  ![{\textstyle \sum _{i=0}^{p-1}|Q_{i}|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c47c838aa5d281e4ff2c5854e976a0399801eb4b) vertices added to the topological sorting.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Parallel_Topological_Sorting.gif/500px-Parallel_Topological_Sorting.gif)](./File:Parallel_Topological_Sorting.gif)Execution of the parallel topological sorting algorithm on a DAG with two processing elements. 

In the first step, PE j assigns the indices      ∑ ∑   i = 0   j − −  1    |   Q  i   1    |  , … …  ,  (   ∑ ∑   i = 0   j    |   Q  i   1    |   )  − −  1   {\textstyle \sum _{i=0}^{j-1}|Q_{i}^{1}|,\dots ,\left(\sum _{i=0}^{j}|Q_{i}^{1}|\right)-1}  ![{\textstyle \sum _{i=0}^{j-1}|Q_{i}^{1}|,\dots ,\left(\sum _{i=0}^{j}|Q_{i}^{1}|\right)-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63a79a820bd39172be3a325720109ef7c6cefd12) to the local vertices in      Q  j   1     {\displaystyle Q_{j}^{1}}  ![{\displaystyle Q_{j}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a6910292344848e4f98b55de54dfc6ef3b5bc95). These vertices in      Q  j   1     {\displaystyle Q_{j}^{1}}  ![{\displaystyle Q_{j}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a6910292344848e4f98b55de54dfc6ef3b5bc95) are removed, together with their corresponding outgoing edges. For each outgoing edge     ( u , v )   {\displaystyle (u,v)}  ![{\displaystyle (u,v)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eadf12294edccd7a29c99cfc1765e4a14bf47e58) with endpoint v in another PE     l , j ≠ ≠  l   {\displaystyle l,j\neq l}  ![{\displaystyle l,j\neq l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e7191b8105913470a4a1ae3748fe3375d2e79453), the message     ( u , v )   {\displaystyle (u,v)}  ![{\displaystyle (u,v)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eadf12294edccd7a29c99cfc1765e4a14bf47e58) is posted to PE l. After all vertices in      Q  j   1     {\displaystyle Q_{j}^{1}}  ![{\displaystyle Q_{j}^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a6910292344848e4f98b55de54dfc6ef3b5bc95) are removed, the posted messages are sent to their corresponding PE. Each message     ( u , v )   {\displaystyle (u,v)}  ![{\displaystyle (u,v)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eadf12294edccd7a29c99cfc1765e4a14bf47e58) received updates the indegree of the local vertex v. If the indegree drops to zero, v is added to      Q  j   2     {\displaystyle Q_{j}^{2}}  ![{\displaystyle Q_{j}^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a193d4505b0f293d868e551e9bf2cf2184bf96a4). Then the next iteration starts.

 

In step k, PE j assigns the indices      a  k − −  1   +  ∑ ∑   i = 0   j − −  1    |   Q  i   k    |  , … …  ,  a  k − −  1   +  (   ∑ ∑   i = 0   j    |   Q  i   k    |   )  − −  1   {\textstyle a_{k-1}+\sum _{i=0}^{j-1}|Q_{i}^{k}|,\dots ,a_{k-1}+\left(\sum _{i=0}^{j}|Q_{i}^{k}|\right)-1}  ![{\textstyle a_{k-1}+\sum _{i=0}^{j-1}|Q_{i}^{k}|,\dots ,a_{k-1}+\left(\sum _{i=0}^{j}|Q_{i}^{k}|\right)-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dbbd5c704c1c882ef0b21b8b89c7658a38dc530), where       a  k − −  1     {\displaystyle a_{k-1}}  ![{\displaystyle a_{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b56e9e10d3cbe93addd3eba751f36913155ad33) is the total number of processed vertices after step ⁠    k − −  1   {\displaystyle k-1}  ![{\displaystyle k-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/21363ebd7038c93aae93127e7d910fc1b2e2c745)⁠. This procedure repeats until there are no vertices left to process, hence      ∑ ∑   i = 0   p − −  1    |   Q  i   D + 1    |  = 0   {\textstyle \sum _{i=0}^{p-1}|Q_{i}^{D+1}|=0}  ![{\textstyle \sum _{i=0}^{p-1}|Q_{i}^{D+1}|=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8e1be13101642fb1389aa0849c4730686c619aa3). Below is a high level, [single program, multiple data](./SPMD) pseudo-code overview of this algorithm.

 

Note that the [prefix sum](./Prefix_sum#Parallel_algorithms) for the local offsets      a  k − −  1   +  ∑ ∑   i = 0   j − −  1    |   Q  i   k    |  , … …  ,  a  k − −  1   +  (   ∑ ∑   i = 0   j    |   Q  i   k    |   )  − −  1   {\textstyle a_{k-1}+\sum _{i=0}^{j-1}|Q_{i}^{k}|,\dots ,a_{k-1}+\left(\sum _{i=0}^{j}|Q_{i}^{k}|\right)-1}  ![{\textstyle a_{k-1}+\sum _{i=0}^{j-1}|Q_{i}^{k}|,\dots ,a_{k-1}+\left(\sum _{i=0}^{j}|Q_{i}^{k}|\right)-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dbbd5c704c1c882ef0b21b8b89c7658a38dc530) can be efficiently calculated in parallel.

 
```
p processing elements with IDs from 0 to p-1
Input: G = (V, E) DAG, distributed to PEs, PE index j = 0, ..., p - 1
Output: topological sorting of G

function traverseDAGDistributed
    δ incoming degree of local vertices V
    Q = {v ∈ V | δ[v] = 0}                     // All vertices with indegree 0
    nrOfVerticesProcessed = 0

    do
        global build prefix sum over size of Q     // get offsets and total number of vertices in this step
        offset = nrOfVerticesProcessed + sum(Qi, i = 0 to j - 1)          // j is the processor index
        foreach u in Q
            localOrder[u] = index++;
            foreach (u,v) in E do post message (u, v) to PE owning vertex v
        nrOfVerticesProcessed += sum(|Qi|, i = 0 to p - 1)
        deliver all messages to neighbors of vertices in Q
        receive messages for local vertices V
        remove all vertices in Q
        foreach message (u, v) received:
            if --δ[v] = 0
                add v to Q
    while global size of Q > 0

    return localOrder
```
 

The communication cost depends heavily on the given graph partition. As for runtime, on a [CRCW-PRAM](./CRCW_PRAM) model that allows fetch-and-decrement in constant time, this algorithm runs in       O    (     m + n  p   + D ( Δ Δ  + log ⁡ ⁡  n )  )    {\textstyle {\mathcal {O}}\left({\frac {m+n}{p}}+D(\Delta +\log n)\right)}  ![{\textstyle {\mathcal {O}}\left({\frac {m+n}{p}}+D(\Delta +\log n)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c633a9209ad4683fe90e9431cd56ac33dd62236), where D is again the longest path in G and Δ the maximum degree.[[7]](./Topological_sorting#cite_note-SMDD-7)

 

## Application to shortest path finding

 

The topological ordering can also be used to quickly compute [shortest paths](./Shortest_path_problem) through a [weighted](./Weighted_graph) directed acyclic graph. Let V be the list of vertices in such a graph, in topological order. Then the following algorithm computes the shortest path from some source vertex s to all other vertices:[[3]](./Topological_sorting#cite_note-CLRS-3)

    
- Let d be an array of the same length as V; this will hold the shortest-path distances from s. Set *d*[*s*] = 0, all other *d*[*u*] = ∞.
- Let p be an array of the same length as V, with all elements initialized to nil. Each *p*[*u*] will hold the predecessor of *u* in the shortest path from s to u.
- Loop over the vertices u as ordered in V, starting from s:

- For each vertex v directly following u (i.e., there exists an edge from u to v):

- Let w be the weight of the edge from u to v.
- Relax the edge: if *d*[*v*] > *d*[*u*] + *w*, set

- *d*[*v*] ← *d*[*u*] + *w*,
- *p*[*v*] ← *u*.

  

Equivalently:

    
- Let d be an array of the same length as V; this will hold the shortest-path distances from s. Set *d*[*s*] = 0, all other *d*[*u*] = ∞.
- Let p be an array of the same length as V, with all elements initialized to nil. Each *p*[*u*] will hold the predecessor of u in the shortest path from s to u.
- Loop over the vertices u as ordered in V, starting from s:

- For each vertex v into u (i.e., there exists an edge from v to u):

- Let w be the weight of the edge from v to u.
- Relax the edge: if *d*[*u*] > *d*[*v*] + *w*, set

- *d*[*u*] ← *d*[*v*] + *w*,
- *p*[*u*] ← *v*.

  

On a graph of n vertices and m edges, this algorithm takes Θ(*n* + *m*), i.e., [linear](./Linear_time), time.[[3]](./Topological_sorting#cite_note-CLRS-3)

 

## Uniqueness

 

If a topological sort has the property that all pairs of consecutive vertices in the sorted order are connected by edges, then these edges form a directed [Hamiltonian path](./Hamiltonian_path) in the [DAG](./Directed_acyclic_graph). If a Hamiltonian path exists, the topological sort order is unique; no other order respects the edges of the path. Conversely, if a topological sort does not form a Hamiltonian path, the DAG will have two or more valid topological orderings, for in this case it is always possible to form a second valid ordering by swapping two consecutive vertices that are not connected by an edge to each other. Therefore, it is possible to test in linear time whether a unique ordering exists, and whether a Hamiltonian path exists, despite the [NP-hardness](./NP-hard) of the Hamiltonian path problem for more general directed graphs (i.e., cyclic directed graphs).[[8]](./Topological_sorting#cite_note-VM-8)

 

## Relation to partial orders

 

Topological orderings are also closely related to the concept of a [linear extension](./Linear_extension) of a [partial order](./Partial_order) in mathematics. A partially ordered set is just a set of objects together with a definition of the "≤" inequality relation, satisfying the axioms of reflexivity (*x* ≤ *x*), antisymmetry (if *x* ≤ *y* and *y* ≤ *x* then *x* = *y*) and [transitivity](./Transitive_relation) (if *x* ≤ *y* and *y* ≤ *z*, then *x* ≤ *z*). A [total order](./Total_order) is a partial order in which, for every two objects *x* and *y* in the set, either *x* ≤ *y* or *y* ≤ *x*. Total orders are familiar in computer science as the comparison operators needed to perform [comparison sorting](./Comparison_sort) algorithms. For finite sets, total orders may be identified with linear sequences of objects, where the "≤" relation is true whenever the first object precedes the second object in the order; a comparison sorting algorithm may be used to convert a total order into a sequence in this way. A linear extension of a partial order is a total order that is compatible with it, in the sense that, if *x* ≤ *y* in the partial order, then  *x* ≤ *y* in the total order as well.

 

One can define a partial ordering from any DAG by letting the set of objects be the vertices of the DAG, and defining *x* ≤ *y* to be true, for any two vertices *x* and *y*, whenever there exists a [directed path](./Directed_path) from *x* to *y*; that is,  whenever *y* is [reachable](./Reachability) from *x*. With these definitions, a topological ordering of the DAG is the same thing as a linear extension of this partial order. Conversely, any partial ordering may be defined as the reachability relation in a DAG. One way of doing this is to define a DAG that has a vertex for every object in the partially ordered set, and an edge *xy* for every pair of objects for which *x* ≤ *y*. An alternative way of doing this is to use the [transitive reduction](./Transitive_reduction) of the partial ordering; in general, this produces DAGs with fewer edges, but the reachability relation in these DAGs is still the same partial order. By using these constructions, one can use topological ordering algorithms to find linear extensions of partial orders.

 

## Relation to scheduling optimisation

 

By definition, the solution of a scheduling problem that includes a precedence graph is a valid solution to topological sort (irrespective of the number of machines), however, topological sort in itself is *not* enough to optimally solve a scheduling optimisation problem. Hu's algorithm is a popular method used to solve scheduling problems that require a precedence graph and involve processing times (where the goal is to minimise the largest completion time amongst all the jobs). Like topological sort, Hu's algorithm is not unique and can be solved using DFS (by finding the largest path length and then assigning the jobs). 

 

## See also

 
- [tsort](./Tsort), a Unix program for topological sorting
- [Feedback arc set](./Feedback_arc_set), a set of edges whose removal allows the remaining subgraph to be topologically sorted
- [Tarjan's strongly connected components algorithm](./Tarjan's_strongly_connected_components_algorithm), an algorithm that gives the topologically sorted list of strongly connected components in a graph
- [Pre-topological order](./Pre-topological_order)

 

## References

 
1. [↑](./Topological_sorting#cite_ref-Jarnagin_1-0) Jarnagin, M. P. (1960), *Automatic machine methods of testing PERT networks for consistency*, Technical Memorandum No. K-24/60, Dahlgren, Virginia: U. S. Naval Weapons Laboratory
2. [↑](./Topological_sorting#cite_ref-Kahn_2-0) Kahn, Arthur B. (1962), "Topological sorting of large networks", *Communications of the ACM*, **5** (11): 558–562, [doi](./Doi_(identifier)):[10.1145/368996.369025](https://doi.org/10.1145%2F368996.369025), [S2CID](./S2CID_(identifier)) [16728233](https://api.semanticscholar.org/CorpusID:16728233)
3. [1](./Topological_sorting#cite_ref-CLRS_3-0) [2](./Topological_sorting#cite_ref-CLRS_3-1) [3](./Topological_sorting#cite_ref-CLRS_3-2) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001), "Section 22.4: Topological sort", [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.), MIT Press and McGraw-Hill, pp. 549–552, [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7)
4. [↑](./Topological_sorting#cite_ref-Tarjan_4-0) [Tarjan, Robert E.](./Robert_Tarjan) (1976), "Edge-disjoint spanning trees and depth-first search", *Acta Informatica*, **6** (2): 171–185, [doi](./Doi_(identifier)):[10.1007/BF00268499](https://doi.org/10.1007%2FBF00268499), [S2CID](./S2CID_(identifier)) [12044793](https://api.semanticscholar.org/CorpusID:12044793)
5. [↑](./Topological_sorting#cite_ref-Cook_5-0) [Cook, Stephen A.](./Stephen_Cook) (1985), "A Taxonomy of Problems with Fast Parallel Algorithms", *Information and Control*, **64** (1–3): 2–22, [doi](./Doi_(identifier)):[10.1016/S0019-9958(85)80041-3](https://doi.org/10.1016%2FS0019-9958%2885%2980041-3)
6. [↑](./Topological_sorting#cite_ref-DNS_6-0) Dekel, Eliezer; Nassimi, David; Sahni, Sartaj (1981), "Parallel matrix and graph algorithms", *SIAM Journal on Computing*, **10** (4): 657–675, [doi](./Doi_(identifier)):[10.1137/0210049](https://doi.org/10.1137%2F0210049), [MR](./MR_(identifier)) [0635424](https://mathscinet.ams.org/mathscinet-getitem?mr=0635424)
7. [1](./Topological_sorting#cite_ref-SMDD_7-0) [2](./Topological_sorting#cite_ref-SMDD_7-1) Sanders, Peter; Mehlhorn, Kurt; Dietzfelbinger, Martin; Dementiev, Roman (2019), [*Sequential and Parallel Algorithms and Data Structures: The Basic Toolbox*](https://www.springer.com/gp/book/9783030252083), Springer International Publishing, [ISBN](./ISBN_(identifier)) [978-3-030-25208-3](./Special:BookSources/978-3-030-25208-3)
8. [↑](./Topological_sorting#cite_ref-VM_8-0) Vernet, Oswaldo; Markenzon, Lilian (1997), ["Hamiltonian problems for reducible flowgraphs"](http://pantheon.ufrj.br/bitstream/11422/2585/4/02_97_000575787.pdf) (PDF), *Proceedings: 17th International Conference of the Chilean Computer Science Society*, pp. 264–267, [doi](./Doi_(identifier)):[10.1109/SCCC.1997.637099](https://doi.org/10.1109%2FSCCC.1997.637099), [hdl](./Hdl_(identifier)):[11422/2585](https://hdl.handle.net/11422%2F2585), [ISBN](./ISBN_(identifier)) [0-8186-8052-0](./Special:BookSources/0-8186-8052-0), [S2CID](./S2CID_(identifier)) [206554481](https://api.semanticscholar.org/CorpusID:206554481)

 

## Further reading

 
- [D. E. Knuth](./D._E._Knuth), [The Art of Computer Programming](./The_Art_of_Computer_Programming), Volume 1, section 2.2.3, which gives an algorithm for topological sorting of a partial ordering, and a brief history.
- [Bertrand Meyer](./Bertrand_Meyer), *Touch of Class: Learning to Program Well with Objects and Contracts*, [Springer](./Springer_Science+Business_Media), 2009, chapter 15, *Devising and engineering an algorithm: topological sort*, using a modern programming language, for a detailed pedagogical presentation of topological sort (using a variant of Kahn's algorithm) with consideration of data structure design, API design, and software engineering concerns.

 

## External links

 
- [NIST Dictionary of Algorithms and Data Structures: topological sort](https://xlinux.nist.gov/dads/HTML/topologicalSort.html)
- [Weisstein, Eric W.](./Eric_W._Weisstein), ["Topological Sort"](https://mathworld.wolfram.com/TopologicalSort.html), *[MathWorld](./MathWorld)*

 
| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |

 
| vteSorting algorithms |
| --- |
| Theory | Computational complexity theoryBig O notationTotal orderListsInplacementStabilityComparison sortAdaptive sortSorting networkInteger sortingX + Y sortingTransdichotomous modelQuantum sort |
| Exchange sorts | Bubble sortCocktail shaker sortOdd–even sortComb sortGnome sortProportion extend sortQuicksort |
| Selection sorts | Selection sortHeapsortSmoothsortCartesian tree sortTournament sortCycle sortWeak-heap sort |
| Insertion sorts | Insertion sortShellsortSplaysortTree sortLibrary sortPatience sorting |
| Merge sorts | Merge sortCascade merge sortOscillating merge sortPolyphase merge sort |
| Distribution sorts | American flag sortBead sortBucket sortBurstsortCounting sortInterpolation sortPigeonhole sortProxmap sortRadix sortFlashsort |
| Concurrentsorts | Bitonic sorterBatcher odd–even mergesortPairwise sorting networkSamplesort |
| Hybrid sorts | Block merge sortIntrosortKirkpatrick–Reisch sortMerge-insertion sortPowersortTimsortSpreadsort |
| Other | Topological sortingPre-topological orderPancake sortingSpaghetti sort |
| Impractical sorts | Stooge sortSlowsortBogosort |