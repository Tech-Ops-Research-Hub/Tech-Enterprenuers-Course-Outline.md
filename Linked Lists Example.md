### 🔹 Question:

Write a Python method `insert_at_position(self, data, pos)` for a singly linked list class that inserts a new node containing the given `data` at the specified `pos` (0-based index).

**Requirements:**

1. If `pos == 0`, the new node becomes the new head of the list.
2. If `pos` is greater than the current list length, raise an `IndexError("Position out of range")`.
3. The function should correctly adjust pointers so that the new node is linked between its previous and next nodes.
4. Demonstrate the method using an example list with multiple insertions at different positions.

**Example Output:**

```
Initial List: 10 -> 20 -> 30 -> None
Insert 5 at position 0
Insert 25 at position 2
Insert 40 at position 4
Final List: 5 -> 10 -> 25 -> 20 -> 30 -> 40 -> None
```







### ✅ Solution

```python
# Node structure
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

# Linked List structure
class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_end(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        temp = self.head
        while temp.next:
            temp = temp.next
        temp.next = new_node

    def insert_at_position(self, data, pos):
        new_node = Node(data)

        # Case 1: Insert at beginning
        if pos == 0:
            new_node.next = self.head
            self.head = new_node
            return

        # Traverse to position - 1
        temp = self.head
        for _ in range(pos - 1):
            if not temp:
                raise IndexError("Position out of range")
            temp = temp.next

        # Insert node
        new_node.next = temp.next
        temp.next = new_node

    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")


# Demonstration
llist = LinkedList()
llist.insert_at_end(10)
llist.insert_at_end(20)
llist.insert_at_end(30)

print("Initial List:")
llist.print_list()

llist.insert_at_position(5, 0)   # Insert at beginning
llist.insert_at_position(25, 2)  # Insert in middle
llist.insert_at_position(40, 5)  # Insert at end

print("\nFinal List:")
llist.print_list()
```

### **Output**

```
Initial List:
10 -> 20 -> 30 -> None

Final List:
5 -> 10 -> 25 -> 20 -> 30 -> 40 -> None
```

### **Explanation**

1. `insert_at_position(5, 0)` places `5` at the start → becomes new head.
2. `insert_at_position(25, 2)` links `25` between `10` and `20`.
3. `insert_at_position(40, 5)` links `40` after the last node.

Each pointer reassignment ensures that the chain remains unbroken and ordered.
