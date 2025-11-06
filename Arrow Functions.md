
# Arrow Functions

Arrow functions are just a shorter way to write functions.

They remove the `function` keyword and reduce extra syntax.

Example:
```js
const add = (a, b) => a + b
````

Meaning: take `a` and `b`, return `a + b`.

---

## 1. When You Have One Line

If the function has only one step, you do not write `return`.

```js
const double = x => x * 2
```

Input: `x`
Output: `x * 2`

---

## 2. When You Have More Than One Line

You must use `{}` and write `return`.

```js
const work = (x) => {
  const y = x + 1
  return y
}
```

---

## 3. Returning an Object

Objects must be wrapped in parentheses.
Otherwise, JavaScript thinks you are starting a code block.

Correct:

```js
const person = () => ({ name: "Sam" })
```

Incorrect:

```js
const person = () => { name: "Sam" } // returns nothing
```

---

## 4. Arrow Functions and `this`

Arrow functions **do not make their own `this`**.
They use `this` from where they were written.

This works:

```js
function Counter() {
  this.count = 0

  setInterval(() => {
    this.count++
  }, 1000)
}
```

The arrow function uses `this` from `Counter`.

---

## 5. Do Not Use Arrow Functions for Object Methods

If a function inside an object needs `this`, use normal function syntax.

Wrong:

```js
const obj = {
  x: 5,
  getX: () => this.x
}
```

This does **not** refer to `obj`.

Correct:

```js
const obj = {
  x: 5,
  getX() { return this.x }
}
```

---

## 6. Arrow Functions Do Not Have `arguments`

Use rest parameters instead.

```js
const f = (...args) => args
```

---

## 7. Arrow Functions Cannot Be Used With `new`

They cannot create objects as constructors.

```js
const C = () => {}
new C() // error
```

---

## 8. Useful With Arrays

```js
arr.map(x => x * 2)
arr.filter(x => x > 0)
arr.reduce((total, x) => total + x, 0)
```

---

## Quizzes

1. Convert to arrow:

```js
function add(a, b) { return a + b }
```

2. Convert to one-line implicit return:

```js
const square = (x) => { return x * x }
```

3. Fix object return:

```js
const makeItem = () => { id: 1 }
```

4. Replace `arguments`:

```js
const sum = () => arguments[0] + arguments[1]
```

5. Explain:

```js
const obj = { val: 20, getVal: () => this.val }
```

---

## Assignments

1. Write `incrementAll(arr)` → return a new array where each number is increased by 1 using `map`.
2. Write `filterEven(arr)` → return only even numbers using `filter`.
3. Write `sumArray(arr)` → return the total using `reduce`.
4. Create an object with a method that uses `this` correctly (no arrow function in the method).
   `markdown`
