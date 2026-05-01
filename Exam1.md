# Exam 1 Study Guide

## Author: Kelvin & Moe

### Chapter 1:

#### Bits and Bytes

Computer store data in binary form **_(0s and 1s)_**. A bit is a single binary digit. **_8 bits = 1 byte_**.

#### Components of a Computer

1. **Central Processing Unit (CPU)**: The brain.
2. **Memory (RAM)**: Short-term memory.
3. **Storage**: Long-term memory (e.g., hard drive, SSD).
4. **Input Devices**: Keyboard, mouse.
5. **Output Devices**: Monitor, printer.

#### Operating Systems

An operating system (OS) manages hardware and software resources. Examples include Windows, macOS, and Linux.

### Chapter 2: Elementary Programming

#### Variables and Assignments

- A **variable** is a name that refers to a value stored in memory
- Assignment uses `=` (not equality!)
- Variable names: must start with a letter or `_`, case-sensitive, no spaces or keywords

```python
x = 5            # assign 5 to x
y = x + 2        # y is 7
x = x + 1        # update x to 6 (old value + 1)

# Multiple assignment
a, b, c = 1, 2, 3

# Swap values
x, y = y, x

# Augmented assignment operators
x += 5   # x = x + 5
x -= 3   # x = x - 3
x *= 2   # x = x * 2
x /= 4   # x = x / 4
x //= 2  # x = x // 2
x %= 3   # x = x % 3
x **= 2  # x = x ** 2
```

- **Naming conventions**: use `snake_case` for variables (e.g., `my_variable`) or `camelCase` for variables (e.g., `myVariable`)
- **Constants**: use `ALL_CAPS` by convention (e.g., `PI = 3.14159`)

---

#### Getting Input

- `input()` **always returns a string** — must convert for math

```python
name = input("Enter your name: ")          # returns str
age = int(input("Enter your age: "))        # convert to int
gpa = float(input("Enter your GPA: "))      # convert to float
```

- `input("prompt")` — the prompt string is optional but recommended

---

#### Data Types

| Type    | Description     | Example           |
| ------- | --------------- | ----------------- |
| `int`   | Whole numbers   | `5`, `-3`, `0`    |
| `float` | Decimal numbers | `3.14`, `-0.5`    |
| `str`   | Text / strings  | `"hello"`, `'hi'` |
| `bool`  | True or False   | `True`, `False`   |

#### Type Conversion (Casting)

```python
int(3.9)       # 3  (truncates, does NOT round)
float(3)       # 3.0
str(42)        # "42"
int("15")      # 15
float("3.14")  # 3.14
type(x)        # check the type of x
```

#### Key Rules

- `int / int` → **always `float`** in Python 3 (e.g., `5 / 2` → `2.5`)
- `int // int` → **always `int`** in Python 3 (e.g., `5 // 2` → `2`)
- `int + float` → result is **`float`** (automatic widening)
- Overflow: Python `int` has **no limit** (arbitrary precision)

---

#### Operators (in order of precedence)

| Precedence  | Operator            | Description                          | Example              |
| ----------- | ------------------- | ------------------------------------ | -------------------- |
| 0 (highest) | `()`                | Parentheses                          | `(3 + 2) * 4` → `20` |
| 1 (high)    | `**`                | Exponentiation                       | `2 ** 3` → `8`       |
| 2           | `*`, `/`, `//`, `%` | Multiply, Divide, Floor Div, Modulus | see below            |
| 3 (low)     | `+`, `-`            | Addition, Subtraction                | `3 + 2` → `5`        |

- **Same precedence** → evaluated **left to right** (except `**` which is **right to left**)
- Use **parentheses `()`** to override precedence

#### Key Operators

```python
10 / 3     # 3.3333...  (true division, always float)
10 // 3    # 3          (floor division, rounds DOWN)
10 % 3     # 1          (modulus / remainder)
2 ** 4     # 16         (exponent)

# Floor division with negatives rounds DOWN (toward -∞)
-7 // 2    # -4  (not -3!)

# Common use of %
x % 2 == 0   # check if even
x % 2 != 0   # check if odd
x % 10       # get last digit
```

---

#### String Formatting

##### 1. f-strings

```python
name = "Alice"
age = 20
print(f"Name: {name}, Age: {age}")
# Output: Name: Alice, Age: 20

# Expressions inside {}
print(f"Next year: {age + 1}")

# Formatting numbers
pi = 3.14159
print(f"{pi:.2f}")        # 3.14   (2 decimal places)
print(f"{1234:,}")         # 1,234  (comma separator)
print(f"{0.85:.0%}")       # 85%    (percentage)
print(f"{'hi':>10}")       # "        hi"  (right-align, width 10)
print(f"{'hi':<10}")       # "hi        "  (left-align, width 10)
```

##### 2. `print()` details

```python
print("a", "b", "c")            # a b c  (space separated by default)
print("a", "b", sep=", ")       # a, b   (custom separator)
print("hello", end="")          # no newline at end
print("hello", end="!\n")       # custom ending
```

---

#### Quick Reference — Common Pitfalls

| Mistake                          | Why it's wrong                   | Fix                            |
| -------------------------------- | -------------------------------- | ------------------------------ |
| `input()` used in math directly  | `input()` returns `str`          | Wrap with `int()` or `float()` |
| `5 / 2` expecting `2`            | `/` gives float in Python 3      | Use `//` for integer division  |
| `int(3.9)` expecting `4`         | `int()` truncates, doesn't round | Use `round(3.9)` for rounding  |
| `"age: " + 21`                   | Can't concatenate `str` + `int`  | Use `str(21)` or f-string      |
| `x = x + 1` before assigning `x` | `x` not defined yet              | Initialize `x` first           |

### Chapter 3:

#### If-else

We use if-else to make decisions.
Syntax:

```python
if condition:
    # code to execute if condition is true
elif another_condition:
    # code to execute if another_condition is true
else:
    # code to execute if all conditions are false
```

We can nest if-else statements to handle multiple conditions.
Example:

```python
if cake_color == "red":
    if cake_flavor == "strawberry":
        print("This is a red strawberry cake.")
    else:
        print("This is a red cake, but not strawberry.")
elif cake_color == "yellow":
    if cake_flavor == "lemon":
        print("This is a yellow lemon cake.")
    else:
        print("This is a yellow cake, but not lemon.")
```

Notice how the padding is important to indicate which code belongs to which condition. If the padding is inconsistent, the code will give us a `IndentationError`.
Example:

```python
if True:
 if True:
      if True:
print(123) # IndentationError: expected an indented block after 'if' statement on line 3
```

#### Logical Operators

1. **_and_**: Both conditions must be true.
2. **_or_**: At least one condition must be true.
3. **_not_**: Negates the condition.

#### Conditional Expressions

A compact way to write an if-else statement.
Syntax:

```python
result = value_if_true if condition else value_if_false
```

Example:

```python
cookie_type = "chocolate chip"
price = 1.50 if cookie_type == "chocolate chip" else 1.00
print(price) # Output: 1.50
```

#### Operators Precedence

From highest to lowest:

1. Parentheses `()`
2. Exponentiation `**`
3. Multiplication `*`, Division `/`, Integer Division `//`, Remainder `%`
4. Addition `+`, Subtraction `-`
5. Comparison Operators `==`, `!=`, `<`, `>`, `<=`, `>=`
6. Logical Operators `not`, `and`, `or`
7. Assignment Operators `=`, `+=`, `-=`, etc.
   The computer will prioritize operators based on this order. If we want to change the order, we can use parentheses.
   Example:

```python
result = 2 + 3 * 4 # Output: 14
result = (2 + 3) * 4 # Output: 20
```

### Chapter 4:

#### Built-in Math Functions

```python
abs(-5)         # 5       → absolute value
max(3, 7, 1)    # 7       → largest value
min(3, 7, 1)    # 1       → smallest value
pow(2, 3)       # 8       → same as 2 ** 3
round(3.456)    # 3       → round to nearest int
round(3.456, 2) # 3.46    → round to 2 decimal places
```

`import math` gives access to more functions:

```python
import math
math.pi           # 3.141592653589793
math.e            # 2.718281828459045
math.sqrt(16)     # 4.0       → square root
math.ceil(2.1)    # 3         → round UP
math.floor(2.9)   # 2         → round DOWN
math.fabs(-5)     # 5.0       → absolute value (float)
math.log(8, 2)    # 3.0       → log base 2
math.log10(1000)  # 3.0       → log base 10
math.gcd(a,b)     #returns greatest common divisors of integers a and b
```

- `math.ceil()` rounds **up**, `math.floor()` rounds **down**, `round()` rounds to **nearest**

#### ASCII and Unicode

Every character has a numeric code. ASCII is a subset of Unicode.

- `'0'`–`'9'` → 48–57
- `'A'`–`'Z'` → 65–90
- `'a'`–`'z'` → 97–122
- Uppercase letters have **smaller** values than lowercase

#### ord() and chr()

- `ord(char)` → returns the integer code of a character
- `chr(int)` → returns the character for an integer code

```python
ord('A')    # 65
ord('a')    # 97
ord('0')    # 48
chr(65)     # 'A'
chr(97)     # 'a'
chr(48)     # '0'

# Useful patterns
ord('B') - ord('A')   # 1    → distance between letters
chr(ord('A') + 3)     # 'D'  → shift letters
```

#### Escape Sequences

| Escape | Meaning       |
| ------ | ------------- |
| `\n`   | Newline       |
| `\t`   | Tab           |
| `\\`   | Backslash `\` |
| `\'`   | Single quote  |
| `\"`   | Double quote  |

```python
print("Line1\nLine2")      # prints on two lines
print("Col1\tCol2")        # tab between columns
print("She said \"hi\"")   # escaped quotes
```

#### str()

Converts other types to a string.

```python
str(42)     # "42"
str(3.14)   # "3.14"
str(True)   # "True"
```

#### min() and max() and len()

```python
len("Hello")             # 5      → number of characters
min("hello")             # 'e'    → smallest char by ASCII
max("hello")             # 'o'    → largest char by ASCII
min("apple", "banana")   # "apple"   (lexicographic)
max("apple", "banana")   # "banana"
```

#### Indexing

Strings are **0-indexed**. Negative indices count from the end.

```python
s = "Hello"
#     H  e  l  l  o
#     0  1  2  3  4     (positive)
#    -5 -4 -3 -2 -1     (negative)

s[0]    # 'H'
s[-1]   # 'o'   (last character)
s[1]    # 'e'
```

#### Slicing

Syntax: `s[start:end:step]` — `start` is **inclusive**, `end` is **exclusive**.

```python
s = "Hello World"

s[0:5]    # "Hello"         (index 0 to 4)
s[6:]     # "World"         (index 6 to end)
s[:5]     # "Hello"         (start to index 4)
s[::2]    # "HloWrd"        (every 2nd character)
s[::-1]   # "dlroW olleH"   (reverse the string)
s[1:4]    # "ell"
```

#### String Concatenation and Repetition

```python
"Hello" + " " + "World"   # "Hello World"
"Ha" * 3                  # "HaHaHa"

# Cannot concatenate str + int directly
"Age: " + str(25)         # "Age: 25"
```

#### String Methods

Strings are **immutable** — methods return a **new** string.

```python
s = "Hello World"

# Case
s.lower()           # "hello world"
s.upper()           # "HELLO WORLD"
s.capitalize()      # "Hello world"
s.title()           # "Hello World"
s.swapcase()        # "hELLO wORLD"

# Search
s.find("World")     # 6     (index, -1 if not found)
s.count("l")        # 3     (occurrences)
s.startswith("He")  # True
s.endswith("ld")    # True

# Checking (return bool)
"abc".isalpha()     # True  (all letters)
"123".isdigit()     # True  (all digits)
"abc1".isalnum()    # True  (letters or digits)
"   ".isspace()     # True  (all whitespace)
"hello".islower()   # True
"HELLO".isupper()   # True

# Modify
s.strip()           # removes leading/trailing whitespace
s.lstrip()          # removes leading whitespace only
s.rstrip()          # removes trailing whitespace only
s.replace("World", "Python")  # "Hello Python"
s.split()           # ["Hello", "World"]
s.split(",")        # split by comma

# in operator (substring check)
"cat" in "education"    # True
"Cat" in "education"    # False  (case-sensitive!)
"xyz" not in "hello"    # True

# Comparison (character by character using ASCII)
"apple" < "banana"      # True  ('a' < 'b')
"A" < "a"               # True  (65 < 97)
"hello" == "hello"      # True
"Hello" == "hello"      # False (case-sensitive)
```

### Chapter 5: Loops

#### While Loops

A `while` loop repeats a block of code **as long as** its condition is `True`.

```python
# Basic syntax
while condition:
    # code to repeat

# Example: print 1 to 5
i = 1
while i <= 5:
    print(i)
    i += 1        # don't forget to update, or infinite loop!
```

- The condition is checked **before** each iteration
- If the condition is `False` from the start, the body **never executes**

---

#### Counter-Controlled Loops

Use a variable to count iterations.

```python
# Sum of 1 to 100
total = 0
i = 1
while i <= 100:
    total += i
    i += 1
print(total)    # 5050
```

---

#### Infinite Loops

A loop that **never ends** because the condition is always `True`.

```python
# BAD — infinite loop (no update to i)
i = 1
while i <= 5:
    print(i)
    # forgot i += 1  → prints 1 forever

# Intentional infinite loop (use with break)
while True:
    user = input("Enter 'q' to quit: ")
    if user == 'q':
        break       # exits the loop
```

---

#### `break` and `continue`

- **`break`** — immediately **exits** the loop entirely
- **`continue`** — **skips** the rest of the current iteration and jumps back to the condition

```python
# break example: stop at 5
i = 0
while i < 10:
    i += 1
    if i == 5:
        break
    print(i)
# Output: 1 2 3 4

# continue example: skip 5
i = 0
while i < 10:
    i += 1
    if i == 5:
        continue
    print(i)
# Output: 1 2 3 4 6 7 8 9 10
```

---

#### Sentinel Value

A **sentinel** is a special value that signals the end of input (e.g., `-1`, `0`, `"done"`).

```python
# Read numbers until user enters 0
total = 0
num = int(input("Enter a number (0 to stop): "))
while num != 0:
    total += num
    num = int(input("Enter a number (0 to stop): "))
print("Total:", total)
```

---

#### Input Validation with While

```python
# Keep asking until valid input
score = int(input("Enter score (0-100): "))
while score < 0 or score > 100:
    print("Invalid! Try again.")
    score = int(input("Enter score (0-100): "))
```

---

### Miscellaneous: Using Random

The `random` module provides functions for generating random numbers.

```python
import random
```

#### `random.randint(a, b)`

Returns a random **integer** N such that `a <= N <= b` (**inclusive** on both ends).

```python
random.randint(1, 6)     # random int from 1 to 6 (like a dice roll)
random.randint(0, 100)   # random int from 0 to 100
```

#### `random.randrange(a, b)`

Returns a random **integer** N such that `a <= N < b` (**excludes** `b`, like `range()`).

```python
random.randrange(1, 7)     # random int from 1 to 6 (same as randint(1,6))
random.randrange(0, 10, 2) # random even number: 0, 2, 4, 6, or 8
```

#### `random.random()`

Returns a random **float** in the range `[0.0, 1.0)` (includes 0.0, excludes 1.0).

```python
random.random()            # e.g., 0.37444887175646646
random.random() * 100      # random float from 0.0 to 99.999...
```

#### `random.choice(seq)`

Returns a **random element** from a non-empty sequence (list, string, tuple).

```python
random.choice([1, 2, 3, 4, 5])        # random element from list
random.choice("abcdef")               # random character from string
random.choice(["heads", "tails"])      # coin flip
```

#### `random.shuffle(seq)`

**Shuffles** a list **in place** (modifies the original list, returns `None`).

```python
cards = [1, 2, 3, 4, 5]
random.shuffle(cards)
print(cards)          # e.g., [3, 1, 5, 2, 4]  (order randomized)

# IMPORTANT: works on lists only, not strings (strings are immutable)
```

---

#### Random Quick Reference

| Function          | Returns           | Range               |
| ----------------- | ----------------- | ------------------- |
| `randint(a, b)`   | `int`             | `[a, b]` inclusive  |
| `randrange(a, b)` | `int`             | `[a, b)` excludes b |
| `random()`        | `float`           | `[0.0, 1.0)`        |
| `choice(seq)`     | element from seq  | any element         |
| `shuffle(list)`   | `None` (in-place) | N/A                 |

# Exam 2

### Chapter 5 (Part 2): For Loops

#### For Loops

A `for` loop is used for iterating over a sequence (list, tuple, string, or range).

```python
# Iterating over a string
for char in "Python":
    print(char)

# Iterating over a range
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4 (excludes 5)

# range(start, stop, step)
for i in range(2, 10, 2):
    print(i)  # 2, 4, 6, 8
```

#### Nested For Loops

A loop inside another loop. The inner loop completes all its iterations for every single iteration of the outer loop.

```python
for i in range(3):        # Outer loop
    for j in range(2):    # Inner loop
        print(f"i={i}, j={j}")
```

#### Using break and continue

- **`break`**: Stops the loop completely.
- **`continue`**: Skips the rest of the current iteration and moves to the next one.

```python
for i in range(10):
    if i == 5:
        break     # Stops at 5
    if i % 2 == 0:
        continue  # Skips even numbers
    print(i)      # Output: 1, 3
```

#### What is the difference between a for loop and a while loop?

| Feature         | For Loop                                 | While Loop                                   |
| :-------------- | :--------------------------------------- | :------------------------------------------- |
| **Usage**       | Known number of iterations (determinate) | Unknown number of iterations (indeterminate) |
| **Control**     | Iterates over a sequence or range        | Iterates as long as a condition is `True`     |
| **Efficiency**  | Generally cleaner for lists/ranges       | Better for sentinel values or input validation |

### Chapter 6: Functions

#### Defining Functions

Functions are reusable blocks of code that perform a specific task. They start with the `def` keyword.

```python
def greet_user():
    """Docstring: simple greeting."""
    print("Hello!")
```

#### Calling Functions

To execute a function, use its name followed by parentheses.

```python
greet_user()  # Output: Hello!
```

#### Function Parameters and Arguments

- **Parameters**: Variables listed in the function definition.
- **Arguments**: Values sent to the function when it is called.

```python
def add(a, b):       # a and b are parameters
    return a + b

result = add(5, 3)   # 5 and 3 are arguments
```

- **Default Parameters**:
```python
def power(base, exp=2):
    return base ** exp

print(power(4))     # 16 (uses default exp=2)
print(power(4, 3))  # 64 (overrides default)
```

#### Return Values

The `return` statement sends a result back to the caller and exits the function. If no `return` is used, the function returns `None`.

```python
def get_square(n):
    return n * n

x = get_square(4)  # x becomes 16
```

#### Scope

- **Local Scope**: Variables defined inside a function. They only exist while the instance of a function is running.

### Chapter 7 (Part 1): Lists

#### List Basics

Lists are ordered, mutable collections of items. They can hold different data types.

```python
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4]
mixed = [1, "hello", 3.14, True]
```

#### List Methods

| Method           | Description                          | Example               |
| :--------------- | :----------------------------------- | :-------------------- |
| `append(x)`      | Adds `x` to the end                  | `l.append(4)`         |
| `insert(i, x)`   | Inserts `x` at index `i`             | `l.insert(0, "hi")`   |
| `remove(x)`      | Removes first occurrence of `x`      | `l.remove("apple")`   |
| `pop(i)`         | Removes and returns item at `i`      | `item = l.pop(1)`     |
| `sort()`         | Sorts the list in place              | `l.sort()`            |
| `reverse()`      | Reverses the list in place           | `l.reverse()`         |
| `index(x)`       | Returns index of first `x`           | `i = l.index(3)`      |
| `count(x)`       | Returns number of `x` in list        | `c = l.count(1)`      |

#### List Operations

```python
list1 = [1, 2]
list2 = [3, 4]

# Concatenation (+)
combined = list1 + list2  # [1, 2, 3, 4]

# Repetition (*)
triple = list1 * 3        # [1, 2, 1, 2, 1, 2]

# Membership (in)
print(1 in list1)         # True
```

#### List Comprehensions

A concise way to create lists.
Syntax: `[expression for item in iterable if condition]`

```python
squares = [x**2 for x in range(5)]           # [0, 1, 4, 9, 16]
evens = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]
```

#### Indexing

Same as strings (0-indexed).

```python
l = [10, 20, 30]
l[0]    # 10
l[-1]   # 30 (last)
l[1] = 99  # Mutable: l is now [10, 99, 30]
```

#### Slicing

Syntax: `list[start:stop:step]`

```python
l = [0, 1, 2, 3, 4, 5]
l[1:4]   # [1, 2, 3]
l[:3]    # [0, 1, 2]
l[::2]   # [0, 2, 4]
l[::-1]  # [5, 4, 3, 2, 1, 0] (reverse)
```

#### Iterating through lists

```python
# Direct iteration
for item in fruits:
    print(item)

# Iteration by index
for i in range(len(fruits)):
    print(f"Index {i}: {fruits[i]}")
```

#### List Comparison

Lists are compared element by element (lexicographically).

```python
[1, 2, 3] < [1, 2, 4]    # True
[1, 2] == [1, 2]         # True
```

#### Taking Input

```python
# Single line of integers
nums = [int(x) for x in input("Enter numbers: ").split()]

# Multiple lines
size = int(input("How many items? "))
items = []
for i in range(size):
    items.append(input("Enter item: "))
```

#### Copying Lists

**Warning**: `list2 = list1` does NOT copy; it makes 2 variables storing the same list.

```python
list1 = [1, 2, 3]

# Proper copying
list2 = [x for x in list1]
list3 = list1[:]
list4 = list(list1)

# Modification of list1 won't affect copies
```

# Final Exam (Everything past Exam 2)

### Chapter 8: Multidimensional Lists

#### Creating 2D lists

A 2D list is simply a list of lists.
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Using a loop or list comprehension:
```python
# 3 rows, 4 columns filled with 0
rows = 3
cols = 4
matrix = [[0 for j in range(cols)] for i in range(rows)]
```
*Note: `[[0] * cols] * rows` creates references to the SAME inner list, which can cause bugs when modifying elements.*

#### Using 2D lists

Accessing and modifying elements uses two indices: `list_name[row][col]`.

```python
matrix[0][1] = 99  # Modifies row 0, column 1
```

Iterating through a 2D list:
```python
for row in matrix:
    for item in row:
        print(item, end=" ")
    print()
```

Or by index:
```python
for r in range(len(matrix)):
    for c in range(len(matrix[r])):
        print(matrix[r][c], end=" ")
    print()
```

### Chapter 9: Objects and Classes

#### What is an object?

An object is a specific instance of a class that contains data (attributes) and behaviors (methods). In Python, almost everything is an object.

#### What is a class?

A class is a blueprint or template for creating objects. It defines what attributes and methods the objects will have.

#### Defining Classes

Use the `class` keyword. By convention, class names use `PascalCase`.

```python
class Dog:
    # Class body goes here
    pass
```

#### Instance Variables

Variables that belong to a specific object. They are initialized in the constructor method `__init__`.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name  # Instance variable
        self.age = age    # Instance variable

my_dog = Dog("Buddy", 3)
print(my_dog.name)  # Output: Buddy
```
- `self` refers to the specific object being created/used. It must be the first parameter in instance methods.

#### Methods

Functions defined inside a class that define the behaviors of objects.

```python
class Dog:
    def __init__(self, name):
        self.name = name
    
    def bark(self):
        print(f"{self.name} says Woof!")

my_dog = Dog("Buddy")
my_dog.bark()  # Output: Buddy says Woof!
```

#### Magic Methods

Special methods starting and ending with double underscores (dunder methods). They allow customization of built-in behavior.
- `__init__(self)`: Constructor, called when creating a new object.
- `__str__(self)`: Returns a readable string representation (called by `print()` or `str()`).
- `__add__(self, other)`: Defines behavior for the `+` operator.
- `__sub__(self, other)`: Defines behavior for the `-` operator.
- `__eq__(self, other)`: Defines behavior for the equality operator `==`.
- `__lt__(self, other)`: Defines behavior for the less-than operator `<`.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __str__(self):
        return f"({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

    def __sub__(self, other):
        return Point(self.x - other.x, self.y - other.y)

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __lt__(self, other):
        # Compare distances from origin
        return (self.x**2 + self.y**2) < (other.x**2 + other.y**2)

p1 = Point(1, 2)
p2 = Point(3, 4)

print(p1)           # Output: (1, 2)
print(p1 + p2)      # Output: (4, 6)
print(p2 - p1)      # Output: (2, 2)
print(p1 == p2)     # Output: False
print(p1 < p2)      # Output: True
```

#### Getters and Setters

Methods used to access (get) or update (set) private attributes safely. Private attributes often start with an underscore `_` (convention) or double underscore `__` (name mangling).

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    # Getter
    def get_balance(self):
        return self.__balance

    # Setter
    def set_balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            print("Invalid amount")

account = BankAccount(100)
print(account.get_balance())
account.set_balance(150)
```

### Chapter 13: Files and Exception Handling

#### Text Input and Output
To read text from a file, we do:
```python
file = open("filename.txt", "r")  # "r" for read mode
content = file.read()  # Read entire file as a string
file.close()  # Always close the file when done
```
To write text to a file, we do:
```python
file = open("filename.txt", "w")  # "w" for write mode (overwrites existing)
file.write("Hello, world!\n")  # Write a string to the file
file.close()  # Always close the file when done
```

To append text to a file, we do:
```python
file = open("filename.txt", "a")  # "a" for append mode
file.write("This will be added to the end of the file.\n")
file.close()  # Always close the file when done
```

Anything that we read or write to a file is treated as a string. If we want to work with numbers, we need to convert them using `int()` or `float()`.
```python
file = open("numbers.txt", "r")
line = file.readline()  # Read one line as a string
number = int(line)  # Convert the string to an integer
file.close()
```

#### Exception Handling
When the Python programs encounter an error, they raise an exception and stop abruptly. We don't want that to happen in any cases, so we can use exception handling to catch and handle errors gracefully.

```python
try:
    # Code that may raise an exception
    num = int(input("Enter a number: "))
    result = 10 / num
    print("Result:", result)
except ValueError:
    print("Invalid input! Please enter a valid integer.")
except ZeroDivisionError:
    print("Cannot divide by zero!")
except Exception as e:
    print("An unexpected error occurred:", e)
```

or like this when we try to open a file that may not exist:
```python
try:
    file = open("nonexistent.txt", "r")
    content = file.read()
    file.close()
except FileNotFoundError:
    print("The file does not exist!")
```

we can also use finally or else blocks:
```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("The file does not exist!")
else:
    print("File read successfully!")
finally:
    print("This will always execute, whether an exception occurred or not.")
```

to verify if a file exists before trying to open it, we can use the `os` module:
```python
import os
if os.path.exists("data.txt"): # returns True if the file exists, False otherwise
    file = open("data.txt", "r")
    content = file.read()
    file.close()
else:
    print("The file does not exist!")
```

#### Raising Exceptions
We can also raise exceptions ourselves when we want to signal that something went wrong.

```python
raise ExceptionClass("Something is wrong") # ExceptionClass can be ValueError, TypeError, etc. or a custom exception class we define ourselves.
raise RuntimeError("Wrong argument") 
```

#### Binary Input and Output using Pickle
Binary files usually have the `.dat` extension. We can use the `pickle` module to read and write binary files.
To read or write, we have to open the file in binary mode by adding `b` to the mode string, like `"rb"` for reading and `"wb"` for writing. Then, we can use `pickle.dump()` to write an object to a file and `pickle.load()` to read an object from a file.
```python
import pickle
# Writing to a binary file
data = {"name": "Alice", "age": 30}
with open("data.dat", "wb") as file:
    pickle.dump(data, file)
# Reading from a binary file
with open("data.dat", "rb") as file:
    loaded_data = pickle.load(file)
print(loaded_data)  # Output: {'name': 'Alice', 'age': 30}
```
### Chapter 14: Tuples, Sets, and Dictionaries

Here's the summary of the key points about tuples, sets, and dictionaries:
| Property | List | Tuple | Set | Dictionary |
| -------- | ---- | ----- | --- | ---------- |
| Syntax | `[]` or `list()` | `()` or `tuple()` | `{}` or `set()` | `{key: value}` or `dict()` |
| Accessing Syntax | `mylist[index]` | `mytuple[index]` | No indexing (unordered) | `mydict[key]` |
| Mutability | Mutable | Immutable | Mutable | Mutable |
| Ordered | Yes | Yes | No | No |
| Duplicates | Allowed | Allowed | Not allowed | Keys not allowed, values allowed |
| Indexing | Yes | Yes | No | No |
| Iteration | Yes | Yes | Yes (unordered) | Yes (keys) |
| Use Cases | General-purpose collection | Fixed data, multiple types | Unique items, membership testing | Key-value pairs, fast lookup |

#### Tuples
- A tuple is an ordered, immutable collection of items. It is defined using parentheses `()`.
```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # Output: 1
for item in my_tuple:
    print(item,end=" ")  # Output: 1 2 3
my_list_of_tuples = [(1, 2), (3, 4), (5, 6)]
```
#### Sets
- A set is an unordered, mutable collection of unique items. It is defined using curly braces `{}`.
```python
my_set = {1, 2, 3}
print(my_set)  # Output: {1, 2, 3}
my_set.add(4)  # my_set is now {1, 2, 3, 4}
my_set.add(2)  # my_set is still {1, 2, 3, 4} (2 is already in the set)
my_set.remove(3)  # my_set is now {1, 2, 4}
new_set = {3, 4, 5}
print(my_set.union(new_set))  # Output: {1, 2, 3, 4, 5}
print(my_set.intersection(new_set))  # Output: {4}
print(my_set.difference(new_set))  # Output: {1, 2}
```

#### Dictionaries
- A dictionary is an unordered, mutable collection of key-value pairs. It is defined using curly braces `{}` with a colon `:` separating keys and values.
```python
my_dict = {"name": "Alice", "age": 30}
print(my_dict["name"])  # Output: Alice
my_dict["age"] = 31  # Update age to 31
my_dict["city"] = "New York"  # Add new key-value pair
print(my_dict)  # Output: {'name': 'Alice', 'age': 31, 'city': 'New York'}
for key in my_dict:
    print(key, my_dict[key])  # Output: name Alice, age 31, city New York
my_dict.pop("age")  # Remove the key "age"
print(my_dict)  # Output: {'name': 'Alice', 'city': 'New York'}
#Common errors:
print(my_dict["age"])  # KeyError: 'age' (since "age" was removed)
my_dict[[1, 2]] = "value"  # TypeError: unhashable type: 'list' (keys must be immutable)
my_dict[{"key": "value"}] = "value"  # TypeError: unhashable type: 'dict' (keys must be immutable)
my_dict[("tuple","")] = "value"  # This works since tuples are immutable
```
#### Where to use each type:
- Use a **tuple** when you want an ordered collection of items that should not change (e.g., coordinates, RGB color).
- Use a **set** when you want a collection of unique items and don't care about order (e.g., unique words in a text).
- Use a **dictionary** when you want to associate keys with values (e.g., a phone book, student grades).