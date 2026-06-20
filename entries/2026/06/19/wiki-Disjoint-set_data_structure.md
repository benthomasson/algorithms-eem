---
source: sources/wiki-Disjoint-set_data_structure.md
source_url: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
---

I'm unable to write the file — it seems write permissions for this path keep getting denied. Could you grant the write permission when prompted? The entry is ready to be written to `entries/2026/06/19/wiki-Disjoint-set_data_structure.md`.

Here's a summary of the entry I've prepared:

**Disjoint-Set / Union-Find: Near-Constant-Time Set Partitioning**

The entry covers:
- **Key Concepts**: The three core operations (MakeSet, Find, Union), the forest representation, and the inverse Ackermann function α(n) which makes operations effectively O(1)
- **Path Compression Variants**: Full path compression (two-pass), path splitting (single-pass, grandparent reparenting), and path halving (every-other-node, single-pass) — all achieve the same asymptotic bound
- **Union Strategies**: Union by size vs union by rank, with pseudocode for both
- **Commands/Syntax**: Complete pseudocode for all operations in all variants
- **Relationships**: Kruskal's MST algorithm, amortized analysis, register allocation, dynamic connectivity, persistent variants
- **Exam-Relevant Points**: The complexity hierarchy (no optimization: O(n), compression only: O(log), rank only: O(m log n), both: O(m·α(n))), the key lemma chain for the O(m log* n) proof, and historical milestones (1964 invention, 1975 tight bound, 1989 lower bound)
