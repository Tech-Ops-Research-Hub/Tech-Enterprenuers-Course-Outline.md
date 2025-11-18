# Linked List Reversal — Iterative Method (From Scratch)

## 1. Concept Overview

Reversing a linked list means flipping the direction of every pointer so that the last node becomes the head and every `next` link is inverted.

A singly linked list only has forward pointers. Therefore, reversal requires manually rewiring each link.

---

## 2. Core Idea

At every step, you disconnect a node from its next node and make it point backward.

This is done without losing access to the rest of the list by storing the next node temporarily.

Reversal is an in-place operation. No new nodes are created.

---

## 3. Why the Iterative Method Works

You maintain three pointers:

* `prev` → the node behind the current one
* `current` → the node you're processing
* `next_node` → the node ahead, preventing loss of the remaining list

At each step:

1. Save the next node.
2. Reverse the `current.next` pointer.
3. Move `prev` forward.
4. Move `current` forward.

When `current` becomes null, `prev` holds the new head.

---

## 4. Visualization

Initial:

```
A -> B -> C -> D -> None
```

During reversal:

```
prev    current    next_node
None      A          B
```

After first rewiring:

```
A -> None
```

Pointers move:

```
prev = A
current = B
```

Repeat until list ends.

End result:

```
D -> C -> B -> A -> None
```

---

## 5. Pseudocode

```
reverse():
    prev = None
    current = head

    while current != None:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node

    head = prev
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

---

## 7. Step-by-Step Execution Example

List: `5 -> 9 -> 1 -> 4`

Iteration breakdown:

* Iteration 1: reverse 5’s pointer → list becomes `5 -> None`
* Iteration 2: reverse 9’s pointer → list fragment `9 -> 5`
* Iteration 3: reverse 1’s pointer → `1 -> 9 -> 5`
* Iteration 4: reverse 4’s pointer → `4 -> 1 -> 9 -> 5`

Final head = 4

---

## 8. Key Properties

* **Time Complexity:** O(n) — single pass
* **Space Complexity:** O(1) — no extra memory
* **Stable:** Node values preserved, only pointers change
* **In-place:** No new allocation

---

## 9. Edge Cases

* Empty list → head remains None
* Single node → unchanged
* Long list → same logic, stable behavior

---

## 10. Error Traps to Avoid

* Forgetting to store `next_node` → losing access to the list
* Misplacing `prev = current` and `current = next_node` order → corrupted links
* Forgetting to update head at the end

---

## 11. Testing

```
ll = LinkedList()
ll.insert(4)
ll.insert(1)
ll.insert(9)
ll.insert(5)

ll.reverse()  # List becomes 4 -> 1 -> 9 -> 5
```
