# Exam 1 Study Guide
## Author: Kelvin & Moe

### Chapter 1:

#### Bits and Bytes
Computer store data in binary form ***(0s and 1s)***. A bit is a single binary digit. ***8 bits = 1 byte***.


#### Components of a Computer
1. **Central Processing Unit (CPU)**: The brain.
2. **Memory (RAM)**: Short-term memory.
3. **Storage**: Long-term memory (e.g., hard drive, SSD).
4. **Input Devices**: Keyboard, mouse.
5. **Output Devices**: Monitor, printer.

#### Operating Systems
An operating system (OS) manages hardware and software resources. Examples include Windows, macOS, and Linux.

### Chapter 2: Elementary Programming

## Variables and Assignments

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

## Getting Input

- `input()` **always returns a string** — must convert for math

```python
name = input("Enter your name: ")          # returns str
age = int(input("Enter your age: "))        # convert to int
gpa = float(input("Enter your GPA: "))      # convert to float
```

- `input("prompt")` — the prompt string is optional but recommended

---

## Data Types

| Type    | Description         | Example            |
|---------|---------------------|--------------------|
| `int`   | Whole numbers       | `5`, `-3`, `0`     |
| `float` | Decimal numbers     | `3.14`, `-0.5`     |
| `str`   | Text / strings      | `"hello"`, `'hi'`  |
| `bool`  | True or False       | `True`, `False`    |

### Type Conversion (Casting)

```python
int(3.9)       # 3  (truncates, does NOT round)
float(3)       # 3.0
str(42)        # "42"
int("15")      # 15
float("3.14")  # 3.14
type(x)        # check the type of x
```

### Key Rules

- `int / int` → **always `float`** in Python 3 (e.g., `5 / 2` → `2.5`)
- `int // int` → **always `int`** in Python 3 (e.g., `5 // 2` → `2`)
- `int + float` → result is **`float`** (automatic widening)
- Overflow: Python `int` has **no limit** (arbitrary precision)

---

## Operators (in order of precedence)

| Precedence | Operator       | Description                  | Example               |
|------------|----------------|------------------------------|-----------------------|
| 0 (highest)| `()`           | Parentheses                  | `(3 + 2) * 4` → `20` |
| 1 (high)   | `**`           | Exponentiation               | `2 ** 3` → `8`       |
| 2          | `*`, `/`, `//`, `%` | Multiply, Divide, Floor Div, Modulus | see below |
| 3 (low)    | `+`, `-`       | Addition, Subtraction        | `3 + 2` → `5`        |

- **Same precedence** → evaluated **left to right** (except `**` which is **right to left**)
- Use **parentheses `()`** to override precedence

### Key Operators

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

## String Formatting

### 1. f-strings

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

### 2. `print()` details

```python
print("a", "b", "c")            # a b c  (space separated by default)
print("a", "b", sep=", ")       # a, b   (custom separator)
print("hello", end="")          # no newline at end
print("hello", end="!\n")       # custom ending
```

---

## Quick Reference — Common Pitfalls

| Mistake | Why it's wrong | Fix |
|---------|---------------|-----|
| `input()` used in math directly | `input()` returns `str` | Wrap with `int()` or `float()` |
| `5 / 2` expecting `2` | `/` gives float in Python 3 | Use `//` for integer division |
| `int(3.9)` expecting `4` | `int()` truncates, doesn't round | Use `round(3.9)` for rounding |
| `"age: " + 21` | Can't concatenate `str` + `int` | Use `str(21)` or f-string |
| `x = x + 1` before assigning `x` | `x` not defined yet | Initialize `x` first |

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
1. ***and***: Both conditions must be true.
2. ***or***: At least one condition must be true.
3. ***not***: Negates the condition.

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