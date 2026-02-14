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
