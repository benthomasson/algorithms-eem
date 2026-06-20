---
source: https://en.wikipedia.org/wiki/Recursion_(computer_science)
fetched: 2026-06-19
---

Use of functions that call themselves This article is about recursive approaches to solving problems. For proofs by recursion, see [Mathematical induction](./Mathematical_induction). For recursion in computer science acronyms, see [Recursive acronym § Computer-related examples](./Recursive_acronym#Computer-related_examples). For general use of the term, see [Recursion](./Recursion). 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Snowflake_Recursion.jpg/250px-Snowflake_Recursion.jpg)](./File:Snowflake_Recursion.jpg)Snowflake pattern made using recursion[![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Honeycomb_Recursion.jpg/120px-Honeycomb_Recursion.jpg)](./File:Honeycomb_Recursion.jpg)Honeycomb pattern made using recursion[![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f7/RecursiveTree.JPG/120px-RecursiveTree.JPG)](./File:RecursiveTree.JPG)Tree fractal created using the [Logo programming language](./Logo_(programming_language))[![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a6/Sierpinski_triangle_turtle.gif/250px-Sierpinski_triangle_turtle.gif)](./File:Sierpinski_triangle_turtle.gif)Recursive drawing of a [Sierpiński Triangle](./Sierpiński_triangle) through [turtle graphics](./Turtle_graphics)Examples made using recursion 

In [computer science](./Computer_science), **recursion** is a method of solving a [computational problem](./Computational_problem) where the solution depends on solutions to smaller instances of the same problem.[[1]](./Recursion_(computer_science)#cite_note-1)[[2]](./Recursion_(computer_science)#cite_note-2) Recursion solves such [recursive problems](./Recursion) by using [functions](./Function_(computer_science)) that call themselves from within their own code. The approach can be applied to many types of problems, and recursion is one of the central ideas of computer science.[[3]](./Recursion_(computer_science)#cite_note-3)

 

The power of recursion evidently lies in the possibility of defining an [infinite set](./Infinite_set) of objects by a finite [statement](./Statement_(computer_science)). In the same manner, an infinite number of computations can be described by a finite recursive program, even if this program contains no explicit repetitions.

— [Niklaus Wirth](./Niklaus_Wirth), *Algorithms + Data Structures = Programs*, 1976[[4]](./Recursion_(computer_science)#cite_note-4)

 

Most computer [programming languages](./Programming_language) support recursion by allowing a function to call itself from within its own code. Some [functional programming](./Functional_programming) languages (for instance, [Clojure](./Clojure))[[5]](./Recursion_(computer_science)#cite_note-5) do not define any built-in looping constructs, and instead rely solely on recursion. It is proved in [computability theory](./Computability_theory) that these recursion-only languages are [Turing complete](./Turing_complete); this means that they are as powerful (they can be used to solve the same problems) as [imperative languages](./Imperative_language) based on control structures such as `while` and `for`.

 

Repeatedly calling a function from within itself may cause the [call stack](./Call_stack) to have a size equal to the sum of the input sizes of all involved calls. It follows that, for problems that can be solved easily by iteration, recursion is generally less [efficient](./Algorithmic_efficiency), and, for certain problems, algorithmic or compiler-optimization techniques such as [tail call](./Tail_call) optimization may improve computational performance over a naive recursive implementation.[*[citation needed](./Wikipedia:Citation_needed)*]

  

## History

 
|  | This sectionneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sourcesin this section. Unsourced material may be challenged and removed.(November 2025)(Learn how and when to remove this message) |
| --- | --- |

 

The development of [recursion](./Recursion_(mathematics)) in computer science grew out of [mathematical logic](./Mathematical_logic) and later became an essential part of [programming language](./Programming_language) design.[[6]](./Recursion_(computer_science)#cite_note-auto5-6) The early work done by [Church](./Alonzo_Church), [Gödel](./Kurt_Gödel), [Kleene](./Stephen_Cole_Kleene), and [Turing](./Alan_Turing) on recursive function and [computability](./Computability) laid the groundwork that made recursion possible in programming languages.[[6]](./Recursion_(computer_science)#cite_note-auto5-6) Recursion has been used by mathematicians for a long time, but it only became a practical tool for programming in the late 1950s and early 1960s.[[7]](./Recursion_(computer_science)#cite_note-auto3-7) Key figures such as [John McCarthy](./John_McCarthy_(computer_scientist)) and the [ALGOL 60](./ALGOL_60) design committee contributed to introducing recursion into programming.[[7]](./Recursion_(computer_science)#cite_note-auto3-7)

 

John McCarthy took the first steps by creating the programming language [LISP](./Lisp_(programming_language)) in 1960.[[8]](./Recursion_(computer_science)#cite_note-auto-8) In his paper *Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I*, McCarthy showed that recursion could be core in a programming language that works with symbols by processing them step by step.[[8]](./Recursion_(computer_science)#cite_note-auto-8) In LISP, recursion could be used in functions using simple rules, and there was also a way to evaluate them in the language.[[8]](./Recursion_(computer_science)#cite_note-auto-8) This demonstrated that recursion was a practical way to write programs and that it also describes the process of computation.[[6]](./Recursion_(computer_science)#cite_note-auto5-6) Therefore, LISP became one of the first programming languages to use recursion as a main feature, and later on also influenced other languages that followed.[[7]](./Recursion_(computer_science)#cite_note-auto3-7)

 

During that time, recursion was also added to [ALGOL 60](./ALGOL_60).[[9]](./Recursion_(computer_science)#cite_note-auto4-9) The *Report on the Algorithmic Language ALGOL 60*, which was published in 1960, was the outcome of an international attempt at designing a standard language.[[9]](./Recursion_(computer_science)#cite_note-auto4-9) Allowing procedures to call themselves was one of the new important features of the language.[[7]](./Recursion_(computer_science)#cite_note-auto3-7) Before that, only [loops](./Loop_(computing)) were allowed to be used by programmers, so it was a significant change.[[7]](./Recursion_(computer_science)#cite_note-auto3-7) Recursion allowed programmers to describe algorithms in a more natural and flexible way.[[7]](./Recursion_(computer_science)#cite_note-auto3-7)

 

## Structure of a recursive function

 

The definition of a recursive [function](./Function_(computer_programming)) is typically divided into two parts: one or more base case(s) and one or more recursive case(s).[[10]](./Recursion_(computer_science)#cite_note-10) This structure mirrors the logic of [mathematical induction](./Mathematical_induction), which is a proof technique where proving the base case(s) and the inductive step ensures that a given theorem holds for all valid inputs.

 

### Base case

 

The base case specifies input values for which the function can provide a result directly, without any further recursion.[[11]](./Recursion_(computer_science)#cite_note-:0-11) These are typically the simplest or smallest possible inputs (which can be solved trivially), allowing a computation to terminate. Base cases are essential because they prevent infinite regress. In other words, they define a stopping condition that terminates the recursion.

 

An example is computing the [factorial](./Factorial) of an integer n, which is the product of all integers from 0 to n. For this problem, the definition 0! = 1 is a base case. Without it, the recursion may continue indefinitely, leading to non-termination or even [stack overflow](./Stack_overflow) errors in actual implementations.

 

Designing a correct base case is crucial for both theoretical and practical reasons. Some problems have a natural base case (e.g., the empty list is a base case in some recursive list-processing functions), while others require an additional parameter to provide a stopping criterion (e.g., using a depth counter in recursive [tree traversal](./Tree_traversal)).

 

In recursive [computer programming](./Computer_programming), omitting the base case or defining it incorrectly may result in unintended infinite recursion. In a study, researchers showed that many students struggle to identify appropriate base cases.[[11]](./Recursion_(computer_science)#cite_note-:0-11)

 

### Recursive case

 

The recursive case describes how to break down a problem into smaller sub-problems of the same form.[[11]](./Recursion_(computer_science)#cite_note-:0-11) Each recursive step transforms the input so that it approaches a base case, ensuring progress toward termination. If the reduction step fails to progress toward a base case, the algorithm can get trapped in an [infinite loop](./Infinite_loop).

 

In the [factorial](./Factorial) example, the recursive case is defined as:
    n ! = n ⋅ ⋅  ( n − −  1 ) !  , ∀ ∀  n > 0.   {\displaystyle n!=n\cdot (n-1)!\,,\forall n>0.}  ![{\displaystyle n!=n\cdot (n-1)!\,,\forall n>0.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ee432dda6f2785a48965ef3d34ac8e1cf8733b37)
Here, each invocation of the function decreases the input     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)by 1. Thus, it ensures that the recursion eventually reaches the base case of     n = 0   {\displaystyle n=0}  ![{\displaystyle n=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26819344e55f5e671c76c07c18eb4291fcec85ae).

 

The recursive case is analogous to the inductive step in a [proof by induction](./Proof_by_induction): it assumes that the function works for a smaller instance and then extends this assumption to the current input. Recursive definitions and algorithms thus closely parallel inductive arguments in [mathematics](./Mathematics), and their correctness often relies on similar reasoning techniques.

 

### Examples

 

There are several practical applications of recursion that follow the base case and recursive case structure. These are widely used to solve complex problems in computer science.

 
- [Tree traversals](./Tree_traversal), such as [depth-first search](./Depth-first_search), use a recursive case to process each subtree (the recursive case), eventually stopping at leaf nodes (the base case).[[12]](./Recursion_(computer_science)#cite_note-12)
- [Merge sort](./Merge_sort) is a [sorting algorithm](./Sorting_algorithm) that recursively sorts and merges divided subarrays (the recursive case) until each subarray consists of one element (the base case).[[13]](./Recursion_(computer_science)#cite_note-13)
- [Fibonacci sequence](./Fibonacci_sequence) is defined by summing the two previous numbers in the sequence (the recursive case), stopping when n = 0 or n = 1 (the base cases).
- [Binary search](./Binary_search) repeatedly divides the search interval in half (recursive case) until the target is found or the interval is empty (base cases).

 

## Recursive data types

 

Many [computer programs](./Computer_program) must process or generate an arbitrarily large quantity of [data](./Data).  Recursion is a technique for representing data whose exact size is unknown to the [programmer](./Programmer): the programmer can specify this data with a [self-referential](./Self-referential) definition.  There are two types of self-referential definitions: inductive and [coinductive](./Coinductive) definitions.

 Further information: [Algebraic data type](./Algebraic_data_type) 

### Inductively defined data

 Main article: [Recursive data type](./Recursive_data_type) 

An inductively defined recursive data definition is one that specifies how to construct instances of the data.  For example, [linked lists](./Linked_list) can be defined inductively (here, using [Haskell](./Haskell) syntax):

 
```
data ListOfStrings = EmptyList | Cons String ListOfStrings

```
 

The code above specifies a list of strings to be either empty, or a structure that contains a string and a list of strings.  The self-reference in the definition permits the construction of lists of any (finite) number of strings.

 

Another example of inductive [definition](./Definition) is the [natural numbers](./Natural_numbers) (or positive [integers](./Integers)):

 
```
A natural number is either 1 or n+1, where n is a natural number.
```
 

Similarly recursive [definitions](./Definition) are often used to model the structure of [expressions](./Expression_(programming)) and [statements](./Statement_(programming)) in programming languages.  Language designers often express grammars in a syntax such as [Backus–Naur form](./Backus–Naur_form); here is such a grammar, for a simple language of arithmetic expressions with multiplication and addition:

 
```
 <expr> ::= <number>
          | (<expr> * <expr>)
          | (<expr> + <expr>)

```
 

This says that an expression is either a number, a product of two expressions, or a sum of two expressions.  By recursively referring to expressions in the second and third lines, the grammar permits arbitrarily complicated arithmetic expressions such as `(5 * ((3 * 6) + 8))`, with more than one product or sum operation in a single expression.

 

### Coinductively defined data and corecursion

 Main articles: [Coinduction](./Coinduction) and [Corecursion](./Corecursion) 

A coinductive data definition is one that specifies the operations that may be performed on a piece of data; typically, self-referential coinductive definitions are used for data structures of infinite size.

 

A coinductive definition of infinite [streams](./Stream_(computer_science)) of strings, given informally, might look like this:

 
```
A stream of strings is an object s such that:
 head(s) is a string, and
 tail(s) is a stream of strings.
```
 

This is very similar to an inductive definition of lists of strings; the difference is that this definition specifies how to access the contents of the data structure—namely, via the [accessor](./Accessor) functions `head` and `tail`—and what those contents may be, whereas the inductive definition specifies how to create the structure and what it may be created from.

 

Corecursion is related to coinduction, and can be used to compute particular instances of (possibly) infinite objects.  As a programming technique, it is used most often in the context of [lazy](./Lazy_evaluation) programming languages, and can be preferable to recursion when the desired size or precision of a program's output is unknown.  In such cases the program requires both a definition for an infinitely large (or infinitely precise) result, and a mechanism for taking a finite portion of that result.  The problem of computing the first n [prime numbers](./Prime_numbers) is one that can be solved with a corecursive program (e.g. [here](./Fold_(higher-order_function)#Examples)).

 

## Types of recursion

 

### Single recursion and multiple recursion

 

Recursion that contains only a single self-reference is known as **single recursion**, while recursion that contains multiple self-references is known as **multiple recursion**. Standard examples of single recursion include list traversal, such as in a linear search, or computing the factorial function, while standard examples of multiple recursion include [tree traversal](./Tree_traversal), such as in a depth-first search.

 

Single recursion is often much more efficient than multiple recursion, and can generally be replaced by an iterative computation, running in linear time and requiring constant space. Multiple recursion, by contrast, may require exponential time and space, and is more fundamentally recursive, not being able to be replaced by iteration without an explicit stack.

 

Multiple recursion can sometimes be converted to single recursion (and, if desired, thence to iteration). For example, while computing the Fibonacci sequence naively entails multiple iteration, as each value requires two previous values, it can be computed by single recursion by passing two successive values as parameters.

 

### Indirect recursion

 Main article: [Mutual recursion](./Mutual_recursion) 

Most basic examples of recursion, and most of the examples presented here, demonstrate ***direct* recursion**, in which a function calls itself.  *Indirect* recursion occurs when a function is called not by itself but by another function that it called (either directly or indirectly). For example, if *f* calls *f,* that is direct recursion, but if *f* calls *g* which calls *f,* then that is indirect recursion of *f.* Chains of three or more functions are possible; for example, function 1 calls function 2, function 2 calls function 3, and function 3 calls function 1 again.

 

Indirect recursion is also called [mutual recursion](./Mutual_recursion), which is a more symmetric term, though this is simply a difference of emphasis, not a different notion. That is, if *f* calls *g* and then *g* calls *f,* which in turn calls *g* again, from the point of view of *f* alone, *f* is indirectly recursing, while from the point of view of *g* alone, it is indirectly recursing, while from the point of view of both, *f* and *g* are mutually recursing on each other. Similarly a set of three or more functions that call each other can be called a set of mutually recursive functions.

 

### Anonymous recursion

 Main article: [Anonymous recursion](./Anonymous_recursion) 

Recursion is usually done by explicitly calling a function by name. However, recursion can also be done via implicitly calling a function based on the current context, which is particularly useful for [anonymous functions](./Anonymous_function), and is known as [anonymous recursion](./Anonymous_recursion).

 

### Structural versus generative recursion

 See also: [Structural recursion](./Structural_recursion) 

Some authors classify recursion as either "structural" or "generative".  The distinction is related to where a recursive procedure gets the data that it works on, and how it processes that data:

 

[Functions that consume structured data] typically decompose their arguments into their immediate structural components and then process those components. If one of the immediate components belongs to the same class of data as the input, the function is recursive. For that reason, we refer to these functions as (STRUCTURALLY) RECURSIVE  FUNCTIONS.

— Felleisen, Findler, Flatt, and Krishnaurthi, *[How to Design Programs](./How_to_Design_Programs)*, 2001[[14]](./Recursion_(computer_science)#cite_note-Felleisen_HtDP_2001-14)

 

Thus, the defining characteristic of a structurally recursive function is that the argument to each recursive call is the content of a field of the original input.  Structural recursion includes nearly all tree traversals, including XML processing, binary tree creation and search, etc. By considering the algebraic structure of the natural numbers (that is, a natural number is either zero or the successor of a natural number), functions such as factorial may also be regarded as structural recursion.

 

**Generative recursion** is the alternative:

 

Many well-known recursive algorithms generate an entirely new piece of data from the given data and recur on it.  [*HtDP* (*How to Design Programs*)](./How_to_Design_Programs) refers to this kind as generative recursion.  Examples of generative recursion include: [gcd](./Euclidean_algorithm), [quicksort](./Quicksort), [binary search](./Binary_search), [mergesort](./Mergesort), [Newton's method](./Newton's_method), [fractals](./Fractal), and [adaptive integration](./Adaptive_quadrature).

— Matthias Felleisen, *Advanced Functional Programming*, 2002[[15]](./Recursion_(computer_science)#cite_note-Felleisen_2002_108-15)

 

This distinction is important in [proving termination](./Termination_analysis#Termination_proof) of a function.

 
- All structurally recursive functions on finite ([inductively defined](./Recursive_data_type)) data structures can easily be shown to terminate, via [structural induction](./Structural_induction): intuitively, each recursive call receives a smaller piece of input data, until a base case is reached.
- Generatively recursive functions, in contrast, do not necessarily feed smaller input to their recursive calls, so proof of their termination is not necessarily as simple, and avoiding [infinite loops](./Infinite_loops) requires greater care. These generatively recursive functions can often be interpreted as corecursive functions – each step generates the new data, such as successive approximation in Newton's method – and terminating this corecursion requires that the data eventually satisfy some condition, which is not necessarily guaranteed.
- In terms of [loop variants](./Loop_variant), structural recursion is when there is an obvious loop variant, namely size or complexity, which starts off finite and decreases at each recursive step.
- By contrast, generative recursion is when there is not such an obvious loop variant, and termination depends on a function, such as "error of approximation" that does not necessarily decrease to zero, and thus termination is not guaranteed without further analysis.

 

## Implementation issues

 

In actual implementation, rather than a pure recursive function (single check for base case, otherwise recursive step), a number of modifications may be made, for purposes of clarity or efficiency. These include:

 
- Wrapper function (at top)
- Short-circuiting the base case, aka "Arm's-length recursion" (at bottom)
- Hybrid algorithm (at bottom) – switching to a different algorithm once data is small enough

 

On the basis of elegance, wrapper functions are generally approved, while short-circuiting the base case is frowned upon, particularly in academia. Hybrid algorithms are often used for efficiency, to reduce the overhead of recursion in small cases, and arm's-length recursion is a special case of this.

 

### Wrapper function

 

A [wrapper function](./Wrapper_function) is a function that is directly called but does not recurse itself, instead calling a separate auxiliary function which actually does the recursion.

 

Wrapper functions can be used to validate parameters (so the recursive function can skip these), perform initialization (allocate memory, initialize variables), particularly for auxiliary variables such as "level of recursion" or partial computations for [memoization](./Memoization), and handle exceptions and errors. In languages that support [nested functions](./Nested_function), the auxiliary function can be nested inside the wrapper function and use a shared scope. In the absence of nested functions, auxiliary functions are instead a separate function, if possible private (as they are not called directly), and information is shared with the wrapper function by using [pass-by-reference](./Pass-by-reference).

 

### Short-circuiting the base case

 

 
| Ordinary recursion | Short-circuit recursion |
| --- | --- |
| intfac1(intn){if(n<=0){return1;}else{returnfac1(n-1)*n;}} | intfac2(intn){// assert(n >= 2);if(n==2){return2;}else{returnfac2(n-1)*n;}}intfac2wrapper(intn){if(n<=1){return1;}else{returnfac2(n);}} |

 

Short-circuiting the base case, also known as **arm's-length recursion**, consists of checking the base case *before* making a recursive call – i.e., checking if the next call will be the base case, instead of calling and then checking for the base case. Short-circuiting is particularly done for efficiency reasons, to avoid the overhead of a function call that immediately returns. Note that since the base case has already been checked for (immediately before the recursive step), it does not need to be checked for separately, but one does need to use a wrapper function for the case when the overall recursion starts with the base case itself. For example, in the factorial function, properly the base case is 0! = 1, while immediately returning 1 for 1! is a short circuit, and may miss 0; this can be mitigated by a wrapper function. The box shows [C](./C_(programming_language)) code to shortcut factorial cases 0 and 1.

 

Short-circuiting is primarily a concern when many base cases are encountered, such as Null pointers in a tree, which can be linear in the number of function calls, hence significant savings for *O*(*n*) algorithms; this is illustrated below for a depth-first search. Short-circuiting on a tree corresponds to considering a leaf (non-empty node with no children) as the base case, rather than considering an empty node as the base case. If there is only a single base case, such as in computing the factorial, short-circuiting provides only *O*(1) savings.

 

Conceptually, short-circuiting can be considered to either have the same base case and recursive step, checking the base case only before the recursion, or it can be considered to have a different base case (one step removed from standard base case) and a more complex recursive step, namely "check valid then recurse", as in considering leaf nodes rather than Null nodes as base cases in a tree. Because short-circuiting has a more complicated flow, compared with the clear separation of base case and recursive step in standard recursion, it is often considered poor style, particularly in academia.[[16]](./Recursion_(computer_science)#cite_note-16)

 

#### Depth-first search

 

A basic example of short-circuiting is given in [depth-first search](./Depth-first_search) (DFS) of a binary tree; see [binary trees](./Recursion_(computer_science)#Binary_trees) section for standard recursive discussion.

 

The standard recursive algorithm for a DFS is:

 
- base case: If current node is Null, return false
- recursive step: otherwise, check value of current node, return true if match, otherwise recurse on children

 

In short-circuiting, this is instead:

 
- check value of current node, return true if match,
- otherwise, on children, if not Null, then recurse.

 

In terms of the standard steps, this moves the base case check *before* the recursive step. Alternatively, these can be considered a different form of base case and recursive step, respectively. Note that this requires a wrapper function to handle the case when the tree itself is empty (root node is Null).

 

In the case of a [perfect binary tree](./Perfect_binary_tree) of height *h,* there are 2*h*+1−1 nodes and 2*h*+1 Null pointers as children (2 for each of the 2*h* leaves), so short-circuiting cuts the number of function calls in half in the worst case.

 

In C, the standard recursive algorithm may be implemented as:

 
```
bool tree_contains(struct BinaryTree* node, int i) {
     if (!node) {
         return false; // base case
     } else if (node->data == i) {
         return true;
     } else {
         return tree_contains(node->left, i)
             || tree_contains(node->right, i);
     }
}

```
 

The short-circuited algorithm may be implemented as:

 
```
#include <assert.h>

// Wrapper function to handle empty tree
bool tree_contains(struct BinaryTree* node, int i) {
    if (!node) {
        return false; // empty tree
    } else {
        return tree_contains_aux(node, i); // call auxiliary function
    }
}

// Assumes node != NULL
bool tree_contains_aux(struct BinaryTree* node, int i) {
    assert(node);
    if (node->data == i) {
        return true; // found
    } else {
        // recurse
        return (node->left && tree_contains_aux(node->left, i))
            || (node->right && tree_contains_aux(node->right, i));
    }
}

```
 

Note the use of [short-circuit evaluation](./Short-circuit_evaluation) of the Boolean && (AND) operators, so that the recursive call is made only if the node is valid (non-Null). Note that while the first term in the AND is a pointer to a node, the second term is a Boolean, so the overall expression evaluates to a Boolean. This is a common idiom in recursive short-circuiting. This is in addition to the short-circuit evaluation of the Boolean || (OR) operator, to only check the right child if the left child fails. In fact, the entire [control flow](./Control_flow) of these functions can be replaced with a single Boolean expression in a return statement, but legibility suffers at no benefit to efficiency.

 

### Hybrid algorithm

 

Recursive algorithms are often inefficient for small data, due to the overhead of repeated function calls and returns. For this reason efficient implementations of recursive algorithms often start with the recursive algorithm, but then switch to a different algorithm when the input becomes small. An important example is [merge sort](./Merge_sort), which is often implemented by switching to the non-recursive [insertion sort](./Insertion_sort) when the data is sufficiently small, as in the [tiled merge sort](./Tiled_merge_sort). Hybrid recursive algorithms can often be further refined, as in [Timsort](./Timsort), derived from a hybrid merge sort/insertion sort.

 

## Recursion versus iteration

 

Recursion and [iteration](./Iteration) are equally expressive: recursion can be replaced by iteration with an explicit [call stack](./Call_stack), while iteration can be replaced with [tail recursion](./Tail_recursion). Which approach is preferable depends on the problem under consideration and the language used. In [imperative programming](./Imperative_programming), iteration is preferred, particularly for simple recursion, as it avoids the overhead of function calls and call stack management, but recursion is generally used for multiple recursion. By contrast, in [functional languages](./Functional_languages) recursion is preferred, with tail recursion optimization leading to little overhead. Implementing an algorithm using iteration may not be easily achievable.

 

Compare the templates to compute xn defined by xn = f(n, xn-1) from xbase:

 
| functionrecursive(n)ifn == basereturnxbaseelsereturnf(n, recursive(n - 1)) | functioniterative(n)
    x = xbasefori = base + 1 to n
        x = f(i, x)returnx |
| --- | --- |

 

For an imperative language the overhead is to define the function, and for a functional language the overhead is to define the accumulator variable x.

 

For example, a [factorial](./Factorial) function may be implemented iteratively in [C](./C_(programming_language)) by assigning to a loop index variable and accumulator variable, rather than by passing arguments and returning values by recursion:

 
```
unsigned int factorial(unsigned int n) {
    unsigned int product = 1; // empty product is 1
    while (n > 0) {
        product *= n;
        --n;
    }
    return product;
}

```
 

### Expressive power

 

Most [programming languages](./Programming_language) in use today allow the direct specification of recursive functions and procedures. When such a function is called, the program's [runtime environment](./Runtime_environment) keeps track of the various [instances](./Instance_(computer_science)) of the function (often using a [call stack](./Call_stack), although other methods may be used). Every recursive function can be transformed into an iterative function by replacing recursive calls with [iterative control constructs](./Control_flow) and simulating the call stack with a [stack](./Stack_(data_structure)) explicitly managed by the program.[[17]](./Recursion_(computer_science)#cite_note-17)[[18]](./Recursion_(computer_science)#cite_note-18)

 

Conversely, all iterative functions and procedures that can be evaluated by a computer (see [Turing completeness](./Turing_completeness)) can be expressed in terms of recursive functions; iterative control constructs such as [while loops](./While_loop) and [for loops](./For_loop) are routinely rewritten in recursive form in [functional languages](./Functional_language).[[19]](./Recursion_(computer_science)#cite_note-19)[[20]](./Recursion_(computer_science)#cite_note-20) However, in practice this rewriting depends on [tail call elimination](./Tail_call_elimination), which is not a feature of all languages. [C](./C_(programming_language)), [Java](./Java_(programming_language)), and [Python](./Python_(programming_language)) are notable mainstream languages in which all function calls, including [tail calls](./Tail_call), may cause stack allocation that would not occur with the use of looping constructs; in these languages, a working iterative program rewritten in recursive form may [overflow the call stack](./Stack_overflow), although tail call elimination may be a feature that is not covered by a language's specification, and different implementations of the same language may differ in tail call elimination capabilities.

 

### Performance issues

 

In languages (such as [C](./C_(programming_language)) and [Java](./Java_(programming_language))) that favor iterative looping constructs, there is usually significant time and space cost associated with recursive programs, due to the overhead required to manage the stack and the relative slowness of function calls; in [functional languages](./Functional_languages), a function call (particularly a [tail call](./Tail_call)) is typically a very fast operation, and the difference is usually less noticeable.

 

As a concrete example, the difference in performance between recursive and iterative implementations of the "factorial" example above depends highly on the [compiler](./Compiler) used. In languages where looping constructs are preferred, the iterative version may be as much as several [orders of magnitude](./Orders_of_magnitude) faster than the recursive one. In functional languages, the overall time difference of the two implementations may be negligible; in fact, the cost of multiplying the larger numbers first rather than the smaller numbers (which the iterative version given here happens to do) may overwhelm any time saved by choosing iteration.

 

### Stack space

 

In some programming languages, the maximum size of the [call stack](./Call_stack) is much less than the space available in the [heap](./Heap_(programming)), and recursive algorithms tend to require more stack space than iterative algorithms. Consequently, these languages sometimes place a limit on the depth of recursion to avoid [stack overflows](./Stack_buffer_overflow); [Python](./Python_(programming_language)) is one such language.[[21]](./Recursion_(computer_science)#cite_note-21) Note the caveat below regarding the special case of [tail recursion](./Tail_recursion).

 

### Vulnerability

 

Because recursive algorithms can be subject to stack overflows, they may be vulnerable to [pathological](./Pathological_(mathematics)) or [malicious](./Malware) input.[[22]](./Recursion_(computer_science)#cite_note-22) Some malware specifically targets a program's call stack and takes advantage of the stack's inherently recursive nature.[[23]](./Recursion_(computer_science)#cite_note-23) Even in the absence of malware, a stack overflow caused by unbounded recursion can be fatal to the program, and [exception handling](./Exception_handling) [logic](./Logic) may not prevent the corresponding [process](./Process_(computing)) from being [terminated](./Process_state#Terminated).[[24]](./Recursion_(computer_science)#cite_note-24)

 

### Multiply recursive problems

 

Multiply recursive problems are inherently recursive, because of prior state they need to track. One example is [tree traversal](./Tree_traversal) as in [depth-first search](./Depth-first_search); though both recursive and iterative methods are used,[[25]](./Recursion_(computer_science)#cite_note-25) they contrast with list traversal and linear search in a list, which is a singly recursive and thus naturally iterative method. Other examples include [divide-and-conquer algorithms](./Divide-and-conquer_algorithm) such as [Quicksort](./Quicksort), and functions such as the [Ackermann function](./Ackermann_function). All of these algorithms can be implemented iteratively with the help of an explicit [stack](./Stack_(data_structure)), but the programmer effort involved in managing the stack, and the complexity of the resulting program, arguably outweigh any advantages of the iterative solution.

 

### Refactoring recursion

 

Recursive algorithms can be replaced with non-recursive counterparts.[[26]](./Recursion_(computer_science)#cite_note-26) One method for replacing recursive algorithms is to simulate them using [heap memory](./Memory_management) in place of [stack memory](./Stack_memory).[[27]](./Recursion_(computer_science)#cite_note-27) An alternative is to develop a replacement algorithm entirely based on non-recursive methods, which can be challenging.[[28]](./Recursion_(computer_science)#cite_note-28) For example, recursive algorithms for [matching wildcards](./Matching_wildcards), such as [Rich Salz](./Rich_Salz)' [wildmat](./Wildmat) algorithm,[[29]](./Recursion_(computer_science)#cite_note-29) were once typical. Non-recursive algorithms for the same purpose, such as the [Krauss matching wildcards algorithm](./Krauss_matching_wildcards_algorithm), have been developed to avoid the drawbacks of recursion[[30]](./Recursion_(computer_science)#cite_note-30) and have improved only gradually based on techniques such as collecting [tests](./Software_testing) and [profiling](./Profiling_(computer_programming)) performance.[[31]](./Recursion_(computer_science)#cite_note-31)

 

## Tail-recursive functions

 

Tail-recursive functions are functions in which all recursive calls are [tail calls](./Tail_call) and hence do not build up any deferred operations. For example, the gcd function (shown again below) is tail-recursive.  In contrast, the factorial function (also below) is **not** tail-recursive; because its recursive call is not in tail position, it builds up deferred multiplication operations that must be performed after the final recursive call completes.  With a [compiler](./Compiler) or [interpreter](./Interpreter_(computing)) that treats tail-recursive calls as [jumps](./Goto) rather than function calls, a tail-recursive function such as gcd will execute using constant space.  Thus the program is essentially iterative, equivalent to using imperative language control structures like the "for" and "while" loops.

 
| Tail recursion: | Augmenting recursion: |
| --- | --- |
| /*** @brief computes GCD using Euclidean algorithm* @param x an int* @param y an int, such that x >= y >= 0* @returns the GCD of x and y*/intgcd(intx,inty){if(y==0){returnx;}else{returngcd(y,x%y);}} | /*** @brief computes the factorial of a non-negative integer* @param n an int* @returns the factorial of n*/unsignedintfactorial(unsignedintn){if(n==0){return1;}else{returnn*factorial(n-1);}} |

 

The significance of tail recursion is that when making a tail-recursive call (or any tail call), the caller's return position need not be saved on the [call stack](./Call_stack); when the recursive call returns, it will branch directly on the previously saved return position. Therefore, in languages that recognize this property of tail calls, tail recursion saves both space and time.

 

## Order of execution

 

Consider these two functions:

 

### Function 1

 
```
#include <stdio.h>

void recursiveFunction(int num) {
    printf("%d\n", num);
    if (num < 4) {
        recursiveFunction(num + 1);
    }
}

```
 

[![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a7/Recursive1.svg/500px-Recursive1.svg.png)](./File:Recursive1.svg)

 

### Function 2

 
```
#include <stdio.h>

void recursiveFunction(int num) {
    if (num < 4) {
        recursiveFunction(num + 1);
    }
    printf("%d\n", num);
}

```
 

[![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fe/Recursive2.svg/500px-Recursive2.svg.png)](./File:Recursive2.svg)

 

The output of function 2 is that of function 1 with the lines swapped.

 

In the case of a function calling itself only once, instructions placed before the recursive call are executed once per recursion before any of the instructions placed after the recursive call. The latter are executed repeatedly after the maximum recursion has been reached.

 

Also note that the *order* of the print statements is reversed, which is due to the way the functions and statements are stored on the [call stack](./Call_stack).

 

## Recursive procedures

 

### Factorial

 

A classic example of a recursive procedure is the function used to calculate the [factorial](./Factorial) of a [natural number](./Natural_number):

     fact ⁡ ⁡  ( n ) =   {    1     if    n = 0     n ⋅ ⋅  fact ⁡ ⁡  ( n − −  1 )     if    n > 0         {\displaystyle \operatorname {fact} (n)={\begin{cases}1&{\mbox{if }}n=0\\n\cdot \operatorname {fact} (n-1)&{\mbox{if }}n>0\\\end{cases}}}  ![{\displaystyle \operatorname {fact} (n)={\begin{cases}1&{\mbox{if }}n=0\\n\cdot \operatorname {fact} (n-1)&{\mbox{if }}n>0\\\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbc0a05bb5402570afdac251df1661194639d397) 
| Pseudocode(recursive): |
| --- |
| functionfactorial is:input: integernsuch thatn>= 0output: [n× (n-1) × (n-2) × ... × 1]1. ifnis 0,return1
    2. otherwise,return[n× factorial(n-1) ]endfactorial |

 

The function can also be written as a [recurrence relation](./Recurrence_relation):

      b  n   = n  b  n − −  1     {\displaystyle b_{n}=nb_{n-1}}  ![{\displaystyle b_{n}=nb_{n-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e489a1211cc945f05a486d09506fdb827febc23)      b  0   = 1   {\displaystyle b_{0}=1}  ![{\displaystyle b_{0}=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e891f2e26ca623a2f9bbd0bfef87a4dfac0a20f) 

This evaluation of the recurrence relation demonstrates the computation that would be performed in evaluating the pseudocode above:

 
| Computing the recurrence relation for n = 4: |
| --- |
| b4= 4 × b3= 4 × (3 × b2)
             = 4 × (3 × (2 × b1))
             = 4 × (3 × (2 × (1 × b0)))
             = 4 × (3 × (2 × (1 × 1)))
             = 4 × (3 × (2 × 1))
             = 4 × (3 × 2)
             = 4 × 6
             = 24 |

 

This factorial function can also be described without using recursion by making use of the typical looping constructs found in imperative programming languages:

 
| Pseudocode (iterative): |
| --- |
| functionfactorial is:input: integernsuch thatn>= 0output: [n× (n-1) × (n-2) × ... × 1]1.createnew variable calledrunning_totalwith a value of 12.beginloop
          1. ifnis 0,exitloop
          2.setrunning_totalto (running_total×n)
          3.decrementn4.repeatloop3.returnrunning_totalendfactorial |

 

The imperative code above is equivalent to this mathematical definition using an accumulator variable t:

         fact ⁡ ⁡  ( n )    =  f a c  t  a c c    ⁡ ⁡  ( n , 1 )      f a c  t  a c c    ⁡ ⁡  ( n , t )    =   {    t     if    n = 0      f a c  t  a c c    ⁡ ⁡  ( n − −  1 , n t )     if    n > 0             {\displaystyle {\begin{aligned}\operatorname {fact} (n)&=\operatorname {fact_{acc}} (n,1)\\\operatorname {fact_{acc}} (n,t)&={\begin{cases}t&{\mbox{if }}n=0\\\operatorname {fact_{acc}} (n-1,nt)&{\mbox{if }}n>0\\\end{cases}}\end{aligned}}}  ![{\displaystyle {\begin{aligned}\operatorname {fact} (n)&=\operatorname {fact_{acc}} (n,1)\\\operatorname {fact_{acc}} (n,t)&={\begin{cases}t&{\mbox{if }}n=0\\\operatorname {fact_{acc}} (n-1,nt)&{\mbox{if }}n>0\\\end{cases}}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5425ae0a78b654f37c41e3e6acfd0b2e59c61b5e) 

The definition above translates straightforwardly to [functional programming languages](./Functional_programming_language) such as [Scheme](./Scheme_(programming_language)); this is an example of iteration implemented recursively.

 

### Greatest common divisor

 

The [Euclidean algorithm](./Euclidean_algorithm), which computes the [greatest common divisor](./Greatest_common_divisor) of two integers, can be written recursively.

 

*Function definition*:

     gcd ( x , y ) =   {    x     if    y = 0     gcd ( y , remainder ⁡ ⁡  ( x , y ) )     if    y > 0         {\displaystyle \gcd(x,y)={\begin{cases}x&{\mbox{if }}y=0\\\gcd(y,\operatorname {remainder} (x,y))&{\mbox{if }}y>0\\\end{cases}}}  ![{\displaystyle \gcd(x,y)={\begin{cases}x&{\mbox{if }}y=0\\\gcd(y,\operatorname {remainder} (x,y))&{\mbox{if }}y>0\\\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/66b3eae7c177b5a9738c42383c664048d8f239a0) 
| Pseudocode(recursive): |
| --- |
| functiongcd is:input: integerx, integerysuch thatx> 0 andy>= 01. ifyis 0,returnx2. otherwise,return[ gcd(y, (remainder ofx/y) ) ]endgcd |

 

[Recurrence relation](./Recurrence_relation) for greatest common divisor, where     x % %  y   {\displaystyle x\%y}  ![{\displaystyle x\%y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f1b133f8669e2ad9a88369d2e490d6efb60956dc) expresses the [remainder](./Remainder) of     x  /  y   {\displaystyle x/y}  ![{\displaystyle x/y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c9f79732fa39115855a4cf9b64d2a63971a41046):

     gcd ( x , y ) = gcd ( y , x % %  y )   {\displaystyle \gcd(x,y)=\gcd(y,x\%y)}  ![{\displaystyle \gcd(x,y)=\gcd(y,x\%y)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1fe0cd9431d08127f9c1110d4b973207e186ff1) if     y ≠ ≠  0   {\displaystyle y\neq 0}  ![{\displaystyle y\neq 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe09d44abefff1fcada712301b088a303591f9e5)     gcd ( x , 0 ) = x   {\displaystyle \gcd(x,0)=x}  ![{\displaystyle \gcd(x,0)=x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/49261e66420afa094166cac921c0195727307eca) 
| Computing the recurrence relation for x = 27 and y = 9: |
| --- |
| gcd(27, 9)   = gcd(9, 27% 9)
             = gcd(9, 0)
             = 9 |
| Computing the recurrence relation for x = 111 and y = 259: |
| gcd(111, 259)   = gcd(259, 111% 259)
                = gcd(259, 111)
                = gcd(111, 259% 111)
                = gcd(111, 37)
                = gcd(37, 111% 37)
                = gcd(37, 0)
                = 37 |

 

The recursive program above is [tail-recursive](./Tail-recursive); it is equivalent to an iterative algorithm, and the computation shown above shows the steps of evaluation that would be performed by a language that eliminates tail calls.  Below is a version of the same algorithm using explicit iteration, suitable for a language that does not eliminate tail calls.  By maintaining its state entirely in the variables *x* and *y* and using a looping construct, the program avoids making recursive calls and growing the call stack.

 
| Pseudocode (iterative): |
| --- |
| functiongcd is:input: integerx, integerysuch thatx>=yandy>= 01.createnew variable calledremainder2.beginloop
          1. ifyis zero,exitloop
          2.setremainderto the remainder of x/y
          3.setx to y
          4.sety toremainder5.repeatloop3.returnxendgcd |

 

The iterative algorithm requires a temporary variable, and even given knowledge of the Euclidean algorithm it is more difficult to understand the process by simple inspection, although the two algorithms are very similar in their steps.

 

### Towers of Hanoi

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/07/Tower_of_Hanoi.jpeg/250px-Tower_of_Hanoi.jpeg)](./File:Tower_of_Hanoi.jpeg)Towers of Hanoi Main article: [Towers of Hanoi](./Towers_of_Hanoi) 

The Towers of Hanoi is a mathematical puzzle whose solution illustrates recursion.[[32]](./Recursion_(computer_science)#cite_note-32)[[33]](./Recursion_(computer_science)#cite_note-33) There are three pegs which can hold stacks of disks of different diameters. A larger disk may never be stacked on top of a smaller. Starting with *n* disks on one peg, they must be moved to another peg one at a time. What is the smallest number of steps to move the stack?

 

*Function definition*:

     hanoi ⁡ ⁡  ( n ) =   {    1     if    n = 1     2 ⋅ ⋅  hanoi ⁡ ⁡  ( n − −  1 ) + 1     if    n > 1         {\displaystyle \operatorname {hanoi} (n)={\begin{cases}1&{\mbox{if }}n=1\\2\cdot \operatorname {hanoi} (n-1)+1&{\mbox{if }}n>1\\\end{cases}}}  ![{\displaystyle \operatorname {hanoi} (n)={\begin{cases}1&{\mbox{if }}n=1\\2\cdot \operatorname {hanoi} (n-1)+1&{\mbox{if }}n>1\\\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/52078a04ec62c4a55887e2cd9011acb238c34452) 

*Recurrence relation for hanoi*:

      h  n   = 2  h  n − −  1   + 1   {\displaystyle h_{n}=2h_{n-1}+1}  ![{\displaystyle h_{n}=2h_{n-1}+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ef787d90c11406d902ea1602275c1aa3f7562a15)      h  1   = 1   {\displaystyle h_{1}=1}  ![{\displaystyle h_{1}=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/083d0eaf2fe9466f7e1ec69edf7f202b8c0b8851) 
| Computing the recurrence relation for n = 4: |
| --- |
| hanoi(4)     = 2×hanoi(3) + 1
             = 2×(2×hanoi(2) + 1) + 1
             = 2×(2×(2×hanoi(1) + 1) + 1) + 1
             = 2×(2×(2×1 + 1) + 1) + 1
             = 2×(2×(3) + 1) + 1
             = 2×(7) + 1
             = 15 |

 

 

Example implementations:

 
| Pseudocode(recursive): |
| --- |
| functionhanoi is:input: integern, such thatn>=11.ifn is 1then return12.return[2 * [callhanoi(n-1)] + 1]endhanoi |

 

Although not all recursive functions have an explicit solution, the Tower of Hanoi sequence can be reduced to an explicit formula.[[34]](./Recursion_(computer_science)#cite_note-34)

 
| An explicit formula for Towers of Hanoi: |
| --- |
| h1= 1   = 21- 1
h2= 3   = 22- 1
h3= 7   = 23- 1
h4= 15  = 24- 1
h5= 31  = 25- 1
h6= 63  = 26- 1
h7= 127 = 27- 1In general:
hn= 2n- 1, for all n >= 1 |

 

### Binary search

 

The [binary search](./Binary_search) algorithm is a method of searching a [sorted array](./Sorted_array) for a single element by cutting the array in half with each recursive pass.  The trick is to pick a midpoint near the center of the array, compare the data at that point with the data being searched and then responding to one of three possible conditions: the data is found at the midpoint, the data at the midpoint is greater than the data being searched for, or the data at the midpoint is less than the data being searched for.

 

Recursion is used in this algorithm because with each pass a new array is created by cutting the old one in half.  The binary search procedure is then called recursively, this time on the new (and smaller) array.  Typically the array's size is adjusted by manipulating a beginning and ending index.  The algorithm exhibits a logarithmic order of growth because it essentially divides the problem domain in half with each pass.

 

Example implementation of binary search in C:

 
```
/**
 * @brief Call binary_search with proper initial conditions.
 * @param data an array of integers SORTED in ASCENDING order
 * @param target the integer to search for
 * @param count the total number of elements in the array
 * @returns result of binary_search
 */
int search(int data[], int target, int count) {
    // Start = 0 (beginning index)
    // End = count - 1 (top index)
    return binary_search(data, target, 0, count - 1);
}

/**
 * @brief Binary Search Algorithm.
 * @param data an array of integers SORTED in ASCENDING order
 * @param target the integer to search for
 * @param start the minimum array index
 * @param end the maximum array index
 * @returns position of the integer toFind within array data, -1 if not found
 */
int binary_search(int data[], int target, int start, int end) {
    //Get the midpoint.
    int mid = start + (end - start) / 2; //Integer division

    if (start > end) {
        return -1; // Stop condition (base case)
    } else if (data[mid] == target) {
        return mid; // Found, return index
    } else if (data[mid] > target) {
        // Data is greater than target, search lower half
        return binary_search(data, target, start, mid - 1);
    } else {
        // Data is less than target, search upper half
        return binary_search(data, target, mid + 1, end);
    }
}

```
 

## Recursive data structures (structural recursion)

 Main article: [Recursive data type](./Recursive_data_type) 

An important application of recursion in computer science is in defining dynamic data structures such as [lists](./List_(abstract_data_type)) and [trees](./Tree_(data_structure)).  Recursive data structures can dynamically grow to a theoretically infinite size in response to runtime requirements; in contrast, the size of a static array must be set at compile time.

  

"Recursive algorithms are particularly appropriate when the underlying problem or the data to be treated are defined in recursive terms."[[35]](./Recursion_(computer_science)#cite_note-35)

  

The examples in this section illustrate what is known as "structural recursion".  This term refers to the fact that the recursive procedures are acting on data that is defined recursively.

  

As long as a programmer derives the template from a data definition, functions employ structural recursion. That is, the recursions in a function's body consume some immediate piece of a given compound value.[[15]](./Recursion_(computer_science)#cite_note-Felleisen_2002_108-15)

  

### Linked lists

 Main article: [Linked list](./Linked_list) 

Below is a C definition of a linked list node structure.  Notice especially how the node is defined in terms of itself.  The "next" element of `LinkedList` is a pointer to another linked list, effectively creating a list type.

 
```
struct LinkedList {
    int data; // some integer data
    struct LinkedList* next; // pointer to another node of the linked list
};

```
 

Because the *struct node* data structure is defined recursively, procedures that operate on it can be implemented naturally as recursive procedures.  The *list_print* procedure defined below walks down the list until the list is empty (i.e., the list pointer has a value of NULL).  For each node it prints the data element (an integer).  In the C implementation, the list remains unchanged by the *list_print* procedure.

 
```
void list_print(struct LinkedList* list) {
    // base case
    if (list) {
        printf("%d ", list->data);  // print integer data followed by a space
        list_print(list->next); // recursive call on the next node
    }
}

```
 

### Binary trees

 Main article: [Binary tree](./Binary_tree) 

Below is a simple definition for a binary tree node.  Like the node for linked lists, it is defined in terms of itself, recursively.  There are two self-referential pointers: left (pointing to the left sub-tree) and right (pointing to the right sub-tree).

 
```
struct BinaryTree {
    int data; // some integer data
    struct BinaryTree* left; // pointer to the left subtree
    struct BinaryTree* right; // pointer to the right subtree
};

```
 

Operations on the tree can be implemented using recursion.  Note that because there are two self-referencing pointers (left and right), tree operations may require two recursive calls:

 
```
// Test if tree_node contains i; return 1 if so, 0 if not.
int tree_contains(struct BinaryTree* node, int i) {
    if (!node) {
        return 0; // base case
    } else if (node->data == i) {
        return 1;
    } else {
        return tree_contains(node->left, i) || tree_contains(node->right, i);
    }
}

```
 

At most two recursive calls will be made for any given call to *tree_contains* as defined above.

 
```
// Inorder traversal:
void tree_print(struct BinaryTree* node) {
    // base case
    if (node) { 
        tree_print(node->left); // go left
        printf("%d ", node->data); // print the integer followed by a space
        tree_print(node->right); // go right
    }
}

```
 

The above example illustrates an [in-order traversal](./Tree_traversal) of the binary tree.  A [Binary search tree](./Binary_search_tree) is a special case of the binary tree where the data elements of each node are in order.

 

### Filesystem traversal

 

Since the number of files in a [filesystem](./Filesystem) may vary, [recursion](./Recursion) is the only practical way to traverse and thus enumerate its contents.  Traversing a filesystem is very similar to that of [tree traversal](./Tree_traversal), therefore the concepts behind tree traversal are applicable to traversing a filesystem.  More specifically, the code below would be an example of a [preorder traversal](./Preorder_traversal) of a filesystem.

 
```
package org.wikipedia.examples;

import java.io.File;

public class Example {
	/**
	 * Obtains the filesystem roots
	 * Proceeds with the recursive filesystem traversal
	 */
	private static void traverse() {
		File[] fs = File.listRoots();
		for (int i = 0; i < fs.length; i++) {
			System.out.println(fs[i]);
			if (fs[i].isDirectory() && fs[i].canRead()) {
				rtraverse(fs[i]);
			}
		}
	}

	/**
	 * Recursively traverse a given directory
	 *
	 * @param fd indicates the starting point of traversal
	 */
	private static void rtraverse(File fd) {
		File[] fss = fd.listFiles();

		for (int i = 0; i < fss.length; i++) {
			System.out.println(fss[i]);
			if (fss[i].isDirectory() && fss[i].canRead()) {
				rtraverse(fss[i]);
			}
		}
	}

	public static void main(String[] args) {
		traverse();
	}
}

```
 

This code is both recursion and [iteration](./Iteration) - the files and directories are iterated, and each directory is opened recursively.

 

The "rtraverse" method is an example of direct recursion, whilst the "traverse" method is a wrapper function.

 

The "base case" scenario is that there will always be a fixed number of files and/or directories in a given filesystem.

 

## Time-efficiency of recursive algorithms

 

The [time efficiency](./Time_complexity) of recursive algorithms can be expressed in a [recurrence relation](./Recurrence_relation) of [Big O notation](./Big_O_notation).  They can (usually) then be simplified into a single Big-O term.

 

### Shortcut rule (master theorem)

 Main article: [Master theorem (analysis of algorithms)](./Master_theorem_(analysis_of_algorithms)) 

If the time-complexity of the function is in the form
    T ( n ) = a ⋅ ⋅  T ( n  /  b ) + f ( n )   {\displaystyle T(n)=a\cdot T(n/b)+f(n)}  ![{\displaystyle T(n)=a\cdot T(n/b)+f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f45874129c69809cfa55de221ef2666051a676d7)

 

Then the Big O of the time-complexity is thus:

 
- If     f ( n ) = O (  n   log  b   ⁡ ⁡  a − −  ε ε    )   {\displaystyle f(n)=O(n^{\log _{b}a-\varepsilon })}  ![{\displaystyle f(n)=O(n^{\log _{b}a-\varepsilon })}](https://wikimedia.org/api/rest_v1/media/math/render/svg/beb3fb687fc8d3f21479f93c3fc406712c588f3c) for some constant     ε ε  > 0   {\displaystyle \varepsilon >0}  ![{\displaystyle \varepsilon >0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e04ec3670b50384a3ce48aca42e7cc5131a06b12), then     T ( n ) = Θ Θ  (  n   log  b   ⁡ ⁡  a   )   {\displaystyle T(n)=\Theta (n^{\log _{b}a})}  ![{\displaystyle T(n)=\Theta (n^{\log _{b}a})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34ce8e979e6eada403e7044342c39fdf41815f22)
- If     f ( n ) = Θ Θ  (  n   log  b   ⁡ ⁡  a   )   {\displaystyle f(n)=\Theta (n^{\log _{b}a})}  ![{\displaystyle f(n)=\Theta (n^{\log _{b}a})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eee762297fbff4f695d84fd6eb3a9ea87b5647c4), then     T ( n ) = Θ Θ  (  n   log  b   ⁡ ⁡  a   log ⁡ ⁡  n )   {\displaystyle T(n)=\Theta (n^{\log _{b}a}\log n)}  ![{\displaystyle T(n)=\Theta (n^{\log _{b}a}\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b30978415211771d1d567ce2ff24228c73e58271)
- If     f ( n ) = Ω Ω  (  n   log  b   ⁡ ⁡  a + ε ε    )   {\displaystyle f(n)=\Omega (n^{\log _{b}a+\varepsilon })}  ![{\displaystyle f(n)=\Omega (n^{\log _{b}a+\varepsilon })}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffc4a9b70dcc15fdb9942fa09d2d04a833b34204) for some constant     ε ε  > 0   {\displaystyle \varepsilon >0}  ![{\displaystyle \varepsilon >0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e04ec3670b50384a3ce48aca42e7cc5131a06b12), and if     a ⋅ ⋅  f ( n  /  b ) ≤ ≤  c ⋅ ⋅  f ( n )   {\displaystyle a\cdot f(n/b)\leq c\cdot f(n)}  ![{\displaystyle a\cdot f(n/b)\leq c\cdot f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5876b27e26e38632de6c5ea675420b643517437) for some constant *c* < 1 and all sufficiently large n, then     T ( n ) = Θ Θ  ( f ( n ) )   {\displaystyle T(n)=\Theta (f(n))}  ![{\displaystyle T(n)=\Theta (f(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e3f2ea15b66701b4ed7351155df63020b3ad5dc5)

 

where a represents the number of recursive calls at each level of recursion, b represents by what factor smaller the input is for the next level of recursion (i.e. the number of pieces you divide the problem into), and *f*(*n*) represents the work that the function does independently of any recursion (e.g. partitioning, recombining) at each level of recursion.

 

## Recursion in Logic Programming

 

In the procedural interpretation of [logic programs](./Logic_programming), clauses (or rules) of the form `A :- B` are treated as procedures, which reduce goals of the form `A` to subgoals of the form `B`.
For example, the [Prolog](./Prolog) clauses:

 
```
path(X,Y) :- arc(X,Y).
path(X,Y) :- arc(X,Z), path(Z,Y).

```
 

define a  procedure, which can be used to search for a path from  *X* to  *Y*, either by finding a direct arc from *X* to *Y*, or by finding an arc from *X* to *Z*, and then searching recursively for a path from *Z* to *Y*. Prolog executes the procedure by reasoning top-down (or [backwards](./Backward_chaining)) and searching the space of possible paths depth-first, one branch at a time. If it tries the second clause, and finitely fails to find a path from *Z* to *Y*, it backtracks and tries to find an arc from *X* to another node, and then searches for a path from that other node to *Y*.

 

However, in the logical reading of logic programs, clauses are understood [declaratively](./Declarative_program) as universally quantified conditionals. For example, the recursive clause of the path-finding procedure is understood as [representing the knowledge](./Knowledge_representation_and_reasoning) that, for every *X*, *Y* and *Z*, if there is an arc from *X* to *Z* and a path from *Z* to *Y* then there is a path from *X* to *Y*. In symbolic form:

     ∀ ∀  X , Y , Z ( a r c ( X , Z ) ∧ ∧  p a t h ( Z , Y ) → →  p a t h ( X , Y ) ) .   {\displaystyle \forall X,Y,Z(arc(X,Z)\land path(Z,Y)\rightarrow path(X,Y)).}  ![{\displaystyle \forall X,Y,Z(arc(X,Z)\land path(Z,Y)\rightarrow path(X,Y)).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a5d7004a9fae850a949eed90114ec03a2f3c0366) 

The logical reading frees the reader from needing to know how the clause is used to solve problems. The clause can be used top-down, as in Prolog, to reduce problems to subproblems. Or it can be used bottom-up (or [forwards](./Forward_chaining)), as in [Datalog](./Datalog), to derive conclusions from conditions. This [separation of concerns](./Separation_of_concerns) is a form of [abstraction](./Abstraction_(computer_science)), which separates declarative knowledge from problem solving methods (see [Algorithm#Algorithm = Logic + Control](./Algorithm#Algorithm_=_Logic_+_Control)).[[36]](./Recursion_(computer_science)#cite_note-36)

 

## Infinite recursion

 

A common mistake among programmers is not providing a way to exit a recursive function, often by omitting or incorrectly checking the base case, letting it run (at least theoretically) infinitely by endlessly calling itself recursively. This is called *infinite recursion*, and the program will never terminate. In practice, this typically exhausts the available [stack](./Stack_(abstract_data_type)) space. In most programming environments, a program with infinite recursion will not really run forever. Eventually, something will break and the program will report an error.[[37]](./Recursion_(computer_science)#cite_note-37) However, if [tail call optimization](./Tail_call_optimization) is used then the recursive calls may be optimized into an infinite loop that can run forever.

 

Below is a Java code that would use infinite recursion:

 
```
public class InfiniteRecursion {
    static void recursive() {
        // Recursive function with no way out
        recursive();
    }
    
    public static void main(String[] args) {
        recursive(); // Executes the recursive function upon runtime
    }
}

```
 

Running this code will result in a [stack overflow](./Stack_overflow) error.

 

## See also

 
- [Recursion](./Recursion) (in general)
- [Functional programming](./Functional_programming)
- [Computational problem](./Computational_problem)
- [Hierarchical and recursive queries in SQL](./Hierarchical_and_recursive_queries_in_SQL)
- [Kleene–Rosser paradox](./Kleene–Rosser_paradox)
- [Open recursion](./Open_recursion)
- [Sierpiński curve](./Sierpiński_curve)
- [McCarthy 91 function](./McCarthy_91_function)
- [μ-recursive functions](./Μ-recursive_function)
- [Primitive recursive functions](./Primitive_recursive_function)
- [Tak (function)](./Tak_(function))
- [Logic programming](./Logic_programming)

 

## Notes

  
1. [↑](./Recursion_(computer_science)#cite_ref-1) [Graham, Ronald](./Ronald_Graham); [Knuth, Donald](./Donald_Knuth); Patashnik, Oren (1990). ["1: Recurrent Problems"](http://www-cs-faculty.stanford.edu/~knuth/gkp.html). *Concrete Mathematics*. Addison-Wesley. [ISBN](./ISBN_(identifier)) [0-201-55802-5](./Special:BookSources/0-201-55802-5).
2. [↑](./Recursion_(computer_science)#cite_ref-2) Kuhail, Mohammad A.; Negreiros, Joao; Seffah, Ahmed (2021). "Teaching Recursive Thinking using Unplugged Activities". *World Transactions on Engineering and Technology Education*. **19** (2): 169–175.
3. [↑](./Recursion_(computer_science)#cite_ref-3) Epp, Susanna (1995). [*Discrete Mathematics with Applications*](https://archive.org/details/discretemathema000epps/page/427) (2nd ed.). PWS Publishing Company. p. [427](https://archive.org/details/discretemathema000epps/page/427). [ISBN](./ISBN_(identifier)) [978-0-53494446-9](./Special:BookSources/978-0-53494446-9).
4. [↑](./Recursion_(computer_science)#cite_ref-4) [Wirth, Niklaus](./Niklaus_Wirth) (1976). [*Algorithms + Data Structures = Programs*](https://archive.org/details/algorithmsdatast00wirt/page/126). [Prentice-Hall](./Prentice-Hall). p. [126](https://archive.org/details/algorithmsdatast00wirt/page/126). [ISBN](./ISBN_(identifier)) [978-0-13022418-7](./Special:BookSources/978-0-13022418-7).
5. [↑](./Recursion_(computer_science)#cite_ref-5) ["Functional Programming | Clojure for the Brave and True"](https://www.braveclojure.com/functional-programming/#Recursion_Instead_of_for_while). *www.braveclojure.com*. Retrieved 2020-10-21.
6. [1](./Recursion_(computer_science)#cite_ref-auto5_6-0) [2](./Recursion_(computer_science)#cite_ref-auto5_6-1) [3](./Recursion_(computer_science)#cite_ref-auto5_6-2) Soare, Robert I. (1996). "Computability and Recursion". *Bulletin of Symbolic Logic*. **2** (3): 284–321. [doi](./Doi_(identifier)):[10.2307/420992](https://doi.org/10.2307%2F420992). [JSTOR](./JSTOR_(identifier)) [420992](https://www.jstor.org/stable/420992).
7. [1](./Recursion_(computer_science)#cite_ref-auto3_7-0) [2](./Recursion_(computer_science)#cite_ref-auto3_7-1) [3](./Recursion_(computer_science)#cite_ref-auto3_7-2) [4](./Recursion_(computer_science)#cite_ref-auto3_7-3) [5](./Recursion_(computer_science)#cite_ref-auto3_7-4) [6](./Recursion_(computer_science)#cite_ref-auto3_7-5) Daylight, Edgar G. (2010). The Advent of Recursion in Programming, 1950s–1960s (Report). Preprint Series PP-2010-04. University of Amsterdam, Institute for Logic, Language and Computation.
8. [1](./Recursion_(computer_science)#cite_ref-auto_8-0) [2](./Recursion_(computer_science)#cite_ref-auto_8-1) [3](./Recursion_(computer_science)#cite_ref-auto_8-2) McCarthy, John (1960). "Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I". *Communications of the ACM*. **3** (4): 184–195. [doi](./Doi_(identifier)):[10.1145/367177.367199](https://doi.org/10.1145%2F367177.367199).
9. [1](./Recursion_(computer_science)#cite_ref-auto4_9-0) [2](./Recursion_(computer_science)#cite_ref-auto4_9-1) Naur, Peter; John Backus; John McCarthy (1960). "Report on the Algorithmic Language ALGOL 60". *Communications of the ACM*. **3** (5): 299–314. [doi](./Doi_(identifier)):[10.1145/367236.367262](https://doi.org/10.1145%2F367236.367262).
10. [↑](./Recursion_(computer_science)#cite_ref-10) Kong, Qingkai; Siauw, Timmy; Bayen, Alexandre M. (2021). "Recursion". *Python Programming and Numerical Methods*. pp. 105–120. [doi](./Doi_(identifier)):[10.1016/B978-0-12-819549-9.00015-4](https://doi.org/10.1016%2FB978-0-12-819549-9.00015-4). [ISBN](./ISBN_(identifier)) [978-0-12-819549-9](./Special:BookSources/978-0-12-819549-9).
11. [1](./Recursion_(computer_science)#cite_ref-:0_11-0) [2](./Recursion_(computer_science)#cite_ref-:0_11-1) [3](./Recursion_(computer_science)#cite_ref-:0_11-2) Sweigart, Al (2022). *The Recursive Book of Recursion: Ace the Coding Interview with Python and JavaScript*. No Starch Press. [ISBN](./ISBN_(identifier)) [978-1-7185-0202-4](./Special:BookSources/978-1-7185-0202-4).[*[page needed](./Wikipedia:Citing_sources)*]
12. [↑](./Recursion_(computer_science)#cite_ref-12) Hopcroft, John; Tarjan, Robert (June 1973). "Algorithm 447: efficient algorithms for graph manipulation". *Communications of the ACM*. **16** (6): 372–378. [doi](./Doi_(identifier)):[10.1145/362248.362272](https://doi.org/10.1145%2F362248.362272).
13. [↑](./Recursion_(computer_science)#cite_ref-13) Bron, C. (May 1972). "Algorithm 426: Merge sort algorithm [M1]". *Communications of the ACM*. **15** (5): 357–358. [doi](./Doi_(identifier)):[10.1145/355602.361317](https://doi.org/10.1145%2F355602.361317).
14. [↑](./Recursion_(computer_science)#cite_ref-Felleisen_HtDP_2001_14-0) [Felleisen et al. 2001](./Recursion_(computer_science)#CITEREFFelleisenFindlerFlattKrishnamurthi2001), [art V "Generative Recursion](http://www.htdp.org/2003-09-26/Book/curriculum-Z-H-31.html) 
15. [1](./Recursion_(computer_science)#cite_ref-Felleisen_2002_108_15-0) [2](./Recursion_(computer_science)#cite_ref-Felleisen_2002_108_15-1) Felleisen, Matthias (2002). ["Developing Interactive Web Programs"](https://books.google.com/books?id=Y3GqCAAAQBAJ&pg=PA108). In Jeuring, Johan (ed.). [*Advanced Functional Programming: 4th International School*](ftp://nozdr.ru/biblio/kolxo3/Cs/CsLn/Advanced%20Functional%20Programming%204%20conf.,%20AFP%202002%20(LNCS2638,%20Springer,%202003)(ISBN%203540401326)(O)(222s).pdf#page=109) (PDF). Springer. p. 108. [ISBN](./ISBN_(identifier)) [9783540448334](./Special:BookSources/9783540448334). 
16. [↑](./Recursion_(computer_science)#cite_ref-16) Mongan, John; Giguère, Eric; Kindler, Noah (2013). [*Programming Interviews Exposed: Secrets to Landing Your Next Job*](https://archive.org/details/programminginter00mong_658) (3rd ed.). [Wiley](./Wiley_(publisher)). p. [115](https://archive.org/details/programminginter00mong_658/page/n148). [ISBN](./ISBN_(identifier)) [978-1-118-26136-1](./Special:BookSources/978-1-118-26136-1).
17. [↑](./Recursion_(computer_science)#cite_ref-17) Hetland, Magnus Lie (2010), [*Python Algorithms: Mastering Basic Algorithms in the Python Language*](https://books.google.com/books?id=4cytGpIPYsAC&pg=PA79), Apress, p. 79, [ISBN](./ISBN_(identifier)) [9781430232384](./Special:BookSources/9781430232384).
18. [↑](./Recursion_(computer_science)#cite_ref-18) Drozdek, Adam (2012), [*Data Structures and Algorithms in C++*](https://books.google.com/books?id=PRgLAAAAQBAJ&pg=PA197) (4th ed.), Cengage Learning, p. 197, [ISBN](./ISBN_(identifier)) [9781285415017](./Special:BookSources/9781285415017).
19. [↑](./Recursion_(computer_science)#cite_ref-19) Shivers, Olin. ["The Anatomy of a Loop - A story of scope and control"](http://www.ccs.neu.edu/home/shivers/papers/loop.pdf) (PDF). Georgia Institute of Technology. Retrieved 2012-09-03.
20. [↑](./Recursion_(computer_science)#cite_ref-20) Lambda the Ultimate. ["The Anatomy of a Loop"](http://lambda-the-ultimate.org/node/1014). Lambda the Ultimate. Retrieved 2012-09-03.
21. [↑](./Recursion_(computer_science)#cite_ref-21) ["27.1. sys — System-specific parameters and functions — Python v2.7.3 documentation"](https://docs.python.org/library/sys.html). Docs.python.org. Retrieved 2012-09-03.
22. [↑](./Recursion_(computer_science)#cite_ref-22) Krauss, Kirk J. (2014). ["Matching Wildcards: An Empirical Way to Tame an Algorithm"](http://www.drdobbs.com/architecture-and-design/matching-wildcards-an-empirical-way-to-t/240169123). *[Dr. Dobb's Journal](./Dr._Dobb's_Journal)*.
23. [↑](./Recursion_(computer_science)#cite_ref-23) Mueller, Oliver (2012). ["Anatomy of a Stack Smashing Attack and How GCC Prevents It"](http://www.drdobbs.com/security/anatomy-of-a-stack-smashing-attack-and-h/240001832). *[Dr. Dobb's Journal](./Dr._Dobb's_Journal)*.
24. [↑](./Recursion_(computer_science)#cite_ref-24) ["StackOverflowException Class"](https://msdn.microsoft.com/en-us/library/system.stackoverflowexception(v=vs.110).aspx). *.NET Framework Class Library*. [Microsoft Developer Network](./Microsoft_Developer_Network). 2018.
25. [↑](./Recursion_(computer_science)#cite_ref-25) ["Depth First Search (DFS): Iterative and Recursive Implementation"](http://www.techiedelight.com/depth-first-search/). Techie Delight. 2018.
26. [↑](./Recursion_(computer_science)#cite_ref-26) Mitrovic, Ivan. ["Replace Recursion with Iteration"](https://www.refactoring.com/catalog/replaceRecursionWithIteration.html). [ThoughtWorks](./ThoughtWorks).
27. [↑](./Recursion_(computer_science)#cite_ref-27) La, Woong Gyu (2015). ["How to replace recursive functions using stack and while-loop to avoid the stack-overflow"](https://www.codeproject.com/Articles/418776/How-to-replace-recursive-functions-using-stack-and). CodeProject.
28. [↑](./Recursion_(computer_science)#cite_ref-28) Moertel, Tom (2013). ["Tricks of the trade: Recursion to Iteration, Part 2: Eliminating Recursion with the Time-Traveling Secret Feature Trick"](http://blog.moertel.com/posts/2013-05-14-recursive-to-iterative-2.html).
29. [↑](./Recursion_(computer_science)#cite_ref-29) Salz, Rich (1991). ["wildmat.c"](https://github.com/trevor/transmission/blob/master/libtransmission/wildmat.c). [GitHub](./GitHub).
30. [↑](./Recursion_(computer_science)#cite_ref-30) Krauss, Kirk J. (2008). ["Matching Wildcards: An Algorithm"](http://www.drdobbs.com/architecture-and-design/matching-wildcards-an-algorithm/210200888). *[Dr. Dobb's Journal](./Dr._Dobb's_Journal)*.
31. [↑](./Recursion_(computer_science)#cite_ref-31) Krauss, Kirk J. (2018). ["Matching Wildcards: An Improved Algorithm for Big Data"](http://www.developforperformance.com/MatchingWildcards_AnImprovedAlgorithmForBigData.html). Develop for Performance.
32. [↑](./Recursion_(computer_science)#cite_ref-32) [Graham, Knuth & Patashnik 1990](./Recursion_(computer_science)#CITEREFGrahamKnuthPatashnik1990), §1.1: The Tower of Hanoi
33. [↑](./Recursion_(computer_science)#cite_ref-33) [Epp 1995](./Recursion_(computer_science)#CITEREFEpp1995), pp. 427–430: The Tower of Hanoi
34. [↑](./Recursion_(computer_science)#cite_ref-34) [Epp 1995](./Recursion_(computer_science)#CITEREFEpp1995), pp. 447–448: An Explicit Formula for the Tower of Hanoi Sequence
35. [↑](./Recursion_(computer_science)#cite_ref-35) [Wirth 1976](./Recursion_(computer_science)#CITEREFWirth1976), p. 127
36. [↑](./Recursion_(computer_science)#cite_ref-36) [Russell, Stuart J.](./Stuart_J._Russell); [Norvig, Peter.](./Peter_Norvig) (2021). *[Artificial Intelligence: A Modern Approach §9.3, §9.4](./Artificial_Intelligence:_A_Modern_Approach)* (4th ed.). Hoboken: Pearson. [ISBN](./ISBN_(identifier)) [978-0134610993](./Special:BookSources/978-0134610993). [LCCN](./LCCN_(identifier)) [20190474](https://lccn.loc.gov/20190474).
37. [↑](./Recursion_(computer_science)#cite_ref-37) ["4.8. Infinite Recursion — How to Think Like a Computer Scientist - C++"](https://runestone.academy/ns/books/published/thinkcpp/Chapter4/InfiniteRecursion.html).

 

## References

  
- [Barron, David William](./David_W._Barron) (1968) [1967].  Written at Cambridge, UK. [Gill, Stanley](./Stanley_Gill) (ed.). *Recursive techniques in programming*. Macdonald Computer Monographs (1 ed.). London, UK: [Macdonald & Co. (Publishers) Ltd.](./Macdonald_&_Co._(Publishers)_Ltd.) [SBN](./SBN_(identifier)) [356-02201-3](./Special:BookSources/0-356-02201-3). (viii+64 pages)
- Felleisen, Matthias; Findler, Robert B.; Flatt, Matthew; Krishnamurthi, Shriram (2001). [*How To Design Programs: An Introduction to Computing and Programming*](http://www.htdp.org/2003-09-26/Book/). [MIT Press](./MIT_Press). [ISBN](./ISBN_(identifier)) [0262062186](./Special:BookSources/0262062186).
- Rubio-Sanchez, Manuel (2017). [*Introduction to Recursive Programming*](https://books.google.com/books?id=9pY4DwAAQBAJ&pg=PA1). [CRC Press](./CRC_Press). [ISBN](./ISBN_(identifier)) [978-1-351-64717-5](./Special:BookSources/978-1-351-64717-5).
- Pevac, Irena (2016). *Practicing Recursion in Java*. CreateSpace Independent. [ISBN](./ISBN_(identifier)) [978-1-5327-1227-2](./Special:BookSources/978-1-5327-1227-2).
- Roberts, Eric (2005). [*Thinking Recursively with Java*](https://archive.org/details/thinkingrecursiv00robe_0). [Wiley](./Wiley_(publisher)). [ISBN](./ISBN_(identifier)) [978-0-47170146-0](./Special:BookSources/978-0-47170146-0).
- Rohl, Jeffrey S. (1984). [*Recursion Via Pascal*](https://books.google.com/books?id=yCk2mWy9inMC). [Cambridge University Press](./Cambridge_University_Press). [ISBN](./ISBN_(identifier)) [978-0-521-26934-6](./Special:BookSources/978-0-521-26934-6).
- Helman, Paul; Veroff, Robert. [*Walls and Mirrors*](./Walls_and_Mirrors).
- [Abelson, Harold](./Harold_Abelson); [Sussman, Gerald Jay](./Gerald_Jay_Sussman); Sussman, Julie (1996). [*Structure and Interpretation of Computer Programs*](./Structure_and_Interpretation_of_Computer_Programs) (2nd ed.). [MIT Press](./MIT_Press). [ISBN](./ISBN_(identifier)) [0-262-51087-1](./Special:BookSources/0-262-51087-1).
- [Dijkstra, Edsger W.](./Edsger_W._Dijkstra) (1960). "Recursive Programming". *Numerische Mathematik*. **2** (1): 312–318. [doi](./Doi_(identifier)):[10.1007/BF01386232](https://doi.org/10.1007%2FBF01386232). [S2CID](./S2CID_(identifier)) [127891023](https://api.semanticscholar.org/CorpusID:127891023).
- McCarthy, John (1960). "Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I". *Communications of the ACM*. **3** (4): 184–195. [doi](./Doi_(identifier)):[10.1145/367177.367199](https://doi.org/10.1145%2F367177.367199).
- Naur, Peter; John Backus; John McCarthy (1960). "Report on the Algorithmic Language ALGOL 60". *Communications of the ACM*. **3** (5): 299–314. [doi](./Doi_(identifier)):[10.1145/367236.367262](https://doi.org/10.1145%2F367236.367262).
- Hoare, C. A. R. (1961). "Quicksort". *Communications of the ACM*. **4** (7): 321–322. [doi](./Doi_(identifier)):[10.1145/366622.366644](https://doi.org/10.1145%2F366622.366644).
- Soare, Robert I. (1996). "Computability and Recursion". *Bulletin of Symbolic Logic*. **2** (3): 284–321. [doi](./Doi_(identifier)):[10.2307/420992](https://doi.org/10.2307%2F420992). [JSTOR](./JSTOR_(identifier)) [420992](https://www.jstor.org/stable/420992).
- Daylight, Edgar G. (2010). The Advent of Recursion in Programming, 1950s–1960s (Report). Preprint Series PP-2010-04. University of Amsterdam, Institute for Logic, Language and Computation.
- Endres, Madeline; Westley Weimer; Amir Kamil (2021). "An Analysis of Iterative and Recursive Problem Performance". *Proceedings of the 52nd ACM Technical Symposium on Computer Science Education (SIGCSE '21)*. Association for Computing Machinery. [doi](./Doi_(identifier)):[10.1145/3408877.3432391](https://doi.org/10.1145%2F3408877.3432391).
- Cormen, Thomas H.; Charles E. Leiserson; Ronald L. Rivest; Clifford Stein (2009). *Introduction to Algorithms* (3rd ed.). MIT Press. [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8).

  
| vteProgramming paradigms |
| --- |
| Imperative | StructuredJackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested functionObject-orientedClass-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax | Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function | Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function |
| Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Declarative | FunctionalRecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonadDataflowFlow-basedReactive(Functional reactive)SignalsStreamsSynchronousLogicAbductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQueryDomain-specificlanguage(DSL)Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual | Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad | Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous | Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery | Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad |
| Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous |
| Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery |
| Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Concurrent,parallel | Actor-basedAutomatic mutual exclusionChoreographic programmingConcurrent logic(Concurrent constraint logic)Concurrent OOMacroprogrammingMultitier programmingOrganic computingParallel programming modelsPartitioned global address spaceProcess-orientedRelativistic programmingService-orientedStructured concurrency |
| Metaprogramming | Attribute-orientedAutomatic(Inductive)DynamicExtensibleGenericHomoiconicityInteractiveMacro(Hygienic)Metalinguistic abstractionMulti-stageProgram synthesis(Bayesian,by demonstration,by example,vibe coding)ReflectiveSelf-modifying codeSymbolicTemplate |
| Separationof concerns | AspectsComponentsData-drivenData-orientedEvent-drivenFeaturesLiterateRolesSubjects |
| Comparisons/Lists | Comparison(multi-paradigm,object-oriented,functional),List(OO,by type) |

 
| vteData structuresandalgorithms |
| --- |
| Data structures | ArrayAssociative arrayBinary search treeFenwick treeGraphHash tableHeapLinked listQueueSegment treeStackStringTreeTrie |
| Algorithms andalgorithmic paradigms | BacktrackingBinary searchBreadth-first searchBrute-force searchDepth-first searchDivide and conquerDynamic programmingGraph traversalFoldGreedyHash functionMinimaxOnlineRandomizedRecursionRoot-findingSortingStreamingSweep lineString-searchingTopological sorting |
| List of data structuresList of algorithms |