# 🐍⚡ Python & JavaScript Basics

A beginner-friendly guide comparing **Python vs JavaScript syntax**, with examples of **input/output, error handling, debugging, and clean code practices**. Includes quizzes, test questions, and projects to practice hands-on.

---

## 📚 Table of Contents

* [Syntax Comparison](#-syntax-comparison)
* [Input & Output](#-input--output)
* [Error Handling & Debugging](#-error-handling--debugging)
* [Writing Clean Code](#-writing-clean-code)
* [Mini-Test](#-mini-test)
* [Quiz](#-quiz)
* [Projects](#-projects)
* [Next Steps](#-next-steps)

---

## 🔄 Syntax Comparison

| Concept           | Python 🐍                                             | JavaScript ⚡                                                                                         |
| ----------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Hello World**   | `print("Hello, World!")`                              | `console.log("Hello, World!");`                                                                      |
| **Variables**     | `x = 5`                                               | `let x = 5;` / `const x = 5;`                                                                        |
| **Conditionals**  | `if x > 10:` <br> `elif x == 10:` <br> `else:`        | `if (x > 10) { } else if (x === 10) { } else { }`                                                    |
| **Loops**         | `for i in range(5):` <br> `while condition:`          | `for (let i = 0; i < 5; i++) { }` <br> `while (condition) { }`                                       |
| **Functions**     | `python\ndef greet(name):\n    return "Hi " + name\n` | `javascript\nfunction greet(name) { return "Hi " + name; }\nconst greet = (name) => "Hi " + name;\n` |
| **Lists/Arrays**  | `my_list = [1, 2, 3]`                                 | `let myArray = [1, 2, 3];`                                                                           |
| **Objects/Dicts** | `person = {"name": "Sam", "age": 25}`                 | `let person = {name: "Sam", age: 25};`                                                               |

---

## 🖥️ Input & Output

<details>
<summary>Python Example 🐍</summary>

```python
name = input("Enter your name: ")
print("Hello,", name)
```

</details>

<details>
<summary>JavaScript Example ⚡</summary>

```javascript
let name = prompt("Enter your name:");
console.log("Hello, " + name);
```

</details>

---

## ⚠️ Error Handling & Debugging

<details>
<summary>Python Example 🐍</summary>

```python
try:
    number = int(input("Enter a number: "))
    print(10 / number)
except ValueError:
    print("Please enter a valid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

</details>

<details>
<summary>JavaScript Example ⚡</summary>

```javascript
try {
    let number = parseInt(prompt("Enter a number:"));
    console.log(10 / number);
} catch (error) {
    console.log("Something went wrong:", error.message);
}
```

</details>

---

## ✨ Writing Clean Code

* ✅ Use **meaningful variable names**
* ✅ Keep functions **small & single-purpose**
* ✅ Add **comments & docstrings**
* ✅ Follow style guides:

  * [PEP 8 (Python)](https://peps.python.org/pep-0008/)
  * [Airbnb JS Guide](https://github.com/airbnb/javascript)
* ✅ Avoid **magic numbers** → use constants
* ✅ Prefer **readable code** over clever code

---

## 🔹 Mini-Test

### Q1. Syntax Conversion

Rewrite this Python loop in **JavaScript**:

```python
for i in range(3):
    print("Python vs JS")
```

---

### Q2. Debugging

What’s wrong with this Python code?

```python
x = 10
if x = 5:
    print("Equal")
```

---

### Q3. Input/Output

Write a program in **both Python and JavaScript** that asks for two numbers and prints their sum.

---

## 📝 Quiz

1. Which language enforces **indentation** for code blocks?

   * a) Python
   * b) JavaScript
   * c) Both

2. What is the output of:

   ```javascript
   console.log(2 + "2");
   ```

   * a) 4
   * b) 22
   * c) Error

3. In Python, dividing by zero raises:

   * a) SyntaxError
   * b) ZeroDivisionError
   * c) TypeError

---

## 🚀 Projects

### 📌 Project 1: Calculator

* Create a console calculator in **both Python & JS**.
* Support: +, -, ×, ÷
* Handle errors (invalid input, divide by zero).

---

### 📌 Project 2: To-Do List (Console-based)

* Features:

  * Add tasks
  * View tasks
  * Delete tasks

---

### 📌 Project 3: Number Guessing Game

* Program generates a random number.
* User guesses until correct.
* Provide hints: “too high” / “too low”.

---

## ✅ Next Steps

* Write **the same programs in both Python & JavaScript**.
* Practice debugging error messages.
* Move to **intermediate topics**:

  * Functions & scope
  * File handling
  * Async programming (in JS)

---
