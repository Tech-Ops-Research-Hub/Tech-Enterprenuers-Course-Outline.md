# 5. 🎯 Final Project

---

### 🔹 Bringing It All Together

So far, you’ve learned:

* **Variables** (boxes that hold stuff).
* **Data Types** (numbers, text, true/false, lists).
* **Operators** (add, subtract, multiply, divide).
* **Control Flow** (if, else, loops, switch).
* **Functions** (recipes you can reuse).
* **Best Practices** (naming, comments, DRY, KISS).

Now it’s time to **mix them all together** into a real program! 🎉

---

### 🔹 Project Idea: A Simple “Mini Shop” 🛒

We will build a tiny shop program where:

1. The program **greets the user**.
2. Asks for their **name and age**.
3. Shows them a **menu of 3 items** (like apples, bananas, and oranges).
4. The user **chooses one item**.
5. The program **tells them the price**.
6. If they are under 10 years old → they get a **discount**.
7. The program says **goodbye** at the end.

---

### 🔹 Example in Python

```python
# Mini Shop Program

# Step 1: Function to greet the user
def greet(name):
    print("Hello " + name + "! Welcome to the Mini Shop.")

# Step 2: Function to show the menu
def show_menu():
    print("\nHere is our menu:")
    print("1. Apple - $2")
    print("2. Banana - $1")
    print("3. Orange - $3")

# Step 3: Function to get price
def get_price(choice):
    if choice == "1":
        return 2
    elif choice == "2":
        return 1
    elif choice == "3":
        return 3
    else:
        return 0

# --- Main Program ---
name = input("What is your name? ")
age = int(input("How old are you? "))

greet(name)
show_menu()

choice = input("Pick a number (1-3): ")
price = get_price(choice)

if price == 0:
    print("Sorry, that is not on the menu.")
else:
    # discount if under 10
    if age < 10:
        price = price - 1
        print("You get a $1 discount!")

    print("The final price is: $" + str(price))

print("Thank you for shopping, goodbye!")
```

---

### 🔹 Example in JavaScript

```javascript
// Mini Shop Program

// Step 1: Function to greet the user
function greet(name) {
    console.log("Hello " + name + "! Welcome to the Mini Shop.");
}

// Step 2: Function to show the menu
function showMenu() {
    console.log("\nHere is our menu:");
    console.log("1. Apple - $2");
    console.log("2. Banana - $1");
    console.log("3. Orange - $3");
}

// Step 3: Function to get price
function getPrice(choice) {
    if (choice === "1") {
        return 2;
    } else if (choice === "2") {
        return 1;
    } else if (choice === "3") {
        return 3;
    } else {
        return 0;
    }
}

// --- Main Program ---
let name = prompt("What is your name?");
let age = parseInt(prompt("How old are you?"));

greet(name);
showMenu();

let choice = prompt("Pick a number (1-3): ");
let price = getPrice(choice);

if (price === 0) {
    console.log("Sorry, that is not on the menu.");
} else {
    // discount if under 10
    if (age < 10) {
        price = price - 1;
        console.log("You get a $1 discount!");
    }
    console.log("The final price is: $" + price);
}

console.log("Thank you for shopping, goodbye!");
```

---

## ✅ Mini-Test (Quick Questions)

1. What is the purpose of the `greet` function in the project?
2. If a 9-year-old picks an apple (\$2), how much will they pay?
3. What happens if the user picks option `4`?
4. Why do we use functions instead of writing all the code in one place?

---

## 📝 Final Assignment & Deliverable

**Assignment:**

* Build your own **Mini Shop Program** (or invent your own theme like a “Mini Zoo” or “Mini Game”).
* Your program should:

  1. Use **variables** for user input (name, age, choice).
  2. Use **control flow** (`if/else`, loops, or switch).
  3. Use at least **2 functions**.
  4. Follow **best practices** (clear names, comments, DRY, KISS).
* Make sure the program works from start to finish.

**Deliverable:**

* Submit your code file:

  * Python → `final_project.py`
  * JavaScript → `final_project.js`
* Along with a short text file `README.md` explaining:

  * What your program does.
  * How to run it.

---

✅ Section 5 (Final Project) is complete.

---

🎉 Congratulations! You’ve now gone through:

* Variables, Data Types, Operators
* Control Flow (if, loops, switch)
* Functions & Scope
* Best Practices (Naming, Comments, DRY, KISS)
* Final Project

