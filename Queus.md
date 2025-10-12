
# 🔷 Understanding Queues

## 🔹 What is a Queue?
A **Queue** is a linear data structure that follows the **First In, First Out (FIFO)** principle.  
The first element added is the first one removed.  
Think of it like a **line at a shop** — the person who joins first is served first.

---

## 🔹 Real-World Analogy
- People waiting in a queue at a bank or supermarket  
- Print jobs waiting in a printer queue  
- Task scheduling in operating systems  

---

## 🔹 Core Operations
| Operation | Description | Example |
|------------|--------------|----------|
| `enqueue(x)` | Add element `x` to the end | `queue.append(x)` |
| `dequeue()` | Remove and return the front element | `queue.pop(0)` |
| `peek()` / `front()` | Get the front element without removing it | `queue[0]` |
| `isEmpty()` | Check if the queue is empty | `len(queue) == 0` |

---

## 🔹 Code Examples

### **Python**
```python
# Queue implementation using list
queue = []
queue.append(1)   # enqueue
queue.append(2)
print(queue.pop(0))  # dequeue -> 1
````

---

### **JavaScript**

```javascript
// Queue implementation using array
let queue = [];
queue.push(1);   // enqueue
queue.push(2);
console.log(queue.shift()); // dequeue -> 1
```

---

## 🔹 Mini-Test

**Question:** What does **FIFO** mean?
**Answer:** **First In, First Out** — the first element inserted is the first to be removed.

---

## 🔹 Practice Problem

**Task:** Implement a function to simulate a queue using two stacks.

### **Example**

Input:

```
enqueue(1)
enqueue(2)
dequeue()
enqueue(3)
dequeue()
```

Output:

```
1
2
```

---

## 🔹 Python Implementation

```python
class QueueUsingStacks:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []

    def enqueue(self, x):
        self.stack1.append(x)

    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        if not self.stack2:
            raise IndexError("Queue is empty")
        return self.stack2.pop()

# Test
q = QueueUsingStacks()
q.enqueue(1)
q.enqueue(2)
print(q.dequeue())  # 1
q.enqueue(3)
print(q.dequeue())  # 2
```

---

## 🔹 JavaScript Implementation

```javascript
class QueueUsingStacks {
  constructor() {
    this.stack1 = [];
    this.stack2 = [];
  }

  enqueue(x) {
    this.stack1.push(x);
  }

  dequeue() {
    if (this.stack2.length === 0) {
      while (this.stack1.length > 0) {
        this.stack2.push(this.stack1.pop());
      }
    }
    if (this.stack2.length === 0) throw new Error("Queue is empty");
    return this.stack2.pop();
  }
}

// Test
const q = new QueueUsingStacks();
q.enqueue(1);
q.enqueue(2);
console.log(q.dequeue()); // 1
q.enqueue(3);
console.log(q.dequeue()); // 2
```

---

## 🔹 Key Takeaways

* Queue = **FIFO** structure
* Enqueue → add to rear
* Dequeue → remove from front
* Used in:

  * Task scheduling
  * Breadth-first search (BFS)
  * Message queues
  * CPU job management

---

```
```
