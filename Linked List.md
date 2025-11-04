# 🔷 Linked Lists 

---

## 🔹 1. Introduction

A **Linked List** is a **linear data structure** in which elements, known as **nodes**, are linked together using **pointers**.
Unlike arrays where memory allocation is contiguous, linked lists store elements in scattered memory locations connected through references.

Each node in a linked list contains:

* **Data:** The actual value stored.
* **Pointer (`next`):** A reference to the next node in the sequence.

This structure enables **dynamic memory allocation**, allowing the list to grow or shrink at runtime without needing reallocation or shifting of elements.

---

## 🔹 2. Why Linked Lists Exist

Arrays have a fixed size and cannot efficiently handle frequent insertions or deletions in the middle of the sequence.
Linked lists solve these issues by providing:

* **Dynamic size adjustment.**
* **Efficient insertions and deletions.**
* **Sequential access through pointers instead of indices.**

However, this comes at the cost of:

* No random access (O(n) traversal time).
* Extra memory usage due to pointer storage.
* More complex memory management.

---

## 🔹 3. Node Structure

### Python Example:

```python
class Node:
    def __init__(self, data):
        self.data = data     # store value
        self.next = None     # pointer to next node
```

Every node stores a data field and a pointer to the next node.
The last node’s pointer is always set to `None`.

---

## 🔹 4. Visual Representation

```
Head
 ↓
+------+    +------+    +------+
| 10   | -> | 20   | -> | 30   | -> None
+------+    +------+    +------+
```

Here:

* `Head` points to the first node.
* Each node links to the next.
* The chain terminates at `None`.

---

## 🔹 5. Types of Linked Lists

### 5.1 Singly Linked List

Each node points only to the next node.
Traversal can only happen in one direction — forward.

```
Head → A → B → C → None
```

### 5.2 Doubly Linked List

Each node has two pointers: one to the next node and one to the previous node.
Traversal can occur both forward and backward.

```
None ← A ⇄ B ⇄ C → None
```

### 5.3 Circular Linked List

The last node points back to the head instead of `None`.
Can be singly or doubly circular.

```
Head → A → B → C ↺
```

---

## 🔹 6. Basic Operations

### 6.1 Insertion

**At Beginning:**

```python
def insert_at_beginning(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
```

**At End:**

```python
def insert_at_end(self, data):
    new_node = Node(data)
    if not self.head:
        self.head = new_node
        return
    temp = self.head
    while temp.next:
        temp = temp.next
    temp.next = new_node
```

**At Specific Position:**

```python
def insert_at_position(self, data, pos):
    new_node = Node(data)
    if pos == 0:
        new_node.next = self.head
        self.head = new_node
        return
    temp = self.head
    for _ in range(pos - 1):
        if not temp:
            raise IndexError("Position out of range")
        temp = temp.next
    new_node.next = temp.next
    temp.next = new_node
```

---

### 6.2 Deletion

**By Value:**

```python
def delete_node(self, key):
    temp = self.head

    # Case 1: Head node contains the key
    if temp and temp.data == key:
        self.head = temp.next
        return

    prev = None
    while temp and temp.data != key:
        prev = temp
        temp = temp.next

    if not temp:
        raise ValueError("Key not found")

    prev.next = temp.next
```

**By Position:**

```python
def delete_at_position(self, pos):
    if not self.head:
        raise IndexError("List is empty")

    temp = self.head
    if pos == 0:
        self.head = temp.next
        return

    for _ in range(pos - 1):
        if not temp:
            raise IndexError("Position out of range")
        temp = temp.next

    if not temp.next:
        raise IndexError("Position out of range")

    temp.next = temp.next.next
```

---

### 6.3 Traversal

To print all elements:

```python
def print_list(self):
    temp = self.head
    while temp:
        print(temp.data, end=" -> ")
        temp = temp.next
    print("None")
```

---

### 6.4 Search

To check if a value exists:

```python
def search(self, key):
    temp = self.head
    while temp:
        if temp.data == key:
            return True
        temp = temp.next
    return False
```

---

## 🔹 7. Reversal

### Iterative Method:

```python
def reverse(self):
    prev = None
    current = self.head
    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
    self.head = prev
```

### Recursive Method:

```python
def reverse_recursive(self, node):
    if not node or not node.next:
        self.head = node
        return node
    rest = self.reverse_recursive(node.next)
    node.next.next = node
    node.next = None
    return rest
```

---

## 🔹 8. Detecting Loops (Cycle Detection)

Using Floyd’s Cycle Detection Algorithm:

```python
def has_loop(self):
    slow = fast = self.head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

---

## 🔹 9. Finding Middle Element

```python
def find_middle(self):
    slow = fast = self.head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow.data if slow else None
```

---

## 🔹 10. Length of Linked List

```python
def length(self):
    count = 0
    temp = self.head
    while temp:
        count += 1
        temp = temp.next
    return count
```

---

## 🔹 11. Time and Space Complexity

| Operation              | Average Case | Worst Case | Notes                       |
| ---------------------- | ------------ | ---------- | --------------------------- |
| Traversal              | O(n)         | O(n)       | Must visit all nodes        |
| Insertion at Beginning | O(1)         | O(1)       | Simple pointer reassignment |
| Insertion at End       | O(n)         | O(n)       | Need traversal to last node |
| Deletion by Value      | O(n)         | O(n)       | Traverse until found        |
| Search                 | O(n)         | O(n)       | Linear search only          |
| Reverse                | O(n)         | O(n)       | Single pass                 |
| Space Complexity       | O(n)         | O(n)       | One pointer per node        |

---

## 🔹 12. Complete Linked List Implementation

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def insert_at_end(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        temp = self.head
        while temp.next:
            temp = temp.next
        temp.next = new_node

    def delete_node(self, key):
        temp = self.head
        if temp and temp.data == key:
            self.head = temp.next
            return
        prev = None
        while temp and temp.data != key:
            prev = temp
            temp = temp.next
        if not temp:
            return
        prev.next = temp.next

    def search(self, key):
        temp = self.head
        while temp:
            if temp.data == key:
                return True
            temp = temp.next
        return False

    def reverse(self):
        prev = None
        current = self.head
        while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        self.head = prev

    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")

# Example Usage
if __name__ == "__main__":
    llist = LinkedList()
    llist.insert_at_end(10)
    llist.insert_at_end(20)
    llist.insert_at_beginning(5)
    llist.print_list()
    llist.delete_node(20)
    llist.print_list()
    llist.reverse()
    llist.print_list()
```

---

## 🔹 13. Memory Representation

Each node occupies a separate memory block.
The `next` pointer stores the **address of the next node**, not its index.
This design allows non-contiguous allocation, unlike arrays.

```
| Data | Next (address) |
```

---

## 🔹 14. Applications

* Dynamic memory management systems.
* Implementation of Stacks and Queues.
* Graph adjacency lists.
* Undo/Redo functionality in editors.
* Real-time navigation and playlist systems.
* Memory-efficient data manipulation for variable-sized datasets.

---

## 🔹 15. Key Advantages and Disadvantages

| **Advantages**                     | **Disadvantages**         |
| ---------------------------------- | ------------------------- |
| Dynamic memory allocation          | No random access          |
| Efficient insert/delete operations | Extra memory for pointers |
| Easy to expand                     | Slower traversal          |
| Flexible data structure            | Complex implementation    |

---

## 🔹 16. Real-World Examples

1. **Web Browsers:** Forward and Backward navigation implemented using Doubly Linked Lists.
2. **Music Players:** Circular Linked Lists to repeat playlists.
3. **Undo Features:** Linked list stack-based structure for reverse actions.
4. **Memory Management:** OS kernel uses linked lists to manage free memory blocks.

---

## 🔹 17. Comparison with Arrays

| Feature           | Array      | Linked List           |
| ----------------- | ---------- | --------------------- |
| Memory Allocation | Static     | Dynamic               |
| Access Time       | O(1)       | O(n)                  |
| Insert/Delete     | Costly     | Efficient             |
| Memory Overhead   | Low        | High (extra pointers) |
| Data Locality     | Contiguous | Non-contiguous        |

---

## 🔹 18. Summary Points

* Core unit: Node (Data + Pointer).
* Head node marks list entry point.
* No direct indexing — must traverse.
* Supports dynamic resizing.
* Efficient for frequent insert/delete operations.
* Pointers must be carefully managed to avoid broken links.
* Best suited for flexible and dynamic datasets.

---

## 🔹 19. Practice Exercises

1. Implement a function to **merge two sorted linked lists**.
2. Write code to **remove duplicates** from a linked list.
3. Create a function to **find the Nth node from the end**.
4. Write a function to **detect and remove a loop**.
5. Build a **circular doubly linked list** version.

---

## 🔹 20. Conclusion

A **Linked List** forms the foundation for multiple complex data structures such as stacks, queues, hash tables, and graphs.
Understanding it establishes a base for mastering **memory management**, **dynamic allocation**, and **pointer-based system design**.

---

**End of Detailed Linked List Notes for GitHub README**
