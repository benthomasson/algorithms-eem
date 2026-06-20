---
source: https://en.wikipedia.org/wiki/Greedy_algorithm
fetched: 2026-06-19
---

Sequence of locally optimal choices

A **greedy algorithm** is an [algorithm](./Algorithm) which, at each step, makes the choice that is locally optimal, and subsequently does not reconsider past choices. Greedy algorithms are often used to solve [combinatorial optimization](./Combinatorial_optimization) problems. If an optimization problem only depends on the partial solution of solving it for one subproblem, we can solve this problem by "greedily" considering only the locally optimal subproblem. In this sense, a greedy algorithm is a special case of a [dynamic programming](./Dynamic_programming) algorithm. [Uriel Feige](./Uriel_Feige)[[1]](./Greedy_algorithm#cite_note-:0-1) notes that: 

[Greedy algorithms] may be viewed as the ultimate form of dynamic programming, in which only one partial solution is maintained. The problem needs to have much more structure for this approach to work. 

In many cases, a greedy algorithm does not produce an exact solution, but can yield solutions that [approximate](./Approximation_algorithm) an exact solution in a reasonable amount of time.[[2]](./Greedy_algorithm#cite_note-2)

 

An example of a problem which admits an exact greedy solution, the [activity selection problem](./Activity_selection_problem). Given a collection of tasks which can be done between allotted time intervals, the problem is to determine the maximum number of tasks that can be done. A greedy algorithm in     O ( n log ⁡ ⁡  ( n ) )   {\displaystyle O(n\log(n))}  ![{\displaystyle O(n\log(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/85994022c28e938772bd858cd8281328643e8b3f) which solves this problem sorts the tasks by the end time and then repeatedly chooses the first task that begins after the last task ended.

 

Many classic algorithms in computer science such as the [Huffman coding algorithm](./Huffman_coding), [Prim's algorithm](./Prim's_algorithm), [Kruskal's algorithm](./Kruskal's_algorithm), and [Dijkstra's algorithm](./Dijkstra's_algorithm) all use greedy properties in their design. Mathematicians frequently use *greedy strategies* in proofs as well. A classic example is what [Raphael Yuster](./Raphael_Yuster) refers to as the greedy proof[[3]](./Greedy_algorithm#cite_note-3) that every [tournament](./Tournament_(graph_theory)) in graph contains a [Hamiltonian path](./Hamiltonian_path).

 

## Characterizations

 

Since there is no formal definition of what a greedy algorithm is,[[4]](./Greedy_algorithm#cite_note-4) a complete characterization of when a problem admits a greedy algorithm as a solution is not known. However, special cases have been identified. [Jack Edmonds](./Jack_Edmonds) showed that a greedy algorithm can be used to solve a class of linear combinatorial optimization problems with a [matroid structure.](./Matroid)[[5]](./Greedy_algorithm#cite_note-5)

 

Later [Bernhard Korte](./Bernhard_Korte) and [László Lovász](./László_Lovász) characterized a broader class of optimization problems by introducing the notion of a [greedoid](./Greedoid). This allowed, for example, a proof of the optimality of [Prim's algorithm](./Prim's_algorithm). 

 

Algorithms which undo past steps are not greedy. For example, the [Gale-Shapley](./Gale–Shapley_algorithm) algorithm is not a greedy algorithm since although it constructs a solution by choosing the current best pairing, in the process, existing solutions may be modified. 

 

## Correctness

 

One technique used to prove the optimiality of greedy algorithms is an exchange argument.[[6]](./Greedy_algorithm#cite_note-6) The exchange argument demonstrates that any solution different from the greedy solution is at most as good as the greedy solution. This proof pattern typically follows these steps:

 
1. Assume there exists an optimal solution different from the greedy solution
2. Consider the first point where the optimal and greedy solutions differ
3. Prove that exchanging the optimal choice for the greedy choice at this point cannot worsen the greedy solution
4. Conclude by induction that the greedy solution is optimal.

 Examples of how a greedy algorithm may fail to achieve the optimal solution[![](//upload.wikimedia.org/wikipedia/commons/thumb/0/06/Greedy_Glouton.svg/330px-Greedy_Glouton.svg.png)](./File:Greedy_Glouton.svg)Starting from A, a greedy algorithm that tries to find the maximum by following the greatest slope will find the local maximum at "m", oblivious to the global maximum at "M".[![](//upload.wikimedia.org/wikipedia/commons/8/8c/Greedy-search-path-example.gif)](./File:Greedy-search-path-example.gif)To reach the largest sum, at each step, the greedy algorithm will choose what appears to be the optimal immediate choice, so it will choose 12 instead of 3 at the second step, and will not reach the best solution, which contains 99. 

## Further examples

 
- In the [fractional knapsack problem](./Continuous_knapsack_problem), one is given a list of items with weights and values. The goal is to choose fractional amounts of each item such that the total value is maximised, and the weight is below a fixed constraint. Unlike the [knapsack problem](./Knapsack_problem), which is known to be [NP-hard](./NP-hardness), the fractional knapsack problem admits a polynomial time greedy algorithm.
- Instances of the [Frobenius coin problem](./Coin_problem) admit greedy solutions. However, in some cases the greedy algorithm does not yield an optimal solution.[[7]](./Greedy_algorithm#cite_note-7)
- The [matching pursuit](./Matching_pursuit) is an example of a greedy algorithm applied on signal approximation.
- A greedy algorithm finds the optimal solution to [Malfatti's problem](./Malfatti_circles) of finding three disjoint circles within a given triangle that maximize the total area of the circles; it is conjectured that the same greedy algorithm is optimal for any number of circles.
- In [decision tree learning](./Decision_tree_learning), greedy algorithms are commonly used, however they are not guaranteed to find the optimal solution.

- One popular such algorithm is the [ID3 algorithm](./ID3_algorithm) for decision tree construction.

- A greedy algorithm constructs the [Zeckendorf representation](./Zeckendorf's_theorem) (or Fibonacci coding) of a natural number. Subtracting the largest Fibonacci number less than or equal to the natural number repeatedly gives its Zecekndorf representation. The greedy algorithm is extracted from the existence proof of the Zeckendorf representation. The uniqueness of the Zeckendorf representation guarantees that no other non-consecutive Fibonacci sum can give a different output.
- [Fibonacci](./Fibonacci) described [an greedy algorithm for computing Egyptian fractions](./Greedy_algorithm_for_Egyptian_fractions).
- Greedy algorithms appear in network [routing](./Routing). Using greedy routing, a message is forwarded to the neighbouring node which is "closest" to the destination. The notion of a node's location (and hence "closeness") may be determined by its physical location, as in [geographic routing](./Geographic_routing) used by [ad hoc networks](./Ad_hoc_network).  Location may also be an entirely artificial construct as in [small world routing](./Small_world_routing) and [distributed hash table](./Distributed_hash_table).

 

## Greedy algorithms on graphs

 

Graph theory is a rich source of greedy algorithms. Computing scientists frequently use greedy algorithms frequently to compute graph invariants. 

 
- [Dijkstra's algorithm](./Dijkstra's_algorithm) and the related [A* search algorithm](./A*_search_algorithm) are verifiably optimal greedy algorithms for [graph search](./Graph_search) and [shortest path finding](./Shortest_path_problem). 

- A* search is conditionally optimal, requiring an "[admissible heuristic](./Admissible_heuristic)" that will not overestimate path costs.

- [Kruskal's algorithm](./Kruskal's_algorithm) and [Prim's algorithm](./Prim's_algorithm) are greedy algorithms for constructing [minimum spanning trees](./Minimum_spanning_tree) of a given [connected graph](./Connected_graph). They always find an optimal solution, which may not be unique in general.
- A greedy algorithm constructs a Huffman tree in [Huffman coding](./Huffman_coding).
- The [Sequitur](./Sequitur_algorithm) and [Lempel-Ziv-Welch](./Lempel-Ziv-Welch_algorithm) algorithms are [greedy algorithms for grammar induction](./Grammar_induction#Grammatical_inference_by_greedy_algorithms).
- A greedy algorithm finds the maximum independent set in a tree.

 

Greedy algorithms are also used to find upper bounds for the [chromatic numbers](./Graph_coloring)[[8]](./Greedy_algorithm#cite_note-8). A simple example is the bound     χ χ  ( G ) ≤ ≤  Δ Δ  ( G ) + 1   {\displaystyle \chi (G)\leq \Delta (G)+1}  ![{\displaystyle \chi (G)\leq \Delta (G)+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d2355938e28c8687d163852f095953de0bf27feb) obtained by a greedy algorithm.[[9]](./Greedy_algorithm#cite_note-9) We begin by taking a vertex that has not been colored. Since it has at most     Δ Δ  ( G )   {\displaystyle \Delta (G)}  ![{\displaystyle \Delta (G)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359a5b6529b6b451a49a95beec7c87d147f51961) neighbours, at most     Δ Δ  ( G )   {\displaystyle \Delta (G)}  ![{\displaystyle \Delta (G)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/359a5b6529b6b451a49a95beec7c87d147f51961) colors are used in adjacent vertices, leaving a color free for the vertex under consideration.

 

## Greedy approximation algorithms

 

A solution to the [NP-complete](./NP-completeness) [travelling salesman problem](./Travelling_salesman_problem) can be approximated by starting from an empty edge set and then adding the next cheapest edge which is a subgraph of a complete tour. This greedy algorithm has been proven to yield at most     Θ Θ  ( log ⁡ ⁡  n )   {\displaystyle \Theta (\log n)}  ![{\displaystyle \Theta (\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65bac5223de9c91eb3e89a032b5c51fd3041dc66) times longer than the optimal tour.[[10]](./Greedy_algorithm#cite_note-10)

 

Another example is that a solution for the [0-1 knapsack problem](./Knapsack_problem) can be approximated by using the greedy algorithm for the  [fractional knapsack problem](./Continuous_knapsack_problem). This greedy algorithm has been proven to yield a solution at least half the value of the optimal solution.[[11]](./Greedy_algorithm#cite_note-11)

 

Solutions for [submodular maximization](./Submodular_maximization) are approximated using a greedy algorithm which yields a solution at least half the value of the optimal solution.[[12]](./Greedy_algorithm#cite_note-12)

 

Problems for which greedy algorithms are used to provide approximation algorithms include the [set cover](./Set_cover_problem#Greedy_algorithm)[, load balancing](./Load_balancing_(computing)), [Steiner tree](./Steiner_tree_problem) and [independent set](./Independent_set_(graph_theory)#Approximation_algorithms)[[13]](./Greedy_algorithm#cite_note-13) problem.

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Nuvola_apps_edu_mathematics_blue-p.svg/40px-Nuvola_apps_edu_mathematics_blue-p.svg.png)](./File:Nuvola_apps_edu_mathematics_blue-p.svg)[Mathematics portal](./Portal:Mathematics)

  Please keep entries in alphabetical order &#x26; add a short description [[WP:SEEALSO]]   
- [Best-first search](./Best-first_search)
- [Epsilon-greedy strategy](./Multi-armed_bandit#Semi-uniform_strategies)
- [Greedy algorithm for Egyptian fractions](./Greedy_algorithm_for_Egyptian_fractions)
- [Greedy source](./Greedy_source)
- [Hill climbing](./Hill_climbing)
- [Horizon effect](./Horizon_effect)
- [Matroid](./Matroid)

   please keep entries in alphabetical order  

## References

  
1. [↑](./Greedy_algorithm#cite_ref-:0_1-0) Feige, Uriel. ["Greedy algorithms and Matroids"](https://www.wisdom.weizmann.ac.il/~feige/Algs2022/GreedyMatroidLecture.pdf) (PDF). Department of Computer Science and Applied Mathematics, Weizmann Institute of Science. Retrieved 30 April 2026.
2. [↑](./Greedy_algorithm#cite_ref-2) van Melkebeek, Dieter. ["Greedy Approximations"](https://pages.cs.wisc.edu/~dieter/Courses/2004F-CS787/Scribes/greedy-approx.pdf) (PDF). *University of Wisconsin–Madison*. Retrieved 2025-07-25.
3. [↑](./Greedy_algorithm#cite_ref-3) Yuster, Raphael (January 2021). "Paths with many shortcuts in tournaments". *Discrete Mathematics*. **344** (1) 112168. [arXiv](./ArXiv_(identifier)):[2009.13985](https://arxiv.org/abs/2009.13985). [doi](./Doi_(identifier)):[10.1016/j.disc.2020.112168](https://doi.org/10.1016%2Fj.disc.2020.112168).
4. [↑](./Greedy_algorithm#cite_ref-4) ["Lecture 1 – Basics and Greedy Algorithms"](https://www.kth.se/social/files/58203563f2765475d38069ea/algorithms-for-networks-notes-v2-lecture1.pdf) (PDF). *KTH Social*. KTH Royal Institute of Technology. Retrieved 30 April 2026.
5. [↑](./Greedy_algorithm#cite_ref-5) Edmonds, Jack (December 1971). ["Matroids and the greedy algorithm"](http://link.springer.com/10.1007/BF01584082). *Mathematical Programming*. **1** (1): 127–136. [doi](./Doi_(identifier)):[10.1007/BF01584082](https://doi.org/10.1007%2FBF01584082). [ISSN](./ISSN_(identifier)) [0025-5610](https://search.worldcat.org/issn/0025-5610).
6. [↑](./Greedy_algorithm#cite_ref-6) Erickson, Jeff (2019). "Greedy Algorithms". [*Algorithms*](https://jeffe.cs.illinois.edu/teaching/algorithms/). University of Illinois at Urbana-Champaign.
7. [↑](./Greedy_algorithm#cite_ref-7) Gupta, Shreya; Huang, Boyang; Impagliazzo, Russell (2024-11-27), *The Greedy Coin Change Problem*, [arXiv](./ArXiv_(identifier)):[2411.18137](https://arxiv.org/abs/2411.18137)
8. [↑](./Greedy_algorithm#cite_ref-8) Campos, Victor; Gyárfás, András; Havet, Frédéric; Linhares Sales, Claudia; Maffray, Frédéric (April 2010). [*New bounds on the Grundy number of products of graphs*](https://inria.hal.science/inria-00470158) (Technical report). INRIA. RR-7243.
9. [↑](./Greedy_algorithm#cite_ref-9) Diestel, Reinhard (2025). *Graph Theory*. Graduate Texts in Mathematics (Sixth Edition 2025 ed.). Erscheinungsort nicht ermittelbar: Springer. [ISBN](./ISBN_(identifier)) [978-3-662-70106-5](./Special:BookSources/978-3-662-70106-5).
10. [↑](./Greedy_algorithm#cite_ref-10) Brecklinghaus, Judith; Hougardy, Stefan (2015-05-01). ["The approximation ratio of the greedy algorithm for the metric traveling salesman problem"](https://www.sciencedirect.com/science/article/pii/S0167637715000280). *Operations Research Letters*. **43** (3): 259–261. [doi](./Doi_(identifier)):[10.1016/j.orl.2015.02.009](https://doi.org/10.1016%2Fj.orl.2015.02.009). [ISSN](./ISSN_(identifier)) [0167-6377](https://search.worldcat.org/issn/0167-6377).
11. [↑](./Greedy_algorithm#cite_ref-11) Nelson, Jelani (March 7, 2017). ["Lecture 13: PTAS/FPTAS/FPRAS examples; Approximation algorithms via SDP"](https://people.seas.harvard.edu/~cs224/spring17/lec/lec13.pdf) (PDF). *CS 224: Advanced Algorithms, Spring 2017*. Scribe: Hongyao Ma. Harvard University. Retrieved May 1, 2026.
12. [↑](./Greedy_algorithm#cite_ref-12) Grimsman, David; Hespanha, Joao P.; Marden, Jason R. (December 17–19, 2018). *Strategic Information Sharing in Greedy Submodular Maximization*. IEEE Conference on Decision and Control. Miami, Fla.: IEEE. pp. 2722–2727. [doi](./Doi_(identifier)):[10.1109/CDC.2018.8619166](https://doi.org/10.1109%2FCDC.2018.8619166). [ISBN](./ISBN_(identifier)) [978-1-5386-1395-5](./Special:BookSources/978-1-5386-1395-5).
13. [↑](./Greedy_algorithm#cite_ref-13) ["Lecture 5: Introduction to Approximation Algorithms"](http://www.win.tue.nl/~mdberg/Onderwijs/AdvAlg_Material/Course%20Notes/lecture5.pdf) (PDF). *Advanced Algorithms (2IL45) — Course Notes*. TU Eindhoven. [Archived](https://ghostarchive.org/archive/20221009/http://www.win.tue.nl/~mdberg/Onderwijs/AdvAlg_Material/Course%20Notes/lecture5.pdf) (PDF) from the original on 2022-10-09.

 

### Sources

  
- Cormen, Thomas H.; Leiserson, Charles E.; Rivest, Ronald L.; Stein, Clifford (2001). ["16 Greedy Algorithms"](https://books.google.com/books?id=NLngYyWFl_YC&pg=PA370). [*Introduction To Algorithms*](./Introduction_to_Algorithms). MIT Press. pp. 370–. [ISBN](./ISBN_(identifier)) [978-0-262-03293-3](./Special:BookSources/978-0-262-03293-3).
- Gutin, Gregory; Yeo, Anders; Zverovich, Alexey (2002). ["Traveling salesman should not be greedy: Domination analysis of greedy-type heuristics for the TSP"](https://doi.org/10.1016%2FS0166-218X%2801%2900195-0). *Discrete Applied Mathematics*. **117** (1–3): 81–86. [doi](./Doi_(identifier)):[10.1016/S0166-218X(01)00195-0](https://doi.org/10.1016%2FS0166-218X%2801%2900195-0).
- Bang-Jensen, Jørgen; Gutin, Gregory; Yeo, Anders (2004). ["When the greedy algorithm fails"](https://doi.org/10.1016%2Fj.disopt.2004.03.007). *Discrete Optimization*. **1** (2): 121–127. [doi](./Doi_(identifier)):[10.1016/j.disopt.2004.03.007](https://doi.org/10.1016%2Fj.disopt.2004.03.007).
- Bendall, Gareth; Margot, François (2006). ["Greedy-type resistance of combinatorial problems"](https://doi.org/10.1016%2Fj.disopt.2006.03.001). *Discrete Optimization*. **3** (4): 288–298. [doi](./Doi_(identifier)):[10.1016/j.disopt.2006.03.001](https://doi.org/10.1016%2Fj.disopt.2006.03.001).
- Feige, U. (1998). ["A threshold of ln n for approximating set cover"](https://www.cs.duke.edu/courses/cps296.2/spring07/papers/p634-feige.pdf) (PDF). *Journal of the ACM*. **45** (4): 634–652. [doi](./Doi_(identifier)):[10.1145/285055.285059](https://doi.org/10.1145%2F285055.285059). [S2CID](./S2CID_(identifier)) [52827488](https://api.semanticscholar.org/CorpusID:52827488). [Archived](https://ghostarchive.org/archive/20221009/https://www.cs.duke.edu/courses/cps296.2/spring07/papers/p634-feige.pdf) (PDF) from the original on 2022-10-09.
- Nemhauser, G.; Wolsey, L.A.; Fisher, M.L. (1978). ["An analysis of approximations for maximizing submodular set functions—I"](https://www.researchgate.net/publication/242914003). *Mathematical Programming*. **14** (1): 265–294. [doi](./Doi_(identifier)):[10.1007/BF01588971](https://doi.org/10.1007%2FBF01588971). [S2CID](./S2CID_(identifier)) [206800425](https://api.semanticscholar.org/CorpusID:206800425).
- Buchbinder, Niv; Feldman, Moran; Naor, Joseph (Seffi); Schwartz, Roy (2014). ["Submodular maximization with cardinality constraints"](http://theory.epfl.ch/moranfe/Publications/SODA2014.pdf) (PDF). [*Proceedings of the twenty-fifth annual ACM-SIAM symposium on Discrete algorithms*](https://infoscience.epfl.ch/handle/20.500.14299/137481). Society for Industrial and Applied Mathematics. [doi](./Doi_(identifier)):[10.1137/1.9781611973402.106](https://doi.org/10.1137%2F1.9781611973402.106). [ISBN](./ISBN_(identifier)) [978-1-61197-340-2](./Special:BookSources/978-1-61197-340-2). [Archived](https://ghostarchive.org/archive/20221009/http://theory.epfl.ch/moranfe/Publications/SODA2014.pdf) (PDF) from the original on 2022-10-09.
- Krause, A.; Golovin, D. (2014). ["Submodular Function Maximization"](https://books.google.com/books?id=YxliAgAAQBAJ&pg=PA71). In Bordeaux, L.; Hamadi, Y.; Kohli, P. (eds.). *Tractability: Practical Approaches to Hard Problems*. Cambridge University Press. pp. 71–104. [doi](./Doi_(identifier)):[10.1017/CBO9781139177801.004](https://doi.org/10.1017%2FCBO9781139177801.004). [ISBN](./ISBN_(identifier)) [9781139177801](./Special:BookSources/9781139177801).
- [Papadimitriou, Christos H.](./Christos_Papadimitriou); [Steiglitz, Kenneth](./Kenneth_Steiglitz) (1998). *Combinatorial Optimization: Algorithms and Complexity*. Dover.

  

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Greedy algorithms](https://commons.wikimedia.org/wiki/Category:Greedy%20algorithms).  
- ["Greedy algorithm"](https://www.encyclopediaofmath.org/index.php?title=Greedy_algorithm), *[Encyclopedia of Mathematics](./Encyclopedia_of_Mathematics)*, [EMS Press](./European_Mathematical_Society), 2001 [1994]
- Gift, Noah. ["Python greedy coin example"](http://www.oreillynet.com/onlamp/blog/2008/04/python_greedy_coin_changer_alg.html).

 
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

| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |

 
| Authority control databases: National | Poland |
| --- | --- |