# Algorithms & Data Structures EEM

An External Epistemic Memory (EEM) knowledge base covering algorithms and data structures for software engineering, built entirely from Wikipedia sources.

## What is an EEM?

An EEM is a structured knowledge base built by an LLM that serves as external memory. It uses a reason maintenance system to track beliefs, their justifications, and dependency chains. Beliefs can be derived from other beliefs, reviewed for validity, and retracted with automatic cascade propagation.

## Knowledge Base Stats

- **52 Wikipedia sources** covering arrays, linked lists, trees, hash tables, heaps, graphs, tries, union-find, sorting, searching, graph traversal, shortest path, dynamic programming, divide-and-conquer, greedy algorithms, backtracking, and more
- **598 beliefs** in the network (302 premises + 296 derived)
- **Depth 15** justification chains
- **3 cycles** of derive-review-repair with automated quality control

## Exam Matrix Results

50-question practice exam across 3 models and 3 conditions:

| Model | Control (no beliefs) | With Beliefs | Agentic (tool-calling) |
|-------|---------------------|--------------|----------------------|
| **Opus** | 50/50 (100%) | 50/50 (100%) | 50/50 (100%) |
| **Sonnet** | 49/50 (98%) | 49/50 (98%) | 47/50 (94%) |
| **Haiku** | 48/50 (96%) | 49/50 (98%) | 49/50 (98%) |

Key findings:
- Beliefs improve Haiku's score from 96% to 98%, rescuing questions on radix sort linearity conditions and trie vs BST string comparison cost
- Agentic mode (tool-calling into the belief database) also improves Haiku to 98%
- Opus scores 100% across all conditions — these questions don't differentiate at that tier
- Recurring weakness across non-Opus models: Big-O formal definition (missing the n0 threshold in the asymptotic bound)

## Structure

| Path | Purpose |
|------|---------|
| `sources/` | 52 Wikipedia source documents (markdown) |
| `entries/` | Summarized entries from sources |
| `reasons.db` | SQLite belief database with dependency tracking |
| `beliefs.md` | Human-readable export of all beliefs |
| `network.json` | Full network export (beliefs + justifications) |
| `questions/` | Practice exam questions |
| `results/` | Exam results by model and condition |

## Tools

Built with [expert-agent-builder](https://github.com/benthomasson/expert-agent-builder) and the `reasons` CLI for reason maintenance.

```bash
# Query the knowledge base
reasons search "binary search tree"
reasons explain belief-id
reasons show belief-id

# Run the exam
expert-build exam questions/algorithms-ds-practice.md

# Run the full matrix
expert-build exam-matrix questions/algorithms-ds-practice.md --agentic
```
