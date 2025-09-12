# 4. Best Practices (Naming, Comments, DRY/KISS)

---

### 🔹 What Are Best Practices?

Best practices are like **good habits** when you brush your teeth. 🪥

* You brush every day.
* You use toothpaste.
* You don’t skip.

In coding, best practices mean **writing code in a clean and smart way** so everyone can understand and use it.

---

### 🔹 Naming Things (Variables, Functions)

Imagine if everyone in your school was named “Kid.” Confusing, right?
That’s why in coding we give things **clear names**.

✅ Good:

```python
age = 10
favorite_color = "blue"
```

❌ Bad:

```python
a = 10
fc = "blue"
```

Same in JavaScript:

```javascript
let age = 10; 
let favoriteColor = "blue";
```

👉 Rule: **Names should tell what’s inside the box.**

---

### 🔹 Comments (Notes for Humans)

Sometimes your teacher writes notes in your book, not for the computer, but **for you**.
That’s what comments are — notes in your code for humans to understand.

#### Python:

```python
# This is my age
age = 10
```

#### JavaScript:

```javascript
// This is my age
let age = 10;
```

👉 Computers ignore comments. They are just **sticky notes** for people.

---

### 🔹 DRY (Don’t Repeat Yourself)

Imagine writing your name on every page of your notebook 100 times. Tiring! 😩
Instead, you write it once and tell your friend: “Copy it everywhere.”

That’s **DRY** → Don’t Repeat Yourself.

* If you write the same code again and again → put it in a function.

#### Bad:

```python
print("Hello Sam")
print("Hello Sam")
print("Hello Sam")
```

#### Good:

```python
def greet():
    print("Hello Sam")

greet()
greet()
greet()
```

---

### 🔹 KISS (Keep It Simple, Silly)

When you explain a game to your little brother, you don’t use big words. You say it **simply**.

That’s **KISS** → Keep It Simple, Silly.

* Write code that is short and clear.
* Don’t make it too complicated.

Example:
❌ Bad:

```python
if (is_hungry == True and is_thirsty == False and has_money == True):
    print("Buy a sandwich")
```

✅ Good:

```python
if is_hungry and has_money:
    print("Buy a sandwich")
```

---

## ✅ Mini-Test (Quick Questions)

1. Why is it important to give variables clear names?
2. Write a Python comment that says: `"This is my pet's name"`.
3. What does DRY stand for?
4. What does KISS mean in coding?

---

## 📝 Assignment & Deliverable

**Assignment:**

* Write a program (Python or JavaScript) that:

  1. Has at least **3 variables** with clear names.
  2. Uses **comments** to explain each part.
  3. Creates a **function** instead of repeating code.
  4. Keeps everything **simple and easy to read**.

**Deliverable:**

* Submit your code file:

  * Python → `assignment4.py`
  * JavaScript → `assignment4.js`

---

