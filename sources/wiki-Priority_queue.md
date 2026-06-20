---
source: https://en.wikipedia.org/wiki/Priority_queue
fetched: 2026-06-19
---

Abstract data type in computer science 

In [computer science](./Computer_science), a **priority queue** is an [abstract data type](./Abstract_data_type) similar to a regular [queue](./Queue_(abstract_data_type)) or [stack](./Stack_(abstract_data_type)) abstract data type.

 

In a priority queue, each element has an associated *priority*, which determines its order of service.[[1]](./Priority_queue#cite_note-:0-1) Priority queue serves highest priority items first.[[1]](./Priority_queue#cite_note-:0-1) Priority values have to be instances of an ordered data type, and higher priority can be given either to the lesser or to the greater values with respect to the given order relation. For example, in [Java](./Java_(programming_language)) standard library, *PriorityQueue'*s the least elements with respect to the order have the highest priority.[[2]](./Priority_queue#cite_note-2) This implementation detail is without much practical significance, since passing to the [opposite order relation](./Converse_relation) turns the least values into the greatest, and vice versa.

 

While priority queues are often implemented using [heaps](./Heap_(data_structure)), they are conceptually distinct. A priority queue can be implemented with a heap or with other methods; just as a list can be implemented with a [linked list](./Linked_list) or with an [array](./Array_(data_structure)).

 

## Operations

 

A priority queue has the following operations:[[3]](./Priority_queue#cite_note-3)[[4]](./Priority_queue#cite_note-:1-4)[[5]](./Priority_queue#cite_note-:2-5)

  

### Max-priority queue

 
- `insert(S, element, priority)`:[[4]](./Priority_queue#cite_note-:1-4)[[5]](./Priority_queue#cite_note-:2-5) add an element to set `S` with an associated priority.

 
- `maximum(S)`: return the element with *highest priority*.
This is also known as "`find_max`".

 
- `extract_max(S)`: remove the element from set `S` with *highest priority*, and return it.
This is also known as "`delete`",[[4]](./Priority_queue#cite_note-:1-4) or "`extract`".[[5]](./Priority_queue#cite_note-:2-5)

 
- `increase_key(S, element, k)`: increase the associated priority with an element to the new value `k`.

 

### Min-priority queue

 
- `insert(S, element, priority)`:[[4]](./Priority_queue#cite_note-:1-4)[[5]](./Priority_queue#cite_note-:2-5) add an element to set `S` with an associated priority.

 
- `minimum(S)`: return the element with *lowest priority*.
This is also known as "`find_min`".

 
- `extract_min(S)`: remove the element from set `S` with *lowest priority*, and return it.
This is also known as "`delete`",[[4]](./Priority_queue#cite_note-:1-4) or "`extract`".[[5]](./Priority_queue#cite_note-:2-5)

 
- `decrease_key(S, element, k)`: decrease the associated priority with an element to the new value `k`.

  

[Stacks](./Stack_(abstract_data_type)) and [queues](./Queue_(abstract_data_type)) can be implemented as particular kinds of priority queues, with the priority determined by the order in which the elements are inserted. In a stack, the priority of each inserted element is monotonically increasing; thus, the last element inserted is always the first retrieved. In a queue, the priority of each inserted element is monotonically decreasing; thus, the first element inserted is always the first retrieved.

 

In some implementations, if two elements have the same priority, they are served in the same order in which they were enqueued. In other implementations, the order of elements with the same priority is undefined.

 

## Implementation

 

### Naive implementations

 

One can create a simple, but inefficient priority queue in a number of ways. These naive implementations can demonstrate the expected behaviour of a priority queue in a simpler manner.

 
- *insert* elements into an unsorted array; find and *extract* element with *highest priority* Performance: "`insert`" performs in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) constant time, where "`extract_max`" performs in     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) linear time.

 
```
insert(element, priority):
 node.element ← element
 node.priority ← priority
 list.append(node)

extract_max():
 highest ← 0
 foreach node in list:
 if highest.priority < node.priority:
  highest ← node
 list.remove(highest)
 return highest.element
```
 
- *insert* elements into a sorted array; *extract* first element
Performance: "`insert`" performs in     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) linear time, where "`extract_max`" performs in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) constant time.

 
```
insert(element, priority):
 node.element ← element
 node.priority ← priority
 for i in [0...N]:
 element ← list.get_at_index(i)
 if element.priority < node.priority:
  list.insert_at_index(node, i + 1)
  return

extract_max():
 highest ← list.get_at_index(0)
 list.remove(highest)
 return highest.element
```
 

### Usual implementation

 

To improve performance, priority queues are typically based on a [heap](./Heap_(data_structure)), giving     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) performance for inserts and removals, and     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) to build the [heap](./Heap_(data_structure)) initially from a set of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) elements. Variants of the basic heap data structure such as [pairing heaps](./Pairing_heap) or [Fibonacci heaps](./Fibonacci_heap) can provide better bounds for some operations.[[6]](./Priority_queue#cite_note-CLRS_priority_queue_pp476-6)

 

Alternatively, when a [self-balancing binary search tree](./Self-balancing_binary_search_tree) is used, insertion and removal also take     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, although building trees from existing sequences of elements takes     O ( n log ⁡ ⁡  n )   {\displaystyle O(n\log n)}  ![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1) time; this is typical where one might already have access to these data structures, such as with third-party or standard libraries. From a space-complexity standpoint, using [self-balancing binary search tree](./Self-balancing_binary_search_tree) with [linked list](./Linked_list) takes more storage, since it requires storing extra references to other nodes.

 

From a computational-complexity standpoint, priority queues are congruent to sorting algorithms. The section on [the equivalence of priority queues and sorting algorithms](./Priority_queue#Equivalence_of_priority_queues_and_sorting_algorithms), below, describes how efficient sorting algorithms can create efficient priority queues.

 

### Specialized heaps

 

There are several specialized [heap](./Heap_(data_structure)) [data structures](./Data_structures) that either supply additional operations or outperform heap-based implementations for specific types of keys, specifically integer keys. Suppose the set of possible keys is     { 1 , 2 , . . . , C }   {\displaystyle \{1,2,...,C\}}  ![{\displaystyle \{1,2,...,C\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e482c394abf2e547aa20bbbe7fe9a6d3871a877).

 
- When only `insert`, `find-min` and `extract-min` are needed and in case of integer priorities, a [bucket queue](./Bucket_queue) can be constructed as an array of     C   {\displaystyle C}  ![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029) [linked lists](./Linked_list) plus a pointer      top    {\displaystyle {\text{top}}}  ![{\displaystyle {\text{top}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3529d9dd3c71c2450c5d0c3d69674dc56ebc3bf1), initially     C   {\displaystyle C}  ![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029). Inserting an item with key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) appends the item to the     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40)'th list, and updates      top  ← ←   min  (  top  , k )   {\displaystyle {\text{top}}\gets {\text{min}}({\text{top}},k)}  ![{\displaystyle {\text{top}}\gets {\text{min}}({\text{top}},k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5cdee62e49d3344d2740f81d82e843d18c10fd92), both in constant time. `extract-min` deletes and returns one item from the list with index      top    {\displaystyle {\text{top}}}  ![{\displaystyle {\text{top}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3529d9dd3c71c2450c5d0c3d69674dc56ebc3bf1), then increments      top    {\displaystyle {\text{top}}}  ![{\displaystyle {\text{top}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3529d9dd3c71c2450c5d0c3d69674dc56ebc3bf1) if needed until it again points to a non-empty list; this takes     O ( C )   {\displaystyle O(C)}  ![{\displaystyle O(C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9546ff613d54fc404ca30a17d142111d88902aa6) time in the worst case. These queues are useful for sorting the vertices of a graph by their degree.[[7]](./Priority_queue#cite_note-7): 374 
- A [van Emde Boas tree](./Van_Emde_Boas_tree) supports the `minimum`, `maximum`, `insert`, `delete`, `search`, `extract-min`, `extract-max`, `predecessor` and `successor]` operations in     O ( log ⁡ ⁡  log ⁡ ⁡  C )   {\displaystyle O(\log \log C)}  ![{\displaystyle O(\log \log C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a9cf31ca3bbcbf30ee1a4ddf0118d3964fec7a8) time, but has a space cost for small queues of about     O (  2  m  /  2   )   {\displaystyle O(2^{m/2})}  ![{\displaystyle O(2^{m/2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/29c55b81c7811ef50015ac4db444ec10c8d20f78), where     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the number of bits in the priority value.[[8]](./Priority_queue#cite_note-8) The space can be reduced significantly with hashing.
- The [Fusion tree](./Fusion_tree) by [Fredman](./Michael_Fredman) and [Willard](./Dan_Willard) implements the `minimum` operation in     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time and `insert` and `extract-min` operations in     O ( log ⁡ ⁡  n  /  log ⁡ ⁡  log ⁡ ⁡  C )   {\displaystyle O(\log n/\log \log C)}  ![{\displaystyle O(\log n/\log \log C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5b962ccdeb17f601f2c34a5b4bcb8d1c0d455534)time. However it is stated by the author that, "Our algorithms have theoretical interest only; The constant factors involved in the execution times preclude practicality."[[9]](./Priority_queue#cite_note-9)

 

For applications that do many "[peek](./Peek_(data_type_operation))" operations for every "`extract-min`" operation, the time complexity for peek actions can be reduced to     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) in all tree and heap implementations by caching the highest priority element after every insertion and removal. For insertion, this adds at most a constant cost, since the newly inserted element is compared only to the previously cached minimum element. For deletion, this at most adds an additional "peek" cost, which is typically cheaper than the deletion cost, so overall time complexity is not significantly impacted.

 

[Monotone priority queues](./Monotone_priority_queue) are specialized queues that are optimized for the case where no item is ever inserted that has a lower priority (in the case of min-heap) than any item previously extracted. This restriction is met by several practical applications of priority queues.

 

### Summary of running times

 

Here are [time complexities](./Computational_complexity_theory)[[10]](./Priority_queue#cite_note-CLRS-10) of various heap data structures. The abbreviation am. indicates that the given complexity is amortized, otherwise it is a worst-case complexity. For the meaning of "*O*(*f*)" and "*Θ*(*f*)" see [Big O notation](./Big_O_notation). Names of operations assume a min-heap.

 
| Operation | find-min | delete-min | decrease-key | insert | meld | make-heap[a] |
| --- | --- | --- | --- | --- | --- | --- |
| Binary[10] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) | Θ(n) |
| Skew[11] | Θ(1) | O(logn)am. | O(logn)am. | O(logn)am. | O(logn)am. | Θ(n)am. |
| Leftist[12] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) |
| Binomial[10][14] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1)am. | Θ(logn)[b] | Θ(n) |
| Skew binomial[15] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1) | Θ(logn)[b] | Θ(n) |
| 2–3 heap[17] | Θ(1) | O(logn)am. | Θ(1) | Θ(1)am. | O(logn)[b] | Θ(n) |
| Bottom-up skew[11] | Θ(1) | O(logn)am. | O(logn)am. | Θ(1)am. | Θ(1)am. | Θ(n)am. |
| Pairing[18] | Θ(1) | O(logn)am. | o(logn)am.[c] | Θ(1) | Θ(1) | Θ(n) |
| Rank-pairing[21] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Fibonacci[10][22] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Strict Fibonacci[23][d] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n) |
| Brodal[24][d] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n)[25] |

 
1. [↑](./Priority_queue#cite_ref-14) *make-heap* is the operation of building a heap from a sequence of *n* unsorted elements. It can be done in *Θ*(*n*) time whenever *meld* runs in *O*(log *n*) time (where both complexities can be amortized).[[11]](./Priority_queue#cite_note-sleator-tarjan-skew-11)[[12]](./Priority_queue#cite_note-tarjan-leftist-12) Another algorithm achieves *Θ*(*n*) for binary heaps.[[13]](./Priority_queue#cite_note-hayward-mcdiarmid-heap-build-13)
2. [1](./Priority_queue#cite_ref-bootstrap-meld_16-0) [2](./Priority_queue#cite_ref-bootstrap-meld_16-1) [3](./Priority_queue#cite_ref-bootstrap-meld_16-2) For [persistent](./Persistent_data_structure) heaps (not supporting *decrease-key*), a generic transformation reduces the cost of *meld* to that of *insert*, while the new cost of *delete-min* is the sum of the old costs of *delete-min* and *meld*.[[16]](./Priority_queue#cite_note-18) Here, it makes *meld* run in *Θ*(1) time (amortized, if the cost of *insert* is) while *delete-min* still runs in *O*(log *n*). Applied to skew binomial heaps, it yields Brodal-Okasaki queues, persistent heaps with optimal worst-case complexities.[[15]](./Priority_queue#cite_note-brodal-okasaki-17)
3. [↑](./Priority_queue#cite_ref-pairingdecreasekey_23-0) Lower bound of     Ω Ω  ( log ⁡ ⁡  log ⁡ ⁡  n ) ,   {\displaystyle \Omega (\log \log n),}  ![{\displaystyle \Omega (\log \log n),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7caf8c32fbd99eed1338c02b7f7f1255f16ade36)[[19]](./Priority_queue#cite_note-Fredman1999-21) upper bound of     O (  2  2   log ⁡ ⁡  log ⁡ ⁡  n     ) .   {\displaystyle O(2^{2{\sqrt {\log \log n}}}).}  ![{\displaystyle O(2^{2{\sqrt {\log \log n}}}).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/45c772d2ec070e49a6438ea92b1c8dc764613c5e)[[20]](./Priority_queue#cite_note-22)
4. [1](./Priority_queue#cite_ref-optimum_27-0) [2](./Priority_queue#cite_ref-optimum_27-1) Brodal queues and strict Fibonacci heaps achieve optimal worst-case complexities for heaps. They were first described as imperative data structures. The Brodal-Okasaki queue is a [persistent](./Persistent_data_structure) data structure achieving the same optimum, except that *decrease-key* is not supported.

 

## Equivalence of priority queues and sorting algorithms

 

### Using a priority queue to sort

 

The [semantics](./Operational_semantics) of priority queues naturally suggest a sorting method: insert all the elements to be sorted into a priority queue, and sequentially remove them; they will come out in sorted order. This is actually the procedure used by several [sorting algorithms](./Sorting_algorithm), once the layer of [abstraction](./Abstraction_(computer_science)) provided by the priority queue is removed. This sorting method is equivalent to the following sorting algorithms:

 
| Name | Priority queue implementation | Best | Average | Worst |
| --- | --- | --- | --- | --- |
| Heapsort | Heap | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} |
| Smoothsort | Leonardo heap | n{\displaystyle n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} |
| Selection sort | Unorderedarray | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} |
| Insertion sort | Orderedarray | n{\displaystyle n} | n2{\displaystyle n^{2}} | n2{\displaystyle n^{2}} |
| Tree sort | Self-balancing binary search tree | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} | nlog⁡n{\displaystyle n\log n} |

 

### Using a sorting algorithm to make a priority queue

 

A sorting algorithm can also be used to implement a priority queue. Specifically, Thorup says:[[26]](./Priority_queue#cite_note-30)

  

We present a general deterministic linear space reduction from priority queues to sorting implying that if we can sort up to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) keys in     S ( n )   {\displaystyle S(n)}  ![{\displaystyle S(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/896aa95cb194816f48a89fecd7e304d4b7f1af71) time per key, then there is a priority queue supporting `delete` and `insert` in     O ( S ( n ) )   {\displaystyle O(S(n))}  ![{\displaystyle O(S(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/343ab759efff53825bd7fa57e82340d2b4d09bc7) time and `find-min` in constant time.

  

That is, if there is a sorting algorithm which can sort in     O ( S )   {\displaystyle O(S)}  ![{\displaystyle O(S)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ebb7fa41b252b80e5c9b7c86087194abf8d06837) time per key, where     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2) is some function of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) and [word size](./Word_size),[[27]](./Priority_queue#cite_note-31) then one can use the given procedure to create a priority queue where pulling the highest-priority element is     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time, and inserting new elements (and deleting elements) is     O ( S )   {\displaystyle O(S)}  ![{\displaystyle O(S)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ebb7fa41b252b80e5c9b7c86087194abf8d06837) time. For example, if one has an     O ( n log ⁡ ⁡  n )   {\displaystyle O(n\log n)}  ![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1) sort algorithm, one can create a priority queue with     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) pulling and     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) insertion.

 

## Libraries

 

A priority queue is often considered to be a "[container data structure](./Container_(abstract_data_type))".

 

The [Standard Template Library](./Standard_Template_Library) (STL), and the [C++](./C++) 1998 standard, specifies [std::priority_queue](https://en.cppreference.com/w/cpp/container/priority_queue) as one of the STL [container](./Container_(programming)) [adaptor](./Adaptor_(programming)) [class templates](./Template_(programming)). However, it does not specify how two elements with same priority should be served, and indeed, common implementations will not return them according to their order in the queue. It implements a max-priority-queue, and has three parameters: a comparison object for sorting such as a function object (defaults to `less<T>` if unspecified), the underlying container for storing the data structures (defaults to `std::vector<T>`), and two iterators to the beginning and end of a sequence. Unlike actual STL containers, it does not allow [iteration](./Iterator) of its elements (it strictly adheres to its abstract data type definition). STL also has utility functions for manipulating another random-access container as a binary max-heap. The [Boost libraries](./Boost_(C++_libraries)) also have an implementation in the library heap.

 

Python's [heapq](https://docs.python.org/library/heapq.html) module implements a binary min-heap on top of a list.

 

[Java](./Java_(programming_language))'s library contains a `PriorityQueue` (`java.util.PriorityQueue`) class, which implements a min-priority-queue as a binary heap.

 

[.NET](./.NET)'s library contains a [System.Collections.Generic.PriorityQueue](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.priorityqueue-2?view=net-6.0) class, which implements an array-backed, quaternary min-heap.

 

[Scala](./Scala_(programming_language))'s library contains a [scala.collection.mutable.PriorityQueue](https://www.scala-lang.org/api/current/scala/collection/mutable/PriorityQueue.html) class, which implements a max-priority-queue.

 

[Go](./Go_(programming_language))'s library contains a [container/heap](https://golang.org/pkg/container/heap/) module, which implements a min-heap on top of any compatible data structure.

 

[Rust](./Rust_(programming_language))'s standard library contains a [std::collections::BinaryHeap](https://doc.rust-lang.org/std/collections/struct.BinaryHeap.html) struct, which implements a priority queue with a binary heap.

 

The [Standard PHP Library](./Standard_PHP_Library) extension contains the class [SplPriorityQueue](http://us2.php.net/manual/en/class.splpriorityqueue.php).

 

Apple's [Core Foundation](./Core_Foundation) framework contains a [CFBinaryHeap](https://developer.apple.com/library/mac/#documentation/CoreFoundation/Reference/CFBinaryHeapRef/Reference/reference.html) structure, which implements a min-heap.

 

## Applications

 

### Bandwidth management

 

Priority queuing can be used to manage limited resources such as [bandwidth](./Bandwidth_(computing)) on a transmission line from a [network](./Computer_network) [router](./Router_(computing)). In the event of outgoing [traffic](./Traffic) queuing due to insufficient bandwidth, all other queues can be halted to send the traffic from the highest priority queue upon arrival. This ensures that the prioritized traffic (such as real-time traffic, e.g. an [RTP](./Real-time_Transport_Protocol) stream of a [VoIP](./Voice_over_Internet_Protocol) connection) is forwarded with the least delay and the least likelihood of being rejected due to a queue reaching its maximum capacity. All other traffic can be handled when the highest priority queue is empty. Another approach used is to send disproportionately more traffic from higher priority queues.

 

Many modern protocols for [local area networks](./Local_area_network) also include the concept of priority queues at the [media access control](./Media_access_control) (MAC) sub-layer to ensure that high-priority applications (such as [VoIP](./VoIP) or [IPTV](./IPTV)) experience lower latency than other applications which can be served with [best-effort service](./Best-effort_service). Examples include [IEEE 802.11e](./IEEE_802.11e) (an amendment to [IEEE 802.11](./IEEE_802.11) which provides [quality of service](./Quality_of_service)) and [ITU-T](./ITU-T) [G.hn](./G.hn) (a standard for high-speed [local area network](./Local_area_network) using existing home wiring ([power lines](./Power_line_communication), phone lines and [coaxial cables](./Ethernet_over_coax)).

 

Usually a limitation (policer) is set to limit the bandwidth that traffic from the highest priority queue can take, in order to prevent high priority packets from choking off all other traffic. This limit is usually never reached due to high level control instances such as the [Cisco](./Cisco_Systems,_Inc.) [Callmanager](./Callmanager?action=edit&redlink=1), which can be programmed to inhibit calls which would exceed the programmed bandwidth limit.

  this was marked IMHO in the original
Priority queues exist on ISO&#x2D;layer 2 (which is Ethernet or WAN interfaces such as T1 / E1) and are filled by entry&#x2D;criterions such as [[Diffserv]] Codepoints or IP&#x2D;Precedence. Network equipment usually can be programmed to pick up priority packets by the layer 4 info (IP protocol and port) or the new one by a mechanism called [[NBAR]].
 

### Discrete event simulation

 

Another use of a priority queue is to manage the events in a [discrete event simulation](./Discrete_event_simulation). The events are added to the queue with their simulation time used as the priority. The execution of the simulation proceeds by repeatedly pulling the top of the queue and executing the event thereon.

 

*See also*: [Scheduling (computing)](./Scheduling_(computing)), [queueing theory](./Queueing_theory)

 

### Dijkstra's algorithm

 

When the graph is stored in the form of [adjacency list](./Adjacency_list) or matrix, priority queue can be used to extract minimum efficiently when implementing [Dijkstra's algorithm](./Dijkstra's_algorithm), although one also needs the ability to alter the priority of a particular vertex in the priority queue efficiently.

 

If instead, a graph is stored as node objects, and priority-node pairs are inserted into a heap, altering the priority of a particular vertex is not necessary if one tracks visited nodes. Once a node is visited, if it comes up in the heap again (having had a lower priority number associated with it earlier), it is popped-off and ignored.

 

### Huffman coding

 

[Huffman coding](./Huffman_coding) requires one to repeatedly obtain the two lowest-frequency trees. A priority queue is [one method of doing this](./Huffman_coding#Compression).

 

### Best-first search algorithms

 

[Best-first search](./Best-first_search) algorithms, like the [A* search algorithm](./A*_search_algorithm), find the shortest path between two [vertices](./Vertex_(graph_theory)) or [nodes](./Node_(graph_theory)) of a [weighted graph](./Weighted_graph), trying out the most promising routes first. A priority queue (also known as the *fringe*) is used to keep track of unexplored routes; the one for which the estimate (a lower bound in the case of A*) of the total path length is smallest is given highest priority. If memory limitations make best-first search impractical, variants like the [SMA*](./SMA*) algorithm can be used instead, with a [double-ended priority queue](./Double-ended_priority_queue) to allow removal of low-priority items.

 

### ROAM triangulation algorithm

 

The Real-time Optimally Adapting Meshes ([ROAM](./ROAM)) algorithm computes a dynamically changing triangulation of a terrain. It works by splitting triangles where more detail is needed and merging them where less detail is needed. The algorithm assigns each triangle in the terrain a priority, usually related to the error decrease if that triangle would be split. The algorithm uses two priority queues, one for triangles that can be split and another for triangles that can be merged. In each step the triangle from the split queue with the highest priority is split, or the triangle from the merge queue with the lowest priority is merged with its neighbours.

 

### Prim's algorithm for minimum spanning tree

 

Using [min heap priority queue](./Binary_heap) in [Prim's algorithm](./Prim's_algorithm) to find the [minimum spanning tree](./Minimum_spanning_tree) of a [connected](./Connected_graph) and [undirected graph](./Undirected_graph), one can achieve a good running time. This min heap priority queue uses the min heap data structure which supports operations such as `insert`, `minimum`, `extract-min`, `decrease-key`.[[28]](./Priority_queue#cite_note-CLR-32) In this implementation, the [weight](./Weighted_graph) of the edges is used to decide the priority of the [vertices](./Vertex_(graph_theory)). Lower the weight, higher the priority and higher the weight, lower the priority.[[29]](./Priority_queue#cite_note-GEEKS-33)

 

## Parallel priority queue

 

Parallelization can be used to speed up priority queues, but requires some changes to the priority queue interface. The reason for such changes is that a sequential update usually only has     O ( 1 )   {\textstyle O(1)}  ![{\textstyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/55a2cd47ca6554fafc21bbef3331256c7e1631ad) or     O ( log ⁡ ⁡  n )   {\textstyle O(\log n)}  ![{\textstyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/652bcc1f7bfa43527824017e3948b78c4ef942c4) cost, and there is no practical gain to parallelize such an operation. One possible change is to allow the concurrent access of multiple processors to the same priority queue. The second possible change is to allow batch operations that work on     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) elements, instead of just one element. For example, `extractMin` will remove the first     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) elements with the highest priority.

 

### Concurrent parallel access

 

If the priority queue allows concurrent access, multiple processes can perform operations concurrently on that priority queue. However, this raises two issues. First of all, the definition of the semantics of the individual operations is no longer obvious. For example, if two processes want to extract the element with the highest priority, should they get the same element or different ones? This restricts parallelism on the level of the program using the priority queue. In addition, because multiple processes have access to the same element, this leads to contention.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/ac/Concurrent_prio_queue_conflict.svg/250px-Concurrent_prio_queue_conflict.svg.png)](./File:Concurrent_prio_queue_conflict.svg)Node 3 is inserted and sets the pointer of node 2 to node 3. Immediately after that, node 2 is deleted and the pointer of node 1 is set to node 4. Now node 3 is no longer reachable. 

The concurrent access to a priority queue can be implemented on a Concurrent Read, Concurrent Write (CRCW) PRAM model. In the following the priority queue is implemented as a [skip list](./Skip_list).[[30]](./Priority_queue#cite_note-skiplist-34)[[31]](./Priority_queue#cite_note-35) In addition, an atomic synchronization primitive, [CAS](./Compare-and-swap), is used to make the skip list [lock](./Lock_(computer_science))-free. The nodes of the skip list consists of a unique key, a priority, an [array](./Array_data_structure) of [pointers](./Pointer_(computer_programming)), for each level, to the next nodes and a `delete` mark. The `delete` mark marks if the node is about to be deleted by a process. This ensures that other processes can react to the deletion appropriately.

 
- `insert(e)`: First, a new node with a key and a priority is created. In addition, the node is assigned a number of levels, which dictates the size of the array of pointers. Then a search is performed to find the correct position where to insert the new node. The search starts from the first node and from the highest level. Then the skip list is traversed down to the lowest level until the correct position is found. During the search, for every level the last traversed node will be saved as parent node for the new node at that level. In addition, the node to which the pointer, at that level, of the parent node points towards, will be saved as the successor node of the new node at that level. Afterwards, for every level of the new node, the pointers of the parent node will be set to the new node. Finally, the pointers, for every level, of the new node will be set to the corresponding successor nodes.
- `extract-min`: First, the skip list is traversed until a node is reached whose `delete` mark is not set. This `delete` mark is than set to true for that node. Finally the pointers of the parent nodes of the deleted node are updated.

 

If the concurrent access to a priority queue is allowed, conflicts may arise between two processes. For example, a conflict arises if one process is trying to insert a new node, but at the same time another process is about to delete the predecessor of that node.[[30]](./Priority_queue#cite_note-skiplist-34) There is a risk that the new node is added to the skip list, yet it is not longer reachable. ([See image](./File:Concurrent_prio_queue_conflict.svg))

 

### *K*-element operations

 

In this setting, operations on a priority queue is generalized to a batch of     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) elements.
For instance, `k_extract-min` deletes the     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) smallest elements of the priority queue and returns those. 

 

In a [shared-memory setting](./Parallel_programming_model), the parallel priority queue can be easily implemented using parallel [binary search trees](./Binary_search_trees) and [join-based tree algorithms](./Join-based_tree_algorithms). In particular, `k_extract-min` corresponds to a *split* on the binary search tree that has     O ( log ⁡ ⁡  n )   {\textstyle O(\log n)}  ![{\textstyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/652bcc1f7bfa43527824017e3948b78c4ef942c4) cost and yields a tree that contains the     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) smallest elements. `k_insert` can be applied by a *union* of the original priority queue and the batch of insertions. If the batch is already sorted by the key, `k_insert` has     O ( k log ⁡ ⁡  ( 1 +   n k   ) )   {\textstyle O(k\log(1+{\frac {n}{k}}))}  ![{\textstyle O(k\log(1+{\frac {n}{k}}))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/42eca403362de73c25092dc6e2490d9a4093a6df) cost. Otherwise, we need to first sort the batch, so the cost will be     O ( k log ⁡ ⁡  ( 1 +   n k   ) + k log ⁡ ⁡  k ) = O ( k log ⁡ ⁡  n )   {\textstyle O(k\log(1+{\frac {n}{k}})+k\log k)=O(k\log n)}  ![{\textstyle O(k\log(1+{\frac {n}{k}})+k\log k)=O(k\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6f0d8bf3311158494389bd208eb0e252d3be601c). Other operations for priority queue can be applied similarly. For instance, `k_decrease-key` can be done by first applying `difference` and then `union`, which first deletes the elements and then inserts them back with the updated keys. All these operations are highly parallel, and the theoretical and practical efficiency can be found in related research papers.[[32]](./Priority_queue#cite_note-join-based-36)[[33]](./Priority_queue#cite_note-pam-37)

 

The rest of this section discusses a queue-based algorithm on distributed memory. We assume each processor has its own local memory and a local (sequential) priority queue. The elements of the global (parallel) priority queue are distributed across all processors.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e1/BulkDeletionPQ.svg/250px-BulkDeletionPQ.svg.png)](./File:BulkDeletionPQ.svg)`k_extract-min` is executed on a priority queue with three processors. The green elements are returned and removed from the priority queue. 

A `k_insert` operation assigns the elements uniformly random to the processors which insert the elements into their local queues. Note that single elements can still be inserted into the queue. Using this strategy the global smallest elements are in the union of the local smallest elements of every processor with high probability. Thus each processor holds a representative part of the global priority queue.

 

This property is used when `k_extract-min` is executed, as the smallest     m   {\textstyle m}  ![{\textstyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3296968aacae7d971a6d649f6b32b5969ed6d4d6) elements of each local queue are removed and collected in a result set. The elements in the result set are still associated with their original processor. The number of elements     m   {\textstyle m}  ![{\textstyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3296968aacae7d971a6d649f6b32b5969ed6d4d6) that is removed from each local queue depends on     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) and the number of processors     p   {\textstyle p}  ![{\textstyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad87bd7009e2a5c52bd0fb5a9bda9d8c1c23a79b). 
[[34]](./Priority_queue#cite_note-AlgToolbox-38)
By parallel selection the     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) smallest elements of the result set are determined. With high probability these are the global     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) smallest elements. If not,     m   {\textstyle m}  ![{\textstyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3296968aacae7d971a6d649f6b32b5969ed6d4d6) elements are again removed from each local queue and put into the result set. This is done until the global     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) smallest elements are in the result set. Now these     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) elements can be returned. All other elements of the result set are inserted back into their local queues. The running time of `k_extract-min` is expected     O (   k p   log ⁡ ⁡  ( n ) )   {\textstyle O({\frac {k}{p}}\log(n))}  ![{\textstyle O({\frac {k}{p}}\log(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1786f666f72262d9af94c2c4f7ae7bd0995fcdb4), where     k = Ω Ω  ( p ⋅ ⋅  log ⁡ ⁡  ( p ) )   {\textstyle k=\Omega (p\cdot \log(p))}  ![{\textstyle k=\Omega (p\cdot \log(p))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b19aef38a319fcd6726a682195492469dd6214a3) and     n   {\textstyle n}  ![{\textstyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc6e1f880981346a604257ebcacdef24c0aca2d6) is the size of the priority queue.[[34]](./Priority_queue#cite_note-AlgToolbox-38)

 

The priority queue can be further improved by not moving the remaining elements of the result set directly back into the local queues after a `k_extract-min` operation. This saves moving elements back and forth all the time between the result set and the local queues.

 

By removing several elements at once a considerable speedup can be reached. But not all algorithms can use this kind of priority queue. Dijkstra's algorithm for example can not work on several nodes at once. The algorithm takes the node with the smallest distance from the priority queue and calculates new distances for all its neighbor nodes. If you would take out     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) nodes, working at one node could change the distance of another one of the     k   {\textstyle k}  ![{\textstyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d5595fc0c47452f8fc2aa6e29c3611f047714b0) nodes. So using k-element operations destroys the label setting property of Dijkstra's algorithm.

 

## See also

 
- [Batch queue](./Batch_queue)
- [Command queue](./Command_queue)
- [Job scheduler](./Job_scheduler)

 

## References

  
1. [1](./Priority_queue#cite_ref-:0_1-0) [2](./Priority_queue#cite_ref-:0_1-1) Miller Jr., Robert G. (1960). ["Priority queues"](https://projecteuclid.org/journals/annals-of-mathematical-statistics/volume-31/issue-1/Priority-Queues/10.1214/aoms/1177705990.pdf) (PDF). *The Annals of Mathematical Statistics*. **31**. Stanford University: 86–103. [doi](./Doi_(identifier)):[10.1214/aoms/1177705990](https://doi.org/10.1214%2Faoms%2F1177705990).
2. [↑](./Priority_queue#cite_ref-2) ["PriorityQueue (Java SE 9 & JDK 9 )"](https://docs.oracle.com/javase/9/docs/api/java/util/PriorityQueue.html). *docs.oracle.com*. Retrieved 2025-03-13.
3. [↑](./Priority_queue#cite_ref-3) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2022) [1990]. "Chapter 6.5: Priority queues". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (4th ed.). MIT Press and McGraw-Hill. pp. 172–176. [ISBN](./ISBN_(identifier)) [0-262-04630-X](./Special:BookSources/0-262-04630-X).
4. [1](./Priority_queue#cite_ref-:1_4-0) [2](./Priority_queue#cite_ref-:1_4-1) [3](./Priority_queue#cite_ref-:1_4-2) [4](./Priority_queue#cite_ref-:1_4-3) [5](./Priority_queue#cite_ref-:1_4-4) Rönngren, Robert; Ayani, Rassul (1997-04-01). ["A comparative study of parallel and sequential priority queue algorithms"](https://dl.acm.org/doi/10.1145/249204.249205). *ACM Trans. Model. Comput. Simul*. **7** (2): 157–209. [doi](./Doi_(identifier)):[10.1145/249204.249205](https://doi.org/10.1145%2F249204.249205). [ISSN](./ISSN_(identifier)) [1049-3301](https://search.worldcat.org/issn/1049-3301).
5. [1](./Priority_queue#cite_ref-:2_5-0) [2](./Priority_queue#cite_ref-:2_5-1) [3](./Priority_queue#cite_ref-:2_5-2) [4](./Priority_queue#cite_ref-:2_5-3) [5](./Priority_queue#cite_ref-:2_5-4) Ayani, R. (December 1990). "LR-algorithm: Concurrent operations on priority queues". *Proceedings of the Second IEEE Symposium on Parallel and Distributed Processing 1990*. pp. 22–25. [doi](./Doi_(identifier)):[10.1109/SPDP.1990.143500](https://doi.org/10.1109%2FSPDP.1990.143500). [ISBN](./ISBN_(identifier)) [0-8186-2087-0](./Special:BookSources/0-8186-2087-0).
6. [↑](./Priority_queue#cite_ref-CLRS_priority_queue_pp476_6-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. "Chapter 20: Fibonacci Heaps". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 476–497. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). Third edition, p. 518.
7. [↑](./Priority_queue#cite_ref-7) [Skiena, Steven](./Steven_Skiena) (2010). *The Algorithm Design Manual* (2nd ed.). [Springer Science+Business Media](./Springer_Science+Business_Media). [ISBN](./ISBN_(identifier)) [978-1-849-96720-4](./Special:BookSources/978-1-849-96720-4).
8. [↑](./Priority_queue#cite_ref-8) P. van Emde Boas. Preserving order in a forest in less than logarithmic time. In *Proceedings of the 16th Annual Symposium on Foundations of Computer Science*, pages 75–84. IEEE Computer Society, 1975.
9. [↑](./Priority_queue#cite_ref-9) [Michael L. Fredman](./Michael_Fredman) and Dan E. Willard. Surpassing the information theoretic bound with fusion trees. *Journal of Computer and System Sciences*, 48(3):533-551, 1994
10. [1](./Priority_queue#cite_ref-CLRS_10-0) [2](./Priority_queue#cite_ref-CLRS_10-1) [3](./Priority_queue#cite_ref-CLRS_10-2) [4](./Priority_queue#cite_ref-CLRS_10-3) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest) (1990). [*Introduction to Algorithms*](./Introduction_to_Algorithms) (1st ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03141-8](./Special:BookSources/0-262-03141-8).
11. [1](./Priority_queue#cite_ref-sleator-tarjan-skew_11-0) [2](./Priority_queue#cite_ref-sleator-tarjan-skew_11-1) [3](./Priority_queue#cite_ref-sleator-tarjan-skew_11-2) [Sleator, Daniel Dominic](./Daniel_Sleator); [Tarjan, Robert Endre](./Robert_Tarjan) (February 1986). ["Self-Adjusting Heaps"](https://www.cs.cmu.edu/~sleator/papers/Adjusting-Heaps.htm). *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **15** (1): 52–69. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.93.6678](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.93.6678). [doi](./Doi_(identifier)):[10.1137/0215004](https://doi.org/10.1137%2F0215004). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397). 
12. [1](./Priority_queue#cite_ref-tarjan-leftist_12-0) [2](./Priority_queue#cite_ref-tarjan-leftist_12-1) [Tarjan, Robert](./Robert_Tarjan) (1983). "3.3. Leftist heaps". *Data Structures and Network Algorithms*. pp. 38–42. [doi](./Doi_(identifier)):[10.1137/1.9781611970265](https://doi.org/10.1137%2F1.9781611970265). [ISBN](./ISBN_(identifier)) [978-0-89871-187-5](./Special:BookSources/978-0-89871-187-5).
13. [↑](./Priority_queue#cite_ref-hayward-mcdiarmid-heap-build_13-0) Hayward, Ryan; McDiarmid, Colin (1991). ["Average Case Analysis of Heap Building by Repeated Insertion"](https://web.archive.org/web/20160205023201/http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF). *J. Algorithms*. **12**: 126–153. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.353.7888](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.353.7888). [doi](./Doi_(identifier)):[10.1016/0196-6774(91)90027-v](https://doi.org/10.1016%2F0196-6774%2891%2990027-v). Archived from [the original](http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF) on 2016-02-05. Retrieved 2016-01-28.
14. [↑](./Priority_queue#cite_ref-15) ["Binomial Heap | Brilliant Math & Science Wiki"](https://brilliant.org/wiki/binomial-heap/). *brilliant.org*. Retrieved 2019-09-30.
15. [1](./Priority_queue#cite_ref-brodal-okasaki_17-0) [2](./Priority_queue#cite_ref-brodal-okasaki_17-1) Brodal, Gerth Stølting; Okasaki, Chris (November 1996), "Optimal purely functional priority queues", *Journal of Functional Programming*, **6** (6): 839–857, [doi](./Doi_(identifier)):[10.1017/s095679680000201x](https://doi.org/10.1017%2Fs095679680000201x)
16. [↑](./Priority_queue#cite_ref-18) [Okasaki, Chris](./Chris_Okasaki) (1998). "10.2. Structural Abstraction". *Purely Functional Data Structures* (1st ed.). pp. 158–162. [ISBN](./ISBN_(identifier)) [9780521631242](./Special:BookSources/9780521631242).
17. [↑](./Priority_queue#cite_ref-19) [Takaoka, Tadao](./Tadao_Takaoka?action=edit&redlink=1) (1999), [*Theory of 2–3 Heaps*](https://ir.canterbury.ac.nz/bitstream/handle/10092/14769/2-3heaps.pdf) (PDF), p. 12
18. [↑](./Priority_queue#cite_ref-Iacono_20-0) [Iacono, John](./John_Iacono) (2000), "Improved upper bounds for pairing heaps", [*Proc. 7th Scandinavian Workshop on Algorithm Theory*](http://john2.poly.edu/papers/swat00/paper.pdf) (PDF), Lecture Notes in Computer Science, vol. 1851, Springer-Verlag, pp. 63–77, [arXiv](./ArXiv_(identifier)):[1110.4428](https://arxiv.org/abs/1110.4428), [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.748.7812](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.748.7812), [doi](./Doi_(identifier)):[10.1007/3-540-44985-X_5](https://doi.org/10.1007%2F3-540-44985-X_5), [ISBN](./ISBN_(identifier)) [3-540-67690-2](./Special:BookSources/3-540-67690-2)
19. [↑](./Priority_queue#cite_ref-Fredman1999_21-0) [Fredman, Michael Lawrence](./Michael_Fredman) (July 1999). ["On the Efficiency of Pairing Heaps and Related Data Structures"](http://www.uqac.ca/azinflou/Fichiers840/EfficiencyPairingHeap.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **46** (4): 473–501. [doi](./Doi_(identifier)):[10.1145/320211.320214](https://doi.org/10.1145%2F320211.320214).
20. [↑](./Priority_queue#cite_ref-22) Pettie, Seth (2005). [*Towards a Final Analysis of Pairing Heaps*](http://web.eecs.umich.edu/~pettie/papers/focs05.pdf) (PDF). FOCS '05 Proceedings of the 46th Annual IEEE Symposium on Foundations of Computer Science. pp. 174–183. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.549.471](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.549.471). [doi](./Doi_(identifier)):[10.1109/SFCS.2005.75](https://doi.org/10.1109%2FSFCS.2005.75). [ISBN](./ISBN_(identifier)) [0-7695-2468-0](./Special:BookSources/0-7695-2468-0).
21. [↑](./Priority_queue#cite_ref-24) Haeupler, Bernhard; Sen, Siddhartha; [Tarjan, Robert E.](./Robert_Tarjan) (November 2011). ["Rank-pairing heaps"](http://sidsen.org/papers/rp-heaps-journal.pdf) (PDF). *SIAM J. Computing*. **40** (6): 1463–1485. [doi](./Doi_(identifier)):[10.1137/100785351](https://doi.org/10.1137%2F100785351).
22. [↑](./Priority_queue#cite_ref-Fredman_And_Tarjan_25-0) [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (July 1987). ["Fibonacci heaps and their uses in improved network optimization algorithms"](http://bioinfo.ict.ac.cn/~dbu/AlgorithmCourses/Lectures/Fibonacci-Heap-Tarjan.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **34** (3): 596–615. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.309.8927](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.309.8927). [doi](./Doi_(identifier)):[10.1145/28869.28874](https://doi.org/10.1145%2F28869.28874). An earlier version of this paper appeared in 1984 {{doi|10.1109/SFCS.1984.715934}}
23. [↑](./Priority_queue#cite_ref-26) [Brodal, Gerth Stølting](./Gerth_Stølting_Brodal); Lagogiannis, George; [Tarjan, Robert E.](./Robert_Tarjan) (2012). [*Strict Fibonacci heaps*](http://www.cs.au.dk/~gerth/papers/stoc12.pdf) (PDF). Proceedings of the 44th symposium on Theory of Computing - STOC '12. pp. 1177–1184. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.233.1740](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.233.1740). [doi](./Doi_(identifier)):[10.1145/2213977.2214082](https://doi.org/10.1145%2F2213977.2214082). [ISBN](./ISBN_(identifier)) [978-1-4503-1245-5](./Special:BookSources/978-1-4503-1245-5).
24. [↑](./Priority_queue#cite_ref-28) [Brodal, Gerth S.](./Gerth_Stølting_Brodal) (1996), ["Worst-Case Efficient Priority Queues"](http://www.cs.au.dk/~gerth/papers/soda96.pdf) (PDF), *Proc. 7th Annual ACM-SIAM Symposium on Discrete Algorithms*, pp. 52–58
25. [↑](./Priority_queue#cite_ref-29) [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2004). "7.3.6. Bottom-Up Heap Construction". *Data Structures and Algorithms in Java* (3rd ed.). pp. 338–341. [ISBN](./ISBN_(identifier)) [0-471-46983-1](./Special:BookSources/0-471-46983-1).
26. [↑](./Priority_queue#cite_ref-30) [Thorup, Mikkel](./Mikkel_Thorup) (2007). "Equivalence between priority queues and sorting". *[Journal of the ACM](./Journal_of_the_ACM)*. **54** (6): 28. [doi](./Doi_(identifier)):[10.1145/1314690.1314692](https://doi.org/10.1145%2F1314690.1314692). [S2CID](./S2CID_(identifier)) [11494634](https://api.semanticscholar.org/CorpusID:11494634).
27. [↑](./Priority_queue#cite_ref-31) ["Archived copy"](http://courses.csail.mit.edu/6.851/spring07/scribe/lec17.pdf) (PDF). [Archived](https://web.archive.org/web/20110720000413/http://courses.csail.mit.edu/6.851/spring07/scribe/lec17.pdf) (PDF) from the original on 2011-07-20. Retrieved 2011-02-10.`{{cite web}}`:  CS1 maint: archived copy as title ([link](./Category:CS1_maint:_archived_copy_as_title))
28. [↑](./Priority_queue#cite_ref-CLR_32-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2009) [1990]. [*Introduction to Algorithms*](./Introduction_to_Algorithms) (3rd ed.). MIT Press and McGraw-Hill. p. 634. [ISBN](./ISBN_(identifier)) [0-262-03384-4](./Special:BookSources/0-262-03384-4). "In order to implement Prim's algorithm efficiently, we need a fast way to select a new edge to add to the tree formed by the edges in A."
29. [↑](./Priority_queue#cite_ref-GEEKS_33-0)  ["Prim's Algorithm"](http://www.geeksforgeeks.org/greedy-algorithms-set-5-prims-minimum-spanning-tree-mst-2/). Geek for Geeks. 18 November 2012. [Archived](https://web.archive.org/web/20140909020508/http://www.geeksforgeeks.org/greedy-algorithms-set-5-prims-minimum-spanning-tree-mst-2/) from the original on 9 September 2014. Retrieved 12 September 2014. 
30. [1](./Priority_queue#cite_ref-skiplist_34-0) [2](./Priority_queue#cite_ref-skiplist_34-1) Sundell, Håkan; Tsigas, Philippas (2005). ["Fast and lock-free concurrent priority queues for multi-thread systems"](https://doi.org/10.1016/j.jpdc.2004.12.005). *Proceedings International Parallel and Distributed Processing Symposium*. Vol. 65. pp. 609–627. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.67.1310](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.67.1310). [doi](./Doi_(identifier)):[10.1109/IPDPS.2003.1213189](https://doi.org/10.1109%2FIPDPS.2003.1213189). [ISBN](./ISBN_(identifier)) [0-7695-1926-1](./Special:BookSources/0-7695-1926-1). [S2CID](./S2CID_(identifier)) [20995116](https://api.semanticscholar.org/CorpusID:20995116).
31. [↑](./Priority_queue#cite_ref-35) Lindén, Jonsson (2013), ["A Skiplist-Based Concurrent Priority Queue with Minimal Memory Contention"](http://www.it.uu.se/research/publications/reports/2018-003/), *Technical Report 2018-003* (in German)
32. [↑](./Priority_queue#cite_ref-join-based_36-0) Blelloch, Guy E.; Ferizovic, Daniel; Sun, Yihan (2016), "Just Join for Parallel Ordered Sets", *Symposium on Parallel Algorithms and Architectures, Proc. of 28th ACM Symp. Parallel Algorithms and Architectures (SPAA 2016)*, ACM, pp. 253–264, [arXiv](./ArXiv_(identifier)):[1602.02120](https://arxiv.org/abs/1602.02120), [doi](./Doi_(identifier)):[10.1145/2935764.2935768](https://doi.org/10.1145%2F2935764.2935768), [ISBN](./ISBN_(identifier)) [978-1-4503-4210-0](./Special:BookSources/978-1-4503-4210-0), [S2CID](./S2CID_(identifier)) [2897793](https://api.semanticscholar.org/CorpusID:2897793)
33. [↑](./Priority_queue#cite_ref-pam_37-0) Blelloch, Guy E.; Ferizovic, Daniel; Sun, Yihan (2018), "PAM: parallel augmented maps", *Proceedings of the 23rd ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming*, ACM, pp. 290–304
34. [1](./Priority_queue#cite_ref-AlgToolbox_38-0) [2](./Priority_queue#cite_ref-AlgToolbox_38-1) Sanders, Peter; Mehlhorn, Kurt; Dietzfelbinger, Martin; Dementiev, Roman (2019). *Sequential and Parallel Algorithms and Data Structures - The Basic Toolbox*. Springer International Publishing. pp. 226–229. [doi](./Doi_(identifier)):[10.1007/978-3-030-25209-0](https://doi.org/10.1007%2F978-3-030-25209-0). [ISBN](./ISBN_(identifier)) [978-3-030-25208-3](./Special:BookSources/978-3-030-25208-3). [S2CID](./S2CID_(identifier)) [201692657](https://api.semanticscholar.org/CorpusID:201692657).

 

## Further reading

 
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. "Section 6.5: Priority queues". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 138–142. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).

 

## External links

 
- [C++ reference for `std::priority_queue`](http://en.cppreference.com/w/cpp/container/priority_queue)
- [Descriptions](http://leekillough.com/heaps/) by [Lee Killough](./Lee_Killough_(programmer)?action=edit&redlink=1)
- [libpqueue](https://github.com/vy/libpqueue) is a generic priority queue (heap) implementation (in C) used by the Apache HTTP Server project.
- [Survey of known priority queue structures](https://web.archive.org/web/20121103132051/http://www.theturingmachine.com/algorithms/heaps.html) by Stefan Xenos
- [UC Berkeley - Computer Science 61B - Lecture 24: Priority Queues](https://archive.org/details/ucberkeley_webcast_yIUFT6AKBGE) (video) - introduction to priority queues using binary heap
- [Methods and operations of Priority queue in C++](https://www.ccbp.in/blog/articles/priority-queue-in-cpp#methods-of-priority-queue-in-cpp)
- [Implementation of Priority Queue in Java](https://www.geeksforgeeks.org/java/priority-queue-in-java/)
- [Implementation of Priority Queue in C](https://www.sanfoundry.com/c-program-priority-queue/)

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |