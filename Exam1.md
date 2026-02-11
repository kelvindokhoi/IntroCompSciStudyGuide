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
3. Multiplication `*`, Division `/`, Floor Division `//`, Modulo `%`
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