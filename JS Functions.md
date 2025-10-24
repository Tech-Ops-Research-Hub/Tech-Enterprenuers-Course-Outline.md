# JavaScript Function

Functions are the core of JavaScript. This guide removes theory clutter and focuses on **how to use**, **how they behave**, and **how to avoid mistakes** in real code.

---

## 1. Parameters and Return Values

### Concept

Functions take **inputs (parameters)**, process them, and return **outputs**.
If no `return` statement, the function gives back `undefined`.

### Basic Example

```js
function add(a, b) {
  return a + b;
}
console.log(add(2, 3)); // 5
```

### Multiple Returns

To return more than one value, wrap them in an array or object.

```js
function calculate(a, b) {
  return { sum: a + b, product: a * b };
}
const result = calculate(2, 3);
console.log(result.sum); // 5
console.log(result.product); // 6
```

### Pass by Value vs Pass by Reference

* **Primitives** (numbers, strings, booleans) → passed by value.
* **Objects/Arrays** → passed by reference (changes inside function affect the original).

```js
function update(arr) {
  arr.push('New');
}
const list = ['Old'];
update(list);
console.log(list); // ['Old', 'New']
```

### Return Rules

* Once `return` executes, function stops running.
* Use `return` to send output or exit early.

```js
function divide(a, b) {
  if (b === 0) return 'Error: cannot divide by zero';
  return a / b;
}
```

---

## 2. Arrow Functions

### Concept

Arrow functions are **short, modern** alternatives to `function` syntax.

```js
const add = (a, b) => a + b;
```

### Key Practical Notes

1. If one parameter → parentheses optional:
   `x => x * x`
2. For one-line expressions → `return` is implied.
   `const double = x => x * 2`
3. For multiple statements → use braces `{}` and `return` explicitly.

   ```js
   const multiply = (a, b) => {
     const result = a * b;
     return result;
   };
   ```
4. Arrow functions **don’t have their own `this`**.

```js
const person = {
  name: "Brandon",
  sayName: () => console.log(this.name) // 'this' not bound
};
person.sayName(); // undefined
```

Fix:

```js
const person = {
  name: "Brandon",
  sayName() { console.log(this.name); }
};
person.sayName(); // Brandon
```

### Use Case

Use arrows for:

* Short, pure, inline functions.
* Array operations (`map`, `filter`, `reduce`).
* Callbacks.

Avoid arrows for:

* Object methods needing `this`.
* Constructors.

---

## 3. Default and Rest Parameters

### Default Parameters

If no value or `undefined` is passed, the default kicks in.

```js
function greet(name = "Guest") {
  return `Hello, ${name}`;
}
console.log(greet()); // Hello, Guest
console.log(greet("Brandon")); // Hello, Brandon
```

### Rest Parameters

Gather remaining arguments into an array.

```js
function sum(...nums) {
  return nums.reduce((total, n) => total + n, 0);
}
console.log(sum(2, 4, 6)); // 12
```

### Combined Example

```js
function register(user = "Anonymous", ...roles) {
  return `${user} registered as ${roles.join(", ")}`;
}
console.log(register("Brandon", "Admin", "Editor"));
// Brandon registered as Admin, Editor
```

### Key Notes

* Default applies only when value is `undefined`.
* Rest parameters must be last.
* Rest parameters replace `arguments` for clarity.

---

## 4. Closures and Scope

### Concept

A **closure** is when a function “remembers” variables from where it was created, even if called outside that scope.

### Use Case 1 — Private Data

```js
function makeCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

`count` stays private inside the closure — no external access.

### Use Case 2 — Configurable Function

```js
function multiplier(factor) {
  return function(num) {
    return num * factor;
  };
}
const double = multiplier(2);
console.log(double(5)); // 10
```

### Use Case 3 — Loop Fix

Closures fix loop problems.

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// prints 0, 1, 2
```

---

## 5. Higher-Order Functions

### Concept

Functions that take other functions as inputs or return them.

```js
function operate(a, b, operation) {
  return operation(a, b);
}
const add = (x, y) => x + y;
console.log(operate(3, 4, add)); // 7
```

### Common Built-in Higher-Order Functions

1. **`map()`** — transforms every element.

   ```js
   const nums = [1, 2, 3];
   const doubled = nums.map(n => n * 2);
   console.log(doubled); // [2, 4, 6]
   ```
2. **`filter()`** — selects items that match condition.

   ```js
   const even = nums.filter(n => n % 2 === 0);
   console.log(even); // [2]
   ```
3. **`reduce()`** — combines all elements into one.

   ```js
   const sum = nums.reduce((acc, n) => acc + n, 0);
   console.log(sum); // 6
   ```
4. **`forEach()`** — performs action (no return).

   ```js
   nums.forEach(n => console.log(n * 2));
   ```

### Practical Example: Custom Filter

```js
function customFilter(arr, fn) {
  const result = [];
  for (let item of arr) {
    if (fn(item)) result.push(item);
  }
  return result;
}
console.log(customFilter([1, 2, 3, 4], n => n > 2)); // [3,4]
```

---

## 6. Pure vs Impure Functions

### Pure Functions

* Depend only on inputs.
* Produce same output every time.
* Cause no side effects.

```js
function add(a, b) {
  return a + b;
}
```

### Impure Functions

* Depend on or modify external state.
* Side effects make results unpredictable.

```js
let total = 0;
function addToTotal(value) {
  total += value;
}
```

### How to Fix

Make pure by passing and returning data instead of mutating:

```js
function addToTotalPure(total, value) {
  return total + value;
}
```

### Benefits

* Easier to test.
* Easier to debug.
* Predictable and reusable.

### Example in Practice

**Impure:**

```js
const users = [];
function registerUser(name) {
  users.push(name);
}
```

**Pure:**

```js
function registerUserPure(users, name) {
  return [...users, name];
}
```

---

## 7. Real-World Practical Examples

### Example 1 — Reusable Data Transformer

```js
function transformUsers(users, transformer) {
  return users.map(transformer);
}
const uppercased = transformUsers(["brandon", "anna"], u => u.toUpperCase());
console.log(uppercased); // ['BRANDON', 'ANNA']
```

### Example 2 — Building a Custom Logger with Closure

```js
function createLogger(prefix) {
  return function(message) {
    console.log(`[${prefix}] ${message}`);
  };
}
const info = createLogger("INFO");
info("Server started"); // [INFO] Server started
```

### Example 3 — Configurable Tax Calculator

```js
function taxCalculator(rate) {
  return function(price) {
    return price + price * rate;
  };
}
const kenyaTax = taxCalculator(0.16);
console.log(kenyaTax(100)); // 116
```

### Example 4 — Functional Composition

```js
const multiplyBy2 = x => x * 2;
const add10 = x => x + 10;

function compose(f, g) {
  return x => f(g(x));
}
const multiplyAndAdd = compose(add10, multiplyBy2);
console.log(multiplyAndAdd(5)); // 20
```

### Example 5 — Rest Parameters + Reduce

```js
function average(...nums) {
  const total = nums.reduce((a, b) => a + b, 0);
  return total / nums.length;
}
console.log(average(10, 20, 30)); // 20
```

---

## 8. Quick Practice Questions

1. Create a function that reverses any array without mutating it.
2. Write a function `compose(f, g)` that chains two functions.
3. Use a closure to create a counter that counts only even numbers.
4. Implement a custom `map` using a for loop.
5. Convert an impure logging function into a pure one.

---

## 9. Cheat Sheet Summary

| Concept         | What It Does               | Common Mistake                        | Fix                               |
| --------------- | -------------------------- | ------------------------------------- | --------------------------------- |
| Parameters      | Inputs to functions        | Forgetting defaults                   | Use `param = value`               |
| Return          | Output value               | Missing `return`                      | Always return result              |
| Arrow Functions | Compact syntax             | Wrong `this`                          | Use normal function for methods   |
| Default Params  | Fallbacks                  | Passing `null` instead of `undefined` | Only undefined triggers default   |
| Rest Params     | Collect extra args         | Using before other params             | Must be last                      |
| Closures        | Remember variables         | Retaining memory unnecessarily        | Release refs if unused            |
| HOF             | Accept or return functions | Passing wrong callback                | Ensure callback signature correct |
| Pure Functions  | Predictable                | Changing external data                | Return new data                   |

---

## 10. Key Rule for Real Projects

Separate logic into:

* **Pure functions** for computation.
* **Impure functions** for input/output (fetch, database, UI).

This structure makes code predictable, testable, and clean.

---
