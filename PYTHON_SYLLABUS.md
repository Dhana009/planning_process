# Python Interview Syllabus - SDET/Automation Engineer

> **Purpose**: Comprehensive checklist of Python topics and actual interview questions you MUST master before interviews
> **Time Allocation**: ~40 hours total

---

## 📋 TABLE OF CONTENTS
1. [Python Fundamentals](#1-python-fundamentals)
2. [Advanced Python Concepts](#2-advanced-python-concepts)
3. [Data Structures & Algorithms](#3-data-structures--algorithms)
4. [Python for Automation](#4-python-for-automation)
5. [OOP & Design Patterns](#5-oop--design-patterns)
6. [Common Coding Interview Problems](#6-common-coding-interview-problems)
7. [Actual Interview Questions](#7-actual-interview-questions)

---

## 1. PYTHON FUNDAMENTALS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Core Concepts
- [ ] **Data Types & Variables**
  - Strings (immutability, string methods, formatting)
  - Integers, Floats, Boolean
  - Lists vs Tuples vs Sets vs Dictionaries
  - Type conversion and type hints
  
- [ ] **Control Structures**
  - If-elif-else statements
  - For loops, While loops
  - Break, Continue, Pass
  - List comprehensions, Dictionary comprehensions
  
- [ ] **Functions**
  - Function definition and calling
  - Parameters: positional, keyword, default
  - `*args` and `**kwargs`
  - Lambda functions
  - Scope: local, global, nonlocal
  - Return statements and multiple returns

- [ ] **Exception Handling**
  - Try-except-else-finally blocks
  - Raising exceptions
  - Custom exceptions
  - Exception hierarchy

### Interview Questions to Prepare:
1. **Q: What's the difference between lists and tuples?**
   - Lists are mutable, tuples are immutable
   - Lists use `[]`, tuples use `()`
   - Tuples are faster and can be used as dictionary keys
   
2. **Q: Explain the difference between `==` and `is` in Python**
   - `==` compares values
   - `is` compares object identity (memory addresses)
   
3. **Q: How does Python's garbage collection work?**
   - Reference counting
   - Cyclic garbage collector
   - Generational garbage collection

---

## 2. ADVANCED PYTHON CONCEPTS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Topics
- [ ] **Decorators**
  - Function decorators
  - Class decorators
  - Decorators with parameters
  - Built-in decorators (@staticmethod, @classmethod, @property)
  
- [ ] **Generators & Iterators**
  - Generator functions (yield keyword)
  - Generator expressions
  - Iterator protocol (__iter__, __next__)
  - Memory efficiency of generators
  
- [ ] **Context Managers**
  - `with` statement
  - Creating custom context managers
  - `contextlib` module
  
- [ ] **File Handling**
  - Reading/writing text files
  - Reading/writing CSV, JSON files
  - Working with file paths (os.path, pathlib)
  
- [ ] **Regular Expressions**
  - `re` module basics
  - Pattern matching
  - Findall, search, match, sub
  
- [ ] **Multithreading & Multiprocessing**
  - Threading module
  - Global Interpreter Lock (GIL)
  - Multiprocessing module
  - When to use threading vs multiprocessing

### Interview Questions to Prepare:
1. **Q: What are Python decorators? How would you create one?**
   ```python
   def my_decorator(func):
       def wrapper():
           print("Before function")
           func()
           print("After function")
       return wrapper
   ```

2. **Q: Explain the Global Interpreter Lock (GIL) in Python**
   - GIL prevents multiple threads from executing Python bytecode simultaneously
   - Only one thread can execute at a time (CPU-bound)
   - I/O-bound operations can still benefit from threading
   - Use multiprocessing for CPU-bound parallel tasks

3. **Q: What's the difference between `yield` and `return`?**
   - `return` terminates function and returns value
   - `yield` pauses function, returns value, allows resumption
   - Generators use `yield` for memory-efficient iteration

4. **Q: Write a generator function to yield Fibonacci numbers up to `n`**
   ```python
   def fibonacci(n):
       a, b = 0, 1
       while a < n:
           yield a
           a, b = b, a + b
   ```

---

## 3. DATA STRUCTURES & ALGORITHMS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Data Structures
- [ ] **Lists & Arrays**
  - Array operations (append, insert, pop, remove)
  - Slicing
  - List methods
  - Time complexity of operations

- [ ] **Stacks & Queues**
  - Stack implementation (LIFO)
  - Queue implementation (FIFO)
  - Using `collections.deque`
  
- [ ] **Linked Lists**
  - Singly linked list
  - Doubly linked list
  - Common operations
  
- [ ] **Trees**
  - Binary trees
  - Binary search trees
  - Tree traversal (inorder, preorder, postorder)
  
- [ ] **Graphs**
  - Graph representation (adjacency list/matrix)
  - BFS and DFS
  - Graph algorithms basics

- [ ] **Hash Tables (Dictionaries)**
  - How dictionaries work internally
  - Hash collisions
  - Dictionary methods and operations

### Algorithms
- [ ] **Sorting Algorithms**
  - Bubble sort
  - Quick sort
  - Merge sort
  - Built-in sort() and sorted()
  
- [ ] **Searching Algorithms**
  - Linear search
  - Binary search
  - Time complexity (O(n), O(log n))
  
- [ ] **Recursion**
  - Recursive functions
  - Base cases
  - Stack overflow considerations
  
- [ ] **Dynamic Programming Basics**
  - Memoization
  - Tabulation
  - Common DP problems

### Interview Coding Problems:
1. **Q: Implement a binary search algorithm in Python**
   ```python
   def binary_search(arr, target):
       left, right = 0, len(arr) - 1
       while left <= right:
           mid = (left + right) // 2
           if arr[mid] == target:
               return mid
           elif arr[mid] < target:
               left = mid + 1
           else:
               right = mid - 1
       return -1
   ```

2. **Q: Write a function to reverse a linked list**
3. **Q: Find the largest element in a list without using max()**
4. **Q: Check if a string is a palindrome**
5. **Q: Write a function to merge two sorted lists into one sorted list**

---

## 4. PYTHON FOR AUTOMATION
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Scripting & Automation
- [ ] **File Operations**
  - Reading/writing files
  - Working with directories
  - File manipulation scripts
  
- [ ] **Working with JSON**
  - Parsing JSON
  - Creating JSON
  - JSON validation
  
- [ ] **Working with CSV**
  - Reading CSV files
  - Writing CSV files
  - CSV parsing and manipulation
  
- [ ] **Working with Excel**
  - `openpyxl` or `pandas` for Excel files
  - Reading/writing Excel data

### API Interaction (Automation Context)
- [ ] **Requests Library**
  - GET, POST, PUT, DELETE requests
  - Headers and authentication
  - Response handling
  - Error handling in API calls
  
- [ ] **JSON Handling**
  - Parsing API responses
  - Validating JSON structure
  - Extracting data from nested JSON

### Interview Questions to Prepare:
1. **Q: Write a function to fetch data from an API endpoint using Python's requests and handle possible errors**
   ```python
   import requests
   
   def fetch_api_data(url):
       try:
           response = requests.get(url, timeout=10)
           response.raise_for_status()
           return response.json()
       except requests.exceptions.RequestException as e:
           print(f"Error fetching data: {e}")
           return None
   ```

2. **Q: How do you handle file operations and what's best practice?**
   - Use context managers (`with` statement)
   - Handle file not found exceptions
   - Close files properly

---

## 5. OOP & DESIGN PATTERNS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Object-Oriented Programming
- [ ] **Classes & Objects**
  - Class definition
  - Instance variables vs Class variables
  - Instance methods vs Class methods vs Static methods
  - `self` parameter
  
- [ ] **Inheritance**
  - Single inheritance
  - Multiple inheritance
  - Method Resolution Order (MRO)
  - `super()` function
  
- [ ] **Polymorphism**
  - Method overriding
  - Duck typing
  - Operator overloading
  
- [ ] **Encapsulation**
  - Private attributes (name mangling)
  - Protected attributes
  - Properties and getters/setters
  
- [ ] **Special Methods (Dunder Methods)**
  - `__init__`, `__str__`, `__repr__`
  - `__len__`, `__getitem__`, `__setitem__`
  - `__eq__`, `__lt__`, etc.

### Design Patterns (Common in Automation)
- [ ] **Singleton Pattern**
  - When and why to use
  - Implementation in Python
  
- [ ] **Factory Pattern**
  - Creating objects without specifying exact class
  - Useful for test framework design
  
- [ ] **Page Object Model (POM)**
  - Not a Python concept, but often implemented in Python
  - Separation of page logic and test logic
  - Class-based structure for pages

### Interview Questions to Prepare:
1. **Q: What is the Singleton pattern? How do you implement it in Python?**
   ```python
   class Singleton:
       _instance = None
       
       def __new__(cls):
           if cls._instance is None:
               cls._instance = super().__new__(cls)
           return cls._instance
   ```

2. **Q: Explain inheritance vs composition in Python**
   - Inheritance: "is-a" relationship
   - Composition: "has-a" relationship
   - When to use each

3. **Q: What's the difference between `@staticmethod` and `@classmethod`?**
   - `@staticmethod`: No access to class or instance, just a function in class namespace
   - `@classmethod`: Receives class as first argument, can access class variables

---

## 6. COMMON CODING INTERVIEW PROBLEMS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Must-Practice Problems:
- [ ] **String Manipulation**
  - [ ] Reverse a string
  - [ ] Check if palindrome
  - [ ] Count character frequency
  - [ ] Find longest substring without repeating characters
  - [ ] Anagrams check
  
- [ ] **List/Array Problems**
  - [ ] Find duplicates in a list
  - [ ] Merge two sorted lists
  - [ ] Find maximum/minimum without built-in functions
  - [ ] Two sum problem
  - [ ] Rotate array
  - [ ] Remove duplicates from sorted array
  
- [ ] **Dictionary Problems**
  - [ ] Count word frequency
  - [ ] Group anagrams
  - [ ] Find common elements between lists
  
- [ ] **Algorithm Problems**
  - [ ] Binary search variations
  - [ ] Fibonacci sequence (recursive and iterative)
  - [ ] Factorial calculation
  - [ ] Reverse a linked list
  - [ ] Detect cycle in linked list
  
- [ ] **Real-World Automation Problems**
  - [ ] Parse and validate JSON structure
  - [ ] Read CSV and filter data
  - [ ] Extract data from nested dictionary
  - [ ] Log parsing and analysis

---

## 7. ACTUAL INTERVIEW QUESTIONS
**Status**: ⬜ Not Started | 🟡 In Progress | ✅ Complete

### Python Fundamentals Questions:
- [ ] Q: Explain the difference between `deep copy` and `shallow copy`
  ```python
  import copy
  # Shallow copy: Creates new object but references nested objects
  shallow = copy.copy(original)
  # Deep copy: Creates new object and recursively copies nested objects
  deep = copy.deepcopy(original)
  ```

- [ ] Q: How does Python manage memory?
- [ ] Q: What are Python's built-in data structures and their use cases?
- [ ] Q: Explain list comprehensions with an example
- [ ] Q: What's the difference between `append()` and `extend()` in lists?

### Advanced Python Questions:
- [ ] Q: What are decorators? Write a decorator that measures function execution time
  ```python
  import time
  def timing_decorator(func):
      def wrapper(*args, **kwargs):
          start = time.time()
          result = func(*args, **kwargs)
          end = time.time()
          print(f"{func.__name__} took {end - start} seconds")
          return result
      return wrapper
  ```

- [ ] Q: Explain GIL and its impact on multithreading
- [ ] Q: When would you use generators instead of lists?
- [ ] Q: What are context managers? Write a custom one

### OOP Questions:
- [ ] Q: Explain method resolution order (MRO) in Python
- [ ] Q: What's the difference between `__str__` and `__repr__`?
- [ ] Q: How does multiple inheritance work in Python?
- [ ] Q: Explain the use of `super()` in inheritance

### Automation-Specific Python Questions:
- [ ] Q: How would you handle exceptions in an automation script?
- [ ] Q: Write code to read a JSON file and extract specific data
- [ ] Q: How do you make API calls thread-safe in Python?
- [ ] Q: Write a function that validates JSON structure before parsing

### Coding Problems (Recent Interview Questions):
- [ ] **Q: Write a function that merges two sorted lists into one sorted list**
  ```python
  def merge_sorted_lists(list1, list2):
      result = []
      i, j = 0, 0
      while i < len(list1) and j < len(list2):
          if list1[i] < list2[j]:
              result.append(list1[i])
              i += 1
          else:
              result.append(list2[j])
              j += 1
      result.extend(list1[i:])
      result.extend(list2[j:])
      return result
  ```

- [ ] Q: How do you handle elements with dynamic IDs that change each session?
  - Use more stable locators (XPath with text, CSS selectors with attributes)
  - Use partial matching
  - Use parent-child relationships

- [ ] Q: Write a function to count word frequency from a text file
- [ ] Q: Implement a stack using Python list
- [ ] Q: Find the second largest number in a list

---

## 📝 NOTES & PRACTICE STRATEGY

### Practice Platforms:
- LeetCode (Python category)
- HackerRank (Python section)
- CodeSignal
- Pramp (mock interviews)

### Key Focus Areas:
1. **String manipulation** - Very common in coding rounds
2. **List/dictionary operations** - Core Python skills
3. **OOP concepts** - Shows senior-level understanding
4. **Exception handling** - Critical for automation scripts
5. **Code efficiency** - Time/space complexity awareness

### Before Interview Checklist:
- [ ] Can explain all fundamental concepts verbally
- [ ] Can write code for common algorithms without lookup
- [ ] Understands time/space complexity of solutions
- [ ] Can debug code issues quickly
- [ ] Knows Python best practices (PEP 8)
- [ ] Has practiced explaining code while writing

---

## 🎯 PROGRESS TRACKER

**Overall Progress**: 0% Complete

- Python Fundamentals: 0/4 sections
- Advanced Concepts: 0/6 topics
- Data Structures: 0/6 structures
- Algorithms: 0/4 categories
- Automation Topics: 0/3 areas
- OOP & Patterns: 0/4 concepts
- Coding Problems: 0/20 problems
- Interview Questions: 0/25 questions

---

**Last Updated**: [Track your progress by updating checkboxes as you complete each topic]

