# 3. Functions & Scope

---

### 🔹 What is a Function?

Imagine you are baking cookies. 🍪

* Every time, you follow the **same recipe**.
* Instead of writing the recipe on the board 100 times, you just say:
  👉 “Use the cookie recipe!”

That’s what a **function** is:

* A **recipe** (instructions).
* You can **call it** anytime.
* You can **reuse** it again and again.

---

### 🔹 Writing a Function

#### Python Example:

```python
def say_hello():
    print("Hello, friend!")
```

Now, to use it:

```python
say_hello()  # prints Hello, friend!
```

#### JavaScript Example:

```javascript
function sayHello() {
    console.log("Hello, friend!");
}

sayHello(); // prints Hello, friend!
```

---

### 🔹 Functions with Input (Parameters)

A recipe sometimes needs **ingredients**.
Like: “Make cookies with chocolate chips.” 🍫

#### Python:

```python
def greet(name):
    print("Hello, " + name)

greet("Sam")   # Hello, Sam
greet("Lily")  # Hello, Lily
```

#### JavaScript:

```javascript
function greet(name) {
    console.log("Hello, " + name);
}

greet("Sam");   // Hello, Sam
greet("Lily");  // Hello, Lily
```

---

### 🔹 Functions with Output (Return)

Sometimes a recipe **gives something back**.
Like: “Make 10 cookies” → you get 10 cookies.

#### Python:

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)   # 5
```

#### JavaScript:

```javascript
function add(a, b) {
    return a + b;
}

let result = add(2, 3);
console.log(result);  // 5
```

---

### 🔹 Scope (Where Things Belong)

Imagine you have toys in your room.

* Only **you** can play with them (private).
* But toys in the **living room** are for everyone (public).

In coding, **scope** decides **where variables can be used**.

#### Python Example:

```python
def my_room():
    toy = "car"  # private toy
    print(toy)

my_room()
# print(toy)   # ❌ error: toy is not known outside
```

#### JavaScript Example:

```javascript
function myRoom() {
    let toy = "car";  // private toy
    console.log(toy);
}

myRoom();
// console.log(toy);  // ❌ error: toy is not known outside
```

---

## ✅ Mini-Test (Quick Questions)

1. What is a function?
2. In Python, write a function `say_goodbye()` that prints `"Goodbye!"`.
3. In JavaScript, write a function `double(x)` that returns `x * 2`.
4. What is **scope** in programming?

---

## 📝 Assignment & Deliverable

**Assignment:**

* Write a function-based program:

  1. Make a function `introduce(name, age)` that prints:

     * `"Hi, my name is NAME and I am AGE years old."`
  2. Make a function `multiply(a, b)` that returns the product.
  3. Use both functions with your own values.

**Deliverable:**

* Submit your code file:

  * Python → `assignment3.py`
  * JavaScript → `assignment3.js`

---
