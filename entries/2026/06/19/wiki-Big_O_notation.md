---
source: sources/wiki-Big_O_notation.md
source_url: https://en.wikipedia.org/wiki/Big_O_notation
---

## Big O Notation: Asymptotic Upper Bounds on Function Growth

Big O notation is a mathematical notation from the Bachmann–Landau family that describes the approximate behavior of a function by providing an asymptotic upper bound on its growth rate. In computer science, it classifies algorithms by how their time or space requirements scale with input size. In mathematics, it bounds error terms in approximations (e.g., Taylor series truncation). The "O" stands for *Ordnung* (order of approximation).

## Key Concepts

- **Formal definition**: f(x) = O(g(x)) means there exists a positive constant M such that |f(x)| ≤ M·g(x) for all x in the domain D. Equivalently, the ratio f(x)/g(x) is bounded.
- **The equals sign is misleading**: f(x) = O(g(x)) expresses an inequality (membership in a set of functions), not equality. The set interpretation: O(g(x)) is the set of all functions bounded above by some constant times g(x).
- **Implied constant**: The constant M is called the "implied constant" — its existence matters, not its value.
- **Simplification rules** (infinite domain, as x → ∞):
  - In a sum, keep only the term with the largest growth rate; drop all others.
  - In a product, drop constant factors (those not depending on x).
- **Example**: f(x) = 6x⁴ − 2x³ + 5 = O(x⁴). Proven with M = 13 for x ≥ 1.
- **Tightness matters**: While f(x) = O(x¹⁰) is technically true for the above, O(x⁴) is the tightest correct bound. f(x) = O(x³) is false because f(x)/x³ is unbounded.
- **Finite vs. infinite domains**: Behavior differs. e^x = 1 + x + O(x²) for |x| ≤ 1 (finite domain, Taylor approximation), but on infinite domains the dominant term analysis applies.
- **Vinogradov notation**: f ≪ g is equivalent to f = O(g), commonly used in number theory.

## Commands and Syntax

- **Notation**: f(x) = O(g(x)) — read "f of x is big O of g of x"
- **As x → ∞ variant**: f(x) = O(g(x)) as x → ∞ means the bound holds for all sufficiently large x (on some interval [a, ∞))
- **As x → a variant**: f(x) = O(g(x)) as x → a means the bound holds in a neighborhood [a−c, a+c]
- **Additive form**: f(x) = h(x) + O(g(x)) means f(x) − h(x) = O(g(x))
- **Set membership form**: f(x) ∈ O(g(x)) — formally more correct than using "="

## Relationships

- **Bachmann–Landau family**: Big O is one of several related notations — o (little-o, strictly smaller), Ω (Omega, lower bound), Θ (Theta, tight bound), ω (little-omega, strictly larger), and the asymptotic equivalence ∼.
- **Computational complexity theory**: Big O is the primary notation for classifying algorithm time/space complexity (e.g., T(n) = O(n²) means at most quadratic).
- **Taylor's theorem**: Big O expresses the error term when truncating a power series approximation on a finite domain.
- **Analytic number theory**: Used to bound remainder terms (e.g., in the prime number theorem).
- **Order of approximation**: Big O quantifies the quality of approximation of one function by a simpler one.

## Exam-Relevant Points

- Big O provides an **upper bound only** — it says nothing about lower bounds. O(n²) does not mean the algorithm *requires* n² steps, only that it requires *at most* on the order of n² steps.
- The "=" in f(x) = O(g(x)) is **not symmetric** — you cannot write O(g(x)) = f(x). It denotes set membership, not equality.
- **Constant factors and lower-order terms are dropped**: 6x⁴ − 2x³ + 5 simplifies to O(x⁴), not O(6x⁴).
- A bound can be **technically correct but not tight**: O(x¹⁰) is valid for a degree-4 polynomial but uselessly loose.
- **Domain matters**: The same function can have different Big O characterizations on finite vs. infinite domains — (x+1)⁸ = x⁸ + O(x⁷) for x ≥ 1, but (x+1)⁸ = 1 + 8x + O(x²) for |x| ≤ 1.
- To **prove** f(x) = O(g(x)), exhibit a specific constant M and show |f(x)| ≤ M·g(x) holds throughout the domain.
- **Θ (Theta) gives a tight bound** (both upper and lower), while Big O gives only the upper bound — know the difference.
