---
source: https://en.wikipedia.org/wiki/Red%E2%80%93black_tree
fetched: 2026-06-19
---

Self-balancing binary search tree data structure 
| Red–black tree |
| --- |
| Type | Tree |
| Invented | 1978 |
| Invented by | Leonidas J. GuibasandRobert Sedgewick |
| Complexities inbig O notation |
| Space complexitySpaceO(n){\displaystyle O(n)}Time complexityFunctionAmortizedWorst caseSearchO(log⁡n){\displaystyle O(\log n)}O(log⁡n){\displaystyle O(\log n)}InsertO(log⁡n){\displaystyle O(\log n)}O(log⁡n){\displaystyle O(\log n)}DeleteO(log⁡n){\displaystyle O(\log n)}O(log⁡n){\displaystyle O(\log n)} | Space complexity | Space |  | O(n){\displaystyle O(n)} |  | Time complexity | Function |  | Amortized | Worst case | Search |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} | Insert |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} | Delete |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} |
| Space complexity |
| Space |  | O(n){\displaystyle O(n)} |  |
| Time complexity |
| Function |  | Amortized | Worst case |
| Search |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} |
| Insert |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} |
| Delete |  | O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/ce/Red-black_tree_example_with_sockets.svg/330px-Red-black_tree_example_with_sockets.svg.png)](./File:Red-black_tree_example_with_sockets.svg)Example of a red-black tree 

In [computer science](./Computer_science), a **red–black tree** is a [self-balancing binary search tree](./Self-balancing_binary_search_tree) [data structure](./Data_structure) noted for fast storage and retrieval of ordered information. The nodes in a red-black tree hold an extra "color" bit, often drawn as red and black, which help ensure that the tree is always approximately balanced.[[1]](./Red–black_tree#cite_note-Cormen2001-1)

 

When the tree is modified, the new tree is rearranged and "repainted" to restore the coloring properties that constrain how unbalanced the tree can become in the worst case. The properties are designed such that this rearranging and recoloring can be performed efficiently.

 

The (re-)balancing is not perfect, but guarantees searching in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of entries in the tree. The insert and delete operations, along with tree rearrangement and recoloring, also execute in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time.[[2]](./Red–black_tree#cite_note-wiscurl2-2)[[3]](./Red–black_tree#cite_note-3)

 

Tracking the color of each node requires only one bit of information per node because there are only two colors (due to memory alignment present in some programming languages, the real memory consumption may differ). The tree does not contain any other data specific to it being a red–black tree, so its [memory footprint](./Memory_footprint) is almost identical to that of a classic (uncolored) [binary search tree](./Binary_search_tree). In some cases, the added bit of information can be stored at no added memory cost.

  

## History

 

In 1972, [Rudolf Bayer](./Rudolf_Bayer)[[4]](./Red–black_tree#cite_note-Bayer72-4) invented a data structure that was a special order-4 case of a [B-tree](./B-tree). These trees maintained all [paths](./Path_(graph_theory)) from root to leaf with the same number of nodes, creating perfectly balanced trees. However, they were not *binary* search trees. Bayer called them a "symmetric binary B-tree" in his paper and later they became popular as [2–3–4 trees](./2–3–4_tree) or even 2–3 trees.[[5]](./Red–black_tree#cite_note-5)

 

In a 1978 paper, "A Dichromatic Framework for Balanced Trees",[[6]](./Red–black_tree#cite_note-GS78-6) [Leonidas J. Guibas](./Leonidas_J._Guibas) and [Robert Sedgewick](./Robert_Sedgewick_(computer_scientist)) derived the red–black tree from the symmetric binary B-tree.[[7]](./Red–black_tree#cite_note-7) The color "red" was chosen because it was the best-looking color produced by the color laser printer available to the authors while working at [Xerox PARC](./Xerox_PARC).[[8]](./Red–black_tree#cite_note-Sedgewick12-8) Another response from Guibas states that it was because of the red and black pens available to them to draw the trees.[[9]](./Red–black_tree#cite_note-9)

 

In 1993, Arne Andersson introduced the idea of a right leaning tree to simplify insert and delete operations.[[10]](./Red–black_tree#cite_note-10)

 

In 1999, [Chris Okasaki](./Chris_Okasaki) showed how to make the insert operation purely functional. Its balance function needed to take care of only four unbalanced cases and one default balanced case.[[11]](./Red–black_tree#cite_note-11)

 

The original algorithm used eight unbalanced cases, but [Cormen et al. (2001)](./Red–black_tree#CITEREFCormenLeisersonRivestStein2001) reduced that to six unbalanced cases.[[1]](./Red–black_tree#cite_note-Cormen2001-1) Sedgewick showed that the insert operation can be implemented in just 46 lines of [Java](./Java_(programming_language)).[[12]](./Red–black_tree#cite_note-Algs1-12)[[13]](./Red–black_tree#cite_note-13)
In 2008, Sedgewick proposed the [left-leaning red–black tree](./Left-leaning_red–black_tree), leveraging Andersson’s idea that simplified the insert and delete operations. Sedgewick originally allowed nodes whose two children are red, making his trees more like 2–3–4 trees, but later this restriction was added, making new trees more like 2–3 trees. Sedgewick implemented the insert algorithm in just 33 lines, significantly shortening his original 46 lines of code.[[14]](./Red–black_tree#cite_note-14)[[15]](./Red–black_tree#cite_note-Algs4-15)

 

## Terminology

 

The **black depth** of a node is defined as the number of black nodes from the root to that node (i.e. the number of black ancestors). The **black height** of a red–black tree is the number of black nodes in any path from the root to the leaves, which, by [requirement 4](./Red–black_tree#req4), is constant (alternatively, it could be defined as the black depth of any leaf node).[[16]](./Red–black_tree#cite_note-Mehlhorn2008-16): 154–165 
The black height of a node is the black height of the subtree rooted by it. In this article, the black height of a null node shall be set to 0, because its subtree is empty as suggested by the example figure, and its tree height is also 0.

 

## Properties

 

In addition to the requirements imposed on a [binary search tree](./Binary_search_tree) the following must be satisfied by a red–black tree:[[17]](./Red–black_tree#cite_note-Cormen2009-17)

 
1. Every node is either red or black.
2. All null nodes are considered black.
3. A red node does not have a red child.
4. Every [path](./Path_(graph_theory)) from a given node to any of its leaf nodes (that is, to any descendant null node) goes through the same number of black nodes.
5. (Conclusion) If a node **N** has exactly one child, the child must be red. If the child were black, its leaves would sit at a different black depth than **N'**s null node (which is considered black by rule 2), violating [requirement 4](./Red–black_tree#req4).

 

Some authors, e.g. Cormen & al.,[[17]](./Red–black_tree#cite_note-Cormen2009-17) claim "the root is black" as fifth requirement; but not Mehlhorn & Sanders[[16]](./Red–black_tree#cite_note-Mehlhorn2008-16) or Sedgewick & Wayne.[[15]](./Red–black_tree#cite_note-Algs4-15): 432–447  Since the root can always be changed from red to black, this rule has little effect on analysis.
This article also omits it, because it slightly disturbs the recursive algorithms and proofs.

 

As an example, every [perfect binary tree](./Binary_tree#Types_of_binary_trees) that consists only of black nodes is a red–black tree.

 

The read-only operations, such as search or tree traversal, do not affect any of the requirements. In contrast, the modifying operations [insert](./Red–black_tree#Insertion) and [delete](./Red–black_tree#Removal:_simple_cases) easily maintain requirements 1 and 2, but with respect to the other requirements some extra effort must be made, to avoid introducing a violation of requirement 3, called a **red-violation**, or of requirement 4, called a **black-violation**.

 

The requirements enforce a critical property of red–black trees: *the path from the root to the farthest leaf is no more than twice as long as the path from the root to the nearest leaf*. The result is that the tree is [height-balanced](./Height-balanced_binary_search_tree). Since operations such as inserting, deleting, and finding values require worst-case time proportional to the height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) of the tree, this upper bound on the height allows red–black trees to be efficient in the worst case, namely [logarithmic](./Logarithmic_growth) in the number     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) of entries, i.e.     h ∈ ∈  O ( log ⁡ ⁡  n )   {\displaystyle h\in O(\log n)}  ![{\displaystyle h\in O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fdb711098e2e947667de03803c495c3b8bd142c4) (a property which is shared by all self-balancing trees, e.g., [AVL tree](./AVL_tree) or [B-tree](./B-tree), but not the ordinary [binary search trees](./Binary_search_tree)). For a mathematical proof see section [Proof of bounds](./Red–black_tree#Proof_of_bounds).

 

Red–black trees, like all [binary search trees](./Binary_search_tree), allow quite efficient [sequential access](./Sequential_access) (e.g. [in-order traversal](./In-order_traversal), that is: in the order Left–Root–Right) of their elements. But they support also asymptotically optimal [direct access](./Random_access) via a traversal from root to leaf, resulting in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) search time.

 

## Analogy to 2–3–4 trees

 [![A 2-node maps to a single black node. A 3-node maps to a black node with a red child. A 4-node maps to a black node with two red children.](//upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Red-black_trees_and_2%E2%80%933%E2%80%934_trees.svg/250px-Red-black_trees_and_2%E2%80%933%E2%80%934_trees.svg.png)](./File:Red-black_trees_and_2–3–4_trees.svg)Figure 1: Similarities between 2–3–4 trees and red-black trees 

Red–black trees are similar in structure to [2–3–4 trees](./2–3–4_trees), which are [B-trees](./B-trees) of order 4.[[18]](./Red–black_tree#cite_note-18) In 2–3–4 trees, each node can contain between 1 and 3 values and have between 2 and 4 children. These 2–3–4 nodes correspond to black node – red children groups in red-black trees, as shown in figure 1. It is not a [1-to-1 correspondence](./1-to-1_correspondence), because 3-nodes have two equivalent representations: the red child may lie either to the left or right. The [left-leaning red-black tree](./Left-leaning_red-black_tree) variant makes this relationship exactly 1-to-1, by only allowing the left child representation. Since every 2–3–4 node has a corresponding black node, invariant 4 of red-black trees is equivalent to saying that the leaves of a 2–3–4 tree all lie at the same level.

 

Despite structural similarities, operations on red–black trees are more economical than B-trees. B-trees require management of vectors of variable length, whereas red-black trees are simply binary trees.[[19]](./Red–black_tree#cite_note-19)

 

## Applications and related data structures

 

Red–black trees offer worst-case guarantees for insertion time, deletion time, and search time. Not only does this make them valuable in time-sensitive applications such as [real-time applications](./Real-time_computing), but it makes them valuable building blocks in other data structures that provide worst-case guarantees. For example, many data structures used in [computational geometry](./Computational_geometry) are based on red–black trees, and the [Completely Fair Scheduler](./Completely_Fair_Scheduler) and [epoll](./Epoll) [system call](./System_call) of the [Linux kernel](./Linux_kernel) use red–black trees.[[20]](./Red–black_tree#cite_note-20)[[21]](./Red–black_tree#cite_note-21)
The [AVL tree](./AVL_tree) is another structure supporting     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) search, insertion, and removal. AVL trees can be colored red–black, and thus are a subset of red-black trees. The worst-case height of AVL is 0.720 times the worst-case height of red-black trees, so AVL trees are more rigidly balanced. The performance measurements of Ben Pfaff with realistic test cases in 79 runs find AVL to RB ratios between 0.677 and 1.077, median at 0.947, and [geometric mean](./Geometric_mean) 0.910.[[22]](./Red–black_tree#cite_note-22) The performance of [WAVL trees](./WAVL_tree) lies between AVL trees and red-black trees.[*[citation needed](./Wikipedia:Citation_needed)*]

 

Red–black trees are also particularly valuable in [functional programming](./Functional_programming), where they are one of the most common [persistent data structures](./Persistent_data_structure), used to construct [associative arrays](./Associative_array) and [sets](./Set_(computer_science)) that can retain previous versions after mutations. The persistent version of red–black trees requires     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) space for each insertion or deletion, in addition to time.

 

For every [2–3–4 tree](./2–3–4_tree), there are corresponding red–black trees with data elements in the same order. The insertion and deletion operations on 2–3–4 trees are also equivalent to color-flipping and rotations in red–black trees. This makes 2–3–4 trees an important tool for understanding the logic behind red–black trees, and this is why many introductory algorithm texts introduce 2–3–4 trees just before red–black trees, even though 2–3–4 trees are not often used in practice.

 

In 2008, [Sedgewick](./Robert_Sedgewick_(computer_scientist)) introduced a simpler version of the red–black tree called the [left-leaning red–black tree](./Left-leaning_red–black_tree)[[23]](./Red–black_tree#cite_note-LLRB-23) by eliminating a previously unspecified degree of freedom in the implementation. The LLRB maintains an additional invariant that all red links must lean left except during inserts and deletes. Red–black trees can be made isometric to either [2–3 trees](./2–3_tree),[[24]](./Red–black_tree#cite_note-24) or 2–3–4 trees,[[23]](./Red–black_tree#cite_note-LLRB-23) for any sequence of operations. The 2–3–4 tree isometry was described in 1978 by Sedgewick.[[6]](./Red–black_tree#cite_note-GS78-6) With 2–3–4 trees, the isometry is resolved by a "color flip," corresponding to a split, in which the red color of two children nodes leaves the children and moves to the parent node.

 

The original description of the [tango tree](./Tango_tree), a type of tree optimised for fast searches, specifically uses red–black trees as part of its data structure.[[25]](./Red–black_tree#cite_note-DHIP-25)

 

As of [Java](./Java_(programming_language)) 8, the [HashMap](./Hashtable) has been modified such that instead of using a [LinkedList](./LinkedList) to store different elements with [colliding](./Hash_function#Uniformity) [hashcodes](./Hashcode), a red–black tree is used. This results in the improvement of [time complexity](./Time_complexity) of searching such an element from     O ( m )   {\displaystyle O(m)}  ![{\displaystyle O(m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0ffd498cf521ce19814e6b7053f1f8ebb1d3c88) to     O ( log ⁡ ⁡  m )   {\displaystyle O(\log m)}  ![{\displaystyle O(\log m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01cc8bc56e37299e3f7da69f923f11e601030fd6) where     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the number of elements with colliding hashes.[[26]](./Red–black_tree#cite_note-26)

 

## Implementation

 

The read-only operations, such as search or tree traversal, on a red–black tree require no modification from those used for [binary search trees](./Binary_search_tree), because every red–black tree is a special case of a simple binary search tree. However, the immediate result of an insertion or removal may violate the properties of a red–black tree, the restoration of which is called *rebalancing* so that red–black trees become self-balancing.
Rebalancing (i.e. color changes) has a worst-case time complexity of     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) and average of     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21),[[27]](./Red–black_tree#cite_note-tarjan-27): 310 [[16]](./Red–black_tree#cite_note-Mehlhorn2008-16): 158  though these are very quick in practice. Additionally, rebalancing takes no more than three [tree rotations](./Tree_rotation)[[28]](./Red–black_tree#cite_note-28) (two for insertion).

 

This is an example implementation of insert and remove in [C](./C_(programming_language)). Below are the data structures and the `rotate_subtree` helper function used in the insert and remove examples.

 
```
typedef enum Color: char { 
    BLACK, 
    RED 
} Color;

typedef enum Direction: char { 
    LEFT, 
    RIGHT 
} Direction;

// red-black tree node
typedef struct Node {
	struct Node* parent; // null for the root node
	union {
		// Union so we can use ->left/->right or ->child[0]/->child[1]
		struct {
			struct Node* left;
			struct Node* right;
		};
		struct Node* child[2];
	};
	Color color;
	int key;
} Node;

typedef struct {
	struct Node* root;
} Tree;

static Direction direction(const Node* N) {
    return N == N->parent->right ? RIGHT : LEFT;
}

Node* rotate_subtree(Tree* tree, Node* sub, Direction dir) {
	Node* sub_parent = sub->parent;
	Node* new_root = sub->child[1 - dir]; // 1 - dir is the opposite direction
	Node* new_child = new_root->child[dir];

	sub->child[1 - dir] = new_child;

	if (new_child) {
        new_child->parent = sub;
    }

	new_root->child[dir] = sub;

	new_root->parent = sub_parent;
	sub->parent = new_root;
	if (sub_parent) {
		sub_parent->child[sub == sub_parent->right] = new_root;
	} else {
		tree->root = new_root;
    }

	return new_root;
}

```
 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Binary_Tree_Rotation_%28animated%29.gif/250px-Binary_Tree_Rotation_%28animated%29.gif)](./File:Binary_Tree_Rotation_(animated).gif)Left rotation and
right rotation, animated.

 

### Notes to the sample code and diagrams of insertion and removal

 

The proposal breaks down both insertion and removal (not mentioning some very simple cases) into six constellations of nodes, edges, and colors, which are called cases. The proposal contains, for both insertion and removal, exactly one case that advances one black level closer to the root and loops, the other five cases rebalance the tree of their own. The more complicated cases are pictured in a diagram.

 
- [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cc/RedNode.svg/20px-RedNode.svg.png)](./File:RedNode.svg) symbolises a red node and [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fe/BlackNode.svg/20px-BlackNode.svg.png)](./File:BlackNode.svg) a (non-NULL) black node (of black height ≥ 1), [![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bd/RedOrBlackNode.svg/20px-RedOrBlackNode.svg.png)](./File:RedOrBlackNode.svg) symbolises the color red or black of a non-NULL node, but the same color throughout the same diagram. NULL nodes are not represented in the diagrams.
- The variable **N** denotes the current node, which is labeled  N  or  N  in the diagrams.
- A diagram contains three columns and two to four actions. The left column shows the first iteration, the right column the higher iterations, the middle column shows the segmentation of a case into its different actions.[[29]](./Red–black_tree#cite_note-pullout-29)

 
1. The action "entry" shows the constellation of nodes with their colors which defines a case and mostly violates some of the [requirements](./Red–black_tree#Properties).
A blue border rings the current node **N** and the other nodes are labeled according to their relation to **N**.
2. If a [rotation](./Tree_rotation) is considered useful, this is pictured in the next action, which is labeled "rotation".
3. If some recoloring is considered useful, this is pictured in the next action, which is labeled "color".[[30]](./Red–black_tree#cite_note-30)
4. If there is still some need to repair, the cases make use of code of other cases and this after a reassignment of the current node **N**, which then again carries a blue ring and relative to which other nodes may have to be reassigned also. This action is labeled "reassign".
For both, insert and delete, there is (exactly) one case which iterates one black level closer to the root; then the reassigned constellation satisfies the respective loop invariant.

 
- A possibly numbered triangle with a black circle atop [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e0/TriangleTop.svg/20px-TriangleTop.svg.png)](./File:TriangleTop.svg) represents a red–black subtree (connected to its parent according to [requirement 3](./Red–black_tree#req3)) with a black height equal to the iteration level minus one, i.e. zero in the first iteration. Its root may be red or black.
A possibly numbered triangle [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3a/TriangleSubtree.svg/20px-TriangleSubtree.svg.png)](./File:TriangleSubtree.svg) represents a red–black subtree with a black height one less, i.e. its parent has black height zero in the second iteration.

 

 Remark For simplicity, the sample code uses the [disjunction](./Logical_disjunction):
`U == NULL || U->color == BLACK // considered black` and the [conjunction](./Logical_conjunction):
`U != NULL && U->color == RED   // not considered black` Thereby, it must be kept in mind that both statements are *not* evaluated in total, if `U == NULL`. Then in both cases `U->color` is not touched (see [Short-circuit evaluation](./Short-circuit_evaluation)).
(The comment `considered black` is in accordance with [requirement 2](./Red–black_tree#consideredBlack).) The related `if`-statements have to occur far less frequently if the proposal[[29]](./Red–black_tree#cite_note-pullout-29) is realised. 

### Insertion

 

Insertion begins by placing the new (non-NULL) node, say **N**, at the position in the [binary search tree](./Binary_search_tree) of a NULL node whose [in-order predecessor’s](./In-order_traversal) key compares less than the new node’s key, which in turn compares less than the key of its in-order successor.
(Frequently, this positioning is the result of a search within the tree immediately preceding the insert operation and consists of a node `P` together with a direction `dir` with `P->child[dir] == NULL`.)
The newly inserted node is temporarily colored red so that all paths contain the same number of black nodes as before.
But if its parent, say **P**, is also red then this action introduces a [red-violation](./Red–black_tree#ViolR).

 
```
// parent is optional
void insert(Tree* tree, Node* node, Node* parent, Direction dir) {
	node->color = RED;
	node->parent = parent;

	if (!parent) {
		tree->root = node;
		return;
	}

	parent->child[dir] = node;

	// rebalance the tree 
	do {
		// Case #1
		if (parent->color == BLACK) {
            return; 
        }

	    Node* grandparent = parent->parent;

		if (!grandparent) {
			// Case #4
			parent->color = BLACK;
			return;
		}

		dir = direction(parent);
		Node* uncle = grandparent->child[1 - dir];
		if (!uncle || uncle->color == BLACK) {
			if (node == parent->child[1 - dir]) {
				// Case #5
				rotate_subtree(tree, parent, dir);
				node = parent;
				parent = grandparent->child[dir];
			}

			// Case #6
			rotate_subtree(tree, grandparent, 1 - dir);
			parent->color = BLACK;
			grandparent->color = RED;
			return;
		}
	
		// Case #2
		parent->color = BLACK;
		uncle->color = BLACK;
		grandparent->color = RED;
		node = grandparent;

	} while ((parent = node->parent));

	// Case #3
	return;

}

```
 

The rebalancing loop of the insert operation has the following [invariants](./Loop_invariant):

 
- **Node** is the current node, initially the insertion node.
- **Node** is red at the beginning of each iteration.
- [Requirement 3](./Red–black_tree#req3) is satisfied for all pairs node←parent with the possible exception **node**←**parent** when **parent** is also red (a [red-violation](./Red–black_tree#ViolR) at **node**).
- All other properties (including [requirement 4](./Red–black_tree#req4)) are satisfied throughout the tree.

 

#### Notes to the insert diagrams

 
| before | case | rotation | assign­ment | after | next | Δh |
| --- | --- | --- | --- | --- | --- | --- |
| P | G | U | x | P | G | U | x |
|  |  |  |  | I1 |  |  |  |  |  |  |  |  |
|  |  |  |  | I2 |  | N:=G | ? |  |  |  | ? | 2 |
| — |  |  |  | I3 |  |  |  |  |  |  |  |  |
|  | — |  |  | I4 |  |  |  |  |  |  |  |  |
|  |  |  | i | I5 | P↶N | N:=P |  |  |  | o | I6 | 0 |
|  |  |  | o | I6 | P↷G |  |  |  |  |  |  |  |
| InsertionThis synopsis shows in itsbeforecolumns, that allpossible cases[31]of constellations are covered. |

 
- In the diagrams, **P** is used for **N**’s parent, **G** for its grandparent, and **U** for its uncle. In the table, "—" indicates the root.
- The diagrams show the parent node **P** as the left child of its parent **G** even though it is possible for **P** to be on either side. The sample code covers both possibilities by means of the side variable `dir`.
- The diagrams show the cases where **P** is red also, the red-violation.
- The column *x* indicates the change in child direction, i.e. o (for "outer") means that **P** and **N** are both left or both right children, whereas i (for "inner") means that the child direction changes from **P**’s to **N**’s.
- The [column group](./Column_group) *before* defines the case, whose name is given in the column *case*. Thereby possible values in cells left empty are ignored. So in case **[I2](./Red–black_tree#Insert_case_2)** the sample code covers both possibilities of child directions of **N**, although the corresponding diagram shows only one.
- The rows in the synopsis are ordered such that the coverage of all possible RB cases is easily comprehensible.
- The column *rotation* indicates whether a rotation contributes to the rebalancing.
- The column *assignment* shows an assignment of **N** before entering a subsequent step. This possibly induces a reassignment of the other nodes **P**, **G**, **U** also.
- If something has been changed by the case, this is shown in the column group *after*.
- A [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/26/Check-green.svg/20px-Check-green.svg.png)](./File:Check-green.svg) sign in column *next* signifies that the rebalancing is complete with this step. If the column *after* determines exactly one case, this case is given as the subsequent one, otherwise there are question marks.
- In case **[2](./Red–black_tree#Insert_case_2)** the problem of rebalancing is escalated     Δ Δ  h = 2   {\displaystyle \Delta h=2}  ![{\displaystyle \Delta h=2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e917f435b864bfa3c32af4940ab895a6d857d07d) tree levels or 1 black level higher in the tree, in that the grandfather **G** becomes the new current node **N**. So it takes maximally        h 2      {\displaystyle {\tfrac {h}{2}}}  ![{\displaystyle {\tfrac {h}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a80fcbc6eae7936fd14446e7e120f846589c3893) steps of iteration to repair the tree (where h is the height of the tree). Because the probability of escalation decreases exponentially with each step the total rebalancing cost is constant on average, indeed [amortized constant](./Red–black_tree#amortized).
- Rotations occur in cases **I6** and **I5 + I6** – outside the loop. Therefore, at most two rotations occur in total.

 

#### Insert case 1

 

The current node’s parent **P** is black, so [requirement 3](./Red–black_tree#req3) holds. Requirement 4 holds also according to the [loop invariant](./Red–black_tree#loopInvariantI).

 

#### Insert case 2

 actions: [e=entry,][r=rotation,][c=color,][a=reassign] actions: eca [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/64/Red-black_tree_insert_case_B0t.svg/120px-Red-black_tree_insert_case_B0t.svg.png)](./File:Red-black_tree_insert_case_B0t.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Red-black_tree_perpendic_579_switch.svg/20px-Red-black_tree_perpendic_579_switch.svg.png)](./File:Red-black_tree_perpendic_579_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/5/55/Red-black_tree_insert_case_B1t.svg/120px-Red-black_tree_insert_case_B1t.svg.png)](./File:Red-black_tree_insert_case_B1t.svg)higher iterationInsert Case 2 

If both the parent **P** and the uncle **U** are red, then both of them can be repainted black and the grandparent **G** becomes red for maintaining [requirement 4](./Red–black_tree#req4). Since any path through the parent or uncle must pass through the grandparent, the number of black nodes on these paths has not changed. However, the grandparent **G** may now violate requirement 3, if it has a red parent. After relabeling **G** to **N** the [loop invariant](./Red–black_tree#loopInvariantI) is fulfilled so that the rebalancing can be iterated on one black level (= 2 tree levels) higher.

 

#### Insert case 3

 

[Insert case 2](./Red–black_tree#Insert_case_2) has been executed for         h − −  1  2      {\displaystyle {\tfrac {h-1}{2}}}  ![{\displaystyle {\tfrac {h-1}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6dab1f16f0a08d28cf3e4e74d3e5ad6107b715e9) times and the total height of the tree has increased by 1, now being h .
The current node **N** is the (red) root of the tree, and all RB-properties are satisfied.

 

#### Insert case 4

 

The parent **P** is red and the root.
Because **N** is also red, requirement 3 is violated. But after switching **P**’s color the tree is in RB-shape.
The black height of the tree increases by 1.

 

#### Insert case 5

 actions: era [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Red-black_tree_insert_case_C0.svg/120px-Red-black_tree_insert_case_C0.svg.png)](./File:Red-black_tree_insert_case_C0.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c1/Red-black_tree_perpendic_639era_switch.svg/20px-Red-black_tree_perpendic_639era_switch.svg.png)](./File:Red-black_tree_perpendic_639era_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/17/Red-black_tree_insert_case_C1.svg/120px-Red-black_tree_insert_case_C1.svg.png)](./File:Red-black_tree_insert_case_C1.svg)higher iterationInsert Case 5 

The parent **P** is red but the uncle **U** is black. The ultimate goal is to rotate the parent node **P** to the grandparent position, but this will not work if **N** is an "inner" grandchild of **G** (i.e., if **N** is the left child of the right child of **G** or the right child of the left child of **G**). A `dir`-rotation at **P** switches the roles of the current node **N** and its parent **P**. The rotation adds paths through **N** (those in the subtree labeled **2**, see diagram) and removes paths through **P** (those in the subtree labeled **4**). But both **P** and **N** are red, so [requirement 4](./Red–black_tree#req4) is preserved. Requirement 3 is restored in case 6.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/68/Red-black_tree_insert_case_D0rot.svg/120px-Red-black_tree_insert_case_D0rot.svg.png)](./File:Red-black_tree_insert_case_D0rot.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Red-black_tree_perpendic_639erc_switch.svg/20px-Red-black_tree_perpendic_639erc_switch.svg.png)](./File:Red-black_tree_perpendic_639erc_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Red-black_tree_insert_case_D1rot.svg/120px-Red-black_tree_insert_case_D1rot.svg.png)](./File:Red-black_tree_insert_case_D1rot.svg)higher iterationInsert Case 6 

#### Insert case 6

 actions: erc

The current node **N** is now certain to be an "outer" grandchild of **G** (left of left child or right of right child). Now `(1-dir)`-rotate at **G**, putting **P** in place of **G** and making **P** the parent of **N** and **G**. **G** is black and its former child **P** is red, since [requirement 3](./Red–black_tree#req3) was violated. After switching the colors of **P** and **G** the resulting tree satisfies requirement 3. [Requirement 4](./Red–black_tree#req4) also remains satisfied, since all paths that went through the black **G** now go through the black **P**.

 

Because the algorithm transforms the input without using an auxiliary data structure and using only a small amount of extra storage space for auxiliary variables it is [in-place](./In-place_algorithm).

 

### Removal

 

#### Simple cases

 
- When the deleted node has **2 children** (non-NULL), then we can swap its value with its in-order successor (the leftmost child of the right subtree), and then delete the successor instead. Since the successor is leftmost, it can only have a right child (non-NULL) or no child at all.
- When the deleted node has **only 1 child** (non-NULL). In this case, just replace the node with its child, and color it black.

- The single child (non-NULL) must be red according to [conclusion 5](./Red–black_tree#con5), and the deleted node must be black according to [requirement 3](./Red–black_tree#req3).

- When the deleted node **has no children** (both NULL) and is the root, replace it with NULL. The tree is empty.
- When the deleted node **has no children** (both NULL), and **is red**, simply remove the leaf node.
- When the deleted node **has no children** (both NULL), and **is black**, deleting it will create an imbalance, and requires a rebalance, as covered in the next section.

 

#### Removal of a black non-root leaf

 

The complex case is when **N** is not the root, colored black and has no proper child (⇔ only NULL children).
In the first iteration, **N** is replaced by NULL.

 
```
void remove(Tree* tree, Node* node) {
	Node* parent = node->parent;

	Node* sibling;
	Node* close_nephew;
	Node* distant_nephew;

	Direction dir = direction(node);

	parent->child[dir] = NULL;
	goto start_balance;

	do {
		dir = direction(node);
start_balance:
		sibling = parent->child[1 - dir];
		distant_nephew = sibling->child[1 - dir];
		close_nephew = sibling->child[dir];
		if (sibling->color == RED) {
			// Case #3
			rotate_subtree(tree, parent, dir);
			parent->color = RED;
			sibling->color = BLACK;
			sibling = close_nephew;

			distant_nephew = sibling->child[1 - dir];
			if (distant_nephew && distant_nephew->color == RED) {
				goto case_6;
            }
			close_nephew = sibling->child[dir];
			if (close_nephew && close_nephew->color == RED) {
				goto case_5;
            }

			// Case #4
			sibling->color = RED;
			parent->color = BLACK;
			return;
		}

		if (distant_nephew && distant_nephew->color == RED) {
			goto case_6;
        }

		if (close_nephew && close_nephew->color == RED) {
			goto case_5;
        }

		if (parent->color == RED) {
			// Case #4
			sibling->color = RED;
			parent->color = BLACK;
			return;
		}

		// Case #2
		sibling->color = RED;
		node = parent;

	} while (parent = node->parent);
	
	// Case #1
    return;
    
case_5:

	rotate_subtree(tree, sibling, 1 - dir);
	sibling->color = RED;
	close_nephew->color = BLACK;
	distant_nephew = sibling;
	sibling = close_nephew;

case_6:

	rotate_subtree(tree, parent, dir);
	sibling->color = parent->color;
	parent->color = BLACK;
	distant_nephew->color = BLACK;
	return;
}

```
 

The rebalancing loop of the delete operation has the following [invariant](./Loop_invariant):

 
- At the beginning of each iteration the black height of **N** equals the iteration number minus one, which means that in the first iteration it is zero and that **N** is a true black node [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fe/BlackNode.svg/20px-BlackNode.svg.png)](./File:BlackNode.svg) in higher iterations.
- The number of black nodes on the paths through **N** is one less than before the deletion, whereas it is unchanged on all other paths, so that there is a [black-violation](./Red–black_tree#ViolB) at **P** if other paths exist.
- All other properties (including [requirement 3](./Red–black_tree#req3)) are satisfied throughout the tree.

 

#### Notes to the delete diagrams

 
| before | case | rotation | assignment | after | next | Δh |
| --- | --- | --- | --- | --- | --- | --- |
| P | C | S | D | P | C | S | D |
| — |  |  |  | D1 |  |  |  |  |  |  |  |  |
|  |  |  |  | D2 |  | N:=P | ? |  |  |  | ? | 1 |
|  |  |  |  | D3 | P↶S | N:=N |  |  |  |  | D6 | 0 |
|  |  |  |  | D5 | 0 |
|  |  |  |  | D4 | 0 |
|  |  |  |  | D4 |  |  |  |  |  |  |  |  |
|  |  |  |  | D5 | C↷S | N:=N |  |  |  |  | D6 | 0 |
|  |  |  |  | D6 | P↶S |  |  |  |  |  |  |  |
| DeletionThis synopsis shows in itsbeforecolumns, that allpossible cases[31]of color constellations are covered. |

 
- In the diagrams below, **P** is used for **N**’s parent, **S** for the sibling of **N**, **C** (meaning *close* nephew) for **S**’s child in the same direction as **N**, and **D** (meaning *distant* nephew) for **S**’s other child (**S** cannot be a NULL node in the first iteration, because it must have black height one, which was the black height of **N** before its deletion, but **C** and **D** may be NULL nodes).
- The diagrams show the current node **N** as the left child of its parent **P** even though it is possible for **N** to be on either side. The code samples cover both possibilities by means of the side variable `dir`.
- At the beginning (in the first iteration) of removal, **N** is the NULL node replacing the node to be deleted. Because its location in parent’s node is the only thing of importance, it is symbolised by [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6c/NilBlue.svg/20px-NilBlue.svg.png)](./File:NilBlue.svg) (meaning: the current node **N** is a NULL node and left child) in the left column of the delete diagrams. As the operation proceeds also proper nodes (of black height ≥ 1) may become current (see e.g. case **[2](./Red–black_tree#Delete_case_2)**).
- By counting the black bullets ([![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fe/BlackNode.svg/20px-BlackNode.svg.png)](./File:BlackNode.svg) and [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e0/TriangleTop.svg/20px-TriangleTop.svg.png)](./File:TriangleTop.svg)) in a delete diagram it can be observed that the paths through **N** have one bullet less than the other paths. This means a black-violation at **P**—if it exists.
- The color constellation in column group *before* defines the case, whose name is given in the column *case*. Thereby possible values in cells left empty are ignored.
- The rows in the synopsis are ordered such that the coverage of all possible RB cases is easily comprehensible.
- The column *rotation* indicates whether a rotation contributes to the rebalancing.
- The column *assignment* shows an assignment of **N** before entering a subsequent iteration step. This possibly induces a reassignment of the other nodes **P**, **C**, **S**, **D** also.
- If something has been changed by the case, this is shown in the column group *after*.
- A [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/26/Check-green.svg/20px-Check-green.svg.png)](./File:Check-green.svg) sign in column *next* signifies that the rebalancing is complete with this step. If the column *after* determines exactly one case, this case is given as the subsequent one, otherwise there are question marks.
- The loop is where the problem of rebalancing is escalated     Δ Δ  h = 1   {\displaystyle \Delta h=1}  ![{\displaystyle \Delta h=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d1e4add760f1aeebaeafee795acfa6f29b548bc) level higher in the tree in that the parent **P** becomes the new current node **N**. So it takes maximally h iterations to repair the tree (where h is the height of the tree). Because the probability of escalation decreases exponentially with each iteration the total rebalancing cost is constant on average, indeed [amortized constant](./Red–black_tree#amortized). (Just as an aside: Mehlhorn & Sanders point out: "AVL trees do *not* support constant amortized update costs."[[16]](./Red–black_tree#cite_note-Mehlhorn2008-16): 165, 158  This is true for the rebalancing after a deletion, but not AVL insertion.[[32]](./Red–black_tree#cite_note-32))
- Out of the body of the loop there are exiting branches to the cases **[3](./Red–black_tree#Delete_case_3)**, **[6](./Red–black_tree#Delete_case_6)**, **[5](./Red–black_tree#Delete_case_5)**, **[4](./Red–black_tree#Delete_case_4)**, and **[1](./Red–black_tree#Delete_case_1)**; section ["Delete case 3"](./Red–black_tree#Delete_case_3) of its own has three different exiting branches to the cases **6**, **5** and **4**.
- Rotations occur in cases **6** and **5 + 6** and **3 + 5 + 6** – all outside the loop. Therefore, at most three rotations occur in total.

 

#### Delete case 1

 

The current node **N** is the new root. One black node has been removed from every path, so the RB-properties are preserved.
The black height of the tree decreases by 1.

 

#### Delete case 2

 actions: eca [→ Explanation of symbols](./Red–black_tree#explan)[![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Red-black_tree_delete_case_B0t.svg/120px-Red-black_tree_delete_case_B0t.svg.png)](./File:Red-black_tree_delete_case_B0t.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Red-black_tree_perpendic_579_switch.svg/20px-Red-black_tree_perpendic_579_switch.svg.png)](./File:Red-black_tree_perpendic_579_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Red-black_tree_delete_case_B1t.svg/120px-Red-black_tree_delete_case_B1t.svg.png)](./File:Red-black_tree_delete_case_B1t.svg)higher iterationDelete case D2 

**P**, **S**, and **S**’s children are black. After painting **S** red all paths passing through **S**, which are precisely those paths *not* passing through **N**, have one less black node. Now all paths in the subtree rooted by **P** have the same number of black nodes, but one fewer than the paths that do not pass through **P**, so [requirement 4](./Red–black_tree#req4) may still be violated. After relabeling **P** to **N** the [loop invariant](./Red–black_tree#loopInvariantD) is fulfilled so that the rebalancing can be iterated on one black level (= 1 tree level) higher.

 

#### Delete case 3

 actions: rca [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/95/Red-black_tree_delete_case_A0rot3.svg/120px-Red-black_tree_delete_case_A0rot3.svg.png)](./File:Red-black_tree_delete_case_A0rot3.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/8/86/Red-black_tree_perpendic_865_switch.svg/20px-Red-black_tree_perpendic_865_switch.svg.png)](./File:Red-black_tree_perpendic_865_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Red-black_tree_delete_case_A1rot3.svg/120px-Red-black_tree_delete_case_A1rot3.svg.png)](./File:Red-black_tree_delete_case_A1rot3.svg)higher iterationDelete case D3 

The sibling **S** is red, so **P** and the nephews **C** and **D** have to be black. A `dir`-rotation at **P** turns **S** into **N**’s grandparent.
Then after reversing the colors of **P** and **S**, the path through **N** is still short one black node. But **N** now has a red parent **P** and after the reassignment a black sibling **S**, so the transformations in cases 4, 5, or 6 are able to restore the RB-shape.

 

#### Delete case 4

 actions: ec [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Red-black_tree_delete_case_C0.svg/120px-Red-black_tree_delete_case_C0.svg.png)](./File:Red-black_tree_delete_case_C0.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/13/Red-black_tree_perpendic_419_switch.svg/20px-Red-black_tree_perpendic_419_switch.svg.png)](./File:Red-black_tree_perpendic_419_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a6/Red-black_tree_delete_case_C1.svg/120px-Red-black_tree_delete_case_C1.svg.png)](./File:Red-black_tree_delete_case_C1.svg)higher iterationDelete case D4 

The sibling **S** and **S**’s children are black, but **P** is red. Exchanging the colors of **S** and **P** does not affect the number of black nodes on paths going through **S**, but it does add one to the number of black nodes on paths going through **N**, making up for the deleted black node on those paths.

 

#### Delete case 5

 actions: rca [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Red-black_tree_delete_case_D0rot.svg/120px-Red-black_tree_delete_case_D0rot.svg.png)](./File:Red-black_tree_delete_case_D0rot.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Red-black_tree_perpendic_919_switch.svg/20px-Red-black_tree_perpendic_919_switch.svg.png)](./File:Red-black_tree_perpendic_919_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Red-black_tree_delete_case_D1rot.svg/120px-Red-black_tree_delete_case_D1rot.svg.png)](./File:Red-black_tree_delete_case_D1rot.svg)higher iterationDelete case D5 

The sibling **S** is black, **S**’s close child **C** is red, and **S**’s distant child **D** is black. After a `(1-dir)`-rotation at **S** the nephew **C** becomes **S**’s parent and **N**’s new sibling. The colors of **S** and **C** are exchanged.
All paths still have the same number of black nodes, but now **N** has a black sibling whose distant child is red, so the constellation is fit for case D6. Neither **N** nor its parent **P** are affected by this transformation, and **P** may be red or black ([![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bd/RedOrBlackNode.svg/20px-RedOrBlackNode.svg.png)](./File:RedOrBlackNode.svg) in the diagram).

 

#### Delete case 6

 actions: erc [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/38/Red-black_tree_delete_case_E0rot.svg/120px-Red-black_tree_delete_case_E0rot.svg.png)](./File:Red-black_tree_delete_case_E0rot.svg)first iteration[![](//upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Red-black_tree_perpendic_639erc_switch.svg/20px-Red-black_tree_perpendic_639erc_switch.svg.png)](./File:Red-black_tree_perpendic_639erc_switch.svg)[![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Red-black_tree_delete_case_E1rot.svg/120px-Red-black_tree_delete_case_E1rot.svg.png)](./File:Red-black_tree_delete_case_E1rot.svg)higher iterationDelete case D6 

The sibling **S** is black, **S**’s distant child **D** is red. After a `dir`-rotation at **P** the sibling **S** becomes the parent of **P** and **S**’s distant child **D**. The colors of **P** and **S** are exchanged, and **D** is made black. The whole subtree still has the same color at its root **S**, namely either red or black ([![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bd/RedOrBlackNode.svg/20px-RedOrBlackNode.svg.png)](./File:RedOrBlackNode.svg) in the diagram), which refers to the same color both before and after the transformation. This way [requirement 3](./Red–black_tree#req3) is preserved. The paths in the subtree not passing through **N** (i.o.w. passing through **D** and node **3** in the diagram) pass through the same number of black nodes as before, but **N** now has one additional black ancestor: either **P** has become black, or it was black and **S** was added as a black grandparent. Thus, the paths passing through **N** pass through one additional black node, so that [requirement 4](./Red–black_tree#req4) is restored and the total tree is in RB-shape.

 

Because the algorithm transforms the input without using an auxiliary data structure and using only a small amount of extra storage space for auxiliary variables it is [in-place](./In-place_algorithm).

 

## Proof of bounds

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5a/5_minimal_red-black_trees_nN.svg/330px-5_minimal_red-black_trees_nN.svg.png)](./File:5_minimal_red-black_trees_nN.svg)Figure 2: Red–black trees RB*h* of heights *h*=1,2,3,4,5,
each with minimal number 1,2,4,6 resp. 10 of nodes. 

For     h ∈ ∈   N    {\displaystyle h\in \mathbb {N} }  ![{\displaystyle h\in \mathbb {N} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/fd796ca77a508511c1ba760a6b508973b08afc36) there is a red–black tree of height     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) with

 
| mh{\displaystyle m_{h}} | =2⌊(h+1)/2⌋+2⌊h/2⌋−2{\displaystyle =2^{\lfloor (h+1)/2\rfloor }+2^{\lfloor h/2\rfloor }-2} |
| --- | --- |
|  | ={{\displaystyle ={\Biggl \{}} | 2⋅2h2−2=2h2+1−2{\displaystyle 2\cdot 2^{\tfrac {h}{2}}-2=2^{{\tfrac {h}{2}}+1}-2} |  | ifh{\displaystyle h}even |
| 3⋅2h−12−2{\displaystyle 3\cdot 2^{\tfrac {h-1}{2}}-2} |  | ifh{\displaystyle h}odd |

 

nodes (    ⌊ ⌊   ⌋ ⌋    {\displaystyle \lfloor \,\rfloor }  ![{\displaystyle \lfloor \,\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/3084289cca849fb18ec6407b9de5faa5846d8607) is the [floor function](./Floor_and_ceiling_functions)) and there is no red–black tree of this tree height with fewer nodes—therefore it is **minimal**.
Its black height is       ⌈ ⌈  h  /  2 ⌉ ⌉    {\displaystyle \lceil h/2\rceil }  ![{\displaystyle \lceil h/2\rceil }](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ab467b2409d6a03abd1eaea955a89b01ab11bc4)   (with black root) or for odd     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) (then with a red root) also       ( h − −  1 )  /  2   .   {\displaystyle (h-1)/2~.}  ![{\displaystyle (h-1)/2~.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/624b37eb86422209805b5a7ae402623f34fe9516)

 Proof 

For a red–black tree of a certain height to have minimal number of nodes, it must have exactly one longest path with maximal number of red nodes, to achieve a maximal tree height with a minimal black height. Besides this path all other nodes have to be black.[[15]](./Red–black_tree#cite_note-Algs4-15): 444 Proof sketch  If a node is taken off this tree it either loses height or some RB property.

 

The RB tree of height     h = 1   {\displaystyle h=1}  ![{\displaystyle h=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d5d82ae0a834e0d0b839e2ea7a0f8eac0ee791d) with red root is minimal. This is in agreement with

      m  1   =  2  ⌊ ⌊  ( 1 + 1 )  /  2 ⌋ ⌋     +   2  ⌊ ⌊  1  /  2 ⌋ ⌋      − −    2 =  2  1    +   2  0     − −    2 = 1   .   {\displaystyle m_{1}=2^{\lfloor (1+1)/2\rfloor }\!+\!2^{\lfloor 1/2\rfloor }\!\!-\!\!2=2^{1}\!+\!2^{0}\!\!-\!\!2=1~.}  ![{\displaystyle m_{1}=2^{\lfloor (1+1)/2\rfloor }\!+\!2^{\lfloor 1/2\rfloor }\!\!-\!\!2=2^{1}\!+\!2^{0}\!\!-\!\!2=1~.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/30e23cc8c099a9f15af5d0b202fcbbd9f6bf61ff) 

A minimal RB tree (RB*h* in figure 2) of height     h > 1   {\displaystyle h>1}  ![{\displaystyle h>1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3df33213a54649226c03c8115b130c49170d0683) has a root whose two child subtrees are of different height. The higher child subtree is also a minimal RB tree, RB*h*–1, containing also a longest path that defines its height     h   − −    1   {\displaystyle h\!\!-\!\!1}  ![{\displaystyle h\!\!-\!\!1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/457b18f3a6b88195f73823276ea191f69975fbe3); it has      m  h − −  1     {\displaystyle m_{h-1}}  ![{\displaystyle m_{h-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1edb81f036dd4ec5ed6234b26b2bb969e140fb5e) nodes and the black height     ⌊ ⌊  ( h   − −    1 )  /  2 ⌋ ⌋  =: s .   {\displaystyle \lfloor (h\!\!-\!\!1)/2\rfloor =:s.}  ![{\displaystyle \lfloor (h\!\!-\!\!1)/2\rfloor =:s.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e058a8d10edc0edb201b22f2e4b24455452d2519) The other subtree is a [perfect binary tree](./Binary_tree#Types_of_binary_trees) of (black) height     s   {\displaystyle s}  ![{\displaystyle s}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01d131dfd7673938b947072a13a9744fe997e632) having      2  s     − −    1 =  2  ⌊ ⌊  ( h − −  1 )  /  2 ⌋ ⌋      − −    1   {\displaystyle 2^{s}\!\!-\!\!1=2^{\lfloor (h-1)/2\rfloor }\!\!-\!\!1}  ![{\displaystyle 2^{s}\!\!-\!\!1=2^{\lfloor (h-1)/2\rfloor }\!\!-\!\!1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5bf25348afb7233dd7a0f4d94f1128874424b09f) black nodes—and no red node. Then the number of nodes is by [induction](./Mathematical_induction)

 
|  | mh{\displaystyle m_{h}} | ={\displaystyle =} | (mh−1){\displaystyle (m_{h-1})} | +{\displaystyle +} | (1){\displaystyle (1)} | +{\displaystyle +} | (2⌊(h−1)/2⌋−1){\displaystyle (2^{\lfloor (h-1)/2\rfloor }-1)} |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  | (higher subtree) |  | (root) |  | (second subtree) |
| resulting in |
|  | mh{\displaystyle m_{h}} | ={\displaystyle =} | (2⌊h/2⌋+2⌊(h−1)/2⌋−2){\displaystyle (2^{\lfloor h/2\rfloor }+2^{\lfloor (h-1)/2\rfloor }-2)} | +{\displaystyle +} | 2⌊(h−1)/2⌋{\displaystyle 2^{\lfloor (h-1)/2\rfloor }} |
|  |  | ={\displaystyle =} | 2⌊h/2⌋+2⌊(h+1)/2⌋−2{\displaystyle 2^{\lfloor h/2\rfloor }+2^{\lfloor (h+1)/2\rfloor }-2}■ |

 

The [graph](./Graph_of_a_function) of the function      m  h     {\displaystyle m_{h}}  ![{\displaystyle m_{h}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8125d74e28bfab7418265ece96c1ea364924cb14) is [convex](./Convex_function) and [piecewise linear](./Piecewise_linear_function) with breakpoints at     ( h = 2 k   |    m  2 k   = 2 ⋅ ⋅   2  k    − −   2 )   {\displaystyle (h=2k\;|\;m_{2k}=2\cdot 2^{k}\!-\!2)}  ![{\displaystyle (h=2k\;|\;m_{2k}=2\cdot 2^{k}\!-\!2)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3ce284b61162046ecc582488fff2f6d539cdfb75) where     k ∈ ∈   N  .   {\displaystyle k\in \mathbb {N} .}  ![{\displaystyle k\in \mathbb {N} .}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7037847116113f919f4a73998f7466f9c0615a1b) The function has been tabulated as      m  h   =   {\displaystyle m_{h}=}  ![{\displaystyle m_{h}=}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f80ecca43c17a8fb1a90622696612e6a5d0742a8) A027383(*h*–1) for     h ≥ ≥  1   {\displaystyle h\geq 1}  ![{\displaystyle h\geq 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0757ec4a3a583f5faf146a91bfbbf088253f112c) (sequence [A027383](//oeis.org/A027383) in the [OEIS](./On-Line_Encyclopedia_of_Integer_Sequences)).

 Solving the function for     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) 

The inequality     9 > 8 =  2  3     {\displaystyle 9>8=2^{3}}  ![{\displaystyle 9>8=2^{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fc6aa3b743ffc4de7d75d22ec4e30b93ae86037) leads to     3 >  2  3  /  2     {\displaystyle 3>2^{3/2}}  ![{\displaystyle 3>2^{3/2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/289041b8c90d373cd5129f1c257ef854de064e4c), which for odd     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) leads to

      m  h   = 3 ⋅ ⋅   2  ( h − −  1 )  /  2   − −  2 =   (   3 ⋅ ⋅   2  − −  3  /  2     )   ⋅ ⋅   2  ( h + 2 )  /  2   − −  2 > 2 ⋅ ⋅   2  h  /  2   − −  2   {\displaystyle m_{h}=3\cdot 2^{(h-1)/2}-2={\bigl (}3\cdot 2^{-3/2}{\bigr )}\cdot 2^{(h+2)/2}-2>2\cdot 2^{h/2}-2}  ![{\displaystyle m_{h}=3\cdot 2^{(h-1)/2}-2={\bigl (}3\cdot 2^{-3/2}{\bigr )}\cdot 2^{(h+2)/2}-2>2\cdot 2^{h/2}-2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/11105813afbd3e754a837dae4eb53795fdf60696). 

So in both, the even and the odd case,     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) is in the interval

 
|  | log2⁡(n+1){\displaystyle \log _{2}(n+1)} | ≤h≤{\displaystyle \leq h\leq } | 2log2⁡(n+2)−2=2log2⁡(n/2+1){\displaystyle 2\log _{2}(n+2)-2=2\log _{2}(n/2+1)} | [<2log2⁡(n+1)]{\displaystyle {\bigl [}<2\log _{2}(n+1)\;{\bigr ]}} |
| --- | --- | --- | --- | --- |
|  | (perfect binary tree) |  | (minimal red–black tree) |

 

with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) being the number of nodes.[[33]](./Red–black_tree#cite_note-33)

 Conclusion 

A red–black tree with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) nodes (keys) has tree height     h ∈ ∈  O ( log ⁡ ⁡  n ) .   {\displaystyle h\in O(\log n).}  ![{\displaystyle h\in O(\log n).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4ef0d66e05a531eac2823ef294cd01ff07908a5f)

 

## Set operations and bulk operations

 

In addition to the single-element insert, delete and lookup operations, several set operations have been defined on red–black trees: [union](./Union_(set_theory)), [intersection](./Intersection_(set_theory)) and [set difference](./Set_difference). Then fast *bulk* operations on insertions or deletions can be implemented based on these set functions. These set operations rely on two helper operations, *Split* and *Join*. With the new operations, the implementation of red–black trees can be more efficient and highly-parallelizable.[[34]](./Red–black_tree#cite_note-join-based-34) In order to achieve its time complexities this implementation requires that the root is allowed to be either red or black, and that every node stores its own **black height**.

 
- *Join*: The function *Join* is on two red–black trees *t*1 and *t*2 and a key k, where *t*1 < *k* < *t*2, i.e. all keys in *t*1 are less than k, and all keys in *t*2 are greater than k. It returns a tree containing all elements in *t*1, *t*2 also as k.

 If the two trees have the same black height, *Join* simply creates a new node with left subtree *t*1, root k and right subtree *t*2. If both *t*1 and *t*2 have black root, set k to be red. Otherwise k is set black. If the black heights are unequal, suppose that *t*1 has larger black height than *t*2 (the other case is symmetric). *Join* follows the right spine of *t*1 until a black node c, which is balanced with *t*2. At this point a new node with left child c, root k (set to be red) and right child *t*2 is created to replace c. The new node may invalidate the red–black invariant because at most three red nodes can appear in a row. This can be fixed with a double rotation. If double red issue propagates to the root, the root is then set to be black, restoring the properties. The cost of this function is the difference of the black heights between the two input trees. 
- *Split*: To split a red–black tree into two smaller trees, those smaller than key x, and those larger than key x, first draw a path from the root by inserting x into the red–black tree. After this insertion, all values less than x will be found on the left of the path, and all values greater than x will be found on the right. By applying *Join*, all the subtrees on the left side are merged bottom-up using keys on the path as intermediate nodes from bottom to top to form the left tree, and the right part is symmetric.

 For some applications, *Split* also returns a Boolean value denoting if x appears in the tree. The cost of *Split* is     O ( log ⁡ ⁡  n ) ,   {\displaystyle O(\log n),}  ![{\displaystyle O(\log n),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d698e277a7d13ddd8b334d95be0e73986fd0cb64) order of the height of the tree. This algorithm actually has nothing to do with any special properties of a red–black tree, and may be used on any tree with a *join* operation, such as an [AVL tree](./AVL_tree). 

The join algorithm is as follows:

 
```
function joinRightRB(TL, k, TR):
    if (TL.color=black) and (TL.blackHeight=TR.blackHeight):
        return Node(TL,⟨k,red⟩,TR)
    T'=Node(TL.left,⟨TL.key,TL.color⟩,joinRightRB(TL.right,k,TR))
    if (TL.color=black) and (T'.right.color=T'.right.right.color=red):
        T'.right.right.color=black;
        return rotateLeft(T')
    return T' /* T''[recte T'] */

function joinLeftRB(TL, k, TR):
  /* symmetric to joinRightRB */

function join(TL, k, TR):
    if TL.blackHeight>TR.blackHeight:
        T'=joinRightRB(TL,k,TR)
        if (T'.color=red) and (T'.right.color=red):
            T'.color=black
        return T'
    if TR.blackHeight>TL.blackHeight:
        /* symmetric */
    if (TL.color=black) and (TR.color=black):
        return Node(TL,⟨k,red⟩,TR)
    return Node(TL,⟨k,black⟩,TR)
```
 

The split algorithm is as follows:

 
```
function split(T, k):
    if (T = NULL) return (NULL, false, NULL)
    if (k = T.key) return (T.left, true, T.right)
    if (k < T.key):
        (L',b,R') = split(T.left, k)
        return (L',b,join(R',T.key,T.right))
    (L',b,R') = split(T.right, k)
    return (join(T.left,T.key,L'),b,R')
```
 

The union of two red–black trees *t*1 and *t*2 representing sets A and B, is a red–black tree t that represents *A* ∪ *B*. The following recursive function computes this union:

 
```
function union(t1, t2):
    if t1 = NULL return t2
    if t2 = NULL return t1
    (L1,b,R1)=split(t1,t2.key)
    proc1=start:
        TL=union(L1,t2.left)
    proc2=start:
        TR=union(R1,t2.right)
    wait all proc1,proc2
    return join(TL, t2.key, TR)
```
 

Here, *split* is presumed to return two trees: one holding the keys less its input key, one holding the greater keys. (The algorithm is [non-destructive](./Persistent_data_structure), but an in-place destructive version exists also.)

 

The algorithm for intersection or difference is similar, but requires the *Join2* helper routine that is the same as *Join* but without the middle key. Based on the new functions for union, intersection or difference, either one key or multiple keys can be inserted to or deleted from the red–black tree. Since *Split* calls *Join* but does not deal with the balancing criteria of red–black trees directly, such an implementation is usually called the ["join-based" implementation](./Join-based_tree_algorithms).

 

The complexity of each of union, intersection and difference is     O  (  m log ⁡ ⁡   (    n m   + 1  )   )    {\displaystyle O\left(m\log \left({n \over m}+1\right)\right)}  ![{\displaystyle O\left(m\log \left({n \over m}+1\right)\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0cd2f7cee37ecf49ccaf8ef28ee006cb55f6b95b) for two red–black trees of sizes     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) and     n ( ≥ ≥  m )   {\displaystyle n(\geq m)}  ![{\displaystyle n(\geq m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8999105a5cf1555933b40c34c91d4a78a3c9b487). This complexity is optimal in terms of the number of comparisons. More importantly, since the recursive calls to union, intersection or difference are independent of each other, they can be executed [in parallel](./Parallel_programming) with a [parallel depth](./Analysis_of_parallel_algorithms)     O ( log ⁡ ⁡  m log ⁡ ⁡  n )   {\displaystyle O(\log m\log n)}  ![{\displaystyle O(\log m\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79240ec677da2c426ef4db2f50ff29a86cc233c).[[34]](./Red–black_tree#cite_note-join-based-34) When     m = 1   {\displaystyle m=1}  ![{\displaystyle m=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6100c5ebd48c6fd848709f2be624465203eb173), the join-based implementation has the same computational [directed acyclic graph](./Directed_acyclic_graph) (DAG) as single-element insertion and deletion if the root of the larger tree is used to split the smaller tree.

 

## Parallel algorithms

 

Parallel algorithms for constructing red–black trees from sorted lists of items can run in constant time or     O ( log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(\log \log n)}  ![{\displaystyle O(\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a9f3ded7e013a35c8039ff3276bee6e183d7f1a7) time, depending on the computer model, if the number of processors available is asymptotically proportional to the number     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) of items where     n → →  ∞ ∞    {\displaystyle n\to \infty }  ![{\displaystyle n\to \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0d55d9b32f6fa8fab6a84ea444a6b5a24bb45e1). Fast search, insertion, and deletion parallel algorithms are also known.[[35]](./Red–black_tree#cite_note-35)

 

The [join-based algorithms](./Join-based_tree_algorithms) for red–black trees are parallel for bulk operations, including union, intersection, construction, filter, map-reduce, and so on.

 

### Parallel bulk operations

 

Basic operations like insertion, removal or update can be parallelised by defining operations that process bulks of multiple elements. It is also possible to process bulks with several basic operations, for example bulks may contain elements to insert and also elements to remove from the tree.

 

The algorithms for bulk operations aren't just applicable to the red–black tree, but can be adapted to other sorted sequence data structures also, like the [2–3 tree](./2–3_tree), [2–3–4 tree](./2–3–4_tree) and [(a,b)-tree](./(a,b)-tree). In the following different algorithms for bulk insert will be explained, but the same algorithms can also be applied to removal and update. Bulk insert is an operation that inserts each element of a sequence     I   {\displaystyle I}  ![{\displaystyle I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/535ea7fc4134a31cbe2251d9d3511374bc41be9f) into a tree     T   {\displaystyle T}  ![{\displaystyle T}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec7200acd984a1d3a3d7dc455e262fbe54f7f6e0).

 

#### Join-based

 

This approach can be applied to every sorted sequence data structure that supports efficient join- and split-operations.[[36]](./Red–black_tree#cite_note-36)
The general idea is to split I and T in multiple parts and perform the insertions on these parts in parallel.

 
1. First the bulk I of elements to insert must be sorted.
2. After that, the algorithm splits I into     k ∈ ∈    N   +     {\displaystyle k\in \mathbb {N} ^{+}}  ![{\displaystyle k\in \mathbb {N} ^{+}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c8abd3366b703d9dc620115174fe692aeb5ded4) parts     ⟨ ⟨   I  1   , ⋯ ⋯  ,  I  k   ⟩ ⟩    {\displaystyle \langle I_{1},\cdots ,I_{k}\rangle }  ![{\displaystyle \langle I_{1},\cdots ,I_{k}\rangle }](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ce29ad08fbed606cec3c147cecccb40eae2fc70) of about equal sizes.
3. Next the tree T must be split into k parts     ⟨ ⟨   T  1   , ⋯ ⋯  ,  T  k   ⟩ ⟩    {\displaystyle \langle T_{1},\cdots ,T_{k}\rangle }  ![{\displaystyle \langle T_{1},\cdots ,T_{k}\rangle }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a790afd93ad6b4f84edea3111d12beecf93f00f) in a way, so that the ranges of      I  m     {\displaystyle I_{m}}  ![{\displaystyle I_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/825a86a19a0ca0180993dfe3dde997e57c5bd30a) and      T  n     {\displaystyle T_{n}}  ![{\displaystyle T_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4d9241493be76739f2400f258f32c24f9689161f) overlap for corresponding parts only (    m = n   {\displaystyle m=n}  ![{\displaystyle m=n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/69c9d8e54796e7de7d4738510cc10bc3fc55d48e)); in other words, thanks to the ordering, for every     j ∈ ∈    N   +    |   1 ≤ ≤  j < k   {\displaystyle j\in \mathbb {N} ^{+}|\,1\leq j<k}  ![{\displaystyle j\in \mathbb {N} ^{+}|\,1\leq j<k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ebcf0163612ff9a0e01e7f9986fa67a81af8b69f) following constraints hold:

1.      last  (  I  j   ) <  first  (  T  j + 1   )   {\displaystyle {\text{last}}(I_{j})<{\text{first}}(T_{j+1})}  ![{\displaystyle {\text{last}}(I_{j})<{\text{first}}(T_{j+1})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1b71d729dc4e58bf17ae09de7a16e7e1761cc8e)
2.      last  (  T  j   ) <  first  (  I  j + 1   )   {\displaystyle {\text{last}}(T_{j})<{\text{first}}(I_{j+1})}  ![{\displaystyle {\text{last}}(T_{j})<{\text{first}}(I_{j+1})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ea8ee23dcd957da50696ad1c86d69af56bcc84fb)

4. Now the algorithm inserts each element of      I  j     {\displaystyle I_{j}}  ![{\displaystyle I_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7cb04680c2246f78082e43ec912f72afe7af266) into      T  j     {\displaystyle T_{j}}  ![{\displaystyle T_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/27cdb9041c8aa769beb9153a48f41002297faacc) sequentially. This step must be performed for every j, which can be done by up to k processors in parallel.
5. Finally, the resulting trees will be joined to form the final result of the entire operation.

 

Note that in Step 3 the constraints for splitting I assure that in Step 5 the trees can be joined again and the resulting sequence is sorted.

 
- [![initial tree](//upload.wikimedia.org/wikipedia/commons/thumb/7/78/BulkInsert_JoinBased_InitialTree.svg/500px-BulkInsert_JoinBased_InitialTree.svg.png)](./File:BulkInsert_JoinBased_InitialTree.svg)initial tree
- [![split I and T](//upload.wikimedia.org/wikipedia/commons/thumb/6/69/BulkInsert_JoinBased_SplitTree.svg/500px-BulkInsert_JoinBased_SplitTree.svg.png)](./File:BulkInsert_JoinBased_SplitTree.svg)split I and T
- [![insert into the split T](//upload.wikimedia.org/wikipedia/commons/thumb/c/c8/BulkInsert_JoinBased_SplitTreeInserted.svg/500px-BulkInsert_JoinBased_SplitTreeInserted.svg.png)](./File:BulkInsert_JoinBased_SplitTreeInserted.svg)insert into the split T
- [![join T](//upload.wikimedia.org/wikipedia/commons/thumb/6/69/BulkInsert_JoinBased_JoinedTree.svg/500px-BulkInsert_JoinBased_JoinedTree.svg.png)](./File:BulkInsert_JoinBased_JoinedTree.svg)join T

 

The pseudo code shows a simple divide-and-conquer implementation of the join-based algorithm for bulk-insert.
Both recursive calls can be executed in parallel.
The join operation used here differs from the version explained in this article, instead [join2](./Join-based_tree_algorithms#Join2) is used, which misses the second parameter k.

 
```
bulkInsert(T, I, k):
    I.sort()
    bulklInsertRec(T, I, k)

bulkInsertRec(T, I, k):
    if k = 1:
        forall e in I: T.insert(e)
    else
        m := ⌊size(I) / 2⌋
        (T1, _, T2) := split(T, I[m])
        bulkInsertRec(T1, I[0 .. m], ⌈k / 2⌉)
            || bulkInsertRec(T2, I[m + 1 .. size(I) - 1], ⌊k / 2⌋)
        T ← join2(T1, T2)
```
 

##### Execution time

 

Sorting I is not considered in this analysis.

 
| #recursion levels | ∈O(log⁡k){\displaystyle \in O(\log k)} |
| --- | --- |
| T(split) + T(join) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| insertions per thread | ∈O(|I|k){\displaystyle \in O\left({\frac {|I|}{k}}\right)} |
| T(insert) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| T(bulkInsert) withk= #processors | ∈O(log⁡klog⁡|T|+|I|klog⁡|T|){\displaystyle \in O\left(\log k\log |T|+{\frac {|I|}{k}}\log |T|\right)} |

 

This can be improved by using parallel algorithms for splitting and joining.
In this case the execution time is     ∈ ∈  O  (  log ⁡ ⁡   |  T  |  +     |  I  |   k   log ⁡ ⁡   |  T  |   )    {\displaystyle \in O\left(\log |T|+{\frac {|I|}{k}}\log |T|\right)}  ![{\displaystyle \in O\left(\log |T|+{\frac {|I|}{k}}\log |T|\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/536948661f840517e2ed25d8b147cf435de56561).[[37]](./Red–black_tree#cite_note-37)

 

##### Work

 
| #splits, #joins | ∈O(k){\displaystyle \in O(k)} |
| --- | --- |
| W(split) + W(join) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| #insertions | ∈O(|I|){\displaystyle \in O(|I|)} |
| W(insert) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| W(bulkInsert) | ∈O(klog⁡|T|+|I|log⁡|T|){\displaystyle \in O(k\log |T|+|I|\log |T|)} |

 

#### Pipelining

 

Another method of parallelizing bulk operations is to use a [pipelining](./Pipeline_(computing)) approach.[[38]](./Red–black_tree#cite_note-38)
This can be done by breaking the task of processing a basic operation up into a sequence of subtasks.
For multiple basic operations the subtasks can be processed in parallel by assigning each subtask to a separate processor.

 
1. First the bulk I of elements to insert must be sorted.
2. For each element in I the algorithm locates the according insertion position in T. This can be done in parallel for each element     ∈ ∈  I   {\displaystyle \in I}  ![{\displaystyle \in I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/115150f88cabd4b520dc0251c17fe061dc4d9897) since T won't be mutated in this process. Now I must be divided into subsequences S according to the insertion position of each element. For example      s  n ,   l e f t       {\displaystyle s_{n,{\mathit {left}}}}  ![{\displaystyle s_{n,{\mathit {left}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c7268d90e4ad5f06166867efe8de95be0086766d) is the subsequence of I that contains the elements whose insertion position would be to the left of node n.
3. The middle element      m  n ,   d i r       {\displaystyle m_{n,{\mathit {dir}}}}  ![{\displaystyle m_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff172765423252c4e5d89983180604e6ce223ed) of every subsequence      s  n ,   d i r       {\displaystyle s_{n,{\mathit {dir}}}}  ![{\displaystyle s_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ff5967e5cddb49c4187a7d5725d8a9929101c60) will be inserted into T as a new node      n ′    {\displaystyle n'}  ![{\displaystyle n'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d215ec5b3d3b48ac8ec46e7131e7b3c091c9114e). This can be done in parallel for each      m  n ,   d i r       {\displaystyle m_{n,{\mathit {dir}}}}  ![{\displaystyle m_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff172765423252c4e5d89983180604e6ce223ed) since by definition the insertion position of each      m  n ,   d i r       {\displaystyle m_{n,{\mathit {dir}}}}  ![{\displaystyle m_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff172765423252c4e5d89983180604e6ce223ed) is unique. If      s  n ,   d i r       {\displaystyle s_{n,{\mathit {dir}}}}  ![{\displaystyle s_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ff5967e5cddb49c4187a7d5725d8a9929101c60) contains elements to the left or to the right of      m  n ,   d i r       {\displaystyle m_{n,{\mathit {dir}}}}  ![{\displaystyle m_{n,{\mathit {dir}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bff172765423252c4e5d89983180604e6ce223ed), those will be contained in a new set of subsequences S as      s   n ′  ,   l e f t       {\displaystyle s_{n',{\mathit {left}}}}  ![{\displaystyle s_{n',{\mathit {left}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/05dd2bb43c617237df9d93284f0f8323e4ef5cd3) or      s   n ′  ,   r i g h t       {\displaystyle s_{n',{\mathit {right}}}}  ![{\displaystyle s_{n',{\mathit {right}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2cad5a20028ec75a94a97d6066ca6c5f7980295e).
4. Now T possibly contains up to two consecutive red nodes at the end of the paths form the root to the leaves, which needs to be repaired. Note that, while repairing, the insertion position of elements     ∈ ∈  S   {\displaystyle \in S}  ![{\displaystyle \in S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/813129d6e4794d5b9c99a446b2c3683c29a539fc) have to be updated, if the corresponding nodes are affected by rotations.

- If two nodes have different nearest black ancestors, they can be repaired in parallel. Since at most four nodes can have the same nearest black ancestor, the nodes at the lowest level can be repaired in a constant number of parallel steps.
- This step will be applied successively to the black levels above until T is fully repaired.

5. The steps 3 to 5 will be repeated on the new subsequences until S is empty. At this point every element     ∈ ∈  I   {\displaystyle \in I}  ![{\displaystyle \in I}](https://wikimedia.org/api/rest_v1/media/math/render/svg/115150f88cabd4b520dc0251c17fe061dc4d9897) has been inserted. Each application of these steps is called a *stage*. Since the length of the subsequences in S is     ∈ ∈  O (  |  I  |  )   {\displaystyle \in O(|I|)}  ![{\displaystyle \in O(|I|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99a53322f6b3ed859f9ab86718ea070677723c9f) and in every stage the subsequences are being cut in half, the number of stages is     ∈ ∈  O ( log ⁡ ⁡   |  I  |  )   {\displaystyle \in O(\log |I|)}  ![{\displaystyle \in O(\log |I|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b2b1ee6732be28b2349b96f67b19e0b3cf0e0a1e).

- Since all stages move up the black levels of the tree, they can be parallelised in a pipeline. Once a stage has finished processing one black level, the next stage is able to move up and continue at that level.

 
- [![Initial tree](//upload.wikimedia.org/wikipedia/commons/thumb/f/f0/BulkInsert_Pipelining_InitialTree.svg/250px-BulkInsert_Pipelining_InitialTree.svg.png)](./File:BulkInsert_Pipelining_InitialTree.svg)Initial tree
- [![Find insert positions](//upload.wikimedia.org/wikipedia/commons/thumb/7/7c/BulkInsert_Pipelining_InsertPositions.svg/250px-BulkInsert_Pipelining_InsertPositions.svg.png)](./File:BulkInsert_Pipelining_InsertPositions.svg)Find insert positions
- [![Stage 1 inserts elements](//upload.wikimedia.org/wikipedia/commons/thumb/8/83/BulkInsert_Pipelining_Stage1Insert.svg/250px-BulkInsert_Pipelining_Stage1Insert.svg.png)](./File:BulkInsert_Pipelining_Stage1Insert.svg)Stage 1 inserts elements
- [![Stage 1 begins to repair nodes](//upload.wikimedia.org/wikipedia/commons/thumb/5/53/BulkInsert_Pipelining_Stage1Repair.svg/250px-BulkInsert_Pipelining_Stage1Repair.svg.png)](./File:BulkInsert_Pipelining_Stage1Repair.svg)Stage 1 begins to repair nodes
- [![Stage 2 inserts elements](//upload.wikimedia.org/wikipedia/commons/thumb/d/d9/BulkInsert_Pipelining_Stage2Insert.svg/250px-BulkInsert_Pipelining_Stage2Insert.svg.png)](./File:BulkInsert_Pipelining_Stage2Insert.svg)Stage 2 inserts elements
- [![Stage 2 begins to repair nodes](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/BulkInsert_Pipelining_Stage2Repair.svg/250px-BulkInsert_Pipelining_Stage2Repair.svg.png)](./File:BulkInsert_Pipelining_Stage2Repair.svg)Stage 2 begins to repair nodes
- [![Stage 3 inserts elements](//upload.wikimedia.org/wikipedia/commons/thumb/8/89/BulkInsert_Pipelining_Stage3Insert.svg/250px-BulkInsert_Pipelining_Stage3Insert.svg.png)](./File:BulkInsert_Pipelining_Stage3Insert.svg)Stage 3 inserts elements
- [![Stage 3 begins to repair nodes](//upload.wikimedia.org/wikipedia/commons/thumb/2/26/BulkInsert_Pipelining_Stage3Repair1.svg/250px-BulkInsert_Pipelining_Stage3Repair1.svg.png)](./File:BulkInsert_Pipelining_Stage3Repair1.svg)Stage 3 begins to repair nodes
- [![Stage 3 continues to repair nodes](//upload.wikimedia.org/wikipedia/commons/thumb/0/00/BulkInsert_Pipelining_Stage3Repair2.svg/250px-BulkInsert_Pipelining_Stage3Repair2.svg.png)](./File:BulkInsert_Pipelining_Stage3Repair2.svg)Stage 3 continues to repair nodes

 

##### Execution time

 

Sorting I is not considered in this analysis.
Also,      |  I  |    {\displaystyle |I|}  ![{\displaystyle |I|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b81474b934a4f217048d45013e8088b97b1311ea) is assumed to be smaller than      |  T  |    {\displaystyle |T|}  ![{\displaystyle |T|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/073a0b1ce9d4c91f30329289adbb91aae47f87ea), otherwise it would be more efficient to construct the resulting tree from scratch.

 
| T(find insert position) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| --- | --- |
| #stages | ∈O(log⁡|I|){\displaystyle \in O(\log |I|)} |
| T(insert) + T(repair) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| T(bulkInsert) with|I|{\displaystyle |I|}~ #processors | ∈O(log⁡|I|+2⋅log⁡|T|){\displaystyle \in O(\log |I|+2\cdot \log |T|)}=O(log⁡|T|){\displaystyle =O(\log |T|)} |

 

##### Work

 
| W(find insert positions) | ∈O(|I|log⁡|T|){\displaystyle \in O(|I|\log |T|)} |
| --- | --- |
| #insertions, #repairs | ∈O(|I|){\displaystyle \in O(|I|)} |
| W(insert) + W(repair) | ∈O(log⁡|T|){\displaystyle \in O(\log |T|)} |
| W(bulkInsert) | ∈O(2⋅|I|log⁡|T|){\displaystyle \in O(2\cdot |I|\log |T|)}=O(|I|log⁡|T|){\displaystyle =O(|I|\log |T|)} |

 

## See also

 
- [List of data structures](./List_of_data_structures)
- [Tree data structure](./Tree_data_structure)
- [Tree rotation](./Tree_rotation)
- [Order statistic tree](./Order_statistic_tree)
- [AA tree](./AA_tree), a variation of the red–black tree
- [Left-leaning red–black tree](./Left-leaning_red–black_tree)
- [AVL tree](./AVL_tree)
- [B-tree](./B-tree) ([2–3 tree](./2–3_tree), [2–3–4 tree](./2–3–4_tree), [B+ tree](./B+_tree), [B*-tree](./B*-tree), [UB-tree](./UB-tree))
- [Scapegoat tree](./Scapegoat_tree)
- [Splay tree](./Splay_tree)
- [T-tree](./T-tree)
- [WAVL tree](./WAVL_tree)
- [GNU libavl](http://adtinfo.org/)

 

## References and notes

 
1. [1](./Red–black_tree#cite_ref-Cormen2001_1-0) [2](./Red–black_tree#cite_ref-Cormen2001_1-1) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). "Red–Black Trees". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press. pp. [273](https://archive.org/details/introductiontoal00corm_691/page/n735)–301. [ISBN](./ISBN_(identifier)) [978-0-262-03293-3](./Special:BookSources/978-0-262-03293-3).
2. [↑](./Red–black_tree#cite_ref-wiscurl2_2-0) Paton, James. ["Red–Black Trees"](http://pages.cs.wisc.edu/~paton/readings/Red-Black-Trees/).
3. [↑](./Red–black_tree#cite_ref-3) Morris, John (1998). ["Red–Black Trees"](https://www.cs.auckland.ac.nz/software/AlgAnim/red_black.html). *Data Structures and Algorithms*.
4. [↑](./Red–black_tree#cite_ref-Bayer72_4-0) Bayer, Rudolf (1972). "Symmetric binary B-Trees: Data structure and maintenance algorithms". *Acta Informatica*. **1** (4): 290–306. [doi](./Doi_(identifier)):[10.1007/BF00289509](https://doi.org/10.1007%2FBF00289509). [S2CID](./S2CID_(identifier)) [28836825](https://api.semanticscholar.org/CorpusID:28836825).
5. [↑](./Red–black_tree#cite_ref-5) Drozdek, Adam (2001). *Data Structures and Algorithms in Java* (2 ed.). Sams Publishing. p. 323. [ISBN](./ISBN_(identifier)) [978-0534376680](./Special:BookSources/978-0534376680).
6. [1](./Red–black_tree#cite_ref-GS78_6-0) [2](./Red–black_tree#cite_ref-GS78_6-1) [Guibas, Leonidas J.](./Leonidas_J._Guibas); [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1978). "A Dichromatic Framework for Balanced Trees". *Proceedings of the 19th Annual Symposium on Foundations of Computer Science*. pp. 8–21. [doi](./Doi_(identifier)):[10.1109/SFCS.1978.3](https://doi.org/10.1109%2FSFCS.1978.3).
7. [↑](./Red–black_tree#cite_ref-7) ["Red Black Trees"](https://web.archive.org/web/20070927222509/http://eternallyconfuzzled.com/tuts/datastructures/jsw_tut_rbtree.aspx). *eternallyconfuzzled.com*. Archived from [the original](http://eternallyconfuzzled.com/tuts/datastructures/jsw_tut_rbtree.aspx) on 2007-09-27. Retrieved 2015-09-02.
8. [↑](./Red–black_tree#cite_ref-Sedgewick12_8-0) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (2012). [*Red–Black BSTs*](https://www.coursera.org/learn/algorithms-graphs-data-structures/lecture/8acpe/red-black-trees). Coursera. A lot of people ask why did we use the name red–black. Well, we invented this data structure, this way of looking at balanced trees, at Xerox PARC that was the home of the personal computer and many other innovations that we live with today entering[sic] graphic user interfaces, Ethernet and object-oriented programmings[sic] and many other things. But one of the things that was invented there was laser printing and we were very excited to have nearby color laser printer that could print things out in color and out of the colors the red looked the best. So, that's why we picked the color red to distinguish red links, the types of links, in three nodes. So, that's an answer to the question for people that have been asking. 
9. [↑](./Red–black_tree#cite_ref-9) ["Where does the term "Red/Black Tree" come from?"](http://programmers.stackexchange.com/a/116621/40127). *programmers.stackexchange.com*. Retrieved 2015-09-02.
10. [↑](./Red–black_tree#cite_ref-10) Andersson, Arne (1993-08-11). ["Balanced search trees made simple"](https://web.archive.org/web/20181208183054/https://www.springer.com/la/book/9783540571551). In Dehne, Frank; Sack, Jörg-Rüdiger; Santoro, Nicola; Whitesides, Sue (eds.). *Algorithms and Data Structures* (Proceedings). Lecture Notes in Computer Science. Vol. 709. Springer-Verlag Berlin Heidelberg. pp. 60–71. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.118.6192](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.118.6192). [doi](./Doi_(identifier)):[10.1007/3-540-57155-8_236](https://doi.org/10.1007%2F3-540-57155-8_236). [ISBN](./ISBN_(identifier)) [978-3-540-57155-1](./Special:BookSources/978-3-540-57155-1). Archived from [the original](https://www.springer.com/la/book/9783540571551) on 2018-12-08. [Alt URL](http://user.it.uu.se/~arnea/ps/simp.pdf)
11. [↑](./Red–black_tree#cite_ref-11) Okasaki, Chris (1999-01-01). ["Red–black trees in a functional setting"](https://doi.org/10.1017%2FS0956796899003494). *Journal of Functional Programming*. **9** (4): 471–477. [doi](./Doi_(identifier)):[10.1017/S0956796899003494](https://doi.org/10.1017%2FS0956796899003494). [ISSN](./ISSN_(identifier)) [1469-7653](https://search.worldcat.org/issn/1469-7653). [S2CID](./S2CID_(identifier)) [20298262](https://api.semanticscholar.org/CorpusID:20298262).
12. [↑](./Red–black_tree#cite_ref-Algs1_12-0) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1983). [*Algorithms*](https://archive.org/details/algorithms00sedg) (1st ed.). [Addison-Wesley](./Addison-Wesley). [ISBN](./ISBN_(identifier)) [978-0-201-06672-2](./Special:BookSources/978-0-201-06672-2).
13. [↑](./Red–black_tree#cite_ref-13) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Wayne, Kevin. ["RedBlackBST.java"](http://algs4.cs.princeton.edu/code/edu/princeton/cs/algs4/RedBlackBST.java.html). *algs4.cs.princeton.edu*. Retrieved 7 April 2018.
14. [↑](./Red–black_tree#cite_ref-14) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (2008). ["Left-leaning Red–Black Trees"](https://sedgewick.io/wp-content/themes/sedgewick/papers/2008LLRB.pdf) (PDF).
15. [1](./Red–black_tree#cite_ref-Algs4_15-0) [2](./Red–black_tree#cite_ref-Algs4_15-1) [3](./Red–black_tree#cite_ref-Algs4_15-2) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Wayne, Kevin (2011). [*Algorithms*](http://algs4.cs.princeton.edu) (4th ed.). Addison-Wesley Professional. [ISBN](./ISBN_(identifier)) [978-0-321-57351-3](./Special:BookSources/978-0-321-57351-3).
16. [1](./Red–black_tree#cite_ref-Mehlhorn2008_16-0) [2](./Red–black_tree#cite_ref-Mehlhorn2008_16-1) [3](./Red–black_tree#cite_ref-Mehlhorn2008_16-2) [4](./Red–black_tree#cite_ref-Mehlhorn2008_16-3) [Mehlhorn, Kurt](./Kurt_Mehlhorn); [Sanders, Peter](./Peter_Sanders_(computer_scientist)) (2008). ["7. Sorted Sequences"](http://people.mpi-inf.mpg.de/~mehlhorn/ftp/Toolbox/SortedSequences.pdf) (PDF). [*Algorithms and Data Structures: The Basic Toolbox*](http://people.mpi-inf.mpg.de/~mehlhorn/Toolbox.html). Berlin/Heidelberg: Springer. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.148.2305](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.148.2305). [doi](./Doi_(identifier)):[10.1007/978-3-540-77978-0](https://doi.org/10.1007%2F978-3-540-77978-0). [ISBN](./ISBN_(identifier)) [978-3-540-77977-3](./Special:BookSources/978-3-540-77977-3).
17. [1](./Red–black_tree#cite_ref-Cormen2009_17-0) [2](./Red–black_tree#cite_ref-Cormen2009_17-1) [Cormen, Thomas](./Thomas_H._Cormen); [Leiserson, Charles](./Charles_E._Leiserson); [Rivest, Ronald](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2022). "13. Red–Black Trees". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (4th ed.). [MIT Press](./MIT_Press). pp. [331](https://archive.org/details/introductiontoal00corm_805/page/n328)–332. [ISBN](./ISBN_(identifier)) [9780262046305](./Special:BookSources/9780262046305).
18. [↑](./Red–black_tree#cite_ref-18) Using Knuth’s definition of order: the maximum number of children
19. [↑](./Red–black_tree#cite_ref-19) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (1998). [*Algorithms in C++*](https://archive.org/details/algorithmscparts00sedg). Addison-Wesley Professional. pp. [565](https://archive.org/details/algorithmscparts00sedg/page/n569)–575. [ISBN](./ISBN_(identifier)) [978-0-201-35088-3](./Special:BookSources/978-0-201-35088-3).
20. [↑](./Red–black_tree#cite_ref-20) ["IBM Developer"](https://developer.ibm.com/tutorials/l-completely-fair-scheduler/). *developer.ibm.com*. Retrieved 25 May 2024.
21. [↑](./Red–black_tree#cite_ref-21) ["The Implementation of epoll (1)"](https://web.archive.org/web/20201011122015/https://idndx.com/2014/09/01/the-implementation-of-epoll-1/). *Datong's Random Thoughts*. September 2014. Archived from [the original](https://idndx.com/2014/09/01/the-implementation-of-epoll-1/) on 2020-10-11. Retrieved 2018-06-25.
22. [↑](./Red–black_tree#cite_ref-22) [Pfaff 2004](./Red–black_tree#Pfaff_b)
23. [1](./Red–black_tree#cite_ref-LLRB_23-0) [2](./Red–black_tree#cite_ref-LLRB_23-1) ["Robert Sedgewick"](http://www.cs.princeton.edu/~rs/talks/LLRB/RedBlack.pdf) (PDF). *Cs.princeton.edu*. 4 June 2020. Retrieved 26 March 2022.
24. [↑](./Red–black_tree#cite_ref-24) ["Balanced Trees"](http://www.cs.princeton.edu/courses/archive/fall08/cos226/lectures/10BalancedTrees-2x2.pdf) (PDF). *Cs.princeton.edu*. Retrieved 26 March 2022.
25. [↑](./Red–black_tree#cite_ref-DHIP_25-0) Demaine, E. D.; Harmon, D.; Iacono, J.; Pătraşcu, M. (2007). ["Dynamic Optimality—Almost"](http://erikdemaine.org/papers/Tango_SICOMP/paper.pdf) (PDF). *SIAM Journal on Computing*. **37** (1): 240. [doi](./Doi_(identifier)):[10.1137/S0097539705447347](https://doi.org/10.1137%2FS0097539705447347). [S2CID](./S2CID_(identifier)) [1480961](https://api.semanticscholar.org/CorpusID:1480961).
26. [↑](./Red–black_tree#cite_ref-26) ["How does a HashMap work in JAVA"](http://coding-geek.com/how-does-a-hashmap-work-in-java/#JAVA_8_improvements). coding-geek.com.
27. [↑](./Red–black_tree#cite_ref-tarjan_27-0) [Tarjan, Robert Endre](./Robert_Tarjan) (April 1985). ["Amortized Computational Complexity"](http://www.cs.duke.edu/courses/fall11/cps234/reading/Tarjan85_AmortizedComplexity.pdf) (PDF). *SIAM Journal on Algebraic and Discrete Methods*. **6** (2): 306–318. [doi](./Doi_(identifier)):[10.1137/0606031](https://doi.org/10.1137%2F0606031).
28. [↑](./Red–black_tree#cite_ref-28) The important thing about these tree rotations is that they preserve the in-order sequence of the tree’s nodes.
29. [1](./Red–black_tree#cite_ref-pullout_29-0) [2](./Red–black_tree#cite_ref-pullout_29-1) The left columns contain far less nodes than the right ones, especially for removal. This indicates that some efficiency can be gained by pulling the first iteration out of the rebalancing loops of insertion and deletion, because many of the named nodes are NIL nodes in the first iteration and definitively non-NIL later. (See also [this remark](./Red–black_tree#C-eval).)
30. [↑](./Red–black_tree#cite_ref-30) Rotations have been placed before recoloring for reasons of clarity. But the two commute, so that it is free choice to move the rotation to the [tail](./Tail_call).
31. [1](./Red–black_tree#cite_ref-cases_31-0) [2](./Red–black_tree#cite_ref-cases_31-1) The same partitioning is found in [Ben Pfaff](./Red–black_tree#Pfaff_a).
32. [↑](./Red–black_tree#cite_ref-32) Dinesh P. Mehta, Sartaj Sahni (Ed.) *Handbook of Data Structures and Applications* 10.4.2
33. [↑](./Red–black_tree#cite_ref-33) Equality at the upper bound holds for the minimal RB trees RB2*k* of even height     2 ⋅ ⋅  k   {\displaystyle 2\cdot k}  ![{\displaystyle 2\cdot k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eaab9b8c5c6b4924fb6da98fa8994a117a2d8a60) with     n = 2 ⋅ ⋅   2  k   − −  2   {\displaystyle n=2\cdot 2^{k}-2}  ![{\displaystyle n=2\cdot 2^{k}-2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/75f5445a7d138357f7f6db91694aa7086431a670) nodes and only for those. So the inequality is marginally more precise than the widespread     h < 2  log  2   ⁡ ⁡  ( n + 1 ) ,   {\displaystyle h<2\log _{2}(n+1),}  ![{\displaystyle h<2\log _{2}(n+1),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/331e7a9177069dea58756c429f4930a8fe326ce6) e.g. in [Cormen](./Red–black_tree#Cormen) p. 264.
Moreover, these trees are binary trees that admit one and only one coloring conforming to the RB requirements 1 to 4. But there are further such trees, e.g. appending a child node to a black leaf always forces it to red. (A minimal RB tree of odd height allows to flip the root’s color from red to black.)
34. [1](./Red–black_tree#cite_ref-join-based_34-0) [2](./Red–black_tree#cite_ref-join-based_34-1) [Blelloch, Guy E.](./Guy_Blelloch); Ferizovic, Daniel; [Sun, Yihan](./Yihan_Sun?action=edit&redlink=1) (2016). ["Just Join for Parallel Ordered Sets"](http://www.cs.cmu.edu/~yihans/papers/join.pdf) (PDF). *Proceedings of the 28th ACM Symposium on Parallelism in Algorithms and Architectures*. ACM. pp. 253–264. [arXiv](./ArXiv_(identifier)):[1602.02120](https://arxiv.org/abs/1602.02120). [doi](./Doi_(identifier)):[10.1145/2935764.2935768](https://doi.org/10.1145%2F2935764.2935768). [ISBN](./ISBN_(identifier)) [978-1-4503-4210-0](./Special:BookSources/978-1-4503-4210-0). [S2CID](./S2CID_(identifier)) [2897793](https://api.semanticscholar.org/CorpusID:2897793)..
35. [↑](./Red–black_tree#cite_ref-35)  Park, Heejin; Park, Kunsoo (2001). ["Parallel algorithms for red–black trees"](https://doi.org/10.1016%2FS0304-3975%2800%2900287-5). *Theoretical Computer Science*. **262** (1–2): 415–435. [doi](./Doi_(identifier)):[10.1016/S0304-3975(00)00287-5](https://doi.org/10.1016%2FS0304-3975%2800%2900287-5). Our parallel algorithm for constructing a red–black tree from a sorted list of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) items runs in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) processors on the CRCW PRAM and runs in     O ( log ⁡ ⁡  log ⁡ ⁡  n )   {\displaystyle O(\log \log n)}  ![{\displaystyle O(\log \log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a9f3ded7e013a35c8039ff3276bee6e183d7f1a7) time with     n  /  log ⁡ ⁡  log ⁡ ⁡  n   {\displaystyle n/\log \log n}  ![{\displaystyle n/\log \log n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9119ed2a7f5be8c422203f04acf6dcc63da14220) processors on the EREW PRAM.
36. [↑](./Red–black_tree#cite_ref-36) Sanders, Peter (2019). Mehlhorn, Kurt; Dietzfelbinger, Martin; Dementiev, Roman (eds.). *Sequential and Parallel Algorithms and Data Structures : The Basic Toolbox*. Springer eBooks. Cham: Springer. pp. 252–253. [doi](./Doi_(identifier)):[10.1007/978-3-030-25209-0](https://doi.org/10.1007%2F978-3-030-25209-0). [ISBN](./ISBN_(identifier)) [9783030252090](./Special:BookSources/9783030252090). [S2CID](./S2CID_(identifier)) [201692657](https://api.semanticscholar.org/CorpusID:201692657).
37. [↑](./Red–black_tree#cite_ref-37) Akhremtsev, Yaroslav; Sanders, Peter (2016). "Fast Parallel Operations on Search Trees". *2016 IEEE 23rd International Conference on High Performance Computing (HiPC)*. pp. 291–300. [arXiv](./ArXiv_(identifier)):[1510.05433](https://arxiv.org/abs/1510.05433). [doi](./Doi_(identifier)):[10.1109/HiPC.2016.042](https://doi.org/10.1109%2FHiPC.2016.042). [ISBN](./ISBN_(identifier)) [978-1-5090-5411-4](./Special:BookSources/978-1-5090-5411-4).
38. [↑](./Red–black_tree#cite_ref-38) Jájá, Joseph (1992). [*An introduction to parallel algorithms*](http://zbmath.org/?q=an:0781.68009). Reading, Mass. [u.a.]: Addison-Wesley. pp. 65–70. [ISBN](./ISBN_(identifier)) [0201548569](./Special:BookSources/0201548569). [Zbl](./Zbl_(identifier)) [0781.68009](https://zbmath.org/?format=complete&q=an:0781.68009).

 

## Further reading

 
- [Mathworld: Red–Black Tree](http://mathworld.wolfram.com/Red-BlackTree.html)
- [San Diego State University: CS 660: Red–Black tree notes](http://www.eli.sdsu.edu/courses/fall95/cs660/notes/RedBlackTree/RedBlack.html#RTFToC2), by Roger Whitney
-  Pfaff, Ben (June 2004). ["Performance Analysis of BSTs in System Software"](http://www.stanford.edu/~blp/papers/libavl.pdf) (PDF). [Stanford University](./Stanford_University).

 

## External links

 
- Ben Pfaff: *An Introduction to Binary Search Trees and Balanced Trees.* Free Software Foundation, Boston 2004, [ftp.gnu.org](https://ftp.gnu.org/gnu/avl/avl-2.0.3.pdf.gz) (PDF gzip; 1662 kB)
- [A complete and working implementation in C](https://web.archive.org/web/20140328232325/http://en.literateprograms.org/Red-black_tree_(C))
- [OCW MIT Lecture on Red-black Trees](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/video-lectures/lecture-10-red-black-trees-rotations-insertions-deletions/) by [Erik Demaine](./Erik_Demaine)
- [Binary Search Tree Insertion Visualization](https://www.youtube.com/watch?v=_VbTnLV8plU) on [YouTube](./YouTube_video_(identifier)) – Visualization of random and pre-sorted data insertions, in elementary binary search trees, and left-leaning red–black trees
- [An intrusive red–black tree written in C++](https://gist.github.com/pallas/10697727)
- Red–black BSTs in [3.3 Balanced Search Trees](https://algs4.cs.princeton.edu/33balanced/)
- [Red–black BST Demo](https://web.archive.org/web/20160722175219/http://algs4.cs.princeton.edu/lectures/33DemoRedBlackBST.mov)

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |