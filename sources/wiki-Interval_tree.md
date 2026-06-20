---
source: https://en.wikipedia.org/wiki/Interval_tree
fetched: 2026-06-19
---

Not to be confused with [segment tree](./Segment_tree). Tree data structure to hold intervals 

In [computer science](./Computer_science), an **interval tree** is a [tree data structure](./Tree_(data_structure)) to hold [intervals](./Interval_(mathematics)). Specifically, it allows one to efficiently find all intervals that overlap with any given interval or point. It is often used for windowing queries,[[1]](./Interval_tree#cite_note-1) for instance, to find all roads on a computerized map inside a rectangular viewport, or to find all visible elements inside a three-dimensional scene. A similar data structure is the [segment tree](./Segment_tree).

 

The trivial solution is to visit each interval and test whether it intersects the given point or interval, which requires     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of intervals in the collection. Since a query may return all intervals, for example if the query is a large interval intersecting all intervals in the collection, this is [asymptotically optimal](./Asymptotically_optimal); however, [output-sensitive algorithms](./Output-sensitive_algorithm), where the runtime is expressed in terms of     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) (the number of intervals produced by the query) may also be considered. Interval trees have a query time of     O ( log ⁡ ⁡  n + m )   {\displaystyle O(\log n+m)}  ![{\displaystyle O(\log n+m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e8f08f139c8022b2da3554deebfcd48995028db6) and an initial creation time of     O ( n log ⁡ ⁡  n )   {\displaystyle O(n\log n)}  ![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1), while limiting memory consumption to     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a). After creation, interval trees may be dynamic, allowing efficient insertion and deletion of an interval in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time. If the endpoints of intervals are within a small integer range (*e.g.*, in the range     [ 1 , … …  , O ( n ) ]   {\displaystyle [1,\ldots ,O(n)]}  ![{\displaystyle [1,\ldots ,O(n)]}](https://wikimedia.org/api/rest_v1/media/math/render/svg/292672ded6aef6ae4a14183608844cb053711060)), faster and in fact optimal data structures exist[[2]](./Interval_tree#cite_note-Schmidt2009-2)[[3]](./Interval_tree#cite_note-3) with preprocessing time     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) and query time     O ( 1 + m )   {\displaystyle O(1+m)}  ![{\displaystyle O(1+m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0347e8f69f1f556f5493edc2c8da90c3113babfb) for reporting     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) intervals containing a given query point (see[[2]](./Interval_tree#cite_note-Schmidt2009-2) for a very simple one).

 

## Naïve approach

 

In a simple case, the intervals do not overlap and they can be inserted into a simple [binary search tree](./Binary_search_tree) and queried in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time. However, with arbitrarily overlapping intervals, there is no way to compare two intervals for insertion into the tree since orderings sorted by the beginning points or the ending points may be different. A naïve approach might be to build two parallel trees, one ordered by the beginning point, and one ordered by the ending point of each interval. This allows discarding half of each tree in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, but the results must be merged, requiring     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) time. This returns queries in     O ( n + log ⁡ ⁡  n ) = O ( n )   {\displaystyle O(n+\log n)=O(n)}  ![{\displaystyle O(n+\log n)=O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c7504fd00f2630fdf659d4b931d6d98658ea67f), which is no better than brute-force.

 

Interval trees solve this problem. This article describes two alternative designs for an interval tree, dubbed the *centered interval tree* and the *augmented tree*.

 

## Centered interval tree

 

Queries require     O ( log ⁡ ⁡  n + m )   {\displaystyle O(\log n+m)}  ![{\displaystyle O(\log n+m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e8f08f139c8022b2da3554deebfcd48995028db6) time, with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) being the total number of intervals and     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) being the number of reported results. Construction requires     O ( n log ⁡ ⁡  n )   {\displaystyle O(n\log n)}  ![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1) time, and storage requires     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) space.

 

### Construction

 

Given a set of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) intervals on the number line, a data structure needs to be constructed so that all intervals overlapping another interval or point can be efficiently retrieved.

 

First, the entire range of all the intervals is taken and divided in half at      x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339) (in practice,        x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339) should be picked to keep the tree relatively balanced). This gives three sets of intervals, those completely to the left of        x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), called      S   left      {\displaystyle S_{\textrm {left}}}  ![{\displaystyle S_{\textrm {left}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/59bcdd25a9823a27ed9194e0d8bcd1fee4f47c5d), those completely to the right of      x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), called       S   right      {\displaystyle S_{\textrm {right}}}  ![{\displaystyle S_{\textrm {right}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/646282c786c1d477f58970e41ea7020357c58548), and those overlapping      x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), called      S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1).

 

The intervals in       S   left      {\displaystyle S_{\textrm {left}}}  ![{\displaystyle S_{\textrm {left}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/59bcdd25a9823a27ed9194e0d8bcd1fee4f47c5d) and       S   right      {\displaystyle S_{\textrm {right}}}  ![{\displaystyle S_{\textrm {right}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/646282c786c1d477f58970e41ea7020357c58548) are recursively divided in the same manner until there are no intervals left.

 

The intervals in      S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) that overlap the center point are stored in a separate data structure linked to the node in the interval tree. This data structure consists of two lists, one containing all the intervals sorted by their beginning points, and another containing all the intervals sorted by their ending points.

 

The result is a [binary tree](./Binary_tree) with each node storing:

 
- A center point
- A pointer to another node containing all intervals completely to the left of the center point
- A pointer to another node containing all intervals completely to the right of the center point
- All intervals overlapping the center point sorted by their beginning point
- All intervals overlapping the center point sorted by their ending point

 

### Intersecting

 

Interval trees allow for quickly computing all the ranges overlapping any input.

 

#### With a point

 

The task is to find all intervals in the tree that overlap a given point     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4). The tree is walked with a similar recursive algorithm as would be used to traverse a traditional binary tree, but with extra logic to support searching the intervals overlapping the "center" point at each node.

 

For each tree node,     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is compared to       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), the midpoint used in node construction above.  If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is less than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), the leftmost set of intervals,       S   left      {\displaystyle S_{\textrm {left}}}  ![{\displaystyle S_{\textrm {left}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/59bcdd25a9823a27ed9194e0d8bcd1fee4f47c5d), is considered. If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is greater than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), the rightmost set of intervals,       S   right      {\displaystyle S_{\textrm {right}}}  ![{\displaystyle S_{\textrm {right}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/646282c786c1d477f58970e41ea7020357c58548), is considered.

 [![](//upload.wikimedia.org/wikipedia/en/thumb/0/0d/Check_if_a_point_overlaps_the_intervals_in_S_center_of_a_centered_interval_tree.svg/330px-Check_if_a_point_overlaps_the_intervals_in_S_center_of_a_centered_interval_tree.svg.png)](./File:Check_if_a_point_overlaps_the_intervals_in_S_center_of_a_centered_interval_tree.svg)All intervals in       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) that begin before     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) must overlap     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) if     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is less than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339).
Similarly, the same technique also applies in checking a given interval. If a given interval ends at  *y* and *y* is less than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), all intervals in       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) that begin before *y* must also overlap the given interval. 

As each node is processed as the tree is traversed from the root to a leaf, the ranges in its       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) are processed. If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is less than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), all intervals in       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) must end after     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), or they could not also overlap       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339). Therefore, it is only necessary find those intervals in      S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) that begin before     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4). The lists of      S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1), which have already been constructed, can be consulted. Since only the interval beginnings are relevant in this scenario, the list can be sorted by beginnings. If the closest number no greater than     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is found in this list, all ranges from the beginning of the list to that found point overlap     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) because they begin before     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) and end after     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) (because they overlap      x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339) which is larger than     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4)). Thus, the intervals in the list can be enumerated until the startpoint value exceeds     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4).

 

Likewise, if     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is greater than       x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), all intervals in       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) must begin before     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), so the intervals that end after     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) can be found using the list sorted by interval endings.

 

If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) exactly matches      x   center      {\displaystyle x_{\textrm {center}}}  ![{\displaystyle x_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/610d04c729413d931e262ba95dd82557bb72f339), all intervals in      S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) can be added to the results without further processing and tree traversal can be stopped.

 

#### With an interval

 

For a result interval     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) to intersect the query interval     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) one of the following must hold:

 
- either the start or end point of     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is in     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d); or
-     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) completely encloses     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d).

 
|  | This articlemay beconfusing or unclearto readers.Please helpclarify the article. There might be a discussion about this onthe talk page.(February 2020)(Learn how and when to remove this message) |
| --- | --- |

 

We first find all intervals with start and/or end points inside     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) using a separately-constructed tree. In the one-dimensional case, we can use a search tree containing all the start and end points in the interval set, each with a pointer to its corresponding interval. A binary search in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time for the start and end of     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) reveals the minimum and maximum points to consider. Each point within this range references an interval that overlaps     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) and is added to the result list. Care must be taken to avoid duplicates, since an interval might both begin and end within     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d). This can be done using a binary flag on each interval to mark whether or not it has been added to the result set.

 

Finally, we must find intervals that enclose     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d). To find these, we pick any point inside     q   {\displaystyle q}  ![{\displaystyle q}](https://wikimedia.org/api/rest_v1/media/math/render/svg/06809d64fa7c817ffc7e323f85997f783dbdf71d) and use the algorithm above to find all intervals intersecting that point (again, being careful to remove duplicates).

 

### Higher dimensions

 

The interval tree data structure can be generalized to a higher dimension     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) with identical query and construction time and     O ( n log ⁡ ⁡  n )   {\displaystyle O(n\log n)}  ![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1) space.

 

First, a [range tree](./Range_tree) in     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) dimensions is constructed that allows efficient retrieval of all intervals with beginning and end points inside the query region     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33). Once the corresponding ranges are found, the only thing that is left are those ranges that enclose the region in some dimension. To find these overlaps,      N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) interval trees are created, and one axis intersecting     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) is queried for each. For example, in two dimensions, the bottom of the square      R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) (or any other horizontal line intersecting     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33)) would be queried against the interval tree constructed for the horizontal axis. Likewise, the left (or any other vertical line intersecting     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33)) would be queried against the interval tree constructed on the vertical axis.

 

Each interval tree also needs an addition for higher dimensions. At each node we traverse in the tree,     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) is compared with       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) to find overlaps. Instead of two sorted lists of points as was used in the one-dimensional case, a range tree is constructed. This allows efficient retrieval of all points in       S   center      {\displaystyle S_{\textrm {center}}}  ![{\displaystyle S_{\textrm {center}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec18349b29033c28e5d6c99ddb8c8c22872e7ff1) that overlap region     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33).

 

### Deletion

 

If after deleting an interval from the tree, the node containing that interval contains no more intervals, that node may be deleted from the tree. This is more complex than a normal binary tree deletion operation.

 

An interval may overlap the center point of several nodes in the tree. Since each node stores the intervals that overlap it, with all intervals completely to the left of its center point in the left subtree, similarly for the right subtree, it follows that each interval is stored in the node closest to the root from the set of nodes whose center point it overlaps.

 

Normal deletion operations in a binary tree (for the case where the node being deleted has two children) involve promoting a node further from the leaf to the position of the node being deleted (usually the leftmost child of the right subtree, or the rightmost child of the left subtree).

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/46/Binary_search_tree_delete.svg/960px-Binary_search_tree_delete.svg.png)](./File:Binary_search_tree_delete.svg)Deleting a node with two children from a binary search tree using the in-order predecessor (rightmost node in the left subtree, labelled **6**). 

As a result of this promotion, some nodes that were above the promoted node will become its descendants; it is necessary to search these nodes for intervals that also overlap the promoted node, and move those intervals into the promoted node. As a consequence, this may result in new empty nodes, which must be deleted, following the same algorithm again.

 

### Balancing

 

The same issues that affect deletion also affect rotation operations; rotation must preserve the invariant that nodes are stored as close to the root as possible.

 

## Augmented tree

 [![](//upload.wikimedia.org/wikipedia/en/b/b0/Example_of_augmented_tree_with_low_value_as_the_key_and_maximum_high_as_extra_annotation.png)](./File:Example_of_augmented_tree_with_low_value_as_the_key_and_maximum_high_as_extra_annotation.png)An augmented tree with low value as the key and maximum high as the extra annotation.For example, when testing if the given interval *[40 ,60)* overlaps the intervals in the tree shown above, we see that it does not overlap the interval *[20, 36)* in the root, but since the root's low value (20) is less than the sought high value (60), we must search the right subtree.  The left subtree's maximum high of 41 exceeds the sought low value (40), so we must search the left subtree as well.  However, both descendants of the *[3, 41)* node have maximum highs less than 40, so the left subtree search ends there and it is not necessary to search them. 

Another way to represent intervals is described in [Cormen et al. (2009](./Interval_tree#CITEREFCormenLeisersonRivestStein2009), Section 14.3: Interval trees, pp. 348–354).

 

Both insertion and deletion require     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) being the total number of intervals in the tree prior to the insertion or deletion operation.

 

An augmented tree can be built from a simple ordered tree, for example a [binary search tree](./Binary_search_tree) or [self-balancing binary search tree](./Self-balancing_binary_search_tree), ordered by the 'low' values of the intervals. An extra annotation is then added to every node, recording the maximum upper value among all the intervals from this node down. Maintaining this attribute involves updating all ancestors of the node from the bottom up whenever a node is added or deleted. This takes only O(*h*) steps per node addition or removal, where *h* is the height of the node added or removed in the tree. If there are any [tree rotations](./Tree_rotation) during insertion and deletion, the affected nodes may need updating as well.

 

Now, it is known that two intervals     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) and     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) overlap only when both      A   low    ≤ ≤   B   high      {\displaystyle A_{\textrm {low}}\leq B_{\textrm {high}}}  ![{\displaystyle A_{\textrm {low}}\leq B_{\textrm {high}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c206f7ae59ba8ff11b5a2d9a09710fc46702cde4) and      A   high    ≥ ≥   B   low      {\displaystyle A_{\textrm {high}}\geq B_{\textrm {low}}}  ![{\displaystyle A_{\textrm {high}}\geq B_{\textrm {low}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/193391cf66ca03f97e1224d16c0161c6baab6eae). When searching the trees for nodes overlapping with a given interval, you can immediately skip:

 
- all nodes to the right of nodes whose low value is past the end of the given interval.
- all nodes that have their maximum high value below the start of the given interval.

 

### Membership queries

 

Some performance may be gained if the tree avoids unnecessary traversals. These can occur when adding intervals that already exist or removing intervals that don't exist.

 

A total order can be defined on the intervals by ordering them first by their lower bounds and then by their upper bounds. Then, a membership check can be performed in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, versus the     O ( k + log ⁡ ⁡  n )   {\displaystyle O(k+\log n)}  ![{\displaystyle O(k+\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/52ea4d30b861cebb6d7deaf008c82812da9579a5) time required to find duplicates if     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) intervals overlap the interval to be inserted or removed. This solution has the advantage of not requiring any additional structures. The change is strictly algorithmic. The disadvantage is that membership queries take     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time.

 

Alternately, at the rate of     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) memory, membership queries in expected constant time can be implemented with a hash table, updated in lockstep with the interval tree. This may not necessarily double the total memory requirement, if the intervals are stored by reference rather than by value.

 

### Java example: Adding a new interval to the tree

 

The key of each node is the interval itself, hence nodes are ordered first by low value and finally by high value, and the value of each node is the end point of the interval:

 
```
public void add(Interval i) {
    put(i, i.getEnd());
}

```
 

### Java example: Searching a point or an interval in the tree

 

To search for an interval, one walks the tree, using the key (`n.getKey()`) and high value (`n.getValue()`) to omit any branches that cannot overlap the query. The simplest case is a point query:

 
```
// Search for all intervals containing "p", starting with the
// node "n" and adding matching intervals to the list "result"
public void search(IntervalNode n, Point p, List<Interval> result) {
    // Don't search nodes that don't exist
    if (n == null)
        return;

    // If p is to the right of the rightmost point of any interval
    // in this node and all children, there won't be any matches.
    if (p.compareTo(n.getValue()) > 0)
        return;

    // Search left children
    search(n.getLeft(), p, result);

    // Check this node
    if (n.getKey().contains(p))
        result.add(n.getKey());

    // If p is to the left of the start of this interval,
    // then it can't be in any child to the right.
    if (p.compareTo(n.getKey().getStart()) < 0)
        return;

    // Otherwise, search right children
    search(n.getRight(), p, result);
}

```
 

where

 `a.compareTo(b)` returns a negative value if a < b `a.compareTo(b)` returns zero if a = b `a.compareTo(b)` returns a positive value if a > b 

The code to search for an interval is similar, except for the check in the middle:

 
```
// Check this node
if (n.getKey().overlapsWith(i))
    result.add (n.getKey());

```
 

`overlapsWith()` is defined as:

 
```
public boolean overlapsWith(Interval other) {
    return start.compareTo(other.getEnd()) <= 0 &&
           end.compareTo(other.getStart()) >= 0;
}

```
 

### Higher dimensions

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(November 2022)(Learn how and when to remove this message) |
| --- | --- |

 

Augmented trees can be extended to higher dimensions by cycling through the dimensions at each level of the tree. For example, for two dimensions, the odd levels of the tree might contain ranges for the *x*-coordinate, while the even levels contain ranges for the *y*-coordinate. This approach effectively converts the data structure from an augmented binary tree to an augmented [kd-tree](./Kd-tree), thus significantly complicating the balancing algorithms for insertions and deletions.

 

A simpler solution is to use nested interval trees. First, create a tree using the ranges for the *y*-coordinate. Now, for each node in the tree, add another interval tree on the *x*-ranges, for all elements whose *y*-range is the same as that node's *y*-range.

 

The advantage of this solution is that it can be extended to an arbitrary number of dimensions using the same code base.

 

At first, the additional cost of the nested trees might seem prohibitive, but this is usually not so. As with the non-nested solution earlier, one node is needed per *x*-coordinate, yielding the same number of nodes for both solutions. The only additional overhead is that of the nested tree structures, one per vertical interval. This structure is usually of negligible size, consisting only of a pointer to the root node, and possibly the number of nodes and the depth of the tree.

 

## Medial- or length-oriented tree

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(October 2016)(Learn how and when to remove this message) |
| --- | --- |

 

A medial- or length-oriented tree is similar to an augmented tree, but symmetrical, with the binary search tree ordered by the medial points of the intervals. There is a maximum-oriented [binary heap](./Binary_heap) in every node, ordered by the length of the interval (or half of the length). Also we store the minimum and maximum possible value of the subtree in each node (thus the symmetry).

 

### Overlap test

 

Using only start and end values of two intervals      (   a  i   ,  b  i    )    {\displaystyle \left(a_{i},b_{i}\right)}  ![{\displaystyle \left(a_{i},b_{i}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec5beeb80bbc35b0973fbb222e41e717269125ed), for     i = 0 , 1   {\displaystyle i=0,1}  ![{\displaystyle i=0,1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b152b69b98c4244dd0c690c8ef74740df7fd343), the overlap test can be performed as follows:

 

     a  0   <  b  1     {\displaystyle a_{0}<b_{1}}  ![{\displaystyle a_{0}<b_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/48a9b76521fe36a241eba6decaa1f09124f0ca1d) and      a  1   <  b  0     {\displaystyle a_{1}<b_{0}}  ![{\displaystyle a_{1}<b_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fd22254b95ba70ba2b5d7374e28bb81075dc49e7)

 

This can be simplified using the sum and difference:

 

     s  i   =  a  i   +  b  i     {\displaystyle s_{i}=a_{i}+b_{i}}  ![{\displaystyle s_{i}=a_{i}+b_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c15e4b668ee1c05e687f50d1a5fefbb3e12390f7)

 

     d  i   =  b  i   − −   a  i     {\displaystyle d_{i}=b_{i}-a_{i}}  ![{\displaystyle d_{i}=b_{i}-a_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/555b7c98eec7adb3df12029968ef0d915085602a)

 

Which reduces the overlap test to:

 

     |   s  1   − −   s  0    |  <  d  0   +  d  1     {\displaystyle \left|s_{1}-s_{0}\right|<d_{0}+d_{1}}  ![{\displaystyle \left|s_{1}-s_{0}\right|<d_{0}+d_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9f5623a3bc63e94917b1faf61973f3d73f243656)

 

### Adding interval

 

Adding new intervals to the tree is the same as for a binary search tree using the medial value as the key. We push      d  i     {\displaystyle d_{i}}  ![{\displaystyle d_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/abe3154db7d4f92fb42dd1f80f52f528c6312e4a) onto the binary heap associated with the node, and update the minimum and maximum possible values associated with all higher nodes.

 

### Searching for all overlapping intervals

 

Let's use      a  q   ,  b  q   ,  m  q   ,  d  q     {\displaystyle a_{q},b_{q},m_{q},d_{q}}  ![{\displaystyle a_{q},b_{q},m_{q},d_{q}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cba495cf587f9c5b6f077a4995947ee1e7ea1e59) for the query interval, and      M  n     {\displaystyle M_{n}}  ![{\displaystyle M_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8656f32ad5c50e679b491b361a423727491496a0) for the key of a node (compared to      m  i     {\displaystyle m_{i}}  ![{\displaystyle m_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95ec8e804f69706d3f5ad235f4f983220c8df7c2) of intervals)

 

Starting with root node, in each node, first we check if it is possible that our query interval overlaps with the node subtree using minimum and maximum values of node (if it is not, we don't continue for this node).

 

Then we calculate     min  {  d  i   }    {\displaystyle \min \left\{d_{i}\right\}}  ![{\displaystyle \min \left\{d_{i}\right\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e073d5ed25d56134b3c893a4a6313c952f62ad45) for intervals inside this node (not its children) to overlap with query interval (knowing      m  i   =  M  n     {\displaystyle m_{i}=M_{n}}  ![{\displaystyle m_{i}=M_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/686c0f63f159478437e67d3715ccadfe4e92a8ec)):

 

    min  {  d  i   }  =  |   m  q   − −   M  n    |  − −   d  q     {\displaystyle \min \left\{d_{i}\right\}=\left|m_{q}-M_{n}\right|-d_{q}}  ![{\displaystyle \min \left\{d_{i}\right\}=\left|m_{q}-M_{n}\right|-d_{q}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/753a0827f3597b8f434031648126deff1038a811)

 

and perform a query on its binary heap for the      d  i     {\displaystyle d_{i}}  ![{\displaystyle d_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/abe3154db7d4f92fb42dd1f80f52f528c6312e4a)'s bigger than     min  {  d  i   }    {\displaystyle \min \left\{d_{i}\right\}}  ![{\displaystyle \min \left\{d_{i}\right\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e073d5ed25d56134b3c893a4a6313c952f62ad45)

 

Then we pass through both left and right children of the node, doing the same thing.

 

In the worst-case, we have to scan all nodes of the binary search tree, but since binary heap query is optimum, this is acceptable (a 2- dimensional problem can not be optimum in both dimensions)

 

This algorithm is expected to be faster than a traditional interval tree (augmented tree) for search operations. Adding elements is a little slower in practice, though the order of growth is the same.

 

## References

 
1. [↑](./Interval_tree#cite_ref-1) ["Computational Geometry - Windowing queries"](https://web.archive.org/web/20221024212654/https://personal.us.es/almar/cg/08windowing.pdf) (PDF). Archived from [the original](https://personal.us.es/almar/cg/08windowing.pdf) (PDF) on 2022-10-24.
2. [1](./Interval_tree#cite_ref-Schmidt2009_2-0) [2](./Interval_tree#cite_ref-Schmidt2009_2-1) [Jens M. Schmidt](./Jens_M._Schmidt?action=edit&redlink=1). *Interval Stabbing Problems in Small Integer Ranges*. [DOI](https://dx.doi.org/10.1007/978-3-642-10631-6_18). ISAAC'09, 2009
3. [↑](./Interval_tree#cite_ref-3) [Range query (computer science)#Semigroup operators](./Range_query_(computer_science)#Semigroup_operators)

 
- [Mark de Berg](./Mark_de_Berg), [Marc van Kreveld](./Marc_van_Kreveld), [Mark Overmars](./Mark_Overmars), and [Otfried Schwarzkopf](./Otfried_Schwarzkopf). *Computational Geometry*, Second Revised Edition. Springer-Verlag 2000. Section 10.1: Interval Trees, pp. 212–217.
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2009), [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.), MIT Press and McGraw-Hill, [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8)
- [Franco P. Preparata](./Franco_P._Preparata) and [Michael Ian Shamos](./Michael_Ian_Shamos). *Computational Geometry: An Introduction*. Springer-Verlag, 1985

  delete when above reference is used * [[Jens M. Schmidt]]. ''Interval Stabbing Problems in Small Integer Ranges''. [https://dx.doi.org/10.1007/978&#x2D;3&#x2D;642&#x2D;10631&#x2D;6_18 DOI]. ISAAC'09, 2009  

## External links

 
- [CGAL : Computational Geometry Algorithms Library in C++](https://www.cgal.org/) contains a robust implementation of Range Trees
- [Boost.Icl](https://www.boost.org/doc/libs/1_64_0/libs/icl/doc/html/index.html) offers C++ implementations of interval sets and maps.
- [IntervalTree (Python)](https://github.com/chaimleib/intervaltree) - a centered interval tree with AVL balancing, compatible with tagged intervals
- [Interval Tree (C#)](https://code.google.com/p/intervaltree/) - an augmented interval tree, with AVL balancing
- [Interval Tree (Ruby)](https://github.com/misshie/interval-tree/) - a centered interval tree, immutable, compatible with tagged intervals
- [IntervalTree (Java)](https://github.com/Breinify/brein-time-utilities/#intervaltree) - an augmented interval tree, with AVL balancing, supporting overlap, find, Collection interface, id-associated intervals
- [Tree::Interval::Fast (Perl/C)](https://metacpan.org/dist/Tree-Interval-Fast) - Efficient creation and manipulation of interval trees.

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |