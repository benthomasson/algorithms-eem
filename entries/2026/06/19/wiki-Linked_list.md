---
source: sources/wiki-Linked_list.md
source_url: https://en.wikipedia.org/wiki/Linked_list
---

## Linked Lists: Structure, Variants, and Tradeoffs

Linked lists are a fundamental linear data structure where each element (node) contains data and a pointer to the next node, rather than relying on contiguous memory placement. This page covers the history, variants (singly, doubly, circular, multiply linked), core operations (insertion, deletion, traversal), and detailed tradeoffs against arrays and dynamic arrays. Linked lists enable O(1) insertion/deletion at known positions but sacrifice random access and cache locality.

## Key Concepts

- **Node structure**: Each node holds a data/payload field and one or more link/pointer fields to other nodes
- **Head**: The first node in the list; provides access to the entire structure
- **Tail**: Either the rest of the list after the head, or the last node specifically
- **Singly linked list**: Each node has one pointer (`next`); supports forward traversal only
- **Doubly linked list**: Each node has two pointers (`next` and `prev`); supports bidirectional traversal at the cost of extra space per node
- **Circular linked list**: The last node points back to the first node instead of null; useful for naturally cyclic structures (round-robin scheduling, polygon vertices, buffer pools)
- **Multiply linked list**: Nodes contain two or more link fields connecting the same data in different orderings (e.g., by name, by date)
- **Sentinel/dummy node**: An extra node added before the first or after the last element to simplify boundary-condition handling in algorithms
- **XOR-linking**: A technique to implement a doubly linked list using only one link field per node by storing `prev XOR next`; requires bitwise operations on addresses
- **Handle**: A reference (pointer) to the first node, giving access to the whole list; sometimes a pair of pointers (first and last)
- **Tail-sharing**: Singly linked lists allow multiple lists to share a common tail segment — a form of persistent data structure; not possible with doubly or circularly linked lists
- **Access time is O(n)**: No random access; must traverse sequentially from the head
- **Insertion/deletion at a known position is O(1)**: Only pointer reassignment needed, no element shifting
- **Cache locality is poor**: Nodes are scattered in memory, leading to more cache misses than arrays

## Commands and Syntax

**C — Add node to tail of singly linked list:**
```c
typedef struct Node {
    int value;
    struct Node* next;
} Node;

Node* addNodeToTail(Node* head, int value) {
    Node* temp = (Node*)malloc(sizeof *temp);
    temp->value = value;
    temp->next = NULL;
    if (!head) {
        head = temp;
    } else {
        Node* p = head;
        while (p->next) {
            p = p->next;
        }
        p->next = temp;
    }
    return head;
}
```

**Pseudocode patterns for core operations:**
- **Insert at head**: Create node, set `node->next = head`, update `head = node` — O(1)
- **Insert at tail (known tail)**: Create node, set `tail->next = node`, update `tail` — O(1)
- **Insert at tail (unknown tail)**: Traverse to end first — O(n)
- **Delete node (singly linked)**: Requires pointer to the *previous* node to relink — O(1) given prev, O(n) to find prev
- **Delete node (doubly linked)**: Can delete given only the node's address — O(1)
- **Cycle detection**: Use Floyd's algorithm (two pointers at different speeds); if they meet, a cycle exists

## Relationships

- **Implements ADTs**: Lists, stacks, queues, associative arrays, S-expressions can all be built on linked lists
- **vs. Dynamic arrays**: Arrays give O(1) random access and better cache performance; linked lists give O(1) insert/delete at known positions without reallocation
- **vs. Balanced trees (AVL, red-black)**: Trees offer O(log n) access and O(log n) insert/delete, bridging the gap between arrays and linked lists
- **Unrolled linked lists**: Hybrid storing multiple elements per node — better cache performance, lower pointer overhead
- **CDR coding**: Optimization replacing pointers with inline data to reduce overhead
- **Hashed array trees**: O(1) access with O(sqrt(n)) excess space — another hybrid
- **LISP/Scheme**: Linked lists are the primary data structure; `car` = head data, `cdr` = rest of list
- **Persistent data structures**: Singly linked lists support tail-sharing, enabling immutable/persistent variants
- **List ranking problem**: Converting linked list to array representation; trivial sequentially but a significant challenge in parallel algorithms
- **Josephus problem**: Classic illustration of linked list vs. array tradeoffs (easy deletion vs. easy indexing)
- **OS internals**: Doubly linked lists maintain active process/thread lists; rootkits may unlink from these to evade detection

## Exam-Relevant Points

| Operation | Linked List | Dynamic Array | Balanced Tree |
|-----------|------------|---------------|---------------|
| Access by index | O(n) | O(1) | O(log n) |
| Insert at beginning | O(1) | O(n) | O(log n) |
| Insert at end (known) | O(1) | O(1) amortized | O(log n) |
| Insert in middle | O(n) search + O(1) splice | O(n) | O(log n) |
| Delete (known node) | O(1) doubly; O(n) singly | O(n) | O(log n) |
| Space overhead | O(n) for pointers | O(n) for unused capacity | O(n) |

- Linked list access is **sequential only** — no random access; arrays have superior **cache locality**
- Insertion/deletion is O(1) **only if you already have a pointer to the position**; finding that position is O(n)
- Doubly linked lists require **more space per node** but allow deletion given only the node's address
- Singly linked lists are **recursive data structures** — many operations have elegant recursive solutions
- Circular lists allow a **single pointer to the last node** to serve as access to both ends (useful for queues)
- Sentinel nodes **eliminate null-check edge cases** but consume extra space — tradeoff for many short lists
- XOR-linked lists save space but **require bitwise address operations**, limiting portability to high-level languages
- **Tail-sharing** is exclusive to singly linked linear lists — doubly linked and circular lists cannot share structure
- The **list ranking problem** (linked list to array conversion) is trivial sequentially but a deep topic in parallel computing
- Historical origin: Newell, Shaw, and Simon (1955-56) at RAND/CMU created linked lists for IPL; McCarthy's LISP (1958) made them central to programming
