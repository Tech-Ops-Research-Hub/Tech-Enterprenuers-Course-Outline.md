# 📘 Python & JavaScript Basics – A Comparative Learning Guide

Welcome to the **Python & JavaScript Basics**!

This guide compares **Python and JavaScript** side by side so you can build a strong foundation in programming.
Each section includes **examples** and **test questions (5+ each)** to check your understanding.

---

## 🚀 Why Learn Python and JavaScript Together?

* **Python** → beginner-friendly, great for AI, data, backend.
* **JavaScript** → runs everywhere, essential for web development.

By mastering both, you’ll:

* Understand different coding styles.
* Easily switch between languages.
* Be ready for real-world projects and technical interviews.

---

## 📖 Table of Contents

1. [Syntax Comparison](#-syntax-comparison-python-vs-javascript)
2. [Input/Output](#-inputoutput)
3. [Error Handling & Debugging](#-error-handling--debugging)
4. [Writing Clean Code](#-writing-clean-code)
5. [Final Test Questions](#-final-test-questions)
6. [Additional Resources](#-additional-resources)
7. [Contribution](#-contribution)

---

## 📝 Syntax Comparison (Python vs JavaScript)

### Variables

```python
# Python
x = 10
name = "Alice"
```

```javascript
// JavaScript
let x = 10;
const name = "Alice";
```

### Conditionals

```python
if x > 5:
    print("Greater")
else:
    print("Smaller or Equal")
```

```javascript
if (x > 5) {
    console.log("Greater");
} else {
    console.log("Smaller or Equal");
}
```

### Loops

```python
for i in range(5):
    print(i)
```

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

---

### 🔹 Test Questions (Syntax)

1. Convert this Python loop into JavaScript:

   ```python
   for i in range(1, 6):
       print(i * 2)
   ```

2. Write the Python equivalent of this JavaScript code:

   ```javascript
   for (let i = 10; i >= 1; i--) {
       console.log(i);
   }
   ```

3. In JavaScript, what’s the difference between:

   * `let`
   * `const`
   * `var`

4. Predict the output:

   ```python
   x = 5
   if x == "5":
       print("Equal")
   else:
       print("Not Equal")
   ```

   👉 How would this behave differently in JavaScript?

5. Write a Python `while` loop that prints numbers from 1 to 10.

6. Write a JavaScript `for` loop that prints only multiples of 3 between 1 and 20.

---

## 📥 Input/Output

### Python

```python
name = input("Enter your name: ")
print(f"Hello, {name}!")
```

### JavaScript (Browser)

```javascript
let name = prompt("Enter your name:");
console.log(`Hello, ${name}!`);
```

### JavaScript (Node.js)

```javascript
const readline = require("readline").createInterface({
  input: process.stdin,
  output: process.stdout
});

readline.question("Enter your name: ", (name) => {
  console.log(`Hello, ${name}!`);
  readline.close();
});
```

---

### 🔹 Test Questions (Input/Output)

1. Write a Python program that:

   * Asks for two numbers.
   * Prints their product.

2. Do the same in JavaScript (Node.js).

3. Modify the Python program so it accepts strings and prints:
   `"Hello, <name>. Welcome!"`

4. In JavaScript, what’s the difference between `prompt()` (browser) and `readline` (Node.js)?

5. Write a Python program that keeps asking for input until the user types `"exit"`.

6. Write a JavaScript program that asks for a number and prints `"Even"` or `"Odd"`.

---

## 🛠️ Error Handling & Debugging

### Python

```python
try:
    num = int(input("Enter a number: "))
    print(10 / num)
except ZeroDivisionError:
    print("❌ Cannot divide by zero!")
except ValueError:
    print("❌ Invalid input!")
```

### JavaScript

```javascript
try {
    let num = parseInt(prompt("Enter a number:"));
    console.log(10 / num);
} catch (error) {
    console.error("❌ Error:", error.message);
}
```

---

### 🔹 Test Questions (Error Handling)

1. What error does Python raise when you divide by zero?

   * Write the exact exception name.

2. In JavaScript, what happens if you do `10 / 0`?

3. Modify this Python program to also handle **negative numbers** as invalid input:

   ```python
   num = int(input("Enter a number: "))
   print(10 / num)
   ```

4. Write a JavaScript program that catches an error if the user enters `"abc"` instead of a number.

5. Debug this broken Python code and fix it:

   ```python
   try:
       x = int("ten")
       print(100 / x)
   except:
       print("Something went wrong")
   ```

   👉 What’s the actual error?

6. In JavaScript, write a `try-catch` that specifically catches `ReferenceError`.

---

## ✨ Writing Clean Code

### Principles

* ✅ Descriptive variable names.
* ✅ Short, focused functions.
* ✅ DRY (Don’t Repeat Yourself).
* ✅ Follow style guides (PEP 8, Airbnb).

### Example

```python
# Python
def calculate_area(radius):
    return 3.14 * radius ** 2
```

```javascript
// JavaScript
function calculateArea(radius) {
    return Math.PI * radius ** 2;
}
```

---

### 🔹 Test Questions (Clean Code)

1. Refactor this messy Python code into clean code:

   ```python
   def f(a,b):return a+b
   ```

2. Write a JavaScript function `isPrime(n)` that checks if a number is prime (clean version).

3. Python: Write a clean function `greet_user(name)` that returns `"Hello, <name>!"`.

4. JavaScript: Write a function `factorial(n)` using recursion, following clean code principles.

5. Explain why using `x1`, `x2`, `x3` as variable names is **bad practice**.

6. Python: Rewrite this into clean code with proper naming:

   ```python
   def c(r,h):return 3.14*r*r*h
   ```

   👉 Hint: It’s the formula for cylinder volume.

---

## 📚 Additional Resources

* [Python Official Documentation](https://docs.python.org/3/tutorial/)
* [JavaScript Guide (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
* [PEP 8 – Python Style Guide](https://peps.python.org/pep-0008/)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
---



Learning both **Python** and **JavaScript** makes you a versatile developer.
Use the **test questions** to practice actively — don’t just read, but **write and run the code**.

---

