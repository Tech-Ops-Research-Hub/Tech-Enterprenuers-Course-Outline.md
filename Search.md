# Linked List Search — Detailed DSA Guide (From Scratch)

## 1. Concept Overview

A linked list is a sequence of nodes. Each node stores:

* A piece of data
* A pointer/reference to the next node

Search means scanning the list node-by-node until you either:

* Find the target value
* Reach the end without finding it

There is no direct access by index. Every search begins at the head.

---

## 2. Why Search Works This Way

Linked lists are linear structures. You cannot jump to the middle.
The only available operation is: move to the next node.

Therefore, search is **sequential traversal**.

---

## 3. When to Use Linked List Search

Use it when:

* Data is dynamic (frequent insertions/deletions)
* Memory is fragmented
* You don't require fast lookup by index

Search time is **O(n)**.

---

## 4. Search Logic (First Principles Breakdown)

1. Start at the head node.
2. Compare the node's data with the key.
3. If equal → search succeeds.
4. Otherwise move to the next node.
5. If next is null → search fails.

You repeat the same operation at every node.

---

## 5. Pseudocode

```
function search(key):
    node = head
    while node is not null:
        if node.data == key:
            return true
        node = node.next
    return false
```

---

## 6. Python Implementation (From Scratch)

```
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def insert(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def search(self, key):
        temp = self.head
        while temp:
            if temp.data == key:
                return True
            temp = temp.next
        return False
```

---

## 7. Step-by-Step Execution Example

Assume list: `7 -> 3 -> 10 -> 5`

Searching for **10**:

* Step 1: Compare 7 with 10 → not equal
* Step 2: Compare 3 with 10 → not equal
* Step 3: Compare 10 with 10 → match → return true

Searching for **8**:

* 7 → 3 → 10 → 5 → null → not found → return false

---

## 8. Time and Space Complexity

* **Time**: O(n) — must check each node
* **Space**: O(1) — only temp pointer is used

---

## 9. Edge Cases

* Empty list → return false immediately
* Single-element list
* Value appears more than once → return first match
* Searching for None/null (depends on data rules)

---

## 10. Extended Variant: Return Node Instead of Boolean

```
    def search_node(self, key):
        temp = self.head
        while temp:
            if temp.data == key:
                return temp
            temp = temp.next
        return None
```

---

## 11. Testing

```
ll = LinkedList()
ll.insert(5)
ll.insert(10)
ll.insert(3)

print(ll.search(10))  # True
print(ll.search(8))   # False
```
## Questions
### 1. Define a linked list and explain why search must be sequential.
### 2. State the time and space complexity of linked-list search and justify each.
### 3. Describe the exact steps executed when searching for a value that is not in the list.
### 4. Rewrite the search algorithm so it returns the node instead of a boolean.
### 5. Explain how search behaves in an empty list, a single-node list, and a list with duplicate values.

