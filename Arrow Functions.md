# Arrow Functions (Simplified Notes)

Arrow function = a short way to write a function.

It removes extra words and symbols.

```
const add = (a, b) => a + b
```

This means: take `a` and `b`, give back `a + b`.

If there is one thing to do, no need for `return`.

```
const double = x => x * 2
```

If you write more than one line, you must use `{}` and `return`.

```
const work = (x) => {
  const y = x + 1
  return y
}
```

If you want to give back an object, wrap it with parentheses:

```
const person = () => ({ name: "Sam" })
```

Arrow functions do not make their own `this`. They use `this` from where they are written, not where they are used.

They also do not have `arguments`. Use `(...args)` instead.

They cannot be used with `new`. They do not create objects like a normal function constructor.

They should not be used for object methods when you need `this`.

```
const obj = {
  x: 5,
  getX() { return this.x }
}
```

Use arrow functions for short tasks.



Arrow functions are a shorter way to write functions. They use the surrounding `this` instead of creating a new one. They cannot be used with `new`.

## Basic Forms

```
const fn = () => value
const fn = x => x + 1
const fn = (x, y) => x + y
```

Return requires braces only when multiple statements exist:

```
const fn = () => {
  const v = 1
  return v + 1
}
```

## Implicit Return

```
const multiply = (a, b) => a * b
```

## Returning Objects

Wrap the object in parentheses:

```
const makeUser = () => ({ name: "Ada" })
```

## Parameters

```
() => 42
x => x * 2
(a, b) => a + b
(...values) => values
```

## `this` Behavior

Arrow functions use `this` from outer scope. They do not change `this`.

Example:

```
function Counter() {
  this.count = 0
  setInterval(() => {
    this.count++
  }, 1000)
}
```

## No `arguments`

Use rest parameters instead:

```
const f = (...args) => args
```

## Not for Object Methods Requiring `this`

Incorrect:

```
const obj = { x: 10, getX: () => this.x }
```

Correct:

```
const obj = { x: 10, getX() { return this.x } }
```

## Cannot Be Constructors

```
const C = () => {}
new C() // error
```

## Common Uses

```
arr.map(x => x * 2)
arr.filter(x => x > 0)
arr.reduce((a, x) => a + x, 0)
```

---

## Quizzes

1. Convert:

```
function add(a, b) { return a + b }
```

2. Convert to implicit return:

```
const square = (x) => { return x * x }
```

3. Fix:

```
const makeItem = () => { id: 1 }
```

4. Replace `arguments`:

```
const sum = () => arguments[0] + arguments[1]
```

5. Explain:

```
const obj = { val: 20, getVal: () => this.val }
```

---

## Assignments

1. `incrementAll(arr)` → return array with each value +1 using `map`.
2. `filterEven(arr)` → return only even numbers using `filter`.
3. `sumArray(arr)` → sum numbers using `reduce`.
4. Create object with a method using regular function syntax to access `this`.
