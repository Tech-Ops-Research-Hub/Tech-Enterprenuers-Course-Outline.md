

---

````markdown
# 🧠 JavaScript Arrow Functions & Array Methods — Practice Questions

## ⚡ 1. Arrow Function Conversion

1. Convert this traditional function into an arrow function:
   ```js
   function subtract(a, b) { return a - b; }
````

2. What is the difference between these two functions?

   ```js
   const square = (x) => { return x * x; }
   ```

   and

   ```js
   const square = x => x * x;
   ```

---

## 🧩 2. Returning Objects

3. Why does this function return `undefined`? How can it be fixed?

   ```js
   const makeItem = () => { id: 1 }
   ```

---

## 🔁 3. Rest Parameters vs `arguments`

4. Why doesn’t this work as expected?
   Rewrite it so that it works correctly.

   ```js
   const sum = () => arguments[0] + arguments[1];
   ```

---

## 🎯 4. Arrow Functions and `this`

5. What will be printed when this code runs? Explain why.

   ```js
   const obj = { val: 20, getVal: () => this.val };
   console.log(obj.getVal());
   ```

6. How can you modify the function so that it correctly logs the value `20`?

---

## 🔢 5. Array Methods

7. Write a function that increments all numbers in an array by 1 using `map`.
   Example:

   ```js
   // Input: [1, 2, 3, 4]
   // Output: [2, 3, 4, 5]
   ```

8. Write a function that filters only even numbers from an array using `filter`.
   Example:

   ```js
   // Input: [1, -2, 3, 10, 15, -6]
   // Output: [-2, 10, -6]
   ```

9. Write a function that returns the total sum of an array using `reduce`.
   Example:

   ```js
   // Input: [10, 20, 30, 40]
   // Output: 100
   ```

---

## 👤 6. Using `this` Correctly

10. Create an object with a `name` property and a `getName()` method that returns the object’s name using `this` (no arrow function).
    Example output when called: `"idhil"`

---

### 💡 Tips

* Use **arrow functions** for concise, single-expression logic.
* Remember: arrow functions do **not** have their own `this` or `arguments`.
* Use `map`, `filter`, and `reduce` for clean array transformations.

---

```

---
```
