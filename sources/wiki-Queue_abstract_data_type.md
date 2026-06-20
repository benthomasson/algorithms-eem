---
source: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
fetched: 2026-06-19
---

Abstract data type 
|  | This article includes a list ofgeneral references, butit lacks sufficient correspondinginline citations.Please help toimprovethis article byintroducingmore precise citations.(January 2014)(Learn how and when to remove this message) |
| --- | --- |

 
| Queue |
| --- |
| Representation of aFIFO(first in, first out) queue |
| Time complexityinbig O notationOperationAverageWorst caseSearchO(n)O(n)InsertO(1)O(1)DeleteO(1)O(1)Space complexitySpaceO(n)O(n) | Time complexityinbig O notation | Operation | Average | Worst case | Search | O(n) | O(n) | Insert | O(1) | O(1) | Delete | O(1) | O(1) | Space complexity | Space | O(n) | O(n) |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Search | O(n) | O(n) |
| Insert | O(1) | O(1) |
| Delete | O(1) | O(1) |
| Space complexity |
| Space | O(n) | O(n) |

 

In [computer science](./Computer_science), a queue is an abstract data type that serves as an ordered [collection](./Collection_(abstract_data_type)) of entities. By convention, the end of the queue where elements are added is called the back, tail, or rear of the queue. The end of the queue where elements are removed is called the head or front of the queue. The name *queue* is an [analogy](./Analogy) to the words used to describe people in line to wait for goods or services. It supports two main operations. 

 
- **Enqueue,** which adds one element to the rear of the queue
- **Dequeue,** which removes one element from the front of the queue.

 

Other operations may also be allowed, often including a *[peek](./Peek_(data_type_operation))* or *front* operation that returns the value of the next element to be dequeued without dequeuing it.

 

The operations of a queue make it a [first-in-first-out (FIFO) data structure](./FIFO_(computing_and_electronics)) as the first element added to the queue is the first one removed. This is equivalent to the requirement that once a new element is added, all elements that were added before have to be removed before the new element can be removed. A queue is an example of a [linear data structure](./Linear_data_structure), or more abstractly a sequential collection.
Queues are common in computer programs, where they are implemented as data structures coupled with access routines, as an [abstract data structure](./Abstract_data_structure) or in object-oriented languages as classes. A queue may be implemented as [circular buffers](./Circular_buffer) and [linked lists](./Linked_list), or by using both the [stack pointer](./Stack_pointer) and the base pointer.

 

Queues provide services in [computer science](./Computer_science), [transport](./Transport), and [operations research](./Operations_research) where various entities such as data, objects, persons, or events are stored and held to be processed later. In these contexts, the queue performs the function of a [buffer](./Buffer_(computer_science)).
Another usage of queues is in the implementation of [breadth-first search](./Breadth-first_search).

 

## Queue implementation

 

Theoretically, one characteristic of a queue is that it does not have a specific capacity. Regardless of how many elements are already contained, a new element can always be added. It can also be empty, at which point removing an element will be impossible until a new element has been added again.

 

Fixed-length arrays are limited in capacity, but it is not true that items need to be copied towards the head of the queue. The simple trick of turning the array into a closed circle and letting the head and tail drift around endlessly in that circle makes it unnecessary to ever move items stored in the array. If n is the size of the array, then computing indices modulo n will turn the [array](./Array_(data_structure)) into a circle. This is still the conceptually simplest way to construct a queue in a [high-level language](./High-level_programming_language), but it does admittedly slow things down a little, because the array indices must be compared to zero and the array size, which is comparable to the time taken to check whether an array index is out of bounds, which some languages do, but this will certainly be the method of choice for a quick and dirty implementation, or for any high-level language that does not have pointer syntax. The array size must be declared ahead of time, but some implementations simply double the declared array size when overflow occurs. Most modern languages with objects or [pointers](./Pointer_(computer_programming)) can implement or come with libraries for dynamic lists. Such [data structures](./Data_structure) may have not specified a fixed capacity limit besides memory constraints. Queue *overflow* results from trying to add an element onto a full queue and queue *underflow* happens when trying to remove an element from an empty queue.

 

A *bounded queue* is a queue limited to a fixed number of items.[[1]](./Queue_(abstract_data_type)#cite_note-1)

 

There are several efficient implementations of FIFO queues. An efficient implementation is one that can perform the operations—en-queuing and de-queuing—in [O(1) time](./Big_O_notation).

 
- [Linked list](./Linked_list) 
- A [doubly linked list](./Doubly_linked_list) has O(1) insertion and deletion at both ends, so it is a natural choice for queues.
- A regular singly linked list only has efficient insertion and deletion at one end. However, a small modification—keeping a pointer to the *last* node in addition to the first one—will enable it to implement an efficient queue.

- A [deque](./Double-ended_queue) implemented using a modified dynamic array

 

### Queues and programming languages

 

Queues may be implemented as a separate data type, or maybe considered a special case of a [double-ended queue](./Double-ended_queue) (deque) and not implemented separately. For example, [Perl](./Perl) and [Ruby](./Ruby_(programming_language)) allow pushing and popping an array from both ends, so one can use **push** and **shift** functions to enqueue and dequeue a list (or, in reverse, one can use **unshift** and **pop**),[[2]](./Queue_(abstract_data_type)#cite_note-2) although in some cases these operations are not efficient.

 

C++'s [Standard Template Library](./Standard_Template_Library) provides a "`queue`" templated class which is restricted to only push/pop operations. Since J2SE5.0, Java's library contains a `Queue` interface that specifies queue operations; implementing classes include `LinkedList` and (since J2SE 1.6) `ArrayDeque`. PHP has an [SplQueue](http://www.php.net/manual/en/class.splqueue.php) class and third-party libraries like [beanstalk'd](./Beanstalk'd?action=edit&redlink=1) and [Gearman](./Gearman).

 

[![UML queue class.svg](//upload.wikimedia.org/wikipedia/commons/thumb/e/ec/UML_queue_class.svg/250px-UML_queue_class.svg.png)](./File:UML_queue_class.svg)

 

### Example

 

A simple queue implemented in [TypeScript](./TypeScript):

 
```
class Queue<T> {
    private items: T[] = [];

    enqueue(element: T): void {
        this.items.push(element);
    }

    dequeue(): T | undefined {
        return this.items.shift();
    }

    isEmpty(): boolean {
        return this.items.length === 0;
    }
}

```
 

## Purely functional implementation

 

Queues can also be implemented as a [purely functional data structure](./Purely_functional_data_structure).[[3]](./Queue_(abstract_data_type)#cite_note-3) There are two implementations. The first one only achieves     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) per operation *on average*.  That is, the [amortized](./Amortized_analysis) time is     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21), but individual operations can take     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) where *n* is the number of elements in the queue.  The second implementation is called a **real-time queue**[[4]](./Queue_(abstract_data_type)#cite_note-4) and it allows the queue to be [persistent](./Persistent_data_structure) with operations in O(1) worst-case time. It is a more complex implementation and requires [lazy](./Lazy_evaluation) lists with [memoization](./Memoization). 

 

### Amortized queue

 

This queue's data is stored in two [singly-linked lists](./Linked_list#Singly_linked_list) named     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) and     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538).  The list     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) holds the front part of the queue.  The list     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) holds the remaining elements (a.k.a., the rear of the queue) *in reverse order*.  It is easy to insert into the front of the queue by adding a node at the head of     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61).  And, if     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is not empty, it is easy to remove from the end of the queue by removing the node at the head of     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538).  When     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is empty, the list     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is reversed and assigned to     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) and then the head of     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is removed.  

 

The insert ("enqueue") always takes     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time.  The removal ("dequeue") takes     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) when the list     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is not empty.  When     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) is empty, the reverse takes     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the number of elements in     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61).  But, we can say it is     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) [amortized](./Amortized_analysis) time, because every element in     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) had to be inserted and we can assign a constant cost for each element in the reverse to when it was inserted.  

 

### Real-time queue

 

The real-time queue achieves     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) time for all operations, without amortization.  This discussion will be technical, so recall that, for     l   {\displaystyle l}  ![{\displaystyle l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/829091f745070b9eb97a80244129025440a1cfac) a list,      |  l  |    {\displaystyle |l|}  ![{\displaystyle |l|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18fb48342bae497cbaf66ff7122c6b74d9518c04) denotes its length, that *NIL* represents an empty list and     CONS ⁡ ⁡  ( h , t )   {\displaystyle \operatorname {CONS} (h,t)}  ![{\displaystyle \operatorname {CONS} (h,t)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4c5cc4ede9b9d1a13d684929c084fb6c2393cf2b) represents the list whose head is *h* and whose tail is *t*.

 

The data structure used to implement our queues consists of three [singly-linked lists](./Linked_list#Singly_linked_list)     ( f , r , s )   {\displaystyle (f,r,s)}  ![{\displaystyle (f,r,s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3edbde37e6e782104dea0a6e29cc0d57aefbc64b) where *f* is the front of the queue and *r* is the rear of the queue in reverse order. The invariant of the structure is that *s* is the rear of *f* without its      |  r  |    {\displaystyle |r|}  ![{\displaystyle |r|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33724ed2b4730b9b29dd9d08e8b216c539ed7dde) first elements, that is      |  s  |  =  |  f  |  − −   |  r  |    {\displaystyle |s|=|f|-|r|}  ![{\displaystyle |s|=|f|-|r|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3adbe9e725c400c6e82bf16347e20cb5dc4087cc). The tail of the queue     ( CONS ⁡ ⁡  ( x , f ) , r , s )   {\displaystyle (\operatorname {CONS} (x,f),r,s)}  ![{\displaystyle (\operatorname {CONS} (x,f),r,s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6d9f50aa1327bb8b2a1913e56df75b682c92ea8a) is then almost     ( f , r , s )   {\displaystyle (f,r,s)}  ![{\displaystyle (f,r,s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3edbde37e6e782104dea0a6e29cc0d57aefbc64b) and
inserting an element *x* to     ( f , r , s )   {\displaystyle (f,r,s)}  ![{\displaystyle (f,r,s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3edbde37e6e782104dea0a6e29cc0d57aefbc64b) is almost     ( f , CONS ⁡ ⁡  ( x , r ) , s )   {\displaystyle (f,\operatorname {CONS} (x,r),s)}  ![{\displaystyle (f,\operatorname {CONS} (x,r),s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c21cfc492ca41cf84696cca9c74ca118f74b61c6). It is said almost, because in both of those results,      |  s  |  =  |  f  |  − −   |  r  |  + 1   {\displaystyle |s|=|f|-|r|+1}  ![{\displaystyle |s|=|f|-|r|+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a547234dfde7de07fda001155d43268f49dfbe7a). An auxiliary function     a u x   {\displaystyle aux}  ![{\displaystyle aux}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f1d8984de37086335c4d81f52321e0da0e8bdebb) must then be called for the invariant to be satisfied. Two cases must be considered, depending on whether     s   {\displaystyle s}  ![{\displaystyle s}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01d131dfd7673938b947072a13a9744fe997e632) is the empty list, in which case      |  r  |  =  |  f  |  + 1   {\displaystyle |r|=|f|+1}  ![{\displaystyle |r|=|f|+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6acd66aac56ebee7e4f790772e9a3a5e27c2568), or not. The formal definition is     aux ⁡ ⁡  ( f , r , Cons ⁡ ⁡  ( _ _  , s ) ) = ( f , r , s )   {\displaystyle \operatorname {aux} (f,r,\operatorname {Cons} (\_,s))=(f,r,s)}  ![{\displaystyle \operatorname {aux} (f,r,\operatorname {Cons} (\_,s))=(f,r,s)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7422e0514cb6e65ce380bb4d160bd96b3aefe8f6) and     aux ⁡ ⁡  ( f , r ,  NIL  ) = (  f ′  ,  NIL  ,  f ′  )   {\displaystyle \operatorname {aux} (f,r,{\text{NIL}})=(f',{\text{NIL}},f')}  ![{\displaystyle \operatorname {aux} (f,r,{\text{NIL}})=(f',{\text{NIL}},f')}](https://wikimedia.org/api/rest_v1/media/math/render/svg/972bbc8c6fca6241d40adbf53ed1b201024da478) where      f ′    {\displaystyle f'}  ![{\displaystyle f'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/258eaada38956fb69b8cb1a2eef46bcb97d3126b) is *f* followed by *r* reversed.

 

Let us call     reverse ⁡ ⁡  ( f , r )   {\displaystyle \operatorname {reverse} (f,r)}  ![{\displaystyle \operatorname {reverse} (f,r)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/062f12d75d3a05fe9e64699ae805de069c04b885) the function which returns *f* followed by *r* reversed. Let us furthermore assume that      |  r  |  =  |  f  |  + 1   {\displaystyle |r|=|f|+1}  ![{\displaystyle |r|=|f|+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6acd66aac56ebee7e4f790772e9a3a5e27c2568), since it is the case when this function is called. More precisely, we define a lazy function     rotate ⁡ ⁡  ( f , r , a )   {\displaystyle \operatorname {rotate} (f,r,a)}  ![{\displaystyle \operatorname {rotate} (f,r,a)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/db852d453bb40f496727ff7038dc8873e4cb7285) which takes as input three lists such that      |  r  |  =  |  f  |  + 1   {\displaystyle |r|=|f|+1}  ![{\displaystyle |r|=|f|+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6acd66aac56ebee7e4f790772e9a3a5e27c2568), and return the concatenation of *f*, of *r* reversed and of *a*. Then     reverse ⁡ ⁡  ( f , r ) = rotate ⁡ ⁡  ( f , r ,  NIL  )   {\displaystyle \operatorname {reverse} (f,r)=\operatorname {rotate} (f,r,{\text{NIL}})}  ![{\displaystyle \operatorname {reverse} (f,r)=\operatorname {rotate} (f,r,{\text{NIL}})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8548c5df6a5863740e385e534113975fdf6c5536).
The inductive definition of rotate is     rotate ⁡ ⁡  (  NIL  , Cons ⁡ ⁡  ( y ,  NIL  ) , a ) = Cons ⁡ ⁡  ( y , a )   {\displaystyle \operatorname {rotate} ({\text{NIL}},\operatorname {Cons} (y,{\text{NIL}}),a)=\operatorname {Cons} (y,a)}  ![{\displaystyle \operatorname {rotate} ({\text{NIL}},\operatorname {Cons} (y,{\text{NIL}}),a)=\operatorname {Cons} (y,a)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/256cf634aaf5a3aa98d7962615e90aac29a762cd) and     rotate ⁡ ⁡  ( CONS ⁡ ⁡  ( x , f ) , CONS ⁡ ⁡  ( y , r ) , a ) = Cons ⁡ ⁡  ( x , rotate ⁡ ⁡  ( f , r , CONS ⁡ ⁡  ( y , a ) ) )   {\displaystyle \operatorname {rotate} (\operatorname {CONS} (x,f),\operatorname {CONS} (y,r),a)=\operatorname {Cons} (x,\operatorname {rotate} (f,r,\operatorname {CONS} (y,a)))}  ![{\displaystyle \operatorname {rotate} (\operatorname {CONS} (x,f),\operatorname {CONS} (y,r),a)=\operatorname {Cons} (x,\operatorname {rotate} (f,r,\operatorname {CONS} (y,a)))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8ce338cfb19c7a34670602886119d616b3071d0a). Its running time is     O ( r )   {\displaystyle O(r)}  ![{\displaystyle O(r)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/307168a31698bc14ae0f0d7bccff65b128cd00d5), but, since lazy evaluation is used, the computation is delayed until the results are forced by the computation.

 

The list *s* in the data structure has two purposes. This list serves as a counter for      |  f  |  − −   |  r  |    {\displaystyle |f|-|r|}  ![{\displaystyle |f|-|r|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/08745a8ef53c631d1b9e9170f0e42d84be6221d5), indeed,      |  f  |  =  |  r  |    {\displaystyle |f|=|r|}  ![{\displaystyle |f|=|r|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/55e3ac72d5ef500a58a66210cb61afd3bc28f10b) if and only if *s* is the empty list. This counter allows us to ensure that the rear is never longer than the front list. Furthermore, using *s*, which is a tail of *f*, forces the computation of a part of the (lazy) list *f* during each *tail* and *insert* operation. Therefore, when      |  f  |  =  |  r  |    {\displaystyle |f|=|r|}  ![{\displaystyle |f|=|r|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/55e3ac72d5ef500a58a66210cb61afd3bc28f10b), the list *f* is totally forced. If it was not the case, the internal representation of *f* could be some append of append of... of append, and forcing would not be a constant time operation anymore.

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Octicons-terminal.svg/40px-Octicons-terminal.svg.png)](./File:Octicons-terminal.svg)[Computer programming portal](./Portal:Computer_programming)

 
- [Event loop](./Event_loop) - events are stored in a queue
- [Message queue](./Message_queue)
- [Priority queue](./Priority_queue)
- [Queuing theory](./Queueing_theory)
- [Stack (abstract data type)](./Stack_(abstract_data_type)) – the "opposite" of a queue: LIFO (Last In First Out)

 

## References

  
1. [↑](./Queue_(abstract_data_type)#cite_ref-1) ["Queue (Java Platform SE 7)"](http://docs.oracle.com/javase/7/docs/api/java/util/Queue.html). Docs.oracle.com. 2014-03-26. Retrieved 2014-05-22.
2. [↑](./Queue_(abstract_data_type)#cite_ref-2) ["Class Array"](https://docs.ruby-lang.org/en/master/Array.html#class-Array-label-Adding+Items+to+an+Array).
3. [↑](./Queue_(abstract_data_type)#cite_ref-3) Okasaki, Chris. ["Purely Functional Data Structures"](https://web.archive.org/web/20231207173058/https://doc.lagout.org/programmation/Functional%20Programming/Chris_Okasaki-Purely_Functional_Data_Structures-Cambridge_University_Press%281998%29.pdf) (PDF). Archived from [the original](https://doc.lagout.org/programmation/Functional%20Programming/Chris_Okasaki-Purely_Functional_Data_Structures-Cambridge_University_Press%281998%29.pdf) (PDF) on 2023-12-07. Retrieved 2022-04-19.
4. [↑](./Queue_(abstract_data_type)#cite_ref-4) Hood, Robert; Melville, Robert (November 1981). "Real-time queue operations in pure Lisp". *Information Processing Letters*. **13** (2): 50–54. [doi](./Doi_(identifier)):[10.1016/0020-0190(81)90030-2](https://doi.org/10.1016%2F0020-0190%2881%2990030-2). [hdl](./Hdl_(identifier)):[1813/6273](https://hdl.handle.net/1813%2F6273).

 

### General references

 
- ![Public Domain](//upload.wikimedia.org/wikipedia/en/thumb/6/62/PD-icon.svg/20px-PD-icon.svg.png) This article incorporates [public domain material](./Copyright_status_of_works_by_the_federal_government_of_the_United_States) from Paul E. Black. ["Bounded queue"](https://xlinux.nist.gov/dads/HTML/boundedqueue.html). *[Dictionary of Algorithms and Data Structures](./Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)*. [NIST](./National_Institute_of_Standards_and_Technology).

 

## Further reading

  
- [Knuth, Donald](./Donald_Knuth) (1997). "§2.2.1: Stacks, Queues, and Dequeues". [*The Art of Computer Programming*](./The_Art_of_Computer_Programming). Vol. 1: Fundamental Algorithms (3rd ed.). Addison-Wesley. pp. 238–243. [ISBN](./ISBN_(identifier)) [0-201-89683-4](./Special:BookSources/0-201-89683-4).
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). "§10.1: Stacks and queues". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 200–4. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
- Ford, William; [Topp, William](./William_Topp?action=edit&redlink=1) (2002). "8. Queues and Priority Queues". *Data Structures with C++ and STL* (2nd ed.). Prentice Hall. pp. 386–390. [ISBN](./ISBN_(identifier)) [0-13-085850-1](./Special:BookSources/0-13-085850-1).
- [Drozdek, Adam](./Adam_Drozdek?action=edit&redlink=1) (2005). "4. Stacks and Queues". *Data Structures and Algorithms in C++* (3rd ed.). Thomson Course Technology. pp. 137–169. [ISBN](./ISBN_(identifier)) [978-0-534-49182-6](./Special:BookSources/978-0-534-49182-6).

  

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Queue data structure](https://commons.wikimedia.org/wiki/Category:Queue%20data%20structure).  
- [STL Quick Reference](http://www.halpernwightsoftware.com/stdlib-scratch/quickref.html#containers14)
- [VBScript implementation of stack, queue, deque, and Red-Black Tree](https://web.archive.org/web/20110714000645/http://www.ludvikjerabek.com/downloads.html)

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |