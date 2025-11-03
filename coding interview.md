# Python Coding Round Syllabus - SDET/Automation Engineer
## Complete Interview Preparation Guide

> **Goal**: Pass coding rounds in SDET/QA Automation interviews at ANY cost
> **Total Problems**: 50 must-know problems with solutions
> **Time Needed**: 40-50 hours of focused practice
> **Success Rate**: Master these → Pass 90%+ of SDET coding interviews

---

## 📋 TABLE OF CONTENTS

1. [How to Use This Guide](#how-to-use-this-guide)
2. [Problem-Solving Strategy](#problem-solving-strategy)
3. [String Problems](#section-1-string-problems) (12 problems)
4. [List/Array Problems](#section-2-listarray-problems) (15 problems)
5. [Dictionary/HashMap Problems](#section-3-dictionaryhashmap-problems) (10 problems)
6. [Algorithm Problems](#section-4-algorithm-problems) (8 problems)
7. [Logic & Math Problems](#section-5-logic--math-problems) (5 problems)
8. [Practice Schedule](#practice-schedule)
9. [Interview Day Tips](#interview-day-tips)

---

## HOW TO USE THIS GUIDE

### Step-by-Step Approach:
1. **Read the problem** - Understand what's being asked
2. **Try solving it yourself** (10-15 min) - Don't look at solution immediately
3. **Check the solution** - Compare with your approach
4. **Understand the explanation** - Know WHY the solution works
5. **Code it yourself** - Type the solution from memory
6. **Practice variations** - Try the follow-up problems

### Daily Practice Plan:
- **Days 1-15**: 3 problems/day = 45 problems
- **Days 16-20**: Review + practice variations
- **Days 21-25**: Solve all problems again without looking
- **Days 26-30**: Mock interviews + challenging variations

### Success Metrics:
- ✅ Can solve 80% of problems without hints
- ✅ Can explain your solution clearly
- ✅ Can identify time/space complexity
- ✅ Can handle variations/follow-ups

---

## PROBLEM-SOLVING STRATEGY

### The 4-Step Interview Approach:

**1. UNDERSTAND THE PROBLEM (2 min)**
- Read carefully
- Ask clarifying questions
- Confirm input/output format
- Check edge cases

**2. PLAN YOUR APPROACH (3 min)**
- Think of brute force first (easier to optimize later)
- Consider data structures to use
- Think about edge cases
- Estimate time/space complexity

**3. CODE THE SOLUTION (10-15 min)**
- Write clean, readable code
- Use meaningful variable names
- Add comments for complex logic
- Handle edge cases

**4. TEST & OPTIMIZE (5 min)**
- Test with example inputs
- Test edge cases (empty input, single element, etc.)
- Discuss time/space complexity
- Mention possible optimizations

### Common Patterns to Recognize:

1. **Two Pointers**: Use when dealing with sorted arrays or strings
2. **Hash Maps**: Use for frequency counting, lookups, grouping
3. **Sliding Window**: Use for subarray/substring problems
4. **In-place Operations**: Modify data structure without extra space
5. **Early Return**: Check edge cases first, return early

---

## SECTION 1: STRING PROBLEMS
**Status**: 0/12 completed

Strings are the #1 most common coding interview topic. Master these!

---

### PROBLEM 1: Reverse a String

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that reverses a string.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "hello"
Output: "olleh"

Input: "Python"
Output: "nohtyP"

Input: ""
Output: ""
```

**SOLUTION 1: Using Slicing (Most Pythonic)**
```python
def reverse_string(s):
    """
    Reverse a string using Python slicing
    Time: O(n), Space: O(n)
    """
    return s[::-1]
```

**SOLUTION 2: Using Built-in Functions**
```python
def reverse_string(s):
    """
    Reverse using reversed() and join()
    Time: O(n), Space: O(n)
    """
    return ''.join(reversed(s))
```

**SOLUTION 3: Manual Approach (Shows Algorithm Understanding)**
```python
def reverse_string(s):
    """
    Reverse using two-pointer technique
    Time: O(n), Space: O(n)
    """
    # Convert string to list (strings are immutable)
    chars = list(s)
    left, right = 0, len(chars) - 1
    
    # Swap characters from both ends
    while left < right:
        chars[left], chars[right] = chars[right], chars[left]
        left += 1
        right -= 1
    
    return ''.join(chars)
```

**EXPLANATION**:
- **Solution 1**: Python's slicing `[::-1]` creates reversed copy. Concise and Pythonic.
- **Solution 2**: `reversed()` returns iterator, `join()` combines characters
- **Solution 3**: Two-pointer approach - swap characters from both ends moving inward

**CONCEPTS USED**:
- String slicing
- Two-pointer technique
- String immutability (why we convert to list in Solution 3)
- `join()` method for string concatenation

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - must process every character
- **Space**: O(n) - creating new string

**EDGE CASES TO HANDLE**:
- Empty string: `""` → `""`
- Single character: `"a"` → `"a"`
- Spaces: `"a b"` → `"b a"`

**INTERVIEW FOLLOW-UPS**:
- Q: Can you do it in-place?
  - A: In Python, strings are immutable, so no true in-place solution. Must create new string or convert to list.
  
- Q: How would you reverse words in a sentence instead of characters?
  - A: `" ".join(s.split()[::-1])` or reverse string, then reverse each word

**PRACTICE VARIATIONS**:
- [ ] Reverse only vowels in a string
- [ ] Reverse words in a sentence
- [ ] Check if string remains same when reversed (palindrome)

---

### PROBLEM 2: Check if String is a Palindrome

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that checks if a given string is a palindrome (reads the same forwards and backwards).
Ignore spaces, punctuation, and case.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "racecar"
Output: True

Input: "A man a plan a canal Panama"
Output: True (ignoring spaces and case)

Input: "hello"
Output: False

Input: ""
Output: True (empty string is palindrome)
```

**SOLUTION 1: Two-Pointer Approach (Best for Interviews)**
```python
def is_palindrome(s):
    """
    Check palindrome using two pointers
    Time: O(n), Space: O(1)
    """
    # Remove non-alphanumeric and convert to lowercase
    cleaned = ''.join(c.lower() for c in s if c.isalnum())
    
    # Two pointers from both ends
    left, right = 0, len(cleaned) - 1
    
    while left < right:
        if cleaned[left] != cleaned[right]:
            return False
        left += 1
        right -= 1
    
    return True
```

**SOLUTION 2: Using Reverse Comparison**
```python
def is_palindrome(s):
    """
    Compare string with its reverse
    Time: O(n), Space: O(n)
    """
    # Clean the string
    cleaned = ''.join(c.lower() for c in s if c.isalnum())
    
    # Compare with reverse
    return cleaned == cleaned[::-1]
```

**SOLUTION 3: Recursive Approach**
```python
def is_palindrome(s):
    """
    Recursive palindrome check
    Time: O(n), Space: O(n) due to recursion stack
    """
    # Clean the string
    cleaned = ''.join(c.lower() for c in s if c.isalnum())
    
    # Base cases
    if len(cleaned) <= 1:
        return True
    
    # Check first and last, recurse on middle
    if cleaned[0] != cleaned[-1]:
        return False
    
    return is_palindrome(cleaned[1:-1])
```

**EXPLANATION**:
- **Solution 1**: Most efficient - compares characters from both ends without creating reversed string
- **Solution 2**: Simple and readable - creates reversed string for comparison
- **Solution 3**: Shows recursion understanding, but less efficient

**Key Steps**:
1. **Clean the string**: Remove spaces/punctuation, convert to lowercase
2. **Compare**: Check if characters from both ends match
3. **Return result**: True if all match, False otherwise

**CONCEPTS USED**:
- Two-pointer technique
- String methods: `isalnum()`, `lower()`
- List comprehension with filter
- String slicing for reversal

**TIME/SPACE COMPLEXITY**:
- **Solution 1**: Time O(n), Space O(n) for cleaned string
- **Solution 2**: Time O(n), Space O(n) for cleaned + reversed strings
- **Solution 3**: Time O(n), Space O(n) for recursion stack

**EDGE CASES TO HANDLE**:
```python
assert is_palindrome("") == True
assert is_palindrome("a") == True
assert is_palindrome("A man, a plan, a canal: Panama") == True
assert is_palindrome("race a car") == False
assert is_palindrome("!!!") == True  # All non-alphanumeric
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if we don't ignore spaces and punctuation?
  - A: Remove the `if c.isalnum()` filter
  
- Q: How would you find the longest palindromic substring?
  - A: Different problem - requires expanding around center or dynamic programming

**PRACTICE VARIATIONS**:
- [ ] Find longest palindromic substring
- [ ] Check if number is palindrome
- [ ] Make string palindrome by removing minimum characters

---

### PROBLEM 3: Count Character Frequency

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that counts the frequency of each character in a string and returns a dictionary.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "hello"
Output: {'h': 1, 'e': 1, 'l': 2, 'o': 1}

Input: "aabbcc"
Output: {'a': 2, 'b': 2, 'c': 2}

Input: ""
Output: {}
```

**SOLUTION 1: Using Dictionary (Manual)**
```python
def char_frequency(s):
    """
    Count character frequency using dictionary
    Time: O(n), Space: O(k) where k is unique characters
    """
    freq = {}
    
    for char in s:
        if char in freq:
            freq[char] += 1
        else:
            freq[char] = 1
    
    return freq
```

**SOLUTION 2: Using get() Method (Cleaner)**
```python
def char_frequency(s):
    """
    Count using dict.get() method
    Time: O(n), Space: O(k)
    """
    freq = {}
    
    for char in s:
        freq[char] = freq.get(char, 0) + 1
    
    return freq
```

**SOLUTION 3: Using Counter from collections (Most Pythonic)**
```python
from collections import Counter

def char_frequency(s):
    """
    Count using Counter class
    Time: O(n), Space: O(k)
    """
    return dict(Counter(s))
```

**SOLUTION 4: Using defaultdict**
```python
from collections import defaultdict

def char_frequency(s):
    """
    Count using defaultdict
    Time: O(n), Space: O(k)
    """
    freq = defaultdict(int)
    
    for char in s:
        freq[char] += 1
    
    return dict(freq)
```

**EXPLANATION**:
- **Solution 1**: Manual approach - shows understanding of dictionaries
- **Solution 2**: Uses `.get(key, default)` to avoid KeyError
- **Solution 3**: Python's Counter class is built for this exact purpose
- **Solution 4**: defaultdict automatically initializes missing keys

**Which to Use in Interview?**
- Start with Solution 1 or 2 (shows you understand the logic)
- Mention Solution 3 as optimization (shows you know Python's standard library)

**CONCEPTS USED**:
- Dictionary operations
- `dict.get(key, default)` method
- `collections.Counter` class
- `collections.defaultdict`
- Iterating over strings

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - iterate through string once
- **Space**: O(k) - where k is number of unique characters (worst case k=n)

**EDGE CASES TO HANDLE**:
```python
assert char_frequency("") == {}
assert char_frequency("a") == {'a': 1}
assert char_frequency("AAaa") == {'A': 2, 'a': 2}  # Case sensitive
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if you want case-insensitive counting?
  ```python
  def char_frequency_case_insensitive(s):
      freq = {}
      for char in s.lower():
          freq[char] = freq.get(char, 0) + 1
      return freq
  ```

- Q: How would you find the most frequent character?
  ```python
  def most_frequent_char(s):
      if not s:
          return None
      freq = Counter(s)
      return max(freq, key=freq.get)  # Returns character with max count
  ```

- Q: What if you need to return characters sorted by frequency?
  ```python
  from collections import Counter
  
  def sorted_by_frequency(s):
      freq = Counter(s)
      return sorted(freq.items(), key=lambda x: x[1], reverse=True)
  ```

**PRACTICE VARIATIONS**:
- [ ] Find first non-repeating character
- [ ] Find most/least frequent character
- [ ] Count word frequency in a sentence
- [ ] Find characters that appear exactly once

---

### PROBLEM 4: Find First Non-Repeating Character

**DIFFICULTY**: ⭐⭐ Easy-Medium

**PROBLEM STATEMENT**:
Write a function that finds the first character that appears only once in a string. Return the character, or `None` if no such character exists.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "leetcode"
Output: "l"

Input: "loveleetcode"
Output: "v"

Input: "aabb"
Output: None

Input: ""
Output: None
```

**SOLUTION 1: Two-Pass Approach (Optimal)**
```python
def first_non_repeating_char(s):
    """
    Find first non-repeating character
    Time: O(n), Space: O(k) where k is unique characters
    """
    if not s:
        return None
    
    # First pass: count frequencies
    freq = {}
    for char in s:
        freq[char] = freq.get(char, 0) + 1
    
    # Second pass: find first char with count 1
    for char in s:
        if freq[char] == 1:
            return char
    
    return None
```

**SOLUTION 2: Using Counter**
```python
from collections import Counter

def first_non_repeating_char(s):
    """
    Using Counter class
    Time: O(n), Space: O(k)
    """
    if not s:
        return None
    
    freq = Counter(s)
    
    for char in s:
        if freq[char] == 1:
            return char
    
    return None
```

**EXPLANATION**:
1. **First pass**: Count frequency of each character
2. **Second pass**: Iterate through original string (to maintain order) and return first character with frequency 1
3. **Why iterate through original string again?**: To preserve the order of appearance

**Key Insight**: 
- Can't just iterate through dictionary because dictionaries don't guarantee order in older Python versions
- Must iterate through original string to find "first" occurrence

**CONCEPTS USED**:
- Hash map for frequency counting
- Two-pass algorithm
- Early return optimization

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - two passes through string, but still linear
- **Space**: O(k) - where k is unique characters

**EDGE CASES TO HANDLE**:
```python
assert first_non_repeating_char("") == None
assert first_non_repeating_char("a") == "a"
assert first_non_repeating_char("aabbcc") == None
assert first_non_repeating_char("aabbc") == "c"
```

**INTERVIEW FOLLOW-UPS**:
- Q: Can you solve it in one pass?
  - A: Possible but complex - need to track both frequency and first occurrence index
  
- Q: What if you need to return the index instead of the character?
  ```python
  def first_non_repeating_index(s):
      freq = {}
      for char in s:
          freq[char] = freq.get(char, 0) + 1
      
      for i, char in enumerate(s):
          if freq[char] == 1:
              return i
      
      return -1
  ```

- Q: What if string is very large? Can we optimize memory?
  - A: If string is ASCII (128 chars) or Unicode (limited set), can use fixed-size array instead of dictionary

**PRACTICE VARIATIONS**:
- [ ] Find first repeating character
- [ ] Find all non-repeating characters
- [ ] Find the kth non-repeating character

---

### PROBLEM 5: Check if Two Strings are Anagrams

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that checks if two strings are anagrams of each other. Anagrams are words formed by rearranging the letters of another word.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "listen", "silent"
Output: True

Input: "hello", "world"
Output: False

Input: "Astronomer", "Moon starer"
Output: True (ignoring spaces and case)

Input: "", ""
Output: True
```

**SOLUTION 1: Using Sorting**
```python
def are_anagrams(s1, s2):
    """
    Check anagrams by sorting both strings
    Time: O(n log n), Space: O(n)
    """
    # Clean strings: remove spaces and convert to lowercase
    clean_s1 = s1.replace(" ", "").lower()
    clean_s2 = s2.replace(" ", "").lower()
    
    # Check lengths first (early optimization)
    if len(clean_s1) != len(clean_s2):
        return False
    
    # Sort and compare
    return sorted(clean_s1) == sorted(clean_s2)
```

**SOLUTION 2: Using Character Frequency Count (Optimal)**
```python
def are_anagrams(s1, s2):
    """
    Check anagrams using frequency counting
    Time: O(n), Space: O(k) where k is unique characters
    """
    # Clean strings
    clean_s1 = s1.replace(" ", "").lower()
    clean_s2 = s2.replace(" ", "").lower()
    
    # Check lengths first
    if len(clean_s1) != len(clean_s2):
        return False
    
    # Count character frequencies
    freq1 = {}
    freq2 = {}
    
    for char in clean_s1:
        freq1[char] = freq1.get(char, 0) + 1
    
    for char in clean_s2:
        freq2[char] = freq2.get(char, 0) + 1
    
    return freq1 == freq2
```

**SOLUTION 3: Using Counter (Most Pythonic)**
```python
from collections import Counter

def are_anagrams(s1, s2):
    """
    Check anagrams using Counter
    Time: O(n), Space: O(k)
    """
    clean_s1 = s1.replace(" ", "").lower()
    clean_s2 = s2.replace(" ", "").lower()
    
    return Counter(clean_s1) == Counter(clean_s2)
```

**EXPLANATION**:
- **Solution 1**: Simple and intuitive - if anagrams, sorted characters are identical
- **Solution 2**: More efficient - linear time using hash maps
- **Solution 3**: Python's Counter class makes it one-liner

**Key Steps**:
1. Clean strings (remove spaces, convert to lowercase)
2. Check lengths (if different, can't be anagrams)
3. Compare character frequencies or sorted strings

**CONCEPTS USED**:
- String methods: `replace()`, `lower()`
- Sorting with `sorted()`
- Dictionary/hash map for counting
- `collections.Counter`

**TIME/SPACE COMPLEXITY**:
- **Solution 1**: Time O(n log n) due to sorting, Space O(n) for sorted lists
- **Solution 2 & 3**: Time O(n), Space O(k) where k is unique characters

**EDGE CASES TO HANDLE**:
```python
assert are_anagrams("", "") == True
assert are_anagrams("a", "a") == True
assert are_anagrams("ab", "ba") == True
assert are_anagrams("ab", "abc") == False  # Different lengths
```

**INTERVIEW FOLLOW-UPS**:
- Q: Which solution is better - sorting or counting?
  - A: Counting is O(n) vs O(n log n) for sorting, so counting is better for large inputs
  
- Q: What if strings contain Unicode characters?
  - A: Both approaches work with Unicode - Python handles it automatically
  
- Q: How would you find all anagrams of a word in a dictionary?
  ```python
  def find_anagrams(word, dictionary):
      target_freq = Counter(word.lower())
      anagrams = []
      
      for dict_word in dictionary:
          if Counter(dict_word.lower()) == target_freq:
              anagrams.append(dict_word)
      
      return anagrams
  ```

**PRACTICE VARIATIONS**:
- [ ] Group anagrams from a list of strings
- [ ] Find all anagrams in a dictionary
- [ ] Check if one string is an anagram of any permutation of another

---

### PROBLEM 6: Remove Duplicates from String

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that removes duplicate characters from a string, keeping only the first occurrence of each character.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "hello"
Output: "helo"

Input: "aabbcc"
Output: "abc"

Input: "programming"
Output: "progamin"

Input: ""
Output: ""
```

**SOLUTION 1: Using Set to Track Seen Characters**
```python
def remove_duplicates(s):
    """
    Remove duplicates while preserving order
    Time: O(n), Space: O(n)
    """
    seen = set()
    result = []
    
    for char in s:
        if char not in seen:
            seen.add(char)
            result.append(char)
    
    return ''.join(result)
```

**SOLUTION 2: Using Dictionary (Preserves Insertion Order in Python 3.7+)**
```python
def remove_duplicates(s):
    """
    Using dict.fromkeys() which preserves order
    Time: O(n), Space: O(n)
    """
    return ''.join(dict.fromkeys(s))
```

**SOLUTION 3: Using List Comprehension with Condition**
```python
def remove_duplicates(s):
    """
    List comprehension with seen tracking
    Time: O(n), Space: O(n)
    """
    seen = set()
    result = []
    
    [result.append(char) or seen.add(char) 
     for char in s if char not in seen]
    
    return ''.join(result)
```

**EXPLANATION**:
- **Solution 1**: Most clear and readable - explicitly tracks seen characters
- **Solution 2**: Clever Python trick - `dict.fromkeys()` preserves order and removes duplicates
- **Solution 3**: More Pythonic but less readable

**Key Points**:
- Must preserve order of first occurrence
- Can't just use `set(s)` because sets don't preserve order
- Need to track which characters we've already seen

**CONCEPTS USED**:
- Sets for O(1) lookup
- List building and joining
- Dictionary fromkeys method
- Order preservation

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass through string
- **Space**: O(n) - storing seen characters and result

**EDGE CASES TO HANDLE**:
```python
assert remove_duplicates("") == ""
assert remove_duplicates("a") == "a"
assert remove_duplicates("aaa") == "a"
assert remove_duplicates("abcabc") == "abc"
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if you want to keep the last occurrence instead of first?
  ```python
  def remove_duplicates_keep_last(s):
      seen = set()
      result = []
      
      # Process string in reverse
      for char in reversed(s):
          if char not in seen:
              seen.add(char)
              result.append(char)
      
      # Reverse result to get correct order
      return ''.join(reversed(result))
  ```

- Q: What if you want to remove only adjacent duplicates?
  ```python
  def remove_adjacent_duplicates(s):
      result = []
      
      for char in s:
          if not result or result[-1] != char:
              result.append(char)
      
      return ''.join(result)
  ```

- Q: Can you do it in-place?
  - A: In Python, strings are immutable, so true in-place is not possible. Would need to use list.

**PRACTICE VARIATIONS**:
- [ ] Remove adjacent duplicates only
- [ ] Remove all duplicates (keep none if appears more than once)
- [ ] Keep only characters that appear exactly k times

---

### PROBLEM 7: Find Longest Substring Without Repeating Characters

**DIFFICULTY**: ⭐⭐⭐ Medium

**PROBLEM STATEMENT**:
Write a function that finds the length of the longest substring without repeating characters.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "abcabcbb"
Output: 3 (substring "abc")

Input: "bbbbb"
Output: 1 (substring "b")

Input: "pwwkew"
Output: 3 (substring "wke")

Input: ""
Output: 0
```

**SOLUTION 1: Sliding Window with Set (Optimal)**
```python
def longest_unique_substring(s):
    """
    Find longest substring without repeating characters
    Time: O(n), Space: O(min(n, m)) where m is character set size
    """
    if not s:
        return 0
    
    char_set = set()
    left = 0
    max_length = 0
    
    for right in range(len(s)):
        # If character already exists, remove from left until it's unique
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        
        # Add current character
        char_set.add(s[right])
        
        # Update max length
        max_length = max(max_length, right - left + 1)
    
    return max_length
```

**SOLUTION 2: Sliding Window with Dictionary (Track Indices)**
```python
def longest_unique_substring(s):
    """
    Using dictionary to store last seen index
    Time: O(n), Space: O(min(n, m))
    """
    if not s:
        return 0
    
    char_index = {}
    left = 0
    max_length = 0
    
    for right in range(len(s)):
        # If character seen and in current window, move left pointer
        if s[right] in char_index and char_index[s[right]] >= left:
            left = char_index[s[right]] + 1
        
        # Update last seen index
        char_index[s[right]] = right
        
        # Update max length
        max_length = max(max_length, right - left + 1)
    
    return max_length
```

**EXPLANATION**:

**Sliding Window Technique**:
- Use two pointers: `left` and `right` to define a window
- Expand window by moving `right` pointer
- Shrink window by moving `left` pointer when duplicate found
- Track maximum window size

**Solution 1 Process**:
1. Expand window by moving `right`
2. If character at `right` already exists in set:
   - Remove characters from `left` until duplicate is gone
3. Add current character to set
4. Update max length

**Solution 2 Process**:
- Stores last seen index of each character
- When duplicate found, jump `left` pointer to position after last occurrence
- More efficient as it doesn't need while loop

**CONCEPTS USED**:
- Sliding window technique
- Hash set / hash map
- Two pointers
- Window expansion and contraction

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - each character visited at most twice (by left and right pointers)
- **Space**: O(min(n, m)) - where m is character set size (e.g., 26 for lowercase English letters)

**STEP-BY-STEP EXAMPLE**:
```
String: "abcabcbb"

Step 1: right=0, left=0, char='a', set={'a'}, length=1
Step 2: right=1, left=0, char='b', set={'a','b'}, length=2
Step 3: right=2, left=0, char='c', set={'a','b','c'}, length=3
Step 4: right=3, left=0, char='a' (duplicate!)
        Remove 'a' from left, left=1, set={'b','c'}
        Add 'a', set={'b','c','a'}, length=3
Step 5: right=4, left=1, char='b' (duplicate!)
        Remove 'b' from left, left=2, set={'c','a'}
        Add 'b', set={'c','a','b'}, length=3
...and so on

Maximum length found: 3
```

**EDGE CASES TO HANDLE**:
```python
assert longest_unique_substring("") == 0
assert longest_unique_substring("a") == 1
assert longest_unique_substring("aaaaaa") == 1
assert longest_unique_substring("abcdef") == 6  # All unique
```

**INTERVIEW FOLLOW-UPS**:
- Q: Can you return the substring instead of just length?
  ```python
  def longest_unique_substring_string(s):
      if not s:
          return ""
      
      char_set = set()
      left = 0
      max_length = 0
      max_start = 0
      
      for right in range(len(s)):
          while s[right] in char_set:
              char_set.remove(s[left])
              left += 1
          
          char_set.add(s[right])
          
          if right - left + 1 > max_length:
              max_length = right - left + 1
              max_start = left
      
      return s[max_start:max_start + max_length]
  ```

- Q: What if you need to find all substrings without repeating characters?
  - A: Would need to store all windows that don't contain duplicates (more complex)

**PRACTICE VARIATIONS**:
- [ ] Find longest substring with at most k distinct characters
- [ ] Find longest substring with at most 2 distinct characters
- [ ] Return the actual substring, not just length

---

### PROBLEM 8: Count Vowels and Consonants

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that counts the number of vowels and consonants in a string. Ignore spaces and special characters.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "hello world"
Output: {'vowels': 3, 'consonants': 7}

Input: "Python Programming"
Output: {'vowels': 5, 'consonants': 12}

Input: "aeiou"
Output: {'vowels': 5, 'consonants': 0}

Input: "123!@#"
Output: {'vowels': 0, 'consonants': 0}
```

**SOLUTION 1: Using Sets and Counters**
```python
def count_vowels_consonants(s):
    """
    Count vowels and consonants in a string
    Time: O(n), Space: O(1)
    """
    vowels = set('aeiouAEIOU')
    vowel_count = 0
    consonant_count = 0
    
    for char in s:
        if char.isalpha():  # Only count letters
            if char in vowels:
                vowel_count += 1
            else:
                consonant_count += 1
    
    return {'vowels': vowel_count, 'consonants': consonant_count}
```

**SOLUTION 2: Using List Comprehension**
```python
def count_vowels_consonants(s):
    """
    Using list comprehension for counting
    Time: O(n), Space: O(n) due to list creation
    """
    vowels = set('aeiouAEIOU')
    letters = [char for char in s if char.isalpha()]
    
    vowel_count = sum(1 for char in letters if char in vowels)
    consonant_count = len(letters) - vowel_count
    
    return {'vowels': vowel_count, 'consonants': consonant_count}
```

**SOLUTION 3: Case Insensitive with Lower**
```python
def count_vowels_consonants(s):
    """
    Convert to lowercase for simpler vowel checking
    Time: O(n), Space: O(1)
    """
    vowels = 'aeiou'
    vowel_count = 0
    consonant_count = 0
    
    for char in s.lower():
        if char.isalpha():
            if char in vowels:
                vowel_count += 1
            else:
                consonant_count += 1
    
    return {'vowels': vowel_count, 'consonants': consonant_count}
```

**EXPLANATION**:
- **Solution 1**: Most straightforward - checks each character
- **Solution 2**: Functional approach using list comprehension
- **Solution 3**: Simplifies by converting to lowercase first

**Key Points**:
- Only count alphabetic characters (ignore numbers, spaces, special chars)
- Use `isalpha()` to check if character is letter
- Use set for O(1) vowel lookup

**CONCEPTS USED**:
- Sets for efficient lookup
- String methods: `isalpha()`, `lower()`
- List comprehension
- Conditional counting

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass through string
- **Space**: O(1) - only storing counters (vowel set is constant size)

**EDGE CASES TO HANDLE**:
```python
assert count_vowels_consonants("") == {'vowels': 0, 'consonants': 0}
assert count_vowels_consonants("aeiou") == {'vowels': 5, 'consonants': 0}
assert count_vowels_consonants("bcdfg") == {'vowels': 0, 'consonants': 5}
assert count_vowels_consonants("123 !@#") == {'vowels': 0, 'consonants': 0}
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if you need to count each vowel separately?
  ```python
  def count_each_vowel(s):
      vowel_counts = {'a': 0, 'e': 0, 'i': 0, 'o': 0, 'u': 0}
      
      for char in s.lower():
          if char in vowel_counts:
              vowel_counts[char] += 1
      
      return vowel_counts
  ```

- Q: What if 'y' should be considered a vowel?
  - A: Add 'y' to vowels set: `vowels = set('aeiouyAEIOUY')`

**PRACTICE VARIATIONS**:
- [ ] Count each vowel separately
- [ ] Find position of all vowels in string
- [ ] Remove all vowels from string
- [ ] Replace vowels with specific character

---

### PROBLEM 9: String Compression

**DIFFICULTY**: ⭐⭐ Easy-Medium

**PROBLEM STATEMENT**:
Write a function that performs basic string compression using counts of repeated characters. For example, "aabcccccaaa" becomes "a2b1c5a3". If compressed string is not smaller than original, return original string.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "aabcccccaaa"
Output: "a2b1c5a3"

Input: "abcdef"
Output: "abcdef" (compressed is longer, return original)

Input: "aabbcc"
Output: "aabbcc" (same length, return original)

Input: ""
Output: ""
```

**SOLUTION 1: Using String Building**
```python
def compress_string(s):
    """
    Compress string using character counts
    Time: O(n), Space: O(n)
    """
    if not s:
        return s
    
    compressed = []
    count = 1
    
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            count += 1
        else:
            compressed.append(s[i-1] + str(count))
            count = 1
    
    # Don't forget last character group
    compressed.append(s[-1] + str(count))
    
    compressed_str = ''.join(compressed)
    
    # Return shorter string
    return compressed_str if len(compressed_str) < len(s) else s
```

**SOLUTION 2: Using Itertools groupby**
```python
from itertools import groupby

def compress_string(s):
    """
    Using groupby to group consecutive characters
    Time: O(n), Space: O(n)
    """
    if not s:
        return s
    
    compressed = ''.join(char + str(len(list(group))) 
                         for char, group in groupby(s))
    
    return compressed if len(compressed) < len(s) else s
```

**EXPLANATION**:

**Solution 1 Process**:
1. Compare each character with previous one
2. If same, increment count
3. If different, append previous character + count to result
4. Don't forget to handle last group of characters
5. Return shorter of original or compressed

**Solution 2 Process**:
- `groupby()` automatically groups consecutive identical elements
- Much cleaner but requires knowing this function

**Key Points**:
- Must handle last character group separately
- Compare lengths and return shorter string
- Edge case: single character strings

**CONCEPTS USED**:
- String building with list and join
- Character comparison
- Counting consecutive elements
- `itertools.groupby()`

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass through string
- **Space**: O(n) - storing compressed string

**STEP-BY-STEP EXAMPLE**:
```
String: "aabcccccaaa"

i=1: s[1]='a', s[0]='a', same, count=2
i=2: s[2]='b', s[1]='a', different, append "a2", count=1
i=3: s[3]='c', s[2]='b', different, append "b1", count=1
i=4: s[4]='c', s[3]='c', same, count=2
i=5: s[5]='c', s[4]='c', same, count=3
i=6: s[6]='c', s[5]='c', same, count=4
i=7: s[7]='c', s[6]='c', same, count=5
i=8: s[8]='a', s[7]='c', different, append "c5", count=1
i=9: s[9]='a', s[8]='a', same, count=2
i=10: s[10]='a', s[9]='a', same, count=3
End: append "a3"

Result: "a2b1c5a3" (length 11 < 12, return compressed)
```

**EDGE CASES TO HANDLE**:
```python
assert compress_string("") == ""
assert compress_string("a") == "a"
assert compress_string("aaa") == "a3"
assert compress_string("abc") == "abc"  # Compressed would be "a1b1c1" (longer)
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if you want to compress only if count > 1?
  ```python
  def compress_string_skip_singles(s):
      if not s:
          return s
      
      compressed = []
      count = 1
      
      for i in range(1, len(s)):
          if s[i] == s[i-1]:
              count += 1
          else:
              if count > 1:
                  compressed.append(s[i-1] + str(count))
              else:
                  compressed.append(s[i-1])
              count = 1
      
      if count > 1:
          compressed.append(s[-1] + str(count))
      else:
          compressed.append(s[-1])
      
      return ''.join(compressed)
  ```

- Q: Can you decompress a compressed string?
  ```python
  def decompress_string(s):
      result = []
      i = 0
      
      while i < len(s):
          char = s[i]
          i += 1
          
          # Collect digits
          count_str = ''
          while i < len(s) and s[i].isdigit():
              count_str += s[i]
              i += 1
          
          count = int(count_str) if count_str else 1
          result.append(char * count)
      
      return ''.join(result)
  ```

**PRACTICE VARIATIONS**:
- [ ] Decompress a compressed string
- [ ] Compress with run-length encoding (different format)
- [ ] Handle case sensitivity in compression

---

### PROBLEM 10: Find All Permutations of a String

**DIFFICULTY**: ⭐⭐⭐ Medium

**PROBLEM STATEMENT**:
Write a function that generates all permutations of a string. A permutation is a rearrangement of all characters.

**EXAMPLE INPUT/OUTPUT**:
```
Input: "abc"
Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']

Input: "ab"
Output: ['ab', 'ba']

Input: "a"
Output: ['a']

Input: ""
Output: ['']
```

**SOLUTION 1: Using itertools.permutations (Most Pythonic)**
```python
from itertools import permutations

def string_permutations(s):
    """
    Generate all permutations using itertools
    Time: O(n! * n), Space: O(n!)
    """
    # permutations returns tuples, convert to strings
    perms = [''.join(p) for p in permutations(s)]
    return perms
```

**SOLUTION 2: Recursive Backtracking (Shows Algorithm Understanding)**
```python
def string_permutations(s):
    """
    Generate permutations using recursion
    Time: O(n! * n), Space: O(n!) for storing results
    """
    result = []
    
    def backtrack(current, remaining):
        # Base case: no more characters to add
        if not remaining:
            result.append(current)
            return
        
        # Try each character as next character
        for i in range(len(remaining)):
            # Choose character at index i
            char = remaining[i]
            # Recurse with updated current and remaining
            backtrack(current + char, remaining[:i] + remaining[i+1:])
    
    backtrack('', s)
    return result
```

**SOLUTION 3: Recursive with Character Swapping**
```python
def string_permutations(s):
    """
    Generate permutations by swapping characters
    Time: O(n!), Space: O(n!) for results
    """
    result = []
    s_list = list(s)  # Convert to list for swapping
    
    def permute(start):
        # Base case: reached end of string
        if start == len(s_list):
            result.append(''.join(s_list))
            return
        
        # Swap each character with start position
        for i in range(start, len(s_list)):
            # Swap
            s_list[start], s_list[i] = s_list[i], s_list[start]
            # Recurse
            permute(start + 1)
            # Backtrack (undo swap)
            s_list[start], s_list[i] = s_list[i], s_list[start]
    
    permute(0)
    return result
```

**EXPLANATION**:

**Solution 1**: 
- Python's `itertools.permutations()` is built for this
- Returns iterator of tuples, convert to strings

**Solution 2 - Backtracking**:
- Build permutation character by character
- For each position, try every remaining character
- Recurse with that character added and removed from remaining

**Solution 3 - Swapping**:
- Fix first character, permute remaining
- Try each character in first position by swapping
- Backtrack to restore original order

**CONCEPTS USED**:
- Recursion
- Backtracking
- String/list manipulation
- itertools library

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n! * n) - n! permutations, n time to create each string
- **Space**: O(n!) - storing all permutations

**STEP-BY-STEP EXAMPLE** (Solution 2):
```
String: "abc"

backtrack('', 'abc')
├─ Choose 'a': backtrack('a', 'bc')
│  ├─ Choose 'b': backtrack('ab', 'c')
│  │  └─ Choose 'c': backtrack('abc', '') → add "abc"
│  └─ Choose 'c': backtrack('ac', 'b')
│     └─ Choose 'b': backtrack('acb', '') → add "acb"
├─ Choose 'b': backtrack('b', 'ac')
│  ├─ Choose 'a': backtrack('ba', 'c')
│  │  └─ Choose 'c': backtrack('bac', '') → add "bac"
│  └─ Choose 'c': backtrack('bc', 'a')
│     └─ Choose 'a': backtrack('bca', '') → add "bca"
└─ Choose 'c': backtrack('c', 'ab')
   ├─ Choose 'a': backtrack('ca', 'b')
   │  └─ Choose 'b': backtrack('cab', '') → add "cab"
   └─ Choose 'b': backtrack('cb', 'a')
      └─ Choose 'a': backtrack('cba', '') → add "cba"

Result: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']
```

**EDGE CASES TO HANDLE**:
```python
assert len(string_permutations("")) == 1  # ['']
assert len(string_permutations("a")) == 1  # ['a']
assert len(string_permutations("ab")) == 2  # 2! = 2
assert len(string_permutations("abc")) == 6  # 3! = 6
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if string has duplicate characters?
  ```python
  def unique_permutations(s):
      from itertools import permutations
      # Use set to remove duplicates
      return list(set(''.join(p) for p in permutations(s)))
  ```

- Q: Can you generate permutations in lexicographic order?
  - A: Sort string first, then generate permutations

- Q: How would you find the nth permutation without generating all?
  - A: More complex - requires factorial number system

**PRACTICE VARIATIONS**:
- [ ] Find unique permutations (handle duplicates)
- [ ] Find permutations of specific length k
- [ ] Check if one string is permutation of another (easier - just compare sorted)

---

### PROBLEM 11: Valid Parentheses

**DIFFICULTY**: ⭐⭐ Easy-Medium

**PROBLEM STATEMENT**:
Write a function that checks if a string containing only parentheses characters `(){}[]` is valid. A string is valid if:
- Open brackets are closed by the same type
- Open brackets are closed in correct order

**EXAMPLE INPUT/OUTPUT**:
```
Input: "()"
Output: True

Input: "()[]{}"
Output: True

Input: "(]"
Output: False

Input: "([)]"
Output: False

Input: "{[]}"
Output: True
```

**SOLUTION: Using Stack**
```python
def is_valid_parentheses(s):
    """
    Check if parentheses are balanced using stack
    Time: O(n), Space: O(n)
    """
    if not s:
        return True
    
    # Map closing brackets to opening brackets
    bracket_map = {
        ')': '(',
        '}': '{',
        ']': '['
    }
    
    stack = []
    
    for char in s:
        if char in bracket_map:  # Closing bracket
            # Check if stack is empty or top doesn't match
            if not stack or stack[-1] != bracket_map[char]:
                return False
            stack.pop()  # Remove matching opening bracket
        else:  # Opening bracket
            stack.append(char)
    
    # Valid if stack is empty (all brackets matched)
    return len(stack) == 0
```

**EXPLANATION**:

**Stack Approach**:
1. Use stack to track opening brackets
2. When see opening bracket `(`, `{`, `[` → push to stack
3. When see closing bracket `)`, `}`, `]`:
   - Check if stack is empty (no matching opening) → invalid
   - Check if top of stack matches → invalid if doesn't match
   - Pop from stack if matches
4. At end, stack should be empty (all brackets matched)

**Why Stack?**
- Parentheses matching follows Last-In-First-Out (LIFO) order
- Most recent opening bracket should match first closing bracket
- Perfect use case for stack data structure

**CONCEPTS USED**:
- Stack data structure (using list)
- Hash map for bracket mapping
- String iteration

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass through string
- **Space**: O(n) - worst case all opening brackets (stack size)

**STEP-BY-STEP EXAMPLE**:
```
String: "{[]}"

char='{': Opening bracket, push to stack → stack = ['{']
char='[': Opening bracket, push to stack → stack = ['{', '[']
char=']': Closing bracket, matches '[', pop → stack = ['{']
char='}': Closing bracket, matches '{', pop → stack = []

Stack empty → Valid!

---

String: "([)]"

char='(': Opening bracket, push → stack = ['(']
char='[': Opening bracket, push → stack = ['(', '[']
char=')': Closing bracket, top is '[' not '(' → Invalid!
```

**EDGE CASES TO HANDLE**:
```python
assert is_valid_parentheses("") == True
assert is_valid_parentheses("(") == False  # Unmatched opening
assert is_valid_parentheses(")") == False  # Unmatched closing
assert is_valid_parentheses("()[]{}") == True
assert is_valid_parentheses("([{}])") == True
assert is_valid_parentheses("([)]") == False  # Wrong order
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if string contains other characters besides brackets?
  ```python
  def is_valid_parentheses_with_chars(s):
      bracket_map = {')': '(', '}': '{', ']': '['}
      stack = []
      
      for char in s:
          if char in '({[':
              stack.append(char)
          elif char in ')}]':
              if not stack or stack[-1] != bracket_map[char]:
                  return False
              stack.pop()
          # Ignore other characters
      
      return len(stack) == 0
  ```

- Q: Can you return the index of the first invalid bracket?
  ```python
  def first_invalid_bracket_index(s):
      bracket_map = {')': '(', '}': '{', ']': '['}
      stack = []
      
      for i, char in enumerate(s):
          if char in bracket_map:
              if not stack or stack[-1][0] != bracket_map[char]:
                  return i
              stack.pop()
          else:
              stack.append((char, i))
      
      return -1 if not stack else stack[0][1]
  ```

**PRACTICE VARIATIONS**:
- [ ] Return minimum number of brackets to add to make valid
- [ ] Find longest valid parentheses substring
- [ ] Generate all valid parentheses combinations of n pairs

---

### PROBLEM 12: String to Integer (atoi)

**DIFFICULTY**: ⭐⭐ Medium

**PROBLEM STATEMENT**:
Implement the `atoi` function which converts a string to an integer. The function should:
- Ignore leading whitespace
- Handle optional '+' or '-' sign
- Read digits until non-digit character
- Return 0 if no valid conversion
- Handle integer overflow (return INT_MAX or INT_MIN)

**EXAMPLE INPUT/OUTPUT**:
```
Input: "42"
Output: 42

Input: "   -42"
Output: -42

Input: "4193 with words"
Output: 4193

Input: "words and 987"
Output: 0

Input: "-91283472332"
Output: -2147483648 (INT_MIN, overflow)
```

**SOLUTION**:
```python
def string_to_integer(s):
    """
    Convert string to integer (atoi implementation)
    Time: O(n), Space: O(1)
    """
    INT_MAX = 2**31 - 1  # 2147483647
    INT_MIN = -2**31     # -2147483648
    
    # Step 1: Remove leading whitespace
    s = s.lstrip()
    
    if not s:
        return 0
    
    # Step 2: Check sign
    sign = 1
    index = 0
    
    if s[0] in ['+', '-']:
        sign = -1 if s[0] == '-' else 1
        index = 1
    
    # Step 3: Convert digits
    result = 0
    
    while index < len(s) and s[index].isdigit():
        digit = int(s[index])
        
        # Check for overflow before adding digit
        if result > (INT_MAX - digit) // 10:
            return INT_MAX if sign == 1 else INT_MIN
        
        result = result * 10 + digit
        index += 1
    
    return sign * result
```

**EXPLANATION**:

**Algorithm Steps**:
1. **Remove whitespace**: Use `lstrip()` to remove leading spaces
2. **Check sign**: Look for '+' or '-' at start
3. **Build number**: Read digits one by one, building the number
4. **Stop at non-digit**: Stop when encounter non-digit character
5. **Handle overflow**: Check before each digit addition

**Overflow Handling**:
- Before adding next digit, check if result would overflow
- Formula: `if result > (INT_MAX - digit) // 10`
- This checks if `result * 10 + digit` would exceed INT_MAX

**CONCEPTS USED**:
- String parsing
- Character checking: `isdigit()`
- Integer overflow handling
- Edge case handling

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - process each character once
- **Space**: O(1) - only using variables

**STEP-BY-STEP EXAMPLE**:
```
String: "   -42"

Step 1: lstrip() → "-42"
Step 2: sign = -1, index = 1
Step 3: 
  - index=1, char='4', result = 0*10 + 4 = 4
  - index=2, char='2', result = 4*10 + 2 = 42
Step 4: Apply sign → -42
```

**EDGE CASES TO HANDLE**:
```python
assert string_to_integer("") == 0
assert string_to_integer("   ") == 0
assert string_to_integer("0") == 0
assert string_to_integer("-0") == 0
assert string_to_integer("+1") == 1
assert string_to_integer("123abc") == 123
assert string_to_integer("abc123") == 0
assert string_to_integer("999999999999") == 2147483647  # Overflow
```

**INTERVIEW FOLLOW-UPS**:
- Q: Why not just use `int()`?
  - A: Interview is testing string parsing logic and overflow handling
  
- Q: What about floating point numbers?
  - A: Would need to handle decimal point and fractional part (more complex)

- Q: How do you detect overflow before it happens?
  - A: Check `result > (INT_MAX - digit) // 10` before multiplication

**PRACTICE VARIATIONS**:
- [ ] Implement string to float conversion
- [ ] Handle scientific notation (e.g., "1e10")
- [ ] Integer to string conversion

---

## STRING PROBLEMS - Summary

**Completed**: 0/12

### Quick Reference:
1. ✅ Reverse a String - Two pointers
2. ✅ Check Palindrome - Two pointers
3. ✅ Character Frequency - Hash map
4. ✅ First Non-Repeating Character - Hash map + two pass
5. ✅ Anagrams - Sorting or hash map
6. ✅ Remove Duplicates - Set tracking
7. ✅ Longest Unique Substring - Sliding window
8. ✅ Count Vowels/Consonants - Set membership
9. ✅ String Compression - Run-length encoding
10. ✅ String Permutations - Recursion/backtracking
11. ✅ Valid Parentheses - Stack
12. ✅ String to Integer - Parsing + overflow handling

### Key Patterns:
- **Two Pointers**: Reversing, palindrome checking
- **Hash Map**: Frequency counting, anagram detection
- **Sliding Window**: Longest substring problems
- **Stack**: Parentheses matching
- **Backtracking**: Permutations

---

## SECTION 2: LIST/ARRAY PROBLEMS
**Status**: 0/15 completed

Arrays/Lists are the second most common interview topic!

---

### PROBLEM 13: Find Duplicates in a List

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Write a function that finds all duplicate elements in a list.

**EXAMPLE INPUT/OUTPUT**:
```
Input: [1, 2, 3, 2, 4, 3, 5]
Output: [2, 3]

Input: [1, 1, 1, 2, 2, 3]
Output: [1, 2]

Input: [1, 2, 3, 4, 5]
Output: []

Input: []
Output: []
```

**SOLUTION 1: Using Set to Track Seen Elements**
```python
def find_duplicates(lst):
    """
    Find all duplicates in list
    Time: O(n), Space: O(n)
    """
    seen = set()
    duplicates = set()
    
    for num in lst:
        if num in seen:
            duplicates.add(num)
        else:
            seen.add(num)
    
    return list(duplicates)
```

**SOLUTION 2: Using Counter**
```python
from collections import Counter

def find_duplicates(lst):
    """
    Using Counter to find duplicates
    Time: O(n), Space: O(n)
    """
    freq = Counter(lst)
    return [num for num, count in freq.items() if count > 1]
```

**SOLUTION 3: Using Dictionary**
```python
def find_duplicates(lst):
    """
    Using dictionary for counting
    Time: O(n), Space: O(n)
    """
    freq = {}
    for num in lst:
        freq[num] = freq.get(num, 0) + 1
    
    return [num for num, count in freq.items() if count > 1]
```

**EXPLANATION**:
- **Solution 1**: Track seen elements, add to duplicates when seen again
- **Solution 2**: Count frequencies, return items with count > 1
- **Solution 3**: Similar to Solution 2 but manual dictionary

**CONCEPTS USED**:
- Sets for tracking
- Hash maps for counting
- List comprehension

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass
- **Space**: O(n) - storing seen/frequency data

**EDGE CASES TO HANDLE**:
```python
assert find_duplicates([]) == []
assert find_duplicates([1]) == []
assert find_duplicates([1, 1]) == [1]
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if list is sorted? Can you optimize?
  ```python
  def find_duplicates_sorted(lst):
      """For sorted lists - O(n) time, O(1) extra space"""
      if not lst:
          return []
      
      duplicates = []
      for i in range(1, len(lst)):
          if lst[i] == lst[i-1] and (not duplicates or duplicates[-1] != lst[i]):
              duplicates.append(lst[i])
      
      return duplicates
  ```

**PRACTICE VARIATIONS**:
- [ ] Remove all duplicates from list
- [ ] Find first duplicate element
- [ ] Count total number of duplicates

---

### PROBLEM 14: Two Sum

**DIFFICULTY**: ⭐⭐ Easy-Medium

**PROBLEM STATEMENT**:
Given a list of integers and a target sum, return indices of two numbers that add up to the target. Assume exactly one solution exists.

**EXAMPLE INPUT/OUTPUT**:
```
Input: nums = [2, 7, 11, 15], target = 9
Output: [0, 1] (nums[0] + nums[1] = 2 + 7 = 9)

Input: nums = [3, 2, 4], target = 6
Output: [1, 2]

Input: nums = [3, 3], target = 6
Output: [0, 1]
```

**SOLUTION 1: Brute Force (Not Optimal)**
```python
def two_sum(nums, target):
    """
    Brute force - check all pairs
    Time: O(n²), Space: O(1)
    """
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return []
```

**SOLUTION 2: Using Hash Map (Optimal)**
```python
def two_sum(nums, target):
    """
    One-pass hash map solution
    Time: O(n), Space: O(n)
    """
    seen = {}  # {number: index}
    
    for i, num in enumerate(nums):
        complement = target - num
        
        if complement in seen:
            return [seen[complement], i]
        
        seen[num] = i
    
    return []
```

**EXPLANATION**:

**Brute Force**:
- Check every possible pair
- O(n²) time - nested loops

**Hash Map Approach** (PREFERRED):
1. For each number, calculate what number we need: `complement = target - num`
2. Check if complement already seen
3. If yes, return indices
4. If no, store current number and index

**Key Insight**: Instead of looking for two numbers that sum to target, look for one number and check if its complement exists.

**CONCEPTS USED**:
- Hash map for O(1) lookup
- Complement calculation
- enumerate() for index tracking

**TIME/SPACE COMPLEXITY**:
- **Brute Force**: Time O(n²), Space O(1)
- **Hash Map**: Time O(n), Space O(n)

**STEP-BY-STEP EXAMPLE**:
```
nums = [2, 7, 11, 15], target = 9

i=0, num=2, complement=7, seen={} → not found, add 2
  seen = {2: 0}
  
i=1, num=7, complement=2, seen={2: 0} → found!
  return [0, 1]
```

**EDGE CASES TO HANDLE**:
```python
assert two_sum([0, 4, 3, 0], 0) == [0, 3]  # Zero case
assert two_sum([3, 3], 6) == [0, 1]  # Same number twice
assert two_sum([-1, -2, -3, -4], -5) == [0, 3]  # Negative numbers
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if there are multiple solutions?
  ```python
  def two_sum_all_pairs(nums, target):
      seen = {}
      results = []
      
      for i, num in enumerate(nums):
          complement = target - num
          if complement in seen:
              for j in seen[complement]:
                  results.append([j, i])
          
          if num not in seen:
              seen[num] = []
          seen[num].append(i)
      
      return results
  ```

- Q: Can the same element be used twice?
  - A: Depends on problem statement. If yes, just check if `target = 2 * num` and num appears twice.

- Q: What if numbers are sorted? Can you do better?
  ```python
  def two_sum_sorted(nums, target):
      """Two-pointer approach for sorted array"""
      left, right = 0, len(nums) - 1
      
      while left < right:
          current_sum = nums[left] + nums[right]
          if current_sum == target:
              return [left, right]
          elif current_sum < target:
              left += 1
          else:
              right -= 1
      
      return []
  ```

**PRACTICE VARIATIONS**:
- [ ] Three Sum (find three numbers that sum to target)
- [ ] Two Sum in sorted array (use two pointers)
- [ ] Two Sum - all unique pairs

---

### PROBLEM 15: Maximum/Minimum in List

**DIFFICULTY**: ⭐ Easy

**PROBLEM STATEMENT**:
Find the maximum and minimum elements in a list WITHOUT using built-in `max()` and `min()` functions.

**EXAMPLE INPUT/OUTPUT**:
```
Input: [3, 1, 4, 1, 5, 9, 2, 6]
Output: {'max': 9, 'min': 1}

Input: [42]
Output: {'max': 42, 'min': 42}

Input: [-5, -1, -10, -3]
Output: {'max': -1, 'min': -10}
```

**SOLUTION 1: Single Pass**
```python
def find_max_min(lst):
    """
    Find max and min in single pass
    Time: O(n), Space: O(1)
    """
    if not lst:
        return None
    
    max_val = lst[0]
    min_val = lst[0]
    
    for num in lst[1:]:
        if num > max_val:
            max_val = num
        if num < min_val:
            min_val = num
    
    return {'max': max_val, 'min': min_val}
```

**SOLUTION 2: Using reduce (Functional Approach)**
```python
from functools import reduce

def find_max_min(lst):
    """
    Using reduce function
    Time: O(n), Space: O(1)
    """
    if not lst:
        return None
    
    def update_max_min(acc, num):
        return {
            'max': num if num > acc['max'] else acc['max'],
            'min': num if num < acc['min'] else acc['min']
        }
    
    initial = {'max': lst[0], 'min': lst[0]}
    return reduce(update_max_min, lst[1:], initial)
```

**EXPLANATION**:
- Initialize max and min with first element
- Iterate through remaining elements
- Update max if current element is larger
- Update min if current element is smaller

**CONCEPTS USED**:
- List iteration
- Comparison operations
- Variable tracking

**TIME/SPACE COMPLEXITY**:
- **Time**: O(n) - single pass
- **Space**: O(1) - only storing two variables

**EDGE CASES TO HANDLE**:
```python
assert find_max_min([5]) == {'max': 5, 'min': 5}
assert find_max_min([1, 1, 1]) == {'max': 1, 'min': 1}
assert find_max_min([-5, -1]) == {'max': -1, 'min': -5}
```

**INTERVIEW FOLLOW-UPS**:
- Q: Can you find the second maximum?
  ```python
  def find_second_max(lst):
      if len(lst) < 2:
          return None
      
      max1 = max2 = float('-inf')
      
      for num in lst:
          if num > max1:
              max2 = max1
              max1 = num
          elif num > max2 and num < max1:
              max2 = num
      
      return max2 if max2 != float('-inf') else None
  ```

- Q: What if list is very large? Any optimizations?
  - A: Could use multiprocessing to divide list into chunks and find max/min in parallel

**PRACTICE VARIATIONS**:
- [ ] Find second largest element
- [ ] Find k-th largest element
- [ ] Find difference between max and min

---

### PROBLEM 16: Merge Two Sorted Lists

**DIFFICULTY**: ⭐⭐ Easy-Medium

**PROBLEM STATEMENT**:
Merge two sorted lists into one sorted list.

**EXAMPLE INPUT/OUTPUT**:
```
Input: list1 = [1, 3, 5], list2 = [2, 4, 6]
Output: [1, 2, 3, 4, 5, 6]

Input: list1 = [1, 2, 3], list2 = []
Output: [1, 2, 3]

Input: list1 = [], list2 = [4, 5, 6]
Output: [4, 5, 6]
```

**SOLUTION 1: Two-Pointer Approach (Optimal)**
```python
def merge_sorted_lists(list1, list2):
    """
    Merge two sorted lists using two pointers
    Time: O(n + m), Space: O(n + m)
    """
    result = []
    i, j = 0, 0
    
    # Compare elements from both lists
    while i < len(list1) and j < len(list2):
        if list1[i] <= list2[j]:
            result.append(list1[i])
            i += 1
        else:
            result.append(list2[j])
            j += 1
    
    # Add remaining elements
    result.extend(list1[i:])
    result.extend(list2[j:])
    
    return result
```

**SOLUTION 2: Using sorted() (Not Interview Preferred)**
```python
def merge_sorted_lists(list1, list2):
    """
    Simple but doesn't show algorithm understanding
    Time: O((n+m) log(n+m)), Space: O(n + m)
    """
    return sorted(list1 + list2)
```

**EXPLANATION**:

**Two-Pointer Approach** (SHOW THIS IN INTERVIEW):
1. Use two pointers, one for each list
2. Compare elements at both pointers
3. Add smaller element to result
4. Move pointer of list that contributed element
5. After one list exhausted, add remaining elements from other list

**CONCEPTS USED**:
- Two-pointer technique
- List merging
- Comparison logic

**TIME/SPACE COMPLEXITY**:
- **Solution 1**: Time O(n + m), Space O(n + m)
- **Solution 2**: Time O((n+m) log(n+m)) due to sorting

**STEP-BY-STEP EXAMPLE**:
```
list1 = [1, 3, 5]
list2 = [2, 4, 6]

i=0, j=0: list1[0]=1, list2[0]=2 → add 1, i=1
i=1, j=0: list1[1]=3, list2[0]=2 → add 2, j=1
i=1, j=1: list1[1]=3, list2[1]=4 → add 3, i=2
i=2, j=1: list1[2]=5, list2[1]=4 → add 4, j=2
i=2, j=2: list1[2]=5, list2[2]=6 → add 5, i=3
i=3: list1 exhausted, add remaining from list2 → add 6

Result: [1, 2, 3, 4, 5, 6]
```

**EDGE CASES TO HANDLE**:
```python
assert merge_sorted_lists([], []) == []
assert merge_sorted_lists([1], []) == [1]
assert merge_sorted_lists([], [1]) == [1]
assert merge_sorted_lists([1, 1], [1, 1]) == [1, 1, 1, 1]
```

**INTERVIEW FOLLOW-UPS**:
- Q: What if lists are different lengths?
  - A: Code already handles it - adds remaining elements after main loop

- Q: Can you merge k sorted lists?
  ```python
  import heapq
  
  def merge_k_sorted_lists(lists):
      """Merge k sorted lists using heap"""
      heap = []
      
      # Add first element from each list to heap
      for i, lst in enumerate(lists):
          if lst:
              heapq.heappush(heap, (lst[0], i, 0))
      
      result = []
      
      while heap:
          val, list_idx, elem_idx = heapq.heappop(heap)
          result.append(val)
          
          # Add next element from same list
          if elem_idx + 1 < len(lists[list_idx]):
              next_val = lists[list_idx][elem_idx + 1]
              heapq.heappush(heap, (next_val, list_idx, elem_idx + 1))
      
      return result
  ```

**PRACTICE VARIATIONS**:
- [ ] Merge k sorted lists
- [ ] Merge sorted lists in-place
- [ ] Find median of two sorted lists

---