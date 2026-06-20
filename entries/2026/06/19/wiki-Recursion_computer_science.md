---
source: sources/wiki-Recursion_computer_science.md
source_url: https://en.wikipedia.org/wiki/Recursion_(computer_science)
---

I'll create the study notes entry now.

## Recursion in Computer Science

Recursion is a method of solving computational problems where the solution depends on solutions to smaller instances of the same problem, implemented via functions that call themselves. It is one of the central ideas of computer science, capable of defining infinite sets of objects or computations through finite statements. Recursion-only languages are proven Turing complete, making them equivalent in power to imperative languages with loops.

## Key Concepts

- **Base case**: The stopping condition that provides a direct result without further recursion; prevents infinite regress. Omitting or incorrectly defining the base case leads to infinite recursion or stack overflow.
- **Recursive case**: Describes how to decompose a problem into smaller sub-problems of the same form, each step progressing toward a base case.
- **Single recursion**: Contains only one self-reference (e.g., factorial, linear search). Generally replaceable by iteration in linear time and constant space.
- **Multiple recursion**: Contains multiple self-references (e.g., naive Fibonacci, tree traversal). May require exponential time/space and cannot be replaced by iteration without an explicit stack.
- **Direct recursion**: A function calls itself.
- **Indirect (mutual) recursion**: Function f calls function g, which calls f again. Chains of three or more functions are possible.
- **Structural recursion**: Recursion where each call receives an immediate structural component of the input (e.g., tree traversals, XML processing). Termination is provable via structural induction.
- **Generative recursion**: Recursion that generates entirely new data from the input and recurses on it (e.g., quicksort, binary search, mergesort, Newton's method, GCD). Termination is not automatically guaranteed and requires further analysis.
- **Recursive data types**: Self-referential data definitions. Inductive definitions specify how to construct instances (e.g., linked lists, natural numbers, BNF grammars). Coinductive definitions specify operations on possibly infinite structures (e.g., infinite streams).
- **Corecursion**: Related to coinduction; computes instances of possibly infinite objects. Used with lazy evaluation when output size is unknown.
- **Call stack overhead**: Recursive calls accumulate stack frames proportional to input size; recursion is generally less efficient than iteration for problems solvable iteratively.
- **Tail call optimization**: Compiler technique that can improve recursive performance by reusing stack frames when the recursive call is the last operation.

## Commands and Syntax

**Factorial — base case and recursive case (C):**
```c
int fac1(int n) {
    if (n <= 0) { return 1; }       // base case
    else { return fac1(n-1) * n; }  // recursive case
}
```

**Recursive data type definition (Haskell):**
```haskell
data ListOfStrings = EmptyList | Cons String ListOfStrings
```

**BNF grammar with recursive definition:**
```
<expr> ::= <number>
         | (<expr> * <expr>)
         | (<expr> + <expr>)
```

**DFS with short-circuit optimization (C):**
```c
bool tree_contains(struct BinaryTree* node, int i) {
    if (!node) return false;
    return tree_contains_aux(node, i);
}

bool tree_contains_aux(struct BinaryTree* node, int i) {
    if (node->data == i) return true;
    return (node->left && tree_contains_aux(node->left, i))
        || (node->right && tree_contains_aux(node->right, i));
}
```

**Wrapper function pattern**: Validate parameters, initialize state, then delegate to a private recursive auxiliary function.

**Hybrid algorithm pattern**: Start with recursion, switch to a different algorithm (e.g., insertion sort) when input becomes small enough to avoid function call overhead.

## Relationships

- **Mathematical induction**: Recursion mirrors induction — base case corresponds to the base case of a proof, recursive case corresponds to the inductive step.
- **Iteration**: Recursion and iteration are equally expressive. Recursion can be replaced by iteration with an explicit stack; iteration can be replaced by tail recursion.
- **Divide and conquer**: Algorithms like merge sort, quicksort, and binary search use recursion to split problems into sub-problems.
- **Tree traversal / DFS**: Natural application of recursion; trees are themselves recursively defined data structures.
- **Computability theory**: Recursive function theory (Church, Godel, Kleene, Turing) underpins the theoretical foundations.
- **Functional programming**: Languages like Clojure and LISP rely on recursion as the primary control flow mechanism instead of loops.
- **ALGOL 60 and LISP**: First languages to formally support recursion (1960), influencing all subsequent language design.
- **Lazy evaluation**: Corecursion pairs with lazy evaluation for computing finite portions of infinite structures.
- **Memoization**: Wrapper functions often handle memoization setup to avoid redundant recomputation in recursive calls.

## Exam-Relevant Points

- Every recursive function requires at least one **base case** and at least one **recursive case**; missing either causes infinite recursion.
- **Single recursion** runs in O(n) time and O(1) space (with iteration); **multiple recursion** (e.g., naive Fibonacci) can be exponential in time and space.
- **Structural recursion** always terminates on finite data (provable by structural induction); **generative recursion** termination requires separate proof.
- Recursion-only languages are **Turing complete** — equivalent in computational power to imperative languages with loops.
- **Short-circuiting (arm's-length recursion)** checks the base case before the recursive call rather than after, cutting function calls in half for perfect binary trees (from 2^(h+1) null-pointer checks to 2^h leaf checks).
- **Hybrid algorithms** switch from recursion to iteration for small inputs to reduce overhead (e.g., merge sort switching to insertion sort = tiled merge sort / Timsort).
- **Indirect/mutual recursion**: f calls g calls f. Requires forward declarations in some languages.
- Multiple recursion can sometimes be converted to single recursion by passing additional state as parameters (e.g., Fibonacci with two accumulator parameters).
- **Wrapper functions** handle parameter validation, initialization, and memoization setup before delegating to the recursive auxiliary function.
- **LISP** (McCarthy, 1960) was the first language to use recursion as a core feature; **ALGOL 60** independently added recursive procedure calls the same year.
