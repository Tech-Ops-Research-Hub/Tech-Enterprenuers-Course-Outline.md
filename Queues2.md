# Queues — Full Implementation Guide

## Overview
A **queue** is a linear data structure that enforces **First In, First Out (FIFO)** order. The earliest inserted element is removed first. Use queues when order of service matters and you must preserve arrival order.

## First principles
Inputs: sequence of values arriving over time.  
Constraint: preserve arrival order on output.  
Primitive operations map directly to physical-world queue semantics: enqueue adds to tail, dequeue removes from head. Implementations vary by performance tradeoffs.

## Behavior and invariants
- Invariant 1: If `a` enqueued before `b`, then `a` dequeued before `b` unless `a` is removed by another operation (e.g., cancellation).
- Invariant 2: After `n` enqueues and `m` dequeues where `n>m`, queue length = `n - m`.
- Empty queue: dequeue must signal error or return sentinel value.
- Concurrent access must preserve atomicity for enqueue/dequeue.

## Core operations (API)
- `enqueue(value)` — push value to tail. O(1) amortized.
- `dequeue()` — remove and return head. O(1) amortized.
- `peek()` / `front()` — return head without removing. O(1).
- `isEmpty()` — boolean. O(1).
- `size()` — count. O(1) if tracked.
- `clear()` — empty queue. O(1) if pointer reset, else O(n) if releasing nodes.

## Complexity
| Operation | Time | Space |
|---|---:|---:|
| enqueue | O(1) amortized | O(1) extra |
| dequeue | O(1) amortized | O(1) extra |
| peek | O(1) | O(1) |
| memory | — | O(n) for n elements |

Notes: array implementations may require resizing. Linked-list and circular buffer avoid per-op resizing.

## Implementation patterns

### 1. Array-backed circular buffer (production-friendly)
Traits: contiguous memory, fixed capacity or resizable, best cache behavior.

**Python (resizable circular buffer)**
```python
class CircularQueue:
    def __init__(self, capacity=8):
        self._cap = max(2, capacity)
        self._data = [None] * self._cap
        self._head = 0
        self._size = 0

    def _resize(self, new_cap):
        a = [None] * new_cap
        for i in range(self._size):
            a[i] = self._data[(self._head + i) % self._cap]
        self._data = a
        self._cap = new_cap
        self._head = 0

    def enqueue(self, val):
        if self._size == self._cap:
            self._resize(self._cap * 2)
        tail = (self._head + self._size) % self._cap
        self._data[tail] = val
        self._size += 1

    def dequeue(self):
        if self._size == 0:
            raise IndexError("dequeue from empty queue")
        val = self._data[self._head]
        self._data[self._head] = None
        self._head = (self._head + 1) % self._cap
        self._size -= 1
        if 0 < self._size <= self._cap // 4:
            self._resize(max(8, self._cap // 2))
        return val

    def peek(self):
        if self._size == 0:
            raise IndexError("peek from empty queue")
        return self._data[self._head]

    def is_empty(self):
        return self._size == 0

    def __len__(self):
        return self._size
````

### 2. Singly linked list (unbounded)

Traits: O(1) enqueue/dequeue, no resizing, stable for large or streaming data.

**Python**

```python
class Node:
    __slots__ = ("val", "next")
    def __init__(self, val):
        self.val = val
        self.next = None

class LinkedQueue:
    def __init__(self):
        self.head = None
        self.tail = None
        self._size = 0

    def enqueue(self, val):
        node = Node(val)
        if self.tail:
            self.tail.next = node
        else:
            self.head = node
        self.tail = node
        self._size += 1

    def dequeue(self):
        if not self.head:
            raise IndexError("dequeue from empty queue")
        val = self.head.val
        self.head = self.head.next
        if not self.head:
            self.tail = None
        self._size -= 1
        return val

    def peek(self):
        if not self.head:
            raise IndexError("peek from empty queue")
        return self.head.val

    def __len__(self):
        return self._size
```

### 3. Two-stacks queue (amortized O(1))

Use case: implement queue using two LIFO stacks. Useful in interview settings and when only stack primitives exist.

**Python**

```python
class QueueUsingStacks:
    def __init__(self):
        self.s_in = []
        self.s_out = []

    def _move_in_to_out(self):
        while self.s_in:
            self.s_out.append(self.s_in.pop())

    def enqueue(self, val):
        self.s_in.append(val)

    def dequeue(self):
        if not self.s_out:
            self._move_in_to_out()
        if not self.s_out:
            raise IndexError("dequeue from empty queue")
        return self.s_out.pop()

    def peek(self):
        if not self.s_out:
            self._move_in_to_out()
        if not self.s_out:
            raise IndexError("peek from empty queue")
        return self.s_out[-1]
```

### 4. Thread-safe / concurrent queues

In multi-threaded contexts use concurrency primitives. Examples: `queue.Queue` in Python, `ConcurrentLinkedQueue` in Java, `BlockingQueue` variants for producer-consumer patterns. Ensure atomicity for head/tail updates. Use locks, compare-and-swap, or lock-free algorithms depending on latency and contention.

## Edge cases and pitfalls

* Off-by-one in circular buffer indexing.
* Forgetting to update tail on empty->non-empty transition in linked list.
* Memory leak if references not cleared in languages with manual memory management.
* Integer overflow when using naive counters for indices in extremely long-running systems.
* Division between logical size and physical capacity. Expose size API if required.
* For two-stacks method, ensure correct amortized analysis and that peek does not mutate state.

## Use cases

* Breadth-first search (BFS).
* Task scheduling and job queues.
* Producer-consumer pipelines.
* Rate-limited API request queues.
* Print spooling and IO buffers.
* Message brokers and stream processing.

## Testing checklist

* Single enqueue then dequeue yields same value.
* Multiple enqueues then multiple dequeues preserve order.
* Dequeue on empty raises error.
* Peek does not remove element.
* Size reflects operations.
* Stress test with many elements to verify resizing and memory behavior.
* Concurrency tests for race conditions and lost updates.
* Fuzz token input for implementations that parse input strings.

## Examples and sample runs

**Simple usage**

```python
q = CircularQueue()
q.enqueue(1)
q.enqueue(2)
assert q.dequeue() == 1
assert q.peek() == 2
```

**Two-stacks**

```python
q = QueueUsingStacks()
q.enqueue(1); q.enqueue(2)
assert q.dequeue() == 1
q.enqueue(3)
assert q.dequeue() == 2
assert q.dequeue() == 3
```

## Test vectors (unit tests)

* `[ ]` -> dequeue error.
* `[1]` -> dequeue = 1.
* `[1,2,3]` -> dequeues [1,2,3].
* Mixed enqueue/dequeue pairs: confirm invariants.
* Large N for performance and memory.

## Repo layout suggestion

```
queue-guide/
├── README.md            # this file
├── python/
│   ├── circular_queue.py
│   ├── linked_queue.py
│   ├── stacks_queue.py
│   └── tests/
│       ├── test_circular.py
│       ├── test_linked.py
│       └── test_stacks.py
├── javascript/
│   ├── circularQueue.js
│   ├── linkedQueue.js
│   └── tests/
│       └── ...
└── examples/
    └── perf_benchmark.py
```

## Implementation checklist for production

* Choose implementation by workload: circular buffer for high throughput, linked list for unpredictable size, blocking/concurrent queue for multi-threading.
* Expose metrics: length, capacity, head/tail indices optionally for diagnostics.
* Add instrumentation: enqueue/dequeue latency, GC pressure, memory usage.
* Add bounded-queue semantics if backpressure is required.
* Add retention policy for stale items where necessary.

```
```
