# Simple Data Structures 

## 1. Arrays / Lists

**What:** Ordered collection of items.

* Python → `list = [1, 2, 3]`
* JavaScript → `let arr = [1, 2, 3]`

**Example:**

```python
arr = [10, 20, 30]
arr.append(40)    # add
print(arr[1])     # 20
```

```javascript
let arr = [10, 20, 30];
arr.push(40);
console.log(arr[1]); // 20
```

**Mini-test:**

1. How do you add to the end of an array?
2. Are arrays ordered?

**Practice test:**

* Write a function to find the largest number in an array.

---

## 2. Dictionaries / Objects

**What:** Store data as **key → value** pairs.

* Python → `{"name": "Alice"}`
* JavaScript → `{name: "Alice"}`

**Example:**

```python
user = {"name": "Alice", "age": 25}
print(user["name"])
```

```javascript
let user = {name: "Alice", age: 25};
console.log(user.name);
```

**Mini-test:**

1. What’s the purpose of a key in a dictionary?
2. Can you have two identical keys?

**Practice test:**

* Count how many times each word appears in a sentence.

---

## 3. Sets

**What:** Collection of **unique** items (no duplicates).

**Example:**

```python
s = {1, 2, 3}
s.add(3)
print(s)  # {1, 2, 3}
```

```javascript
let s = new Set([1, 2, 3]);
s.add(3);
console.log(s); // {1, 2, 3}
```

**Mini-test:**

1. Do sets allow duplicates?
2. Can you access items by index?

**Practice test:**

* Remove duplicates from an array using a set.

---

## 4. Stacks

**What:** Last In, First Out (**LIFO**). Like a stack of plates.

**Example:**

```python
stack = []
stack.append(1)
stack.append(2)
print(stack.pop())  # 2
```

```javascript
let stack = [];
stack.push(1);
stack.push(2);
console.log(stack.pop()); // 2
```

**Mini-test:**

1. What does LIFO mean?

**Practice test:**

* Check if parentheses in a string are balanced: `"(()())"` ✅ `"(()"` ❌

---

## 5. Queues

**What:** First In, First Out (**FIFO**). Like a line at a shop.

**Example:**

```python
from collections import deque
q = deque()
q.append(1)
q.append(2)
print(q.popleft())  # 1
```

```javascript
let q = [];
q.push(1);
q.push(2);
console.log(q.shift()); // 1
```

**Mini-test:**

1. What does FIFO mean?

**Practice test:**

* Simulate a queue at a bank (people enter, people leave).

---

## 6. Linked Lists

**What:** A chain of nodes. Each node has data + pointer to next.

**Example:**

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

head = Node(10)
head.next = Node(20)
```

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}
let head = new Node(10);
head.next = new Node(20);
```

**Mini-test:**

1. Are linked lists indexed?
2. Which is faster: inserting in middle of a list or a linked list?

**Practice test:**

* Write a function to reverse a linked list.

---

## 7. Trees

**What:** Hierarchical structure with root + children.

* Example: family tree, file system.

**Example:**

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

root = Node(10)
root.left = Node(5)
root.right = Node(20)
```

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.left = null;
    this.right = null;
  }
}
let root = new Node(10);
root.left = new Node(5);
root.right = new Node(20);
```

**Mini-test:**

1. What is a binary tree?

**Practice test:**

* Do an in-order traversal (left → root → right).

---

## 8. Graphs

**What:** Collection of **nodes (vertices)** connected by **edges**.

**Example:**

```python
graph = {
  "A": ["B", "C"],
  "B": ["A", "D"]
}
```

```javascript
let graph = {
  A: ["B", "C"],
  B: ["A", "D"]
};
```

**Mini-test:**

1. What are vertices and edges?

**Practice test:**

* Traverse the graph using BFS (Breadth-First Search).

---

## 9. When to Use What

* **Array** → ordered data, fast indexing.
* **Dictionary/Object** → key → value mapping.
* **Set** → remove duplicates, check membership.
* **Stack** → undo, backtracking.
* **Queue** → scheduling, BFS.
* **Linked List** → many insertions/deletions.
* **Tree** → hierarchical data.
* **Graph** → networks, relationships.

---

# ✅ Final Test

Try to answer these:

1. Write a Python/JS function to reverse a string using a stack.
2. Use a queue to simulate ticket booking.
3. Implement a word frequency counter using a dictionary.
4. Build a set from a list and remove duplicates.
5. Write in-order traversal of a binary tree.
6. Show BFS traversal of a simple graph.

