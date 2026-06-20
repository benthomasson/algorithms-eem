---
source: sources/wiki-Stack_abstract_data_type.md
source_url: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
---

## Stack (Abstract Data Type)

A stack is an abstract data type that implements a last-in, first-out (LIFO) collection of elements. It supports two principal operations — **push** (add to top) and **pop** (remove from top) — and is one of the most fundamental data structures in computer science, with applications ranging from expression parsing to memory management to graph algorithms.

## Key Concepts

- **LIFO ordering**: the most recently added element is the first removed
- **Top**: the single end of the stack where push and pop occur; the other end (bottom) is fixed
- **Push**: adds an element to the top; increments the top pointer
- **Pop**: removes and returns the top element; decrements the top pointer
- **Peek / Top-of-stack**: observes the top element without modifying the stack (non-essential — decomposable into pop + push)
- **Stack overflow**: push when the stack has reached its bounded capacity
- **Stack underflow**: pop or peek when the stack is empty
- **Two canonical implementations**: array-based (bounded, O(1) ops, contiguous memory) and linked-list-based (unbounded until memory exhaustion, pointer overhead per element)
- **Dynamic array implementation**: amortized O(1) push and pop, grows/shrinks as needed
- **Hardware stacks**: many CPU architectures have dedicated stack pointer registers and push/pop instructions (x86, Z80, 6502, PDP-11, 68000)
- **Stack machines**: architectures where arithmetic/logic operations implicitly use a stack for operands (Burroughs Large Systems, x87 FPU, Forth-based microprocessors)
- Additional hardware operations: **Duplicate**, **Swap/Exchange**, **Rotate/Roll** (left and right variants)

## Commands and Syntax

**Array-based implementation (pseudocode):**
```
structure stack:
    maxsize : integer
    top : integer
    items : array of item

procedure push(stk, x):
    if stk.top = stk.maxsize: report overflow
    else: stk.items[stk.top] ← x; stk.top ← stk.top + 1

procedure pop(stk):
    if stk.top = 0: report underflow
    else: stk.top ← stk.top − 1; return stk.items[stk.top]
```

**Linked-list-based implementation (pseudocode):**
```
structure frame:
    data : item
    next : frame or nil

procedure push(stk, x):
    newhead ← new frame
    newhead.data ← x; newhead.next ← stk.head
    stk.head ← newhead; stk.size ← stk.size + 1

procedure pop(stk):
    if stk.head = nil: report underflow
    else: r ← stk.head.data; stk.head ← stk.head.next
          stk.size ← stk.size - 1; return r
```

**Language-native stack operations:**
- **Common Lisp**: `(push 'item stack)`, `(pop stack)`
- **Java**: `Stack<T>` class with `.push()`, `.pop()`, `.peek()`
- **C++ STL**: `std::stack` adapter; also `push_back()` / `pop_back()` on containers
- **Python/JavaScript/Perl**: push/pop available on standard list/array types

## Relationships

- **Abstract data type** — stack is a specialization of a collection/list ADT, restricted to LIFO access
- **Queue** — the FIFO counterpart; together stacks and queues are the two fundamental sequential access patterns
- **Array / Dynamic array** — common underlying implementation; dynamic arrays give amortized O(1) push/pop
- **Singly linked list** — alternative implementation; push/pop at the head in O(1)
- **Call stack** — runtime use of a stack for subroutine return addresses, local variables, and calling conventions
- **Depth-first search / Backtracking** — algorithms that use a stack (explicit or via recursion) to explore and retreat
- **Reverse Polish notation (RPN)** — expression evaluation model built on a stack
- **Context-free grammars** — parsed using stack-based machines (pushdown automata)
- **Stack-oriented languages** — Forth, PostScript operate directly on language-visible stacks
- **Buffer overflow / Stack smashing** — security vulnerabilities arising from shared data/return-address stacks

## Exam-Relevant Points

- A stack enforces **LIFO** order; a queue enforces **FIFO** — know the distinction cold
- **Array-based**: O(1) push/pop, bounded capacity unless dynamic array is used; dynamic array gives **amortized O(1)**
- **Linked-list-based**: O(1) push/pop (worst case), no overflow (until memory exhaustion), but O(n) extra space for pointers
- **Peek is non-essential** — it can be decomposed into pop followed by push
- Stacks are used in: **expression evaluation** (RPN), **syntax parsing**, **backtracking** (DFS, branch-and-bound), **call stack / memory management**, **Graham scan** (convex hull), **all nearest smaller values**, **nearest-neighbor chain** (hierarchical clustering)
- **Stack overflow** = push on a full bounded stack; **stack underflow** = pop/peek on an empty stack
- The **call stack** stores return addresses and local variables; sharing this with data creates **stack smashing** vulnerabilities (buffer overflow attacks)
- **CISC** processors (x86, Z80, 68000) typically have dedicated stack pointer registers and push/pop instructions; **RISC** processors generally do not
- **Stack machines** use implicit top-of-stack as operands — smaller code footprint but harder to optimize for superscalar execution
- Historical note: Turing used stack concepts ("bury"/"unbury") in **1946**; Samelson and Bauer filed a patent in **1957**; Bauer received the IEEE Computer Pioneer Award for the stack principle in **1988**
