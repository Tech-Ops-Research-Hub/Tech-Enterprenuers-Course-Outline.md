# 2. Control Flow (If, Loops, Switch)

---

### 🔹 What is Control Flow?

Imagine you are playing a game.

* If you have **candy**, you eat it.
* If you don’t have candy, you go ask your mom.

That’s **control flow**: it tells the computer **what to do next, depending on the situation**.

---

### 🔹 IF Statements

An **if statement** is like making a choice.

* "If it’s raining, take an umbrella."
* "If it’s sunny, wear sunglasses."

#### Python Example:

```python
is_raining = True

if is_raining:
    print("Take an umbrella")
else:
    print("Wear sunglasses")
```

#### JavaScript Example:

```javascript
let isRaining = true;

if (isRaining) {
    console.log("Take an umbrella");
} else {
    console.log("Wear sunglasses");
}
```

---

### 🔹 ELSE IF (More than Two Choices)

What if there are many choices?

* If it’s raining → umbrella.
* If it’s sunny → sunglasses.
* If it’s snowy → wear a coat.

#### Python:

```python
weather = "snowy"

if weather == "rainy":
    print("Take an umbrella")
elif weather == "sunny":
    print("Wear sunglasses")
elif weather == "snowy":
    print("Wear a coat")
else:
    print("Stay inside")
```

#### JavaScript:

```javascript
let weather = "snowy";

if (weather === "rainy") {
    console.log("Take an umbrella");
} else if (weather === "sunny") {
    console.log("Wear sunglasses");
} else if (weather === "snowy") {
    console.log("Wear a coat");
} else {
    console.log("Stay inside");
}
```

---

### 🔹 Loops (Doing Things Again and Again)

Loops are like when your teacher says:
"Clap 5 times!" 👏👏👏👏👏

Instead of writing `print("Clap")` five times, you can **loop**.

#### Python (for loop):

```python
for i in range(5):
    print("Clap")
```

#### JavaScript (for loop):

```javascript
for (let i = 0; i < 5; i++) {
    console.log("Clap");
}
```

---

### 🔹 While Loops

While loops mean "keep going **while something is true**."

Example:
"Keep eating candy while there’s still candy left."

#### Python:

```python
candy = 3

while candy > 0:
    print("Eat candy")
    candy -= 1   # take 1 candy away
```

#### JavaScript:

```javascript
let candy = 3;

while (candy > 0) {
    console.log("Eat candy");
    candy--;  // take 1 candy away
}
```

---

### 🔹 Switch (Many Choices, but Neater)

Sometimes, checking many choices with `if` feels messy.
Switch is like a menu at a restaurant.

#### JavaScript Example:

```javascript
let fruit = "apple";

switch (fruit) {
    case "apple":
        console.log("You picked an apple");
        break;
    case "banana":
        console.log("You picked a banana");
        break;
    case "orange":
        console.log("You picked an orange");
        break;
    default:
        console.log("I don’t know that fruit");
}
```

👉 Note: Python doesn’t have a real `switch` (but you can use `if/elif`).

---

## ✅ Mini-Test (Quick Questions)

1. What does an **if statement** do?
2. Write a Python program that checks if your age is **above 10**.

   * If yes → print `"You are older than 10"`.
   * If no → print `"You are 10 or younger"`.
3. In JavaScript, make a loop that prints `"Jump!"` 3 times.
4. What happens if you forget the `break;` in a JavaScript switch?

---

## 📝 Assignment & Deliverable

**Assignment:**

* Write a program where:

  1. Ask the user to choose their favorite color (red, blue, or green).
  2. Use **if/elif (Python)** or **if/switch (JavaScript)** to print:

     * "You picked red"
     * "You picked blue"
     * "You picked green"
     * "I don’t know that color" (for other inputs).
  3. Add a loop that prints `"I like coding"` 5 times.

**Deliverable:**

* Submit your code file:

  * Python → `Control Flow.py`
  * JavaScript → `Control Flow.js`

---
