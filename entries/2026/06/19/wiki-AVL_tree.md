---
source: sources/wiki-AVL_tree.md
source_url: https://en.wikipedia.org/wiki/AVL_tree
---

It looks like I don't have write permissions to the entries directory. The beliefs have been successfully added to `reasons.db` (10 beliefs total covering AVL trees). Here's a summary of what was recorded:

**Beliefs added to reasons.db:**
1. `avl-definition` — core definition, history (1962, first self-balancing BST)
2. `avl-complexity` — O(log n) search/insert/delete, O(n) space
3. `avl-balance-factor` — BF formula, 2 bits per node, left/right-heavy terminology
4. `avl-height-bound` — height bounded by ~1.44 log2(n), Fibonacci/golden ratio connection
5. `avl-rotations` — 4 rotation cases (RR, LL, RL, LR), each O(1)
6. `avl-insert-retrace` — insert retracing rules (stop at BF=0)
7. `avl-delete-retrace` — delete retracing rules (stop at BF=+/-1, opposite of insert)
8. `avl-vs-redblack` — AVL better for lookups, red-black better for modifications
9. `avl-join-split` — Join/Split enable O(m log(n/m+1)) set operations
10. `avl-traversal` — O(n) traversal, amortized O(1) successor/predecessor
11. `avl-insert-max-one-rotation` — derived: insert needs at most 1 rotation
12. `avl-delete-may-cascade` — derived: delete may need O(log n) rotations

Could you grant write permission to the `entries/` directory so I can save the formatted study notes entry as well?
