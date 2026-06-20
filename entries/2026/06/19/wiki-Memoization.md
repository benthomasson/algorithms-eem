---
source: sources/wiki-Memoization.md
source_url: https://en.wikipedia.org/wiki/Memoization
---

## Memoization: Caching Function Results for Speed Optimization

Memoization is an optimization technique that speeds up programs by storing the results of expensive pure function calls and returning the cached result when the same inputs recur. It is a space–time tradeoff — trading increased memory usage for reduced computation time — typically implemented with a hash table. Coined by Donald Michie in 1968, the term derives from Latin *memorandum*. Memoization is a runtime optimization (unlike compile-time techniques such as strength reduction) and is machine-independent and cross-platform.

## Key Concepts

- **Prerequisite: referential transparency** — a function can only be memoized if it is pure (calling it has the same effect as substituting its return value). No side effects allowed.
- **Cache population is transparent** — unlike a precomputed lookup table, a memoized function populates its cache on the fly as new inputs are encountered.
- **Cumulative benefit** — a memoized function becomes more time-efficient the more often it is called, since more results are cached over time.
- **Space–time tradeoff** — runtime decreases at the cost of increased memory consumption. Both dimensions are measured by computational complexity.
- **Associative array storage** — results are keyed by the function's input arguments in a hash map or similar structure.
- **Replacement policy** — the cache may be fixed-size with a replacement algorithm, or unbounded, depending on the use case.
- **Singleton pattern as extreme case** — creating an object on first call and returning the cached instance thereafter is a degenerate form of memoization.
- **Tabling** — in logic programming languages, memoization is called tabling.

## Commands and Syntax

**Non-memoized factorial (pseudocode):**
```
function factorial(n)
    if n is 0 then return 1
    else return factorial(n - 1) * n
```

**Memoized factorial with explicit lookup table:**
```
function factorial(n)
    if n is 0 then return 1
    else if n is in lookup-table then return lookup-table[n]
    else
        x = factorial(n - 1) * n
        store x in lookup-table at slot n
        return x
```

**Generic automatic memoization wrapper (first-class functions):**
```
function memoized-call(F)
    if F has no attached values then
        allocate associative array values; attach to F
    if F.values[arguments] is empty then
        F.values[arguments] = F(arguments)
    return F.values[arguments]
```
Usage: `memoized-call(factorial)(n)`

**Decorator/functor factory pattern (closure-based):**
```
function construct-memoized-functor(F)
    let memoized-version(arguments) be
        if self.values[arguments] is empty then
            self.values[arguments] = F(arguments)
        return self.values[arguments]
    return memoized-version

factorial = construct-memoized-functor(factorial)
```

## Relationships

- **Dynamic programming** — memoization is the top-down counterpart to bottom-up DP; both cache subproblem results to avoid redundant computation.
- **Caching** — memoization is a specific form of caching scoped to function return values keyed by arguments.
- **Hash tables** — the standard implementation substrate for the memo cache.
- **Lazy evaluation** — shares the concept of deferring computation; thunks in call-by-name functional languages are memoized to avoid recomputation.
- **Parsing algorithms** — memoization converts exponential backtracking parsers into polynomial-time ones (Norvig 1991). Packrat parsing (Ford 2002) uses memoization for linear-time PEG parsing. Connects to Earley and CYK algorithms.
- **Decorator pattern / Flyweight pattern** — memoization wrappers are often implemented as decorators; the Flyweight pattern uses similar instance-sharing.
- **Partial evaluation** — a related compile-time optimization technique.
- **Materialized views** — the database analogue of memoization (precomputed query results).

## Exam-Relevant Points

- Memoization **requires referential transparency** (pure functions only) — this is the most commonly tested constraint.
- It is a **runtime** optimization, not a compile-time one — distinguish from strength reduction.
- The factorial example demonstrates how memoization turns O(n) repeated calls into O(1) lookups: calling `factorial(5)` then `factorial(7)` requires only 2 new recursive calls (for 7 and 6).
- **Automatic memoization** can be applied externally to any referentially transparent function using higher-order functions, closures, or decorators — no modification of the original function needed.
- In parsing, memoization reduces exponential backtracking to **polynomial time**: O(n^4) for left-recursive grammars, O(n^3) for non-left-recursive grammars (Frost, Hafiz, Callaghan 2007).
- **Packrat parsing** (Ford 2002) uses memoization to guarantee **linear-time** parsing of PEGs.
- Selective memoization (Acar et al. 2003) addresses the overhead problem: not every rule benefits from caching, and indiscriminate memoization can **slow down** a parser.
- Memoization is **not only for speed** — it is also used for delaying constraint resolution in parsing (Johnson & Dörre 1995) and handling mutual recursion.
- In functional programming compilers, **thunks** are memoized to avoid recomputing arguments under call-by-name evaluation.
