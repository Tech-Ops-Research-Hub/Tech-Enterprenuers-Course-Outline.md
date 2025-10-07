
## 1. Introduction to JavaScript

### What is JavaScript?
JavaScript is a high-level, interpreted programming language that powers interactivity on the web.  
It runs in browsers and servers (Node.js), supports multiple paradigms (functional, OOP), and interacts with HTML/CSS to create dynamic interfaces.

**Core traits:**
- Interpreted, dynamically typed, single-threaded
- Event-driven, prototype-based
- Supports asynchronous programming

**Common uses:**
- Web interactivity (frontend)
- APIs and backend logic (Node.js)
- Cross-platform apps (React Native, Electron)

---

### History and Evolution (ES5 → ES2025)
- **1995** – Created by Brendan Eich (Netscape)
- **1997** – ECMAScript standard introduced (ES1)
- **2009 (ES5)** – Added `forEach`, `map`, JSON support, strict mode
- **2015 (ES6)** – Introduced `let`, `const`, classes, arrow functions, promises, modules
- **2016–2025** – Yearly ECMAScript updates:
  - Async/Await (ES2017)
  - Optional chaining `?.` (ES2020)
  - Nullish coalescing `??` (ES2020)
  - Top-level await (ES2022)
  - Records/Tuples (proposed ES2025)

---

### How JavaScript Works (Runtime, Engine, Event Loop)

**Engine:** Converts JS code → bytecode → machine instructions  
Examples:  
- Chrome: **V8**  
- Firefox: **SpiderMonkey**  
- Safari: **JavaScriptCore**

**Event Loop:**
- Manages asynchronous tasks via **Call Stack**, **Web APIs**, **Callback Queue**, and **Microtask Queue**.  
- Ensures non-blocking execution.

---

### Setting Up the Development Environment
1. **Install Node.js** → [nodejs.org](https://nodejs.org)  
   Verify with `node -v`.
2. **Editor:** Use VS Code with ESLint + Prettier.
3. **Browser Console:** Test snippets (Ctrl + Shift + J).
4. **Online Platforms:** CodePen, JSFiddle, Replit.

---

### Running JavaScript in Browser and Node.js
**Browser:**
```html
<script>
  console.log("Running in browser");
</script>
````

**Node.js:**

```bash
node app.js
```

---

### 🧠 Quick Quiz – Introduction

1. Who created JavaScript and in what year?
2. What is the purpose of the Event Loop?
3. Name two differences between Node.js and browser JavaScript environments.
4. What does ECMAScript refer to?
5. Give two new features introduced in ES6.

---

## 2. Core Fundamentals

### Variables (`let`, `const`, `var`)

| Keyword | Scope    | Reassignment | Redeclaration | Hoisted         |
| ------- | -------- | ------------ | ------------- | --------------- |
| `var`   | Function | ✅            | ✅             | Yes (undefined) |
| `let`   | Block    | ✅            | ❌             | No              |
| `const` | Block    | ❌            | ❌             | No              |

Best practice:

* Use `const` by default.
* Use `let` when reassignment is required.
* Avoid `var` for modern code.

---

### Data Types

**Primitive Types:**
`String`, `Number`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`

**Reference Types:**
`Object`, `Array`, `Function`

```js
typeof "hello"; // string
typeof 42;      // number
typeof null;    // object
```

---

### Type Conversion and Coercion

**Explicit Conversion:**

```js
Number("10");   // 10
String(50);     // "50"
Boolean(0);     // false
```

**Implicit (Coercion):**

```js
"5" + 1; // "51"
"5" - 1; // 4
```

---

### Operators and Expressions

* Arithmetic: `+ - * / % **`
* Comparison: `== != === !== > < >= <=`
* Logical: `&& || !`
* Assignment: `= += -=`
* Ternary: `condition ? true : false`
* Nullish Coalescing: `??`

---

### Comments and Code Style

* Single-line: `//`
* Multi-line: `/* ... */`
* Use consistent indentation and variable naming.
* Use **Prettier** or **ESLint** for formatting.

---

### 🧩 Practice Questions – Fundamentals

1. What is the difference between `let` and `const`?
2. What is the output of `typeof null`?
3. Convert `"50"` into a number without using `parseInt()`.
4. What is the result of `"10" - 5 + "5"`?
5. Why is `var` discouraged in modern JavaScript?

---

### 🧠 Quiz – Core Fundamentals

1. Which keyword has function-level scope?
   a) let
   b) const
   c) var
   d) none
2. What will `Number(false)` return?
   a) 0
   b) 1
   c) undefined
   d) NaN
3. What is `2 + "2" - 2`?
   a) 22
   b) 2
   c) 20
   d) NaN
4. Which operator checks both value and type equality?
   a) `==`
   b) `===`
   c) `=`
   d) `!=`

---

## 3. Control Flow

### Conditional Statements (`if`, `else`, `switch`)

**if / else example:**

```js
if (age >= 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

**switch example:**

```js
switch (color) {
  case "red":
    console.log("Stop");
    break;
  case "green":
    console.log("Go");
    break;
  default:
    console.log("Invalid color");
}
```

---

### Loops (`for`, `while`, `do...while`)

**for loop:**

```js
for (let i = 1; i <= 3; i++) console.log(i);
```

**while loop:**

```js
let i = 0;
while (i < 3) {
  console.log(i);
  i++;
}
```

**do...while loop:**

```js
let x = 0;
do {
  console.log(x);
  x++;
} while (x < 2);
```

---

### `break` and `continue`

* **break:** exits loop immediately.
* **continue:** skips to next iteration.

```js
for (let i = 0; i < 5; i++) {
  if (i === 2) continue;
  if (i === 4) break;
  console.log(i);
}
```

Output: `0 1 3`

---

### Error Handling (`try...catch`, `throw`)

**try...catch:**

```js
try {
  let result = riskyOperation();
} catch (err) {
  console.log("Error:", err.message);
} finally {
  console.log("Execution completed");
}
```

**Custom Error:**

```js
if (age < 0) throw new Error("Invalid age");
```

---

### 🧩 Practice Questions – Control Flow

1. What is the difference between `break` and `continue`?
2. Write a loop that prints numbers 1–10 but skips even numbers.
3. What will happen if an error occurs inside `try` without a `catch` block?
4. How can you simulate multiple conditions using `switch`?
5. Why is `finally` block used?

---

### 🧠 Quiz – Control Flow

1. What does the following output?

   ```js
   let x = 0;
   while (x < 3) {
     if (x === 1) break;
     console.log(x);
     x++;
   }
   ```

   a) 0
   b) 0 1
   c) 0 1 2
   d) none

2. In which case is the `finally` block executed?
   a) Only if `try` succeeds
   b) Only if an error occurs
   c) Always
   d) Never

3. What is wrong with this code?

   ```js
   switch (num) {
     case 1:
       console.log("One");
     case 2:
       console.log("Two");
   }
   ```

   a) Missing `break` statements
   b) Missing `default`
   c) Invalid syntax
   d) None

4. Identify the output:

   ```js
   for (let i = 0; i < 3; i++) {
     if (i === 1) continue;
     console.log(i);
   }
   ```

   a) 0 1 2
   b) 0 2
   c) 1 2
   d) none

---

✅ **End of Module Assessment (Covering Sections 1–3)**

1. Explain the role of the JavaScript engine and event loop.
2. Compare `var`, `let`, and `const` in scope and behavior.
3. Write a function that checks if a number is even using conditional statements.
4. Identify three ES6+ features that modernized JavaScript.
5. Write a `try...catch` example that safely handles division by zero.

---

```
```
