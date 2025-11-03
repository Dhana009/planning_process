# Pure Python Interview Questions - SDET/Automation Engineer

> **Purpose**: Master pure Python concepts to confidently answer interview questions and handle follow-ups
> **Focus**: Conceptual questions only - NO coding problems, NO automation-specific topics
> **Target**: 40-45 questions organized by topic
> **Status**: 🟡 In Progress (18/40 questions complete - 45%)

---

## 📖 HOW TO USE THIS DOCUMENT

### Study Approach:
1. **Read the Question** - Understand what's being asked
2. **Read the Answer** - See how to respond in an interview
3. **Study the Concepts** - Understand the "why" behind the answer
4. **Review Follow-ups** - Be ready for deeper probing questions
5. **Note Interview Tips** - Pay attention to 💡 and ⚠️ callouts

### During Interview:
- Start with the **direct answer** (keep it concise)
- If interviewer asks for more detail, explain the **concepts**
- Be ready to handle **follow-up questions**
- Use the callouts to avoid **common mistakes**

### Tracking Progress:
- See [Progress Tracker](#-progress-tracker) at the bottom
- Work through sections sequentially or jump to topics you need

---

## 📋 TABLE OF CONTENTS
1. [Python Fundamentals](#1-python-fundamentals) - ✅ 15/15 (Complete)
2. [Advanced Python Concepts](#2-advanced-python-concepts) - 🟡 3/12-15 (In Progress)
3. [OOP in Python](#3-oop-in-python) - ⬜ 0/8-10 (Not Started)
4. [Python Internals & Behaviors](#4-python-internals--behaviors) - ⬜ 0/5-8 (Not Started)

---

## 1. PYTHON FUNDAMENTALS

### Q1: What's the difference between lists and tuples in Python?

**ANSWER:**
Lists and tuples are both sequence types, but they differ in mutability:
- **Lists** are mutable (can be modified after creation) - use square brackets `[]`
- **Tuples** are immutable (cannot be modified after creation) - use parentheses `()`

**Key Differences:**
1. **Mutability**: You can add, remove, or modify items in a list, but not in a tuple
2. **Performance**: Tuples are slightly faster because Python can optimize them (they're fixed)
3. **Use as dictionary keys**: Tuples can be dictionary keys (if they contain immutable elements), lists cannot
4. **Memory**: Tuples use less memory than lists

**CONCEPTS TO UNDERSTAND:**

**Mutability:**
- Lists are stored in a way that allows Python to resize the underlying array
- When you modify a list, Python may need to allocate new memory if the list grows
- Tuples have a fixed size, so Python can allocate exactly the memory needed upfront
- This is why tuples are more memory-efficient for fixed data

**Immutability in Python:**
- Immutability means the object cannot be changed after creation
- This doesn't mean you can't reassign a variable - `my_tuple = (1, 2, 3)` then `my_tuple = (4, 5)` is allowed (you're creating a new tuple)
- True immutability means you can't do `my_tuple[0] = 5` - this would raise a TypeError

**Dictionary Keys:**
- Dictionary keys must be hashable (immutable)
- Lists are mutable, so they're not hashable - Python can't create a hash value for something that might change
- Tuples are hashable (if they contain only hashable elements like strings, numbers, or other tuples)
- This is why you can do: `{(1, 2): "value"}` but not `{[1, 2]: "value"}`

**COMMON FOLLOW-UP QUESTIONS:**

**Q: When would you use a tuple vs a list?**
- Use tuples for: fixed data (coordinates, RGB colors), dictionary keys, function arguments that shouldn't change, returning multiple values from a function
- Use lists for: data that needs to be modified, dynamic collections, when you need methods like append(), extend(), remove()

**Q: Are tuples really immutable? Can you show me?**
- Yes, tuples are immutable. Example:
  ```python
  t = (1, 2, 3)
  t[0] = 5  # TypeError: 'tuple' object does not support item assignment
  ```
- However, if a tuple contains a mutable object (like a list), you can modify that mutable object:
  ```python
  t = ([1, 2], 3)
  t[0].append(4)  # This works! Tuple still contains the same list object
  # t is now ([1, 2, 4], 3)
  ```

---

### Q2: Explain the difference between `==` and `is` in Python.

**ANSWER:**
- `==` compares the **values** of two objects
- `is` compares the **identity** (memory addresses) of two objects

`is` checks if two variables point to the same object in memory, while `==` checks if the values are equal.

**CONCEPTS TO UNDERSTAND:**

**Object Identity:**
- Every object in Python has a unique identity (memory address)
- The `id()` function returns this identity
- `is` compares these identities: `a is b` is equivalent to `id(a) == id(b)`

**Value Equality vs Identity:**
- Two different objects can have the same value (e.g., two lists with `[1, 2, 3]`)
- They would be equal with `==` but not identical with `is`
- Same object in memory = same identity = `is` returns True

**Small Integer Caching (Python Optimization):**
- Python caches small integers (-5 to 256) for performance
- This means `a = 5` and `b = 5` might point to the same object
- This is an implementation detail - don't rely on it for your code logic

**Example:**
```python
# Lists with same values
list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 == list2)  # True (same values)
print(list1 is list2)   # False (different objects in memory)

# Integers (Python caches small integers)
a = 5
b = 5
print(a == b)  # True
print(a is b)  # True (same cached object)

c = 1000
d = 1000
print(c == d)  # True
print(c is d)  # May be False (depends on Python version/implementation)
```

**COMMON FOLLOW-UP QUESTIONS:**

**Q: When should I use `is` vs `==`?**
- Use `is` for: checking `None` (`if x is None`), checking boolean values (`if x is True`), checking if same object
- Use `==` for: comparing values in most cases
- **Best practice**: Always use `is None` and `is not None` for None checks, never `== None`

**Q: Why does `is` work differently for strings?**
- Python also interns (caches) some strings for optimization
- Short strings or strings that look like identifiers might be the same object
- Don't rely on this - always use `==` for string comparison

---

### Q3: How does Python's garbage collection work?

**ANSWER:**
Python uses automatic memory management with two main mechanisms:
1. **Reference Counting**: Primary mechanism - Python tracks how many references point to each object
2. **Cyclic Garbage Collector**: Handles circular references that reference counting can't resolve

When an object's reference count reaches zero, Python automatically frees the memory.

**CONCEPTS TO UNDERSTAND:**

**Reference Counting:**
- Every object has a counter that tracks how many variables/references point to it
- When you assign: `x = [1, 2, 3]`, the reference count for that list becomes 1
- When you do `y = x`, the reference count becomes 2 (both x and y point to same list)
- When `x` goes out of scope or is reassigned, reference count decreases
- When count reaches 0, Python immediately deallocates the object (in most cases)
- You can check reference count: `import sys; sys.getrefcount(x)` (returns count + 1 due to function call)

**How Reference Count Changes:**
- Increases when: variable assignment, passing to function, adding to container
- Decreases when: variable goes out of scope, reassignment, deleting variable, removing from container

**Cyclic References Problem:**
- If object A references object B, and object B references object A, they form a cycle
- Even if nothing else references them, their reference counts never reach zero
- Example:
  ```python
  a = []
  b = []
  a.append(b)  # a references b
  b.append(a)  # b references a
  # Now a and b form a cycle: a -> [b], b -> [a]
  # Each has refcount of 1 (from the other), even if no other variables point to them
  del a
  del b
  # Objects still exist in memory! Refcounts don't reach 0
  # Cyclic GC will eventually clean them up
  ```

**Generational Garbage Collector:**
- Python uses a generational garbage collector (gc module) to handle cycles
- It divides objects into generations (newly created vs older objects)
- Runs periodically to detect and break circular references
- Based on the idea that "young objects die young" - most objects are used briefly
- Can be controlled/manually triggered: `import gc; gc.collect()`

**When Garbage Collection Happens:**
- Reference counting: Immediate (happens as code runs)
- Generational GC: Periodic (when thresholds are reached or manually triggered)

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Can you manually trigger garbage collection?**
- Yes: `import gc; gc.collect()`
- Usually not needed - Python handles it automatically
- Might be useful in specific memory-constrained scenarios

**Q: What's the `__del__` method?**
- It's a destructor method called when an object is about to be destroyed
- Not guaranteed when due to reference cycles
- Generally avoid using it - use context managers (`with` statement) instead

**Q: Are there any issues with garbage collection?**
- Circular references can delay cleanup
- `__del__` methods in circular references can prevent objects from being collected
- Generational GC has overhead (runs periodically), but usually negligible

---

### Q4: What's the difference between `append()` and `extend()` in lists?

**ANSWER:**
- `append()` adds a **single element** to the end of the list
- `extend()` adds **all elements from an iterable** to the end of the list

**CONCEPTS TO UNDERSTAND:**

**append() Behavior:**
- Takes exactly one argument (any type)
- Adds that argument as a single element
- If you pass a list, it adds the entire list as one element (nested list)
- Example:
  ```python
  my_list = [1, 2]
  my_list.append([3, 4])
  # Result: [1, 2, [3, 4]]  # List is added as one element
  ```

**extend() Behavior:**
- Takes one iterable argument (list, tuple, string, etc.)
- Iterates through the iterable and adds each element individually
- Extends the list's length by the number of elements in the iterable
- Example:
  ```python
  my_list = [1, 2]
  my_list.extend([3, 4])
  # Result: [1, 2, 3, 4]  # Elements are added individually
  ```

**What is an Iterable?**
- An iterable is any object you can loop over with a `for` loop
- Lists, tuples, strings, dictionaries, sets, generators, etc.
- For strings: `extend("abc")` adds 'a', 'b', 'c' as separate characters

**Common Mistake:**
- Many people confuse these:
  ```python
  list1 = [1, 2]
  list1.append([3, 4])     # Wrong if you want [1, 2, 3, 4]
  list1.extend([3, 4])     # Correct - gives [1, 2, 3, 4]
  ```

**COMMON FOLLOW-UP QUESTIONS:**

**Q: What's the difference between `extend()` and using `+` operator?**
- `extend()` modifies the list in-place (no new list created)
- `list1 + list2` creates a new list (original lists unchanged)
- `extend()` is more memory-efficient for large lists
- Example:
  ```python
  list1 = [1, 2]
  list2 = [3, 4]
  result = list1 + list2      # Creates new list [1, 2, 3, 4], list1 unchanged
  list1.extend(list2)         # Modifies list1 to [1, 2, 3, 4], no new list
  ```

**Q: Can you use `extend()` with non-list iterables?**
- Yes! Works with any iterable: tuples, strings, sets, generators
- `list1.extend((1, 2))` works (tuple)
- `list1.extend("abc")` works (string - adds 'a', 'b', 'c')
- `list1.extend({1, 2, 3})` works (set - order not guaranteed)

---

### Q5: What are list comprehensions? When would you use them?

**ANSWER:**
List comprehensions are a concise way to create lists in Python. They combine a `for` loop and list creation into a single line.

**Syntax:**
```python
[expression for item in iterable if condition]
```

**CONCEPTS TO UNDERSTAND:**

**Basic List Comprehension:**
```python
# Traditional way:
squares = []
for x in range(10):
    squares.append(x**2)

# List comprehension:
squares = [x**2 for x in range(10)]
```
- More readable and Pythonic
- Generally faster than traditional loops (Python optimizes them)

**Components:**
- **Expression**: What you want in the new list (`x**2`, `x.upper()`, etc.)
- **for clause**: Iteration over an iterable
- **Conditional (optional)**: `if condition` filters items

**With Conditions:**
```python
# Only even squares:
even_squares = [x**2 for x in range(10) if x % 2 == 0]

# Equivalent traditional way:
even_squares = []
for x in range(10):
    if x % 2 == 0:
        even_squares.append(x**2)
```

**Nested List Comprehensions:**
```python
# Flatten a 2D list:
matrix = [[1, 2], [3, 4], [5, 6]]
flat = [item for row in matrix for item in row]
# Result: [1, 2, 3, 4, 5, 6]
```

**When to Use:**
- ✅ Creating simple lists from iterables
- ✅ Filtering and transforming data
- ✅ Readable one-liners
- ❌ Complex logic (use regular loops for clarity)
- ❌ When you need side effects (like printing during iteration)

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Are list comprehensions faster than loops?**
- Generally yes, but difference is usually small
- Python can optimize comprehensions internally
- Readability should be priority unless profiling shows performance issue

**Q: Can you have multiple conditions in a list comprehension?**
- Yes: `[x for x in range(20) if x % 2 == 0 if x > 10]` (both conditions must be true)
- Or use `and`: `[x for x in range(20) if x % 2 == 0 and x > 10]`

**Q: What's the difference between list comprehension and generator expression?**
- List comprehension: `[x**2 for x in range(10)]` - creates entire list in memory
- Generator expression: `(x**2 for x in range(10))` - creates generator, yields values on demand
- Generator is memory-efficient for large sequences (doesn't store all values)

---

### Q6: Explain Python's scope and the LEGB rule.

**ANSWER:**
Python uses the **LEGB rule** to determine variable scope. When you reference a variable, Python searches in this order:
1. **L**ocal (inside current function)
2. **E**nclosing (outer functions in nested functions)
3. **G**lobal (module level)
4. **B**uilt-in (Python's built-in functions/variables)

**CONCEPTS TO UNDERSTAND:**

**Local Scope:**
- Variables defined inside a function are local
- Only accessible within that function
- Created when function is called, destroyed when function returns

**Enclosing Scope (Nonlocal):**
- In nested functions, inner function can access outer function's variables
- Use `nonlocal` keyword to modify outer function's variable from inner function
- Example:
  ```python
  def outer():
      x = "outer"
      def inner():
          nonlocal x  # Allows modifying outer's x
          x = "modified"
      inner()
      return x  # Returns "modified"
  ```

**Global Scope:**
- Variables defined at module level (outside functions/classes)
- Accessible from anywhere in the module
- Use `global` keyword to modify global variable from inside a function

**Built-in Scope:**
- Python's built-in functions and variables (`print`, `len`, `range`, etc.)
- Always available, no import needed
- Can be shadowed (don't use `print` as variable name!)

**Example of LEGB Search:**
```python
x = "global"

def outer():
    x = "enclosing"
    def inner():
        x = "local"
        print(x)  # Prints "local" (found in Local scope first)
    inner()

outer()  # Prints "local"
```

**Reading vs Writing:**
- **Reading a variable**: Python follows LEGB rule automatically
- **Writing to a variable**: If you assign (`x = 5`), Python creates a LOCAL variable by default
- Use `global` or `nonlocal` to modify outer scopes

**COMMON FOLLOW-UP QUESTIONS:**

**Q: What happens if I don't use `global` keyword?**
- If you only read: works fine (Python searches LEGB automatically)
- If you write: Python creates a NEW local variable, doesn't modify global
- Example:
  ```python
  x = 10
  def func():
      x = 20  # Creates NEW local x, doesn't modify global
  func()
  print(x)  # Still prints 10 (global unchanged)
  ```

**Q: What's the difference between `global` and `nonlocal`?**
- `global`: Access/modify module-level (global) variables
- `nonlocal`: Access/modify variables in enclosing (outer) function scope
- Both are needed when you want to WRITE to outer scopes

---

### Q7: What are `*args` and `**kwargs` in Python?

**ANSWER:**
- `*args` allows a function to accept **any number of positional arguments**
- `**kwargs` allows a function to accept **any number of keyword arguments**

**CONCEPTS TO UNDERSTAND:**

**`*args` (Arbitrary Positional Arguments):**
- The `*` unpacks arguments into a tuple
- `args` is just a convention - you can use any name (`*values`, `*items`)
- All positional arguments beyond explicitly named parameters are collected into `args`
- Example:
  ```python
  def my_func(a, b, *args):
      print(a, b)      # First two arguments
      print(args)      # Tuple of remaining arguments
      print(*args)     # Unpacking args
  
  my_func(1, 2, 3, 4, 5)
  # Output:
  # 1 2
  # (3, 4, 5)
  # 3 4 5
  ```

**`**kwargs` (Arbitrary Keyword Arguments):**
- The `**` unpacks keyword arguments into a dictionary
- `kwargs` is convention - you can use any name (`**options`, `**params`)
- All keyword arguments beyond explicitly named parameters are collected into `kwargs`
- Example:
  ```python
  def my_func(a, b, **kwargs):
      print(a, b)          # First two arguments
      print(kwargs)        # Dictionary of remaining keyword arguments
  
  my_func(1, 2, name="John", age=30, city="NYC")
  # Output:
  # 1 2
  # {'name': 'John', 'age': 30, 'city': 'NYC'}
  ```

**Order of Parameters:**
- Standard parameters → `*args` → `**kwargs`
- Correct: `def func(a, b, *args, **kwargs)`
- Wrong: `def func(**kwargs, *args)` - won't work

**Unpacking When Calling:**
- You can also unpack when CALLING functions:
  ```python
  def my_func(a, b, c):
      print(a, b, c)
  
  my_list = [1, 2, 3]
  my_func(*my_list)  # Unpacks list as positional arguments
  
  my_dict = {'a': 1, 'b': 2, 'c': 3}
  my_func(**my_dict)  # Unpacks dict as keyword arguments
  ```

**Use Cases:**
- **Flexible functions**: Don't know how many arguments will be passed
- **Wrapper functions**: Passing arguments to another function
- **API functions**: Accepting various optional parameters

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Can you have a function with only `*args` and `**kwargs`?**
- Yes: `def func(*args, **kwargs):`
- This function accepts any number of any arguments
- Common in decorators and wrapper functions

**Q: What happens if you pass both positional and keyword arguments to `*args`?**
- `*args` only collects positional arguments
- If you mix them: `func(1, 2, 3, x=4)`
  - `1, 2, 3` go to `*args` as tuple `(1, 2, 3)`
  - `x=4` goes to `**kwargs` as `{'x': 4}`

**Q: Can you modify `*args` or `**kwargs`?**
- `*args` is a tuple (immutable) - can't modify directly, would need to convert to list
- `**kwargs` is a dictionary (mutable) - can modify: `kwargs['new_key'] = 'value'`

---

### Q8: What's the difference between `deep copy` and `shallow copy`?

**ANSWER:**
- **Shallow copy**: Creates a new object but references the same nested objects
- **Deep copy**: Creates a new object and recursively copies all nested objects

**CONCEPTS TO UNDERSTAND:**

**Shallow Copy:**
- Only copies the "first level" of the object
- For containers (lists, dicts), creates a new container but keeps references to same nested objects
- If you modify a nested object, both original and copy are affected
- Example:
  ```python
  import copy
  original = [[1, 2], [3, 4]]
  shallow = copy.copy(original)
  
  shallow[0][0] = 999  # Modifies nested list
  print(original)  # [[999, 2], [3, 4]] - Also changed!
  print(shallow)   # [[999, 2], [3, 4]]
  ```
- Methods: `copy.copy()`, `list.copy()`, `[:]` for lists, `.copy()` for dicts

**Deep Copy:**
- Creates a completely independent copy
- Recursively copies all nested objects
- Changes to nested objects don't affect the original
- Example:
  ```python
  import copy
  original = [[1, 2], [3, 4]]
  deep = copy.deepcopy(original)
  
  deep[0][0] = 999  # Modifies nested list
  print(original)  # [[1, 2], [3, 4]] - Unchanged!
  print(deep)      # [[999, 2], [3, 4]]
  ```

**When to Use Each:**
- **Shallow copy**: When you only need to copy the top level, or nested objects are immutable
- **Deep copy**: When you need completely independent copies, especially with mutable nested objects

**Performance:**
- Shallow copy is faster (less work)
- Deep copy is slower (must traverse entire object structure)

**Common Gotcha:**
- For flat lists/dicts, shallow and deep copy behave the same
- Difference only matters with nested structures

**COMMON FOLLOW-UP QUESTIONS:**

**Q: What happens if I do `new_list = old_list`?**
- That's **not a copy at all** - both variables point to the same object
- Any modification affects both:
  ```python
  old_list = [1, 2, 3]
  new_list = old_list  # Not a copy!
  new_list.append(4)
  print(old_list)  # [1, 2, 3, 4] - Also modified!
  ```

> **⚠️ COMMON MISTAKE**: Many beginners think `=` copies a list. It doesn't! It just creates another reference to the same object. Always use `.copy()`, `[:]`, or `copy.deepcopy()` when you need an actual copy.

**Q: Can you do deep copy for custom objects/classes?**
- Yes, `copy.deepcopy()` works with custom classes
- Custom classes can implement `__copy__()` and `__deepcopy__()` methods for custom behavior

**Q: Are there any issues with deep copy?**
- Can be slow for very large/deep structures
- Can fail with circular references (objects that reference each other)
- May copy more than needed (including objects you don't want copied)

---

### Q9: How does Python handle mutable vs immutable objects?

**ANSWER:**
Python divides objects into two categories:
- **Immutable**: Cannot be changed after creation (int, str, tuple, frozenset)
- **Mutable**: Can be changed after creation (list, dict, set)

**CONCEPTS TO UNDERSTAND:**

**Immutable Objects:**
- Once created, the object itself cannot be modified
- Common immutable types: `int`, `float`, `str`, `tuple`, `frozenset`, `bool`
- "Modifying" an immutable object actually creates a new object
- Example:
  ```python
  x = "hello"
  x = x + " world"  # Creates NEW string object, doesn't modify original
  # The original "hello" string object still exists in memory until garbage collected
  ```

**Mutable Objects:**
- Can be modified in-place without creating a new object
- Common mutable types: `list`, `dict`, `set`, custom classes
- Example:
  ```python
  my_list = [1, 2, 3]
  my_list.append(4)  # Modifies existing list object
  # Same object in memory, just changed its contents
  ```

**Why This Matters - Function Arguments:**
- Immutable objects: Passed by value (function can't modify original)
- Mutable objects: Passed by reference (function CAN modify original)
- Example:
  ```python
  def modify_list(lst):
      lst.append(4)  # Modifies original list!
  
  def modify_string(s):
      s = s + " world"  # Creates new string, doesn't modify original
  
  my_list = [1, 2, 3]
  my_string = "hello"
  modify_list(my_list)
  modify_string(my_string)
  print(my_list)    # [1, 2, 3, 4] - Modified!
  print(my_string)  # "hello" - Unchanged!
  ```

**Identity vs Equality:**
- Two immutable objects with same value might be the same object (cached) or different
- Two mutable objects are always different objects, even with same contents
- Example:
  ```python
  a = "hello"
  b = "hello"
  print(a is b)  # Might be True (string interning)
  
  c = [1, 2]
  d = [1, 2]
  print(c is d)  # Always False (different objects)
  ```

**Immutability is Not Absolute:**
- A tuple is immutable, but if it contains a list, you can modify that list:
  ```python
  t = ([1, 2], 3)
  t[0].append(3)  # This works! Modifies the list inside tuple
  # Tuple itself is still immutable, but its contents (if mutable) can change
  ```

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Why are tuples immutable if you can have mutable elements inside?**
- The tuple itself cannot be changed (can't add/remove items, can't reassign items)
- But the tuple stores references to objects
- If those referenced objects are mutable, you can modify them
- The tuple still "points" to the same objects, so it's technically still immutable

**Q: What happens when you modify a mutable argument in a function?**
- The original object is modified - this is often unexpected!
- To avoid this, make a copy inside the function:
  ```python
  def safe_modify(lst):
      lst = lst.copy()  # Work with copy
      lst.append(4)
      return lst
  ```

> **💡 INTERVIEW TIP**: This is a common "gotcha" question. Interviewers often ask: "What's the output of this code?" with mutable default arguments:
> ```python
> def add_item(item, lst=[]):
>     lst.append(item)
>     return lst
> 
> print(add_item(1))  # [1]
> print(add_item(2))  # [1, 2] - Unexpected!
> ```
> The default list is created once and shared across calls. Always use `None` as default: `def add_item(item, lst=None): lst = lst if lst else []`

---

### Q10: What are lambda functions in Python?

**ANSWER:**
Lambda functions are small, anonymous (unnamed) functions that can be defined inline. They're limited to a single expression.

**Syntax:** `lambda arguments: expression`

**CONCEPTS TO UNDERSTAND:**

**Basic Syntax:**
- `lambda` keyword
- Arguments (can have multiple: `lambda x, y: x + y`)
- Colon `:`
- Single expression (what the function returns)
- Example:
  ```python
  # Regular function:
  def add(x, y):
      return x + y
  
  # Lambda equivalent:
  add = lambda x, y: x + y
  
  # Both can be called the same way:
  print(add(2, 3))  # 5
  ```

**When to Use:**
- **As arguments to functions**: `sorted(students, key=lambda s: s.age)`
- **In filter/map/reduce**: `filter(lambda x: x > 0, numbers)`
- **Simple one-liners**: When function is too simple to warrant `def`
- **Callback functions**: Passing small functions to other functions

**Limitations:**
- Can only contain expressions, not statements
- Can't include: `print`, `if-elif-else` (but can use ternary operator), loops, assignments
- Can't have docstrings or annotations
- Harder to debug (no function name in stack traces)

**Lambda vs Regular Functions:**
- **Lambda**: Anonymous, single expression, inline definition
- **Regular function**: Named, multiple statements, can have docstrings, easier to debug

**Common Use Cases:**
```python
# Sorting with custom key:
sorted(list_of_dicts, key=lambda x: x['age'])

# Filtering:
evens = filter(lambda x: x % 2 == 0, numbers)

# Mapping:
squares = map(lambda x: x**2, numbers)
```

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Can lambda functions have default arguments?**
- Yes: `lambda x, y=10: x + y`
- Can be called: `f(5)` (uses default) or `f(5, 20)` (overrides default)

**Q: Can you use lambda instead of if-else?**
- Not `if-elif-else` statements, but you can use ternary operator:
  ```python
  lambda x: "even" if x % 2 == 0 else "odd"
  ```

**Q: When should I avoid lambda?**
- Complex logic (use regular function)
- When function needs to be reused (give it a name!)
- When readability suffers (sometimes regular function is clearer)

**Q: What's the difference between lambda and def?**
- Both create function objects
- Main difference: lambda is expression (can be used inline), def is statement (standalone)
- Lambda is just syntactic sugar - under the hood, Python creates a function object for both

---

### Q11: How does exception handling work in Python?

**ANSWER:**
Python uses `try-except-else-finally` blocks to handle exceptions (errors) that occur during code execution. When an exception occurs, Python stops normal execution and looks for an exception handler.

**CONCEPTS TO UNDERSTAND:**

**Basic Exception Handling:**
```python
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Handle specific exception
    print("Cannot divide by zero")
except Exception as e:
    # Handle any other exception
    print(f"An error occurred: {e}")
```

**Exception Hierarchy:**
- All exceptions inherit from `BaseException`
- Most exceptions inherit from `Exception` (which inherits from `BaseException`)
- `KeyboardInterrupt`, `SystemExit` inherit directly from `BaseException` (rarely caught)
- Specific exceptions: `ZeroDivisionError`, `ValueError`, `TypeError`, `KeyError`, `IndexError`, etc.
- You can catch more specific exceptions first, then more general ones

**Try-Except-Else-Finally:**
```python
try:
    # Code that might raise exception
    file = open("data.txt")
    data = file.read()
except FileNotFoundError:
    # Runs if exception occurs
    print("File not found")
else:
    # Runs if NO exception occurred
    print("File read successfully")
finally:
    # ALWAYS runs, whether exception occurred or not
    file.close()
```

**Raising Exceptions:**
- Use `raise` to manually raise exceptions: `raise ValueError("Invalid input")`
- Can re-raise exceptions: `raise` (without arguments) in an except block

**Custom Exceptions:**
- Create custom exception classes by inheriting from `Exception`:
  ```python
  class CustomError(Exception):
      pass
  
  raise CustomError("Something went wrong")
  ```

**Exception Chaining:**
- When an exception occurs while handling another exception, Python chains them
- Use `raise ... from ...` to preserve exception chain for debugging
- Example:
  ```python
  try:
      data = json.loads(file_content)
  except json.JSONDecodeError as e:
      raise ValueError("Invalid JSON format") from e
      # Preserves original JSONDecodeError in traceback
  ```

**Assert Statement:**
- `assert condition, "error message"` - raises `AssertionError` if condition is False
- Useful for debugging and testing, but can be disabled with `-O` flag
- Don't use for production validation (use explicit `if` and `raise`)

**COMMON FOLLOW-UP QUESTIONS:**

**Q: What's the difference between `except Exception` and `except`?**
- `except Exception`: Catches all exceptions that inherit from `Exception`
- `except`: Catches ALL exceptions, including `KeyboardInterrupt`, `SystemExit` (not recommended)
- **Best practice**: Always specify exception types, avoid bare `except`

**Q: When should I use `else` clause in try-except?**
- When you have code that should only run if no exception occurred
- Alternative to putting it at end of try block (but else is clearer about intent)
- Common pattern: `try` opens resource, `except` handles errors, `else` processes data, `finally` closes resource

**Q: What happens if exception occurs in `finally` block?**
- The original exception is lost (this is a common pitfall)
- The exception from finally block propagates
- Be careful: don't put code that might fail in finally (especially don't close resources that might not be open)

**Q: Can I catch multiple exceptions in one except clause?**
- Yes: `except (ValueError, TypeError):`
- All specified exceptions will be caught by the same handler

---

### Q12: What are dictionaries and how do they work internally?

**ANSWER:**
Dictionaries are mutable, unordered collections of key-value pairs. They're implemented as hash tables, which provides O(1) average-case time complexity for lookups, insertions, and deletions.

**CONCEPTS TO UNDERSTAND:**

**Dictionary Basics:**
- Keys must be hashable (immutable: strings, numbers, tuples of immutables)
- Values can be any type
- Keys are unique (duplicate keys overwrite previous value)
- Python 3.7+ preserves insertion order

**Hash Table Implementation:**
- Dictionaries use hash tables (hash maps) internally
- When you do `dict[key]`, Python:
  1. Hashes the key: `hash(key)` returns an integer
  2. Uses hash to find bucket (slot) in internal array
  3. Stores/retrieves value from that bucket
- This is why lookups are O(1) on average

**Hashable vs Non-Hashable:**
- **Hashable**: int, float, str, tuple (if contains only hashables), frozenset
- **Non-hashable**: list, dict, set (mutable types)
- Why? Hash values must be constant - if object can change, hash would change, breaking dictionary

**Common Dictionary Operations:**
```python
# Access:
value = dict['key']  # Raises KeyError if key doesn't exist
value = dict.get('key', default)  # Returns default if key doesn't exist

# Check existence:
if 'key' in dict:  # O(1) lookup

# Iteration:
for key in dict:  # Iterate keys
for key, value in dict.items():  # Iterate key-value pairs
for value in dict.values():  # Iterate values
```

**Dictionary Methods:**
- `dict.keys()` - Returns view of keys
- `dict.values()` - Returns view of values
- `dict.items()` - Returns view of key-value pairs
- `dict.update(other)` - Merges another dict into this one
- `dict.pop(key, default)` - Removes and returns value
- `dict.setdefault(key, default)` - Gets value, sets default if key missing

**Dictionary Comprehensions:**
- Similar to list comprehensions, but create dictionaries:
  ```python
  # Create dict from list
  squares = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
  
  # Filter and transform
  even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
  
  # Swap keys and values
  inverted = {v: k for k, v in original_dict.items()}
  ```

**Hash Collisions:**
- When two different keys produce the same hash value
- Python handles this internally using open addressing (probing for next available slot)
- Example: Two keys might hash to same bucket, but Python finds alternative slots
- This is why worst-case lookup can be O(n) (if all keys collide), but average is O(1)
- In practice, Python's hash function is designed to minimize collisions

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Why can't lists be dictionary keys?**
- Lists are mutable - if you changed the list, its hash would change
- This would break the dictionary (key wouldn't be found in correct bucket)
- If you need a list as a key, convert it to tuple first

**Q: What's the time complexity of dictionary operations?**
- Average case: O(1) for lookup, insert, delete
- Worst case: O(n) if many hash collisions (rare)
- Iteration: O(n) where n is number of items

**Q: What's the difference between `dict.get(key)` and `dict[key]`?**
- `dict[key]`: Raises `KeyError` if key doesn't exist
- `dict.get(key)`: Returns `None` if key doesn't exist
- `dict.get(key, default)`: Returns `default` if key doesn't exist
- Use `get()` when you're not sure key exists, use `[]` when you expect it to exist

**Q: How does dictionary preserve insertion order (Python 3.7+)?**
- Internally uses a combination of hash table and insertion-order linked list
- The order is maintained separately from the hash buckets
- This is a CPython implementation detail - order is now guaranteed by the language spec

---

### Q13: What are sets in Python? How do they differ from lists and tuples?

**ANSWER:**
Sets are unordered, mutable collections of unique elements. They're implemented as hash tables (like dictionaries), providing fast membership testing and set operations.

**CONCEPTS TO UNDERSTAND:**

**Set Characteristics:**
- **Unordered**: No indexing, no guarantee of order (though Python 3.7+ may preserve insertion order in some implementations)
- **Mutable**: Can add/remove elements
- **Unique elements**: No duplicates allowed
- **Hashable elements only**: Elements must be immutable (same rule as dict keys)

**Creating Sets:**
```python
# Empty set (note: {} is a dict, not a set!)
empty_set = set()

# Set with elements:
my_set = {1, 2, 3, 4}
# or
my_set = set([1, 2, 3, 4])
```

**Set Operations:**
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union:
set1 | set2  # or set1.union(set2) -> {1, 2, 3, 4, 5}

# Intersection:
set1 & set2  # or set1.intersection(set2) -> {3}

# Difference:
set1 - set2  # or set1.difference(set2) -> {1, 2}

# Symmetric Difference (elements in either set, but not both):
set1 ^ set2  # or set1.symmetric_difference(set2) -> {1, 2, 4, 5}
```

**Membership Testing:**
- `x in set` - O(1) average case (very fast!)
- `x in list` - O(n) worst case (must check each element)
- This is why sets are great for removing duplicates and fast lookups

**Common Use Cases:**
- Removing duplicates from a list: `unique = list(set(duplicates))`
- Fast membership testing
- Set operations (union, intersection, etc.)
- Tracking seen/unseen items

**Sets vs Lists vs Tuples:**
- **Sets**: Unordered, unique, mutable, fast membership testing
- **Lists**: Ordered, duplicates allowed, mutable, indexed
- **Tuples**: Ordered, duplicates allowed, immutable, indexed

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Why are sets faster for membership testing than lists?**
- Sets use hash tables - O(1) average lookup time
- Lists must check each element sequentially - O(n) worst case
- For large collections, sets are dramatically faster

**Q: Can sets contain lists?**
- No, because lists are mutable and not hashable
- Sets can contain tuples (if tuples contain only hashable elements)
- Example: `my_set = {(1, 2), (3, 4)}` works, but `my_set = {[1, 2]}` raises TypeError

**Q: What's a frozenset?**
- An immutable version of a set
- Hashable (can be used as dict key or set element)
- Created with: `frozen = frozenset([1, 2, 3])`
- Once created, cannot add/remove elements

**Q: How do you find common elements between two lists?**
- Convert to sets and use intersection: `set(list1) & set(list2)`
- Or: `set(list1).intersection(list2)`
- Much faster than nested loops!

---

### Q14: What are Python's string methods and string immutability?

**ANSWER:**
Strings in Python are immutable sequences of Unicode characters. You cannot modify a string in-place - operations that appear to modify strings actually create new string objects.

**CONCEPTS TO UNDERSTAND:**

**String Immutability:**
- Once created, a string cannot be changed
- Operations like `upper()`, `replace()`, `strip()` return NEW strings
- Example:
  ```python
  s = "hello"
  s.upper()  # Returns "HELLO" but s is still "hello"
  s = s.upper()  # Now s is "HELLO" (reassigned to new object)
  ```

**Common String Methods:**
```python
s = "  Hello World  "

# Case conversion:
s.upper()        # "  HELLO WORLD  "
s.lower()        # "  hello world  "
s.capitalize()   # "  hello world  " (only first char)
s.title()        # "  Hello World  " (each word capitalized)

# Stripping whitespace:
s.strip()        # "Hello World" (removes leading/trailing)
s.lstrip()       # "Hello World  " (left strip)
s.rstrip()       # "  Hello World" (right strip)

# Finding/replacing:
s.find("World")   # Returns index or -1 if not found
s.index("World") # Returns index or raises ValueError
s.replace("World", "Python")  # "  Hello Python  "

# Checking:
s.startswith("  ")  # True
s.endswith("  ")    # True
s.isdigit()         # False
s.isalpha()         # False (has spaces)
```

**String Formatting:**
- Old style: `"%s %d" % ("hello", 5)`
- `.format()`: `"{} {}".format("hello", 5)`
- f-strings (Python 3.6+): `f"{name} is {age} years old"` (preferred!)
- f-strings are fastest and most readable

**String Operations:**
```python
# Concatenation:
"hello" + " " + "world"  # Creates new string
"hello" * 3              # "hellohellohello"

# Membership:
"lo" in "hello"          # True

# Slicing (creates new string):
"hello"[1:4]             # "ell"
```

**Why Immutability?**
- Allows string interning (Python can cache/reuse string objects)
- Thread-safe (can't be modified, so safe to share)
- Can be used as dictionary keys
- More predictable behavior

**String Encoding (Advanced):**
- Python 3 strings are Unicode by default
- `str` type stores Unicode characters
- Use `encode()` to convert to bytes, `decode()` to convert bytes to str

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Is string concatenation with `+` efficient?**
- No, for many concatenations - creates new string each time
- Better: Use `.join()` for multiple strings: `"".join(list_of_strings)`
- `+` is fine for few concatenations, but `join()` is better for loops

**Q: What's the difference between `find()` and `index()`?**
- Both find substring position
- `find()` returns -1 if not found
- `index()` raises ValueError if not found
- Use `find()` if you want to check existence, `index()` if you're sure it exists

**Q: Can you modify strings with slicing?**
- No, slicing creates a new string
- To "modify" a string, you'd do: `s = s[:5] + "X" + s[6:]` (creates new string)
- Or use methods like `replace()` which also create new strings

**Q: What's the difference between `==` and `is` for strings?**
- `==` compares values
- `is` compares identity (same object in memory)
- Python may intern (cache) some strings, but don't rely on it
- Always use `==` for string comparison

---

### Q15: What is the `pass` statement in Python?

**ANSWER:**
`pass` is a null operation - it does nothing. It's used as a placeholder when syntactically some code is required, but you don't want to execute anything.

**CONCEPTS TO UNDERSTAND:**

**When to Use `pass`:**
- Empty function/class definitions (Python requires something in the body)
- Placeholder for code you'll implement later
- In exception handlers when you want to silently catch exceptions
- In conditional blocks you're not ready to implement

**Examples:**
```python
# Empty function (syntax requires body):
def my_function():
    pass  # TODO: implement later

# Empty class:
class MyClass:
    pass  # Will add methods later

# Silent exception handling:
try:
    risky_operation()
except SomeError:
    pass  # Ignore this error

# Placeholder in if statement:
if condition:
    pass  # Will handle later
else:
    do_something()
```

**`pass` vs Other Placeholders:**
- `pass`: Does nothing, placeholder
- `...` (Ellipsis): Also does nothing, sometimes used in modern Python for type stubs/protocols
  ```python
  def future_function():
      ...  # Modern style, especially in type annotations
  
  class AbstractClass:
      def method(self) -> int:
          ...  # Preferred in protocol definitions
  ```
- Comments: `# TODO` - just a comment, not executable code

**Why Not Just Leave It Empty?**
- Python requires at least one statement in function/class bodies
- Empty blocks would cause `IndentationError` or `SyntaxError`
- `pass` or `...` satisfies the syntax requirement

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Is `pass` the same as a comment?**
- No! `pass` is executable code (does nothing, but still executed)
- Comments are ignored by Python interpreter
- `pass` satisfies syntax requirements, comments don't

**Q: When would you use `pass` in exception handling?**
- When you want to catch an exception but don't need to do anything
- Example: Catching `KeyboardInterrupt` but allowing program to exit naturally
- Be careful: silent exception handling can hide bugs!

**Q: What's the difference between `pass`, `continue`, and `break`?**
- `pass`: Does nothing, continues to next line
- `continue`: Skips remaining code in loop, goes to next iteration
- `break`: Exits the loop entirely

---

## 2. ADVANCED PYTHON CONCEPTS

### Q16: What are decorators in Python? How do they work?

**ANSWER:**
Decorators are functions that modify or extend the behavior of other functions without permanently modifying them. They're a way to wrap functions with additional functionality.

**CONCEPTS TO UNDERSTAND:**

**Basic Decorator Syntax:**
```python
def my_decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function
# Hello!
# After function
```

**How Decorators Work:**
- `@decorator_name` is syntactic sugar
- `@my_decorator` before `def say_hello()` is equivalent to: `say_hello = my_decorator(say_hello)`
- The decorator function receives the original function as argument
- It returns a new function (wrapper) that replaces the original

**Decorator with Arguments:**
```python
def repeat(num_times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(num_times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello {name}")

greet("Alice")  # Prints 3 times
```

**Decorator with Arguments Explained:**
- `@repeat(3)` actually calls `repeat(3)` first
- `repeat(3)` returns the `decorator` function
- That `decorator` function receives the original `greet` function
- The decorator returns `wrapper` which replaces `greet`

**Common Use Cases:**
- **Timing functions**: Measure execution time
- **Logging**: Log function calls and arguments
- **Authentication**: Check permissions before executing
- **Caching/Memoization**: Cache function results
- **Validation**: Validate function arguments

**Preserving Function Metadata:**
- Decorators can hide original function's metadata (name, docstring)
- Use `functools.wraps` to preserve it:
  ```python
  from functools import wraps
  
  def my_decorator(func):
      @wraps(func)
      def wrapper(*args, **kwargs):
          return func(*args, **kwargs)
      return wrapper
  ```

**Class-based Decorators:**
- Decorators can also be classes (implement `__call__` method)
- Useful when you need to maintain state between calls

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Can a function have multiple decorators?**
- Yes! Applied bottom to top:
  ```python
  @decorator1
  @decorator2
  def my_func():
      pass
  ```
  This is equivalent to: `my_func = decorator1(decorator2(my_func))`

**Q: What's the difference between `@staticmethod` and `@classmethod` decorators?**
- `@staticmethod`: No access to class or instance - just a function in class namespace
- `@classmethod`: Receives class as first argument (`cls`), can access class variables
- Both can be called on class or instance

**Q: How do you pass arguments to a decorator?**
- Use a decorator factory: a function that returns a decorator
- The outer function receives decorator arguments, returns the actual decorator
- Example shown above with `repeat(num_times)`

**Q: Can decorators modify function arguments or return values?**
- Yes! Wrapper function can:
  - Modify arguments: `wrapper(*args, **kwargs)` can change args before calling `func`
  - Modify return value: `result = func(*args, **kwargs)` then return modified result
  - Or replace function entirely: don't call `func` at all!

---

### Q17: Explain generators and the `yield` keyword.

**ANSWER:**
Generators are functions that return an iterator. Instead of using `return`, they use `yield` to produce values one at a time, on-demand. They're memory-efficient because they don't store all values in memory at once.

**CONCEPTS TO UNDERSTAND:**

**Generator Function:**
```python
def count_up_to(n):
    count = 1
    while count <= n:
        yield count  # Yields value and pauses
        count += 1   # Resumes here when next() is called

# Usage:
counter = count_up_to(5)
print(next(counter))  # 1
print(next(counter))  # 2
for num in counter:    # 3, 4, 5
    print(num)
```

**How `yield` Works:**
- When function hits `yield`, it:
  1. Returns the value
  2. **Pauses** execution (saves state)
  3. Resumes when `next()` is called again
- Unlike `return`, the function doesn't end - it remembers where it paused

**Generator vs Regular Function:**
```python
# Regular function - creates entire list in memory:
def squares_list(n):
    result = []
    for i in range(n):
        result.append(i**2)
    return result  # All values in memory

# Generator - produces values on-demand:
def squares_gen(n):
    for i in range(n):
        yield i**2  # One value at a time
```

**Memory Efficiency:**
- List: `[0, 1, 4, 9, 16, ...]` - all stored in memory
- Generator: Produces next value only when requested - huge memory savings for large sequences
- Example: `range(1000000)` as generator vs `list(range(1000000))`

**Generator Expressions:**
- Similar to list comprehensions but use parentheses:
  ```python
  # List comprehension (creates list):
  squares = [x**2 for x in range(10)]
  
  # Generator expression (creates generator):
  squares = (x**2 for x in range(10))
  ```
- Generator expressions are lazy - don't compute until iterated

**When to Use Generators:**
- ✅ Large sequences (memory efficiency)
- ✅ Infinite sequences (can't store all values)
- ✅ Processing data streams (file reading, network data)
- ❌ When you need random access (generators are sequential)
- ❌ When you need all values multiple times (generator exhausted after iteration)

**Generator Methods:**
- `.send(value)`: Send value into generator, resumes execution
- `.throw(exception)`: Raise exception in generator
- `.close()`: Close generator

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Can you iterate over a generator multiple times?**
- No! Once exhausted, generator is done
- You need to create a new generator: `gen = my_generator()` then iterate
- Lists can be iterated multiple times

**Q: What's the difference between `yield` and `return`?**
- `return`: Terminates function, returns value, function ends
- `yield`: Pauses function, returns value, function can resume
- Function with `yield` becomes a generator function automatically

**Q: Can a generator function have multiple `yield` statements?**
- Yes! Function yields value at each `yield`, pauses, resumes at next line
- Example:
  ```python
  def my_gen():
      yield 1
      yield 2
      yield 3
  ```

**Q: When would you use a generator vs a list?**
- Use generator: Large datasets, memory concerns, one-time iteration, infinite sequences
- Use list: Need random access, need to iterate multiple times, small datasets, need list methods

---

### Q18: What is the Global Interpreter Lock (GIL)?

**ANSWER:**
The GIL is a mutex (lock) in CPython that allows only one thread to execute Python bytecode at a time. This prevents multiple threads from executing Python code simultaneously, even on multi-core processors.

**CONCEPTS TO UNDERSTAND:**

**What GIL Does:**
- CPython (standard Python) has a GIL that protects access to Python objects
- Only one thread can hold the GIL and execute Python code at a time
- Other threads must wait for the GIL to be released

**Why GIL Exists:**
- Simplifies memory management (reference counting)
- Makes CPython implementation easier and safer
- Prevents race conditions in reference counting
- Makes C extensions easier to write (don't need to worry about thread safety)

**Impact on Multithreading:**
- **CPU-bound tasks**: GIL prevents true parallel execution - threads take turns
- **I/O-bound tasks**: Threads release GIL during I/O operations (file read, network call, etc.)
- For CPU-bound work, multithreading doesn't help much (due to GIL)
- For I/O-bound work, multithreading can still provide speedup

**Example:**
```python
# CPU-bound: Threading won't help (GIL limits parallelism)
import threading
def cpu_task():
    # Heavy computation - GIL prevents parallel execution
    pass

# I/O-bound: Threading helps (GIL released during I/O)
def io_task():
    # File read, network request - GIL released during wait
    pass
```

**Workarounds:**
- **Multiprocessing**: Use separate processes (each has own GIL)
- **Alternative Python implementations**: Jython, IronPython don't have GIL (but less common)
- **C extensions**: Can release GIL during heavy computation
- **Async/Await**: For I/O-bound concurrent tasks

**Multiprocessing vs Multithreading:**
- **Multithreading**: Multiple threads, shared memory, limited by GIL for CPU tasks
- **Multiprocessing**: Multiple processes, separate memory, no GIL limitation
- Multiprocessing has more overhead (process creation, inter-process communication)

**GIL and Concurrency:**
- GIL is per-process, so multiple processes can run in parallel
- Async/await (asyncio) works around GIL by using single thread with cooperative multitasking

**COMMON FOLLOW-UP QUESTIONS:**

**Q: Does GIL affect all Python code?**
- Only CPython (standard Python) has GIL
- Jython (Java), IronPython (.NET) don't have GIL
- C extensions can release GIL during native code execution

**Q: Why not remove the GIL?**
- Would require major CPython rewrite
- Would make reference counting more complex (need atomic operations)
- Would hurt single-threaded performance
- Several attempts made, but trade-offs haven't been worth it yet

**Q: How does asyncio work with GIL?**
- asyncio uses cooperative multitasking (single thread)
- Tasks yield control voluntarily during I/O waits
- No thread switching, so GIL isn't the bottleneck
- Great for I/O-bound concurrent tasks

**Q: When should I use threading vs multiprocessing?**
- **Threading**: I/O-bound tasks (network requests, file I/O)
- **Multiprocessing**: CPU-bound tasks (heavy computation, image processing)
- Multiprocessing has more overhead, but can use multiple CPU cores effectively

> **💡 INTERVIEW TIP**: GIL questions are common in senior SDET interviews. Be ready to explain:
> - Why multithreading doesn't speed up CPU-heavy Python code
> - When you'd choose multiprocessing vs threading vs asyncio
> - Real-world example: "If you're testing APIs, use threading or asyncio. If you're processing images/data, use multiprocessing."
> - Shows you understand performance optimization for test automation

---

## 📊 PROGRESS TRACKER

**Document Status**: 🟡 In Progress

### Completed Sections:
- ✅ **Python Fundamentals**: 15/15 questions (100% complete)
  - Q1: Lists vs Tuples
  - Q2: `==` vs `is`
  - Q3: Garbage Collection
  - Q4: `append()` vs `extend()`
  - Q5: List Comprehensions
  - Q6: LEGB Scope Rule
  - Q7: `*args` and `**kwargs`
  - Q8: Deep vs Shallow Copy
  - Q9: Mutable vs Immutable
  - Q10: Lambda Functions
  - Q11: Exception Handling
  - Q12: Dictionaries & Hash Tables
  - Q13: Sets
  - Q14: String Methods & Immutability
  - Q15: `pass` Statement

- 🟡 **Advanced Python Concepts**: 3/12-15 questions (20% complete)
  - Q16: Decorators
  - Q17: Generators & `yield`
  - Q18: Global Interpreter Lock (GIL)
  - ⬜ Q19-Q30: To be added

- ⬜ **OOP in Python**: 0/8-10 questions (Not started)
  - Topics to cover: Classes, Inheritance, MRO, Polymorphism, Encapsulation, Special Methods

- ⬜ **Python Internals & Behaviors**: 0/5-8 questions (Not started)
  - Topics to cover: Imports, `__name__`, Module system, Bytecode

### Overall Progress: 18/40 questions (45%)

---

## 📝 NEXT STEPS

To continue building this document:
1. Add remaining Advanced Python questions (Context Managers, Iterators, Closures, etc.)
2. Create OOP in Python section
3. Create Python Internals section
4. Add more interview tips and common mistakes throughout

---

*[More questions to be added in future sessions...]*
