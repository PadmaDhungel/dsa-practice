## Collections in Python

In Python, **collections** are data structures used to store and organize multiple values in a single variable.

They allow you to group, access, and manipulate data efficiently, and are used everywhere—from simple scripts to complex applications.


### Types of Built-in Collections

Python offers four main built-in collection types:

| Collection | Ordered | Mutable | Allows Duplicates | Example |
|------------|---------|---------|-------------------|---------|
| **List**   |  Yes  |  Yes  |  Yes             | `[1, 2, 3]` |
| **Tuple**  |  Yes  |  No   |  Yes             | `(1, 2, 3)` |
| **Set**    |  No   |  Yes  |  No              | `{1, 2, 3}` |
| **Dict**   |  *Yes  |  Yes  |  (Keys unique)   | `{'a': 1, 'b': 2}` |

---
*Dictionaries order preserved but not guaranteed in python 3.6 while guaranteed in 3.7* 
## Why Use Collections?

- **Lists**: Store a sequence of items that can change (e.g., shopping cart, tasks)
- **Tuples**: Use when data should not change (e.g., GPS coordinates)
- **Sets**: Great for membership tests and removing duplicates
- **Dictionaries**: Store data in key-value pairs (e.g., user profiles, settings)


### Common Operations

Here are some operations you can perform on most collections:
- Looping through items (`for item in collection`)
- Checking membership (`x in collection`)
- Adding/removing elements
- Sorting (for lists)
- Accessing items by index or key (for list/tuple/dict)

### When to Use What?

- Need to **preserve order** and **change values** → Use **List**
- Need to **preserve order** and **keep data constant** → Use **Tuple**
- Need **fast lookup** and **no duplicates** → Use **Set**
- Need to **associate keys with values** → Use **Dictionary**

### More
```
Iterable (Any object implementing `__iter__`)
│
├── Container (holds items, supports `in` operator)
│   ├── Collection (Container with `len()`)
│   │   ├── Sequence (Ordered, indexable, supports slicing)
│   │   │   ├── Mutable Sequences (unhashable)
│   │   │   │   ├── list
│   │   │   │   ├── bytearray
│   │   │   ├── Immutable Sequences
│   │   │   │   ├── str (immutable, hashable)
│   │   │   │   ├── range (immutable, hashable)
│   │   │   │   ├── bytes (immutable, hashable)
│   │   │   │   ├── tuple (immutable, hashable if elements are hashable)
│   │   ├── Set (Unordered, no duplicates)
│   │   │   ├── set (mutable, unhashable)
│   │   │   ├── frozenset (immutable, hashable)
│   │   ├── Mapping (Key-value pairs, insertion ordered)
│   │   │   ├── dict (mutable, unhashable)


```

### What's Next?

Each of these collections has its own syntax, methods, and use cases.

 Explore them in detail:
- [`list.md`](list/notes.md)
- [`tuple.md`](tuple/notes.md)
- [`set.md`](set/notes.md)
- [`dict.md`](dict/notes.md)

---

## Bonus: Advanced Collections

Python also includes **advanced collections** in the `collections` module:
- `namedtuple()`
- `deque`
- `Counter`
- `defaultdict`