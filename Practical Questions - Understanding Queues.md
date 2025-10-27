# 🔷 Practical Questions — Queues

---

### **1. Conceptual Understanding**

1. Explain the **FIFO** property in your own words.
2. How is a **queue** different from a **stack**?
3. Give three real-world examples of queue usage.
4. What happens if you call `dequeue()` on an empty queue?
5. Why is a queue often used in **Breadth-First Search (BFS)** algorithms?

---

### **2. Code Tracing (Python)**

Given the following code:

```python
queue = []
queue.append(10)
queue.append(20)
queue.append(30)
print(queue.pop(0))
queue.append(40)
print(queue.pop(0))
print(queue)
```

**Questions:**

1. What are the outputs of the two `print()` statements?
2. What is the final state of the queue?
3. Which operations represent **enqueue** and which represent **dequeue**?

---

### **3. Code Tracing (JavaScript)**

```javascript
let q = [];
q.push('A');
q.push('B');
q.push('C');
console.log(q.shift());
q.push('D');
console.log(q.shift());
console.log(q);
```

**Questions:**

1. What are the outputs of the two `console.log()` calls?
2. What is the final state of `q`?
3. Which line demonstrates the **FIFO** property?

---

### **4. Implementation Challenges**

1. Implement a queue using only **two stacks** in Python or JavaScript.
2. Implement a **circular queue** that supports wrap-around indexing.
3. Modify the queue so that it can display its current **front** and **rear** elements without removing them.
4. Write a function `reverseQueue(queue)` that reverses all elements of a queue using only standard queue operations.
5. Implement a **queue with max size**, where `enqueue()` raises an error if the queue is full.

---

### **5. Applied Scenarios**

1. Explain how queues are used in **printer spooling systems**.
2. Describe how **task scheduling** in operating systems makes use of queues.
3. In **web servers**, how can queues help manage incoming client requests?
4. How would you use a queue to perform **level-order traversal** of a binary tree?
5. Explain one way queues are used in **network packet buffering**.

---

### **6. Debugging Questions**

For the code below, identify the error and correct it:

```python
class Queue:
    def __init__(self):
        self.queue = []

    def dequeue(self):
        return self.queue.pop()
```

**Hint:** Which end of the list should be popped to maintain FIFO?

---

### **7. Mini-Project Exercise**

**Problem:**
Simulate a **customer service system** where each customer joins a queue and is served in order.

**Requirements:**

* Each customer has a name and a service number.
* Customers join via `enqueue(name)` and are served via `dequeue()`.
* Print the queue status after every operation.

**Expected Example:**

```
enqueue('Alice')
enqueue('Bob')
dequeue()
enqueue('Charlie')
```

**Output:**

```
Alice served
Current Queue: ['Bob', 'Charlie']
```

---

### **8. Key Logic Review**

* **Queue Rule:** First element in → first element out.
* **Primary Methods:** `enqueue()`, `dequeue()`, `peek()`, `isEmpty()`.
* **Common Uses:** Scheduling, buffering, BFS traversal, messaging systems.
