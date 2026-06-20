---
source: sources/wiki-Divide-and-conquer_algorithm.md
source_url: https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm
---

Here's the structured summary:

## Divide-and-Conquer Algorithm Design Paradigm

Divide and conquer is a fundamental algorithm design paradigm in which a problem is recursively broken down into two or more sub-problems of the same or related type until they become simple enough to solve directly. The solutions to the sub-problems are then combined to produce the solution to the original problem. This paradigm underlies many of the most efficient known algorithms for sorting, multiplication, matrix operations, and signal processing.

## Key Concepts

- **Three-step structure**: (1) Divide the problem into smaller sub-problems, (2) Conquer each sub-problem recursively, (3) Combine the solutions to form the answer to the original problem.
- **Decrease and conquer**: A variant where each problem reduces to only *one* sub-problem (e.g., binary search, Euclidean algorithm). Some authors reserve "divide and conquer" for the multi-subproblem case only.
- **Prune and search**: When the search space is reduced by a constant factor at each step, the overall algorithm has the same asymptotic complexity as the pruning step (geometric series argument).
- **Base cases**: The small subproblems solved directly to terminate recursion. Choosing larger base cases and switching to non-recursive algorithms (hybrid approach) often improves practical performance.
- **Short-circuiting the base case** (arm's-length recursion): Checking whether the next recursive call would hit a base case *before* making the call, avoiding unnecessary function invocations.
- **Correctness** is typically proved via mathematical induction; **complexity** is determined by solving recurrence relations.
- **Cache-oblivious behavior**: D&C algorithms naturally exploit memory hierarchy — once sub-problems fit in cache, all further work stays in cache without needing to know cache size explicitly.
- **Parallelism**: Sub-problems are independent and can be distributed across processors, making D&C algorithms naturally suited to multi-processor and shared-memory systems.
- **Roundoff control**: D&C approaches like pairwise summation can yield more numerically accurate results than equivalent iterative methods due to reduced floating-point error accumulation.
- **Overlapping subproblems**: When D&C recursion evaluates the same sub-problem repeatedly, memoization can be applied, leading toward dynamic programming as the limit of this technique.

## Commands and Syntax

No specific commands. The paradigm is expressed in pseudocode form:

```
function DivideAndConquer(problem):
    if problem is small enough:
        return DirectSolve(problem)
    subproblems = Divide(problem)
    solutions = [DivideAndConquer(sp) for sp in subproblems]
    return Combine(solutions)
```

**Complexity formulas** (for sub-problems of size ~n/p with O(n) split/combine work):
- General case: O(n log_p n)
- With q > 2 sub-problems of size n/2 and O(n) overhead: O(n^(log_2 q))
- With 1 sub-problem of size n/2 and O(n) overhead: O(n)
- With 2 sub-problems of size n/2 and O(n^2) overhead: O(n^2)

These are instances of the **Master Theorem**.

## Relationships

- **Sorting algorithms**: Merge sort and quicksort are canonical D&C examples. Radix sort relates to the postal-routing D&C analogy.
- **Master Theorem**: The primary tool for solving D&C recurrence relations — directly determines time complexity from the number of sub-problems, their size ratio, and overhead cost.
- **Akra-Bazzi method**: A generalization of the Master Theorem for more complex D&C recurrences.
- **Dynamic programming**: Arises when D&C has overlapping subproblems; memoization bridges D&C to DP.
- **Binary search**: A decrease-and-conquer algorithm (single sub-problem variant).
- **Karatsuba algorithm**: D&C for integer multiplication, achieving O(n^1.585) instead of O(n^2).
- **Strassen algorithm**: D&C for matrix multiplication.
- **FFT (Cooley-Tukey)**: D&C for computing discrete Fourier transforms.
- **Recursion and call stack**: D&C is naturally implemented via recursion; stack overflow is a practical concern.
- **Cache-oblivious algorithms**: D&C is the foundational technique for designing algorithms that optimally use memory hierarchy without knowing cache parameters.
- **Fork-join model**: The parallel computing model that maps naturally to D&C execution.
- **MapReduce**: A distributed computing paradigm with structural similarity to D&C.
- **Branch-and-bound**: Can use explicit stack-based D&C implementation for optimization.
- **Big O notation**: Used throughout to express D&C complexity bounds.

## Exam-Relevant Points

- D&C has three steps: **divide**, **conquer** (recurse), **combine**. Know this structure cold.
- **Decrease and conquer** = single sub-problem (binary search, Euclidean GCD). **Divide and conquer** (strict) = two or more sub-problems.
- The complexity of D&C algorithms is determined by **recurrence relations**, typically solved with the **Master Theorem**.
- For p sub-problems of size n/p with O(n) overhead: **O(n log_p n)** — this gives merge sort's O(n log n).
- For q > 2 sub-problems of size n/2 with O(n) overhead: **O(n^(log_2 q))** — this gives Karatsuba's O(n^1.585) for q=3.
- Karatsuba (1960) disproved Kolmogorov's conjecture that multiplication requires Ω(n^2) operations.
- **Merge sort** (von Neumann, 1945) was the first D&C algorithm specifically developed for computers.
- D&C algorithms are **cache-oblivious**: they exploit memory hierarchy without explicit cache-size parameters.
- D&C algorithms are **naturally parallelizable** — sub-problems can execute on different processors.
- **Hybrid algorithms**: Practical implementations switch to simpler algorithms (e.g., insertion sort) at small base cases to reduce overhead. This is why library quicksort implementations use insertion sort for small partitions.
- Quicksort's recursion depth can be limited to **O(log n)** with proper implementation (always recurse on the smaller partition first).
- **Pairwise summation** demonstrates that D&C can improve numerical accuracy over iterative approaches.
- When D&C produces **overlapping subproblems**, memoization converts it into **dynamic programming**.
- Binary search dates conceptually to Babylonia (~200 BC); the computer algorithm was described by Mauchly in 1946.
- Gauss described what became the FFT algorithm in 1805, though it wasn't widely used until Cooley-Tukey rediscovered it over 150 years later.

I wasn't able to write the file due to permissions — you'll need to grant write access to the entries directory if you'd like me to save it.
