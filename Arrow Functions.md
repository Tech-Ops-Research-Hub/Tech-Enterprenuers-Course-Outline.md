# Arrow Functions 

Arrow functions are an expression-based function definition form. They shorten syntax and capture `this` lexically. They do not have their own `this`, `arguments`, `super`, or `new.target`. They cannot be used as constructors.

## Core Syntax Forms

```
const fn = () => value
const fn = x => x + 1
const fn = (x, y) => x + y
const fn = () => ({ key: "value" })
const fn = () => {
  const v = 1
  return v + 1
}
```

## Implicit vs Explicit Return

Single expression body returns automatically:

```
const multiply = (a, b) => a * b
```

Block body requires `return`:

```
const multiply = (a, b) => {
  return a * b
}
```

## Returning Object Literals

Object literal requires parentheses:

```
const makeUser = () => ({ name: "Ada", role: "Engineer" })
```

If braces are used without parentheses, JavaScript interprets them as a block, not a value.

## Parameter Arity Rules

Zero parameters:

```
() => 42
```

One parameter:

```
x => x * 2
```

Multiple parameters:

```
(a, b, c) => a + b + c
```

Rest parameters:

```
(...values) => values
```

## Lexical `this`

Arrow functions do not define their own `this`. They use the `this` value of the surrounding lexical scope.

Example of correct behavior:

```
function Counter() {
  this.count = 0
  setInterval(() => {
    this.count++
  }, 1000)
}
```

If a normal function were used inside `setInterval`, `this` would not refer to the Counter instance unless manually bound.

## No `arguments` Object

Arrow functions do not bind `arguments`. Use rest:

```
const f = (...args) => args
```

## Not Constructible

Arrow functions cannot be used with `new`:

```
const C = () => {}
new C() // TypeError
```

They do not implement the internal `[[Construct]]` method.

## Method Definition Consideration

Using arrow functions for methods that expect dynamic `this` is incorrect:

```
const obj = {
  x: 10,
  getX: () => this.x
}
```

`this` here refers to the surrounding scope, not `obj`. Correct approach:

```
const obj = {
  x: 10,
  getX() { return this.x }
}
```

## Common Functional Operations

Mapping:

```
const doubled = arr.map(x => x * 2)
```

Filtering:

```
const positives = arr.filter(x => x > 0)
```

Reduction:

```
const sum = arr.reduce((acc, x) => acc + x, 0)
```

## Use Cases

Use arrow functions for:

* Small, stateless transformations
* Inline callbacks
* Higher-order functions
* Situations where `this` should refer to outer context

Avoid arrow functions for:

* Object prototype methods
* Class instance methods requiring `this`
* Constructors
* Scenarios requiring `arguments` without restructuring

---

## Quizzes

1. Convert to arrow function:

```
function add(a, b) {
  return a + b
}
```

2. Convert to implicit return:

```
const square = (x) => {
  return x * x
}
```

3. Correct the object literal return:

```
const makeItem = () => { id: 1, name: "Item" }
```

4. Replace `arguments` correctly:

```
const sum = () => arguments[0] + arguments[1]
```

5. Explain the output:

```
const obj = {
  val: 20,
  getVal: () => this.val
}
```

---

## Practical Assignments

1. Implement `incrementAll(arr)` that returns a new array with each element incremented by 1 using `map` and an arrow function.

2. Implement `filterEven(arr)` that returns only even numbers using `filter` and an arrow function.

3. Implement `sumArray(arr)` that returns sum of numbers using `reduce` and an arrow function.

4. Create an object with a method that returns one of its properties. Do not use an arrow function for the method.
