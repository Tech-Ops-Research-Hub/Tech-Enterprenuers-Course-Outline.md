
# 📘 Parameters and Return Values
---

## 🧩 Concept Overview

### **Function Input → Output Model**

Every function transforms **input (parameters)** into **output (return value)**.

- **Parameters**: Placeholders for data the function expects.  
- **Arguments**: Actual values supplied when the function is called.  
- **Return Value**: The result that exits the function and can be stored or reused.

```js
function add(a, b) {
  return a + b;
}

let result = add(5, 3); // a=5, b=3
console.log(result);    // 8
````

---

## ⚙️ First Principles Breakdown

1. A function without parameters can’t adapt to different inputs.
2. A function without a return value performs work but doesn’t produce results.
3. Combining both gives a **reusable computational unit**.

Example:

```js
function square(x) {
  return x * x;
}
console.log(square(2)); // 4
console.log(square(10)); // 100
```

---

## 🧱 Parameter Types

| Type             | Description                            | Example                          |
| ---------------- | -------------------------------------- | -------------------------------- |
| **Required**     | Must be passed                         | `function greet(name)`           |
| **Default**      | Has fallback if missing                | `function greet(name = "Guest")` |
| **Rest**         | Collects multiple inputs into an array | `function sum(...nums)`          |
| **Destructured** | Breaks down object/array inputs        | `function display({name, age})`  |

### Examples

**1. Required Parameters**

```js
function greet(name) {
  return "Hello " + name;
}
console.log(greet("Alice"));
```

**2. Default Parameters**

```js
function greet(name = "Guest") {
  return "Hello " + name;
}
console.log(greet()); // Hello Guest
```

**3. Rest Parameters**

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

**4. Destructured Parameters**

```js
function showUser({ name, age }) {
  return `${name} is ${age} years old.`;
}
console.log(showUser({ name: "John", age: 25 }));
```

---

## 🔁 Return Values

* `return` ends the function and outputs a value.
* Without `return`, the function gives `undefined`.

### Example

```js
function multiply(a, b) {
  return a * b;
}
let result = multiply(4, 5);
console.log(result); // 20
```

### Function Without Return

```js
function logResult(a, b) {
  console.log(a * b);
}
let output = logResult(2, 3);
console.log(output); // undefined
```

---

## ⚗️ Pure vs Impure Functions

| Type       | Description                  | Example                         |
| ---------- | ---------------------------- | ------------------------------- |
| **Pure**   | Output depends only on input | `function add(a,b){return a+b}` |
| **Impure** | Depends on external state    | `let c=0; function inc(){c++}`  |

Pure functions simplify debugging and testing.

---

## 🧮 Returning Multiple Values

Functions can return multiple results using objects or arrays.

```js
function calculate(a, b) {
  return {
    sum: a + b,
    product: a * b
  };
}

let result = calculate(2, 3);
console.log(result.sum);     // 5
console.log(result.product); // 6
```

---

## 🧠 Best Practices

1. Keep parameters minimal.
2. Define defaults when possible.
3. Avoid returning mixed data types.
4. Keep functions pure and predictable.
5. Use destructuring when parameters grow complex.

---

## 💻 Real-World Example

```js
function processOrder(order, discountRate = 0.1) {
  const { price, quantity } = order;

  const total = price * quantity;
  const discount = total * discountRate;
  const finalTotal = total - discount;

  return { total, discount, finalTotal };
}

let orderDetails = processOrder({ price: 100, quantity: 5 });
console.log(orderDetails);
// { total: 500, discount: 50, finalTotal: 450 }
```

---

## 🧩 Mini Tests

### **Test 1**

Write a function `divide(a, b)` that:

* Returns `"Cannot divide by zero"` if `b` is 0.
* Else returns the division result.

### **Test 2**

Write a function `greetUser(name, age = 18)` that returns:
`"Welcome <name>, age <age>"`.

### **Test 3**

Create a function `analyzeNumbers(...nums)` that returns:

```js
{ min, max, average }
```

### **Test 4**

Write a function that takes `{ name, score }` and returns:

* `"Excellent"` if score > 80
* `"Good"` if 50–80
* `"Poor"` otherwise

### **Test 5**

Write a function `transform(x)` that:

1. Doubles the input.
2. Squares the result.
3. Returns the final value.

---

## 📘 Summary

| Concept          | Description                 |
| ---------------- | --------------------------- |
| Parameters       | Define expected inputs      |
| Arguments        | Actual values passed        |
| Return           | Defines function output     |
| Default Params   | Provide fallback values     |
| Rest Params      | Handle variable inputs      |
| Pure Functions   | Deterministic output        |
| Impure Functions | Dependent on external state |

---

## 🧾 License

This project is open-sourced under the MIT License.

