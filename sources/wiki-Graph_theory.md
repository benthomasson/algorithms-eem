---
source: https://en.wikipedia.org/wiki/Graph_theory
fetched: 2026-06-19
---

This article is about Mathematical field on vertices connected by edges. For graphs of mathematical functions, see [Graph of a function](./Graph_of_a_function). For other uses, see [Graph (disambiguation)](./Graph_(disambiguation)). Area of discrete mathematics [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Example_of_simple_undirected_graph_3.svg/250px-Example_of_simple_undirected_graph_3.svg.png)](./File:Example_of_simple_undirected_graph_3.svg)A graph with 6 vertices and 7 edges 

In [mathematics](./Mathematics) and [computer science](./Computer_science), **graph theory** is the study of [graphs](./Graph_(discrete_mathematics)), which are [mathematical structures](./Mathematical_structures) used to model pairwise relations between objects. A graph in this context is made up of [vertices](./Vertex_(graph_theory)) (also called nodes or points) which are connected by [edges](./Glossary_of_graph_theory_terms#edge) (also called arcs, links, or lines). A distinction is made between undirected graphs, where edges link two vertices symmetrically, and [directed graphs](./Directed_graph), where edges link two vertices asymmetrically. Graphs are one of the principal objects of study in [discrete mathematics](./Discrete_mathematics).

 

## Definition and etymology

 Main article: [Graph (discrete mathematics)](./Graph_(discrete_mathematics)) [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Undirected%2C_directed%2C_mixed%2C_multigraph.svg/250px-Undirected%2C_directed%2C_mixed%2C_multigraph.svg.png)](./File:Undirected,_directed,_mixed,_multigraph.svg)A graph consists of vertices connected by edges. A graph is occasionally called:

 
- An undirected graph (top left), distinguishing it from a [directed graph](./Directed_graph) that has an arrow on each edge (top right). Undirected and directed graphs can be merged into a [mixed graph](./Mixed_graph) (bottom left); and
- A simple graph, distinguishing it from a [multigraph](./Multigraph) (bottom right).

  

Graph theory is a branch of mathematics that studies [graphs](./Graph_(discrete_mathematics)), mathematical structures for modelling pairwise relations between objects. It is part of [discrete mathematics](./Discrete_mathematics), often considered part of [combinatorics](./Combinatorics), although it is a stand-alone field due to its great growth and distinct from other fields, having its own kind of problems.[[1]](./Graph_theory#cite_note-FOOTNOTEMoharThomassen2001-1) The term "graph" was introduced by [James Joseph Sylvester](./James_Joseph_Sylvester) in a paper published in 1878 in *[Nature](./Nature_(journal))*, where he drew an analogy between "quantic invariants" and "co-variants" of algebra and molecular diagrams.[[2]](./Graph_theory#cite_note-FOOTNOTESylvester1878-2)

 

The definition of a graph can vary, but one can understand that a graph is a structure consisting of vertices (also called nodes or points) and edges (also called arcs, links, or lines). Two vertices of an edge are called the endpoints.[[3]](./Graph_theory#cite_note-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage1_1]-3) Occasionally, a graph is called an undirected graph, to distinguish it from a [directed graph](./Directed_graph). A directed graph is a graph where each edge has an assignment direction known as [orientation](./Orientation_(graph_theory)), designated with an arrow.[[4]](./Graph_theory#cite_note-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage2_2]-4) A [mixed graph](./Mixed_graph) can have edges that may be directed, and some may be undirected.[[5]](./Graph_theory#cite_note-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage3_3]-5) A graph can also be called a simple graph, to distinguish it from a [multigraph](./Multigraph). A multigraph allows many edges to have the same pair of endpoints, and it also allows an edge to connect a vertex to itself, known as a [loop](./Loop_(graph_theory)).[[6]](./Graph_theory#cite_note-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA7_7]-6) A graph can have its edges assigned a number, which is known as the weight. Such a graph is called a weighted graph.

 

## History

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Konigsberg_bridges.png/250px-Konigsberg_bridges.png)](./File:Konigsberg_bridges.png)Map of [Königsberg](./Königsberg) from 1651 showing the layout of the [seven bridges](./Seven_Bridges_of_Königsberg), highlighting the [Pregel River](./Pregel_River) (in blue) and the bridges (in lime). The problem lays the foundation of both graph theory and [topology](./Topology). 

In 1736, [Leonhard Euler](./Leonhard_Euler) published a paper titled *Solutio Problematis ad Geometriam Situs Pertinentis* on the [Seven Bridges of Königsberg](./Seven_Bridges_of_Königsberg), which is regarded as the first paper in the history of graph theory.[[7]](./Graph_theory#cite_note-FOOTNOTEBiggsLloydWilson1986[httpsbooksgooglecombooksidXqYTk0sXmpoCpgPA2_2–3]-7) Euler's paper and [Alexandre-Théophile Vandermonde](./Alexandre-Théophile_Vandermonde)'s 1771 *Remarques sur les Problèmes de Situation* paper on the [knight's tour](./Knight's_tour) carried on with the *analysis situs*, initiated by [Gottfried Wilhelm Leibniz](./Gottfried_Wilhelm_Leibniz).[[8]](./Graph_theory#cite_note-FOOTNOTEBiggsLloydWilson1986[httpsbooksgooglecombooksidXqYTk0sXmpoCpgPA21_21–22]-8) [Euler's characteristic](./Euler's_characteristic) relating the number of edges, vertices, and faces of a convex polyhedron was studied and generalized by [Augustin-Louis Cauchy](./Augustin-Louis_Cauchy) and [Simon Antoine Jean L'Huilier](./Simon_Antoine_Jean_L'Huilier),[[9]](./Graph_theory#cite_note-9) and represents the beginning of the branch of mathematics known as [topology](./Topology).[[10]](./Graph_theory#cite_note-FOOTNOTERicheson200863-10)

 

More than one century after Euler's paper on the bridges of [Königsberg](./Königsberg), and while [Johann Benedict Listing](./Johann_Benedict_Listing) was introducing the concept of topology, [Arthur Cayley](./Arthur_Cayley) was led by an interest in particular analytical forms arising from [differential calculus](./Differential_calculus) to study a particular class of graphs, the [trees](./Tree_(graph_theory)).[[11]](./Graph_theory#cite_note-FOOTNOTECayley1875-11) This study had many implications for theoretical [chemistry](./Chemistry). The techniques he used mainly concern the [enumeration of graphs](./Enumeration_of_graphs) with particular properties. Enumerative graph theory then arose from the results of Cayley and the fundamental results published by [Pólya](./George_Pólya) between 1935 and 1937. These were generalized by [Nicolaas Govert de Bruijn](./Nicolaas_Govert_de_Bruijn) in 1959. Cayley linked his results on trees with contemporary studies of chemical composition.[[11]](./Graph_theory#cite_note-FOOTNOTECayley1875-11) The fusion of ideas from mathematics with those from chemistry began what has become part of the standard terminology of graph theory.

 

The autonomous development of topology from 1860 to 1930 fertilized graph theory back through the works of [Camille Jordan](./Camille_Jordan), [Kazimierz Kuratowski](./Kazimierz_Kuratowski), and [Hassler Whitney](./Hassler_Whitney). Another important factor in the common development of graph theory and topology came from the use of the techniques of modern algebra. The first example of such a use comes from the work of the physicist [Gustav Kirchhoff](./Gustav_Kirchhoff), who published in 1845 his [Kirchhoff's circuit laws](./Kirchhoff's_circuit_laws) for calculating the [voltage](./Voltage) and [current](./Electric_current) in [electric circuits](./Electric_circuit).

 

The first textbook on graph theory was written by [Dénes Kőnig](./Dénes_Kőnig), and published in 1936.[[12]](./Graph_theory#cite_note-FOOTNOTETutte2001[httpsbooksgooglecombooksiduTGhooU37h4CpgPA30_30]-12) Another book by [Frank Harary](./Frank_Harary), published in 1969, was "considered the world over to be the definitive textbook on the subject",[[13]](./Graph_theory#cite_note-FOOTNOTEGardner1992203-13) and enabled mathematicians, chemists, electrical engineers and social scientists to talk to each other. Harary donated all of the royalties to fund the [Pólya Prize](./George_Pólya_Prize).[[14]](./Graph_theory#cite_note-FOOTNOTESociety_for_Industrial_and_Applied_Mathematics200226-14)

 

One of the most famous problems in graph theory is the [four color problem](./Four_color_problem): Is it true that any map drawn in the plane may have its regions colored with four colors, in such a way that any two regions having a common border have different colors? This problem was first posed by [Francis Guthrie](./Francis_Guthrie) in 1852, and its first written record is in a letter of [Augustus De Morgan](./Augustus_De_Morgan) addressed to [William Rowan Hamilton](./William_Rowan_Hamilton) the same year. Many incorrect proofs have been proposed, including those by Augustin Cayley, [Alfred Kempe](./Alfred_Kempe), and others. The study and the generalization of this problem by [Peter Tait](./Peter_Tait_(physicist)), [Percy John Heawood](./Percy_John_Heawood), [Frank P. Ramsey](./Frank_P._Ramsey) and [Hadwiger](./Hugo_Hadwiger) led to the study of the colorings of the graphs embedded on surfaces with arbitrary [genus](./Genus_(mathematics)). Tait's reformulation generated a new class of problems, the *factorization problems*, particularly studied by [Petersen](./Julius_Petersen) and [Dénes Kőnig](./Dénes_Kőnig). The works of Ramsey on colorations, and more specially, the results obtained by [Pál Turán](./Pál_Turán) in 1941, were at the origin of another branch of graph theory, known as [extremal graph theory](./Extremal_graph_theory).

 

The four-color problem remained unsolved for more than a century. In 1969, [Heinrich Heesch](./Heinrich_Heesch) published a method for solving the problem using computers.[[15]](./Graph_theory#cite_note-15) A computer-aided proof produced in 1976 by [Kenneth Appel](./Kenneth_Appel) and [Wolfgang Haken](./Wolfgang_Haken) makes fundamental use of the notion of "discharging" developed by Heesch.[[16]](./Graph_theory#cite_note-AA1-16)[[17]](./Graph_theory#cite_note-AA2-17) The proof involved checking the properties of 1,936 configurations by computer, and was not fully accepted at the time due to its complexity. A simpler proof considering only 633 configurations was given twenty years later by [Robertson](./Neil_Robertson_(mathematician)), [Seymour](./Paul_Seymour_(mathematician)), [Sanders](./Daniel_P._Sanders) and [Thomas](./Robin_Thomas_(mathematician)).[[18]](./Graph_theory#cite_note-RSST-18)

 

The introduction of [probabilistic methods](./Probabilistic_method) in graph theory, especially in the study of [Erdős](./Paul_Erdős) and [Rényi](./Alfréd_Rényi) of the asymptotic probability of graph connectivity, gave rise to yet another branch, known as [random graph theory](./Random_graph), which has been a fruitful source of graph-theoretic results.[[19]](./Graph_theory#cite_note-FOOTNOTEBollobás2001[httpbooksgooglecombooksido9WecWgilzYCpgPR10_xi]-19)

 

## Subareas

 

### Topological graph theory

 Main article: [Topological graph theory](./Topological_graph_theory) See also: [Category:Topological graph theory](./Category:Topological_graph_theory) [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Heawood_graph_and_map_on_torus.png/250px-Heawood_graph_and_map_on_torus.png)](./File:Heawood_graph_and_map_on_torus.png)[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Diamond_pagewidth.svg/250px-Diamond_pagewidth.svg.png)](./File:Diamond_pagewidth.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Zarankiewicz_K4_7.svg/250px-Zarankiewicz_K4_7.svg.png)](./File:Zarankiewicz_K4_7.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Map_of_United_States_accessible_colors_shown.svg/250px-Map_of_United_States_accessible_colors_shown.svg.png)](./File:Map_of_United_States_accessible_colors_shown.svg)Topological graph theory deals with the study of graphs related to topology. The topics, along with the given top-to-bottom illustrations, are

- [Embedding of a graph](./Graph_embedding) in a surface, with an example of [Heawood graph](./Heawood_graph) in torus;
- [1-page embedding](./Book_embedding) of the [diamond graph](./Diamond_graph);
- [Crossing number](./Crossing_number_(graph_theory)), with an example of a [complete bipartite graph](./Complete_bipartite_graph) of four and seven vertices      K  4 , 7     {\displaystyle K_{4,7}}  ![{\displaystyle K_{4,7}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fb5a257465cad23b7b349e4f2974c03ae3446cd8), having with 18 crossings (in red dots); and
- Map coloring, using [four-color theorem](./Four-color_theorem) to color differently each [state](./U.S._state) in the [United States](./United_States), ignoring lakes and oceans.

 

[Topological graph theory](./Topological_graph_theory) deals with the study of graphs as [topological spaces](./Topological_space). The graph in a topology is a set of [simplexes](./Simplex) that is called the [simplicial one-dimensional complex](./Simplicial_complex).[[20]](./Graph_theory#cite_note-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA1_1]-20) This subarea studies the [embedding](./Graph_embedding) (or imbedding) of a graph in [surface](./Surface_(topology)) and [linkless embedding](./Linkless_embedding), [graph minors](./Graph_minor), [crossing number](./Crossing_number_(graph_theory)), map coloring, and [voltage graph](./Voltage_graph).[[21]](./Graph_theory#cite_note-21)

 

The embedding of a graph in a surface is the representation of a graph in which the points are associated with the vertices and simple arcs with edges in a surface. The endpoints are associated with an edge, and the points with the end vertices. No arcs include points associated with other vertices, and two arcs never intersect at a point that is interior to either of the arcs.[*[citation needed](./Wikipedia:Citation_needed)*] The graph embedding can be generalized into the linkless embedding, whereby no two cycles of the graph are linked in three-dimensional Euclidean space,[[22]](./Graph_theory#cite_note-FOOTNOTELovász200676-22) and a [book](./Book_embedding), a collection of [half-planes](./Half-space_(geometry)) all having the same line as their boundary.[[23]](./Graph_theory#cite_note-FOOTNOTEPersinger1966-23)

 

The graph is said to be minor if it can be formed from another graph by deleting vertices and edges, and by [edge-contraction](./Edge_contraction).[[22]](./Graph_theory#cite_note-FOOTNOTELovász200676-22) The earliest result of the graph minor theory is from [Wagner's theorem](./Wagner's_theorem), stating that a finite graph is planar if and only if its minor includes neither the [complete graph on five vertices](./Complete_graph)      K  5     {\displaystyle K_{5}}  ![{\displaystyle K_{5}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/10a83da34fe45aa3be9a7d0b197417021bb4a884) nor the [utility graph](./Utility_graph).[[24]](./Graph_theory#cite_note-FOOTNOTELovász200677-24) A related result is the [Robertson–Seymour theorem](./Robertson–Seymour_theorem), implying the existence of [forbidden minor](./Forbidden_minor) for every property of graphs preserved by deletions and edge contractions.[[25]](./Graph_theory#cite_note-FOOTNOTELovász200678Theorem_4-25)

 

The crossing number tells the minimum number of crossing edges of a graph. This study originated from a Hungarian mathematician [Pál Turán](./Pál_Turán) who [asked for a factory plan that minimized the number of crossings between tracks connecting brick kilns to storage sites](./Turán's_brick_factory_problem). This problem can be formalized as asking for the crossing number of a [complete bipartite graph](./Complete_bipartite_graph).[[26]](./Graph_theory#cite_note-FOOTNOTEFoulds1992[httpsbooksgooglecombooksid5G4QBwAAQBAJpgPA71_71]-26)

 

A [graph coloring](./Graph_coloring) is a methodical assignment of labelling the elements of a graph, which is traditionally called [colors](./Color). In coloring, no two adjacent elements have the same color. It requires the minimum number of colors, which is known as the chromatic number. [Four-color theorem](./Four-color_theorem) stated that no more than four colors are required to color the regions of any map so that no two adjacent regions have the same color; that is, no two regions share a common boundary.[[27]](./Graph_theory#cite_note-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA215_215]-27) This theorem is stronger than [five-color theorem](./Five-color_theorem). Relatedly, [Earth–Moon problem](./Earth–Moon_problem) is known for the nowadays open problem on extension of the planar map coloring problem, solved by the four-color theorem.

 

A voltage graph is a directed graph whose edges are labelled invertibly by elements of a [group](./Group_(mathematics)). This graph concisely specifies the [derived graph](./Derived_graph).[[28]](./Graph_theory#cite_note-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA57_57]-28) It is also a common way to form a [covering graph](./Covering_graph).[[29]](./Graph_theory#cite_note-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA72_72]-29)

 

### Algebraic graph theory

 Main article: [Algebraic graph theory](./Algebraic_graph_theory) See also: [Spectral graph theory](./Spectral_graph_theory) and [Category:Topological graph theory](./Category:Topological_graph_theory) [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/91/Petersen1_tiny.svg/250px-Petersen1_tiny.svg.png)](./File:Petersen1_tiny.svg)Algebraic graph theory uses group theory to study the symmetry of a graph. For example, [Petersen graph](./Petersen_graph) is high-symmetrical, known for [vertex-transitive](./Vertex-transitive_graph), [symmetric](./Symmetric_graph), [distance-transitive](./Distance-transitive_graph), and [distance-regular](./Distance-regular_graph). Its [automorphism group](./Graph_automorphism) has 120 elements and [symmetric group](./Symmetric_group)      S  5     {\displaystyle S_{5}}  ![{\displaystyle S_{5}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7d113353a42f71fc5e7154ddef2257079ab2e25a). 

[Algebraic graph theory](./Algebraic_graph_theory) is the study of graph theory that involves major branches of [algebra](./Algebra). Major branches of algebra that are used are [linear algebra](./Linear_algebra) and [group theory](./Group_theory).

 

A study of graph theory using linear algebra is called [spectral graph theory](./Spectral_graph_theory). This study focuses on [adjacency matrix](./Adjacency_matrix), a matrix that represents the graph, and its [spectrum](./Eigendecomposition_of_a_matrix), which focuses on the [characteristic polynomial](./Characteristic_polynomial), [eigenvalues, and eigenvectors](./Eigenvalues_and_eigenvectors) of the given adjacency matrix. It also focuses on the [Laplacian matrix](./Laplacian_matrix) of a graph, which involves the [degree matrix](./Degree_matrix) (a [diagonal matrix](./Diagonal_matrix) that represents the degree of a vertex) and the adjacency matrix.[[30]](./Graph_theory#cite_note-30)

 

Group theory, particularly [automorphism groups](./Automorphism_group) and [geometric group theory](./Geometric_group_theory), focuses on various families of graphs based on symmetry in algebraic graph theory.[[31]](./Graph_theory#cite_note-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA115_Chapter_15:_Automorphisms_of_graphs]-31) Such a symmetry includes [symmetric graphs](./Symmetric_graph), [vertex-transitive graphs](./Vertex-transitive_graph), [edge-transitive graphs](./Edge-transitive_graph), [distance-transitive graphs](./Distance-transitive_graph), [distance-regular graphs](./Distance-regular_graph), and [strongly regular graphs](./Strongly_regular_graph).[[32]](./Graph_theory#cite_note-FOOTNOTEGodsilRoyle2001[httpbooksgooglecombooksidGeSPBAAAQBAJpgPR12_xii–ixi]-32) [Frucht's theorem](./Frucht's_theorem) states that every [finite group](./Finite_group) is the group of symmetries of a finite undirected graph, or more strongly, there exist infinitely many non-isomorphic simple connected graphs such that the automorphism group of each of them is isomorphic to a finite group.[[33]](./Graph_theory#cite_note-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA70_70]-33)

 

Algebraic graph theory also studies the algebraic [invariants](./Graph_invariant), [chromatic polynomial](./Chromatic_polynomial), [Tutte polynomial](./Tutte_polynomial) of a graph, and [knot invariant](./Knot_invariant).[[32]](./Graph_theory#cite_note-FOOTNOTEGodsilRoyle2001[httpbooksgooglecombooksidGeSPBAAAQBAJpgPR12_xii–ixi]-32) A graph invariant is a property of graphs that depends only on the abstract structure, instead of labellings or drawings of the graph. A chromatic polynomial is a polynomial that counts the number of graph colorings as a function of the number of colors.[[34]](./Graph_theory#cite_note-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA64_64]-34) The Tutte polynomial is a two-variable polynomial on graph connectivity.[[35]](./Graph_theory#cite_note-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA98_98]-35)

 

### Geometric graph theory

 Main article: [Geometric graph theory](./Geometric_graph_theory) See also: [Graph drawing](./Graph_drawing) and [Category:Geometric graph theory](./Category:Geometric_graph_theory) [![](//upload.wikimedia.org/wikipedia/commons/thumb/1/16/Euclidean_minimum_spanning_tree.svg/250px-Euclidean_minimum_spanning_tree.svg.png)](./File:Euclidean_minimum_spanning_tree.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Dodecahedron_schlegel.svg/250px-Dodecahedron_schlegel.svg.png)](./File:Dodecahedron_schlegel.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/9/94/Circle_packing_graph.svg/250px-Circle_packing_graph.svg.png)](./File:Circle_packing_graph.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/0/01/Fano_plane-Levi_graph.svg/250px-Fano_plane-Levi_graph.svg.png)](./File:Fano_plane-Levi_graph.svg)Geometric graph theory studies a graph drawn with straight-line or continuous curved edges with geometric properties combinatorially. Within these illustrations, the geometric graph theory studies:

- the [Euclidean graph](./Euclidean_graph) as in [Euclidean minimum spanning tree](./Euclidean_minimum_spanning_tree) (top left);
- [polyhedral graph](./Polyhedral_graph) with an example of [dodecahedral graph](./Dodecahedral_graph) for a regular dodecahedron (top right);
- the [intersection graph](./Intersection_graph) of geometric sets like the [coin graph](./Coin_graph) with [circle packing](./Circle_packing) (bottom left); and
- the [incidence geometry](./Incidence_geometry) as in the [Heawood graph](./Heawood_graph) being the [Levi graph](./Levi_graph) of [Fano plane](./Fano_plane) (bottom right).

 

[Geometric graph theory](./Geometric_graph_theory) focuses on combinatorial and geometric properties of a graph that is drawn in a plane with straight-line or continuous curved edges in [Euclidean space](./Euclidean_space).[[36]](./Graph_theory#cite_note-FOOTNOTEPach2018[httpbooksgooglecombooksid9mlQDwAAQBAJpgPA257_257]-36) As part of [discrete geometry](./Discrete_geometry) and [computational geometry](./Computational_geometry), geometric graph theory studies [planar graphs](./Planar_graph),[[37]](./Graph_theory#cite_note-FOOTNOTEBounceurBezouiEuler2019[httpbooksgooglecombooksidUmYIEQAAQBAJpgPA13_13–14]-37) relationship to [higher-dimensional convex polytopes](./Polytope),[[38]](./Graph_theory#cite_note-38) [intersection](./Intersection) of geometrical shaped sets,[[39]](./Graph_theory#cite_note-FOOTNOTEMcKeeMcMorris1999[httpbooksgooglecombooksidphWjyYLP7d4CpgPA1_1&ndash;2]-39) and other geometries' subareas of [incidence geometry](./Incidence_geometry) and [projective geometry](./Projective_geometry).[[40]](./Graph_theory#cite_note-FOOTNOTEGrünbaum2006[httpsbooksgooglecombooksidcKpBGcqpspICpgPA181_181]-40)

 

A planar graph wherein its vertices are embedded as points, and its edges are non-crossing [line segments](./Line_segment) in the [Euclidean plane](./Euclidean_plane) is called [planar straight-line graph](./Planar_straight-line_graph). Any planar graph can be represented as a planar straight-line graph by [Fáry's theorem](./Fáry's_theorem). The planar straight-line graph is the special case of a Euclidean graph. The Euclidean graph allows its edges to have the length of the [Euclidean distance](./Euclidean_distance) between its endpoints. Its notions are the [Euclidean minimum spanning tree](./Euclidean_minimum_spanning_tree) on minimizing the total length of the segments for finite points in any [Euclidean space](./Euclidean_space), [Hadwiger–Nelson problem](./Hadwiger–Nelson_problem) on asking for the minimum number of coloring plane such that no two points at a [unit distance](./Unit_distance_graph) from each other have the same color, and [shortest path problem](./Shortest_path_problem) on finding a path between two vertices in a graph that minimizes the sum of the assigned values of its edges.[[37]](./Graph_theory#cite_note-FOOTNOTEBounceurBezouiEuler2019[httpbooksgooglecombooksidUmYIEQAAQBAJpgPA13_13–14]-37)

 

A [visibility graph](./Visibility_graph) is a graph whose vertices and edges are the point locations and visible connections, respectively. In a [simple polygon](./Simple_polygon), where its edges are not self-intersecting and have no holes, the vertices of a visibility graph are connected by edges that represent the sides and diagonals of a polygon. The vertices are defined as the point locations.[[41]](./Graph_theory#cite_note-FOOTNOTEEverettCorneil1995-41) [Polyhedral graph](./Polyhedral_graph) is an undirected graph that forms the vertices and edges of a three-dimensional [convex polyhedron](./Convex_polyhedron). In order to achieve it, such a graph must meet the requirements of [Steinitz's theorem](./Steinitz's_theorem), stating that every convex polyhedron is [3-vertex connected planar graph](./Vertex_connectivity). The planar graph remains connected whenever any two of its vertices are removed.[[42]](./Graph_theory#cite_note-FOOTNOTEZiegler2007628–642-42)

 

An [intersection graph](./Intersection_graph) is a graph in which each vertex is associated with a set and in which vertices are connected by edges whenever the corresponding sets have a nonempty [intersection](./Intersection).[[39]](./Graph_theory#cite_note-FOOTNOTEMcKeeMcMorris1999[httpbooksgooglecombooksidphWjyYLP7d4CpgPA1_1&ndash;2]-39) Each vertex is represented as a set, and every two vertices are connected. Hence, the intersection graph of finite sets can be represented through the smallest number of required elements, known as the [intersection number](./Intersection_number_(graph_theory)). The result graph can be geometric whenever the sets are geometrical objects. For instance, the intersection graph of line segments in one dimension is an [interval graph](./Interval_graph). The intersection graph of unit disks in the plane is a [unit disk graph](./Unit_disk_graph). The intersection of a [circle packing](./Circle_packing) is a [coin graph](./Coin_graph), where a vertex and an edge represent a circle and every pair of tangent circles; by Koebe–Andreev–Thurston theorem, the intersection graphs of non-crossing circles are exactly the planar graphs.[[43]](./Graph_theory#cite_note-43) [Scheinerman's theorem](./Scheinerman's_conjecture) states that every planar graph can be represented as the intersection graph of line segments in the plane.[[44]](./Graph_theory#cite_note-FOOTNOTEChalopinGonçalves2009-44)

 

The [Levi graph](./Levi_graph) is a [bipartite graph](./Bipartite_graph) that associates to the [incidence structure](./Incidence_structure) and [projective configuration](./Configuration_(geometry)).[[40]](./Graph_theory#cite_note-FOOTNOTEGrünbaum2006[httpsbooksgooglecombooksidcKpBGcqpspICpgPA181_181]-40)

 

By applying to [information visualization](./Information_visualization), this creates another subarea of graph theory that is known as [graph drawing](./Graph_drawing), which visualizes a graph depiction. Frequently drawn as node–link diagrams, the vertices of a graph are represented as disks, boxes, or textual labels, and the edges are represented as line segments, polylines, or curves in the Euclidean plane.[[45]](./Graph_theory#cite_note-FOOTNOTEDi_BattistaEadesTamassiaTollis1994viii-45) Many definitions for graph drawings based on quality measures include the crossing number,[[46]](./Graph_theory#cite_note-FOOTNOTEDi_BattistaEadesTamassiaTollis199414-46) [area](./Area_(graph_drawing)), symmetry display on finding the problem of a graph's group automorphism,[[47]](./Graph_theory#cite_note-FOOTNOTEDi_BattistaEadesTamassiaTollis199416-47) [bend minimization](./Bend_minimization), [angular resolution](./Angular_resolution_(graph_drawing)),[[48]](./Graph_theory#cite_note-FOOTNOTEPachSharir2009-48) and [slope number](./Slope_number).[[48]](./Graph_theory#cite_note-FOOTNOTEPachSharir2009-48) Tools for graph drawings are the circle packing,[[49]](./Graph_theory#cite_note-FOOTNOTEMalitzPapakostas1994-49) the intersection graph, and other visualizations of the adjacency matrix.

 

### Extremal graph theory

 Main article: [Extremal graph theory](./Extremal_graph_theory) See also: [Category:Extremal graph theory](./Category:Extremal_graph_theory) [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Biclique_K_5_5.svg/250px-Biclique_K_5_5.svg.png)](./File:Biclique_K_5_5.svg)Extremal graph theory studies the maximum number of a graph's edges, known as the extremal number. The origin is from Mantel's theorem on finding the extremal number of a [triangle-free graph](./Triangle-free_graph) (illustrated), which is     ⌊ ⌊   n  2    /  4 ⌋ ⌋    {\displaystyle \lfloor n^{2}/4\rfloor }  ![{\displaystyle \lfloor n^{2}/4\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c9ee46de44c6ef9a36d80e4119114dbe14cb7d1f). 

[Extremal graph theory](./Extremal_graph_theory) is a branch of mathematics at the intersection of [extremal combinatorics](./Extremal_combinatorics) and graph theory. This area studies the maximum number of a graph's edges, known as the extremal number.[[50]](./Graph_theory#cite_note-FOOTNOTEChartrandJordonVatterZhang2024[httpbooksgooglecombooksid01cIEQAAQBAJpgPA221_221]-50) The subarea's milestone originated from Mantel's theorem on the extremal number of a [triangle-free graph](./Triangle-free_graph). [Turán's theorem](./Turán's_theorem) extended Mantel's theorem for any undirected graph that does not have a complete subgraph of a given size. Turán's theorem is generalized by [Erdős–Stone theorem](./Erdős–Stone_theorem), which is occasionally known as the "fundamental theorem of extremal graph theory".[[51]](./Graph_theory#cite_note-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA104_104]-51)

 

Extremal graph theory also studies [forbidden subgraph problem](./Forbidden_subgraph_problem), [homomorphism density](./Homomorphism_density), and [Szemerédi regularity lemma](./Szemerédi_regularity_lemma). The forbidden subgraphs problem suggests finding the extremal number of a graph with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) vertices such that it does not have a subgraph that is [isomorphic](./Graph_isomorphism) to the graph.[[52]](./Graph_theory#cite_note-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA123_123]-52) A [homomorphism density](./Homomorphism_density) is a parameter that involves the [graph homomorphism](./Graph_homomorphism). The density may refer to the probability that a map from the vertices of a graph to the vertices of another one chosen uniformly at random is a graph homomorphism. Being homomorphic means there exists a mapping between two graphs that respects their structure, or equivalently, a function between the vertex sets of two graphs that maps adjacent vertices to adjacent vertices.[[53]](./Graph_theory#cite_note-53) Szemerédi's regularity lemma states that a graph can be partitioned into a bounded number of parts so that the edges between parts are     ε ε    {\displaystyle \varepsilon }  ![{\displaystyle \varepsilon }](https://wikimedia.org/api/rest_v1/media/math/render/svg/a30c89172e5b88edbd45d3e2772c7f5e562e5173)-regular.

 

### Theory of random graph

 Main article: [Random graph](./Random_graph) See also: [Category:Random graphs](./Category:Random_graphs) 

The theory of [random graph](./Random_graph) focuses on graphs using [probabilistic method](./Probabilistic_method). The subarea was founded by Hungarian mathematicians [Paul Erdős](./Paul_Erdős) and [Alfréd Rényi](./Alfréd_Rényi), whose modelling generates random graphs, known as [Erdős–Rényi model](./Erdős–Rényi_model).[[19]](./Graph_theory#cite_note-FOOTNOTEBollobás2001[httpbooksgooglecombooksido9WecWgilzYCpgPR10_xi]-19)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Random_minimum_spanning_tree.svg/250px-Random_minimum_spanning_tree.svg.png)](./File:Random_minimum_spanning_tree.svg)[Random minimum spanning tree](./Random_minimum_spanning_tree) on the same graph but with randomized weights 

This subarea studies the [random tree](./Random_tree). A [tree](./Tree_(graph_theory)) is an undirected graph where every pair of vertices is connected by exactly one [path](./Path_(graph_theory)). Therefore, a random tree is a tree that is formed by a [stochastic process](./Stochastic_process). Many types of random trees include:

 
- [Uniform spanning tree](./Uniform_spanning_tree) is a [spanning tree](./Spanning_tree) of a given graph in which each different tree is [equally likely to be selected](./Discrete_uniform_distribution). Being a spanning tree means that a subgraph is a tree that includes all of the vertices of a graph. The uniform spanning tree can be generated by using the method of random simple path known as the [loop-erased random walk](./Loop-erased_random_walk), of taking a random walk on the given graph and erasing the cycles created by this walk.[[54]](./Graph_theory#cite_note-FOOTNOTEWilson1996-54)
- [Branching process](./Branching_process), a model of a population in which each individual has a random number of children
- [Brownian tree](./Brownian_tree), a fractal tree structure created by diffusion-limited aggregation processes
- [Random binary tree](./Random_binary_tree) is a [binary tree](./Binary_tree) selected at random from some [probability distribution](./Probability_distribution) on binary trees.[[55]](./Graph_theory#cite_note-FOOTNOTESedgewickFlajolet2013286-55) This includes trees formed by random insertion orders,[[56]](./Graph_theory#cite_note-FOOTNOTEMorin2004-56) and trees that are uniformly distributed with a given number of nodes.
- [Random forest](./Random_forest), a machine-learning classifier based on choosing random subsets of variables for each tree and using the most frequent tree output as the overall classification.
- [Random minimal spanning tree](./Random_minimal_spanning_tree) is a spanning tree of a graph formed by choosing random edge weights and using the [minimum spanning tree](./Minimum_spanning_tree) for those weights.[[57]](./Graph_theory#cite_note-FOOTNOTEMcDiarmidJohnsonStone1997-57)
- [Random recursive tree](./Random_recursive_tree), increasingly labelled trees, which can be generated using a simple stochastic growth rule.
- [Rapidly exploring random tree](./Rapidly_exploring_random_tree), a fractal space-filling pattern used as a data structure for searching high-dimensional spaces.
- [Treap](./Treap) or randomized binary search tree, a data structure that uses random choices to simulate a random binary tree for non-random update sequences

 

### Graph enumeration

 Main article: [Graph enumeration](./Graph_enumeration) 

## Applications

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Wikipedia_multilingual_network_graph_July_2013.svg/250px-Wikipedia_multilingual_network_graph_July_2013.svg.png)](./File:Wikipedia_multilingual_network_graph_July_2013.svg)The network graph formed by Wikipedia editors (edges) contributing to different Wikipedia language versions (vertices) during one month in summer 2013[[58]](./Graph_theory#cite_note-58) 

Graphs can be used to model many types of relations and processes in physical, biological,[[59]](./Graph_theory#cite_note-59)[[60]](./Graph_theory#cite_note-60) social and information systems.[[61]](./Graph_theory#cite_note-61) Many practical problems can be represented by graphs. Emphasizing their application to real-world systems, the term *network* is sometimes defined to mean a graph in which attributes (e.g. names) are associated with the vertices and edges, and the subject that expresses and understands real-world systems as a network is called [network science](./Network_science).

 

### Computer science

 

Within [computer science](./Computer_science), '[causal](./Cybernetics)' and 'non-causal' linked structures are graphs that are used to represent networks of communication, data organization, computational devices, the flow of computation, etc. For instance, the link structure of a [website](./Website) can be represented by a directed graph, in which the vertices (nodes) represent web pages and directed edges represent [links](./Hyperlink) from one page to another. A similar approach can be taken to problems in social media,[[62]](./Graph_theory#cite_note-62) travel, biology, computer chip design, mapping the progression of neuro-degenerative diseases,[[63]](./Graph_theory#cite_note-63)[[64]](./Graph_theory#cite_note-64) and many other fields. The development of [algorithms](./Algorithm) to [handle graphs](./List_of_algorithms#Graph_algorithms) is therefore of major interest in computer science. The [transformation of graphs](./Graph_transformation) is often formalized and represented by [graph rewrite systems](./Graph_rewriting). Complementary to [graph transformation](./Graph_transformation) systems focusing on rule-based in-memory manipulation of graphs are [graph databases](./Graph_database) geared towards [transaction](./Database_transaction)-safe, [persistent](./Persistence_(computer_science)) storing and querying of [graph-structured data](./Graph_(data_structure)).

 

### Linguistics

 

Graph-theoretic methods, in various forms, have proven particularly useful in [linguistics](./Linguistics), since natural language often lends itself well to discrete structure. Traditionally, [syntax](./Syntax) and compositional semantics follow tree-based structures, whose expressive power lies in the [principle of compositionality](./Principle_of_compositionality), modeled in a hierarchical graph. More contemporary approaches such as [head-driven phrase structure grammar](./Head-driven_phrase_structure_grammar) model the syntax of natural language using [typed feature structures](./Feature_structure), which are [directed acyclic graphs](./Directed_acyclic_graph). 
Within [lexical semantics](./Lexical_semantics), especially as applied to computers, modeling word meaning is easier when a given word is understood in terms of related words; [semantic networks](./Semantic_network) are therefore important in [computational linguistics](./Computational_linguistics). Still, other methods in phonology (e.g. [optimality theory](./Optimality_theory), which uses [lattice graphs](./Lattice_graph)) and morphology (e.g. finite-state morphology, using [finite-state transducers](./Finite-state_transducer)) are common in the analysis of language as a graph. Indeed, the usefulness of this area of mathematics to linguistics has borne organizations such as [TextGraphs](http://www.textgraphs.org/), as well as various 'Net' projects, such as [WordNet](./WordNet), [VerbNet](./VerbNet), and others.

 

### Physics and chemistry

 

Graph theory is also used to study molecules in [chemistry](./Chemistry) and [physics](./Physics). In [condensed matter physics](./Condensed_matter_physics), the three-dimensional structure of complicated simulated atomic structures can be studied quantitatively by gathering statistics on graph-theoretic properties related to the topology of the atoms. Also, "the [Feynman graphs and rules of calculation](./Feynman_diagram) summarize [quantum field theory](./Quantum_field_theory) in a form in close contact with the experimental numbers one wants to understand."[[65]](./Graph_theory#cite_note-65) In chemistry a graph makes a natural model for a molecule, where vertices represent [atoms](./Atom) and edges [bonds](./Chemical_bond). This approach is especially used in computer processing of molecular structures, ranging from [chemical editors](./Molecule_editor) to database searching. In [statistical physics](./Statistical_physics), graphs can represent local connections between interacting parts of a system, as well as the dynamics of a physical process on such
systems. Similarly, in [computational neuroscience](./Computational_neuroscience) graphs can be used to represent functional connections between brain areas that interact to give rise to various cognitive processes, where the vertices represent different areas of the brain and the edges represent the connections between those areas. Graph theory plays an important role in electrical modeling of electrical networks, here, weights are associated with resistance of the wire segments to obtain electrical properties of network structures.[[66]](./Graph_theory#cite_note-66) Graphs are also used to represent the micro-scale channels of [porous media](./Porous_medium), in which the vertices represent the pores and the edges represent the smaller channels connecting the pores. [Chemical graph theory](./Chemical_graph_theory) uses the [molecular graph](./Molecular_graph) as a means to model molecules.
Graphs and networks are excellent models to study and understand phase transitions and critical phenomena. Removal of nodes or edges leads to a critical transition where the network breaks into small clusters which is studied as a phase transition. This breakdown is studied via [percolation theory](./Percolation_theory).[[67]](./Graph_theory#cite_note-67)

 

### Social sciences

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Moreno_Sociogram_2nd_Grade.svg/250px-Moreno_Sociogram_2nd_Grade.svg.png)](./File:Moreno_Sociogram_2nd_Grade.svg)Graph theory in sociology: [Moreno](./Jacob_L._Moreno) [Sociogram](./Sociogram) (1953).[[68]](./Graph_theory#cite_note-68) 

Graph theory is also widely used in [sociology](./Sociology) as a way, for example, to [measure actors' prestige](./Six_Degrees_of_Kevin_Bacon) or to explore [rumor spreading](./Rumor_spread_in_social_network), notably through the use of [social network analysis](./Social_network_analysis) software. Under the umbrella of social networks are many different types of graphs.[[69]](./Graph_theory#cite_note-69) Acquaintanceship and friendship graphs describe whether people know each other. Influence graphs model whether certain people can influence the behavior of others. Finally, collaboration graphs model whether two people work together in a particular way, such as acting in a movie together.

 

### Biology and ecology

 

Likewise, graph theory is useful in [biology](./Biology) and conservation efforts where a vertex can represent regions where certain species exist (or inhabit) and the edges represent migration paths or movement between the regions. This information is important when looking at breeding patterns or tracking the spread of disease, parasites or how changes to the movement can affect other species.

 

Graphs are also commonly used in [molecular biology](./Molecular_biology) and [genomics](./Genomics) to model and analyze datasets with complex relationships. For example, graph-based methods are often used to 'cluster' cells together into cell-types in [single-cell transcriptome analysis](./Single-cell_analysis#Transcriptomics). Another use is to model genes or proteins in a [pathway](./Biological_pathway) and study the relationships between them, such as metabolic pathways and gene regulatory networks.[[70]](./Graph_theory#cite_note-70) Evolutionary trees, ecological networks, and hierarchical clustering of gene expression patterns are also represented as graph structures. 

 

Graph theory is also used in [connectomics](./Connectomics);[[71]](./Graph_theory#cite_note-71) nervous systems can be seen as a graph, where the nodes are neurons and the edges are the connections between them.

 

### Other topics

 

A graph structure can be extended by assigning a weight to each edge of the graph. Graphs with weights, or [weighted graphs](./Weighted_graph), are used to represent structures in which pairwise connections have some numerical values. For example, if a graph represents a road network, the weights could represent the length of each road. There may be several weights associated with each edge, including distance (as in the previous example), travel time, or monetary cost. Such weighted graphs are commonly used to program GPS's, and travel-planning search engines that compare flight times and costs.

 

## Representation

 

A graph is an abstraction of relationships that emerge in nature; hence, it cannot be coupled to a certain representation. The way it is represented depends on the degree of convenience such representation provides for a certain application. The most common representations are the visual, in which, usually, vertices are drawn and connected by edges, and the tabular, in which rows of a table provide information about the relationships between the vertices within the graph.

 

### Visual: Graph drawing

 Main article: [Graph drawing](./Graph_drawing) 

Graphs are usually represented visually by drawing a point or circle for every vertex, and drawing a line between two vertices if they are connected by an edge. If the graph is directed, the direction is indicated by drawing an arrow. If the graph is weighted, the weight is added on the arrow.

 

A graph drawing should not be confused with the graph itself (the abstract, non-visual structure) as there are several ways to structure the graph drawing. All that matters is which vertices are connected to which others by how many edges and not the exact layout. In practice, it is often difficult to decide if two drawings represent the same graph. Depending on the problem domain some layouts may be better suited and easier to understand than others.

 

The pioneering work of [W. T. Tutte](./W._T._Tutte) was very influential on the subject of graph drawing. Among other achievements, he introduced the use of linear algebraic methods to obtain graph drawings.

 

Graph drawing also can be said to encompass problems that deal with the [crossing number](./Crossing_number_(graph_theory)) and its various generalizations. The crossing number of a graph is the minimum number of intersections between edges that a drawing of the graph in the plane must contain. For a [planar graph](./Planar_graph), the crossing number is zero by definition. Drawings on surfaces other than the plane are also studied.

 

There are other techniques to visualize a graph away from vertices and edges, including [circle packings](./Circle_packing_theorem), [intersection graph](./Intersection_graph), and other visualizations of the [adjacency matrix](./Adjacency_matrix).

 

### Tabular: Graph data structures

 Main article: [Graph (abstract data type)](./Graph_(abstract_data_type)) 

The tabular representation lends itself well to computational applications. There are different ways to store graphs in a computer system. The [data structure](./Data_structure) used depends on both the graph structure and the [algorithm](./Algorithm) used for manipulating the graph. Theoretically one can distinguish between list and matrix structures but in concrete applications the best structure is often a combination of both. List structures are often preferred for [sparse graphs](./Sparse_graph) as they have smaller memory requirements. [Matrix](./Matrix_(mathematics)) structures on the other hand provide faster access for some applications but can consume huge amounts of memory. Implementations of sparse matrix structures that are efficient on modern parallel computer architectures are an object of current investigation.[[72]](./Graph_theory#cite_note-72)

 

List structures include the [edge list](./Edge_list), an array of pairs of vertices, and the [adjacency list](./Adjacency_list), which separately lists the neighbors of each vertex: Much like the edge list, each vertex has a list of which vertices it is adjacent to.

 

Matrix structures include the [incidence matrix](./Incidence_matrix), a matrix of 0's and 1's whose rows represent vertices and whose columns represent edges, and the [adjacency matrix](./Adjacency_matrix), in which both the rows and columns are indexed by vertices. In both cases a 1 indicates two adjacent objects and a 0 indicates two non-adjacent objects. The [degree matrix](./Degree_matrix) indicates the degree of vertices. The [Laplacian matrix](./Laplacian_matrix) is a modified form of the adjacency matrix that incorporates information about the [degrees](./Degree_(graph_theory)) of the vertices, and is useful in some calculations such as [Kirchhoff's theorem](./Kirchhoff's_theorem) on the number of [spanning trees](./Spanning_tree) of a graph.
The [distance matrix](./Distance_matrix), like the adjacency matrix, has both its rows and columns indexed by vertices, but rather than containing a 0 or a 1 in each cell it contains the length of a [shortest path](./Shortest_path) between two vertices.

 

## Problems

 

### Enumeration

 

There is a large literature on [graphical enumeration](./Graphical_enumeration): the problem of counting graphs meeting specified conditions. Some of this work is found in Harary and Palmer (1973).

 

### Subgraphs, induced subgraphs, and minors

 

A common problem, called the [subgraph isomorphism problem](./Subgraph_isomorphism_problem), is finding a fixed graph as a [subgraph](./Glossary_of_graph_theory#Subgraphs) in a given graph. One reason to be interested in such a question is that many [graph properties](./Graph_properties) are *hereditary* for subgraphs, which means that a graph has the property if and only if all subgraphs have it too.
Finding maximal subgraphs of a certain kind is often an [NP-complete problem](./NP-complete_problem). For example:

 
- Finding the largest complete subgraph is called the [clique problem](./Clique_problem) (NP-complete).

 

One special case of subgraph isomorphism is the [graph isomorphism problem](./Graph_isomorphism_problem). It asks whether two graphs are isomorphic. It is not known whether this problem is NP-complete, nor whether it can be solved in polynomial time.

 

A similar problem is finding [induced subgraphs](./Induced_subgraph) in a given graph. Again, some important graph properties are hereditary with respect to induced subgraphs, which means that a graph has a property if and only if all induced subgraphs also have it. Finding maximal induced subgraphs of a certain kind is also often NP-complete. For example:

 
- Finding the largest edgeless induced subgraph or [independent set](./Independent_set_(graph_theory)) is called the [independent set problem](./Independent_set_problem) (NP-complete).

 

Still another such problem, the minor containment problem, is to find a fixed graph as a minor of a given graph. A [minor](./Minor_(graph_theory)) or subcontraction of a graph is any graph obtained by taking a subgraph and contracting some (or no) edges. Many graph properties are hereditary for minors, which means that a graph has a property if and only if all minors have it too. For example, [Wagner's Theorem](./Wagner's_theorem) states: 

 
- A graph is [planar](./Planar_graph) if it contains as a minor neither the [complete bipartite graph](./Complete_bipartite_graph) *K*3,3 (see the [Three-cottage problem](./Three-cottage_problem)) nor the complete graph *K*5.

 

A similar problem, the subdivision containment problem, is to find a fixed graph as a [subdivision](./Subdivision_(graph_theory)) of a given graph. A [subdivision](./Subdivision_(graph_theory)) or [homeomorphism](./Homeomorphism_(graph_theory)) of a graph is any graph obtained by subdividing some (or no) edges. Subdivision containment is related to graph properties such as [planarity](./Planarity_(graph_theory)). For example, [Kuratowski's Theorem](./Kuratowski's_theorem) states:

 
- A graph is [planar](./Planar_graph) if it contains as a subdivision neither the [complete bipartite graph](./Complete_bipartite_graph) *K*3,3 nor the [complete graph](./Complete_graph) *K*5.

 

Another problem in subdivision containment is the [Kelmans–Seymour conjecture](./Kelmans–Seymour_conjecture):

 
- Every [5-vertex-connected](./K-vertex-connected_graph) graph that is not [planar](./Planar_graph) contains a [subdivision](./Homeomorphism_(graph_theory)) of the 5-vertex [complete graph](./Complete_graph) *K*5.

 

Another class of problems has to do with the extent to which various species and generalizations of graphs are determined by their *point-deleted subgraphs*. For example:

 
- The [reconstruction conjecture](./Reconstruction_conjecture)

 

### Graph coloring

 Main article: [Graph coloring](./Graph_coloring) 

Many problems and theorems in graph theory have to do with various ways of coloring graphs. Typically, one is interested in coloring a graph so that no two adjacent vertices have the same color, or with other similar restrictions. One may also consider coloring edges (possibly so that no two coincident edges are the same color), or other variations. Among the famous results and conjectures concerning graph coloring are the following:

 
- [Four-color theorem](./Four-color_theorem)
- [Strong perfect graph theorem](./Strong_perfect_graph_theorem)
- [Erdős–Faber–Lovász conjecture](./Erdős–Faber–Lovász_conjecture)
- [Total coloring conjecture](./Total_coloring), also called [Behzad](./Mehdi_Behzad)'s conjecture (unsolved)
- [List coloring conjecture](./List_edge-coloring) (unsolved)
- [Hadwiger conjecture (graph theory)](./Hadwiger_conjecture_(graph_theory)) (unsolved)

 

### Subsumption and unification

 

Constraint modeling theories concern families of directed graphs related by a [partial order](./Partial_order). In these applications, graphs are ordered by specificity, meaning that more constrained graphs—which are more specific and thus contain a greater amount of information—are subsumed by those that are more general. Operations between graphs include evaluating the direction of a subsumption relationship between two graphs, if any, and computing graph unification. The unification of two argument graphs is defined as the most general graph (or the computation thereof) that is consistent with (i.e. contains all of the information in) the inputs, if such a graph exists; efficient unification algorithms are known.

 

For constraint frameworks which are strictly [compositional](./Principle_of_Compositionality), graph unification is the sufficient satisfiability and combination function. Well-known applications include [automatic theorem proving](./Automatic_theorem_prover) and modeling the [elaboration of linguistic structure](./Parsing).

 

### Route problems

 
- [Hamiltonian path problem](./Hamiltonian_path_problem)
- [Minimum spanning tree](./Minimum_spanning_tree)
- [Route inspection problem](./Route_inspection_problem) (also called the "Chinese postman problem")
- [Seven bridges of Königsberg](./Seven_bridges_of_Königsberg)
- [Shortest path problem](./Shortest_path_problem)
- [Steiner tree](./Steiner_tree)
- [Three-cottage problem](./Three-cottage_problem)
- [Traveling salesman problem](./Traveling_salesman_problem) (NP-hard)

 

### Network flow

 

There are numerous problems arising especially from applications that have to do with various notions of [flows in networks](./Flow_network), for example:

 
- [Max flow min cut theorem](./Max_flow_min_cut_theorem)

 

### Visibility problems

 
- [Museum guard problem](./Museum_guard_problem)

 

### Covering problems

 

[Covering problems](./Covering_problem) in graphs may refer to various [set cover problems](./Set_cover_problem) on subsets of vertices/subgraphs.

 
- [Dominating set](./Dominating_set) problem is the special case of set cover problem where sets are the closed [neighborhoods](./Neighbourhood_(graph_theory)).
- [Vertex cover problem](./Vertex_cover_problem) is the special case of set cover problem where sets to cover are every edges.
- The original set cover problem, also called hitting set, can be described as a vertex cover in a hypergraph.

 

### Decomposition problems

 

Decomposition, defined as partitioning the edge set of a graph (with as many vertices as necessary accompanying the edges of each part of the partition), has a wide variety of questions. Often, the problem is to decompose a graph into subgraphs isomorphic to a fixed graph; for instance, decomposing a complete graph into Hamiltonian cycles. Other problems specify a family of graphs into which a given graph should be decomposed, for instance, a family of cycles, or decomposing a complete graph *K**n* into *n* − 1 specified trees having, respectively, 1, 2, 3, ..., *n* − 1 edges.

 

Some specific decomposition problems and similar problems that have been studied include:

 
- [Arboricity](./Arboricity), a decomposition into as few forests as possible
- [Cycle double cover](./Cycle_double_cover), a collection of cycles covering each edge exactly twice
- [Edge coloring](./Edge_coloring), a decomposition into as few [matchings](./Matching_(graph_theory)) as possible
- [Graph factorization](./Graph_factorization), a decomposition of a [regular graph](./Regular_graph) into regular subgraphs of given degrees

 

### Graph classes

 

Many problems involve characterizing the members of various classes of graphs. Some examples of such questions are below:

 
- [Enumerating](./Graph_enumeration) the members of a class
- Characterizing a class in terms of [forbidden substructures](./Forbidden_graph_characterization)
- Ascertaining relationships among classes (e.g. does one property of graphs imply another)
- Finding efficient [algorithms](./Algorithm) to [decide](./Decision_problem) membership in a class
- Finding [representations](./Representation_(mathematics)) for members of a class

 

## See also

 
- [Gallery of named graphs](./Gallery_of_named_graphs)
- [Glossary of graph theory](./Glossary_of_graph_theory)
- [List of graph theory topics](./List_of_graph_theory_topics)
- [List of unsolved problems in graph theory](./List_of_unsolved_problems_in_graph_theory)
- [Publications in graph theory](./List_of_publications_in_mathematics#Graph_theory)
- [Graph algorithm](./Graph_algorithm)
- [Graph theorists](./Category:Graph_theorists)

 

## Notes

 
1. [↑](./Graph_theory#cite_ref-FOOTNOTEMoharThomassen2001_1-0) [Mohar & Thomassen (2001)](./Graph_theory#CITEREFMoharThomassen2001).
2. [↑](./Graph_theory#cite_ref-FOOTNOTESylvester1878_2-0) [Sylvester (1878)](./Graph_theory#CITEREFSylvester1878).
3. [↑](./Graph_theory#cite_ref-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage1_1]_3-0) [Ore (1962)](./Graph_theory#CITEREFOre1962), p. [1](https://archive.org/details/theoryofgraphs0000orey/page/1).
4. [↑](./Graph_theory#cite_ref-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage2_2]_4-0) [Ore (1962)](./Graph_theory#CITEREFOre1962), p. [2](https://archive.org/details/theoryofgraphs0000orey/page/2).
5. [↑](./Graph_theory#cite_ref-FOOTNOTEOre1962[httpsarchiveorgdetailstheoryofgraphs0000oreypage3_3]_5-0) [Ore (1962)](./Graph_theory#CITEREFOre1962), p. [3](https://archive.org/details/theoryofgraphs0000orey/page/3).
6. [↑](./Graph_theory#cite_ref-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA7_7]_6-0) [Bollobas (2013)](./Graph_theory#CITEREFBollobas2013), p. [7](http://books.google.com/books?id=JeIlBQAAQBAJ&pg=PA7).
7. [↑](./Graph_theory#cite_ref-FOOTNOTEBiggsLloydWilson1986[httpsbooksgooglecombooksidXqYTk0sXmpoCpgPA2_2–3]_7-0) [Biggs, Lloyd & Wilson (1986)](./Graph_theory#CITEREFBiggsLloydWilson1986), pp. [2–3](https://books.google.com/books?id=XqYTk0sXmpoC&pg=PA2).
8. [↑](./Graph_theory#cite_ref-FOOTNOTEBiggsLloydWilson1986[httpsbooksgooglecombooksidXqYTk0sXmpoCpgPA21_21–22]_8-0) [Biggs, Lloyd & Wilson (1986)](./Graph_theory#CITEREFBiggsLloydWilson1986), pp. [21–22](https://books.google.com/books?id=XqYTk0sXmpoC&pg=PA21).
9. [↑](./Graph_theory#cite_ref-9) 
- [Cauchy (1813)](./Graph_theory#CITEREFCauchy1813)
- [L'Huillier (1812–1813)](./Graph_theory#CITEREFL'Huillier1812–1813)

10. [↑](./Graph_theory#cite_ref-FOOTNOTERicheson200863_10-0) [Richeson (2008)](./Graph_theory#CITEREFRicheson2008), p. 63.
11. [1](./Graph_theory#cite_ref-FOOTNOTECayley1875_11-0) [2](./Graph_theory#cite_ref-FOOTNOTECayley1875_11-1) [Cayley (1875)](./Graph_theory#CITEREFCayley1875).
12. [↑](./Graph_theory#cite_ref-FOOTNOTETutte2001[httpsbooksgooglecombooksiduTGhooU37h4CpgPA30_30]_12-0) [Tutte (2001)](./Graph_theory#CITEREFTutte2001), p. [30](https://books.google.com/books?id=uTGhooU37h4C&pg=PA30).
13. [↑](./Graph_theory#cite_ref-FOOTNOTEGardner1992203_13-0) [Gardner (1992)](./Graph_theory#CITEREFGardner1992), p. 203.
14. [↑](./Graph_theory#cite_ref-FOOTNOTESociety_for_Industrial_and_Applied_Mathematics200226_14-0) [Society for Industrial and Applied Mathematics (2002)](./Graph_theory#CITEREFSociety_for_Industrial_and_Applied_Mathematics2002), p. 26.
15. [↑](./Graph_theory#cite_ref-15) Heinrich Heesch: Untersuchungen zum Vierfarbenproblem. Mannheim: Bibliographisches Institut 1969.
16. [↑](./Graph_theory#cite_ref-AA1_16-0) Appel, K.; Haken, W. (1977), ["Every planar map is four colorable. Part I. Discharging"](https://projecteuclid.org/journals/illinois-journal-of-mathematics/volume-21/issue-3/Every-planar-map-is-four-colorable-Part-I-Discharging/10.1215/ijm/1256049011.pdf) (PDF), *Illinois J. Math.*, **21** (3): 429–490, [doi](./Doi_(identifier)):[10.1215/ijm/1256049011](https://doi.org/10.1215%2Fijm%2F1256049011).
17. [↑](./Graph_theory#cite_ref-AA2_17-0) Appel, K.; Haken, W. (1977), "Every planar map is four colorable. Part II. Reducibility", *Illinois J. Math.*, **21** (3): 491–567, [doi](./Doi_(identifier)):[10.1215/ijm/1256049012](https://doi.org/10.1215%2Fijm%2F1256049012).
18. [↑](./Graph_theory#cite_ref-RSST_18-0) Robertson, N.; Sanders, D.; Seymour, P.; Thomas, R. (1997), "The four color theorem", *Journal of Combinatorial Theory, Series B*, **70**: 2–44, [doi](./Doi_(identifier)):[10.1006/jctb.1997.1750](https://doi.org/10.1006%2Fjctb.1997.1750).
19. [1](./Graph_theory#cite_ref-FOOTNOTEBollobás2001[httpbooksgooglecombooksido9WecWgilzYCpgPR10_xi]_19-0) [2](./Graph_theory#cite_ref-FOOTNOTEBollobás2001[httpbooksgooglecombooksido9WecWgilzYCpgPR10_xi]_19-1) [Bollobás (2001)](./Graph_theory#CITEREFBollobás2001), p. [xi](http://books.google.com/books?id=o9WecWgilzYC&pg=PR10).
20. [↑](./Graph_theory#cite_ref-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA1_1]_20-0) [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), p. [1](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PA1).
21. [↑](./Graph_theory#cite_ref-21) 
- [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), [Contents](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PR9)
- [Beineke & Wilson (2009)](./Graph_theory#CITEREFBeinekeWilson2009), Contents

22. [1](./Graph_theory#cite_ref-FOOTNOTELovász200676_22-0) [2](./Graph_theory#cite_ref-FOOTNOTELovász200676_22-1) [Lovász (2006)](./Graph_theory#CITEREFLovász2006), p. 76.
23. [↑](./Graph_theory#cite_ref-FOOTNOTEPersinger1966_23-0) [Persinger (1966)](./Graph_theory#CITEREFPersinger1966).
24. [↑](./Graph_theory#cite_ref-FOOTNOTELovász200677_24-0) [Lovász (2006)](./Graph_theory#CITEREFLovász2006), p. 77.
25. [↑](./Graph_theory#cite_ref-FOOTNOTELovász200678Theorem_4_25-0) [Lovász (2006)](./Graph_theory#CITEREFLovász2006), p. 78, Theorem 4.
26. [↑](./Graph_theory#cite_ref-FOOTNOTEFoulds1992[httpsbooksgooglecombooksid5G4QBwAAQBAJpgPA71_71]_26-0) [Foulds (1992)](./Graph_theory#CITEREFFoulds1992), p. [71](https://books.google.com/books?id=5G4QBwAAQBAJ&pg=PA71).
27. [↑](./Graph_theory#cite_ref-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA215_215]_27-0) [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), p. [215](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PA215).
28. [↑](./Graph_theory#cite_ref-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA57_57]_28-0) [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), p. [57](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PA57).
29. [↑](./Graph_theory#cite_ref-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA72_72]_29-0) [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), p. [72](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PA72).
30. [↑](./Graph_theory#cite_ref-30) 
- [Cvetković & Rowlinson (2004)](./Graph_theory#CITEREFCvetkovićRowlinson2004), p. [88](https://books.google.com/books?id=z2K26gZLC1MC&pg=PA88)
- [Kaveh (2013)](./Graph_theory#CITEREFKaveh2013), pp. [27–28](http://books.google.com/books?id=oV9GAAAAQBAJ&pg=PA27)

31. [↑](./Graph_theory#cite_ref-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA115_Chapter_15:_Automorphisms_of_graphs]_31-0) [Biggs (1993)](./Graph_theory#CITEREFBiggs1993), [Chapter 15: Automorphisms of graphs](http://books.google.com/books?id=6TasRmIFOxQC&pg=PA115).
32. [1](./Graph_theory#cite_ref-FOOTNOTEGodsilRoyle2001[httpbooksgooglecombooksidGeSPBAAAQBAJpgPR12_xii–ixi]_32-0) [2](./Graph_theory#cite_ref-FOOTNOTEGodsilRoyle2001[httpbooksgooglecombooksidGeSPBAAAQBAJpgPR12_xii–ixi]_32-1) [Godsil & Royle (2001)](./Graph_theory#CITEREFGodsilRoyle2001), pp. [xii–ixi](http://books.google.com/books?id=GeSPBAAAQBAJ&pg=PR12).
33. [↑](./Graph_theory#cite_ref-FOOTNOTEGrossTucker2012[httpsbooksgooglecombooksid6HmA_x0dL9oCpgPA70_70]_33-0) [Gross & Tucker (2012)](./Graph_theory#CITEREFGrossTucker2012), p. [70](https://books.google.com/books?id=6HmA_x0dL9oC&pg=PA70).
34. [↑](./Graph_theory#cite_ref-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA64_64]_34-0) [Biggs (1993)](./Graph_theory#CITEREFBiggs1993), p. [64](http://books.google.com/books?id=6TasRmIFOxQC&pg=PA64).
35. [↑](./Graph_theory#cite_ref-FOOTNOTEBiggs1993[httpbooksgooglecombooksid6TasRmIFOxQCpgPA98_98]_35-0) [Biggs (1993)](./Graph_theory#CITEREFBiggs1993), p. [98](http://books.google.com/books?id=6TasRmIFOxQC&pg=PA98).
36. [↑](./Graph_theory#cite_ref-FOOTNOTEPach2018[httpbooksgooglecombooksid9mlQDwAAQBAJpgPA257_257]_36-0) [Pach (2018)](./Graph_theory#CITEREFPach2018), p. [257](http://books.google.com/books?id=9mlQDwAAQBAJ&pg=PA257).
37. [1](./Graph_theory#cite_ref-FOOTNOTEBounceurBezouiEuler2019[httpbooksgooglecombooksidUmYIEQAAQBAJpgPA13_13–14]_37-0) [2](./Graph_theory#cite_ref-FOOTNOTEBounceurBezouiEuler2019[httpbooksgooglecombooksidUmYIEQAAQBAJpgPA13_13–14]_37-1) [Bounceur, Bezoui & Euler (2019)](./Graph_theory#CITEREFBounceurBezouiEuler2019), pp. [13–14](http://books.google.com/books?id=UmYIEQAAQBAJ&pg=PA13).
38. [↑](./Graph_theory#cite_ref-38) 
- [Everett & Corneil (1995)](./Graph_theory#CITEREFEverettCorneil1995)
- [Ziegler (2007)](./Graph_theory#CITEREFZiegler2007), pp. 628–642

39. [1](./Graph_theory#cite_ref-FOOTNOTEMcKeeMcMorris1999[httpbooksgooglecombooksidphWjyYLP7d4CpgPA1_1&ndash;2]_39-0) [2](./Graph_theory#cite_ref-FOOTNOTEMcKeeMcMorris1999[httpbooksgooglecombooksidphWjyYLP7d4CpgPA1_1&ndash;2]_39-1) [McKee & McMorris (1999)](./Graph_theory#CITEREFMcKeeMcMorris1999), p. [1–2](http://books.google.com/books?id=phWjyYLP7d4C&pg=PA1).
40. [1](./Graph_theory#cite_ref-FOOTNOTEGrünbaum2006[httpsbooksgooglecombooksidcKpBGcqpspICpgPA181_181]_40-0) [2](./Graph_theory#cite_ref-FOOTNOTEGrünbaum2006[httpsbooksgooglecombooksidcKpBGcqpspICpgPA181_181]_40-1) [Grünbaum (2006)](./Graph_theory#CITEREFGrünbaum2006), p. [181](https://books.google.com/books?id=cKpBGcqpspIC&pg=PA181).
41. [↑](./Graph_theory#cite_ref-FOOTNOTEEverettCorneil1995_41-0) [Everett & Corneil (1995)](./Graph_theory#CITEREFEverettCorneil1995).
42. [↑](./Graph_theory#cite_ref-FOOTNOTEZiegler2007628–642_42-0) [Ziegler (2007)](./Graph_theory#CITEREFZiegler2007), pp. 628–642.
43. [↑](./Graph_theory#cite_ref-43) 
- [Brightwell & Scheinerman (1993)](./Graph_theory#CITEREFBrightwellScheinerman1993), p. 214
- [Thurston (2002)](./Graph_theory#CITEREFThurston2002), p. 330, Corollary 13.6.2.

44. [↑](./Graph_theory#cite_ref-FOOTNOTEChalopinGonçalves2009_44-0) [Chalopin & Gonçalves (2009)](./Graph_theory#CITEREFChalopinGonçalves2009).
45. [↑](./Graph_theory#cite_ref-FOOTNOTEDi_BattistaEadesTamassiaTollis1994viii_45-0) [Di Battista et al. (1994)](./Graph_theory#CITEREFDi_BattistaEadesTamassiaTollis1994), p. viii.
46. [↑](./Graph_theory#cite_ref-FOOTNOTEDi_BattistaEadesTamassiaTollis199414_46-0) [Di Battista et al. (1994)](./Graph_theory#CITEREFDi_BattistaEadesTamassiaTollis1994), p. 14.
47. [↑](./Graph_theory#cite_ref-FOOTNOTEDi_BattistaEadesTamassiaTollis199416_47-0) [Di Battista et al. (1994)](./Graph_theory#CITEREFDi_BattistaEadesTamassiaTollis1994), p. 16.
48. [1](./Graph_theory#cite_ref-FOOTNOTEPachSharir2009_48-0) [2](./Graph_theory#cite_ref-FOOTNOTEPachSharir2009_48-1) [Pach & Sharir (2009)](./Graph_theory#CITEREFPachSharir2009).
49. [↑](./Graph_theory#cite_ref-FOOTNOTEMalitzPapakostas1994_49-0) [Malitz & Papakostas (1994)](./Graph_theory#CITEREFMalitzPapakostas1994).
50. [↑](./Graph_theory#cite_ref-FOOTNOTEChartrandJordonVatterZhang2024[httpbooksgooglecombooksid01cIEQAAQBAJpgPA221_221]_50-0) [Chartrand et al. (2024)](./Graph_theory#CITEREFChartrandJordonVatterZhang2024), p. [221](http://books.google.com/books?id=01cIEQAAQBAJ&pg=PA221).
51. [↑](./Graph_theory#cite_ref-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA104_104]_51-0) [Bollobas (2013)](./Graph_theory#CITEREFBollobas2013), p. [104](http://books.google.com/books?id=JeIlBQAAQBAJ&pg=PA104).
52. [↑](./Graph_theory#cite_ref-FOOTNOTEBollobas2013[httpbooksgooglecombooksidJeIlBQAAQBAJpgPA123_123]_52-0) [Bollobas (2013)](./Graph_theory#CITEREFBollobas2013), p. [123](http://books.google.com/books?id=JeIlBQAAQBAJ&pg=PA123).
53. [↑](./Graph_theory#cite_ref-53) 
- [Zhao (2023)](./Graph_theory#CITEREFZhao2023), p. [135](http://books.google.com/books?id=QDHEEAAAQBAJ&pg=PA135)
- [Borgs et al. (2008)](./Graph_theory#CITEREFBorgsChayesLovászSós2008)
- [Hahn & Tardif (1997)](./Graph_theory#CITEREFHahnTardif1997), p. [108–109](http://books.google.com/books?id=-tIaXdII8egC&pg=PA108)

54. [↑](./Graph_theory#cite_ref-FOOTNOTEWilson1996_54-0) [Wilson (1996)](./Graph_theory#CITEREFWilson1996).
55. [↑](./Graph_theory#cite_ref-FOOTNOTESedgewickFlajolet2013286_55-0) [Sedgewick & Flajolet (2013)](./Graph_theory#CITEREFSedgewickFlajolet2013), p. 286.
56. [↑](./Graph_theory#cite_ref-FOOTNOTEMorin2004_56-0) [Morin (2004)](./Graph_theory#CITEREFMorin2004). sfnp error: no target: CITEREFMorin2004 ([help](./Category:Harv_and_Sfn_template_errors))
57. [↑](./Graph_theory#cite_ref-FOOTNOTEMcDiarmidJohnsonStone1997_57-0) [McDiarmid, Johnson & Stone (1997)](./Graph_theory#CITEREFMcDiarmidJohnsonStone1997).
58. [↑](./Graph_theory#cite_ref-58) Hale, Scott A. (2014). "Multilinguals and Wikipedia editing". *Proceedings of the 2014 ACM conference on Web science*. pp. 99–108. [arXiv](./ArXiv_(identifier)):[1312.0976](https://arxiv.org/abs/1312.0976). [Bibcode](./Bibcode_(identifier)):[2013arXiv1312.0976H](https://ui.adsabs.harvard.edu/abs/2013arXiv1312.0976H). [doi](./Doi_(identifier)):[10.1145/2615569.2615684](https://doi.org/10.1145%2F2615569.2615684). [ISBN](./ISBN_(identifier)) [978-1-4503-2622-3](./Special:BookSources/978-1-4503-2622-3). [S2CID](./S2CID_(identifier)) [14027025](https://api.semanticscholar.org/CorpusID:14027025).
59. [↑](./Graph_theory#cite_ref-59) Mashaghi, A.; et al. (2004). "Investigation of a protein complex network". *European Physical Journal B*. **41** (1): 113–121. [arXiv](./ArXiv_(identifier)):[cond-mat/0304207](https://arxiv.org/abs/cond-mat/0304207). [Bibcode](./Bibcode_(identifier)):[2004EPJB...41..113M](https://ui.adsabs.harvard.edu/abs/2004EPJB...41..113M). [doi](./Doi_(identifier)):[10.1140/epjb/e2004-00301-0](https://doi.org/10.1140%2Fepjb%2Fe2004-00301-0). [S2CID](./S2CID_(identifier)) [9233932](https://api.semanticscholar.org/CorpusID:9233932).
60. [↑](./Graph_theory#cite_ref-60) Shah, Preya; Ashourvan, Arian; Mikhail, Fadi; Pines, Adam; Kini, Lohith; Oechsel, Kelly; Das, Sandhitsu R; Stein, Joel M; Shinohara, Russell T (2019-07-01). ["Characterizing the role of the structural connectome in seizure dynamics"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6598625). *Brain*. **142** (7): 1955–1972. [doi](./Doi_(identifier)):[10.1093/brain/awz125](https://doi.org/10.1093%2Fbrain%2Fawz125). [ISSN](./ISSN_(identifier)) [0006-8950](https://search.worldcat.org/issn/0006-8950). [PMC](./PMC_(identifier)) [6598625](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6598625). [PMID](./PMID_(identifier)) [31099821](https://pubmed.ncbi.nlm.nih.gov/31099821).
61. [↑](./Graph_theory#cite_ref-61) Adali, Tulay; Ortega, Antonio (May 2018). "Applications of Graph Theory [Scanning the Issue]". *Proceedings of the IEEE*. **106** (5): 784–786. [doi](./Doi_(identifier)):[10.1109/JPROC.2018.2820300](https://doi.org/10.1109%2FJPROC.2018.2820300). [ISSN](./ISSN_(identifier)) [0018-9219](https://search.worldcat.org/issn/0018-9219).
62. [↑](./Graph_theory#cite_ref-62) Grandjean, Martin (2016). ["A social network analysis of Twitter: Mapping the digital humanities community"](https://hal.archives-ouvertes.fr/hal-01517493/file/A%20social%20network%20analysis%20of%20Twitter%20Mapping%20the%20digital%20humanities%20community.pdf) (PDF). *Cogent Arts & Humanities*. **3** (1) 1171458. [doi](./Doi_(identifier)):[10.1080/23311983.2016.1171458](https://doi.org/10.1080%2F23311983.2016.1171458). [S2CID](./S2CID_(identifier)) [114999767](https://api.semanticscholar.org/CorpusID:114999767).
63. [↑](./Graph_theory#cite_ref-63) Vecchio, F (2017). ""Small World" architecture in brain connectivity and hippocampal volume in Alzheimer's disease: a study via graph theory from EEG data". *Brain Imaging and Behavior*. **11** (2): 473–485. [doi](./Doi_(identifier)):[10.1007/s11682-016-9528-3](https://doi.org/10.1007%2Fs11682-016-9528-3). [PMID](./PMID_(identifier)) [26960946](https://pubmed.ncbi.nlm.nih.gov/26960946). [S2CID](./S2CID_(identifier)) [3987492](https://api.semanticscholar.org/CorpusID:3987492).
64. [↑](./Graph_theory#cite_ref-64) Vecchio, F (2013). "Brain network connectivity assessed using graph theory in frontotemporal dementia". *Neurology*. **81** (2): 134–143. [doi](./Doi_(identifier)):[10.1212/WNL.0b013e31829a33f8](https://doi.org/10.1212%2FWNL.0b013e31829a33f8). [PMID](./PMID_(identifier)) [23719145](https://pubmed.ncbi.nlm.nih.gov/23719145). [S2CID](./S2CID_(identifier)) [28334693](https://api.semanticscholar.org/CorpusID:28334693).
65. [↑](./Graph_theory#cite_ref-65) Bjorken, J. D.; Drell, S. D. (1965). [*Relativistic Quantum Fields*](https://archive.org/details/relativisticquan0000bjor_c5q0). New York: McGraw-Hill. p. viii.
66. [↑](./Graph_theory#cite_ref-66) Kumar, Ankush; Kulkarni, G. U. (2016-01-04). "Evaluating conducting network based transparent electrodes from geometrical considerations". *Journal of Applied Physics*. **119** (1): 015102. [Bibcode](./Bibcode_(identifier)):[2016JAP...119a5102K](https://ui.adsabs.harvard.edu/abs/2016JAP...119a5102K). [doi](./Doi_(identifier)):[10.1063/1.4939280](https://doi.org/10.1063%2F1.4939280). [ISSN](./ISSN_(identifier)) [0021-8979](https://search.worldcat.org/issn/0021-8979).
67. [↑](./Graph_theory#cite_ref-67) Newman, Mark (2010). [*Networks: An Introduction*](https://web.archive.org/web/20200728132820/http://math.sjtu.edu.cn/faculty/xiaodong/course/Networks%20An%20introduction.pdf) (PDF). Oxford University Press. Archived from [the original](http://math.sjtu.edu.cn/faculty/xiaodong/course/Networks%20An%20introduction.pdf) (PDF) on 2020-07-28. Retrieved 2019-10-30.
68. [↑](./Graph_theory#cite_ref-68) Grandjean, Martin (2015). ["Social network analysis and visualization: Moreno's Sociograms revisited"](https://www.martingrandjean.ch/social-network-analysis-visualization-morenos-sociograms-revisited/). Redesigned network strictly based on Moreno (1934), *Who Shall Survive*.
69. [↑](./Graph_theory#cite_ref-69) Rosen, Kenneth H. (2011-06-14). *Discrete mathematics and its applications* (7th ed.). New York: McGraw-Hill. [ISBN](./ISBN_(identifier)) [978-0-07-338309-5](./Special:BookSources/978-0-07-338309-5).
70. [↑](./Graph_theory#cite_ref-70) Kelly, S.; Black, Michael (2020-07-09). ["graphsim: An R package for simulating gene expression data from graph structures of biological pathways"](https://www.biorxiv.org/content/biorxiv/early/2020/06/30/2020.03.02.972471.full.pdf) (PDF). *Journal of Open Source Software*. **5** (51). The Open Journal: 2161. [Bibcode](./Bibcode_(identifier)):[2020JOSS....5.2161K](https://ui.adsabs.harvard.edu/abs/2020JOSS....5.2161K). [bioRxiv](./BioRxiv_(identifier)) [10.1101/2020.03.02.972471](https://doi.org/10.1101%2F2020.03.02.972471). [doi](./Doi_(identifier)):[10.21105/joss.02161](https://doi.org/10.21105%2Fjoss.02161). [ISSN](./ISSN_(identifier)) [2475-9066](https://search.worldcat.org/issn/2475-9066). [S2CID](./S2CID_(identifier)) [214722561](https://api.semanticscholar.org/CorpusID:214722561).
71. [↑](./Graph_theory#cite_ref-71) Shah, Preya; Ashourvan, Arian; Mikhail, Fadi; Pines, Adam; Kini, Lohith; Oechsel, Kelly; Das, Sandhitsu R; Stein, Joel M; Shinohara, Russell T (2019-07-01). ["Characterizing the role of the structural connectome in seizure dynamics"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6598625). *Brain*. **142** (7): 1955–1972. [doi](./Doi_(identifier)):[10.1093/brain/awz125](https://doi.org/10.1093%2Fbrain%2Fawz125). [ISSN](./ISSN_(identifier)) [0006-8950](https://search.worldcat.org/issn/0006-8950). [PMC](./PMC_(identifier)) [6598625](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6598625). [PMID](./PMID_(identifier)) [31099821](https://pubmed.ncbi.nlm.nih.gov/31099821).
72. [↑](./Graph_theory#cite_ref-72) Kepner, Jeremy; Gilbert, John (2011). [*Graph Algorithms in the Language of Linear Algebra*](https://my.siam.org/Store/Product/viewproduct/?ProductId=106663). SIAM. p. 1171458. [ISBN](./ISBN_(identifier)) [978-0-898719-90-1](./Special:BookSources/978-0-898719-90-1).

 

## References

 
- [Lowell W. Beineke](./Lowell_W._Beineke); Bjarne Toft; and [Robin J. Wilson](./Robin_Wilson_(mathematician)): *Milestones in Graph Theory: A Century of Progress*, AMS/MAA, (SPECTRUM, v.108), ISBN 978-1-4704-6431-8 (2025).
- Beineke, Lowell W.; Wilson, Robin J. (2009). [*Topics in Topological Graph Theory*](https://books.google.com/books?id=Z8P3CwAAQBAJ). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-1-139-64368-9](./Special:BookSources/978-1-139-64368-9).
- Bender, Edward A.; Williamson, S. Gill (2010). [*Lists, Decisions and Graphs. With an Introduction to Probability*](https://books.google.com/books?id=vaXv_yhefG8C).
- Berge, Claude (1958). *Théorie des graphes et ses applications*. Paris: Dunod. English edition, Wiley 1961; Methuen & Co, New York 1962; Russian, Moscow 1961; Spanish, Mexico 1962; Roumanian, Bucharest 1969; Chinese, Shanghai 1963; Second printing of the 1962 first English edition, Dover, New York 2001.
- Biggs, Norman (1993). *Algebraic Graph Theory* (2nd ed.). Cambridge University Press.
- Biggs, N.; Lloyd, E.; Wilson, R. (1986). [*Graph Theory, 1736-1936*](./Graph_Theory,_1736–1936). Oxford University Press.
- Bollobas, Bela (2013). [*Modern Graph Theory*](https://books.google.com/books?id=JeIlBQAAQBAJ). Springer. [ISBN](./ISBN_(identifier)) [978-1-4612-0619-4](./Special:BookSources/978-1-4612-0619-4).
- Bollobás, Béla; Riordan, O. M. (2003). *Mathematical results on scale-free random graphs in "Handbook of Graphs and Networks" (S. Bornholdt and H.G. Schuster (eds))* (1st ed.). Weinheim: Wiley VCH.
- Bollobás, B. (2001). [*Random Graphs*](https://books.google.com/books?id=o9WecWgilzYC) (2nd ed.). Cambridge University Press. [ISBN](./ISBN_(identifier)) [0-521-79722-5](./Special:BookSources/0-521-79722-5).
- Bondy, J. A.; Murty, U. S. R. (2008). *Graph Theory*. Springer. [ISBN](./ISBN_(identifier)) [978-1-84628-969-9](./Special:BookSources/978-1-84628-969-9).
- Borgs, Christian; Chayes, Jennifer T.; [Lovász, László](./László_Lovász); [Sós, Vera T](./Vera_Sós); [Vestergombi, Katalin](./Katalin_Vesztergombi) (2008). ["Convergent sequences of dense graphs. I. Subgraph frequencies, metric properties and testing"](https://doi.org/10.1016%2Fj.aim.2008.07.008). *[Advances in Mathematics](./Advances_in_Mathematics)*. **219** (6): 1801–1851. [arXiv](./ArXiv_(identifier)):[math/0702004](https://arxiv.org/abs/math/0702004). [doi](./Doi_(identifier)):[10.1016/j.aim.2008.07.008](https://doi.org/10.1016%2Fj.aim.2008.07.008).
- Bounceur, Ahcene; Bezoui, Madani; Euler, Reinhardt (2019). [*Boundaries and Hulls of Euclidean Graphs: From Theory to Practice*](https://books.google.com/books?id=UmYIEQAAQBAJ). CRC Press. [ISBN](./ISBN_(identifier)) [978-1-351-69028-7](./Special:BookSources/978-1-351-69028-7).
- A. Bretto and  A. Faisant and F.   Hennecart. Elements of Graph Theory: From Basic Concepts to Modern Developments. Ems Textbooks in Mathematics, 25, 2022 .
- [Brightwell, Graham R.](./Graham_Brightwell); [Scheinerman, Edward R.](./Ed_Scheinerman) (1993). "Representations of planar graphs". *[SIAM Journal on Discrete Mathematics](./SIAM_Journal_on_Discrete_Mathematics)*. **6** (2): 214–229. [doi](./Doi_(identifier)):[10.1137/0406017](https://doi.org/10.1137%2F0406017).
- [Cauchy, A. L.](./Augustin-Louis_Cauchy) (1813). "Recherche sur les polyèdres - premier mémoire". *Journal de l'École Polytechnique*. 9 (Cahier 16): 66–86.
- [Cayley, A.](./Augustin-Louis_Cauchy) (1875). ["Ueber die Analytischen Figuren, welche in der Mathematik Bäume genannt werden und ihre Anwendung auf die Theorie chemischer Verbindungen"](https://zenodo.org/record/1425086). *Berichte der Deutschen Chemischen Gesellschaft*. **8** (2): 1056–1059. [doi](./Doi_(identifier)):[10.1002/cber.18750080252](https://doi.org/10.1002%2Fcber.18750080252).
- [Cayley, A.](./Arthur_Cauchy?action=edit&redlink=1) (2009) [1890]. "On the theory of the analytical forms called trees". [*The Collected Mathematical Papers*](https://rcin.org.pl/dlibra/docmetadata?showContent=true&id=173708). Vol. 3. pp. 242–246. [doi](./Doi_(identifier)):[10.1017/CBO9780511703690.046](https://doi.org/10.1017%2FCBO9780511703690.046). [ISBN](./ISBN_(identifier)) [978-0-511-70369-0](./Special:BookSources/978-0-511-70369-0).
- Chalopin, J.; Gonçalves, D. (2009). "Every planar graph is the intersection graph of segments in the plane: Extended abstract". *Proceedings of the forty-first annual ACM symposium on Theory of computing*. pp. 631–638. [doi](./Doi_(identifier)):[10.1145/1536414.1536500](https://doi.org/10.1145%2F1536414.1536500). [ISBN](./ISBN_(identifier)) [978-1-60558-506-2](./Special:BookSources/978-1-60558-506-2).
- Chartrand, Gary (1985). [*Introductory Graph Theory*](https://archive.org/details/introductorygrap0000char). Dover. [ISBN](./ISBN_(identifier)) [0-486-24775-9](./Special:BookSources/0-486-24775-9).
- Chartrand, Gary; Jordon, Heather; Vatter, Vincent; Zhang, Ping (2024). [*Graphs & Digraphs*](https://books.google.com/books?id=01cIEQAAQBAJ). CRC Press. [ISBN](./ISBN_(identifier)) [978-1-003-80108-5](./Special:BookSources/978-1-003-80108-5).
- Cvetković, Dragoš M.; Rowlinson, Peter (2004). "Spectral graph theory". In Beineke, Lowell W.; Wilson, Robin J. (eds.). [*Topics in Algebraic Graph Theory*](https://books.google.com/books?id=z2K26gZLC1MC). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-80197-3](./Special:BookSources/978-0-521-80197-3).
- Deo, Narsingh (1974). [*Graph Theory with Applications to Engineering and Computer Science*](https://www.edutechlearners.com/download/Graphtheory.pdf) (PDF). Englewood, New Jersey: Prentice-Hall. [ISBN](./ISBN_(identifier)) [0-13-363473-6](./Special:BookSources/0-13-363473-6). [Archived](https://web.archive.org/web/20190517165158/http://www.edutechlearners.com/download/Graphtheory.pdf) (PDF) from the original on 2019-05-17.
- Di Battista, Giuseppe; [Eades, Peter](./Peter_Eades); [Tamassia, Roberto](./Roberto_Tamassia); Tollis, Ioannis G. (1994). ["Algorithms for Drawing Graphs: an Annotated Bibliography"](https://doi.org/10.1016%2F0925-7721%2894%2900014-x). *[Computational Geometry: Theory and Applications](./Computational_Geometry_(journal))*. **4** (5): 235–282. [doi](./Doi_(identifier)):[10.1016/0925-7721(94)00014-x](https://doi.org/10.1016%2F0925-7721%2894%2900014-x).
- Everett, Hazel; [Corneil, Derek](./Derek_Corneil) (1995). "Negative results on characterizing visibility graphs". *[Computational Geometry: Theory & Applications](./Computational_Geometry_(journal))*. **5** (2): 51–63. [doi](./Doi_(identifier)):[10.1016/0925-7721(95)00021-Z](https://doi.org/10.1016%2F0925-7721%2895%2900021-Z). [MR](./MR_(identifier)) [1353288](https://mathscinet.ams.org/mathscinet-getitem?mr=1353288).
- Foulds, L. R. (1992). [*Graph Theory Applications*](https://books.google.com/books?id=5G4QBwAAQBAJ). Universitext. Springer. [ISBN](./ISBN_(identifier)) [978-1-4612-0933-1](./Special:BookSources/978-1-4612-0933-1).
- [Gardner, Martin](./Martin_Gardner) (1992), *Fractal Music, Hypercards, and more…Mathematical Recreations from Scientific American*, W. H. Freeman and Company, p. 203
- Gibbons, Alan (1985). *Algorithmic Graph Theory*. [Cambridge University Press](./Cambridge_University_Press).
- Godsil, Chris; Royle, Gordon F. (2001). [*Algebraic Graph Theory*](https://books.google.com/books?id=GeSPBAAAQBAJ). Springer. [ISBN](./ISBN_(identifier)) [978-1-4613-0163-9](./Special:BookSources/978-1-4613-0163-9).
- Golumbic, Martin (1980). *Algorithmic Graph Theory and Perfect Graphs*. [Academic Press](./Academic_Press).
- Gross, J. L.; [Tucker, T. W.](./Thomas_W._Tucker) (2012) [1987]. [*Topological Graph Theory*](https://books.google.com/books?id=6HmA_x0dL9oC). Dover Publications. [ISBN](./ISBN_(identifier)) [978-0-486-41741-7](./Special:BookSources/978-0-486-41741-7).
- [Grünbaum, Branko](./Branko_Grünbaum) (2006). "Configurations of points and lines". *The Coxeter Legacy*. Providence, RI: American Mathematical Society. pp. 179–225. [MR](./MR_(identifier)) [2209028](https://mathscinet.ams.org/mathscinet-getitem?mr=2209028).
- Hahn, Geňa; Tardif, Claude (1997). "Graph homomorphisms: structure and symmetry". In Hahn, Geňa; Sabidussi, Gert (eds.). [*Graph Symmetry: Algebraic Methods and Applications*](https://books.google.com/books?id=-tIaXdII8egC). Kluwer Academic Publisher. [ISBN](./ISBN_(identifier)) [978-0-7923-4668-5](./Special:BookSources/978-0-7923-4668-5).
- Harary, Frank (1969). *Graph Theory*. Reading, Massachusetts: Addison-Wesley.
- Harary, Frank; Palmer, Edgar M. (1973). *Graphical Enumeration*. New York, New York: Academic Press.
- Kaveh, A. (2013). [*Optimal Analysis of Structures by Concepts of Symmetry and Regularity*](https://books.google.com/books?id=oV9GAAAAQBAJ). Springer. [ISBN](./ISBN_(identifier)) [978-3-7091-1565-7](./Special:BookSources/978-3-7091-1565-7).
- Kepner, Jeremy; Gilbert, John (2011). [*Graph Algorithms in The Language of Linear Algebra*](https://my.siam.org/Store/Product/viewproduct/?ProductId=106663). Philadelphia, Pennsylvania: SIAM. [ISBN](./ISBN_(identifier)) [978-0-89871-990-1](./Special:BookSources/978-0-89871-990-1).
- L'Huillier, S.A.J. (1812–1813). "Mémoire sur la polyèdrométrie". *Annales de Mathématiques*. **3**: 169–189.
- [Lovász, László](./László_Lovász) (2006). ["Graph minor theory"](https://doi.org/10.1090%2FS0273-0979-05-01088-8). *[Bulletin of the American Mathematical Society](./Bulletin_of_the_American_Mathematical_Society)*. **43** (1): 75–86. [doi](./Doi_(identifier)):[10.1090/S0273-0979-05-01088-8](https://doi.org/10.1090%2FS0273-0979-05-01088-8).
- Mahadev, N. V. R.; Peled, Uri N. (1995). *Threshold Graphs and Related Topics*. [North-Holland](./North-Holland_Publishing_Company).
- Malitz, Seth; Papakostas, Achilleas (1994). "On the angular resolution of planar graphs". *[SIAM Journal on Discrete Mathematics](./SIAM_Journal_on_Discrete_Mathematics)*. **7** (2): 172–183. [doi](./Doi_(identifier)):[10.1137/S0895480193242931](https://doi.org/10.1137%2FS0895480193242931). [MR](./MR_(identifier)) [1271989](https://mathscinet.ams.org/mathscinet-getitem?mr=1271989).
- McDiarmid, Colin; Johnson, Theodore; Stone, Harold S. (1997). ["On finding a minimum spanning tree in a network with random weights"](http://www.stats.ox.ac.uk/~cstone/mst.pdf) (PDF). *Random Structures & Algorithms*. **10** (1–2): 187–204. [doi](./Doi_(identifier)):[10.1002/(SICI)1098-2418(199701/03)10:1/2<187::AID-RSA10>3.3.CO;2-Y](https://doi.org/10.1002%2F%28SICI%291098-2418%28199701%2F03%2910%3A1%2F2%3C187%3A%3AAID-RSA10%3E3.3.CO%3B2-Y). [MR](./MR_(identifier)) [1611522](https://mathscinet.ams.org/mathscinet-getitem?mr=1611522).
- McKee, Terry A.; McMorris, F. R. (1999). [*Topics in Intersection Graph Theory*](https://books.google.com/books?id=phWjyYLP7d4C). [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics). [ISBN](./ISBN_(identifier)) [978-0-89871-430-2](./Special:BookSources/978-0-89871-430-2).
- [Mohar, Bojan](./Bojan_Mohar); [Thomassen, Carsten](./Carsten_Thomassen_(mathematician)) (2001). [*Graphs on Surfaces*](https://www.press.jhu.edu/books/title/1675/graphs-surfaces). Johns Hopkins University Press. [ISBN](./ISBN_(identifier)) [978-0-8018-6689-0](./Special:BookSources/978-0-8018-6689-0). [OCLC](./OCLC_(identifier)) [45102952](https://search.worldcat.org/oclc/45102952).
- [Morin, Pat](./Pat_Morin) (March 22, 2014). "Chapter 7: Random Binary Search Trees". [*Open Data Structures (in pseudocode)*](https://opendatastructures.org/ods-python.pdf) (PDF) (0.1Gβ ed.). pp. 145–164.
- Newman, Mark (2010). *Networks: An Introduction*. Oxford University Press.
- [Ore, Øystein](./Øystein_Ore) (1962). [*Theory of Graphs*](https://archive.org/details/theoryofgraphs0000orey). American Mathematical Society.
- Pach, János (2018). "Geometric Graph Theory". In Toth, Csaba D.; O'Rourke, Joseph; Goodman, Jacob E. (eds.). *Handbook of Discrete and Computational Geometry* (3rd ed.). CRC Press.
- [Pach, János](./János_Pach); [Sharir, Micha](./Micha_Sharir) (2009). "5.5 Angular resolution and slopes". *Combinatorial Geometry and Its Algorithmic Applications: The Alcalá Lectures*. Mathematical Surveys and Monographs. Vol. 152. [American Mathematical Society](./American_Mathematical_Society). pp. 126–127.
- Persinger, C. A. (1966). ["Subsets of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)-books in      E  3     {\displaystyle E^{3}}  ![{\displaystyle E^{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ab83515bfb94cf95187779f517841793ac61ee5d)"](https://doi.org/10.2140%2Fpjm.1966.18.169). *[Pacific Journal of Mathematics](./Pacific_Journal_of_Mathematics)*. **18**: 169–173. [doi](./Doi_(identifier)):[10.2140/pjm.1966.18.169](https://doi.org/10.2140%2Fpjm.1966.18.169). [MR](./MR_(identifier)) [0195077](https://mathscinet.ams.org/mathscinet-getitem?mr=0195077).
- [Richeson, D.](./David_Richeson) (2008). [*Euler's Gem: The Polyhedron Formula and the Birth of Topology*](./Euler's_Gem). Princeton University Press.
- [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); [Flajolet, Philippe](./Philippe_Flajolet) (2013). "Chapter 6: Trees". *An Introduction to the Analysis of Algorithms* (2nd ed.). Addison-Wesley. [ISBN](./ISBN_(identifier)) [9780133373486](./Special:BookSources/9780133373486).
- "The George Polya Prize". [*Looking Back, Looking Ahead: A SIAM History*](https://web.archive.org/web/20160305010030/http://www.siam.org/about/more/siam50.pdf) (PDF). [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics). 2002. p. 26. Archived from [the original](http://www.siam.org/about/more/siam50.pdf) (PDF) on 2016-03-05. Retrieved 2016-03-14.
- [Sylvester, James Joseph](./James_Joseph_Sylvester) (1878). ["Chemistry and Algebra"](https://archive.org/stream/nature15unkngoog#page/n312/mode/1up). *Nature*. **17** (432): 284. [Bibcode](./Bibcode_(identifier)):[1878Natur..17..284S](https://ui.adsabs.harvard.edu/abs/1878Natur..17..284S). [doi](./Doi_(identifier)):[10.1038/017284a0](https://doi.org/10.1038%2F017284a0).
- [Thurston, William](./William_Thurston) (March 2002). "§13.6, Andreev's theorem and generalizations, and §13.7, Constructing patterns of circles". [*The Geometry and Topology of 3-manifolds*](https://library.slmath.org/nonmsri/gt3m/). MSRI Publications. pp. 330–346. Electronic version 1.1. Retrieved 2025-12-09.
- [Tutte, W. T.](./W._T._Tutte) (2001). [*Graph Theory*](https://books.google.com/books?id=uTGhooU37h4C). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-79489-3](./Special:BookSources/978-0-521-79489-3).
- Wilson, David Bruce (1996). "Generating random spanning trees more quickly than the cover time". [*Proceedings of the Twenty-Eighth Annual ACM Symposium on the Theory of Computing (STOC 1996)*](./Symposium_on_Theory_of_Computing). pp. 296–303. [doi](./Doi_(identifier)):[10.1145/237814.237880](https://doi.org/10.1145%2F237814.237880). [ISBN](./ISBN_(identifier)) [0-89791-785-5](./Special:BookSources/0-89791-785-5). [MR](./MR_(identifier)) [1427525](https://mathscinet.ams.org/mathscinet-getitem?mr=1427525).
- Zhao, Yufei (2023). [*Graph Theory and Additive Combinatorics: Exploring Structure and Randomness*](https://books.google.com/books?id=QDHEEAAAQBAJ). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-1-009-31094-9](./Special:BookSources/978-1-009-31094-9).
- [Ziegler, Günter M.](./Günter_M._Ziegler) (2007). "Convex polytopes: extremal constructions and     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61)-vector shapes. Section 1.3: Steinitz's theorem via circle packings". In Miller, Ezra; Reiner, Victor; [Sturmfels, Bernd](./Bernd_Sturmfels) (eds.). *Geometric Combinatorics*. IAS/Park City Mathematics Series. Vol. 13. [American Mathematical Society](./American_Mathematical_Society). pp. 628–642. [ISBN](./ISBN_(identifier)) [978-0-8218-3736-8](./Special:BookSources/978-0-8218-3736-8).

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Graph theory](https://commons.wikimedia.org/wiki/Graph%20theory).  
- ["Graph theory"](https://www.encyclopediaofmath.org/index.php?title=Graph_theory), *[Encyclopedia of Mathematics](./Encyclopedia_of_Mathematics)*, [EMS Press](./European_Mathematical_Society), 2001 [1994]
- [Graph theory tutorial](http://www.utm.edu/departments/math/graph/) [Archived](https://web.archive.org/web/20120116185332/http://www.utm.edu/departments/math/graph/) 2012-01-16 at the [Wayback Machine](./Wayback_Machine)
- [A searchable database of small connected graphs](http://www.gfredericks.com/main/sandbox/graphs)
- [House of Graphs](https://houseofgraphs.org/) — searchable database of graphs with a drawing-based search feature.
- [Image gallery: graphs](https://web.archive.org/web/20060206155001/http://www.nd.edu/~networks/gallery.htm) at the [Wayback Machine](./Wayback_Machine) (archived February 6, 2006)
- [Concise, annotated list of graph theory resources for researchers](https://web.archive.org/web/20161114100939/http://www.babelgraph.org/links.html)
- [rocs](https://www.kde.org/applications/education/rocs/) — a graph theory IDE
- [The Social Life of Routers](http://www.orgnet.com/SocialLifeOfRouters.pdf) — non-technical paper discussing graphs of people and computers
- [Graph Theory Software](https://graphtheorysoftware.com/) — tools to teach and learn graph theory
- [Online books](https://ftl.toolforge.org/cgi-bin/ftl?st=&su=Graph+theory&library=OLBP), and library resources [in your library](https://ftl.toolforge.org/cgi-bin/ftl?st=&su=Graph+theory) and [in other libraries](https://ftl.toolforge.org/cgi-bin/ftl?st=&su=Graph+theory&library=0CHOOSE0) about graph theory
- [A list of graph algorithms](http://www.martinbroadhurst.com/Graph-algorithms.html) [Archived](https://web.archive.org/web/20190713044421/http://www.martinbroadhurst.com/Graph-algorithms.html) 2019-07-13 at the [Wayback Machine](./Wayback_Machine) with references and links to graph library implementations

 

### Online textbooks

 
- Hartmann, Alexander K.; Weigt, Martin (2005). "Introduction to graphs". *Phase Transitions in Combinatorial Optimization Problems: Basics, Algorithms and Statistical Mechanics*. Wiley. pp. 25–66. [arXiv](./ArXiv_(identifier)):[cond-mat/0602129](https://arxiv.org/abs/cond-mat/0602129). [doi](./Doi_(identifier)):[10.1002/3527606734.ch3](https://doi.org/10.1002%2F3527606734.ch3). [ISBN](./ISBN_(identifier)) [978-3-527-60673-3](./Special:BookSources/978-3-527-60673-3).
- [Digraphs: Theory Algorithms and Applications](https://www.cs.rhul.ac.uk/books/dbook/) 2007 by Jorgen Bang-Jensen and Gregory Gutin
- [Graph Theory, by Reinhard Diestel](http://diestel-graph-theory.com/index.html)

 
| vteMajormathematicsareas |
| --- |
| HistoryTimelineFutureListsGlossary |
| Foundations | Category theoryInformation theoryMathematical logicPhilosophy of mathematicsSet theoryType theory |
| Algebra | AbstractBooleanCliffordCommutativeElementaryField theoryGroup theoryHomologicalLieLinearMultilinearRing theoryUniversal |
| Analysis | CalculusReal analysisComplex analysisHypercomplex analysisDifferential equationsFunctional analysisHarmonic analysisMeasure theory |
| Discrete | CombinatoricsDiscrete geometryGraph theoryMatroid theoryOrder theory |
| Geometry | AlgebraicAffineAnalyticArithmeticComplexComputationalConvexDifferentialDiscreteEuclideanFiniteInformationProjective |
| Number theory | AlgebraicAnalyticArithmeticDiophantine geometry |
| Topology | GeneralAlgebraicDifferentialGeometricHomotopy theoryKnot theory |
| Applied | Engineering mathematicsMathematical biologyMathematical chemistryMathematical economicsMathematical financeMathematical geologyMathematical linguisticsMathematical physicsMathematical psychologyMathematical sociologyMathematical statisticsProbabilityStatisticsSystems scienceControl theoryGame theoryOperations research |
| Computational | Computer scienceTheory of computationComputational complexity theoryNumerical analysisOptimizationComputer algebra |
| Related topics | MathematicianslistsInformal mathematicsFilms about mathematiciansRecreational mathematicsMathematics and artMathematics educationNumberLarge |
| MathematicsportalCategoryCommonsWikiProject |

 
| vteComputer science |
| --- |
| This template follows roughly the 2012ACM Computing Classification System |
| Hardware | Printed circuit boardPeripheralIntegrated circuitVery-large-scale integrationSystem on a chip(SoC)Energy consumption(green computing)Electronic design automationHardware accelerationProcessorSize–Form |
| Systemsorganization | Computer architectureComputational complexityDependabilityEmbedded systemReal-time computingCyber-physical systemFault toleranceWireless sensor network |
| Networks | Network architectureNetwork protocolNetwork componentsNetwork schedulerNetwork performance evaluationNetwork service |
| Softwareorganization | InterpreterMiddlewareVirtual machineOperating systemSoftware quality |
| Softwarenotations,tools | Programming paradigmProgramming languageCompilerDomain-specific languageModeling languageSoftware frameworkIntegrated development environmentSoftware configuration managementSoftware librarySoftware repository |
| Softwaredevelopment | Control flowSoftware development processRequirements analysisSoftware designSoftware constructionSoftware deploymentSoftware engineeringSoftware maintenanceProgramming teamOpen sourcemodel |
| Theory ofcomputing | Model of computationStochasticFormal languageAutomata theoryComputability theoryComputational complexity theoryLogicSemantics |
| Algorithms | Algorithm designAnalysis of algorithmsAlgorithmic efficiencyRandomized algorithmComputational geometry |
| Mathematicsofcomputing | Discrete mathematicsProbabilityStatisticsMathematical softwareInformation theoryMathematical analysisNumerical analysisTheoretical computer scienceComputational problem |
| Informationsystems | DatabasemanagementInformation storageEnterprise informationSocial informationGeographic informationDecision supportProcess controlMultimedia informationData miningDigital libraryComputing platformDigital marketingWorld Wide WebInformation retrieval |
| Security | CryptographyFormal methodsSecurity hackerSecurityservicesIntrusion detection systemHardware securityNetwork securityInformation securityApplication security |
| Human-centeredcomputing | AccessibilityExtended realityaugmentedvirtualHuman–computer interactionInteraction designMobile computingSocial computingUbiquitous computingVisualization |
| Concurrency | Concurrent computingParallel computingDistributed computingMultithreadingMultiprocessing |
| Artificialintelligence | Computational intelligenceNatural language processingKnowledge representation and reasoningComputer visionAutomated planning and schedulingSearch methodologyControl methodPhilosophy ofDistributedMachinelearningSupervisedUnsupervisedReinforcementMulti-taskCross-validation | Computational intelligenceNatural language processingKnowledge representation and reasoningComputer visionAutomated planning and schedulingSearch methodologyControl methodPhilosophy ofDistributed | Machinelearning | SupervisedUnsupervisedReinforcementMulti-taskCross-validation |
| Computational intelligenceNatural language processingKnowledge representation and reasoningComputer visionAutomated planning and schedulingSearch methodologyControl methodPhilosophy ofDistributed |
| Machinelearning | SupervisedUnsupervisedReinforcementMulti-taskCross-validation |
| Graphics | AnimationRenderingPhotograph manipulationGraphics processing unitImage compressionSolid modeling |
| Appliedcomputing | Quantum computingE-commerceEnterprise softwareComputational mathematicsComputational physicsComputational chemistryComputational biologyComputational social scienceComputational engineeringDifferentiable computingComputational healthcareDigital artElectronic publishingCyberwarfareElectronic votingVideo gamesWord processingOperations researchEducational technologyDocument management |
| OutlineGlossariesCategory |

 
| vteGraph analysis software |
| --- |
| Free | CytoscapeGraphvizGephiigraphMicrosoft Automatic Graph LayoutNetworkXTulip |
| Proprietary | MapleMathematica |

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesFranceBnF dataJapanCzech RepublicIsrael |
| Other | Yale LUX |