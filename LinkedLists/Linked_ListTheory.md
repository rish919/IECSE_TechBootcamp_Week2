# Linked List - Complete Theory Guide

The Linked List is a linear data structure where elements are stored in **nodes**.

Each node contains:
- Data
- A reference (pointer) to the next node

Unlike arrays:
- Memory is **not contiguous**
- Size is **dynamic**
- Insertions & deletions are easier

# 📌 Why Do We Need Linked Lists?

Problem with Arrays:
- Fixed size
- Insertion in middle → O(n)
- Deletion in middle → O(n)

Linked Lists solve:
- Dynamic growth
- O(1) insertion (if pointer known)
- Flexible memory usage

# 🧱 Basic Structure

## 1️⃣ Singly Linked List Node

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}
```

## Visual Representation

```
Head
 ↓
[10] → [20] → [30] → null
```

Each node stores:
- Value
- Address of next node


# 🔄 Types of Linked Lists


## 1️⃣ Singly Linked List

Each node points to next node only.

```
1 → 2 → 3 → 4 → null
```

Traversal: Only forward


## 2️⃣ Doubly Linked List

Each node has:
- Pointer to next
- Pointer to previous

```java
class DoublyNode {
    int val;
    DoublyNode prev;
    DoublyNode next;

    DoublyNode(int val) {
        this.val = val;
    }
}
```

Visualization:

```
null ← 1 ⇄ 2 ⇄ 3 ⇄ 4 → null
```

Advantages:
- Traverse both directions
- Easier deletion

Disadvantage:
- Extra memory


## 3️⃣ Circular Linked List

Last node points back to head.

```
1 → 2 → 3 → 4
↑           ↓
← ← ← ← ← ←
```

Used in:
- Round robin scheduling
- Cyclic buffers

# ⚙️ Basic Operations

## 1️⃣ Traversal

Time: O(n)

```java
public void printList(ListNode head) {
    ListNode curr = head;

    while (curr != null) {
        System.out.print(curr.val + " ");
        curr = curr.next;
    }
}
```

## 2️⃣ Insert at Beginning

Time: O(1)

```java
public ListNode insertAtHead(ListNode head, int val) {
    ListNode newNode = new ListNode(val);
    newNode.next = head;
    return newNode;
}
```

## 3️⃣ Insert at End

Time: O(n)

```java
public ListNode insertAtTail(ListNode head, int val) {
    ListNode newNode = new ListNode(val);

    if (head == null) return newNode;

    ListNode curr = head;
    while (curr.next != null) {
        curr = curr.next;
    }

    curr.next = newNode;
    return head;
}
```

## 4️⃣ Delete a Node (Given Value)

Time: O(n)

```java
public ListNode deleteNode(ListNode head, int key) {
    if (head == null) return null;

    if (head.val == key) return head.next;

    ListNode curr = head;

    while (curr.next != null && curr.next.val != key) {
        curr = curr.next;
    }

    if (curr.next != null) {
        curr.next = curr.next.next;
    }

    return head;
}
```

# 🆚 Array vs Linked List

| Feature | Array | Linked List |
|----------|--------|--------------|
| Memory | Contiguous | Non-contiguous |
| Access | O(1) | O(n) |
| Insert | O(n) | O(1)* |
| Delete | O(n) | O(1)* |
| Dynamic | No | Yes |

\* If pointer/reference is known.

# 🧠 Important Concepts

## 1️⃣ Head Pointer

The head stores reference to first node.

If head becomes null → List is empty.

## 2️⃣ Losing Reference Problem

Incorrect pointer update can lose the rest of list.

❌ Wrong:

```java
curr.next = curr.next.next;
curr = curr.next;
```

If done incorrectly, nodes may become unreachable.

Always store next temporarily when modifying pointers.

## 3️⃣ Memory Representation

Each node exists separately in heap memory.

Example:

```
Node1 → memory location 1000
Node2 → memory location 4500
Node3 → memory location 2300
```

Linked by addresses, not adjacency.

# 🔥 Common Patterns

Linked List problems are mostly based on these patterns:

1. Reverse Pattern
2. Fast & Slow Pointer Pattern
3. Dummy Node Pattern
4. Two Pointer Pattern
5. Merge Pattern
6. HashMap + LinkedList (LRU Cache)

If you master these → you can solve most problems.

# 🧪 Edge Cases to Always Handle

✔ head == null  
✔ head.next == null  
✔ Removing head  
✔ Removing last node  
✔ Single element list  
✔ Even vs Odd length  
✔ Cycle present  

# 📊 Time Complexity Summary

| Operation | Time |
|------------|--------|
| Traverse | O(n) |
| Insert at head | O(1) |
| Insert at tail | O(n) |
| Delete | O(n) |
| Reverse | O(n) |
| Detect Cycle | O(n) |

# 🚀 When Should You Think of Linked Lists?

Look for keywords:

- "Remove node"
- "Reverse"
- "Merge two sorted lists"
- "Find middle"
- "Detect cycle"
- "Design LRU cache"
- "Add two numbers"

# 🎯 Summary

Linked Lists are:
- Dynamic
- Pointer-based
- Flexible
- Powerful in interviews

They trade:
- Faster insert/delete  
for  
- Slower random access  

Master pointer manipulation, and Linked Lists become easy.

---

Next: Practice implementing all operations manually before solving problems.
