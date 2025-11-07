# 📘 JavaScript: Arrow Functions

---
---

## **1. Basic Syntax**

### **Traditional Function**
```javascript
function add(a, b) {
  return a + b;
}
````

### **Arrow Function**

```javascript
const add = (a, b) => a + b;
```

---

## **2. Syntax Variations**

| Type                | Syntax                        | Example                                         | Return Behavior            |
| ------------------- | ----------------------------- | ----------------------------------------------- | -------------------------- |
| Single parameter    | `(x) => x * 2`                | `const double = x => x * 2;`                    | Implicit return            |
| Multiple parameters | `(a, b) => a + b`             | `const add = (a, b) => a + b;`                  | Implicit return            |
| No parameters       | `() => value`                 | `const greet = () => "Hello";`                  | Implicit return            |
| Multi-line          | `(a, b) => { return a * b; }` | `const multiply = (a, b) => { return a * b; };` | Explicit `return` required |

---

## **3. Key Differences from Regular Functions**

### **a. No `this` Binding**

Arrow functions **don’t have their own `this`**.
They capture `this` from the **surrounding lexical scope**.

```javascript
function Counter() {
  this.count = 0;
  setInterval(() => {
    this.count++;
    console.log(this.count);
  }, 1000);
}

new Counter(); // Works correctly
```

If you used a normal function inside `setInterval`, `this` would refer to the global object, not the instance.

---

### **b. Cannot be Used as Constructors**

Arrow functions **cannot be used with `new`** because they do not have a `[[Construct]]` method.

```javascript
const Person = (name) => { this.name = name; };
// new Person("Brandon"); ❌ TypeError
```

---

### **c. No `arguments` Object**

Arrow functions **do not have an `arguments`** object.
Use **rest parameters** instead.

```javascript
const sum = (...args) => args.reduce((a, b) => a + b, 0);
console.log(sum(1, 2, 3)); // 6
```

---

### **d. No `prototype` Property**

Arrow functions do not have a `prototype` property, so you cannot attach methods to them.

```javascript
const greet = () => "Hi";
// greet.prototype.sayHello = () => "Hello"; ❌ Error
```

---

## **4. When to Use Arrow Functions**

✅ **Use them for:**

* Short, inline functions.
* Array operations: `map()`, `filter()`, `reduce()`.
* Callback functions.
* Maintaining lexical `this`.

❌ **Avoid them for:**

* Methods that rely on `this`.
* Object constructors.
* Functions requiring the `arguments` object.

---

## **5. Common Use Cases**

### **Array Methods**

```javascript
const numbers = [1, 2, 3, 4];
const squares = numbers.map(n => n * n);
console.log(squares); // [1, 4, 9, 16]
```

### **Callbacks**

```javascript
setTimeout(() => console.log("Executed after 2s"), 2000);
```

### **Chaining**

```javascript
const result = [10, 20, 30]
  .filter(n => n > 15)
  .map(n => n / 2)
  .reduce((a, b) => a + b);
console.log(result); // 25
```

---

## **6. Practical Example: Lexical `this`**

```javascript
const user = {
  name: "Brandon",
  hobbies: ["Coding", "Music", "Teaching"],
  showHobbies() {
    this.hobbies.forEach(hobby => {
      console.log(`${this.name} loves ${hobby}`);
    });
  }
};
user.showHobbies();
```

Output:

```
Brandon loves Coding
Brandon loves Music
Brandon loves Teaching
```

---

## **7. Comparison Summary**

| Feature             | Regular Function | Arrow Function |
| ------------------- | ---------------- | -------------- |
| Syntax              | Verbose          | Concise        |
| `this`              | Dynamic          | Lexical        |
| `arguments`         | Available        | Not available  |
| `prototype`         | Yes              | No             |
| Used as Constructor | Yes              | No             |

---

## **8. Best Practices**

1. Prefer arrow functions for **small, pure functions**.
2. Avoid using them as **object methods**.
3. Use parentheses for clarity with single-line returns.
4. Always use `{}` and `return` for complex logic blocks.
5. Use them for **functional programming patterns**.

---

## **9. Practice Exercises**

### **Exercise 1**

Convert to arrow function:

```javascript
function greet(name) {
  return "Hello, " + name;
}
```

### **Exercise 2**

Use arrow function to:

* Filter even numbers from `[1,2,3,4,5,6]`.
* Return their sum.

### **Exercise 3**

Explain why `this` behaves differently inside:

```javascript
function example() {
  setTimeout(function() {
    console.log(this);
  }, 1000);
}
example();
```

and

```javascript
function example() {
  setTimeout(() => {
    console.log(this);
  }, 1000);
}
example();
```

---

## **10. Quick Reference**

| Syntax                                     | Description                  |
| ------------------------------------------ | ---------------------------- |
| `const fn = () => value;`                  | One-liner, implicit return   |
| `const fn = (x, y) => x + y;`              | Multiple params              |
| `const fn = x => x * 2;`                   | Single param, no parentheses |
| `const fn = () => { return value; };`      | Explicit return              |
| `const fn = (...args) => args.join(", ");` | Rest parameters              |

---

### **Summary**

Arrow functions simplify syntax and improve lexical `this` handling.
They are best suited for small, inline, and callback functions—not constructors or object methods.

---

```
```
