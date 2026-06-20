---
source: sources/wiki-Longest_common_subsequence.md
source_url: https://en.wikipedia.org/wiki/Longest_common_subsequence
---

I'll create the study entry for Longest Common Subsequence.

## Longest Common Subsequence (LCS)

The longest common subsequence problem finds the longest subsequence present in all sequences from a given set. Unlike the longest common *substring*, elements of a subsequence need not be contiguous in the original sequences. LCS is a foundational dynamic programming problem with direct practical applications in diff utilities, version control systems (e.g., Git), computational linguistics, and bioinformatics.

## Key Concepts

- **Subsequence vs. substring**: A subsequence preserves relative order but elements need not be adjacent; a substring requires contiguous positions.
- **LCS is not unique**: Multiple longest common subsequences of the same length may exist. For (ABCD) and (ACBAD), both (ABD) and (ACD) are LCSs of length 3.
- **Optimal substructure**: LCS of prefixes can be built from LCS of shorter prefixes — the hallmark property enabling dynamic programming.
- **Overlapping subproblems**: Higher-level subproblems reuse solutions to lower-level ones, making memoization effective.
- **Two key recurrence properties**:
  - If both sequences end with the same symbol A: LCS(X^A, Y^A) = LCS(X, Y)^A
  - If they end with different symbols A != B: LCS(X^A, Y^B) = longest of {LCS(X^A, Y), LCS(X, Y^B)}
- **Base case**: When either sequence is empty, LCS is the empty string.
- **Traceback**: The DP table stores lengths and directional arrows; actual subsequences are recovered by backtracking from C[m,n] to C[0,0].

## Commands and Syntax

**Computing LCS length** — O(mn) time, O(mn) space:
```
function LCSLength(X[1..m], Y[1..n])
    C = array(0..m, 0..n)
    for i := 0..m: C[i,0] = 0
    for j := 0..n: C[0,j] = 0
    for i := 1..m
        for j := 1..n
            if X[i] = Y[j]
                C[i,j] := C[i-1,j-1] + 1
            else
                C[i,j] := max(C[i,j-1], C[i-1,j])
    return C[m,n]
```

**Reading out one LCS** (backtrack):
```
function backtrack(C, X, Y, i, j)
    if i = 0 or j = 0: return ""
    if X[i] = Y[j]: return backtrack(C, X, Y, i-1, j-1) + X[i]
    if C[i,j-1] > C[i-1,j]: return backtrack(C, X, Y, i, j-1)
    return backtrack(C, X, Y, i-1, j)
```

**Reading out all LCSs** (exponential in worst case):
```
function backtrackAll(C, X, Y, i, j)
    if i = 0 or j = 0: return {""}
    if X[i] = Y[j]: return {Z + X[i] for all Z in backtrackAll(C, X, Y, i-1, j-1)}
    R := {}
    if C[i,j-1] >= C[i-1,j]: R := backtrackAll(C, X, Y, i, j-1)
    if C[i-1,j] >= C[i,j-1]: R := R ∪ backtrackAll(C, X, Y, i-1, j)
    return R
```

**Printing a diff** from the LCS table:
```
function printDiff(C, X, Y, i, j)
    if i >= 0 and j >= 0 and X[i] = Y[j]
        printDiff(C, X, Y, i-1, j-1); print "  " + X[i]
    else if j > 0 and (i = 0 or C[i,j-1] >= C[i-1,j])
        printDiff(C, X, Y, i, j-1); print "+ " + Y[j]
    else if i > 0 and (j = 0 or C[i,j-1] < C[i-1,j])
        printDiff(C, X, Y, i-1, j); print "- " + X[i]
```

## Relationships

- **Edit distance**: When only insertions and deletions are allowed (no substitution), edit distance d'(X,Y) = n + m - 2|LCS(X,Y)|.
- **Shortest common supersequence (SCS)**: |SCS(X,Y)| = n + m - |LCS(X,Y)|. LCS and SCS are duals.
- **Longest common substring**: Related but stricter — requires contiguous elements. Different DP formulation.
- **Diff utilities and version control**: LCS is the algorithmic backbone of `diff`, `patch`, and merge operations in Git and other VCS tools.
- **Dynamic programming**: LCS is a canonical example demonstrating optimal substructure and overlapping subproblems.
- **Sequence alignment in bioinformatics**: LCS generalizes to alignment scoring in DNA/protein sequence comparison.

## Exam-Relevant Points

- **Complexity for two sequences**: O(n * m) time and space using dynamic programming.
- **General case (arbitrary number of sequences)**: NP-hard. For fixed N sequences, DP gives O(N * product of all lengths).
- **Recurrence relation** — three cases: (1) either sequence empty -> empty string; (2) last characters match -> extend LCS of shorter prefixes; (3) last characters differ -> max of two subproblems dropping one character from each sequence.
- **LCS is not necessarily unique**; the number of common subsequences can be exponential — enumerating all LCSs is not polynomial.
- **Space optimization**: Only the current and previous rows of the DP table are needed to compute length (reduces space to O(min(m,n))), but full table is needed for traceback.
- **Practical optimization**: Strip matching prefixes and suffixes before building the DP table — in real-world diffs, beginnings and ends rarely both change.
- **Relationship formulas**: |SCS| = n + m - |LCS| and edit distance (indel only) = n + m - 2|LCS| — know both directions of conversion.
- **Backtracking recovers the actual subsequence** from the length table by following arrows (diagonal = match, up/left = skip); multiple arrows at a cell mean multiple LCSs exist.
