# 📘 Understanding **Stacks** in Detail  

A **Stack** is a *linear data structure* that follows the **LIFO (Last In, First Out)** principle — the last element added is the first one to be removed. Think of a stack as a pile of plates: you can only remove the top plate first.

---

## 🧠 Core Concept  

- **LIFO Principle** → Last element pushed is the first to pop out.  
- Operations occur only at **one end (the top)**.  
- Used in **function calls**, **undo/redo**, **expression evaluation**, **backtracking**, and **browser history**.

---

## 🧩 Basic Stack Operations  

| Operation | Description | Time Complexity |
|------------|--------------|-----------------|
| `push(x)` | Add an element `x` on top of the stack | O(1) |
| `pop()` | Remove the top element | O(1) |
| `peek()` or `top()` | View the top element without removing it | O(1) |
| `isEmpty()` | Check if the stack is empty | O(1) |
| `size()` | Return the number of elements | O(1) |

---

## 🏗️ Stack Implementation Examples  

### 1. **Using Array (Static Stack)**
```javascript
class Stack {
  constructor() {
    this.items = [];
  }

  push(element) {
    this.items.push(element);
  }

  pop() {
    if (this.isEmpty()) return "Underflow";
    return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}
