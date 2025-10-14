# 🧱 Stack Implementations in Python

### Using `collections.deque`, a Linked List, and `queue.LifoQueue`

A **stack** is a **Last-In, First-Out (LIFO)** data structure where the last element added is the first one to be removed. It supports two main operations:

* **push(item)** — add an element to the top
* **pop()** — remove the topmost element

Stacks are widely used in **undo mechanisms**, **syntax parsing**, **function call management**, and **backtracking algorithms**.

---

## 📘 Table of Contents

1. [Introduction](#introduction)
2. [1️⃣ Using `collections.deque`](#1-using-collectionsdeque)
3. [2️⃣ Using a Linked List](#2-using-a-linked-list)
4. [3️⃣ Using `queue.LifoQueue` (Thread-Safe)](#3-using-queuelifoqueue-thread-safe)
5. [🧩 Comparison Table](#comparison-table)
6. [🧠 Practice Questions](#practice-questions)
7. [🔗 References](#references)

---

## 🪄 Introduction

Stacks can be implemented using various data structures. The choice depends on the **requirements of performance**, **memory efficiency**, and **thread-safety**.

In this repository, we explore **three implementations**:

| Implementation      | Key Feature                | Use Case                                   |
| ------------------- | -------------------------- | ------------------------------------------ |
| `collections.deque` | Fast append/pop operations | General-purpose, performance-critical apps |
| Linked List         | Custom and flexible        | Learning, implementing from scratch        |
| `queue.LifoQueue`   | Thread-safe                | Multi-threaded applications                |

---

## 1️⃣ Using `collections.deque`

The `collections.deque` class is **optimized for fast appends and pops from both ends**, making it ideal for stack operations.

```python
from collections import deque

class StackDeque:
    def __init__(self):
        self.stack = deque()

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
        return "Stack is empty!"

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
        return "Stack is empty!"

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)
```

### ✅ Example Usage

```python
if __name__ == "__main__":
    s = StackDeque()
    s.push(10)
    s.push(20)
    print(s.peek())   # 20
    print(s.pop())    # 20
    print(s.size())   # 1
```

**Advantages:**

* Very fast O(1) append and pop.
* Built-in and memory efficient.
* Ideal for performance-critical applications.

---

## 2️⃣ Using a Linked List

A **Linked List** based implementation provides **complete control** over memory management and node manipulation.

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class StackLinkedList:
    def __init__(self):
        self.top = None
        self._size = 0

    def push(self, value):
        new_node = Node(value)
        new_node.next = self.top
        self.top = new_node
        self._size += 1

    def pop(self):
        if self.is_empty():
            return "Stack is empty!"
        popped_value = self.top.value
        self.top = self.top.next
        self._size -= 1
        return popped_value

    def peek(self):
        if self.is_empty():
            return "Stack is empty!"
        return self.top.value

    def is_empty(self):
        return self.top is None

    def size(self):
        return self._size
```

### ✅ Example Usage

```python
if __name__ == "__main__":
    s = StackLinkedList()
    s.push(5)
    s.push(15)
    print(s.peek())   # 15
    print(s.pop())    # 15
    print(s.size())   # 1
```

**Advantages:**

* Full control over memory.
* Useful for understanding internal working of stacks.
* No predefined size limit.

**Disadvantages:**

* Slightly slower than `deque` due to Python object overhead.

---

## 3️⃣ Using `queue.LifoQueue` (Thread-Safe)

The `queue.LifoQueue` class provides a **thread-safe** stack implementation, ideal for **multi-threaded applications**.

```python
from queue import LifoQueue

class ThreadSafeStack:
    def __init__(self):
        self.stack = LifoQueue()

    def push(self, item):
        self.stack.put(item)

    def pop(self):
        if not self.stack.empty():
            return self.stack.get()
        return "Stack is empty!"

    def peek(self):
        # No direct peek method, so we handle carefully
        if self.stack.empty():
            return "Stack is empty!"
        temp = []
        while not self.stack.empty():
            temp.append(self.stack.get())
        top_item = temp[-1]
        for item in temp:
            self.stack.put(item)
        return top_item

    def is_empty(self):
        return self.stack.empty()

    def size(self):
        return self.stack.qsize()
```

### ✅ Example Usage

```python
if __name__ == "__main__":
    s = ThreadSafeStack()
    s.push("A")
    s.push("B")
    print(s.peek())  # B
    print(s.pop())   # B
    print(s.size())  # 1
```

**Advantages:**

* Built-in **thread safety** using locks.
* Perfect for **multi-threaded environments**.

**Disadvantages:**

* Slightly slower due to locking overhead.
* No direct access (like `peek`).

---

## 🧩 Comparison Table

| Feature       | `collections.deque` | Linked List | `queue.LifoQueue` |
| ------------- | ------------------- | ----------- | ----------------- |
| Speed         | ✅ Fastest           | ⚙️ Moderate | 🐢 Slower         |
| Thread-safe   | ❌ No                | ❌ No        | ✅ Yes             |
| Customization | ❌ Limited           | ✅ High      | ⚙️ Medium         |
| Built-in      | ✅ Yes               | ❌ No        | ✅ Yes             |
| Ideal for     | General use         | Educational | Multithreading    |

---

## 🧠 Practice Questions

### 🧩 Section 1: Using `deque`

1. What happens if you try to pop from an empty deque?
2. Why is `deque` faster than using a Python list for stack operations?
3. Write a method to reverse a string using a `deque` stack.
4. How can you limit the stack size using `deque(maxlen=N)`?
5. Implement a function that checks for balanced parentheses using `deque`.

### 🧩 Section 2: Using Linked List

1. Modify the `StackLinkedList` to support a `clear()` method.
2. How can you detect memory leaks in a linked list stack implementation?
3. What would happen if you forget to update `self.top` after popping?
4. Implement an `__iter__()` method to traverse the stack from top to bottom.
5. Compare the space complexity of `deque` vs Linked List.

### 🧩 Section 3: Using `queue.LifoQueue`

1. What makes `LifoQueue` thread-safe?
2. Write a test that demonstrates concurrent stack operations using `threading`.
3. How can you block a `put()` operation when the queue is full?
4. Why doesn’t `LifoQueue` support direct peeking by default?
5. Implement a timeout pop using `get(timeout=2)` and explain when it’s useful.

---

## 🔗 References

* Python Docs: [`collections.deque`](https://docs.python.org/3/library/collections.html#collections.deque)
* Python Docs: [`queue.LifoQueue`](https://docs.python.org/3/library/queue.html#queue.LifoQueue)
* Data Structures and Algorithms in Python — Michael T. Goodrich

---
