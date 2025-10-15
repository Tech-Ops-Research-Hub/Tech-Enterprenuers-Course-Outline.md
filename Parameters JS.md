
# Parameters and Return Values

## Overview
In JavaScript, **parameters** and **return values** define how functions receive input and produce output. Understanding them is crucial for writing reusable and predictable code.

---

## 1. Parameters

### Definition
Parameters are **variables** listed in a function’s definition. They act as **placeholders** for the values (arguments) that will be passed when the function is called.

```js
function add(a, b) {
  return a + b;
}
````

Here:

* `a` and `b` are **parameters**.
* They represent values supplied during function execution.

### Types of Parameters

#### a. Required Parameters

Must be provided when calling the function.

```js
function greet(name) {
  console.log("Hello, " + name);
}

greet("Brandon"); // Output: Hello, Brandon
```

#### b. Default Parameters

Used when no argument is provided.

```js
function greet(name = "Guest") {
  console.log("Hello, " + name);
}

greet(); // Output: Hello, Guest
```

#### c. Rest Parameters

Capture multiple arguments into an array.

```js
function sum(...numbers) {
  return numbers.reduce((acc, val) => acc + val, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
```

#### d. Destructured Parameters

Used for objects or arrays.

```js
function displayUser({ name, age }) {
  console.log(`${name} is ${age} years old`);
}

displayUser({ name: "Alice", age: 25 }); // Output: Alice is 25 years old
```

---

## 2. Arguments vs Parameters

* **Parameters:** variables in the function definition.
* **Arguments:** actual values passed to those parameters when the function is called.

```js
function multiply(x, y) { // x, y → parameters
  return x * y;
}

multiply(4, 5); // 4, 5 → arguments
```

---

## 3. Return Values

### Definition

The **return value** is the output produced when a function finishes executing. Defined using the `return` keyword.

```js
function square(num) {
  return num * num;
}

let result = square(4); // result = 16
```

### Characteristics

* The `return` statement **ends** the function execution immediately.
* A function without `return` returns `undefined`.

```js
function noReturn() {
  let a = 10;
}
console.log(noReturn()); // undefined
```

---

## 4. Multiple Return Values

A function can return multiple values via arrays or objects.

**Using Arrays**

```js
function getCoordinates() {
  return [10, 20];
}

const [x, y] = getCoordinates();
console.log(x, y); // 10 20
```

**Using Objects**

```js
function getUser() {
  return { name: "Brandon", age: 30 };
}

const { name, age } = getUser();
console.log(name, age); // Brandon 30
```

---

## 5. Return Values and Control Flow

The `return` statement stops further execution.

```js
function check(num) {
  if (num > 0) return "Positive";
  if (num < 0) return "Negative";
  return "Zero";
}

console.log(check(5)); // Positive
```

---

## 6. Best Practices

* Keep parameter lists short (prefer objects for many parameters).
* Use descriptive parameter names.
* Always return consistent types.
* Use default parameters instead of checking for `undefined`.
* Document both parameters and return values in code comments.

```js
/**
 * Calculates total price with tax.
 * @param {number} price - Base price.
 * @param {number} taxRate - Tax percentage.
 * @returns {number} Total price including tax.
 */
function calculateTotal(price, taxRate = 0.1) {
  return price + price * taxRate;
}
```

---

## 7. Common Pitfalls

| Issue                 | Description                              | Example                                                                    |
| --------------------- | ---------------------------------------- | -------------------------------------------------------------------------- |
| Missing return        | Function doesn’t output anything         | `function f(x) { x + 1 }` → `undefined`                                    |
| Wrong parameter order | Arguments mapped incorrectly             | `function divide(a, b) { return a/b }` → `divide(2, 10)` ≠ `divide(10, 2)` |
| Mutating parameters   | Changing input objects inside a function | Avoid side effects                                                         |

---

## 8. Advanced Example

```js
function processOrder({ items, taxRate = 0.08 }) {
  const subtotal = items.reduce((sum, item) => sum + item.price, 0);
  const total = subtotal + subtotal * taxRate;
  return { subtotal, total };
}

const order = {
  items: [
    { name: "Headphones", price: 50 },
    { name: "Keyboard", price: 80 }
  ],
  taxRate: 0.1
};

const { subtotal, total } = processOrder(order);
console.log(subtotal, total); // 130 143
```

---

## 9. Test Questions

1. Define **parameters** and **arguments** and explain the difference.
2. What happens when a function does not include a `return` statement?
3. Write a function with default and rest parameters to calculate average scores.
4. How can multiple values be returned from one function? Show both array and object methods.
5. Explain why mutating parameters inside functions is discouraged.
6. Implement a function `calculateBMI(weight, height)` that returns both BMI value and category.
7. How does destructuring in parameters simplify function usage? Provide an example.
8. What is the purpose of default parameters in function definitions?
9. Demonstrate control flow using `return` in conditional branches.
10. Comment your code using JSDoc to describe parameters and return values for a simple function.

---

```
```
