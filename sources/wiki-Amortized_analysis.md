---
source: https://en.wikipedia.org/wiki/Amortized_analysis
fetched: 2026-06-19
---

Method for algorithm analysis in computer science "Amortized" redirects here. For other uses, see [Amortization](./Amortization_(disambiguation)). 

In [computer science](./Computer_science), **amortized analysis** is a method for [analyzing](./Analysis_of_algorithms) a given algorithm's [complexity](./Computational_complexity), or how much of a resource, especially time or memory, it takes to [execute](./Execution_(computing)).  The motivation for amortized analysis is that looking at the worst-case run time can be too pessimistic.  Instead, amortized analysis averages the running times of operations in a sequence over that sequence.[[1]](./Amortized_analysis#cite_note-tarjan-1): 306 
As a conclusion: "Amortized analysis is a useful tool that complements other techniques such as [worst-case](./Worst-case_execution_time) and [average-case](./Average-case_complexity) analysis."[[2]](./Amortized_analysis#cite_note-fiebrink-2): 14 [[3]](./Amortized_analysis#cite_note-3)

 

For a given operation of an algorithm, certain situations (e.g., input parametrizations or data structure contents) may imply a significant cost in resources, whereas other situations may not be as costly.  The amortized analysis considers both the costly and less costly operations together over the whole sequence of operations.  This may include accounting for different types of input, length of the input, and other factors that affect its performance.[[2]](./Amortized_analysis#cite_note-fiebrink-2)

 

## History

 

Amortized analysis initially emerged from a method called aggregate analysis, which is now subsumed by amortized analysis. The technique was first formally introduced by [Robert Tarjan](./Robert_Tarjan) in his 1985 paper *Amortized Computational Complexity*,[[1]](./Amortized_analysis#cite_note-tarjan-1) which addressed the need for a more useful form of analysis than the common probabilistic methods used. Amortization was initially used for very specific types of algorithms, particularly those involving [binary trees](./Binary_tree) and [union](./Union-find_data_structure) operations. However, it is now ubiquitous and comes into play when analyzing many other algorithms as well.[[2]](./Amortized_analysis#cite_note-fiebrink-2)

 

## Method

 Main articles: [Accounting method (computer science)](./Accounting_method_(computer_science)) and [Potential method](./Potential_method) 

Amortized analysis requires knowledge of which series of operations are possible. This is most commonly the case with [data structures](./Data_structure), which have a [state](./State_(computer_science)) that persists between operations. The basic idea is that a worst-case operation can alter the state in such a way that the worst case cannot occur again for a long time, thus "amortizing" its cost.

 

There are generally three methods for performing amortized analysis: the aggregate method, the [accounting method](./Accounting_method_(computer_science)), and the [potential method](./Potential_method). All of these give correct answers; the choice of which to use depends on which is most convenient for a particular situation.[[4]](./Amortized_analysis#cite_note-Lecture_20-4)

 
- Aggregate analysis determines the upper bound *T*(*n*) on the total cost of a sequence of *n* operations, then calculates the amortized cost to be *T*(*n*) / *n*.[[4]](./Amortized_analysis#cite_note-Lecture_20-4)
- The [accounting method](./Accounting_method_(computer_science)) is a form of aggregate analysis which assigns to each operation an *amortized cost* which may differ from its actual cost.  Early operations have an amortized cost higher than their actual cost, which accumulates a saved "credit" that pays for later operations having an amortized cost lower than their actual cost.  Because the credit begins at zero, the actual cost of a sequence of operations equals the amortized cost minus the accumulated credit.  Because the credit is required to be non-negative, the amortized cost is an upper bound on the actual cost.  Usually, many short-running operations accumulate such credit in small increments, while rare long-running operations decrease it drastically.[[4]](./Amortized_analysis#cite_note-Lecture_20-4)
- The [potential method](./Potential_method) is a form of the accounting method where the saved credit is computed as a function (the "potential") of the state of the data structure.  The amortized cost is the immediate cost plus the change in potential.[[4]](./Amortized_analysis#cite_note-Lecture_20-4)

 

## Examples

 

### Dynamic array

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3c/ArrayListAmotizedPush.png/330px-ArrayListAmotizedPush.png)](./File:ArrayListAmotizedPush.png)Amortized analysis of the push operation for a dynamic array 

Consider a [dynamic array](./Dynamic_array) that grows in size as more elements are added to it, such as `ArrayList` in Java or `std::vector` in C++. If we started out with a dynamic array of size 4, we could push 4 elements onto it, and each operation would take [constant time](./Constant_time). Yet pushing a fifth element onto that array would take longer as the array would have to create a new array of a scaled size, copy the old elements onto the new array, then add the new element. The next few push operations would similarly take constant time, then the subsequent addition would require another slow scaling of the array size.

 

In general, for an arbitrary number     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) of pushes to an array of any initial size, the times for steps that scale the array add in a [geometric series](./Geometric_series) to     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a), while the constant times for each remaining push also add to     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a). Therefore the average time per push operation is     O ( n )  /  n = O ( 1 )   {\displaystyle O(n)/n=O(1)}  ![{\displaystyle O(n)/n=O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/646a933a329e9c1be029dd0e4f1018fbdbc34266). This reasoning can be formalized and generalized to more complicated data structures using amortized analysis.[[4]](./Amortized_analysis#cite_note-Lecture_20-4)

 

### Queue

 

Shown is a [Python](./Python_(programming_language)) implementation of a [queue](./Queue_(abstract_data_type)), a [FIFO data structure](./FIFO_(computing_and_electronics)):

 
```
class Queue:
    """Represents a first-in, first-out collection."""
    # Initialize the queue with two empty lists
    def __init__(self):
        self.input = []  # Stores elements that are enqueued
        self.output = []  # Stores elements that are dequeued

    def enqueue(self, element):
        """Add an object to the end of the queue."""
        self.input.append(element)  # Append the element to the input list

    def dequeue(self):
        """Remove and return the object at the beginning of the queue."""
        if not self.output:  # If the output list is empty
            # Transfer all elements from the input list to the output list, reversing the order
            while self.input:  # While the input list is not empty
                self.output.append(
                    self.input.pop()
                )  # Pop the last element from the input list and append it to the output list

        return self.output.pop()  # Pop and return the last element from the output list

```
 

The enqueue operation just pushes an element onto the input array; this operation does not depend on the lengths of either input or output and therefore runs in constant time.

 

However the dequeue operation is more complicated.  If the output array already has some elements in it, then dequeue runs in constant time; otherwise, dequeue takes ⁠    O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a)⁠ time to add all the elements onto the output array from the input array, where *n* is the current length of the input array.  After copying *n* elements from input, we can perform *n* dequeue operations, each taking constant time, before the output array is empty again. Thus, we can perform a sequence of *n* dequeue operations in only ⁠    O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a)⁠ time, which implies that the amortized time of each dequeue operation is ⁠    O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21)⁠.[[5]](./Amortized_analysis#cite_note-Grossman-5)

 

Alternatively, we can charge the cost of copying any item from the input array to the output array to the earlier enqueue operation for that item.  This charging scheme doubles the amortized time for enqueue but reduces the amortized time for dequeue to ⁠    O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21)⁠.

 

## Common use

 
- In common usage, an "amortized algorithm" is one that an amortized analysis has shown to perform well.
- [Online algorithms](./Online_algorithm) commonly use amortized analysis.

 

## References

  
1. [1](./Amortized_analysis#cite_ref-tarjan_1-0) [2](./Amortized_analysis#cite_ref-tarjan_1-1) [Tarjan, Robert Endre](./Robert_Tarjan) (April 1985). ["Amortized Computational Complexity"](http://www.cs.duke.edu/courses/fall11/cps234/reading/Tarjan85_AmortizedComplexity.pdf) (PDF). *SIAM Journal on Algebraic and Discrete Methods*. **6** (2): 306–318. [doi](./Doi_(identifier)):[10.1137/0606031](https://doi.org/10.1137%2F0606031). [Archived](https://web.archive.org/web/20150226051958/http://www.cs.duke.edu/courses/fall11/cps234/reading/Tarjan85_AmortizedComplexity.pdf) (PDF) from the original on 26 February 2015. Retrieved 9 June 2024.was:http://www.cs.princeton.edu/courses/archive/spr06/cos423/Handouts/Amortized.pdf
2. [1](./Amortized_analysis#cite_ref-fiebrink_2-0) [2](./Amortized_analysis#cite_ref-fiebrink_2-1) [3](./Amortized_analysis#cite_ref-fiebrink_2-2) Rebecca Fiebrink (2007), [*Amortized Analysis Explained*](https://web.archive.org/web/20131020020356/http://www.cs.princeton.edu/~fiebrink/423/AmortizedAnalysisExplained_Fiebrink.pdf) (PDF), archived from [the original](http://www.cs.princeton.edu/~fiebrink/423/AmortizedAnalysisExplained_Fiebrink.pdf) (PDF) on 20 October 2013, retrieved 3 May 2011
3. [↑](./Amortized_analysis#cite_ref-3) ["Lecture 18: Amortized Algorithms"](https://www.cs.cornell.edu/courses/cs312/2006sp/lectures/lec18.html). *CS312 -Data Structures and Functional Programming*. Cornell University. 2006. [Amortized analysis] is different from what is commonly referred to as average case analysis, because amortized analysis does not make any assumption about the distribution of the data values, whereas average case analysis assumes the data are not "bad" (e.g., some sorting algorithms do well on "average" over all input orderings but very badly on certain input orderings).  That is, amortized analysis is a worst case analysis, but for a sequence of operations, rather than for individual operations.
4. [1](./Amortized_analysis#cite_ref-Lecture_20_4-0) [2](./Amortized_analysis#cite_ref-Lecture_20_4-1) [3](./Amortized_analysis#cite_ref-Lecture_20_4-2) [4](./Amortized_analysis#cite_ref-Lecture_20_4-3) [5](./Amortized_analysis#cite_ref-Lecture_20_4-4) Kozen, Dexter (Spring 2011). ["CS 3110 Lecture 20: Amortized Analysis"](https://www.cs.cornell.edu/courses/cs3110/2011sp/lectures/lec20-amortized/amortized.htm). [Cornell University](./Cornell_University). Retrieved 14 March 2015.
5. [↑](./Amortized_analysis#cite_ref-Grossman_5-0) Grossman, Dan. ["CSE332: Data Abstractions"](http://courses.cs.washington.edu/courses/cse332/10sp/lectures/lecture21.pdf) (PDF). *cs.washington.edu*. Retrieved 14 March 2015.

 

## Literature

 
- ["Lecture 7: Amortized Analysis"](https://www.cs.cmu.edu/afs/cs/academic/class/15451-s07/www/lecture_notes/lect0206.pdf) (PDF). [Carnegie Mellon University](./Carnegie_Mellon_University). Retrieved 14 March 2015.
- [Allan Borodin](./Allan_Borodin) and Ran El-Yaniv (1998). [*Online Computation and Competitive Analysis*](https://www.cs.technion.ac.il/~rani/book.html). pp. 20, 141.