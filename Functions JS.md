# 4. Functions

## Essence

A function is a mapping from inputs to outputs plus optional side effects. Treat functions as units of behavior. Understand two orthogonal axes: (1) how functions are *created/declared* and (2) how they *behave at runtime* (scope, `this`, side effects, closures).

---

## 4.1 Function Declaration vs Expression vs IIFE

* **Declaration**

  ```js
  function f(a){ return a+1; }
  ```

  * Hoisted with binding. Safe to call before the line where defined.
  * Named for stack traces and recursion.

* **Expression**

  ```js
  const f = function(a){ return a+1; };
  ```

  * Not hoisted. Useful for assigning or passing.

* **Named Function Expression**

  ```js
  const f = function g(a){ return a+1; };
  ```

  * `g` available only inside the function for recursion.

* **IIFE (Immediately Invoked Function Expression)**

  ```js
  (function(){ /* isolated scope */ })();
  ```

  * Useful for module-like isolation before ES modules existed.

**Pitfall**: `var` hoisting with function expressions can produce `undefined` and runtime errors.

---

## 4.2 Parameters, `arguments`, Return

* Parameters are local bindings.
* Functions return `undefined` by default if no `return`.
* The `arguments` object is array-like for non-arrow functions. Prefer rest parameters.

Example:

```js
function sum(...nums){
  return nums.reduce((s,n)=>s+n,0);
}
```

---

## 4.3 Arrow Functions

* Syntax: `const f = (a) => a*2`.
* No own `this`. `this` is lexical from enclosing scope.
* No `arguments` object.
* Not constructible (`new` fails).
* Best for short callbacks or functions that should inherit `this`.

**Pitfall**: Using arrow functions as object methods loses intended `this`.

---

## 4.4 Default and Rest Parameters

* Default:

  ```js
  function greet(name = "Guest"){ return `Hi ${name}`; }
  ```
* Rest collects trailing args:

  ```js
  function concat(...parts){ return parts.join(''); }
  ```

Edge: Default parameters evaluated at call time.

---

## 4.5 Closures and Scope

* **Closure**: function + preserved lexical environment.
* Use cases: data privacy, factories, memoization.
* Memory: closures keep references to outer variables; avoid retaining large objects unintentionally.

Example (counter):

```js
function counter(){
  let n = 0;
  return () => ++n;
}
```

Common bug: closures in loops capturing same variable (use `let` to fix).

---

## 4.6 Higher-Order Functions (HOF)

* Functions that accept or return functions.
* Use for composition, currying, decorators, middleware.

Implement `compose`, `curry`:

```js
const compose = (f,g) => x => f(g(x));
const curry = fn => a => b => fn(a,b);
```

---

## 4.7 Pure vs Impure Functions

* **Pure**: deterministic, no external side effects. Testable and cacheable.
* **Impure**: mutate external state, read from I/O, use randomness/time.

Prefer pure functions inside business logic. Isolate impure code at boundaries.

---

## 4.8 Practical patterns and utilities

* **Memoize**
* **Once**
* **Debounce / Throttle** (related to events)
* **Partial application / Currying**
* **Factory functions vs classes**

Examples:

```js
function memoize(fn){
  const cache = new Map();
  return (...args) => {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const val = fn(...args);
    cache.set(key, val);
    return val;
  };
}
```

---

## 4.9 Instructor exercises (hands-on)

1. Write `multiplyAll(...nums)` returning product.
2. Implement `once(fn)` — runs `fn` only the first time.
3. Convert a callback API to return a Promise.
4. Implement `curry(fn)` that curries a 2-arg function.
5. Show closure leak: create and then remove closure reference safely.

---

## 4.10 Quizzes — Functions

### MCQs

1. Which is true about arrow functions?

   * a) They have their own `this`
   * b) They cannot be used as constructors
   * c) They create their own `arguments` object
   * d) They are hoisted

2. What does `function f(){}` hoisting mean?

   * a) Function available after definition only
   * b) Function binding created at parse time and available anywhere in scope
   * c) Function is blocked by `let`

3. Which is a pure function?

   * a) `x => x * 2`
   * b) `() => Date.now()`
   * c) `() => Math.random()`

### Coding questions

1. Implement `sum(...nums)` using `reduce`.
2. Implement `memoize`.

### Model answers (short)

1.

```js
const sum = (...nums) => nums.reduce((s,n)=>s+n,0);
```

2. See memoize above.

---

# 5. Objects and Arrays — Instructor Notes (very detailed)

## Essence (first principles)

Objects are collections of key→value bindings; arrays are ordered collections. Both are reference types. Behavior depends on mutability, identity, and prototype chain.

---

## 5.1 Object Literals, Property Descriptors, Symbols

* Literal:

  ```js
  const obj = { a:1, b(){ return 2; } };
  ```
* Property attributes: `writable`, `enumerable`, `configurable`.
* `Object.defineProperty` for precise control.
* `Symbol` for hidden/unique keys.

Example:

```js
const s = Symbol('id');
obj[s] = 123;
```

---

## 5.2 Getters and Setters

Define computed properties while preserving encapsulation:

```js
const user = {
  first: 'A', last: 'B',
  get full(){ return `${this.first} ${this.last}`; },
  set full(v){ [this.first,this.last] = v.split(' '); }
};
```

---

## 5.3 `this` and Method Binding

* `this` determined at call time.
* Methods: `obj.method()` → `this` = `obj`.
* Use `bind` to fix `this`.
* Arrow functions inherit `this` lexically.

Pitfall: detaching a method loses `this`.

```js
const m = obj.method;
m(); // wrong `this`
```

---

## 5.4 Prototype and Inheritance

* Every object has `[[Prototype]]` (`__proto__`).
* `Object.create(proto)` creates object with specified prototype.
* Constructor functions + `.prototype` used historically.
* ES6 `class` is syntactic sugar over prototype chain.

Pitfall: Mutating prototypes of built-ins can break code.

---

## 5.5 Arrays: Methods, Mutability, Sparse Arrays

* **Non-mutating:** `map`, `filter`, `slice`, `concat`
* **Mutating:** `push`, `pop`, `splice`, `sort`, `reverse`
* Prefer immutability in pure functions; use spread or `slice` to copy.
* Sparse arrays have holes; many array operations skip holes.

Reduce pattern:

```js
const flatten = arr => arr.reduce((acc,x) => acc.concat(Array.isArray(x)? flatten(x) : x), []);
```

---

## 5.6 Destructuring and Spread

* Objects:

  ```js
  const {a, b:alias = 2, ...rest} = obj;
  ```
* Arrays:

  ```js
  const [first, ...tail] = arr;
  ```
* Spread to copy/merge:

  ```js
  const copy = {...obj};
  ```

Edge: Spread performs shallow copy only.

---

## 5.7 JSON and Data Manipulation

* `JSON.stringify` loses functions, `undefined`, `Symbol`.
* `JSON.parse` gives raw objects, not class instances.
* Use `structuredClone` (modern) for deep clone when available:

  ```js
  const clone = structuredClone(obj);
  ```

Pitfalls: circular references cause `JSON.stringify` to throw.

---

## 5.8 Immutability patterns

* `Object.freeze()` shallow freeze.
* Libraries: Immer, immutable.js.
* For reliable immutability, copy on write.

---

## 5.9 Performance notes

* Arrays are fastest for dense numeric-indexed data.
* Avoid creating many small objects in hot loops.
* Use `Map`/`Set` for frequent key-based operations.

---

## 5.10 Instructor exercises (objects & arrays)

1. Implement `unique(arr)` returning unique values using `Set`.
2. Deep clone an object with nested arrays (no third-party libs). Show pitfalls.
3. Use `reduce` to group array of objects by a key.
4. Implement `pluck(arr, key)` returns array of values for key.
5. Demonstrate difference between mutating and non-mutating `sort`.

---

## 5.11 Quizzes — Objects & Arrays

### MCQs

1. Which method returns a new array?

   * a) forEach
   * b) map
   * c) push
   * d) splice
     **Answer:** b

2. What is `typeof null`?

   * a) object
   * b) null
   * c) undefined

3. What happens when you `JSON.stringify` a function?

   * a) Serialized as string
   * b) Ignored (omitted)
   * c) Throws error

### Coding questions

1. Use `reduce` to compute frequency map of words from `["a","b","a"]`.
2. Implement shallow copy of an object without `Object.assign`.

### Model answers (short)

1.

```js
const freq = arr => arr.reduce((m,x)=> (m[x]=(m[x]||0)+1,m), {});
```

2.

```js
const copy = {...obj};
```

---

# 6. DOM Manipulation — Instructor Notes (very detailed)

## Essence

The DOM is a live tree representation of the document. Interactions happen by selecting nodes, changing nodes, and responding to events. Structure, performance, and security are primary constraints.

---

## 6.1 DOM model fundamentals

* Node types: Element, Text, Comment.
* `document` is the root.
* Properties vs attributes: `el.id` vs `el.getAttribute('id')`.
* Live vs static collections: `getElementsByClassName` returns live `HTMLCollection`. `querySelectorAll` returns static `NodeList`.

---

## 6.2 Selecting elements

* `document.getElementById(id)` — fastest for single ID.
* `document.querySelector(selector)` — flexible, slightly slower.
* Prefer `querySelector` for consistency unless profiling shows bottleneck.

Example:

```js
const btn = document.querySelector('#submit');
```

---

## 6.3 Changing content and styles

* `textContent` for plain text.
* `innerHTML` parses HTML (security risk).
* Use `.classList` to toggle classes:

  ```js
  el.classList.add('is-active');
  el.classList.toggle('open', shouldOpen);
  ```
* Avoid inline styles where CSS classes suffice.

Security note: never insert user content via `innerHTML` without sanitization.

---

## 6.4 Creating and removing elements

* Create node:

  ```js
  const li = document.createElement('li');
  li.textContent = 'Item';
  list.appendChild(li);
  ```
* Remove:

  ```js
  el.remove();
  ```
* Use `DocumentFragment` for batch inserts to reduce reflows.

---

## 6.5 Event listeners and delegation

* Use `addEventListener(type, handler, options)`.
* Remove with `removeEventListener` and same function reference.
* Event delegation: attach single listener to parent and detect target via `event.target.closest(selector)`.

  * Reduces listeners and improves performance for dynamic lists.

Example:

```js
list.addEventListener('click', e => {
  const btn = e.target.closest('.btn');
  if (!btn) return;
  // handle
});
```

---

## 6.6 Bubbling vs Capturing

* Default is bubbling (child → parent).
* Use `{ capture: true }` to listen during capture phase.
* Most code uses bubbling.

---

## 6.7 Forms and browser events

* `submit` event on `form`. Use `e.preventDefault()` to stop native submit.
* `FormData` to gather form values safely.
* Validate on `input`/`change`. Use built-in constraints (`required`, `pattern`) for accessibility and progressive enhancement.

Example:

```js
form.addEventListener('submit', e=>{
  e.preventDefault();
  const data = new FormData(form);
  fetch('/submit', { method: 'POST', body: data });
});
```

---

## 6.8 Accessibility basics

* Use semantic HTML (`<button>`, `<label>`, `<header>`).
* Manage focus programmatically: `element.focus()`.
* Use ARIA only when necessary. Keep tab order logical.

---

## 6.9 Performance and memory

* Batch DOM writes. Read then write to avoid layout thrashing.
* Use `requestAnimationFrame` for visual updates.
* Remove event listeners when elements are removed to avoid leaks.

---

## 6.10 Advanced: MutationObserver

* Observe DOM changes efficiently.

```js
const obs = new MutationObserver(records => { /* handle */ });
obs.observe(target, { childList:true, subtree:true });
```

Use to react to structural changes without polling.

---

## 6.11 Instructor exercises (DOM)

1. Build a dynamic todo list: add, toggle complete, remove. Use event delegation.
2. Implement debounce for an input `keyup` handler.
3. Create a modal component that traps focus and is keyboard-accessible.
4. Demonstrate inserting 1000 list items with `DocumentFragment` and without, measure FPS.

---

## 6.12 Quizzes — DOM

### MCQs

1. Which is safest for inserting user-generated text?

   * a) innerHTML
   * b) textContent
   * c) insertAdjacentHTML

2. Event delegation is useful because:

   * a) It avoids propagation
   * b) It reduces number of listeners for dynamic children
   * c) It disables default behavior

3. `querySelectorAll` returns:

   * a) Live NodeList
   * b) Static NodeList

### Coding question

1. Implement a single event listener on a `<ul>` that toggles `.done` class for clicked `<li>` items.
   **Model answer:**

```js
ul.addEventListener('click', e=>{
  const li = e.target.closest('li');
  if(!li || !ul.contains(li)) return;
  li.classList.toggle('done');
});
```

---

# 7. ES6+ Modern JavaScript — Instructor Notes (very detailed)

## Essence (first principles)

ES6+ introduced syntactic constructs and primitives that map more clearly to modern programming abstractions: modules, lexical scoping, asynchronous primitives, and better data structures. Understand semantics rather than syntax sugar.

---

## 7.1 Template Literals and Tagged Templates

* Backtick strings allow interpolation and multiline.

```js
const msg = `Hi ${name}\nLine 2`;
```

* Tagged templates let you process template parts.

```js
function tag(parts, ...vals){ /* sanitize etc */ }
tag`Hello ${name}`;
```

Use for safe HTML templating or custom interpolation.

---

## 7.2 Modules (`import` / `export`)

* Named export:

  ```js
  export function f(){}
  import { f } from './mod.js';
  ```
* Default export:

  ```js
  export default function(){}
  import f from './mod.js';
  ```
* Dynamic import:

  ```js
  const mod = await import('./mod.js');
  ```
* Modules run in strict mode and have module scope.

Caveats: ESM vs CommonJS in Node. Use top-level `await` carefully.

---

## 7.3 Destructuring assignment deep dive

* Default values and nested patterns.

```js
const { a: { b = 2 } = {} } = obj;
```

* Use destructuring for function parameters to reduce boilerplate.

Pitfall: destructuring `null` or `undefined` throws. Provide defaults.

---

## 7.4 Spread and Rest nuance

* Spread for copying arrays/objects shallowly.
* Rest in parameter position gathers remaining items.
* Order matters: rest must be last in parameter list.

---

## 7.5 Classes and Inheritance

* `class` is syntactic sugar; prototype chain remains.
* `constructor`, `super`, `static` methods, private fields (`#`).

```js
class Base { #id; constructor(id){ this.#id = id; } }
```

* Beware subclassing built-ins (Array) historically tricky.

---

## 7.6 Promises and Async/Await

* **Promise states**: pending → fulfilled/rejected.
* `then` chain returns new promises enabling pipeline.
* `Promise.all` rejects fast on first rejection. `Promise.allSettled` waits for all results.
* `async` function returns a Promise. `await` pauses the async function until promise settles. `await` does not block event loop.

Error handling:

```js
try{
  const res = await fetch(url);
} catch(err){
  // handle
}
```

Microtask queue: resolved promises schedule microtasks which run before the next macrotask. This order matters for concurrency reasoning.

---

## 7.7 Optional Chaining `?.` and Nullish Coalescing `??`

* `a?.b` short-circuits if `a` is `null` or `undefined`.
* `x ?? y` returns `y` only if `x` is `null` or `undefined`.
* Difference vs `||`: `0 || 'fallback'` yields `'fallback'`; `0 ?? 'fallback'` yields `0`.

---

## 7.8 Arrow functions and `this` revisited

* Arrow functions are not suited for methods meant to be dynamic `this`.
* They are suitable for callbacks and short functions that need lexical `this`.

---

## 7.9 Modern language features to teach

* `Map`, `Set`, `WeakMap`, `WeakSet` for different lifetime semantics.
* `for...of` for iterables. `for...in` iterates keys (not recommended for arrays).
* `Symbol` for unique property keys.
* `BigInt` for integers beyond `Number.MAX_SAFE_INTEGER`.

---

## 7.10 Instructor exercises (ES6+)

1. Convert callback pyramid to `async/await`.
2. Implement dynamic import to load feature module on demand.
3. Create a class with private fields and static factory method.
4. Demonstrate `Promise.allSettled` usage and show how to process partial failures.

---

## 7.11 Quizzes — ES6+

### MCQs

1. What does `a ?? b` return if `a` is `0`?

   * a) b
   * b) 0

2. Which statement about `import()` is true?

   * a) It returns the module synchronously
   * b) It returns a Promise resolving to the module

3. `class` in JS:

   * a) Is a new runtime model different from prototypes
   * b) Is syntactic sugar over prototypes

### Coding questions

1. Implement:

   * a. A function `fetchJson(url)` returning parsed JSON with `async/await` and error handling.
   * b. Use `Promise.allSettled` to fetch multiple URLs and return successes only.

**Model answers (short)**

a.

```js
async function fetchJson(url){
  const res = await fetch(url);
  if(!res.ok) throw new Error(`HTTP ${res.status}`);
  return res.json();
}
```

b.

```js
async function fetchMany(urls){
  const results = await Promise.allSettled(urls.map(u=>fetchJson(u)));
  return results.filter(r=>r.status==='fulfilled').map(r=>r.value);
}
```

---

# Full assessment (integrated, instructor-level)

### Lab assignment (capstone)

Build a small single-page app (no frameworks) that:

1. Loads a list of items (simulate fetch with `Promise`).
2. Renders items using `DocumentFragment`.
3. Allows adding items via a form. Validate input.
4. Uses event delegation for item controls (edit, delete, toggle).
5. Stores data in `localStorage` (serialize/deserialize with JSON).
6. Expose a module structure: `api.js`, `ui.js`, `app.js`.
7. Provide unit-like tests (simple assertions) for:

   * `memoize` function.
   * `sum` using `reduce`.
   * `unique` function.

### Grading rubric (instructor checklist)

* Correct use of modules and `import/export`.
* No memory leaks. Event handlers removed properly.
* Clear separation: pure business logic vs DOM side effects.
* Use of modern features where appropriate (arrow functions, destructuring, optional chaining).
* Code readability: meaningful names, comments where needed.
* Tests present and passing.

---

# Answer keys (quick reference)

* Functions MCQ answers: Functions section answers listed inline.
* Objects & Arrays MCQ answers: inline.
* DOM MCQ answers: inline.
* ES6+ MCQ answers: inline.
* Coding model answers: inline after respective sections.
