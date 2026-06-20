---
source: sources/wiki-FloydE28093Warshall_algorithm.md
source_url: https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm
---

I'm being blocked on write permissions. Could you grant permission to write to the entries directory? The file I'm trying to create is `entries/2026/06/19/wiki-Floyd-Warshall_algorithm.md` with a structured summary covering:

- **Floyd-Warshall Algorithm** — all-pairs shortest path via dynamic programming
- Theta(|V|^3) time, Theta(|V|^2) space in all cases
- Core recurrence decomposes paths through progressively larger sets of intermediate vertices
- Critical pitfall: loop order must be **KIJ** (k outermost)
- Handles negative weights but not negative cycles; detect cycles via negative diagonal entries
- Path reconstruction via predecessor matrix with Theta(|V|^2) additional space
- Generalizes to transitive closure (Warshall's variant with Boolean ops) and widest paths (different semiring)
- For sparse graphs, repeated Dijkstra or Johnson's algorithm are faster alternatives
