# Python OOP Mastery: 8-Week Curriculum
## Complete Guide from Fundamentals to Proficiency

**Duration**: 8 Weeks (6 days/week, Sundays off)  
**Daily Time Commitment**: 1.4 hours  
**Total Hours**: ~67 hours  
**Python Version**: 3.13  
**IDE**: VSCode with Python extension

---

## Table of Contents

- [Chapter 0: Debugging Python in VSCode](#chapter-0-debugging-python-in-vscode)
- [Week 1: Python Fundamentals I](#week-1-python-fundamentals-i)
- [Week 2: Python Fundamentals II](#week-2-python-fundamentals-ii)
- [Week 3: Introduction to OOP](#week-3-introduction-to-oop)
- [Week 4: OOP Core Concepts](#week-4-oop-core-concepts)
- [Week 5: Intermediate OOP](#week-5-intermediate-oop)
- [Week 6: Advanced OOP Patterns](#week-6-advanced-oop-patterns)
- [Week 7: Design Patterns & Best Practices](#week-7-design-patterns--best-practices)
- [Week 8: Capstone Project](#week-8-capstone-project)
- [Grading Rubrics](#grading-rubrics)

---

<details>
<summary><h1>Chapter 0: Debugging Python in VSCode</h1></summary>

**Time**: Complete before Week 1 begins  
**Estimated Duration**: 2 hours (one-time setup and learning)

## Setup Instructions

### 1. Install Required Tools

**Python 3.13**
- Download from: https://www.python.org/downloads/
- During installation, check "Add Python to PATH"
- Verify installation: Open terminal and run `python --version`

**VSCode**
- Download from: https://code.visualstudio.com/
- Install the Python extension by Microsoft
  - Open VSCode → Extensions (Ctrl+Shift+X)
  - Search for "Python"
  - Install the extension by Microsoft (should be the top result)

### 2. Configure VSCode for Python

1. **Create a workspace folder** for this course (e.g., `python_oop_course`)
2. **Open VSCode** and open this folder (File → Open Folder)
3. **Select Python interpreter**:
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
   - Type "Python: Select Interpreter"
   - Choose Python 3.13

### 3. Debugging Basics

#### Setting Up a Debug Configuration

1. **Create a Python file**: `test_debug.py`
```python
def calculate_sum(numbers):
    total = 0
    for num in numbers:
        total += num
    return total

def main():
    data = [1, 2, 3, 4, 5]
    result = calculate_sum(data)
    print(f"Sum is: {result}")
    
    # Intentional error for debugging practice
    bad_data = [1, "two", 3]
    result2 = calculate_sum(bad_data)
    print(f"Sum 2 is: {result2}")

if __name__ == "__main__":
    main()
```

2. **Set a breakpoint**:
   - Click in the gutter (left of line numbers) on line 3 (the `total = 0` line)
   - A red dot appears indicating a breakpoint

3. **Start debugging**:
   - Press `F5` or click Run → Start Debugging
   - Select "Python File" when prompted
   - Code execution will pause at your breakpoint

#### Debugging Controls

| Action | Shortcut | Description |
|--------|----------|-------------|
| **Continue** | `F5` | Resume execution until next breakpoint |
| **Step Over** | `F10` | Execute current line, don't enter functions |
| **Step Into** | `F11` | Enter into function calls |
| **Step Out** | `Shift+F11` | Exit current function |
| **Restart** | `Ctrl+Shift+F5` | Restart debugging session |
| **Stop** | `Shift+F5` | Stop debugging |

#### Debug Panels

**Variables Panel**: Shows all variables in current scope and their values

**Watch Panel**: Add expressions to monitor (right-click variable → Add to Watch)

**Call Stack**: Shows the sequence of function calls that led to current position

**Debug Console**: Execute Python code in current context
- Example: Type `total` to see its current value
- Example: Type `len(numbers)` to check the length

### 4. Common Debugging Techniques

#### Technique 1: Print Statement Debugging
```python
def buggy_function(data):
    print(f"DEBUG: Input data = {data}")  # Add debug prints
    result = process_data(data)
    print(f"DEBUG: Result = {result}")
    return result
```

#### Technique 2: Conditional Breakpoints
- Right-click on a breakpoint → Edit Breakpoint
- Add condition: `num == "two"` (only breaks when condition is True)

#### Technique 3: Exception Breakpoints
- In Debug view, check "Raised Exceptions" under BREAKPOINTS
- Debugger will pause when any exception is raised

#### Technique 4: Logpoints
- Right-click in gutter → Add Logpoint
- Enter: `"Value of total: {total}"`
- Logs to Debug Console without stopping execution

### 5. Debugging Best Practices

1. **Start with the error message**: Read the full traceback from bottom to top
2. **Isolate the problem**: Use breakpoints to narrow down where things go wrong
3. **Check assumptions**: Use the debug console to verify variable values
4. **Step through systematically**: Use Step Over to understand execution flow
5. **Use the call stack**: Navigate through function calls to understand context

### 6. Exercise: Debug Practice

Create a file called `debug_practice.py` with this buggy code:

```python
def find_average(numbers):
    total = 0
    for num in numbers:
        total += num
    return total / len(numbers)

def process_scores(scores_dict):
    results = {}
    for student, scores in scores_dict.items():
        avg = find_average(scores)
        results[student] = avg
    return results

# Test data with bugs
students = {
    "Alice": [85, 90, 92],
    "Bob": [78, 82],
    "Charlie": [],  # Bug: empty list
    "David": [95, 88, 91, 87]
}

final_results = process_scores(students)
print(final_results)
```

**Your task**:
1. Run the code (it will crash)
2. Use breakpoints to identify the problem
3. Check the Variables panel when the error occurs
4. Fix the bug so empty score lists return 0 average
5. Verify your fix works

**Solution** (try first before looking):
```python
def find_average(numbers):
    if len(numbers) == 0:
        return 0
    total = 0
    for num in numbers:
        total += num
    return total / len(numbers)
```

### 7. VSCode Python Debugging Resources

- **Official Documentation**: https://code.visualstudio.com/docs/python/debugging
- **Python Extension Documentation**: https://code.visualstudio.com/docs/languages/python
- **Debugging Tutorial Video**: https://code.visualstudio.com/docs/introvideos/debugging

### Chapter 0 Completion Checklist

- [ ] Python 3.13 installed and in PATH
- [ ] VSCode installed with Python extension
- [ ] Successfully set and hit a breakpoint
- [ ] Used Step Over, Step Into, and Continue
- [ ] Examined variables in the Variables panel
- [ ] Used the Debug Console to evaluate expressions
- [ ] Completed the debug practice exercise

**Once completed, you're ready to start Week 1!**

</details>

---

<details>
<summary><h1>Week 1: Python Fundamentals I</h1></summary>

**Focus**: Variables, Data Types, Conditional Statements, and Basic Input/Output

## Day 1: Variables, Data Types, and Basic I/O

**Concepts** (40 min):

### Variables and Assignment
```python
# Variables don't need type declaration
name = "Alice"
age = 30
is_active = True
salary = 75000.50

# Multiple assignment
x, y, z = 1, 2, 3

# Swapping variables
a, b = 5, 10
a, b = b, a  # Now a=10, b=5
```

### Basic Data Types
```python
# int (integers)
count = 42
negative = -17

# float (decimal numbers)
temperature = 98.6
pi = 3.14159

# str (strings)
message = "Hello, World!"
multiline = """This is
a multiline
string"""

# bool (boolean)
is_valid = True
is_complete = False

# type() function shows data type
print(type(count))  # <class 'int'>
print(type(temperature))  # <class 'float'>
```

### Type Conversion
```python
# Convert between types
num_str = "42"
num_int = int(num_str)  # "42" → 42
num_float = float(num_str)  # "42" → 42.0

# Be careful with invalid conversions
# bad = int("hello")  # ValueError!

# String concatenation vs addition
age = 25
# Wrong: print("Age: " + age)  # TypeError
# Right: print("Age: " + str(age))
# Better: print(f"Age: {age}")  # f-strings
```

### Input and Output
```python
# Output
print("Hello, World!")
print("Value:", 42, "Name:", "Alice")  # Multiple values

# Input (always returns string)
name = input("Enter your name: ")
age_str = input("Enter your age: ")
age = int(age_str)  # Convert to int

# f-strings (formatted string literals)
print(f"Hello, {name}! You are {age} years old.")
```

**Practice** (50 min):

**Exercise 1.1**: Personal Information Program
```python
# Write a program that:
# 1. Asks for user's name, age, and city
# 2. Asks if they are a student (yes/no)
# 3. Asks for their GPA (if student)
# 4. Prints a formatted summary using f-strings

# Expected output format:
# Name: Alice
# Age: 22
# City: New York
# Student Status: Yes
# GPA: 3.75
```

**Exercise 1.2**: Temperature Converter
```python
# Write a program that:
# 1. Asks user for temperature in Celsius
# 2. Converts to Fahrenheit: F = (C * 9/5) + 32
# 3. Converts to Kelvin: K = C + 273.15
# 4. Prints all three temperatures with labels
# 5. Use proper variable names and comments
```

**Exercise 1.3**: Type Exploration
```python
# Create variables of each type:
# - An integer (your favorite number)
# - A float (pi to 5 decimal places)
# - A string (your favorite quote)
# - A boolean (whether you like Python)
# 
# Print each variable with its type using type()
# Example: print(f"{my_var} is type {type(my_var)}")
```

---

## Day 2: Operators and Expressions

**Concepts** (40 min):

### Arithmetic Operators
```python
# Basic operations
a = 10
b = 3

addition = a + b        # 13
subtraction = a - b     # 7
multiplication = a * b  # 30
division = a / b        # 3.3333... (always returns float)
floor_division = a // b # 3 (integer division)
modulus = a % b         # 1 (remainder)
exponent = a ** b       # 1000 (10^3)

# Operator precedence (PEMDAS)
result = 2 + 3 * 4      # 14 (not 20)
result = (2 + 3) * 4    # 20 (parentheses first)
```

### Comparison Operators
```python
x = 5
y = 10

equal = x == y          # False
not_equal = x != y      # True
greater = x > y         # False
less = x < y            # True
greater_equal = x >= 5  # True
less_equal = y <= 10    # True

# Comparing strings (lexicographic)
"apple" < "banana"      # True (alphabetical order)
"10" < "2"              # True (string comparison, not numeric!)
```

### Logical Operators
```python
# and, or, not
age = 25
has_license = True

can_drive = age >= 16 and has_license  # True
is_teen = age >= 13 and age < 20       # False
is_not_teen = not is_teen              # True

# Short-circuit evaluation
x = 5
# This won't cause error even though y doesn't exist:
result = x < 3 and y > 10  # False (doesn't evaluate y > 10)
```

### Assignment Operators
```python
x = 10

x += 5   # x = x + 5  → x is now 15
x -= 3   # x = x - 3  → x is now 12
x *= 2   # x = x * 2  → x is now 24
x /= 4   # x = x / 4  → x is now 6.0
x //= 2  # x = x // 2 → x is now 3.0
x %= 2   # x = x % 2  → x is now 1.0
```

**Practice** (50 min):

**Exercise 1.4**: Calculator Program
```python
# Create a basic calculator that:
# 1. Asks for two numbers
# 2. Performs all basic operations (+, -, *, /, //, %, **)
# 3. Prints results in a formatted way
# 
# Example output:
# Enter first number: 10
# Enter second number: 3
# Addition: 10 + 3 = 13
# Subtraction: 10 - 3 = 7
# ... (all operations)
```

**Exercise 1.5**: Circle Calculator
```python
# Write a program that:
# 1. Asks for the radius of a circle
# 2. Calculates:
#    - Diameter (2 * r)
#    - Circumference (2 * pi * r)
#    - Area (pi * r^2)
# 3. Prints results rounded to 2 decimal places
# Use 3.14159 for pi
```

**Exercise 1.6**: Age Calculator
```python
# Create a program that:
# 1. Asks for birth year
# 2. Calculates current age (assume current year is 2024)
# 3. Calculates age in months (age * 12)
# 4. Calculates age in days (age * 365, ignore leap years)
# 5. Determines if user can vote (age >= 18)
# 6. Prints all results with appropriate labels
```

---

## Day 3: Conditional Statements I (if, elif, else)

**Concepts** (35 min):

### Basic if Statement
```python
age = 20

if age >= 18:
    print("You are an adult")
    print("You can vote")

# Code here runs regardless of condition
print("Program continues")
```

### if-else Statement
```python
temperature = 75

if temperature > 80:
    print("It's hot outside")
else:
    print("It's not hot outside")
```

### if-elif-else Statement
```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Your grade is: {grade}")
```

### Nested Conditionals
```python
age = 25
has_license = True

if age >= 16:
    if has_license:
        print("You can drive")
    else:
        print("You need a license")
else:
    print("Too young to drive")
```

### Combining Conditions
```python
age = 25
income = 50000

# Using 'and'
if age >= 18 and income >= 30000:
    print("Eligible for loan")

# Using 'or'
if age < 18 or income < 30000:
    print("Not eligible for loan")

# Complex conditions
if (age >= 18 and income >= 30000) or age >= 65:
    print("Special consideration")
```

**Practice** (55 min):

**Exercise 1.7**: Grade Calculator
```python
# Create a grading system that:
# 1. Asks for a numerical score (0-100)
# 2. Assigns letter grade:
#    90-100: A
#    80-89: B
#    70-79: C
#    60-69: D
#    Below 60: F
# 3. Add special messages:
#    - Score > 95: "Excellent work!"
#    - Score < 60: "You need to study more"
# 4. Handle invalid input (score < 0 or > 100)
```

**Exercise 1.8**: Login System
```python
# Create a simple login checker:
# 1. Define correct username and password (hardcoded)
# 2. Ask user for username
# 3. If username correct, ask for password
# 4. If both correct: "Login successful"
# 5. If username wrong: "Invalid username"
# 6. If password wrong: "Invalid password"
# 7. Add: After 3 failed attempts, display "Account locked"
```

**Exercise 1.9**: BMI Calculator with Categories
```python
# Body Mass Index calculator:
# 1. Ask for weight (kg) and height (meters)
# 2. Calculate BMI = weight / (height^2)
# 3. Categorize based on BMI:
#    < 18.5: Underweight
#    18.5-24.9: Normal weight
#    25-29.9: Overweight
#    >= 30: Obese
# 4. Print BMI and category
# 5. Add health advice for each category
```

---

## Day 4: Conditional Statements II (Complex Conditions)

**Concepts** (35 min):

### Truth Values and Comparisons
```python
# Everything in Python has a truth value
bool(0)          # False
bool(1)          # True
bool("")         # False (empty string)
bool("hello")    # True
bool(None)       # False

# This allows concise conditionals
name = input("Enter name: ")
if name:  # True if name is not empty
    print(f"Hello, {name}")
else:
    print("No name provided")
```

### Ternary Operator (Conditional Expression)
```python
# Long form
age = 20
if age >= 18:
    status = "adult"
else:
    status = "minor"

# Short form (ternary)
status = "adult" if age >= 18 else "minor"

# Another example
max_value = a if a > b else b  # Returns larger of a or b
```

### Match Statement (Python 3.10+)
```python
# Modern alternative to multiple elif statements
status_code = 404

match status_code:
    case 200:
        message = "OK"
    case 404:
        message = "Not Found"
    case 500:
        message = "Internal Server Error"
    case _:  # Default case (like 'else')
        message = "Unknown Status"

print(message)

# Match with conditions
match age:
    case n if n < 13:
        category = "child"
    case n if n < 20:
        category = "teenager"
    case _:
        category = "adult"
```

### Defensive Programming
```python
# Validate input before processing
user_input = input("Enter a number: ")

# Check if input is numeric
if user_input.isdigit():
    number = int(user_input)
    result = number * 2
    print(f"Double is: {result}")
else:
    print("Error: Please enter a valid number")

# Check for division by zero
divisor = int(input("Enter divisor: "))
if divisor != 0:
    result = 100 / divisor
    print(f"Result: {result}")
else:
    print("Error: Cannot divide by zero")
```

**Practice** (55 min):

**Exercise 1.10**: Ticket Pricing System
```python
# Movie ticket pricing calculator:
# 1. Ask for age and day of week
# 2. Pricing rules:
#    - Children (< 12): $8
#    - Seniors (>= 65): $10
#    - Adults (12-64): $15
#    - Tuesday discount: 20% off all tickets
#    - Weekend (Saturday/Sunday): $3 surcharge for adults only
# 3. Calculate final price
# 4. Print itemized receipt showing:
#    - Base price
#    - Any discounts
#    - Any surcharges
#    - Final price
```

**Exercise 1.11**: Password Strength Checker
```python
# Check password strength:
# 1. Ask user for password
# 2. Check these criteria:
#    - Length >= 8 characters
#    - Contains at least one digit
#    - Contains at least one uppercase letter
#    - Contains at least one lowercase letter
# 3. Assign strength:
#    - All 4 criteria: "Strong"
#    - 3 criteria: "Medium"
#    - 2 criteria: "Weak"
#    - 1 or 0 criteria: "Very Weak"
# 4. Print strength and which criteria were met/missed
# 
# Hints: 
# - use .isdigit(), .isupper(), .islower()
# - use 'in' to check for characters
```

**Exercise 1.12**: Tax Calculator
```python
# Progressive tax calculator:
# 1. Ask for annual income
# 2. Calculate tax based on brackets:
#    - $0-$10,000: 0% tax
#    - $10,001-$30,000: 10% tax
#    - $30,001-$60,000: 20% tax
#    - $60,001+: 30% tax
# 3. Tax is calculated on each bracket separately:
#    Example: $35,000 income
#    - First $10,000: $0
#    - Next $20,000: $2,000 (10%)
#    - Remaining $5,000: $1,000 (20%)
#    - Total tax: $3,000
# 4. Print breakdown and total tax owed
```

---

## Day 5: Introduction to Loops (while loops)

**Concepts** (40 min):

### Basic while Loop
```python
# Repeat code while condition is True
count = 0
while count < 5:
    print(f"Count is: {count}")
    count += 1
print("Loop finished")

# Infinite loop (be careful!)
# while True:
#     print("This runs forever!")  # Use Ctrl+C to stop
```

### Loop Control: break and continue
```python
# break - exit loop immediately
count = 0
while count < 10:
    if count == 5:
        break  # Exit loop when count reaches 5
    print(count)
    count += 1
# Output: 0, 1, 2, 3, 4

# continue - skip rest of current iteration
count = 0
while count < 5:
    count += 1
    if count == 3:
        continue  # Skip printing 3
    print(count)
# Output: 1, 2, 4, 5
```

### Input Validation with while
```python
# Keep asking until valid input
age = -1
while age < 0 or age > 120:
    age = int(input("Enter your age (0-120): "))
    if age < 0 or age > 120:
        print("Invalid age. Try again.")

print(f"Your age is: {age}")
```

### Sentinel-Controlled Loops
```python
# Loop until specific value (sentinel) is entered
total = 0
value = 0

while value != -1:
    value = int(input("Enter a number (-1 to quit): "))
    if value != -1:
        total += value

print(f"Sum: {total}")
```

**Practice** (50 min):

**Exercise 1.13**: Guessing Game
```python
# Number guessing game:
# 1. Program picks a secret number (1-100)
# 2. User has unlimited guesses
# 3. After each guess, tell them "Too high" or "Too low"
# 4. When correct, print "Correct! You guessed in X tries"
# 5. Add option to quit by entering 0
# 
# Hint: import random; secret = random.randint(1, 100)
```

**Exercise 1.14**: ATM Simulator
```python
# Simple ATM menu system:
# 1. Start with balance of $1000
# 2. Menu options:
#    1. Check Balance
#    2. Deposit
#    3. Withdraw
#    4. Exit
# 3. Loop until user chooses Exit
# 4. Validate withdrawals (can't withdraw more than balance)
# 5. Keep running total of transactions
```

**Exercise 1.15**: Multiplication Table Quiz
```python
# Math practice program:
# 1. Ask user which multiplication table (1-12)
# 2. Quiz them on all 12 problems (x * 1 through x * 12)
# 3. Keep track of correct/incorrect answers
# 4. Show final score at end
# 5. Ask if they want to practice another table
```

---

## Day 6: Weekly Assignment - Week 1

**Time**: 1.4 hours  
**Due**: End of Day 6  
**Grading**: See rubric at end

### Assignment 1: Personal Finance Tracker

Create a comprehensive personal finance tracking program that demonstrates all concepts from Week 1.

**Requirements**:

1. **User Profile Setup** (Variables, Input, Data Types)
   - Ask for user's name and monthly income
   - Ask for number of dependents
   - Store this information in variables

2. **Expense Categories** (Conditionals, Operators)
   - Ask user to enter expenses for:
     - Housing (rent/mortgage)
     - Transportation
     - Food
     - Utilities
     - Entertainment
   - Calculate total expenses
   - Calculate remaining money (income - expenses)

3. **Budget Analysis** (Complex Conditionals)
   - Calculate percentage of income spent
   - Provide feedback:
     - < 50% spent: "Excellent! You're saving well"
     - 50-75% spent: "Good job managing your money"
     - 75-90% spent: "Be careful, you're spending a lot"
     - 90-100% spent: "Warning! You're spending almost all your income"
     - > 100% spent: "Alert! You're spending more than you earn"

4. **Expense Adjustment** (Loops, Input Validation)
   - If spending > 90%, enter a loop that:
     - Shows current expenses by category
     - Asks which category to reduce
     - Asks how much to reduce
     - Recalculates total and percentage
     - Continues until spending < 90% or user quits

5. **Final Report** (Output, F-strings)
   - Print a formatted summary showing:
     - User profile
     - All expense categories with amounts
     - Total expenses
     - Remaining money
     - Percentage of income spent
     - Final advice based on spending

**Example Output**:
```
=== Personal Finance Tracker ===

Enter your name: Alice
Enter monthly income: 5000
Enter number of dependents: 2

--- Enter Monthly Expenses ---
Housing: 1500
Transportation: 400
Food: 600
Utilities: 200
Entertainment: 150

--- Budget Analysis ---
Name: Alice
Monthly Income: $5000.00
Dependents: 2

Expenses:
  Housing:        $1500.00
  Transportation: $400.00
  Food:           $600.00
  Utilities:      $200.00
  Entertainment:  $150.00
  ----------------
  Total:          $2850.00

Remaining Money: $2150.00
Spending Rate: 57.0% of income

Financial Status: Good job managing your money
Advice: You're in a healthy spending range. Consider saving the extra $2150.00 for emergencies or future goals.
```

**Bonus Challenges** (+10 points each):
1. Add savings goal tracking (user sets a goal, program calculates months to reach it)
2. Implement a "what-if" analyzer (let user test different expense scenarios)
3. Add monthly comparison (store previous month and show increase/decrease)

---

### Grading Rubric - Week 1 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **Functionality** | 40 | |
| Profile setup | 10 | Correctly captures and stores user info |
| Expense tracking | 10 | All 5 categories input and calculated |
| Budget analysis | 10 | Correct calculations and conditional feedback |
| Expense adjustment loop | 10 | Working loop with proper validation |
| **Code Quality** | 30 | |
| Variable naming | 10 | Descriptive, consistent names (snake_case) |
| Comments | 10 | Clear comments explaining logic |
| Code organization | 10 | Logical flow, proper indentation |
| **Output & UX** | 20 | |
| Formatted output | 10 | Clean, aligned, professional formatting |
| User experience | 10 | Clear prompts, helpful error messages |
| **Input Validation** | 10 | |
| Error handling | 10 | Validates numeric input, handles edge cases |
| **Bonus** | +30 | Up to 3 bonus challenges (+10 each) |

**Grading Scale**:
- 90-100: A (Excellent)
- 80-89: B (Good)
- 70-79: C (Satisfactory)
- 60-69: D (Needs Improvement)
- Below 60: F (Incomplete)

**Submission**:
- Save as `week1_assignment.py`
- Include your name and date in comments at top
- Test thoroughly before submitting

</details>

---

<details>
<summary><h1>Week 2: Python Fundamentals II</h1></summary>

**Focus**: Loops (for), Variable Scope, Lists, and Dictionaries

## Day 7 (Monday): For Loops and range()

**Concepts** (35 min):

### Basic for Loop
```python
# for loop iterates over a sequence
for i in range(5):
    print(i)
# Output: 0, 1, 2, 3, 4

# range(start, stop, step)
for i in range(1, 10, 2):
    print(i)
# Output: 1, 3, 5, 7, 9

# Counting backwards
for i in range(10, 0, -1):
    print(i)
# Output: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

### Iterating Over Strings
```python
name = "Python"
for letter in name:
    print(letter)
# Output: P, y, t, h, o, n

# With index using enumerate()
for index, letter in enumerate(name):
    print(f"Position {index}: {letter}")
```

### Nested Loops
```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} x {j} = {i*j}")
    print("---")  # Separator between rows
```

### Loop Control in for Loops
```python
# break - exit loop early
for i in range(10):
    if i == 5:
        break
    print(i)
# Output: 0, 1, 2, 3, 4

# continue - skip current iteration
for i in range(5):
    if i == 2:
        continue
    print(i)
# Output: 0, 1, 3, 4

# else clause (runs if loop completes without break)
for i in range(5):
    print(i)
else:
    print("Loop completed normally")
```

**Practice** (55 min):

**Exercise 2.1**: Pattern Printer
```python
# Create a program that prints various patterns:
# 
# Pattern 1 - Right Triangle:
# *
# **
# ***
# ****
# *****
#
# Pattern 2 - Number Pyramid:
# 1
# 12
# 123
# 1234
# 12345
#
# Pattern 3 - Multiplication Table (user chooses size)
# Ask user for a number, print multiplication table up to 10
```

**Exercise 2.2**: Prime Number Checker
```python
# Write a program that:
# 1. Asks user for a number
# 2. Checks if it's prime (only divisible by 1 and itself)
# 3. Use a for loop to test divisibility
# 4. Use break to exit early if factor found
# 5. Print whether number is prime or not
# 6. If not prime, list all factors
```

**Exercise 2.3**: Factorial Calculator
```python
# Calculate factorial using for loop:
# 1. Ask user for a number n
# 2. Calculate n! = n × (n-1) × (n-2) × ... × 1
# 3. Example: 5! = 5 × 4 × 3 × 2 × 1 = 120
# 4. Print each multiplication step
# 5. Handle edge case: 0! = 1
```

---

## Day 8: Variable Scope

**Concepts** (40 min):

### Local vs Global Scope
```python
# Global variable
global_var = "I'm global"

def my_function():
    # Local variable
    local_var = "I'm local"
    print(global_var)  # Can access global
    print(local_var)   # Can access local

my_function()
# print(local_var)  # Error! local_var doesn't exist here
```

### The global Keyword
```python
counter = 0  # Global variable

def increment():
    global counter  # Declare we're using global counter
    counter += 1

increment()
print(counter)  # 1
increment()
print(counter)  # 2
```

### Function Parameters and Scope
```python
def greet(name):  # 'name' is local to this function
    message = f"Hello, {name}!"  # 'message' is also local
    return message

result = greet("Alice")
print(result)
# print(name)  # Error! 'name' doesn't exist here
```

### Nested Scope
```python
def outer():
    outer_var = "outer"
    
    def inner():
        inner_var = "inner"
        print(outer_var)  # Can access outer function's variables
        print(inner_var)
    
    inner()
    # print(inner_var)  # Error! Can't access inner's variables

outer()
```

### Best Practices
```python
# BAD - Relying on global variables
total = 0
def add_to_total(value):
    global total
    total += value

# GOOD - Passing values explicitly
def add_to_total(total, value):
    return total + value

total = 0
total = add_to_total(total, 5)
```

**Practice** (50 min):

**Exercise 2.4**: Scope Explorer
```python
# Create a program that demonstrates scope:
# 1. Define a global variable 'game_score = 0'
# 2. Create function 'increase_score(points)' that adds to score
# 3. Create function 'decrease_score(points)' that subtracts from score
# 4. Create function 'show_score()' that displays current score
# 5. In main program:
#    - Show initial score
#    - Increase by 10
#    - Decrease by 3
#    - Show final score
# 6. Explain in comments where each variable exists
```

**Exercise 2.5**: Temperature Logger
```python
# Build a temperature tracking system:
# 1. Global list to store temperatures
# 2. Function 'add_temperature(temp)' - adds temp to list
# 3. Function 'get_average()' - calculates average of all temps
# 4. Function 'get_highest()' - returns highest temp
# 5. Function 'get_lowest()' - returns lowest temp
# 6. Main program:
#    - Add at least 5 temperatures
#    - Display all statistics
# 7. Use proper scope (minimize global usage)
```

**Exercise 2.6**: Bank Account Manager
```python
# Create a simple bank account system:
# 1. Global variables: account_balance, account_holder
# 2. Function 'initialize_account(name, initial_balance)'
# 3. Function 'deposit(amount)' - adds to balance
# 4. Function 'withdraw(amount)' - subtracts from balance
#    - Return True if successful, False if insufficient funds
# 5. Function 'get_balance()' - returns current balance
# 6. Test all functions in main program
```

---

## Day 9: Lists I (Basics and Operations)

**Concepts** (40 min):

### Creating and Accessing Lists
```python
# Creating lists
numbers = [1, 2, 3, 4, 5]
names = ["Alice", "Bob", "Charlie"]
mixed = [1, "hello", 3.14, True]
empty = []

# Accessing elements (0-indexed)
print(numbers[0])   # 1 (first element)
print(numbers[-1])  # 5 (last element)
print(numbers[-2])  # 4 (second from end)

# Slicing
print(numbers[1:4])   # [2, 3, 4] (index 1 to 3)
print(numbers[:3])    # [1, 2, 3] (start to index 2)
print(numbers[2:])    # [3, 4, 5] (index 2 to end)
print(numbers[::2])   # [1, 3, 5] (every 2nd element)
print(numbers[::-1])  # [5, 4, 3, 2, 1] (reversed)
```

### Modifying Lists
```python
# Lists are mutable (can be changed)
fruits = ["apple", "banana", "cherry"]

# Changing an element
fruits[1] = "blueberry"  # ["apple", "blueberry", "cherry"]

# Adding elements
fruits.append("date")       # Add to end
fruits.insert(1, "apricot") # Insert at position 1
fruits.extend(["elderberry", "fig"])  # Add multiple

# Removing elements
fruits.remove("apple")  # Remove by value
popped = fruits.pop()   # Remove and return last
popped = fruits.pop(0)  # Remove and return at index
del fruits[0]          # Delete at index
fruits.clear()         # Remove all elements
```

### List Operations
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# Concatenation
combined = list1 + list2  # [1, 2, 3, 4, 5, 6]

# Repetition
repeated = list1 * 3  # [1, 2, 3, 1, 2, 3, 1, 2, 3]

# Membership
print(2 in list1)     # True
print(7 not in list1) # True

# Length
print(len(list1))  # 3

# Other useful methods
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()        # Sort in place
numbers.reverse()     # Reverse in place
print(numbers.count(1))   # Count occurrences of 1
print(numbers.index(4))   # Find index of first 4
```

**Practice** (50 min):

**Exercise 2.7**: Shopping List Manager
```python
# Create a shopping list application:
# 1. Start with empty list
# 2. Menu options:
#    1. Add item
#    2. Remove item
#    3. View list
#    4. Check if item in list
#    5. Clear list
#    6. Exit
# 3. Display numbered list when viewing
# 4. Handle errors (removing non-existent items)
```

**Exercise 2.8**: Number List Analyzer
```python
# Create a program that:
# 1. Asks user how many numbers to enter
# 2. Stores all numbers in a list
# 3. Calculates and displays:
#    - Sum of all numbers
#    - Average
#    - Largest number
#    - Smallest number
#    - Numbers above average
#    - Numbers below average
# 4. Print list in ascending order
# 5. Print list in descending order
```

**Exercise 2.9**: Grade Manager
```python
# Build a grade tracking system:
# 1. Create empty list for grades
# 2. Let user add grades (0-100)
# 3. Calculate:
#    - Average grade
#    - Letter grade (using average)
#    - Number of passing grades (>= 60)
#    - Number of failing grades
# 4. Display all grades
# 5. Find and display highest/lowest grades
# 6. Allow user to remove a specific grade
# 7. Show updated statistics
```

---

## Day 10: Lists II (Iteration and List Comprehensions)

**Concepts** (40 min):

### Iterating Through Lists
```python
# Basic iteration
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)

# With index
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# With custom index starting point
for index, fruit in enumerate(fruits, start=1):
    print(f"Item {index}: {fruit}")
```

### List Comprehensions
```python
# Traditional way
squares = []
for i in range(10):
    squares.append(i ** 2)

# List comprehension (more concise)
squares = [i ** 2 for i in range(10)]

# With condition
evens = [x for x in range(20) if x % 2 == 0]

# Transform existing list
names = ["alice", "bob", "charlie"]
upper_names = [name.upper() for name in names]

# With if-else
numbers = [1, 2, 3, 4, 5]
labels = ["even" if x % 2 == 0 else "odd" for x in numbers]
```

### Nested Lists
```python
# 2D list (list of lists)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Accessing elements
print(matrix[0][0])  # 1 (first row, first column)
print(matrix[1][2])  # 6 (second row, third column)

# Iterating through 2D list
for row in matrix:
    for element in row:
        print(element, end=" ")
    print()  # New line after each row
```

### Common List Patterns
```python
# Finding maximum/minimum
numbers = [3, 7, 2, 9, 1]
maximum = max(numbers)  # 9
minimum = min(numbers)  # 1

# Sum and average
total = sum(numbers)       # 22
average = sum(numbers) / len(numbers)  # 4.4

# Filtering
original = [1, 2, 3, 4, 5, 6]
evens = [x for x in original if x % 2 == 0]

# Mapping (transforming)
numbers = [1, 2, 3, 4]
doubled = [x * 2 for x in numbers]

# Copying lists (be careful!)
list1 = [1, 2, 3]
list2 = list1        # Reference (both point to same list)
list3 = list1.copy() # Actual copy
list4 = list1[:]     # Slice copy
```

**Practice** (50 min):

**Exercise 2.10**: Todo List Application
```python
# Create a comprehensive todo list app:
# 1. Each task is a list: [task_name, is_completed (True/False)]
# 2. Store all tasks in a list of lists
# 3. Menu options:
#    1. Add task
#    2. Mark task as complete
#    3. View all tasks (show completion status)
#    4. View incomplete tasks only
#    5. View completed tasks only
#    6. Remove task
#    7. Exit
# 4. Use list comprehensions where appropriate
# 5. Display tasks with numbered bullets
```

**Exercise 2.11**: Student Roster
```python
# Build a class roster system:
# 1. Each student is a list: [name, [list of grades]]
# 2. Store all students in a nested list
# 3. Functions to create:
#    - add_student(name)
#    - add_grade(student_name, grade)
#    - get_average(student_name)
#    - get_class_average()
#    - find_top_student()
#    - list_failing_students() (average < 60)
# 4. Print formatted roster with averages
```

**Exercise 2.12**: Matrix Operations
```python
# Implement basic matrix operations:
# 1. Create a 3x3 matrix from user input
# 2. Operations to implement:
#    - Print matrix in formatted grid
#    - Calculate sum of each row
#    - Calculate sum of each column
#    - Find largest element and its position
#    - Calculate average of all elements
#    - Transpose matrix (swap rows and columns)
# 3. Display all results clearly
```

---

## Day 11: Dictionaries

**Concepts** (40 min):

### Creating and Accessing Dictionaries
```python
# Creating dictionaries
student = {
    "name": "Alice",
    "age": 20,
    "major": "Computer Science"
}

# Empty dictionary
empty_dict = {}
also_empty = dict()

# Accessing values
print(student["name"])  # "Alice"
print(student.get("age"))  # 20
print(student.get("gpa", 0.0))  # 0.0 (default if key doesn't exist)

# KeyError if key doesn't exist
# print(student["gpa"])  # Error!
# print(student.get("gpa"))  # None (no error)
```

### Modifying Dictionaries
```python
person = {"name": "Bob", "age": 25}

# Adding/updating key-value pairs
person["city"] = "New York"  # Add new key
person["age"] = 26           # Update existing key

# Multiple updates
person.update({"job": "Engineer", "salary": 75000})

# Removing items
person.pop("salary")  # Remove and return value
del person["job"]     # Delete key
person.clear()        # Remove all items
```

### Dictionary Operations
```python
student = {"name": "Alice", "age": 20, "major": "CS"}

# Check if key exists
if "name" in student:
    print("Name exists")

# Get all keys, values, items
keys = student.keys()      # dict_keys(['name', 'age', 'major'])
values = student.values()  # dict_values(['Alice', 20, 'CS'])
items = student.items()    # dict_items([('name', 'Alice'), ...])

# Length
print(len(student))  # 3

# Iterate through dictionary
for key in student:
    print(f"{key}: {student[key]}")

for key, value in student.items():
    print(f"{key}: {value}")
```

### Nested Dictionaries
```python
# Dictionary of dictionaries
students = {
    "001": {"name": "Alice", "grade": 85},
    "002": {"name": "Bob", "grade": 92},
    "003": {"name": "Charlie", "grade": 78}
}

# Access nested values
print(students["001"]["name"])  # "Alice"

# Iterate through nested
for student_id, info in students.items():
    print(f"ID: {student_id}")
    print(f"  Name: {info['name']}")
    print(f"  Grade: {info['grade']}")
```

**Practice** (50 min):

**Exercise 2.13**: Contact Book
```python
# Create a contact management system:
# 1. Dictionary structure: {name: {"phone": "123-456", "email": "x@y.com"}}
# 2. Menu options:
#    1. Add contact
#    2. Search contact (by name)
#    3. Update contact
#    4. Delete contact
#    5. List all contacts
#    6. Exit
# 3. Handle duplicate names
# 4. Validate phone number format
# 5. Display contacts in alphabetical order
```

**Exercise 2.14**: Inventory System
```python
# Build a product inventory tracker:
# 1. Dictionary structure: {product_id: {"name": str, "price": float, "quantity": int}}
# 2. Functions to implement:
#    - add_product()
#    - update_quantity(product_id, amount) - can be positive or negative
#    - get_product_value(product_id) - price * quantity
#    - get_total_inventory_value()
#    - find_low_stock(threshold) - products below threshold quantity
#    - get_most_expensive()
# 3. Main menu for user interaction
# 4. Display formatted inventory report
```

**Exercise 2.15**: Word Frequency Counter
```python
# Create a word frequency analyzer:
# 1. Ask user to input a sentence or paragraph
# 2. Count frequency of each word (case-insensitive)
# 3. Store in dictionary: {word: frequency}
# 4. Display results:
#    - Total unique words
#    - Most common word and its count
#    - Least common word and its count
#    - All words sorted by frequency (descending)
#    - All words sorted alphabetically
# 5. Ignore punctuation (.!?,)
# 
# Example input: "Hello world! Hello Python. Python is great."
# Output:
# Word Frequencies:
# hello: 2
# python: 2
# world: 1
# is: 1
# great: 1
```

---

## Day 12: Weekly Assignment - Week 2

**Time**: 1.4 hours  
**Due**: End of Day 12  
**Grading**: See rubric at end

### Assignment 2: Student Grade Management System

Create a comprehensive student management system that uses all Week 2 concepts: for loops, scope, lists, and dictionaries.

**Program Structure**:

You will build a system with the following components:

1. **Global Data Structure**
```python
# Use this structure:
students = {
    "student_id": {
        "name": "Student Name",
        "grades": [85, 90, 78, 92],  # List of grades
        "attendance": 95.5  # Percentage
    }
}
```

2. **Required Functions** (Proper Scope Management):

```python
def add_student(student_id, name):
    """Add a new student to the system"""
    pass

def add_grade(student_id, grade):
    """Add a grade to a student's record"""
    pass

def calculate_average(student_id):
    """Calculate and return average grade for a student"""
    pass

def get_letter_grade(average):
    """Convert numeric average to letter grade"""
    pass

def display_student(student_id):
    """Display all information for one student"""
    pass

def display_all_students():
    """Display summary for all students"""
    pass

def get_class_statistics():
    """Calculate and return class-wide statistics"""
    pass

def find_honor_students():
    """Find students with average >= 90"""
    pass

def find_at_risk_students():
    """Find students with average < 70"""
    pass
```

3. **Main Menu Loop** (Implement these options):
   1. Add new student
   2. Add grade to student
   3. View single student
   4. View all students
   5. View class statistics
   6. View honor students
   7. View at-risk students
   8. Remove student
   9. Exit

4. **Required Features**:

   **Input Validation**:
   - Grades must be 0-100
   - Student IDs must be unique
   - Cannot add grades to non-existent students
   - Attendance must be 0-100%

   **Class Statistics** (using loops and list comprehensions):
   - Class average grade
   - Highest average student
   - Lowest average student
   - Total number of students
   - Average class attendance

   **Display Format**:
   ```
   ========================================
   Student ID: 12345
   Name: Alice Johnson
   Grades: [85, 90, 88, 92, 87]
   Average: 88.4
   Letter Grade: B
   Attendance: 95.5%
   Status: Good Standing
   ========================================
   ```

5. **Advanced Requirements**:

   - Use **list comprehensions** to filter students
   - Use **for loops** to iterate through dictionaries
   - Use **proper variable scope** (minimize global variables)
   - Include **docstrings** for all functions
   - Handle **edge cases** (empty grade list, etc.)

**Example Interaction**:
```
=== Student Grade Management System ===

1. Add new student
2. Add grade to student
3. View single student
4. View all students
5. View class statistics
6. View honor students
7. View at-risk students
8. Remove student
9. Exit

Enter choice: 1

Enter student ID: 12345
Enter student name: Alice Johnson
Enter initial attendance % (0-100): 95.5
Student added successfully!

Enter choice: 2

Enter student ID: 12345
Enter grade (0-100): 85
Grade added successfully!

... (continue interaction)
```

**Bonus Challenges** (+10 points each):
1. **Grade Trend Analysis**: Show if each student's grades are improving, declining, or stable
2. **Data Persistence**: Save data to a file and load it on startup
3. **Search Functionality**: Search students by name (partial match)
4. **Grade Distribution**: Show histogram of grade ranges (A's, B's, etc.)

---

### Grading Rubric - Week 2 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **Data Structures** | 20 | |
| Dictionary setup | 10 | Correct nested dictionary with lists |
| Data integrity | 10 | No data corruption, proper updates |
| **Functions** | 30 | |
| All 9 required functions | 15 | Each function works correctly |
| Proper scope | 10 | Minimal global usage, proper parameters |
| Docstrings | 5 | All functions documented |
| **Loops & Comprehensions** | 20 | |
| For loops | 10 | Correctly iterates through data structures |
| List comprehensions | 10 | Used for filtering/transforming data |
| **Input Validation** | 15 | |
| Grade validation | 5 | Ensures 0-100 range |
| Student ID validation | 5 | Checks for duplicates |
| Error handling | 5 | Graceful handling of invalid input |
| **Output & UX** | 15 | |
| Formatted displays | 10 | Clean, aligned, professional output |
| Menu system | 5 | Clear, easy to use |
| **Bonus** | +40 | Up to 4 bonus challenges (+10 each) |

**Code Quality Expectations**:
- Consistent naming conventions (snake_case)
- Meaningful variable and function names
- Proper indentation and spacing
- Comments explaining complex logic
- No redundant code

**Testing Checklist**:
- [ ] Can add multiple students
- [ ] Can add multiple grades per student
- [ ] Averages calculate correctly
- [ ] Statistics functions work with multiple students
- [ ] Honor students filter works (avg >= 90)
- [ ] At-risk students filter works (avg < 70)
- [ ] Cannot add invalid grades
- [ ] Cannot add duplicate student IDs
- [ ] Display functions show all information correctly
- [ ] Menu loop exits properly

**Submission**:
- Save as `week2_assignment.py`
- Include comprehensive comments
- Include test data in comments showing the system works
- Document any bonus features implemented

</details>

---

<details>
<summary><h1>Week 3: Introduction to OOP</h1></summary>

**Focus**: Classes, Objects, Methods, and Attributes

## Day 13 (Monday): Introduction to Classes and Objects

**Concepts** (45 min):

### What is Object-Oriented Programming?

**Procedural vs OOP Thinking**:
```python
# Procedural approach (what we've been doing)
student_name = "Alice"
student_age = 20
student_gpa = 3.5

def print_student_info(name, age, gpa):
    print(f"{name}, {age} years old, GPA: {gpa}")

print_student_info(student_name, student_age, student_gpa)

# OOP approach (what we're learning)
class Student:
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa
    
    def print_info(self):
        print(f"{self.name}, {self.age} years old, GPA: {self.gpa}")

student = Student("Alice", 20, 3.5)
student.print_info()
```

**Key OOP Concepts**:
- **Class**: Blueprint for creating objects (like a recipe)
- **Object**: Instance of a class (actual thing created from blueprint)
- **Attribute**: Data stored in an object (variables)
- **Method**: Function that belongs to a class

### Creating Your First Class

```python
# Define a class
class Dog:
    # Constructor method (initializer)
    def __init__(self, name, breed):
        # Instance attributes
        self.name = name
        self.breed = breed
    
    # Instance method
    def bark(self):
        return f"{self.name} says Woof!"
    
    # Another method
    def get_info(self):
        return f"{self.name} is a {self.breed}"

# Create objects (instances)
dog1 = Dog("Max", "Golden Retriever")
dog2 = Dog("Buddy", "Labrador")

# Access attributes
print(dog1.name)    # "Max"
print(dog2.breed)   # "Labrador"

# Call methods
print(dog1.bark())      # "Max says Woof!"
print(dog2.get_info())  # "Buddy is a Labrador"
```

### Understanding `self`

```python
class Counter:
    def __init__(self, start=0):
        self.count = start  # 'self' refers to the specific object
    
    def increment(self):
        self.count += 1  # Access this object's count
    
    def get_count(self):
        return self.count

# Each object has its own 'count'
counter1 = Counter()
counter2 = Counter(10)

counter1.increment()
counter1.increment()
print(counter1.get_count())  # 2

counter2.increment()
print(counter2.get_count())  # 11

# They're independent!
```

### Class vs Instance Attributes

```python
class Circle:
    # Class attribute (shared by all instances)
    pi = 3.14159
    
    def __init__(self, radius):
        # Instance attribute (unique to each object)
        self.radius = radius
    
    def calculate_area(self):
        # Access class attribute through 'self' or class name
        return Circle.pi * (self.radius ** 2)

circle1 = Circle(5)
circle2 = Circle(3)

print(circle1.pi)  # 3.14159 (same for all)
print(circle2.pi)  # 3.14159 (same for all)

print(circle1.radius)  # 5 (different for each)
print(circle2.radius)  # 3 (different for each)

print(circle1.calculate_area())  # 78.53975
```

**Practice** (45 min):

**Exercise 3.1**: Book Class
```python
# Create a Book class with:
# Attributes:
#   - title
#   - author
#   - pages
#   - current_page (starts at 0)
# 
# Methods:
#   - read(pages) - advance current_page
#   - get_progress() - return percentage read
#   - get_info() - return formatted string with all info
#   - is_finished() - return True if finished reading
#
# Create at least 3 book objects and demonstrate all methods
```

**Exercise 3.2**: Bank Account Class
```python
# Create a BankAccount class with:
# Attributes:
#   - account_number
#   - account_holder
#   - balance (starts at 0)
# 
# Methods:
#   - deposit(amount) - add to balance
#   - withdraw(amount) - subtract from balance (check for sufficient funds)
#   - get_balance() - return current balance
#   - print_statement() - print formatted account info
#
# Create 2 accounts and perform various transactions
```

**Exercise 3.3**: Rectangle Class
```python
# Create a Rectangle class with:
# Attributes:
#   - width
#   - height
# 
# Methods:
#   - calculate_area() - return width * height
#   - calculate_perimeter() - return 2 * (width + height)
#   - is_square() - return True if width == height
#   - scale(factor) - multiply both dimensions by factor
#   - get_info() - return formatted string with dimensions
#
# Test with various rectangles and demonstrate all methods
```

---

## Day 14: Methods and Behaviors

**Concepts** (45 min):

### Instance Methods in Depth

```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius
    
    # Method that returns a value
    def to_fahrenheit(self):
        return (self.celsius * 9/5) + 32
    
    # Method that returns a value
    def to_kelvin(self):
        return self.celsius + 273.15
    
    # Method that modifies the object
    def increase(self, amount):
        self.celsius += amount
    
    # Method that uses other methods
    def display_all(self):
        print(f"Celsius: {self.celsius}")
        print(f"Fahrenheit: {self.to_fahrenheit()}")
        print(f"Kelvin: {self.to_kelvin()}")

temp = Temperature(25)
temp.display_all()
temp.increase(5)
temp.display_all()
```

### Method Parameters and Return Values

```python
class Calculator:
    def __init__(self):
        self.history = []
    
    # Method with multiple parameters
    def add(self, a, b):
        result = a + b
        self.history.append(f"{a} + {b} = {result}")
        return result
    
    # Method with default parameter
    def power(self, base, exponent=2):
        result = base ** exponent
        self.history.append(f"{base}^{exponent} = {result}")
        return result
    
    # Method that returns complex data
    def get_history(self):
        return self.history.copy()  # Return a copy, not original
    
    def clear_history(self):
        self.history.clear()

calc = Calculator()
print(calc.add(5, 3))        # 8
print(calc.power(2, 3))      # 8
print(calc.power(5))         # 25 (default exponent)
print(calc.get_history())    # ['5 + 3 = 8', '2^3 = 8', '5^2 = 25']
```

### Methods Calling Other Methods

```python
class ShoppingCart:
    def __init__(self):
        self.items = []
        self.tax_rate = 0.08
    
    def add_item(self, name, price):
        self.items.append({"name": name, "price": price})
    
    def get_subtotal(self):
        return sum(item["price"] for item in self.items)
    
    def get_tax(self):
        # Method calling another method
        return self.get_subtotal() * self.tax_rate
    
    def get_total(self):
        # Method calling multiple other methods
        return self.get_subtotal() + self.get_tax()
    
    def print_receipt(self):
        print("=" * 30)
        print("RECEIPT")
        print("=" * 30)
        for item in self.items:
            print(f"{item['name']:<20} ${item['price']:>7.2f}")
        print("-" * 30)
        print(f"{'Subtotal':<20} ${self.get_subtotal():>7.2f}")
        print(f"{'Tax (8%)':<20} ${self.get_tax():>7.2f}")
        print("=" * 30)
        print(f"{'TOTAL':<20} ${self.get_total():>7.2f}")
        print("=" * 30)

cart = ShoppingCart()
cart.add_item("Apple", 1.99)
cart.add_item("Bread", 2.50)
cart.add_item("Milk", 3.49)
cart.print_receipt()
```

### Class Methods vs Instance Methods

```python
class Employee:
    # Class attribute
    company_name = "TechCorp"
    employee_count = 0
    
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.employee_count += 1
    
    # Instance method (works with specific employee)
    def give_raise(self, amount):
        self.salary += amount
    
    # Class method (works with the class itself)
    @classmethod
    def get_employee_count(cls):
        return cls.employee_count
    
    # Static method (doesn't need class or instance data)
    @staticmethod
    def is_valid_salary(salary):
        return salary > 0 and salary < 1000000

# Using instance method
emp1 = Employee("Alice", 50000)
emp1.give_raise(5000)

# Using class method
print(Employee.get_employee_count())  # 1

# Using static method
print(Employee.is_valid_salary(75000))  # True
```

**Practice** (45 min):

**Exercise 3.4**: Student Class with Methods
```python
# Create a comprehensive Student class:
# Attributes:
#   - name
#   - student_id
#   - grades (list)
#   - attendance (list of True/False)
# 
# Methods:
#   - add_grade(grade) - add grade to list
#   - get_average() - calculate average grade
#   - get_letter_grade() - return letter based on average
#   - mark_attendance(present) - add True/False to attendance
#   - get_attendance_rate() - return percentage of days present
#   - is_passing() - return True if average >= 60 and attendance >= 75%
#   - print_report() - formatted report with all info
#
# Create students, add data, and generate reports
```

**Exercise 3.5**: Playlist Manager
```python
# Create a Playlist class:
# Attributes:
#   - name
#   - songs (list of dictionaries: {"title": str, "artist": str, "duration": int})
# 
# Methods:
#   - add_song(title, artist, duration)
#   - remove_song(title)
#   - get_total_duration() - sum of all song durations
#   - get_song_count()
#   - find_song(title) - return song dict or None
#   - get_songs_by_artist(artist) - return list of songs
#   - shuffle() - randomize song order (import random)
#   - print_playlist() - formatted list of all songs
#
# Demonstrate with a playlist of at least 8 songs
```

**Exercise 3.6**: Password Manager
```python
# Create a PasswordEntry class:
# Attributes:
#   - service (e.g., "Gmail")
#   - username
#   - password
#   - created_date
#   - last_changed_date
# 
# Methods:
#   - get_info() - return formatted string
#   - change_password(new_password) - update password and last_changed_date
#   - check_password_strength() - return "Strong", "Medium", or "Weak"
#   - days_since_change() - return number of days since last change
#   - needs_update() - return True if password older than 90 days
#
# Create a PasswordVault class:
# Attributes:
#   - entries (list of PasswordEntry objects)
# 
# Methods:
#   - add_entry(service, username, password)
#   - find_entry(service)
#   - list_all_services()
#   - get_outdated_passwords() - return entries needing update
#   - print_vault() - show all entries
#
# Hint: Use datetime.date.today() for dates
```

---

## Day 15: Attributes and State Management

**Concepts** (45 min):

### Public vs Private Attributes

```python
class BankAccount:
    def __init__(self, account_number, balance):
        self.account_number = account_number  # Public attribute
        self.__balance = balance  # Private attribute (name mangling with __)
        self._transaction_history = []  # Protected (convention with _)
    
    # Getter method
    def get_balance(self):
        return self.__balance
    
    # Setter method with validation
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            self._transaction_history.append(f"Deposit: ${amount}")
            return True
        return False
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            self._transaction_history.append(f"Withdrawal: ${amount}")
            return True
        return False

account = BankAccount("12345", 1000)
print(account.account_number)     # OK - public
print(account.get_balance())      # OK - through method
# print(account.__balance)        # AttributeError - private!
# print(account._BankAccount__balance)  # Technically works (name mangling) but DON'T do this
```

### Property Decorators

```python
class Person:
    def __init__(self, name, age):
        self._name = name  # Protected attribute
        self._age = age
    
    # Getter using @property
    @property
    def name(self):
        return self._name
    
    # Setter using @name.setter
    @name.setter
    def name(self, value):
        if len(value) > 0:
            self._name = value
        else:
            raise ValueError("Name cannot be empty")
    
    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, value):
        if 0 <= value <= 120:
            self._age = value
        else:
            raise ValueError("Age must be between 0 and 120")
    
    # Read-only property (no setter)
    @property
    def is_adult(self):
        return self._age >= 18

# Use like regular attributes
person = Person("Alice", 25)
print(person.name)       # "Alice" (calls getter)
person.name = "Bob"      # Calls setter
print(person.name)       # "Bob"
print(person.is_adult)   # True

# person.is_adult = False  # Error! No setter defined
# person.name = ""         # ValueError! Validation failed
```

### Managing Object State

```python
class TrafficLight:
    def __init__(self):
        self._state = "red"  # Current state
        self._states = ["red", "yellow", "green"]
        self._duration = {"red": 30, "yellow": 5, "green": 25}
    
    @property
    def current_state(self):
        return self._state
    
    def change(self):
        """Transition to next state"""
        current_index = self._states.index(self._state)
        next_index = (current_index + 1) % len(self._states)
        self._state = self._states[next_index]
        return self._state
    
    def get_duration(self):
        """Get duration of current state"""
        return self._duration[self._state]
    
    def can_cross(self):
        """Check if pedestrians can cross"""
        return self._state == "red"  # Pedestrians cross when traffic is red

light = TrafficLight()
print(f"State: {light.current_state}, Duration: {light.get_duration()}s")
light.change()
print(f"State: {light.current_state}, Duration: {light.get_duration()}s")
```

### Dynamic Attributes

```python
class GameCharacter:
    def __init__(self, name):
        self.name = name
        self.stats = {
            "health": 100,
            "strength": 10,
            "defense": 5
        }
        self.inventory = []
    
    def add_item(self, item):
        self.inventory.append(item)
        # Items can modify stats
        if item.get("type") == "armor":
            self.stats["defense"] += item.get("defense_bonus", 0)
        elif item.get("type") == "weapon":
            self.stats["strength"] += item.get("strength_bonus", 0)
    
    def remove_item(self, item_name):
        for item in self.inventory:
            if item["name"] == item_name:
                # Remove stat bonuses
                if item.get("type") == "armor":
                    self.stats["defense"] -= item.get("defense_bonus", 0)
                elif item.get("type") == "weapon":
                    self.stats["strength"] -= item.get("strength_bonus", 0)
                self.inventory.remove(item)
                return True
        return False
    
    def take_damage(self, damage):
        actual_damage = max(0, damage - self.stats["defense"])
        self.stats["health"] -= actual_damage
        return self.stats["health"] > 0  # Return True if still alive
    
    def print_stats(self):
        print(f"=== {self.name} ===")
        for stat, value in self.stats.items():
            print(f"{stat.capitalize()}: {value}")
        print(f"Inventory: {[item['name'] for item in self.inventory]}")

# Example usage
player = GameCharacter("Hero")
player.add_item({"name": "Iron Sword", "type": "weapon", "strength_bonus": 5})
player.add_item({"name": "Leather Armor", "type": "armor", "defense_bonus": 3})
player.print_stats()

player.take_damage(10)
player.print_stats()
```

**Practice** (45 min):

**Exercise 3.7**: Smart Thermostat
```python
# Create a Thermostat class:
# Private attributes:
#   - __current_temp (float)
#   - __target_temp (float)
#   - __mode ("heat", "cool", "off")
# 
# Properties (with @property):
#   - current_temp (read-only)
#   - target_temp (getter and setter, validate 50-90°F)
#   - mode (getter and setter, validate modes)
# 
# Methods:
#   - adjust_temperature() - move current_temp toward target
#   - is_running() - True if current != target and mode != "off"
#   - get_status() - return formatted status string
#   - set_schedule(time, temp) - future feature, just store in dict
#
# Test: Create thermostat, change settings, simulate temperature changes
```

**Exercise 3.8**: Inventory Item
```python
# Create an InventoryItem class:
# Attributes:
#   - name
#   - __quantity (private)
#   - __price (private)
#   - reorder_level
# 
# Properties:
#   - quantity (getter and setter, validate >= 0)
#   - price (getter and setter, validate > 0)
#   - total_value (read-only, calculated as quantity * price)
# 
# Methods:
#   - add_stock(amount)
#   - remove_stock(amount) - return True if successful
#   - needs_reorder() - return True if quantity <= reorder_level
#   - apply_discount(percentage) - reduce price by percentage
#   - get_info() - formatted string
#
# Create several items and demonstrate state management
```

**Exercise 3.9**: User Account System
```python
# Create a UserAccount class:
# Private attributes:
#   - __username
#   - __password (store as hash in real system, but use plain text here)
#   - __email
#   - __login_attempts
#   - __is_locked
# 
# Properties:
#   - username (read-only)
#   - email (getter and setter with email validation)
#   - is_locked (read-only)
# 
# Methods:
#   - login(password) - check password, track failed attempts, lock after 3 fails
#   - change_password(old_password, new_password)
#   - reset_password(email) - unlock account and reset attempts
#   - get_account_status() - return dict with status info
#
# Test the security features (incorrect passwords, account locking)
```

---

## Day 16: The __str__ and __repr__ Methods

**Concepts** (40 min):

### String Representation Methods

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    # __str__ for human-readable output (used by print())
    def __str__(self):
        return f"Point({self.x}, {self.y})"
    
    # __repr__ for debugging/developer output (used by console)
    def __repr__(self):
        return f"Point(x={self.x}, y={self.y})"

point = Point(3, 4)
print(point)        # Uses __str__: Point(3, 4)
print(repr(point))  # Uses __repr__: Point(x=3, y=4)
print([point])      # Uses __repr__: [Point(x=3, y=4)]

# If only __repr__ is defined, it's used for both
# If only __str__ is defined, __repr__ uses default
```

### Best Practices for __str__ and __repr__

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
    
    def __str__(self):
        # For end users: concise and readable
        return f'"{self.title}" by {self.author}'
    
    def __repr__(self):
        # For developers: should be unambiguous and ideally reproduce the object
        return f'Book(title="{self.title}", author="{self.author}", year={self.year})'

book = Book("1984", "George Orwell", 1949)

# End user output
print(f"Currently reading: {book}")
# Currently reading: "1984" by George Orwell

# Developer/debug output
print(book)  # Uses __str__ in print()
# "1984" by George Orwell

books = [book]
print(books)  # Uses __repr__ in lists
# [Book(title="1984", author="George Orwell", year=1949)]
```

### Complex __str__ Examples

```python
class Receipt:
    def __init__(self):
        self.items = []
        self.tax_rate = 0.08
    
    def add_item(self, name, price):
        self.items.append({"name": name, "price": price})
    
    def __str__(self):
        lines = []
        lines.append("=" * 40)
        lines.append("RECEIPT".center(40))
        lines.append("=" * 40)
        
        for item in self.items:
            name = item["name"]
            price = item["price"]
            lines.append(f"{name:<30} ${price:>7.2f}")
        
        subtotal = sum(item["price"] for item in self.items)
        tax = subtotal * self.tax_rate
        total = subtotal + tax
        
        lines.append("-" * 40)
        lines.append(f"{'Subtotal':<30} ${subtotal:>7.2f}")
        lines.append(f"{'Tax (8%)':<30} ${tax:>7.2f}")
        lines.append("=" * 40)
        lines.append(f"{'TOTAL':<30} ${total:>7.2f}")
        lines.append("=" * 40)
        
        return "\n".join(lines)
    
    def __repr__(self):
        return f"Receipt(items={len(self.items)}, total=${sum(item['price'] for item in self.items):.2f})"

receipt = Receipt()
receipt.add_item("Coffee", 4.50)
receipt.add_item("Sandwich", 8.99)
receipt.add_item("Cookie", 2.50)

print(receipt)  # Shows full formatted receipt
print(repr(receipt))  # Receipt(items=3, total=$15.99)
```

### Using __repr__ for Debugging

```python
class Transaction:
    transaction_count = 0
    
    def __init__(self, from_account, to_account, amount):
        Transaction.transaction_count += 1
        self.id = Transaction.transaction_count
        self.from_account = from_account
        self.to_account = to_account
        self.amount = amount
        self.timestamp = "2024-01-15 10:30:00"  # Simplified
    
    def __repr__(self):
        # Detailed representation for debugging
        return (f"Transaction(id={self.id}, "
                f"from={self.from_account}, "
                f"to={self.to_account}, "
                f"amount={self.amount}, "
                f"timestamp='{self.timestamp}')")
    
    def __str__(self):
        # User-friendly representation
        return f"Transaction #{self.id}: ${self.amount:.2f} from {self.from_account} to {self.to_account}"

t1 = Transaction("ACC001", "ACC002", 150.00)
t2 = Transaction("ACC003", "ACC001", 75.50)

print(t1)  # Transaction #1: $150.00 from ACC001 to ACC002
print(repr(t1))  # Transaction(id=1, from=ACC001, to=ACC002, amount=150.0, timestamp='2024-01-15 10:30:00')

transactions = [t1, t2]
print(transactions)  # Shows __repr__ for each
```

**Practice** (50 min):

**Exercise 3.10**: Product Class
```python
# Create a Product class with excellent string representations:
# Attributes:
#   - name
#   - price
#   - category
#   - stock_quantity
#   - sku (unique identifier)
# 
# Implement:
#   - __str__() - User-friendly format like:
#     "iPhone 14 (Electronics) - $999.99 [42 in stock]"
#   
#   - __repr__() - Developer format that could recreate object:
#     "Product(name='iPhone 14', price=999.99, category='Electronics', stock_quantity=42, sku='ELEC-001')"
#
# Test: Create products, print them, put them in lists, verify both methods work
```

**Exercise 3.11**: Meeting Class
```python
# Create a Meeting class:
# Attributes:
#   - title
#   - date (string like "2024-01-15")
#   - time (string like "14:30")
#   - attendees (list of names)
#   - location
# 
# Implement:
#   - __str__() - Calendar-style format:
#     """
#     Meeting: Sprint Planning
#     Date: 2024-01-15 at 14:30
#     Location: Conference Room A
#     Attendees: Alice, Bob, Charlie (3 people)
#     """
#   
#   - __repr__() - Compact debug format:
#     "Meeting('Sprint Planning', '2024-01-15', '14:30', 3 attendees, 'Conference Room A')"
#
# Create multiple meetings and test both representations
```

**Exercise 3.12**: Game Leaderboard Entry
```python
# Create a LeaderboardEntry class:
# Attributes:
#   - player_name
#   - score
#   - level_reached
#   - time_played (minutes)
#   - achievement_count
# 
# Implement:
#   - __str__() - Leaderboard display format:
#     "1. ALICE - 25,430 points (Level 42, 127 mins)"
#     Should include rank (passed as method parameter or attribute)
#   
#   - __repr__() - Full debug info
#
# Create a Leaderboard class:
# Attributes:
#   - entries (list of LeaderboardEntry objects)
# 
# Methods:
#   - add_entry(entry)
#   - sort_by_score()
#   - __str__() - Shows complete leaderboard with ranks
#   - __repr__() - Shows "Leaderboard(X entries)"
#
# Create leaderboard with 5+ entries and display it
```

---

## Day 17: Object Relationships and Composition

**Concepts** (45 min):

### Objects Containing Other Objects

```python
class Address:
    def __init__(self, street, city, state, zipcode):
        self.street = street
        self.city = city
        self.state = state
        self.zipcode = zipcode
    
    def __str__(self):
        return f"{self.street}, {self.city}, {self.state} {self.zipcode}"

class Person:
    def __init__(self, name, address):
        self.name = name
        self.address = address  # Person HAS-A Address
    
    def __str__(self):
        return f"{self.name}\n{self.address}"

# Create composition
address = Address("123 Main St", "Springfield", "IL", "62701")
person = Person("John Doe", address)
print(person)
# John Doe
# 123 Main St, Springfield, IL 62701

# Access nested object attributes
print(person.address.city)  # Springfield
```

### Lists of Objects

```python
class Course:
    def __init__(self, code, name, credits):
        self.code = code
        self.name = name
        self.credits = credits
    
    def __repr__(self):
        return f"Course('{self.code}', '{self.name}', {self.credits})"

class Student:
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.courses = []  # List of Course objects
    
    def enroll(self, course):
        self.courses.append(course)
    
    def drop(self, course_code):
        self.courses = [c for c in self.courses if c.code != course_code]
    
    def get_total_credits(self):
        return sum(course.credits for course in self.courses)
    
    def print_schedule(self):
        print(f"Schedule for {self.name} ({self.student_id})")
        print(f"Total Credits: {self.get_total_credits()}")
        for course in self.courses:
            print(f"  {course.code}: {course.name} ({course.credits} credits)")

# Create objects and relationships
student = Student("Alice Johnson", "S12345")
student.enroll(Course("CS101", "Intro to Programming", 3))
student.enroll(Course("MATH201", "Calculus I", 4))
student.enroll(Course("ENG101", "English Composition", 3))
student.print_schedule()
```

### Complex Composition

```python
class MenuItem:
    def __init__(self, name, price, category):
        self.name = name
        self.price = price
        self.category = category
    
    def __repr__(self):
        return f"{self.name} (${self.price:.2f})"

class Order:
    order_number = 1000
    
    def __init__(self):
        Order.order_number += 1
        self.number = Order.order_number
        self.items = []  # List of MenuItem objects
    
    def add_item(self, item, quantity=1):
        for _ in range(quantity):
            self.items.append(item)
    
    def get_subtotal(self):
        return sum(item.price for item in self.items)
    
    def get_tax(self, tax_rate=0.08):
        return self.get_subtotal() * tax_rate
    
    def get_total(self):
        return self.get_subtotal() + self.get_tax()
    
    def __str__(self):
        lines = [f"Order #{self.number}"]
        lines.append("-" * 40)
        
        # Group items by name
        item_counts = {}
        for item in self.items:
            if item.name in item_counts:
                item_counts[item.name]["count"] += 1
            else:
                item_counts[item.name] = {"item": item, "count": 1}
        
        # Display grouped items
        for name, data in item_counts.items():
            item = data["item"]
            count = data["count"]
            total = item.price * count
            lines.append(f"{count}x {item.name:<20} ${total:>7.2f}")
        
        lines.append("-" * 40)
        lines.append(f"{'Subtotal':<25} ${self.get_subtotal():>7.2f}")
        lines.append(f"{'Tax':<25} ${self.get_tax():>7.2f}")
        lines.append("=" * 40)
        lines.append(f"{'TOTAL':<25} ${self.get_total():>7.2f}")
        
        return "\n".join(lines)

class Restaurant:
    def __init__(self, name):
        self.name = name
        self.menu = []
        self.orders = []
    
    def add_menu_item(self, item):
        self.menu.append(item)
    
    def find_menu_item(self, name):
        for item in self.menu:
            if item.name.lower() == name.lower():
                return item
        return None
    
    def create_order(self):
        order = Order()
        self.orders.append(order)
        return order
    
    def print_menu(self):
        print(f"\n{'=' * 50}")
        print(f"{self.name} MENU".center(50))
        print(f"{'=' * 50}")
        
        categories = {}
        for item in self.menu:
            if item.category not in categories:
                categories[item.category] = []
            categories[item.category].append(item)
        
        for category, items in categories.items():
            print(f"\n{category.upper()}")
            print("-" * 50)
            for item in items:
                print(f"{item.name:<35} ${item.price:>7.2f}")

# Usage example
restaurant = Restaurant("Joe's Diner")
restaurant.add_menu_item(MenuItem("Burger", 8.99, "Mains"))
restaurant.add_menu_item(MenuItem("Fries", 3.49, "Sides"))
restaurant.add_menu_item(MenuItem("Soda", 1.99, "Drinks"))
restaurant.add_menu_item(MenuItem("Salad", 6.99, "Mains"))

restaurant.print_menu()

order = restaurant.create_order()
order.add_item(restaurant.find_menu_item("Burger"), 2)
order.add_item(restaurant.find_menu_item("Fries"), 2)
order.add_item(restaurant.find_menu_item("Soda"), 1)
print("\n" + str(order))
```

**Practice** (45 min):

**Exercise 3.13**: Library System
```python
# Create a complete library management system with these classes:
#
# Book class:
#   - title, author, isbn, is_available
#   - checkout() - mark as unavailable
#   - return_book() - mark as available
#   - __str__() for display
#
# Member class:
#   - name, member_id
#   - checked_out_books (list of Book objects)
#   - checkout_book(book) - add to list if available
#   - return_book(book) - remove from list
#   - get_checked_out_count()
#   - __str__() showing member and books
#
# Library class:
#   - name
#   - books (list of all Book objects)
#   - members (list of all Member objects)
#   - add_book(book)
#   - register_member(member)
#   - find_book(title) - return Book object or None
#   - find_member(member_id)
#   - print_catalog()
#   - print_members()
#
# Demonstrate:
#   - Add 5+ books
#   - Register 2+ members
#   - Have members check out and return books
#   - Print catalogs showing availability
```

**Exercise 3.14**: Hospital Management System
```python
# Create a hospital system with:
#
# Patient class:
#   - name, patient_id, age
#   - medical_history (list of strings)
#   - current_medications (list of strings)
#   - add_to_history(note)
#   - add_medication(medication)
#   - __str__() - formatted patient info
#
# Appointment class:
#   - patient (Patient object)
#   - doctor_name
#   - date, time
#   - reason
#   - notes
#   - __str__() - formatted appointment info
#
# Hospital class:
#   - name
#   - patients (list of Patient objects)
#   - appointments (list of Appointment objects)
#   - register_patient(patient)
#   - schedule_appointment(patient_id, doctor, date, time, reason)
#   - find_patient(patient_id)
#   - get_appointments_for_date(date)
#   - print_schedule(date)
#
# Create scenario with multiple patients and appointments
```

**Exercise 3.15**: E-commerce Shopping System
```python
# Build a shopping system with:
#
# Product class:
#   - name, price, category, stock
#   - reduce_stock(quantity)
#   - add_stock(quantity)
#   - is_in_stock()
#
# CartItem class:
#   - product (Product object)
#   - quantity
#   - get_subtotal()
#
# ShoppingCart class:
#   - items (list of CartItem objects)
#   - add_item(product, quantity)
#   - remove_item(product_name)
#   - update_quantity(product_name, new_quantity)
#   - get_total()
#   - checkout() - reduce stock for all products
#   - __str__() - formatted cart display
#
# Store class:
#   - name
#   - products (list of Product objects)
#   - completed_orders (list of ShoppingCart objects)
#   - add_product(product)
#   - find_product(name)
#   - get_products_by_category(category)
#   - process_order(cart)
#   - print_inventory()
#
# Create a complete shopping scenario with multiple products and orders
```

---

## Day 18: Weekly Assignment - Week 3

**Time**: 1.4 hours  
**Due**: End of Day 18  
**Grading**: See rubric at end

### Assignment 3: Security Incident Management System (Foundation)

You will begin building a **Security Incident Management System** that you'll continue to enhance throughout the remaining weeks. This week focuses on creating the core classes with proper OOP principles.

**System Overview**:
This system will eventually manage security incidents, users, and assets in a Security Operations Center (SOC) environment.

**Requirements for Week 3**:

### Part 1: SecurityIncident Class (30 points)

Create a `SecurityIncident` class that represents a security event:

**Private Attributes**:
- `__incident_id` (auto-generated, unique)
- `__title`
- `__description`
- `__severity` ("Low", "Medium", "High", "Critical")
- `__status` ("Open", "In Progress", "Resolved", "Closed")
- `__reported_date`
- `__assigned_to` (analyst name, can be None)
- `__resolution_notes` (string, starts empty)

**Properties** (use @property):
- `incident_id` (read-only)
- `title` (read-only after creation)
- `severity` (getter and setter with validation)
- `status` (getter and setter with validation)
- `assigned_to` (getter and setter)

**Methods**:
- `__init__(title, description, severity)`
- `assign_to(analyst_name)` - assign incident to analyst
- `update_status(new_status)` - change status
- `add_resolution_note(note)` - append to resolution notes
- `escalate()` - increase severity by one level
- `get_details()` - return formatted string with all info
- `__str__()` - user-friendly summary
- `__repr__()` - detailed debug representation

**Example Usage**:
```python
incident = SecurityIncident(
    "Suspicious Login Attempt",
    "Multiple failed login attempts from IP 192.168.1.100",
    "Medium"
)
incident.assign_to("Alice")
incident.update_status("In Progress")
incident.add_resolution_note("Investigated IP, appears to be brute force attack")
print(incident.get_details())
```

### Part 2: SecurityAnalyst Class (25 points)

Create a `SecurityAnalyst` class representing SOC analysts:

**Attributes**:
- `name`
- `analyst_id`
- `assigned_incidents` (list of SecurityIncident objects)
- `expertise_areas` (list of strings like "Malware", "Network", "Cloud")

**Methods**:
- `__init__(name, analyst_id, expertise_areas)`
- `assign_incident(incident)` - add incident to their workload
- `resolve_incident(incident_id, resolution_note)` - mark incident as resolved
- `get_workload_count()` - return number of open/in-progress incidents
- `get_incidents_by_severity(severity)` - return filtered list
- `print_workload()` - formatted display of all assigned incidents
- `__str__()` - analyst summary
- `__repr__()` - detailed representation

### Part 3: Asset Class (20 points)

Create an `Asset` class representing IT assets being monitored:

**Attributes**:
- `asset_id`
- `asset_type` ("Server", "Workstation", "Network Device", "Application")
- `hostname`
- `ip_address`
- `operating_system`
- `is_critical` (boolean)
- `last_scan_date`

**Methods**:
- `__init__(asset_id, asset_type, hostname, ip_address, os, is_critical)`
- `update_scan_date(date)` - update last scan
- `mark_as_critical()` / `mark_as_non_critical()`
- `get_info()` - formatted asset information
- `__str__()` - concise asset summary
- `__repr__()` - detailed representation

### Part 4: SecurityOperationsCenter Class (25 points)

Create a `SecurityOperationsCenter` class that manages everything:

**Attributes**:
- `name` (SOC name)
- `incidents` (list of SecurityIncident objects)
- `analysts` (list of SecurityAnalyst objects)
- `assets` (list of Asset objects)

**Methods**:
- `__init__(name)`
- `add_analyst(analyst)`
- `add_asset(asset)`
- `report_incident(title, description, severity, affected_asset_id)` - creates incident
- `assign_incident(incident_id, analyst_id)` - assign to analyst
- `get_open_incidents()` - return list of unresolved incidents
- `get_critical_incidents()` - return list of critical severity incidents
- `get_incident_by_id(incident_id)` - find specific incident
- `get_analyst_by_id(analyst_id)` - find specific analyst
- `print_dashboard()` - formatted SOC dashboard showing:
  - Total incidents by status
  - Critical incidents needing attention
  - Analyst workload summary
  - Critical assets
- `__str__()` - SOC summary

### Testing Requirements:

Your program should include a `main()` function that demonstrates:

1. Creating a SOC with a name
2. Adding 3+ analysts with different expertise
3. Adding 5+ assets (mix of critical and non-critical)
4. Reporting 8+ incidents with varying severities
5. Assigning incidents to appropriate analysts
6. Updating incident statuses
7. Resolving some incidents with notes
8. Escalating at least one incident
9. Printing the SOC dashboard
10. Printing individual analyst workloads
11. Demonstrating all properties and validation

**Example Dashboard Output**:
```
========================================
CYBER DEFENSE SOC - DASHBOARD
========================================
Generated: 2024-01-15 14:30:00

INCIDENT SUMMARY
----------------
Total Incidents: 8
  Open: 2
  In Progress: 4
  Resolved: 1
  Closed: 1

CRITICAL INCIDENTS REQUIRING ATTENTION
---------------------------------------
1. [CRITICAL] Ransomware Detected - OPEN
   Asset: SRV-WEB-01
   Reported: 2024-01-15 08:15:00
   
2. [CRITICAL] Data Exfiltration Attempt - IN PROGRESS
   Asset: SRV-DB-01
   Assigned to: Alice
   Reported: 2024-01-15 09:30:00

ANALYST WORKLOAD
----------------
Alice (ID: A001) - Network, Malware
  Active Incidents: 3
  Expertise: Network, Malware
  
Bob (ID: A002) - Cloud, Forensics
  Active Incidents: 2
  Expertise: Cloud, Forensics

CRITICAL ASSETS
---------------
- SRV-DB-01 (Server) - Database Server
- SRV-WEB-01 (Server) - Web Server
- FW-CORE-01 (Network Device) - Core Firewall

========================================
```

---

### Grading Rubric - Week 3 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **SecurityIncident Class** | 30 | |
| Attributes & properties | 10 | Correct private attributes, working properties |
| Methods | 10 | All required methods implemented correctly |
| String representations | 5 | Both __str__ and __repr__ properly formatted |
| Validation | 5 | Severity and status validated properly |
| **SecurityAnalyst Class** | 25 | |
| Attributes | 5 | Correct structure with incident list |
| Methods | 12 | All methods work correctly |
| Incident management | 5 | Properly assigns/resolves incidents |
| String representations | 3 | __str__ and __repr__ implemented |
| **Asset Class** | 20 | |
| Attributes | 8 | All required attributes present |
| Methods | 8 | Update and query methods work |
| String representations | 4 | __str__ and __repr__ implemented |
| **SecurityOperationsCenter Class** | 25 | |
| Data management | 10 | Properly stores and manages all objects |
| Query methods | 8 | Find, filter, get methods work correctly |
| Dashboard | 7 | Formatted, informative dashboard output |
| **Bonus** | +20 | See bonus challenges below |

**Bonus Challenges** (+5 points each):

1. **Incident Timeline**: Add methods to track status change history with timestamps
2. **Auto-Assignment**: Implement `auto_assign_incident()` that assigns based on analyst workload and expertise
3. **Metrics**: Add `generate_metrics()` method that calculates:
   - Average time to resolve incidents
   - Incidents per analyst
   - Most common incident types
4. **Export**: Add method to export incidents to formatted text file

**Code Quality Expectations**:
- Proper use of private attributes (__)
- Properties used appropriately with validation
- Clear, descriptive variable/method names
- Comprehensive docstrings
- Proper encapsulation (no direct attribute access from outside)
- Well-formatted string representations

**Submission**:
- Save as `week3_assignment.py`
- Include your name, date, and assignment number in header comment
- Include detailed comments explaining your OOP design choices
- Test thoroughly with the required demonstration scenarios

</details>

---

<details>
<summary><h1>Week 4: OOP Core Concepts</h1></summary>

**Focus**: Encapsulation, Class Methods, Static Methods, and Special Methods

## Day 19 (Monday): Encapsulation Deep Dive

**Concepts** (45 min):

### Understanding Encapsulation

Encapsulation is about bundling data and methods that work on that data within a single unit (class) and restricting direct access to some of the object's components.

```python
# Bad: No encapsulation
class BadBankAccount:
    def __init__(self, balance):
        self.balance = balance  # Anyone can modify directly!

account = BadBankAccount(1000)
account.balance = 999999  # Oops! Direct modification
account.balance = -500    # Negative balance! No validation

# Good: Proper encapsulation
class GoodBankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute
    
    def get_balance(self):
        return self.__balance
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False

account = GoodBankAccount(1000)
# account.__balance = 999999  # AttributeError!
account.deposit(500)  # Controlled access with validation
```

### Property Decorators for Encapsulation

```python
class Temperature:
    def __init__(self):
        self.__celsius = 0
    
    @property
    def celsius(self):
        """Get temperature in Celsius"""
        return self.__celsius
    
    @celsius.setter
    def celsius(self, value):
        """Set temperature in Celsius with validation"""
        if value < -273.15:
            raise ValueError("Temperature cannot be below absolute zero")
        self.__celsius = value
    
    @property
    def fahrenheit(self):
        """Get temperature in Fahrenheit (calculated property)"""
        return (self.__celsius * 9/5) + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        """Set temperature using Fahrenheit"""
        if value < -459.67:
            raise ValueError("Temperature cannot be below absolute zero")
        self.__celsius = (value - 32) * 5/9
    
    @property
    def kelvin(self):
        """Get temperature in Kelvin (read-only calculated property)"""
        return self.__celsius + 273.15

# Usage - looks like attribute access but uses methods
temp = Temperature()
temp.celsius = 25
print(temp.fahrenheit)  # 77.0
print(temp.kelvin)      # 298.15

temp.fahrenheit = 98.6
print(temp.celsius)     # 37.0

# temp.kelvin = 300  # AttributeError - kelvin is read-only
```

### Encapsulation with Data Validation

```python
class CreditCard:
    def __init__(self, card_number, cvv, expiry_month, expiry_year):
        self.card_number = card_number  # Uses setter
        self.cvv = cvv                  # Uses setter
        self.expiry_month = expiry_month
        self.expiry_year = expiry_year
    
    @property
    def card_number(self):
        # Only show last 4 digits
        return "**** **** **** " + self.__card_number[-4:]
    
    @card_number.setter
    def card_number(self, value):
        # Remove spaces and validate
        cleaned = value.replace(" ", "").replace("-", "")
        if not cleaned.isdigit():
            raise ValueError("Card number must contain only digits")
        if len(cleaned) != 16:
            raise ValueError("Card number must be 16 digits")
        self.__card_number = cleaned
    
    @property
    def cvv(self):
        return "***"  # Never show CVV
    
    @cvv.setter
    def cvv(self, value):
        if not str(value).isdigit():
            raise ValueError("CVV must be numeric")
        if len(str(value)) not in [3, 4]:
            raise ValueError("CVV must be 3 or 4 digits")
        self.__cvv = value
    
    @property
    def expiry_month(self):
        return self.__expiry_month
    
    @expiry_month.setter
    def expiry_month(self, value):
        if not 1 <= value <= 12:
            raise ValueError("Month must be 1-12")
        self.__expiry_month = value
    
    @property
    def expiry_year(self):
        return self.__expiry_year
    
    @expiry_year.setter
    def expiry_year(self, value):
        if value < 2024:
            raise ValueError("Card has expired")
        self.__expiry_year = value
    
    def is_valid(self):
        """Check if card is not expired"""
        # Simplified - in real app, compare with current date
        return self.expiry_year >= 2024
    
    def __str__(self):
        return f"Card: {self.card_number}, Exp: {self.expiry_month:02d}/{self.expiry_year}"

# Usage
card = CreditCard("1234-5678-9012-3456", "123", 12, 2025)
print(card)  # Card: **** **** **** 3456, Exp: 12/2025
print(card.cvv)  # *** (hidden)

# Try invalid data
try:
    bad_card = CreditCard("123", "999", 13, 2020)  # Will raise errors
except ValueError as e:
    print(f"Error: {e}")
```

**Practice** (45 min):

**Exercise 4.1**: Secure User Account
```python
# Create a UserAccount class with full encapsulation:
# 
# Private attributes:
#   - __username (once set, cannot be changed)
#   - __email
#   - __password_hash (store as hash, not plain text - simulate with reversed string)
#   - __failed_login_attempts
#   - __is_locked
#   - __creation_date
# 
# Properties:
#   - username (read-only)
#   - email (validate format: must contain @ and .)
#   - is_locked (read-only)
#   - account_age_days (read-only, calculated from creation_date)
# 
# Methods:
#   - login(password) - check password, track failed attempts, lock after 5 fails
#   - change_password(old_password, new_password) - validate both
#   - unlock_account(admin_password) - unlock with special password
#   - __str__() - safe representation (no password info)
#
# Test all validation and security features
```

**Exercise 4.2**: Validated Product Inventory
```python
# Create a Product class with strict validation:
# 
# Private attributes:
#   - __sku (Stock Keeping Unit - once set, cannot change)
#   - __name
#   - __price
#   - __quantity
#   - __min_quantity (reorder threshold)
# 
# Properties:
#   - sku (read-only)
#   - name (getter/setter, cannot be empty)
#   - price (getter/setter, must be > 0)
#   - quantity (getter/setter, must be >= 0)
#   - min_quantity (getter/setter, must be >= 0)
#   - needs_reorder (read-only, True if quantity <= min_quantity)
#   - stock_value (read-only, quantity * price)
# 
# Methods:
#   - add_stock(amount) - increase quantity
#   - remove_stock(amount) - decrease quantity (validate sufficient stock)
#   - update_price(new_price) - change price (validate > 0)
#   - __str__() - formatted product info
#
# Create inventory system that demonstrates proper encapsulation
```

**Exercise 4.3**: Date Range Validator
```python
# Create a DateRange class with validation:
# 
# Private attributes:
#   - __start_date (string "YYYY-MM-DD")
#   - __end_date (string "YYYY-MM-DD")
# 
# Properties:
#   - start_date (getter/setter, validate format and that start < end)
#   - end_date (getter/setter, validate format and that end > start)
#   - duration_days (read-only, calculated)
# 
# Methods:
#   - contains_date(date) - check if date falls in range
#   - overlaps_with(other_date_range) - check for overlap
#   - extend(days) - add days to end_date
#   - __str__() - formatted range display
#
# Test with various date scenarios and edge cases
```

---

## Day 20: Class Methods and Static Methods

**Concepts** (45 min):

### Class Methods (@classmethod)

Class methods work with the class itself, not specific instances. They receive the class as the first argument (cls) instead of the instance (self).

```python
class Employee:
    # Class attributes
    company_name = "TechCorp"
    employee_count = 0
    min_salary = 30000
    
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.employee_count += 1
    
    # Instance method (works with specific employee)
    def give_raise(self, amount):
        self.salary += amount
    
    # Class method (works with the class)
    @classmethod
    def get_employee_count(cls):
        return cls.employee_count
    
    @classmethod
    def set_min_salary(cls, new_min):
        cls.min_salary = new_min
    
    # Class method as alternative constructor
    @classmethod
    def from_string(cls, emp_string):
        """Create employee from string: 'Name,Salary'"""
        name, salary = emp_string.split(',')
        return cls(name, int(salary))
    
    def __str__(self):
        return f"{self.name}: ${self.salary:,}"

# Using class methods
emp1 = Employee("Alice", 75000)
emp2 = Employee("Bob", 65000)

print(Employee.get_employee_count())  # 2 (called on class)
print(emp1.get_employee_count())      # 2 (can also call on instance)

# Alternative constructor
emp3 = Employee.from_string("Charlie,80000")
print(emp3)  # Charlie: $80,000

# Modify class attribute
Employee.set_min_salary(35000)
print(Employee.min_salary)  # 35000
```

### Static Methods (@staticmethod)

Static methods don't receive self or cls. They're utility functions that logically belong to the class but don't need access to class or instance data.

```python
class MathOperations:
    @staticmethod
    def add(a, b):
        return a + b
    
    @staticmethod
    def is_even(number):
        return number % 2 == 0
    
    @staticmethod
    def celsius_to_fahrenheit(celsius):
        return (celsius * 9/5) + 32
    
    @staticmethod
    def fahrenheit_to_celsius(fahrenheit):
        return (fahrenheit - 32) * 5/9

# Call without creating instance
print(MathOperations.add(5, 3))                    # 8
print(MathOperations.is_even(10))                  # True
print(MathOperations.celsius_to_fahrenheit(25))    # 77.0

# Can still call on instance, but rarely done
math = MathOperations()
print(math.add(2, 2))  # 4
```

### Real-World Example: User Management

```python
from datetime import datetime

class User:
    # Class attributes
    all_users = []
    user_count = 0
    
    def __init__(self, username, email, role="user"):
        self.username = username
        self.email = email
        self.role = role
        self.created_at = datetime.now()
        User.user_count += 1
        User.all_users.append(self)
    
    # Instance method
    def promote_to_admin(self):
        self.role = "admin"
    
    # Class methods for managing all users
    @classmethod
    def get_user_count(cls):
        return cls.user_count
    
    @classmethod
    def find_by_username(cls, username):
        for user in cls.all_users:
            if user.username == username:
                return user
        return None
    
    @classmethod
    def get_admins(cls):
        return [user for user in cls.all_users if user.role == "admin"]
    
    @classmethod
    def clear_all_users(cls):
        cls.all_users.clear()
        cls.user_count = 0
    
    # Alternative constructors using class methods
    @classmethod
    def create_admin(cls, username, email):
        return cls(username, email, role="admin")
    
    @classmethod
    def from_csv_line(cls, csv_line):
        """Create user from CSV: username,email,role"""
        username, email, role = csv_line.split(',')
        return cls(username, email, role)
    
    # Static methods for validation
    @staticmethod
    def is_valid_email(email):
        return '@' in email and '.' in email.split('@')[1]
    
    @staticmethod
    def is_strong_password(password):
        if len(password) < 8:
            return False
        has_upper = any(c.isupper() for c in password)
        has_lower = any(c.islower() for c in password)
        has_digit = any(c.isdigit() for c in password)
        return has_upper and has_lower and has_digit
    
    def __str__(self):
        return f"{self.username} ({self.role}) - {self.email}"
    
    def __repr__(self):
        return f"User('{self.username}', '{self.email}', '{self.role}')"

# Usage examples
# Validate before creating
email = "alice@example.com"
if User.is_valid_email(email):
    user1 = User("alice", email)

# Alternative constructors
admin = User.create_admin("bob", "bob@example.com")
user2 = User.from_csv_line("charlie,charlie@example.com,user")

# Class-level queries
print(f"Total users: {User.get_user_count()}")  # 3
print(f"Admins: {User.get_admins()}")  # [bob]

# Find specific user
found = User.find_by_username("alice")
if found:
    print(f"Found: {found}")

# Static method validation
password = "MyPass123"
if User.is_strong_password(password):
    print("Password is strong")
```

### When to Use Each Type

```python
class BankAccount:
    # Class attribute
    interest_rate = 0.02
    total_accounts = 0
    
    def __init__(self, account_number, balance):
        self.account_number = account_number
        self.__balance = balance
        BankAccount.total_accounts += 1
    
    # INSTANCE METHOD - operates on specific account
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False
    
    # CLASS METHOD - operates on class data
    @classmethod
    def set_interest_rate(cls, rate):
        cls.interest_rate = rate
    
    @classmethod
    def get_total_accounts(cls):
        return cls.total_accounts
    
    # STATIC METHOD - utility function (doesn't need class or instance data)
    @staticmethod
    def is_valid_account_number(number):
        return len(str(number)) == 10 and str(number).isdigit()
    
    @staticmethod
    def calculate_interest(balance, rate):
        return balance * rate

# Instance method - needs specific account
account = BankAccount("1234567890", 1000)
account.deposit(500)  # Works on THIS account

# Class method - affects all accounts
BankAccount.set_interest_rate(0.03)

# Static method - pure utility
if BankAccount.is_valid_account_number("1234567890"):
    print("Valid account number")
```

**Practice** (45 min):

**Exercise 4.4**: Product Factory with Class Methods
```python
# Create a Product class with factory methods:
# 
# Class attributes:
#   - all_products (list)
#   - product_count
#   - default_tax_rate
# 
# Instance attributes:
#   - product_id (auto-generated)
#   - name, price, category
# 
# Instance methods:
#   - apply_discount(percentage)
#   - get_price_with_tax()
# 
# Class methods:
#   - create_electronics(name, price) - creates with category="Electronics"
#   - create_clothing(name, price) - creates with category="Clothing"
#   - from_dict(product_dict) - alternative constructor
#   - find_by_id(product_id)
#   - get_products_by_category(category)
#   - get_average_price()
#   - set_tax_rate(rate)
# 
# Static methods:
#   - is_valid_price(price) - checks price > 0
#   - calculate_bulk_discount(price, quantity) - 10% off if quantity >= 10
#   - format_currency(amount) - returns "$X.XX"
# 
# Demonstrate all three method types
```

**Exercise 4.5**: Date Utilities Class
```python
# Create a DateUtils class with static methods:
# 
# Static methods:
#   - is_leap_year(year)
#   - days_in_month(month, year)
#   - is_valid_date(year, month, day)
#   - day_of_week(year, month, day) - return "Monday", "Tuesday", etc.
#   - days_between(date1, date2) - calculate difference
#   - add_days(date, days) - return new date
#   - format_date(year, month, day, format) - format="US" or "EU"
# 
# Don't use datetime library - implement algorithms yourself
# This is purely utility functions, so all static methods
# 
# Test with various dates and operations
```

**Exercise 4.6**: Student Registry System
```python
# Create a Student class with all three method types:
# 
# Class attributes:
#   - all_students (list)
#   - current_year (e.g., 2024)
#   - min_gpa (e.g., 2.0)
# 
# Instance attributes:
#   - student_id, name, year, gpa, major
# 
# Instance methods:
#   - update_gpa(new_gpa)
#   - advance_year() - move to next year
#   - is_eligible_for_honors() - gpa >= 3.5
# 
# Class methods:
#   - create_freshman(name, gpa, major)
#   - from_csv(csv_line) - parse "id,name,year,gpa,major"
#   - get_student_by_id(student_id)
#   - get_students_by_major(major)
#   - get_honor_students()
#   - promote_all_students() - advance everyone's year
#   - set_min_gpa(gpa)
# 
# Static methods:
#   - is_valid_gpa(gpa) - 0.0 to 4.0
#   - is_valid_year(year) - 1 (Freshman) to 4 (Senior)
#   - calculate_credits_needed(year) - returns typical credits for year
#   - gpa_to_letter(gpa) - convert numeric to letter grade
# 
# Create a complete student management demonstration
```

---

## Day 21: Special Methods (Magic Methods) Part I

**Concepts** (45 min):

### What Are Special Methods?

Special methods (also called magic methods or dunder methods) are methods with double underscores before and after their names. They allow your classes to implement built-in Python behaviors.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    # String representation
    def __str__(self):
        return f"Point({self.x}, {self.y})"
    
    def __repr__(self):
        return f"Point(x={self.x}, y={self.y})"
    
    # Comparison operators
    def __eq__(self, other):
        """Equal to (==)"""
        if not isinstance(other, Point):
            return False
        return self.x == other.x and self.y == other.y
    
    def __lt__(self, other):
        """Less than (<)"""
        # Compare by distance from origin
        return (self.x**2 + self.y**2) < (other.x**2 + other.y**2)
    
    def __le__(self, other):
        """Less than or equal (<=)"""
        return self == other or self < other
    
    # Arithmetic operators
    def __add__(self, other):
        """Addition (+)"""
        return Point(self.x + other.x, self.y + other.y)
    
    def __sub__(self, other):
        """Subtraction (-)"""
        return Point(self.x - other.x, self.y - other.y)
    
    def __mul__(self, scalar):
        """Multiplication (*)"""
        return Point(self.x * scalar, self.y * scalar)

# Usage
p1 = Point(1, 2)
p2 = Point(3, 4)

print(p1)           # Point(1, 2) - uses __str__
print(repr(p1))     # Point(x=1, y=2) - uses __repr__

print(p1 == p2)     # False - uses __eq__
print(p1 < p2)      # True - uses __lt__

p3 = p1 + p2        # Point(4, 6) - uses __add__
p4 = p2 - p1        # Point(2, 2) - uses __sub__
p5 = p1 * 3         # Point(3, 6) - uses __mul__
```

### Comparison Special Methods

```python
class Student:
    def __init__(self, name, gpa):
        self.name = name
        self.gpa = gpa
    
    def __eq__(self, other):
        """Students are equal if same name and GPA"""
        return self.name == other.name and self.gpa == other.gpa
    
    def __ne__(self, other):
        """Not equal (!=) - opposite of __eq__"""
        return not self.__eq__(other)
    
    def __lt__(self, other):
        """Less than - compare by GPA"""
        return self.gpa < other.gpa
    
    def __le__(self, other):
        """Less than or equal"""
        return self.gpa <= other.gpa
    
    def __gt__(self, other):
        """Greater than"""
        return self.gpa > other.gpa
    
    def __ge__(self, other):
        """Greater than or equal"""
        return self.gpa >= other.gpa
    
    def __str__(self):
        return f"{self.name} (GPA: {self.gpa})"

# Now students can be compared and sorted!
alice = Student("Alice", 3.8)
bob = Student("Bob", 3.5)
charlie = Student("Charlie", 3.9)

print(alice > bob)        # True
print(bob < charlie)      # True
print(alice == charlie)   # False

students = [alice, bob, charlie]
students.sort()  # Sorts by GPA using __lt__
print([str(s) for s in students])
# ['Bob (GPA: 3.5)', 'Alice (GPA: 3.8)', 'Charlie (GPA: 3.9)']
```

### Arithmetic Special Methods

```python
class Money:
    def __init__(self, dollars, cents=0):
        self.dollars = dollars
        self.cents = cents
        self._normalize()
    
    def _normalize(self):
        """Convert excess cents to dollars"""
        if self.cents >= 100:
            self.dollars += self.cents // 100
            self.cents = self.cents % 100
        elif self.cents < 0:
            dollars_to_subtract = (-self.cents // 100) + 1
            self.dollars -= dollars_to_subtract
            self.cents += dollars_to_subtract * 100
    
    def __add__(self, other):
        """Add two Money objects"""
        return Money(self.dollars + other.dollars, self.cents + other.cents)
    
    def __sub__(self, other):
        """Subtract two Money objects"""
        return Money(self.dollars - other.dollars, self.cents - other.cents)
    
    def __mul__(self, factor):
        """Multiply money by a number"""
        total_cents = (self.dollars * 100 + self.cents) * factor
        return Money(0, int(total_cents))
    
    def __truediv__(self, divisor):
        """Divide money by a number"""
        total_cents = (self.dollars * 100 + self.cents) / divisor
        return Money(0, int(total_cents))
    
    def __iadd__(self, other):
        """In-place addition (+=)"""
        self.dollars += other.dollars
        self.cents += other.cents
        self._normalize()
        return self
    
    def __str__(self):
        return f"${self.dollars}.{self.cents:02d}"
    
    def __repr__(self):
        return f"Money({self.dollars}, {self.cents})"

# Usage
price1 = Money(10, 50)
price2 = Money(5, 75)

total = price1 + price2     # $16.25
diff = price1 - price2      # $4.75
doubled = price1 * 2        # $21.00
half = price2 / 2           # $2.87

cart_total = Money(0)
cart_total += Money(10, 99)  # Uses __iadd__
cart_total += Money(5, 50)
print(cart_total)  # $16.49
```

### Container Special Methods

```python
class Playlist:
    def __init__(self, name):
        self.name = name
        self.songs = []
    
    def add_song(self, song):
        self.songs.append(song)
    
    def __len__(self):
        """len(playlist) returns number of songs"""
        return len(self.songs)
    
    def __getitem__(self, index):
        """playlist[index] returns song at index"""
        return self.songs[index]
    
    def __setitem__(self, index, song):
        """playlist[index] = song sets song at index"""
        self.songs[index] = song
    
    def __delitem__(self, index):
        """del playlist[index] removes song at index"""
        del self.songs[index]
    
    def __contains__(self, song):
        """song in playlist checks membership"""
        return song in self.songs
    
    def __iter__(self):
        """for song in playlist: loops through songs"""
        return iter(self.songs)
    
    def __str__(self):
        return f"Playlist '{self.name}' with {len(self)} songs"

# Usage
my_playlist = Playlist("Favorites")
my_playlist.add_song("Song A")
my_playlist.add_song("Song B")
my_playlist.add_song("Song C")

# Acts like a list!
print(len(my_playlist))          # 3 - uses __len__
print(my_playlist[1])            # "Song B" - uses __getitem__
my_playlist[1] = "Song B (remix)" # Uses __setitem__

if "Song A" in my_playlist:      # Uses __contains__
    print("Found Song A")

# Can iterate!
for song in my_playlist:         # Uses __iter__
    print(f"  - {song}")

del my_playlist[0]               # Uses __delitem__
print(len(my_playlist))          # 2
```

**Practice** (45 min):

**Exercise 4.7**: Vector Class with Operations
```python
# Create a Vector class for 2D vectors:
# 
# Attributes:
#   - x, y (components)
# 
# Special methods to implement:
#   - __init__(x, y)
#   - __str__() - return "Vector(x, y)"
#   - __repr__() - return "Vector(x=..., y=...)"
#   - __eq__(other) - vectors equal if same x and y
#   - __add__(other) - vector addition
#   - __sub__(other) - vector subtraction
#   - __mul__(scalar) - multiply by scalar
#   - __abs__() - return magnitude (length) of vector
#   - __neg__() - return negative vector (-x, -y)
# 
# Regular methods:
#   - dot(other) - dot product
#   - angle_with(other) - angle between vectors (bonus)
# 
# Test all operations:
# v1 = Vector(3, 4)
# v2 = Vector(1, 2)
# v3 = v1 + v2  # Vector(4, 6)
# v4 = v1 * 2   # Vector(6, 8)
# print(abs(v1)) # 5.0 (magnitude)
```

**Exercise 4.8**: Fraction Class
```python
# Create a Fraction class for rational numbers:
# 
# Attributes:
#   - numerator, denominator
# 
# Special methods:
#   - __init__(numerator, denominator) - simplify automatically
#   - __str__() - return "3/4" format
#   - __repr__() - return "Fraction(3, 4)"
#   - __eq__(other) - check equality
#   - __lt__(other) - less than comparison
#   - __add__(other) - add fractions
#   - __sub__(other) - subtract fractions
#   - __mul__(other) - multiply fractions
#   - __truediv__(other) - divide fractions
#   - __float__() - convert to decimal
# 
# Helper methods:
#   - simplify() - reduce to lowest terms
#   - gcd(a, b) - greatest common divisor (static method)
# 
# Examples:
# f1 = Fraction(1, 2)
# f2 = Fraction(1, 4)
# f3 = f1 + f2  # Fraction(3, 4)
# print(f1 > f2)  # True
# print(float(f1))  # 0.5
```

**Exercise 4.9**: Shopping Cart Container
```python
# Create a ShoppingCart class that acts like a container:
# 
# Attributes:
#   - items (dict: {product_name: {"price": float, "quantity": int}})
# 
# Special methods to implement:
#   - __len__() - return total number of items (sum of quantities)
#   - __getitem__(product_name) - return item dict
#   - __setitem__(product_name, item_dict) - add/update item
#   - __delitem__(product_name) - remove item
#   - __contains__(product_name) - check if product in cart
#   - __iter__() - iterate over product names
#   - __add__(other_cart) - merge two carts
#   - __str__() - formatted cart display
# 
# Regular methods:
#   - add_item(name, price, quantity)
#   - update_quantity(name, quantity)
#   - get_total()
#   - clear()
# 
# Usage should look like:
# cart = ShoppingCart()
# cart["Apple"] = {"price": 0.99, "quantity": 5}
# if "Apple" in cart:
#     print(cart["Apple"])
# for product in cart:
#     print(product)
```

---

## Day 22: Special Methods (Magic Methods) Part II

**Concepts** (45 min):

### Context Managers (__enter__ and __exit__)

Context managers allow you to allocate and release resources precisely. Used with the `with` statement.

```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        """Called when entering 'with' block"""
        print(f"Opening {self.filename}")
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_value, traceback):
        """Called when exiting 'with' block"""
        if self.file:
            print(f"Closing {self.filename}")
            self.file.close()
        # Return False to propagate exceptions
        # Return True to suppress exceptions
        return False

# Usage
with FileManager("test.txt", "w") as f:
    f.write("Hello, World!")
# File automatically closed after 'with' block

# More practical example: Database connection
class DatabaseConnection:
    def __init__(self, connection_string):
        self.connection_string = connection_string
        self.connection = None
    
    def __enter__(self):
        print("Connecting to database...")
        # Simulate connection
        self.connection = {"connected": True, "data": []}
        return self.connection
    
    def __exit__(self, exc_type, exc_value, traceback):
        print("Closing database connection...")
        if self.connection:
            self.connection["connected"] = False
        if exc_type is not None:
            print(f"Exception occurred: {exc_value}")
        return False

with DatabaseConnection("mydb://localhost") as db:
    db["data"].append("some data")
    print("Working with database...")
# Connection automatically closed
```

### Callable Objects (__call__)

Makes an instance callable like a function.

```python
class Multiplier:
    def __init__(self, factor):
        self.factor = factor
    
    def __call__(self, x):
        """Makes instance callable: multiplier(5)"""
        return x * self.factor

# Create callable objects
double = Multiplier(2)
triple = Multiplier(3)

print(double(5))   # 10 - calls __call__(5)
print(triple(5))   # 15

# More complex example: Counter
class Counter:
    def __init__(self):
        self.count = 0
    
    def __call__(self):
        """Each call increments and returns count"""
        self.count += 1
        return self.count
    
    def reset(self):
        self.count = 0

counter = Counter()
print(counter())  # 1
print(counter())  # 2
print(counter())  # 3
counter.reset()
print(counter())  # 1

# Practical example: Validator
class EmailValidator:
    def __init__(self):
        self.valid_count = 0
        self.invalid_count = 0
    
    def __call__(self, email):
        """Validate email when instance is called"""
        is_valid = '@' in email and '.' in email.split('@')[1]
        if is_valid:
            self.valid_count += 1
        else:
            self.invalid_count += 1
        return is_valid
    
    def get_stats(self):
        return {
            "valid": self.valid_count,
            "invalid": self.invalid_count
        }

validate = EmailValidator()
print(validate("user@example.com"))   # True
print(validate("invalid-email"))      # False
print(validate("another@test.org"))   # True
print(validate.get_stats())           # {'valid': 2, 'invalid': 1}
```

### Attribute Access (__getattr__, __setattr__, __delattr__)

Control how attributes are accessed, set, and deleted.

```python
class DynamicStorage:
    def __init__(self):
        # Use object.__setattr__ to avoid infinite recursion
        object.__setattr__(self, '_data', {})
    
    def __getattr__(self, name):
        """Called when attribute doesn't exist normally"""
        if name in self._data:
            return self._data[name]
        raise AttributeError(f"'{type(self).__name__}' has no attribute '{name}'")
    
    def __setattr__(self, name, value):
        """Called for all attribute assignments"""
        if name.startswith('_'):
            # Allow private attributes to be set normally
            object.__setattr__(self, name, value)
        else:
            # Store public attributes in _data dict
            self._data[name] = value
    
    def __delattr__(self, name):
        """Called when del obj.attr is used"""
        if name in self._data:
            del self._data[name]
        else:
            raise AttributeError(f"Cannot delete attribute '{name}'")
    
    def __str__(self):
        return f"DynamicStorage({self._data})"

# Usage
storage = DynamicStorage()
storage.name = "Alice"      # Uses __setattr__
storage.age = 30
print(storage.name)         # Uses __getattr__ - "Alice"
del storage.age             # Uses __delattr__
print(storage)              # DynamicStorage({'name': 'Alice'})

# Practical example: Logged attributes
class LoggedObject:
    def __init__(self):
        object.__setattr__(self, '_log', [])
        object.__setattr__(self, '_attributes', {})
    
    def __setattr__(self, name, value):
        if name.startswith('_'):
            object.__setattr__(self, name, value)
        else:
            old_value = self._attributes.get(name)
            self._attributes[name] = value
            self._log.append(f"Set {name}: {old_value} -> {value}")
    
    def __getattr__(self, name):
        if name in self._attributes:
            self._log.append(f"Accessed {name}")
            return self._attributes[name]
        raise AttributeError(f"No attribute '{name}'")
    
    def show_log(self):
        for entry in self._log:
            print(entry)

obj = LoggedObject()
obj.name = "Alice"
obj.age = 25
obj.age = 26
print(obj.name)
obj.show_log()
# Output:
# Set name: None -> Alice
# Set age: None -> 25
# Set age: 25 -> 26
# Accessed name
```

### Descriptors (__get__, __set__, __delete__)

Descriptors allow you to customize attribute access at the class level.

```python
class ValidatedString:
    def __init__(self, min_length=0, max_length=100):
        self.min_length = min_length
        self.max_length = max_length
    
    def __set_name__(self, owner, name):
        """Called when descriptor is assigned to class attribute"""
        self.name = "_" + name
    
    def __get__(self, obj, objtype=None):
        """Called when attribute is accessed"""
        if obj is None:
            return self
        return getattr(obj, self.name, "")
    
    def __set__(self, obj, value):
        """Called when attribute is set"""
        if not isinstance(value, str):
            raise TypeError(f"{self.name} must be a string")
        if len(value) < self.min_length:
            raise ValueError(f"{self.name} must be at least {self.min_length} characters")
        if len(value) > self.max_length:
            raise ValueError(f"{self.name} must be at most {self.max_length} characters")
        setattr(obj, self.name, value)

class User:
    # Descriptors for validation
    username = ValidatedString(min_length=3, max_length=20)
    email = ValidatedString(min_length=5)
    
    def __init__(self, username, email):
        self.username = username  # Uses descriptor __set__
        self.email = email

# Usage
user = User("alice", "alice@example.com")
print(user.username)  # Uses descriptor __get__

try:
    user.username = "ab"  # Too short - raises ValueError
except ValueError as e:
    print(e)

try:
    user2 = User("a", "test@test.com")  # Too short
except ValueError as e:
    print(e)
```

**Practice** (45 min):

**Exercise 4.10**: Resource Manager Context Manager
```python
# Create a ResourceManager context manager:
# 
# Features:
#   - Tracks multiple resource allocations
#   - Logs when resources are acquired/released
#   - Ensures all resources are released even if exception occurs
# 
# Class structure:
# class ResourceManager:
#     def __init__(self, name)
#     def __enter__()
#     def __exit__(exc_type, exc_value, traceback)
#     def allocate(resource_name)
#     def release(resource_name)
# 
# Usage:
# with ResourceManager("DB") as manager:
#     manager.allocate("connection")
#     manager.allocate("cursor")
#     # Do work
#     # Resources automatically released on exit
# 
# Add logging to show what's happening
```

**Exercise 4.11**: Function Call Counter
```python
# Create a CountedFunction class using __call__:
# 
# Features:
#   - Wraps any function
#   - Counts how many times it's been called
#   - Tracks arguments used
#   - Can reset counter
# 
# Class structure:
# class CountedFunction:
#     def __init__(self, func)
#     def __call__(*args, **kwargs) - execute function and count
#     def call_count()
#     def reset()
#     def get_call_history()
# 
# Usage:
# def add(a, b):
#     return a + b
# 
# counted_add = CountedFunction(add)
# result = counted_add(2, 3)  # 5
# result = counted_add(5, 7)  # 12
# print(counted_add.call_count())  # 2
```

**Exercise 4.12**: Monitored Dictionary
```python
# Create a MonitoredDict class that tracks all changes:
# 
# Special methods to implement:
#   - __getitem__, __setitem__, __delitem__
#   - __len__, __contains__, __iter__
#   - __str__, __repr__
# 
# Additional features:
#   - Log all operations (get, set, delete)
#   - Track modification count
#   - Undo last change
#   - Get history of all changes
# 
# Example usage:
# md = MonitoredDict()
# md["key1"] = "value1"
# md["key2"] = "value2"
# value = md["key1"]
# del md["key2"]
# md.show_history()
# # Should show all operations logged
```

---

## Day 23: Inheritance Basics

**Concepts** (45 min):

### Basic Inheritance

Inheritance allows a class (child/subclass) to inherit attributes and methods from another class (parent/superclass).

```python
# Parent class (superclass/base class)
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species
        self.is_alive = True
    
    def eat(self, food):
        print(f"{self.name} is eating {food}")
    
    def sleep(self):
        print(f"{self.name} is sleeping")
    
    def make_sound(self):
        print(f"{self.name} makes a sound")

# Child class (subclass/derived class)
class Dog(Animal):
    def __init__(self, name, breed):
        # Call parent constructor
        super().__init__(name, "Dog")
        self.breed = breed
    
    # Override parent method
    def make_sound(self):
        print(f"{self.name} barks: Woof!")
    
    # Add new method specific to Dog
    def fetch(self, item):
        print(f"{self.name} fetches the {item}")

class Cat(Animal):
    def __init__(self, name, color):
        super().__init__(name, "Cat")
        self.color = color
    
    def make_sound(self):
        print(f"{self.name} meows: Meow!")
    
    def scratch(self, target):
        print(f"{self.name} scratches the {target}")

# Usage
dog = Dog("Max", "Golden Retriever")
cat = Cat("Whiskers", "Orange")

# Inherited methods
dog.eat("kibble")      # Max is eating kibble
cat.sleep()            # Whiskers is sleeping

# Overridden methods
dog.make_sound()       # Max barks: Woof!
cat.make_sound()       # Whiskers meows: Meow!

# Subclass-specific methods
dog.fetch("ball")      # Max fetches the ball
cat.scratch("couch")   # Whiskers scratches the couch

# Check inheritance
print(isinstance(dog, Dog))      # True
print(isinstance(dog, Animal))   # True
print(isinstance(dog, Cat))      # False
```

### The super() Function

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        print(f"Person.__init__ called for {name}")
    
    def introduce(self):
        print(f"Hi, I'm {self.name}, {self.age} years old")

class Employee(Person):
    def __init__(self, name, age, employee_id, salary):
        # Call parent constructor
        super().__init__(name, age)
        self.employee_id = employee_id
        self.salary = salary
        print(f"Employee.__init__ called for {name}")
    
    def introduce(self):
        # Call parent method, then add more
        super().introduce()
        print(f"Employee ID: {self.employee_id}")
        print(f"Salary: ${self.salary:,}")

class Manager(Employee):
    def __init__(self, name, age, employee_id, salary, department):
        super().__init__(name, age, employee_id, salary)
        self.department = department
        self.team = []
        print(f"Manager.__init__ called for {name}")
    
    def introduce(self):
        super().introduce()
        print(f"Department: {self.department}")
        print(f"Team size: {len(self.team)}")
    
    def add_team_member(self, employee):
        self.team.append(employee)

# Creating objects shows constructor chain
manager = Manager("Alice", 35, "E001", 85000, "Engineering")
# Output:
# Person.__init__ called for Alice
# Employee.__init__ called for Alice
# Manager.__init__ called for Alice

manager.introduce()
# Hi, I'm Alice, 35 years old
# Employee ID: E001
# Salary: $85,000
# Department: Engineering
# Team size: 0
```

### Method Resolution Order (MRO)

```python
class A:
    def method(self):
        print("A.method")

class B(A):
    def method(self):
        print("B.method")
        super().method()

class C(A):
    def method(self):
        print("C.method")
        super().method()

class D(B, C):
    def method(self):
        print("D.method")
        super().method()

# Method Resolution Order: D -> B -> C -> A -> object
d = D()
d.method()
# Output:
# D.method
# B.method
# C.method
# A.method

# View MRO
print(D.__mro__)
# (<class '__main__.D'>, <class '__main__.B'>, 
#  <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
```

### Practical Inheritance Example

```python
class BankAccount:
    """Base class for all bank accounts"""
    account_counter = 1000
    
    def __init__(self, owner, initial_balance=0):
        BankAccount.account_counter += 1
        self.account_number = f"ACC{BankAccount.account_counter}"
        self.owner = owner
        self._balance = initial_balance
        self.transactions = []
        self._log_transaction("Account opened", initial_balance)
    
    def _log_transaction(self, description, amount):
        """Private method for logging"""
        self.transactions.append({
            "description": description,
            "amount": amount,
            "balance": self._balance
        })
    
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
            self._log_transaction("Deposit", amount)
            return True
        return False
    
    def withdraw(self, amount):
        if 0 < amount <= self._balance:
            self._balance -= amount
            self._log_transaction("Withdrawal", -amount)
            return True
        return False
    
    def get_balance(self):
        return self._balance
    
    def print_statement(self):
        print(f"{'='*50}")
        print(f"Account Statement - {self.account_number}")
        print(f"Owner: {self.owner}")
        print(f"{'='*50}")
        for trans in self.transactions:
            sign = "+" if trans["amount"] >= 0 else ""
            print(f"{trans['description']:<20} {sign}${trans['amount']:>8.2f} "
                  f"Balance: ${trans['balance']:>8.2f}")
        print(f"{'='*50}")
        print(f"Current Balance: ${self._balance:.2f}")
        print(f"{'='*50}")

class SavingsAccount(BankAccount):
    """Savings account with interest"""
    def __init__(self, owner, initial_balance=0, interest_rate=0.02):
        super().__init__(owner, initial_balance)
        self.interest_rate = interest_rate
    
    def apply_interest(self):
        """Calculate and add interest"""
        interest = self._balance * self.interest_rate
        self._balance += interest
        self._log_transaction(f"Interest ({self.interest_rate*100}%)", interest)
        return interest
    
    def withdraw(self, amount):
        """Override: Limit withdrawals to 6 per month"""
        withdrawal_count = sum(1 for t in self.transactions 
                             if "Withdrawal" in t["description"])
        if withdrawal_count >= 6:
            print("Monthly withdrawal limit reached")
            return False
        return super().withdraw(amount)

class CheckingAccount(BankAccount):
    """Checking account with overdraft protection"""
    def __init__(self, owner, initial_balance=0, overdraft_limit=100):
        super().__init__(owner, initial_balance)
        self.overdraft_limit = overdraft_limit
    
    def withdraw(self, amount):
        """Override: Allow overdraft up to limit"""
        if amount > 0 and amount <= self._balance + self.overdraft_limit:
            self._balance -= amount
            self._log_transaction("Withdrawal", -amount)
            if self._balance < 0:
                print(f"Warning: Overdraft of ${-self._balance:.2f}")
            return True
        print("Insufficient funds including overdraft")
        return False
    
    def charge_overdraft_fee(self):
        """Charge fee if in overdraft"""
        if self._balance < 0:
            fee = 35
            self._balance -= fee
            self._log_transaction("Overdraft fee", -fee)
            return fee
        return 0

# Usage
savings = SavingsAccount("Alice", 1000, 0.03)
checking = CheckingAccount("Bob", 500, 200)

# Savings operations
savings.deposit(500)
savings.apply_interest()
savings.print_statement()

# Checking with overdraft
checking.withdraw(600)  # Goes into overdraft
checking.charge_overdraft_fee()
checking.print_statement()
```

**Practice** (45 min):

**Exercise 4.13**: Vehicle Hierarchy
```python
# Create a vehicle inheritance hierarchy:
# 
# Base class: Vehicle
#   Attributes: make, model, year, mileage
#   Methods:
#     - __init__
#     - drive(miles) - increase mileage
#     - get_info() - return formatted string
#     - calculate_value() - base depreciation formula
# 
# Subclass: Car (inherits Vehicle)
#   Additional attributes: num_doors, trunk_capacity
#   Override calculate_value() - different depreciation
#   Add: is_sedan() - returns True if 4 doors
# 
# Subclass: Truck (inherits Vehicle)
#   Additional attributes: bed_length, towing_capacity
#   Override calculate_value()
#   Add: can_tow(weight) - check if can tow given weight
# 
# Subclass: Motorcycle (inherits Vehicle)
#   Additional attributes: engine_cc, has_sidecar
#   Override calculate_value()
#   Add: is_sport_bike() - returns True if engine_cc > 600
# 
# Create instances of each type and demonstrate all methods
```

**Exercise 4.14**: Employee Management System
```python
# Create an employee hierarchy:
# 
# Base class: Employee
#   Attributes: name, employee_id, hire_date, base_salary
#   Methods:
#     - __init__
#     - calculate_salary() - returns base_salary
#     - get_info()
#     - years_of_service() - calculate from hire_date
# 
# Subclass: HourlyEmployee (inherits Employee)
#   Additional: hours_worked, hourly_rate
#   Override calculate_salary() - hours * rate
#   Add: log_hours(hours)
# 
# Subclass: SalariedEmployee (inherits Employee)
#   Additional: annual_salary
#   Override calculate_salary() - annual/12
#   Add: get_annual_salary()
# 
# Subclass: Manager (inherits SalariedEmployee)
#   Additional: department, team_size, bonus_percentage
#   Override calculate_salary() - base + bonus
#   Add: add_bonus(percentage)
# 
# Subclass: Executive (inherits Manager)
#   Additional: stock_options
#   Override calculate_salary() - salary + stock value
#   Add: exercise_options(amount)
# 
# Demonstrate the entire hierarchy with sample data
```

**Exercise 4.15**: Shape Hierarchy with Area Calculations
```python
# Create a shape hierarchy:
# 
# Base class: Shape
#   Attributes: name, color
#   Methods:
#     - __init__
#     - calculate_area() - raises NotImplementedError
#     - calculate_perimeter() - raises NotImplementedError
#     - get_info()
# 
# Subclass: Rectangle (inherits Shape)
#   Additional: width, height
#   Override calculate_area() and calculate_perimeter()
#   Add: is_square() - returns True if width == height
# 
# Subclass: Circle (inherits Shape)
#   Additional: radius
#   Override calculate_area() and calculate_perimeter()
#   Add: get_diameter()
# 
# Subclass: Triangle (inherits Shape)
#   Additional: side_a, side_b, side_c
#   Override calculate_area() (use Heron's formula) and calculate_perimeter()
#   Add: is_right_triangle() - check if right triangle
#   Add: triangle_type() - returns "Equilateral", "Isosceles", or "Scalene"
# 
# Create multiple shapes and calculate total area
```

---

## Day 24: Weekly Assignment - Week 4

**Time**: 1.4 hours  
**Due**: End of Day 24  
**Grading**: See rubric at end

### Assignment 4: Enhanced Security System with Inheritance

Expand your Week 3 Security Incident Management System by implementing inheritance hierarchies and advanced OOP techniques.

**New Requirements**:

### Part 1: Incident Type Hierarchy (35 points)

Create an inheritance hierarchy for different incident types:

**Base Class: SecurityIncident** (modify from Week 3)
- Keep all existing functionality
- Add abstract methods that subclasses must implement:
  - `get_severity_score()` - returns numeric severity (0-100)
  - `get_response_procedure()` - returns list of response steps
  - `requires_immediate_action()` - returns boolean

**Subclass: MalwareIncident**
```python
class MalwareIncident(SecurityIncident):
    def __init__(self, title, description, severity, malware_type, affected_systems):
        super().__init__(title, description, severity)
        self.malware_type = malware_type  # "Virus", "Ransomware", "Trojan", etc.
        self.affected_systems = affected_systems  # list of system names
        self.is_contained = False
    
    # Override/implement methods
    def get_severity_score(self):
        # Calculate based on malware_type and number of affected_systems
        pass
    
    def get_response_procedure(self):
        # Return malware-specific response steps
        pass
    
    def requires_immediate_action(self):
        # Ransomware always requires immediate action
        pass
    
    # New methods
    def contain_malware(self, systems):
        # Mark systems as contained
        pass
    
    def get_affected_system_count(self):
        pass
```

**Subclass: NetworkIncident**
```python
class NetworkIncident(SecurityIncident):
    def __init__(self, title, description, severity, source_ip, 
                 destination_ip, port, protocol):
        super().__init__(title, description, severity)
        self.source_ip = source_ip
        self.destination_ip = destination_ip
        self.port = port
        self.protocol = protocol  # "TCP", "UDP", "ICMP"
        self.is_blocked = False
    
    # Implement required methods
    def get_severity_score(self):
        # Based on port, protocol, and IPs
        pass
    
    def get_response_procedure(self):
        # Network-specific response
        pass
    
    def requires_immediate_action(self):
        # Based on common attack ports
        pass
    
    # New methods
    def block_source(self):
        pass
    
    def is_internal_to_internal(self):
        # Check if both IPs are internal
        pass
```

**Subclass: DataBreachIncident**
```python
class DataBreachIncident(SecurityIncident):
    def __init__(self, title, description, severity, data_type,
                 records_affected, exfiltration_method):
        super().__init__(title, description, severity)
        self.data_type = data_type  # "PII", "Financial", "Healthcare", etc.
        self.records_affected = records_affected
        self.exfiltration_method = exfiltration_method
        self.regulatory_notification_required = self._check_regulatory()
    
    def _check_regulatory(self):
        # Determine if regulatory notification needed
        pass
    
    def get_severity_score(self):
        # Higher if PII/Healthcare, more records
        pass
    
    def get_response_procedure(self):
        # Data breach specific response
        pass
    
    def requires_immediate_action(self):
        # Always True for data breaches
        pass
    
    def get_notification_requirements(self):
        # Return list of required notifications
        pass
```

### Part 2: Analyst Specialization Hierarchy (25 points)

Create specialized analyst classes:

**Base Class: SecurityAnalyst** (from Week 3)
- Enhance with additional methods

**Subclass: JuniorAnalyst**
```python
class JuniorAnalyst(SecurityAnalyst):
    def __init__(self, name, analyst_id, expertise_areas, mentor):
        super().__init__(name, analyst_id, expertise_areas)
        self.mentor = mentor  # Reference to SeniorAnalyst
        self.max_concurrent_incidents = 3
    
    def can_handle_incident(self, incident):
        # Check if expertise matches and under limit
        pass
    
    def request_help(self, incident_id):
        # Escalate to mentor
        pass
```

**Subclass: SeniorAnalyst**
```python
class SeniorAnalyst(SecurityAnalyst):
    def __init__(self, name, analyst_id, expertise_areas, certifications):
        super().__init__(name, analyst_id, expertise_areas)
        self.certifications = certifications  # list of certs
        self.mentees = []  # list of JuniorAnalysts
        self.max_concurrent_incidents = 10
    
    def add_mentee(self, junior_analyst):
        pass
    
    def handle_escalation(self, incident, from_analyst):
        # Take over escalated incident
        pass
    
    def can_handle_incident(self, incident):
        # Can handle any incident type
        pass
```

**Subclass: IncidentResponseLead**
```python
class IncidentResponseLead(SeniorAnalyst):
    def __init__(self, name, analyst_id, expertise_areas, certifications):
        super().__init__(name, analyst_id, expertise_areas, certifications)
        self.active_investigations = []
        self.can_declare_major_incident = True
    
    def declare_major_incident(self, incident):
        # Escalate to major incident status
        pass
    
    def coordinate_response(self, incident, team):
        # Coordinate multi-analyst response
        pass
```

### Part 3: Enhanced SOC with Inheritance (25 points)

Update SecurityOperationsCenter class to work with inheritance:

```python
class SecurityOperationsCenter:
    def __init__(self, name):
        self.name = name
        self.incidents = []
        self.analysts = []
        self.assets = []
    
    def report_malware_incident(self, title, description, severity, 
                                malware_type, affected_systems):
        # Create MalwareIncident
        pass
    
    def report_network_incident(self, title, description, severity,
                               source_ip, dest_ip, port, protocol):
        # Create NetworkIncident
        pass
    
    def report_data_breach(self, title, description, severity,
                          data_type, records, method):
        # Create DataBreachIncident
        pass
    
    def auto_assign_incident(self, incident):
        # Intelligently assign based on analyst type and expertise
        # Junior analysts get simpler incidents
        # Senior analysts get complex incidents
        pass
    
    def get_incidents_by_type(self, incident_type):
        # Return all incidents of specific type
        pass
    
    def get_incidents_requiring_immediate_action(self):
        # Use requires_immediate_action() method
        pass
    
    def generate_incident_report(self, incident_id):
        # Generate detailed report using incident-specific methods
        pass
    
    def print_enhanced_dashboard(self):
        # Enhanced dashboard showing:
        # - Incidents by type
        # - Immediate action items
        # - Analyst workload by level (Junior/Senior/Lead)
        # - Average severity scores
        pass
```

### Part 4: Demonstration (15 points)

Create a comprehensive demonstration that shows:

1. **Create diverse incidents**:
   - 3+ malware incidents (different types)
   - 3+ network incidents (various ports/protocols)
   - 2+ data breach incidents (different data types)

2. **Create analyst team**:
   - 2 junior analysts with mentors
   - 3 senior analysts (some are mentors)
   - 1 incident response lead

3. **Demonstrate functionality**:
   - Auto-assignment based on expertise and level
   - Escalation from junior to senior
   - Major incident declaration
   - Incident-specific response procedures
   - Severity score calculations
   - Immediate action identification

4. **Print reports**:
   - Enhanced dashboard
   - Individual incident reports showing type-specific details
   - Analyst workload by level
   - Summary statistics by incident type

**Example Output**:
```
========================================
CYBER DEFENSE SOC - ENHANCED DASHBOARD
========================================

INCIDENTS BY TYPE
-----------------
Malware Incidents: 3
  - Ransomware: 1 (CRITICAL)
  - Trojan: 1 (HIGH)
  - Virus: 1 (MEDIUM)

Network Incidents: 3
  - Port Scans: 2 (MEDIUM)
  - DDoS: 1 (HIGH)

Data Breach Incidents: 2
  - PII Breach: 1 (CRITICAL) - Regulatory notification required
  - Financial Data: 1 (HIGH)

IMMEDIATE ACTION REQUIRED
-------------------------
1. [CRITICAL] Ransomware - Finance Server
   Severity Score: 95/100
   Affected Systems: 12
   Response: Isolate, contain, notify executive team

2. [CRITICAL] PII Data Breach
   Severity Score: 90/100
   Records Affected: 50,000
   Regulatory: GDPR notification required within 72 hours

ANALYST WORKLOAD
----------------
Junior Analysts:
  John Smith (Mentor: Sarah Connor) - 2 incidents
    - Network scan investigation
    - Phishing email analysis
  
Senior Analysts:
  Sarah Connor (Mentoring: 2 analysts) - 4 incidents
    - Ransomware containment
    - Data breach investigation
    - Plus 2 escalated from juniors

Incident Response Lead:
  Mike Johnson - Coordinating major incidents: 1
    - Active: Ransomware outbreak response

METRICS
-------
Average Severity Score: 67/100
Incidents Requiring Immediate Action: 2
Auto-Assignment Success Rate: 100%
Escalation Rate: 15%
========================================
```

---

### Grading Rubric - Week 4 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **Incident Hierarchy** | 35 | |
| Base class design | 10 | Proper abstract methods, good inheritance structure |
| MalwareIncident | 8 | Correctly implements all methods, malware-specific logic |
| NetworkIncident | 8 | Network-specific implementation, IP/port handling |
| DataBreachIncident | 9 | Regulatory logic, severity calculations |
| **Analyst Hierarchy** | 25 | |
| Base enhancement | 5 | Enhanced SecurityAnalyst with inheritance in mind |
| JuniorAnalyst | 7 | Mentor relationship, escalation logic |
| SeniorAnalyst | 7 | Mentee management, advanced handling |
| IncidentResponseLead | 6 | Major incident coordination |
| **Enhanced SOC** | 25 | |
| Type-specific creation | 8 | Methods for each incident type |
| Auto-assignment | 10 | Intelligent assignment based on analyst level/expertise |
| Reporting | 7 | Enhanced dashboard with type breakdowns |
| **Demonstration** | 15 | |
| Diverse scenarios | 5 | Variety of incidents and analysts |
| Functionality showcase | 7 | All features demonstrated clearly |
| Output quality | 3 | Professional, well-formatted output |
| **Bonus** | +25 | See bonus challenges below |

**Code Quality Requirements**:
- Proper use of super() in all subclasses
- Method overriding done correctly
- Clear distinction between base and subclass functionality
- No code duplication (use inheritance properly)
- Type checking with isinstance() where appropriate

**Bonus Challenges** (+5 points each):

1. **Incident Correlation**: Add method to find related incidents (same source IP, malware type, etc.)
2. **Analyst Performance Metrics**: Track resolution times, success rates per analyst
3. **Automated Playbooks**: Implement automated response playbooks for each incident type
4. **Incident Timeline**: Track detailed timeline of all incident actions
5. **Context Managers**: Implement `with` statement support for incident handling

**Testing Requirements**:
- [ ] All three incident types create correctly
- [ ] Severity scores calculate differently per type
- [ ] Response procedures are type-specific
- [ ] Junior analysts can escalate to seniors
- [ ] Senior analysts can accept escalations
- [ ] Incident Response Lead can declare major incidents
- [ ] Auto-assignment respects analyst levels
- [ ] Enhanced dashboard shows all new information
- [ ] isinstance() checks work correctly

**Submission**:
- Save as `week4_assignment.py`
- Include detailed comments explaining inheritance design
- Document any design decisions in header comments
- Include test scenarios demonstrating all functionality

</details>

---

<details>
<summary><h1>Week 5: Intermediate OOP</h1></summary>

**Focus**: Polymorphism, Abstract Classes, Multiple Inheritance, and Composition

## Day 25 (Monday): Polymorphism

**Concepts** (45 min):

### Understanding Polymorphism

Polymorphism means "many forms" - the ability of different objects to respond to the same method call in different ways.

```python
# Different classes, same interface
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

class Duck:
    def speak(self):
        return "Quack!"

# Polymorphism in action
def animal_sound(animal):
    """Works with any object that has a speak() method"""
    print(animal.speak())

animals = [Dog(), Cat(), Duck()]
for animal in animals:
    animal_sound(animal)
# Woof!
# Meow!
# Quack!
```

### Polymorphism Through Inheritance

```python
class PaymentMethod:
    def process_payment(self, amount):
        raise NotImplementedError("Subclass must implement process_payment")
    
    def get_receipt(self, amount):
        return f"Payment of ${amount:.2f} processed"

class CreditCard(PaymentMethod):
    def __init__(self, card_number, cvv):
        self.card_number = card_number[-4:]  # Store only last 4
        self.cvv = cvv
    
    def process_payment(self, amount):
        print(f"Processing credit card payment of ${amount:.2f}")
        print(f"Card ending in: {self.card_number}")
        return True

class PayPal(PaymentMethod):
    def __init__(self, email):
        self.email = email
    
    def process_payment(self, amount):
        print(f"Processing PayPal payment of ${amount:.2f}")
        print(f"Account: {self.email}")
        return True

class Bitcoin(PaymentMethod):
    def __init__(self, wallet_address):
        self.wallet_address = wallet_address
    
    def process_payment(self, amount):
        print(f"Processing Bitcoin payment of ${amount:.2f}")
        print(f"Wallet: {self.wallet_address[:10]}...")
        return True

# Polymorphic function
def checkout(payment_method, amount):
    """Works with ANY PaymentMethod subclass"""
    if payment_method.process_payment(amount):
        print(payment_method.get_receipt(amount))
        return True
    return False

# All three use the same interface
credit_card = CreditCard("1234-5678-9012-3456", "123")
paypal = PayPal("user@example.com")
bitcoin = Bitcoin("1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa")

checkout(credit_card, 99.99)
print()
checkout(paypal, 149.50)
print()
checkout(bitcoin, 0.005)
```

### Duck Typing

Python uses "duck typing" - if it walks like a duck and quacks like a duck, it's a duck. Objects don't need to inherit from the same class.

```python
class FileWriter:
    def write(self, data):
        with open("output.txt", "a") as f:
            f.write(data + "\n")

class DatabaseWriter:
    def write(self, data):
        print(f"Saving to database: {data}")

class NetworkWriter:
    def write(self, data):
        print(f"Sending over network: {data}")

def log_message(writer, message):
    """Works with anything that has a write() method"""
    writer.write(f"[LOG] {message}")

# All three can be used interchangeably
file_writer = FileWriter()
db_writer = DatabaseWriter()
net_writer = NetworkWriter()

log_message(file_writer, "Application started")
log_message(db_writer, "User logged in")
log_message(net_writer, "Data synced")
```

### Polymorphism with Operators

```python
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector2D(self.x + other.x, self.y + other.y)
    
    def __str__(self):
        return f"Vector({self.x}, {self.y})"

class Vector3D:
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z
    
    def __add__(self, other):
        return Vector3D(self.x + other.x, self.y + other.y, self.z + other.z)
    
    def __str__(self):
        return f"Vector({self.x}, {self.y}, {self.z})"

# Same + operator, different behavior
v1 = Vector2D(1, 2)
v2 = Vector2D(3, 4)
print(v1 + v2)  # Vector(4, 6)

v3 = Vector3D(1, 2, 3)
v4 = Vector3D(4, 5, 6)
print(v3 + v4)  # Vector(5, 7, 9)
```

### Real-World Example: Report Generation

```python
class Report:
    def __init__(self, title, data):
        self.title = title
        self.data = data
    
    def generate(self):
        raise NotImplementedError("Subclass must implement generate()")

class PDFReport(Report):
    def generate(self):
        print(f"Generating PDF: {self.title}")
        print("=" * 50)
        for item in self.data:
            print(f"  • {item}")
        print("=" * 50)
        print("[PDF format applied]")

class ExcelReport(Report):
    def generate(self):
        print(f"Generating Excel: {self.title}")
        print("| Column 1        | Column 2        |")
        print("|" + "-" * 17 + "|" + "-" * 17 + "|")
        for item in self.data:
            print(f"| {item:<15} | Data            |")
        print("[Excel format applied]")

class HTMLReport(Report):
    def generate(self):
        print(f"<html><head><title>{self.title}</title></head>")
        print("<body>")
        print(f"<h1>{self.title}</h1>")
        print("<ul>")
        for item in self.data:
            print(f"  <li>{item}</li>")
        print("</ul>")
        print("</body></html>")

def create_report(report_type, title, data):
    """Factory function using polymorphism"""
    reports = {
        "pdf": PDFReport,
        "excel": ExcelReport,
        "html": HTMLReport
    }
    
    if report_type in reports:
        return reports[report_type](title, data)
    raise ValueError(f"Unknown report type: {report_type}")

# Polymorphic usage
data = ["Sales: $1M", "Expenses: $500K", "Profit: $500K"]

for format in ["pdf", "excel", "html"]:
    report = create_report(format, "Q4 Financial Report", data)
    report.generate()
    print("\n")
```

**Practice** (45 min):

**Exercise 5.1**: Shape Drawing System
```python
# Create a polymorphic drawing system:
# 
# Base class: Shape
#   Methods:
#     - draw() - raises NotImplementedError
#     - get_info() - returns shape details
# 
# Subclasses:
#   - Circle(Shape) - draws circle using ASCII
#   - Rectangle(Shape) - draws rectangle using ASCII
#   - Triangle(Shape) - draws triangle using ASCII
# 
# Function: draw_multiple_shapes(shapes)
#   Takes list of Shape objects and draws each
# 
# Create various shapes and draw them all with one function
# Demonstrate polymorphism
```

**Exercise 5.2**: Notification System
```python
# Create a polymorphic notification system:
# 
# Base class: Notification
#   Attributes: recipient, message
#   Methods:
#     - send() - raises NotImplementedError
#     - log() - logs that notification was sent
# 
# Subclasses:
#   - EmailNotification - sends via email
#   - SMSNotification - sends via SMS
#   - PushNotification - sends push notification
#   - SlackNotification - sends to Slack
# 
# Function: send_notification(notification)
#   Works with any Notification subclass
# 
# Function: send_bulk(notifications)
#   Sends list of different notification types
# 
# Demonstrate sending mixed notification types
```

**Exercise 5.3**: Data Serializer
```python
# Create polymorphic data serializers:
# 
# Base class: Serializer
#   Methods:
#     - serialize(data) - raises NotImplementedError
#     - deserialize(string) - raises NotImplementedError
# 
# Subclasses:
#   - JSONSerializer - converts to/from JSON
#   - XMLSerializer - converts to/from XML
#   - CSVSerializer - converts to/from CSV
#   - YAMLSerializer - converts to/from YAML (simplified)
# 
# Function: save_data(serializer, data, filename)
#   Uses any serializer to save data
# 
# Function: load_data(serializer, filename)
#   Uses any serializer to load data
# 
# Demonstrate saving/loading with different formats
```

---

## Day 26: Abstract Base Classes

**Concepts** (45 min):

### Introduction to ABC (Abstract Base Classes)

Abstract base classes enforce that subclasses implement certain methods. They cannot be instantiated directly.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    """Abstract base class - cannot instantiate"""
    
    def __init__(self, name):
        self.name = name
    
    @abstractmethod
    def make_sound(self):
        """Subclasses MUST implement this"""
        pass
    
    @abstractmethod
    def move(self):
        """Subclasses MUST implement this"""
        pass
    
    # Concrete method (has implementation)
    def sleep(self):
        print(f"{self.name} is sleeping")

class Dog(Animal):
    def make_sound(self):
        return "Woof!"
    
    def move(self):
        print(f"{self.name} runs on four legs")

class Bird(Animal):
    def make_sound(self):
        return "Chirp!"
    
    def move(self):
        print(f"{self.name} flies in the sky")

# Cannot create Animal directly
# animal = Animal("Generic")  # TypeError!

# Can create subclasses
dog = Dog("Rex")
print(dog.make_sound())  # Woof!
dog.move()               # Rex runs on four legs
dog.sleep()              # Rex is sleeping

# Incomplete subclass won't work
class Incomplete(Animal):
    def make_sound(self):
        return "..."
    # Missing move() method!

# incomplete = Incomplete("Test")  # TypeError!
```

### Abstract Properties

```python
from abc import ABC, abstractmethod

class Employee(ABC):
    def __init__(self, name, employee_id):
        self._name = name
        self._employee_id = employee_id
    
    @property
    @abstractmethod
    def salary(self):
        """Subclasses must implement salary property"""
        pass
    
    @abstractmethod
    def calculate_bonus(self):
        """Subclasses must implement bonus calculation"""
        pass
    
    def get_info(self):
        return f"{self._name} (ID: {self._employee_id})"

class HourlyEmployee(Employee):
    def __init__(self, name, employee_id, hourly_rate, hours):
        super().__init__(name, employee_id)
        self.hourly_rate = hourly_rate
        self.hours = hours
    
    @property
    def salary(self):
        return self.hourly_rate * self.hours
    
    def calculate_bonus(self):
        return self.salary * 0.05  # 5% bonus

class SalariedEmployee(Employee):
    def __init__(self, name, employee_id, annual_salary):
        super().__init__(name, employee_id)
        self.annual_salary = annual_salary
    
    @property
    def salary(self):
        return self.annual_salary / 12  # Monthly
    
    def calculate_bonus(self):
        return self.annual_salary * 0.10  # 10% bonus

# Both work the same way
emp1 = HourlyEmployee("Alice", "E001", 25, 160)
emp2 = SalariedEmployee("Bob", "E002", 60000)

print(f"{emp1.get_info()}: ${emp1.salary:.2f} + ${emp1.calculate_bonus():.2f} bonus")
print(f"{emp2.get_info()}: ${emp2.salary:.2f} + ${emp2.calculate_bonus():.2f} bonus")
```

### Interface-like ABC

```python
from abc import ABC, abstractmethod

class DatabaseInterface(ABC):
    """Defines interface for database operations"""
    
    @abstractmethod
    def connect(self, connection_string):
        pass
    
    @abstractmethod
    def disconnect(self):
        pass
    
    @abstractmethod
    def execute_query(self, query):
        pass
    
    @abstractmethod
    def fetch_all(self):
        pass

class MySQLDatabase(DatabaseInterface):
    def __init__(self):
        self.connection = None
    
    def connect(self, connection_string):
        print(f"Connecting to MySQL: {connection_string}")
        self.connection = "MySQL Connection"
    
    def disconnect(self):
        print("Disconnecting from MySQL")
        self.connection = None
    
    def execute_query(self, query):
        print(f"MySQL executing: {query}")
    
    def fetch_all(self):
        return ["row1", "row2", "row3"]

class PostgreSQLDatabase(DatabaseInterface):
    def __init__(self):
        self.connection = None
    
    def connect(self, connection_string):
        print(f"Connecting to PostgreSQL: {connection_string}")
        self.connection = "PostgreSQL Connection"
    
    def disconnect(self):
        print("Disconnecting from PostgreSQL")
        self.connection = None
    
    def execute_query(self, query):
        print(f"PostgreSQL executing: {query}")
    
    def fetch_all(self):
        return ["record1", "record2", "record3"]

def perform_database_operations(db: DatabaseInterface):
    """Works with any DatabaseInterface implementation"""
    db.connect("server=localhost;database=mydb")
    db.execute_query("SELECT * FROM users")
    results = db.fetch_all()
    print(f"Retrieved {len(results)} results")
    db.disconnect()

# Both can be used interchangeably
mysql_db = MySQLDatabase()
postgres_db = PostgreSQLDatabase()

perform_database_operations(mysql_db)
print()
perform_database_operations(postgres_db)
```

### Multiple Abstract Methods

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start_engine(self):
        pass
    
    @abstractmethod
    def stop_engine(self):
        pass
    
    @abstractmethod
    def accelerate(self, speed):
        pass
    
    @abstractmethod
    def brake(self):
        pass
    
    @abstractmethod
    def get_fuel_level(self):
        pass

class Car(Vehicle):
    def __init__(self, make, model):
        self.make = make
        self.model = model
        self.engine_running = False
        self.speed = 0
        self.fuel_level = 100
    
    def start_engine(self):
        self.engine_running = True
        print(f"{self.make} {self.model} engine started")
    
    def stop_engine(self):
        self.engine_running = False
        self.speed = 0
        print(f"{self.make} {self.model} engine stopped")
    
    def accelerate(self, speed):
        if self.engine_running:
            self.speed += speed
            self.fuel_level -= speed * 0.1
            print(f"Accelerating to {self.speed} mph")
    
    def brake(self):
        self.speed = max(0, self.speed - 10)
        print(f"Braking, speed now {self.speed} mph")
    
    def get_fuel_level(self):
        return self.fuel_level

class ElectricCar(Vehicle):
    def __init__(self, make, model):
        self.make = make
        self.model = model
        self.power_on = False
        self.speed = 0
        self.battery_level = 100
    
    def start_engine(self):
        self.power_on = True
        print(f"{self.make} {self.model} powered on (silent)")
    
    def stop_engine(self):
        self.power_on = False
        self.speed = 0
        print(f"{self.make} {self.model} powered off")
    
    def accelerate(self, speed):
        if self.power_on:
            self.speed += speed
            self.battery_level -= speed * 0.2
            print(f"Accelerating to {self.speed} mph (electric)")
    
    def brake(self):
        self.speed = max(0, self.speed - 10)
        self.battery_level += 1  # Regenerative braking!
        print(f"Braking, speed now {self.speed} mph (regen +1%)")
    
    def get_fuel_level(self):
        return self.battery_level

def test_drive(vehicle: Vehicle):
    """Test drive any vehicle"""
    vehicle.start_engine()
    vehicle.accelerate(30)
    vehicle.accelerate(20)
    print(f"Fuel/Battery: {vehicle.get_fuel_level():.1f}%")
    vehicle.brake()
    vehicle.stop_engine()

car = Car("Toyota", "Camry")
electric = ElectricCar("Tesla", "Model 3")

test_drive(car)
print()
test_drive(electric)
```

**Practice** (45 min):

**Exercise 5.4**: Payment Processor Interface
```python
# Create an abstract payment processing system:
# 
# Abstract Base Class: PaymentProcessor
#   Abstract methods:
#     - validate_payment_details()
#     - process_transaction(amount)
#     - refund_transaction(transaction_id)
#     - get_transaction_fee(amount)
#     - generate_receipt(transaction)
#   
#   Abstract property:
#     - provider_name
# 
# Concrete subclasses:
#   - CreditCardProcessor
#   - PayPalProcessor
#   - CryptocurrencyProcessor
#   - BankTransferProcessor
# 
# Each should implement all abstract methods differently
# Create function that works with any processor
```

**Exercise 5.5**: Data Storage Interface
```python
# Create abstract data storage system:
# 
# Abstract Base Class: DataStore
#   Abstract methods:
#     - connect()
#     - disconnect()
#     - save(key, value)
#     - load(key)
#     - delete(key)
#     - exists(key)
#     - list_all_keys()
#   
#   Concrete methods:
#     - get_connection_status()
# 
# Implementations:
#   - FileDataStore - saves to files
#   - MemoryDataStore - saves to dictionary
#   - SQLDataStore - saves to database (simulated)
# 
# Demonstrate that all three work identically from user perspective
```

**Exercise 5.6**: Logger Interface
```python
# Create abstract logging system:
# 
# Abstract Base Class: Logger
#   Abstract methods:
#     - log_info(message)
#     - log_warning(message)
#     - log_error(message)
#     - log_debug(message)
#     - flush() - write buffered logs
#   
#   Abstract property:
#     - log_level (property that can be get/set)
#   
#   Concrete methods:
#     - should_log(level) - checks if level should be logged
# 
# Implementations:
#   - FileLogger - logs to file
#   - ConsoleLogger - logs to console
#   - NetworkLogger - sends logs over network (simulated)
#   - MultiLogger - logs to multiple destinations
# 
# Create application that uses logger polymorphically
```

---

## Day 27: Multiple Inheritance

**Concepts** (45 min):

### Basic Multiple Inheritance

A class can inherit from multiple parent classes.

```python
class Flyable:
    def fly(self):
        print(f"{self.name} is flying")
    
    def land(self):
        print(f"{self.name} is landing")

class Swimmable:
    def swim(self):
        print(f"{self.name} is swimming")
    
    def dive(self):
        print(f"{self.name} is diving")

class Duck:
    def __init__(self, name):
        self.name = name

class WaterBird(Duck, Flyable, Swimmable):
    """Inherits from three classes"""
    def __init__(self, name):
        super().__init__(name)

# Duck can fly AND swim
duck = WaterBird("Donald")
duck.fly()   # from Flyable
duck.swim()  # from Swimmable
duck.land()  # from Flyable
duck.dive()  # from Swimmable
```

### Diamond Problem and MRO

```python
class A:
    def method(self):
        print("A.method")

class B(A):
    def method(self):
        print("B.method")
        super().method()

class C(A):
    def method(self):
        print("C.method")
        super().method()

class D(B, C):
    def method(self):
        print("D.method")
        super().method()

# Method Resolution Order (MRO)
print(D.__mro__)
# (<class 'D'>, <class 'B'>, <class 'C'>, <class 'A'>, <class 'object'>)

d = D()
d.method()
# Output:
# D.method
# B.method
# C.method
# A.method
```

### Mixins

Mixins are classes designed to add functionality to other classes through multiple inheritance.

```python
class TimestampMixin:
    """Add timestamp functionality to any class"""
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        from datetime import datetime
        self.created_at = datetime.now()
        self.updated_at = datetime.now()
    
    def touch(self):
        """Update the updated_at timestamp"""
        from datetime import datetime
        self.updated_at = datetime.now()
    
    def get_age(self):
        """Return age in seconds"""
        from datetime import datetime
        return (datetime.now() - self.created_at).total_seconds()

class SerializableMixin:
    """Add serialization functionality"""
    def to_dict(self):
        """Convert object to dictionary"""
        result = {}
        for key, value in self.__dict__.items():
            if not key.startswith('_'):
                result[key] = str(value)
        return result
    
    def from_dict(self, data):
        """Load object from dictionary"""
        for key, value in data.items():
            if hasattr(self, key):
                setattr(self, key, value)

class PrintableMixin:
    """Add pretty printing"""
    def pretty_print(self):
        print("=" * 50)
        print(f"{self.__class__.__name__} Object")
        print("=" * 50)
        for key, value in self.__dict__.items():
            if not key.startswith('_'):
                print(f"{key:<20}: {value}")
        print("=" * 50)

# Use mixins to enhance a class
class User(TimestampMixin, SerializableMixin, PrintableMixin):
    def __init__(self, username, email):
        super().__init__()  # Important for mixins!
        self.username = username
        self.email = email

# User now has all mixin functionality
user = User("alice", "alice@example.com")
user.pretty_print()

import time
time.sleep(2)
print(f"Age: {user.get_age():.2f} seconds")

user_dict = user.to_dict()
print(f"\nSerialized: {user_dict}")
```

### Practical Example: Enhanced Database Model

```python
class ValidationMixin:
    """Mixin for data validation"""
    def validate(self):
        """Override in subclass for custom validation"""
        errors = []
        
        # Check required fields
        if hasattr(self, 'required_fields'):
            for field in self.required_fields:
                if not hasattr(self, field) or getattr(self, field) is None:
                    errors.append(f"Missing required field: {field}")
        
        return errors
    
    def is_valid(self):
        return len(self.validate()) == 0

class AuditMixin:
    """Mixin for audit trail"""
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.audit_log = []
    
    def log_change(self, field, old_value, new_value):
        from datetime import datetime
        self.audit_log.append({
            'timestamp': datetime.now(),
            'field': field,
            'old_value': old_value,
            'new_value': new_value
        })
    
    def get_audit_trail(self):
        for entry in self.audit_log:
            print(f"{entry['timestamp']}: {entry['field']} changed "
                  f"from {entry['old_value']} to {entry['new_value']}")

class SoftDeleteMixin:
    """Mixin for soft delete functionality"""
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.is_deleted = False
        self.deleted_at = None
    
    def delete(self):
        """Soft delete - mark as deleted"""
        from datetime import datetime
        self.is_deleted = True
        self.deleted_at = datetime.now()
    
    def restore(self):
        """Restore soft-deleted item"""
        self.is_deleted = False
        self.deleted_at = None
    
    def is_active(self):
        return not self.is_deleted

class BaseModel:
    """Base class for all models"""
    def __init__(self):
        self.id = None

# Combine everything
class Product(BaseModel, ValidationMixin, AuditMixin, SoftDeleteMixin, 
              SerializableMixin, TimestampMixin, PrintableMixin):
    
    required_fields = ['name', 'price', 'sku']
    
    def __init__(self, name, price, sku):
        super().__init__()
        self.name = name
        self.price = price
        self.sku = sku
    
    def update_price(self, new_price):
        old_price = self.price
        self.price = new_price
        self.log_change('price', old_price, new_price)
        self.touch()  # From TimestampMixin

# Product now has ALL the functionality
product = Product("Laptop", 999.99, "LAP-001")

# Validation
if product.is_valid():
    print("Product is valid")

# Audit trail
product.update_price(899.99)
product.update_price(849.99)
product.get_audit_trail()

# Soft delete
product.delete()
print(f"Active: {product.is_active()}")

# Pretty print
product.pretty_print()
```

**Practice** (45 min):

**Exercise 5.7**: Enhanced Employee System
```python
# Create employee system with multiple mixins:
# 
# Mixins to create:
#   1. ContactInfoMixin - email, phone, address methods
#   2. PermissionsMixin - roles, permissions checking
#   3. SalaryMixin - salary calculations, tax, bonuses
#   4. AttendanceMixin - clock in/out, hours tracking
# 
# Base Classes:
#   - Person (basic info)
#   - Employee (inherits Person + all mixins)
# 
# Employee Types:
#   - FullTimeEmployee
#   - PartTimeEmployee
#   - ContractEmployee
# 
# Each employee type uses different mixin features differently
# Demonstrate MRO and super() chains
```

**Exercise 5.8**: Social Media Post System
```python
# Create social media post system with mixins:
# 
# Mixins:
#   1. LikeableMixin - like(), unlike(), get_like_count()
#   2. CommentableMixin - add_comment(), delete_comment(), get_comments()
#   3. ShareableMixin - share(), get_share_count()
#   4. ReportableMixin - report(), is_flagged()
# 
# Base Class:
#   - Post(content, author, timestamp)
# 
# Post Types (inherit Post + different mixins):
#   - TextPost (all mixins)
#   - PhotoPost (all mixins + photo-specific methods)
#   - VideoPost (all mixins + video-specific methods)
#   - StoryPost (likeable only, disappears after 24h)
# 
# Demonstrate polymorphic handling of different post types
```

**Exercise 5.9**: Game Character with Abilities
```python
# Create game character with ability mixins:
# 
# Mixins:
#   1. CombatMixin - attack(), defend(), health management
#   2. MagicMixin - cast_spell(), mana management
#   3. StealthMixin - hide(), sneak(), detection
#   4. CraftingMixin - craft_item(), gather_resources()
# 
# Base Class:
#   - Character(name, level, experience)
# 
# Character Classes (different mixin combinations):
#   - Warrior (Combat)
#   - Mage (Magic, weak Combat)
#   - Rogue (Stealth, Combat)
#   - Ranger (Combat, Stealth, Crafting)
#   - Paladin (Combat, Magic)
# 
# Demonstrate how different combinations create different gameplay
# Show MRO for each character class
```

---

## Day 28: Composition vs Inheritance

**Concepts** (45 min):

### Understanding Composition

Composition means "has-a" relationship instead of "is-a". Objects contain other objects as attributes.

```python
# Inheritance approach ("is-a")
class ElectricGuitar:
    def __init__(self):
        self.strings = 6
        self.has_amplifier = True
    
    def play_loud(self):
        print("Electric guitar plays LOUD!")

# Composition approach ("has-a")
class Amplifier:
    def __init__(self, wattage):
        self.wattage = wattage
        self.volume = 5
    
    def turn_up(self):
        self.volume = min(10, self.volume + 1)
    
    def turn_down(self):
        self.volume = max(0, self.volume - 1)

class Guitar:
    def __init__(self, strings=6):
        self.strings = strings
        self.amplifier = None  # Composition
    
    def plug_in(self, amplifier):
        self.amplifier = amplifier
    
    def play(self):
        if self.amplifier:
            print(f"Playing through {self.amplifier.wattage}W amp "
                  f"at volume {self.amplifier.volume}")
        else:
            print("Playing acoustic")

# Using composition
guitar = Guitar()
amp = Amplifier(100)
guitar.plug_in(amp)
amp.turn_up()
guitar.play()
```

### When to Use Composition

```python
# BAD: Using inheritance for "has-a" relationship
class CarWithEngine:
    """Wrong - Car is-a Engine? No!"""
    def __init__(self):
        self.horsepower = 200
    
    def start_engine(self):
        print("Engine started")

# GOOD: Using composition
class Engine:
    def __init__(self, horsepower, fuel_type):
        self.horsepower = horsepower
        self.fuel_type = fuel_type
        self.running = False
    
    def start(self):
        self.running = True
        print(f"{self.horsepower}HP {self.fuel_type} engine started")
    
    def stop(self):
        self.running = False
        print("Engine stopped")

class Car:
    def __init__(self, make, model, engine):
        self.make = make
        self.model = model
        self.engine = engine  # Composition!
    
    def start(self):
        print(f"Starting {self.make} {self.model}")
        self.engine.start()
    
    def stop(self):
        self.engine.stop()
        print(f"{self.make} {self.model} stopped")

# Using composition
v8_engine = Engine(400, "Gasoline")
mustang = Car("Ford", "Mustang", v8_engine)
mustang.start()
```

### Complex Composition Example

```python
class CPU:
    def __init__(self, cores, speed):
        self.cores = cores
        self.speed = speed  # GHz
    
    def process(self, task):
        print(f"Processing {task} on {self.cores} cores at {self.speed}GHz")

class RAM:
    def __init__(self, size):
        self.size = size  # GB
        self.used = 0
    
    def allocate(self, amount):
        if self.used + amount <= self.size:
            self.used += amount
            return True
        return False
    
    def get_available(self):
        return self.size - self.used

class Storage:
    def __init__(self, capacity, storage_type):
        self.capacity = capacity  # GB
        self.storage_type = storage_type  # "SSD" or "HDD"
        self.used = 0
    
    def write(self, data_size):
        if self.used + data_size <= self.capacity:
            self.used += data_size
            speed = "fast" if self.storage_type == "SSD" else "normal"
            print(f"Writing {data_size}GB to {self.storage_type} ({speed})")
            return True
        return False

class Computer:
    def __init__(self, name, cpu, ram, storage):
        self.name = name
        self.cpu = cpu        # Composition
        self.ram = ram        # Composition
        self.storage = storage  # Composition
        self.powered_on = False
    
    def power_on(self):
        self.powered_on = True
        print(f"\n{self.name} is powering on...")
        print(f"CPU: {self.cpu.cores} cores @ {self.cpu.speed}GHz")
        print(f"RAM: {self.ram.size}GB")
        print(f"Storage: {self.storage.capacity}GB {self.storage.storage_type}")
    
    def run_application(self, app_name, ram_needed, storage_needed):
        if not self.powered_on:
            print("Computer is off!")
            return False
        
        print(f"\nRunning {app_name}...")
        
        if self.ram.allocate(ram_needed):
            print(f"Allocated {ram_needed}GB RAM")
        else:
            print(f"Insufficient RAM! Available: {self.ram.get_available()}GB")
            return False
        
        if self.storage.write(storage_needed):
            print(f"Saved {storage_needed}GB to storage")
        else:
            print("Insufficient storage!")
            return False
        
        self.cpu.process(app_name)
        return True
    
    def get_specs(self):
        return {
            "name": self.name,
            "cpu_cores": self.cpu.cores,
            "cpu_speed": self.cpu.speed,
            "ram": self.ram.size,
            "storage": self.storage.capacity,
            "storage_type": self.storage.storage_type
        }

# Build computers using composition
cpu1 = CPU(8, 3.5)
ram1 = RAM(16)
storage1 = Storage(512, "SSD")
gaming_pc = Computer("Gaming Beast", cpu1, ram1, storage1)

cpu2 = CPU(4, 2.4)
ram2 = RAM(8)
storage2 = Storage(256, "SSD")
laptop = Computer("Work Laptop", cpu2, ram2, storage2)

# Use the computers
gaming_pc.power_on()
gaming_pc.run_application("Cyberpunk 2077", 12, 100)

laptop.power_on()
laptop.run_application("VS Code", 2, 1)
```

### Combining Inheritance and Composition

```python
class Weapon:
    def __init__(self, name, damage):
        self.name = name
        self.damage = damage
    
    def attack(self):
        return self.damage

class Armor:
    def __init__(self, name, defense):
        self.name = name
        self.defense = defense
    
    def block(self, damage):
        return max(0, damage - self.defense)

class GameCharacter:
    """Base class using inheritance"""
    def __init__(self, name, health):
        self.name = name
        self.health = health
        self.max_health = health
        self.weapon = None     # Composition
        self.armor = None      # Composition
    
    def equip_weapon(self, weapon):
        self.weapon = weapon
        print(f"{self.name} equipped {weapon.name}")
    
    def equip_armor(self, armor):
        self.armor = armor
        print(f"{self.name} equipped {armor.name}")
    
    def attack(self, target):
        if not self.weapon:
            damage = 5  # Bare hands
        else:
            damage = self.weapon.attack()
        
        target.take_damage(damage)
    
    def take_damage(self, damage):
        if self.armor:
            damage = self.armor.block(damage)
        
        self.health -= damage
        print(f"{self.name} takes {damage} damage! Health: {self.health}/{self.max_health}")

class Warrior(GameCharacter):
    """Inheritance for specialization"""
    def __init__(self, name):
        super().__init__(name, 150)  # More health
        self.rage = 0
    
    def battle_cry(self):
        self.rage += 20
        print(f"{self.name} lets out a battle cry! Rage: {self.rage}")
    
    def attack(self, target):
        # Override to use rage
        super().attack(target)
        if self.rage >= 50:
            print(f"{self.name} performs RAGE ATTACK!")
            super().attack(target)
            self.rage = 0

class Mage(GameCharacter):
    """Different specialization"""
    def __init__(self, name):
        super().__init__(name, 80)  # Less health
        self.mana = 100
    
    def cast_spell(self, target, spell_cost=20):
        if self.mana >= spell_cost:
            self.mana -= spell_cost
            magic_damage = 30
            target.take_damage(magic_damage)
            print(f"{self.name} casts spell! Mana: {self.mana}")
        else:
            print(f"{self.name} has insufficient mana!")

# Create weapons and armor (composition)
sword = Weapon("Excalibur", 25)
staff = Weapon("Elder Staff", 15)
plate_armor = Armor("Plate Mail", 15)
robe = Armor("Mystic Robe", 5)

# Create characters (inheritance)
warrior = Warrior("Conan")
mage = Mage("Gandalf")

# Combine both
warrior.equip_weapon(sword)
warrior.equip_armor(plate_armor)

mage.equip_weapon(staff)
mage.equip_armor(robe)

# Battle!
warrior.battle_cry()
warrior.attack(mage)
mage.cast_spell(warrior)
```

**Practice** (45 min):

**Exercise 5.10**: Smart Home System
```python
# Design a smart home system using composition:
# 
# Component Classes:
#   - Light(brightness, color)
#   - Thermostat(current_temp, target_temp)
#   - SecurityCamera(location, recording)
#   - DoorLock(is_locked)
#   - Speaker(volume, playing)
# 
# Room Class (uses composition):
#   - Room(name, lights, thermostat, cameras, locks, speakers)
#   - Methods: turn_on_lights(), set_temperature(), etc.
# 
# House Class (contains rooms):
#   - House(address, rooms)
#   - Methods: secure_all(), comfort_mode(), away_mode()
# 
# Demonstrate composition over inheritance
# Show how components can be reused across rooms
```

**Exercise 5.11**: Restaurant Order System
```python
# Create restaurant system using composition:
# 
# Component Classes:
#   - MenuItem(name, price, category, prep_time)
#   - Ingredient(name, quantity, unit)
#   - Chef(name, specialty, orders_completed)
#   - Server(name, tables, tips)
# 
# Composed Classes:
#   - Order(order_id, items, table_number, server)
#     - add_item(), remove_item(), calculate_total()
#   - Kitchen(chefs, pending_orders, completed_orders)
#     - assign_order(), complete_order()
#   - Restaurant(name, menu, kitchen, servers, orders)
#     - place_order(), process_orders(), generate_report()
# 
# Show how composition makes system flexible
# Demonstrate replacing components (e.g., different chefs)
```

**Exercise 5.12**: University Course System
```python
# Design university system with composition:
# 
# Component Classes:
#   - Professor(name, department, courses_taught)
#   - Student(name, student_id, enrolled_courses)
#   - Textbook(title, isbn, price)
#   - Classroom(building, room_number, capacity)
# 
# Composed Classes:
#   - Course(code, title, professor, textbooks, classroom, students)
#     - enroll_student(), drop_student(), get_enrollment()
#   - Department(name, professors, courses)
#     - add_course(), assign_professor()
#   - University(name, departments, students)
#     - register_student(), create_course(), generate_schedule()
# 
# Compare to inheritance approach - show why composition is better
# Demonstrate flexibility of composition
```

---

## Day 29: Design Principles (SOLID Introduction)

**Concepts** (45 min):

### Single Responsibility Principle (SRP)

Each class should have one, and only one, reason to change.

```python
# BAD: Class has multiple responsibilities
class UserManager:
    def __init__(self):
        self.users = []
    
    def add_user(self, user):
        self.users.append(user)
    
    def save_to_database(self, user):
        # Database logic here
        print(f"Saving {user} to database")
    
    def send_welcome_email(self, user):
        # Email logic here
        print(f"Sending email to {user}")
    
    def generate_report(self):
        # Reporting logic here
        print("Generating user report")

# GOOD: Each class has single responsibility
class User:
    def __init__(self, username, email):
        self.username = username
        self.email = email

class UserRepository:
    """Responsible ONLY for data storage"""
    def __init__(self):
        self.users = []
    
    def add(self, user):
        self.users.append(user)
    
    def get_all(self):
        return self.users
    
    def find_by_username(self, username):
        for user in self.users:
            if user.username == username:
                return user
        return None

class EmailService:
    """Responsible ONLY for sending emails"""
    def send_welcome_email(self, user):
        print(f"Sending welcome email to {user.email}")
    
    def send_notification(self, user, message):
        print(f"Sending notification to {user.email}: {message}")

class UserReportGenerator:
    """Responsible ONLY for generating reports"""
    def __init__(self, user_repository):
        self.user_repository = user_repository
    
    def generate_user_report(self):
        users = self.user_repository.get_all()
        print(f"User Report: {len(users)} total users")
        for user in users:
            print(f"  - {user.username} ({user.email})")

# Usage with SRP
repo = UserRepository()
email_service = EmailService()
report_gen = UserReportGenerator(repo)

user = User("alice", "alice@example.com")
repo.add(user)
email_service.send_welcome_email(user)
report_gen.generate_user_report()
```

### Open/Closed Principle (OCP)

Classes should be open for extension but closed for modification.

```python
# BAD: Need to modify class to add new discount types
class BadDiscountCalculator:
    def calculate_discount(self, customer_type, amount):
        if customer_type == "regular":
            return amount * 0.05
        elif customer_type == "premium":
            return amount * 0.10
        elif customer_type == "vip":
            return amount * 0.20
        # Need to modify this method for each new type!

# GOOD: Open for extension, closed for modification
from abc import ABC, abstractmethod

class DiscountStrategy(ABC):
    @abstractmethod
    def calculate_discount(self, amount):
        pass

class RegularDiscount(DiscountStrategy):
    def calculate_discount(self, amount):
        return amount * 0.05

class PremiumDiscount(DiscountStrategy):
    def calculate_discount(self, amount):
        return amount * 0.10

class VIPDiscount(DiscountStrategy):
    def calculate_discount(self, amount):
        return amount * 0.20

class SeasonalDiscount(DiscountStrategy):
    def calculate_discount(self, amount):
        return amount * 0.15

class DiscountCalculator:
    def __init__(self, discount_strategy):
        self.discount_strategy = discount_strategy
    
    def calculate_discount(self, amount):
        return self.discount_strategy.calculate_discount(amount)

# Usage - can add new discount types without modifying existing code
regular_calc = DiscountCalculator(RegularDiscount())
print(regular_calc.calculate_discount(100))  # 5.0

vip_calc = DiscountCalculator(VIPDiscount())
print(vip_calc.calculate_discount(100))  # 20.0

# Add new type without modifying existing classes
seasonal_calc = DiscountCalculator(SeasonalDiscount())
print(seasonal_calc.calculate_discount(100))  # 15.0
```

### Liskov Substitution Principle (LSP)

Derived classes must be substitutable for their base classes.

```python
# BAD: Violates LSP
class Bird:
    def fly(self):
        print("Flying")

class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins can't fly!")  # Violates LSP!

# GOOD: Respects LSP
class Bird:
    def move(self):
        print("Moving")

class FlyingBird(Bird):
    def move(self):
        print("Flying")

class SwimmingBird(Bird):
    def move(self):
        print("Swimming")

class Sparrow(FlyingBird):
    pass

class Penguin(SwimmingBird):
    pass

# Now substitution works correctly
def make_bird_move(bird: Bird):
    bird.move()

make_bird_move(Sparrow())   # Flying
make_bird_move(Penguin())   # Swimming
```

### Interface Segregation Principle (ISP)

Clients should not be forced to depend on interfaces they don't use.

```python
# BAD: Fat interface
class Worker:
    def work(self):
        pass
    
    def eat(self):
        pass
    
    def sleep(self):
        pass

class Robot(Worker):
    def work(self):
        print("Robot working")
    
    def eat(self):
        pass  # Robots don't eat! Forced to implement unused method
    
    def sleep(self):
        pass  # Robots don't sleep! Forced to implement unused method

# GOOD: Segregated interfaces
from abc import ABC, abstractmethod

class Workable(ABC):
    @abstractmethod
    def work(self):
        pass

class Eatable(ABC):
    @abstractmethod
    def eat(self):
        pass

class Sleepable(ABC):
    @abstractmethod
    def sleep(self):
        pass

class Human(Workable, Eatable, Sleepable):
    def work(self):
        print("Human working")
    
    def eat(self):
        print("Human eating")
    
    def sleep(self):
        print("Human sleeping")

class Robot(Workable):
    def work(self):
        print("Robot working")
    # No eat() or sleep() needed!

def make_worker_work(worker: Workable):
    worker.work()

make_worker_work(Human())   # Works
make_worker_work(Robot())   # Works
```

### Dependency Inversion Principle (DIP)

High-level modules should not depend on low-level modules. Both should depend on abstractions.

```python
# BAD: High-level depends on low-level
class MySQLDatabase:
    def save(self, data):
        print(f"Saving {data} to MySQL")

class UserService:
    def __init__(self):
        self.database = MySQLDatabase()  # Tightly coupled!
    
    def save_user(self, user):
        self.database.save(user)

# GOOD: Both depend on abstraction
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def save(self, data):
        pass
    
    @abstractmethod
    def load(self, id):
        pass

class MySQLDatabase(Database):
    def save(self, data):
        print(f"Saving {data} to MySQL")
    
    def load(self, id):
        return f"Data {id} from MySQL"

class PostgreSQLDatabase(Database):
    def save(self, data):
        print(f"Saving {data} to PostgreSQL")
    
    def load(self, id):
        return f"Data {id} from PostgreSQL"

class UserService:
    def __init__(self, database: Database):
        self.database = database  # Depends on abstraction!
    
    def save_user(self, user):
        self.database.save(user)
    
    def get_user(self, user_id):
        return self.database.load(user_id)

# Can easily swap databases
mysql_service = UserService(MySQLDatabase())
mysql_service.save_user("Alice")

postgres_service = UserService(PostgreSQLDatabase())
postgres_service.save_user("Bob")
```

**Practice** (45 min):

**Exercise 5.13**: SOLID Refactoring Challenge
```python
# Given this BAD code, refactor to follow SOLID principles:
#
# class OrderProcessor:
#     def __init__(self):
#         self.orders = []
#
#     def add_order(self, order):
#         # Validation logic
#         if order.total < 0:
#             raise ValueError("Invalid order")
#         self.orders.append(order)
#
#     def calculate_tax(self, order):
#         if order.location == "CA":
#             return order.total * 0.0725
#         elif order.location == "NY":
#             return order.total * 0.08
#         return order.total * 0.06
#
#     def process_payment(self, order):
#         if order.payment_method == "credit_card":
#             print("Processing credit card")
#         elif order.payment_method == "paypal":
#             print("Processing PayPal")
#
#     def send_email(self, order):
#         print(f"Sending email confirmation for order {order.id}")
#
#     def save_to_database(self, order):
#         print(f"Saving order {order.id} to database")
#
#     def generate_invoice(self, order):
#         print(f"Generating invoice for order {order.id}")
#
# Refactor to:
# 1. Single Responsibility - separate concerns
# 2. Open/Closed - use strategy pattern for tax/payment
# 3. Liskov Substitution - proper inheritance
# 4. Interface Segregation - multiple small interfaces
# 5. Dependency Inversion - depend on abstractions
```

**Exercise 5.14**: Design a Notification System (SOLID)
```python
# Design a notification system following SOLID:
# 
# Requirements:
# - Support multiple notification types (Email, SMS, Push, Slack)
# - Different notification priorities (Low, Medium, High, Critical)
# - Ability to add new notification types without modifying existing code
# - Some users prefer certain notification types
# - High priority notifications should use multiple channels
# 
# Classes to consider:
# - NotificationChannel (abstract)
# - NotificationService (depends on abstractions)
# - NotificationRepository (for storing notifications)
# - NotificationFormatter (for formatting messages)
# - PriorityHandler (for handling priorities)
# 
# Demonstrate all SOLID principles in your design
```

**Exercise 5.15**: Logging Framework (SOLID)
```python
# Create a logging framework following SOLID:
# 
# Features needed:
# - Multiple log destinations (file, console, database, remote)
# - Multiple log levels (debug, info, warning, error, critical)
# - Log formatting (text, JSON, XML)
# - Log filtering (by level, by source, by timestamp)
# - Log rotation (file size, time-based)
# 
# Apply each SOLID principle:
# 1. SRP - separate logger, formatter, destination, filter
# 2. OCP - extensible for new destinations/formats
# 3. LSP - all destinations substitutable
# 4. ISP - separate interfaces for different features
# 5. DIP - depend on abstractions
# 
# Show how easy it is to add new functionality
```

---

## Day 30: Weekly Assignment - Week 5

**Time**: 1.4 hours  
**Due**: End of Day 30  
**Grading**: See rubric at end

### Assignment 5: SOLID Security Incident Response System

Refactor and enhance your Security Incident Management System to follow all SOLID principles. This assignment focuses on proper design patterns and architecture.

**Objectives**:
1. Apply all five SOLID principles
2. Implement polymorphism throughout
3. Use composition where appropriate
4. Create flexible, extensible architecture

### Part 1: Notification System (25 points)

Create a flexible notification system following SOLID principles:

**Interfaces (Abstract Base Classes)**:
```python
from abc import ABC, abstractmethod

class NotificationChannel(ABC):
    """ISP - Focused interface"""
    @abstractmethod
    def send(self, recipient, message):
        pass
    
    @abstractmethod
    def is_available(self):
        pass

class NotificationFormatter(ABC):
    """SRP - Separate formatting concern"""
    @abstractmethod
    def format(self, incident):
        pass

class NotificationPriority(ABC):
    """OCP - Extensible priority system"""
    @abstractmethod
    def should_notify(self, incident):
        pass
    
    @abstractmethod
    def get_channels(self):
        pass
```

**Implementations Required**:
1. **Channels** (implement NotificationChannel):
   - EmailChannel
   - SMSChannel
   - SlackChannel
   - PagerChannel (for critical)

2. **Formatters** (implement NotificationFormatter):
   - PlainTextFormatter
   - HTMLFormatter
   - JSONFormatter

3. **Priority Handlers** (implement NotificationPriority):
   - LowPriorityHandler - email only
   - MediumPriorityHandler - email + Slack
   - HighPriorityHandler - all except pager
   - CriticalPriorityHandler - all channels including pager

4. **Service** (DIP - depends on abstractions):
```python
class NotificationService:
    def __init__(self, channels: list[NotificationChannel], 
                 formatter: NotificationFormatter):
        self.channels = channels  # DIP!
        self.formatter = formatter
    
    def notify(self, incident, recipients):
        """Send notifications through all channels"""
        pass
    
    def add_channel(self, channel):
        """OCP - can add channels without modification"""
        pass
```

### Part 2: Incident Analysis Pipeline (25 points)

Create an analysis pipeline using composition and polymorphism:

**Component Classes**:
```python
class IncidentAnalyzer(ABC):
    """Analyze incidents"""
    @abstractmethod
    def analyze(self, incident):
        """Return dict with analysis results"""
        pass

class SeverityAnalyzer(IncidentAnalyzer):
    """Calculate severity score"""
    pass

class ImpactAnalyzer(IncidentAnalyzer):
    """Assess business impact"""
    pass

class ThreatAnalyzer(IncidentAnalyzer):
    """Identify threat indicators"""
    pass

class ComplianceAnalyzer(IncidentAnalyzer):
    """Check compliance requirements"""
    pass
```

**Pipeline Class (Composition)**:
```python
class AnalysisPipeline:
    def __init__(self, analyzers: list[IncidentAnalyzer]):
        self.analyzers = analyzers  # Composition!
    
    def analyze_incident(self, incident):
        """Run all analyzers and aggregate results"""
        results = {}
        for analyzer in self.analyzers:
            results.update(analyzer.analyze(incident))
        return results
    
    def add_analyzer(self, analyzer):
        """OCP - extensible"""
        self.analyzers.append(analyzer)
```

### Part 3: Response Automation (25 points)

Implement automated response system:

**Strategy Pattern for Responses**:
```python
class ResponseStrategy(ABC):
    @abstractmethod
    def execute(self, incident):
        """Execute response actions"""
        pass
    
    @abstractmethod
    def can_automate(self, incident):
        """Check if can be automated"""
        pass

class IsolateSystemStrategy(ResponseStrategy):
    """Automatically isolate affected systems"""
    pass

class BlockIPStrategy(ResponseStrategy):
    """Automatically block malicious IPs"""
    pass

class QuarantineFileStrategy(ResponseStrategy):
    """Quarantine malicious files"""
    pass

class NotifyTeamStrategy(ResponseStrategy):
    """Notify response team"""
    pass

class ResponseAutomation:
    def __init__(self):
        self.strategies = {}  # incident_type -> list of strategies
    
    def register_strategy(self, incident_type, strategy):
        """Register strategy for incident type"""
        pass
    
    def auto_respond(self, incident):
        """Execute appropriate strategies"""
        pass
```

### Part 4: Reporting System (15 points)

Create flexible reporting using polymorphism:

**Report Generators**:
```python
class ReportGenerator(ABC):
    @abstractmethod
    def generate(self, data):
        """Generate report from data"""
        pass

class IncidentSummaryReport(ReportGenerator):
    """Executive summary"""
    pass

class DetailedIncidentReport(ReportGenerator):
    """Technical details"""
    pass

class ComplianceReport(ReportGenerator):
    """Regulatory compliance"""
    pass

class MetricsReport(ReportGenerator):
    """Performance metrics"""
    pass

class ReportFactory:
    """Factory for creating reports"""
    @staticmethod
    def create_report(report_type):
        pass
```

### Part 5: Integration and Demonstration (10 points)

**Main System Class**:
```python
class EnhancedSOC:
    def __init__(self, 
                 notification_service: NotificationService,
                 analysis_pipeline: AnalysisPipeline,
                 response_automation: ResponseAutomation):
        # DIP - depends on abstractions!
        self.notification_service = notification_service
        self.analysis_pipeline = analysis_pipeline
        self.response_automation = response_automation
        self.incidents = []
    
    def handle_incident(self, incident):
        """Complete incident handling workflow"""
        # 1. Analyze
        analysis = self.analysis_pipeline.analyze_incident(incident)
        incident.analysis_results = analysis
        
        # 2. Auto-respond
        self.response_automation.auto_respond(incident)
        
        # 3. Notify
        priority = self._determine_priority(analysis)
        self.notification_service.notify(incident, priority)
        
        # 4. Store
        self.incidents.append(incident)
```

**Demonstration Requirements**:
1. Create diverse incidents (malware, network, data breach)
2. Show different notification paths based on severity
3. Demonstrate analysis pipeline with multiple analyzers
4. Show automated responses
5. Generate different report types
6. Prove extensibility - add new feature without modifying existing code

**Example Output**:
```
========================================
SOLID SOC - INCIDENT PROCESSING
========================================

Processing Incident: Ransomware Attack
----------------------------------------
ANALYSIS PHASE:
  Severity Analyzer: Score 95/100 (CRITICAL)
  Impact Analyzer: Business-critical systems affected
  Threat Analyzer: Known ransomware family detected
  Compliance Analyzer: GDPR notification required

AUTOMATED RESPONSE:
  ✓ Isolated 3 affected systems
  ✓ Blocked C2 server IP: 192.168.1.100
  ✓ Quarantined malicious files: ransomware.exe

NOTIFICATIONS SENT:
  [CRITICAL] Priority Handler Active
  ✓ Email sent to: security@company.com
  ✓ SMS sent to: +1-555-0123
  ✓ Slack alert: #security-incidents
  ✓ Pager alert: On-call team

REPORTS GENERATED:
  ✓ Executive Summary (HTML)
  ✓ Technical Details (PDF)
  ✓ Compliance Report (JSON)

========================================
EXTENSIBILITY DEMONSTRATION:
========================================

Adding new analyzer without modifying existing code...
✓ Added: GeolocationAnalyzer

Adding new notification channel...
✓ Added: TeamsChannel

Adding new response strategy...
✓ Added: BackupSystemStrategy

Reprocessing with new components...
[All new components integrated successfully]
========================================
```

---

### Grading Rubric - Week 5 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **SOLID Principles** | 40 | |
| Single Responsibility | 8 | Each class has one clear purpose |
| Open/Closed | 8 | Extensible without modification |
| Liskov Substitution | 8 | Subtypes fully substitutable |
| Interface Segregation | 8 | Focused, single-purpose interfaces |
| Dependency Inversion | 8 | Depends on abstractions, not concretions |
| **Notification System** | 25 | |
| Channel implementations | 10 | All channels work correctly |
| Formatters | 5 | Multiple formats supported |
| Priority handling | 10 | Appropriate channels per priority |
| **Analysis Pipeline** | 25 | |
| Analyzer components | 15 | All analyzers implemented correctly |
| Pipeline composition | 10 | Proper use of composition |
| **Response Automation** | 10 | |
| Strategy pattern | 5 | Correct strategy implementation |
| Automation logic | 5 | Appropriate automated responses |
| **Bonus** | +30 | See bonus challenges below |

**Code Quality Expectations**:
- No code duplication
- Proper use of ABCs and `@abstractmethod`
- Type hints for method parameters
- Comprehensive docstrings
- Clear demonstration of each SOLID principle
- Comments explaining design decisions

**Bonus Challenges** (+6 points each):

1. **Decorator Pattern**: Implement notification decorators (retry, rate-limiting, logging)
2. **Observer Pattern**: Add observer system for incident state changes
3. **Command Pattern**: Implement undo/redo for response actions
4. **Factory Pattern**: Advanced factory for creating complex objects
5. **Singleton Pattern**: Thread-safe singleton for configuration management

**Testing Requirements**:
- [ ] Can add new notification channel without modifying existing code
- [ ] Can add new analyzer without modifying pipeline
- [ ] All notification channels work polymorphically
- [ ] Priority handling routes to correct channels
- [ ] Analysis pipeline aggregates results correctly
- [ ] Automated responses execute appropriately
- [ ] Reports generate in multiple formats
- [ ] Dependency injection works throughout
- [ ] LSP holds for all inheritance hierarchies
- [ ] ISP demonstrated with focused interfaces

**Documentation Requirements**:
- Explain each SOLID principle application in comments
- Document design decisions
- Show class diagrams (ASCII art acceptable)
- Provide examples of extensibility

**Submission**:
- Save as `week5_assignment.py`
- Include SOLID_PRINCIPLES.md explaining how each principle is applied
- Demonstrate adding new functionality without modification

</details>

---

<details>
<summary><h1>Week 6: Advanced OOP Patterns</h1></summary>

**Focus**: Design Patterns, Advanced Composition, Metaprogramming Basics

## Day 31 (Monday): Creational Patterns - Factory and Singleton

**Concepts** (45 min):

### Factory Pattern

Factory pattern creates objects without specifying the exact class.

```python
from abc import ABC, abstractmethod

# Product interface
class Database(ABC):
    @abstractmethod
    def connect(self):
        pass
    
    @abstractmethod
    def query(self, sql):
        pass

# Concrete products
class MySQLDatabase(Database):
    def connect(self):
        return "Connected to MySQL"
    
    def query(self, sql):
        return f"MySQL executing: {sql}"

class PostgreSQLDatabase(Database):
    def connect(self):
        return "Connected to PostgreSQL"
    
    def query(self, sql):
        return f"PostgreSQL executing: {sql}"

class SQLiteDatabase(Database):
    def connect(self):
        return "Connected to SQLite"
    
    def query(self, sql):
        return f"SQLite executing: {sql}"

# Factory
class DatabaseFactory:
    @staticmethod
    def create_database(db_type):
        """Factory method to create database objects"""
        databases = {
            'mysql': MySQLDatabase,
            'postgresql': PostgreSQLDatabase,
            'sqlite': SQLiteDatabase
        }
        
        if db_type.lower() in databases:
            return databases[db_type.lower()]()
        raise ValueError(f"Unknown database type: {db_type}")

# Usage - client doesn't need to know concrete classes
db = DatabaseFactory.create_database('mysql')
print(db.connect())
print(db.query("SELECT * FROM users"))

# Easy to switch
db = DatabaseFactory.create_database('postgresql')
print(db.connect())
```

### Singleton Pattern

Singleton ensures a class has only one instance.

```python
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# Test singleton
s1 = Singleton()
s2 = Singleton()
print(s1 is s2)  # True - same object

# Practical example: Configuration Manager
class ConfigurationManager:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
            cls._instance._initialized = False
        return cls._instance
    
    def __init__(self):
        if not self._initialized:
            self._config = {}
            self._initialized = True
    
    def set(self, key, value):
        self._config[key] = value
    
    def get(self, key, default=None):
        return self._config.get(key, default)
    
    def get_all(self):
        return self._config.copy()

# Usage
config1 = ConfigurationManager()
config1.set('database_url', 'localhost:5432')

config2 = ConfigurationManager()  # Gets same instance
print(config2.get('database_url'))  # 'localhost:5432'

print(config1 is config2)  # True
```

### Abstract Factory Pattern

Creates families of related objects.

```python
from abc import ABC, abstractmethod

# Abstract products
class Button(ABC):
    @abstractmethod
    def render(self):
        pass

class Checkbox(ABC):
    @abstractmethod
    def render(self):
        pass

# Windows products
class WindowsButton(Button):
    def render(self):
        return "[Windows Button]"

class WindowsCheckbox(Checkbox):
    def render(self):
        return "[x] Windows Checkbox"

# Mac products
class MacButton(Button):
    def render(self):
        return "( Mac Button )"

class MacCheckbox(Checkbox):
    def render(self):
        return "☑ Mac Checkbox"

# Abstract factory
class GUIFactory(ABC):
    @abstractmethod
    def create_button(self):
        pass
    
    @abstractmethod
    def create_checkbox(self):
        pass

# Concrete factories
class WindowsFactory(GUIFactory):
    def create_button(self):
        return WindowsButton()
    
    def create_checkbox(self):
        return WindowsCheckbox()

class MacFactory(GUIFactory):
    def create_button(self):
        return MacButton()
    
    def create_checkbox(self):
        return MacCheckbox()

# Application code
class Application:
    def __init__(self, factory: GUIFactory):
        self.button = factory.create_button()
        self.checkbox = factory.create_checkbox()
    
    def render(self):
        print(self.button.render())
        print(self.checkbox.render())

# Usage
import sys
platform = 'windows' if sys.platform == 'win32' else 'mac'

if platform == 'windows':
    factory = WindowsFactory()
else:
    factory = MacFactory()

app = Application(factory)
app.render()
```

**Practice** (45 min):

**Exercise 6.1**: Log Handler Factory
```python
# Create a logging system using Factory pattern:
# 
# Abstract Product: LogHandler
#   - write(message, level)
#   - format(message)
# 
# Concrete Products:
#   - FileLogHandler - writes to file
#   - ConsoleLogHandler - writes to console
#   - DatabaseLogHandler - writes to database
#   - NetworkLogHandler - sends over network
# 
# Factory: LogHandlerFactory
#   - create_handler(handler_type, config)
#   - supports: 'file', 'console', 'database', 'network'
# 
# Logger class that uses factory to create handlers
# Demonstrate creating different loggers easily
```

**Exercise 6.2**: Connection Pool Singleton
```python
# Create a database connection pool using Singleton:
# 
# ConnectionPool (Singleton):
#   - Maintains pool of database connections
#   - Max pool size: 10
#   - Methods:
#     - get_connection() - returns available connection
#     - release_connection(conn) - returns to pool
#     - get_pool_status() - shows available/in-use
# 
# Demonstrate that only one pool exists
# Show multiple parts of application using same pool
```

**Exercise 6.3**: Document Creator Abstract Factory
```python
# Create document creation system:
# 
# Products: Document, Image, Table
# 
# Families:
#   - PDF: PDFDocument, PDFImage, PDFTable
#   - Word: WordDocument, WordImage, WordTable
#   - HTML: HTMLDocument, HTMLImage, HTMLTable
# 
# Abstract Factory: DocumentFactory
# Concrete Factories: PDFFactory, WordFactory, HTMLFactory
# 
# Application creates complete documents
# Show how easy it is to switch document types
```

---

## Day 32: Structural Patterns - Adapter and Decorator

**Concepts** (45 min):

### Adapter Pattern

Adapter converts interface of a class into another interface clients expect.

```python
# Existing class with different interface
class LegacyPrinter:
    def print_document(self, text):
        print(f"Legacy printing: {text}")

# Target interface we want
class ModernPrinter:
    def print(self, document):
        print(f"Modern printing: {document}")

# Adapter
class PrinterAdapter(ModernPrinter):
    def __init__(self, legacy_printer):
        self.legacy_printer = legacy_printer
    
    def print(self, document):
        # Adapt new interface to old
        self.legacy_printer.print_document(document)

# Usage
legacy = LegacyPrinter()
adapter = PrinterAdapter(legacy)

# Client code expects ModernPrinter interface
def print_doc(printer: ModernPrinter, doc):
    printer.print(doc)

print_doc(adapter, "Hello World")  # Works with legacy through adapter
```

### Decorator Pattern

Decorator adds responsibilities to objects dynamically.

```python
# Base component
class Coffee:
    def cost(self):
        return 2.00
    
    def description(self):
        return "Coffee"

# Decorator base
class CoffeeDecorator:
    def __init__(self, coffee):
        self._coffee = coffee
    
    def cost(self):
        return self._coffee.cost()
    
    def description(self):
        return self._coffee.description()

# Concrete decorators
class Milk(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 0.50
    
    def description(self):
        return self._coffee.description() + ", Milk"

class Sugar(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 0.25
    
    def description(self):
        return self._coffee.description() + ", Sugar"

class WhippedCream(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 0.75
    
    def description(self):
        return self._coffee.description() + ", Whipped Cream"

# Usage - can stack decorators
coffee = Coffee()
print(f"{coffee.description()}: ${coffee.cost():.2f}")

coffee_with_milk = Milk(coffee)
print(f"{coffee_with_milk.description()}: ${coffee_with_milk.cost():.2f}")

# Stack multiple
fancy_coffee = WhippedCream(Sugar(Milk(coffee)))
print(f"{fancy_coffee.description()}: ${fancy_coffee.cost():.2f}")
# Coffee, Milk, Sugar, Whipped Cream: $3.50
```

### Real-World Adapter Example

```python
# Third-party libraries with different interfaces
class StripePayment:
    def make_payment(self, amount, currency, card_token):
        print(f"Stripe: Processing ${amount} {currency}")
        return {"status": "success", "transaction_id": "stripe_123"}

class PayPalPayment:
    def send_payment(self, amount, email):
        print(f"PayPal: Sending ${amount} to {email}")
        return {"success": True, "id": "paypal_456"}

# Our unified interface
class PaymentProcessor:
    def process(self, amount, details):
        raise NotImplementedError

# Adapters
class StripeAdapter(PaymentProcessor):
    def __init__(self):
        self.stripe = StripePayment()
    
    def process(self, amount, details):
        result = self.stripe.make_payment(
            amount, 
            details.get('currency', 'USD'),
            details['card_token']
        )
        return {
            'success': result['status'] == 'success',
            'transaction_id': result['transaction_id']
        }

class PayPalAdapter(PaymentProcessor):
    def __init__(self):
        self.paypal = PayPalPayment()
    
    def process(self, amount, details):
        result = self.paypal.send_payment(amount, details['email'])
        return {
            'success': result['success'],
            'transaction_id': result['id']
        }

# Client code - works with any payment processor
class ShoppingCart:
    def __init__(self, payment_processor: PaymentProcessor):
        self.payment_processor = payment_processor
        self.items = []
    
    def add_item(self, item, price):
        self.items.append({'item': item, 'price': price})
    
    def checkout(self, payment_details):
        total = sum(item['price'] for item in self.items)
        result = self.payment_processor.process(total, payment_details)
        if result['success']:
            print(f"Order complete! Transaction ID: {result['transaction_id']}")
        return result

# Usage - same interface, different providers
cart1 = ShoppingCart(StripeAdapter())
cart1.add_item("Book", 29.99)
cart1.checkout({'currency': 'USD', 'card_token': 'tok_123'})

cart2 = ShoppingCart(PayPalAdapter())
cart2.add_item("Laptop", 999.99)
cart2.checkout({'email': 'buyer@example.com'})
```

**Practice** (45 min):

**Exercise 6.4**: Data Source Adapter
```python
# Create adapters for different data sources:
# 
# Target Interface: DataSource
#   - read_data() -> dict
#   - write_data(data: dict)
# 
# Existing Classes (different interfaces):
#   - JSONFile: load_json(), save_json()
#   - SQLDatabase: query(), insert()
#   - APIClient: get(), post()
#   - CSVFile: read_csv(), write_csv()
# 
# Create adapters for each to match DataSource interface
# Demonstrate application working with all sources
```

**Exercise 6.5**: Text Formatting Decorators
```python
# Create text formatting system with decorators:
# 
# Base: Text(content)
#   - render() -> str
# 
# Decorators:
#   - Bold(text) - wraps in **text**
#   - Italic(text) - wraps in *text*
#   - Underline(text) - wraps in _text_
#   - Color(text, color) - adds color tags
#   - Link(text, url) - creates hyperlink
# 
# Stack decorators to create complex formatting
# Example: Bold(Italic(Link(Text("Click here"), "http://example.com")))
```

**Exercise 6.6**: Notification Decorator System
```python
# Enhance notification system with decorators:
# 
# Base: Notification(message)
#   - send()
# 
# Decorators:
#   - EncryptedNotification - encrypts message
#   - CompressedNotification - compresses message
#   - LoggedNotification - logs before sending
#   - RetryNotification - retries on failure
#   - RateLimitedNotification - rate limiting
# 
# Show how to combine decorators for different scenarios
# Example: Logged(Retry(Encrypted(Notification())))
```

---

## Day 33: Behavioral Patterns - Strategy and Observer

**Concepts** (45 min):

### Strategy Pattern

Strategy defines a family of algorithms and makes them interchangeable.

```python
from abc import ABC, abstractmethod

# Strategy interface
class SortStrategy(ABC):
    @abstractmethod
    def sort(self, data):
        pass

# Concrete strategies
class BubbleSort(SortStrategy):
    def sort(self, data):
        data = data.copy()
        n = len(data)
        for i in range(n):
            for j in range(0, n-i-1):
                if data[j] > data[j+1]:
                    data[j], data[j+1] = data[j+1], data[j]
        return data

class QuickSort(SortStrategy):
    def sort(self, data):
        if len(data) <= 1:
            return data
        pivot = data[len(data) // 2]
        left = [x for x in data if x < pivot]
        middle = [x for x in data if x == pivot]
        right = [x for x in data if x > pivot]
        return self.sort(left) + middle + self.sort(right)

class MergeSort(SortStrategy):
    def sort(self, data):
        if len(data) <= 1:
            return data
        mid = len(data) // 2
        left = self.sort(data[:mid])
        right = self.sort(data[mid:])
        return self._merge(left, right)
    
    def _merge(self, left, right):
        result = []
        i = j = 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                result.append(left[i])
                i += 1
            else:
                result.append(right[j])
                j += 1
        result.extend(left[i:])
        result.extend(right[j:])
        return result

# Context
class DataSorter:
    def __init__(self, strategy: SortStrategy):
        self._strategy = strategy
    
    def set_strategy(self, strategy: SortStrategy):
        self._strategy = strategy
    
    def sort(self, data):
        print(f"Sorting with {self._strategy.__class__.__name__}")
        return self._strategy.sort(data)

# Usage
data = [64, 34, 25, 12, 22, 11, 90]

sorter = DataSorter(BubbleSort())
print(sorter.sort(data))

sorter.set_strategy(QuickSort())
print(sorter.sort(data))

sorter.set_strategy(MergeSort())
print(sorter.sort(data))
```

### Observer Pattern

Observer defines one-to-many dependency so when one object changes state, all dependents are notified.

```python
from abc import ABC, abstractmethod

# Observer interface
class Observer(ABC):
    @abstractmethod
    def update(self, subject):
        pass

# Subject (Observable)
class Subject:
    def __init__(self):
        self._observers = []
        self._state = None
    
    def attach(self, observer: Observer):
        if observer not in self._observers:
            self._observers.append(observer)
    
    def detach(self, observer: Observer):
        self._observers.remove(observer)
    
    def notify(self):
        for observer in self._observers:
            observer.update(self)
    
    def set_state(self, state):
        self._state = state
        self.notify()
    
    def get_state(self):
        return self._state

# Concrete observers
class EmailObserver(Observer):
    def __init__(self, email):
        self.email = email
    
    def update(self, subject):
        print(f"Email to {self.email}: State changed to {subject.get_state()}")

class SMSObserver(Observer):
    def __init__(self, phone):
        self.phone = phone
    
    def update(self, subject):
        print(f"SMS to {self.phone}: State changed to {subject.get_state()}")

class LogObserver(Observer):
    def update(self, subject):
        print(f"LOG: State changed to {subject.get_state()}")

# Usage
subject = Subject()

email_obs = EmailObserver("user@example.com")
sms_obs = SMSObserver("+1-555-0123")
log_obs = LogObserver()

subject.attach(email_obs)
subject.attach(sms_obs)
subject.attach(log_obs)

# All observers notified
subject.set_state("Active")
subject.set_state("Inactive")

# Remove one observer
subject.detach(sms_obs)
subject.set_state("Active")  # SMS not notified
```

### Practical Example: Stock Market

```python
class Stock(Subject):
    def __init__(self, symbol, price):
        super().__init__()
        self.symbol = symbol
        self._price = price
    
    def set_price(self, price):
        print(f"\n{self.symbol} price changing: ${self._price} -> ${price}")
        self._price = price
        self._state = price
        self.notify()
    
    def get_price(self):
        return self._price

class Investor(Observer):
    def __init__(self, name):
        self.name = name
    
    def update(self, stock):
        price = stock.get_price()
        print(f"{self.name}: {stock.symbol} is now ${price}")
        if price < 100:
            print(f"  -> {self.name} is buying!")
        elif price > 150:
            print(f"  -> {self.name} is selling!")

class TradingBot(Observer):
    def __init__(self, name, buy_threshold, sell_threshold):
        self.name = name
        self.buy_threshold = buy_threshold
        self.sell_threshold = sell_threshold
    
    def update(self, stock):
        price = stock.get_price()
        if price <= self.buy_threshold:
            print(f"{self.name} BOT: AUTO-BUY at ${price}")
        elif price >= self.sell_threshold:
            print(f"{self.name} BOT: AUTO-SELL at ${price}")

# Usage
apple_stock = Stock("AAPL", 150)

investor1 = Investor("Alice")
investor2 = Investor("Bob")
bot = TradingBot("TradeBot", buy_threshold=90, sell_threshold=160)

apple_stock.attach(investor1)
apple_stock.attach(investor2)
apple_stock.attach(bot)

apple_stock.set_price(145)
apple_stock.set_price(85)   # Bot buys
apple_stock.set_price(165)  # Bot sells
```

**Practice** (45 min):

**Exercise 6.7**: Compression Strategy
```python
# Create file compression system with strategies:
# 
# Strategy interface: CompressionStrategy
#   - compress(data) -> bytes
#   - decompress(data) -> bytes
# 
# Strategies:
#   - ZipCompression
#   - GzipCompression
#   - BZ2Compression
#   - NoCompression (pass-through)
# 
# FileCompressor class:
#   - Uses strategy to compress/decompress
#   - Can change strategy at runtime
#   - Tracks compression ratio
# 
# Demonstrate different strategies on same file
```

**Exercise 6.8**: Event System with Observers
```python
# Create event-driven system:
# 
# Subject: EventBus
#   - subscribe(event_type, observer)
#   - unsubscribe(event_type, observer)
#   - publish(event_type, data)
# 
# Events: user_login, user_logout, purchase, error
# 
# Observers:
#   - AnalyticsObserver - tracks events
#   - EmailObserver - sends emails on certain events
#   - LogObserver - logs all events
#   - CacheObserver - clears cache on certain events
# 
# Demonstrate multiple observers responding to events
```

**Exercise 6.9**: Payment Processing Strategy
```python
# Create payment system with strategies:
# 
# Strategy: PaymentStrategy
#   - validate(details) -> bool
#   - process(amount, details) -> result
#   - refund(transaction_id) -> result
# 
# Strategies:
#   - CreditCardStrategy
#   - PayPalStrategy
#   - CryptocurrencyStrategy
#   - BankTransferStrategy
# 
# PaymentProcessor:
#   - Uses different strategies
#   - Logs transactions
#   - Notifies observers on successful payment
# 
# Combine Strategy and Observer patterns
```

---

## Day 34: Command and Template Method Patterns

**Concepts** (45 min):

### Command Pattern

Command encapsulates a request as an object, allowing parameterization and queuing.

```python
from abc import ABC, abstractmethod

# Receiver
class Light:
    def __init__(self, location):
        self.location = location
        self.is_on = False
    
    def turn_on(self):
        self.is_on = True
        print(f"{self.location} light is ON")
    
    def turn_off(self):
        self.is_on = False
        print(f"{self.location} light is OFF")

# Command interface
class Command(ABC):
    @abstractmethod
    def execute(self):
        pass
    
    @abstractmethod
    def undo(self):
        pass

# Concrete commands
class LightOnCommand(Command):
    def __init__(self, light):
        self.light = light
    
    def execute(self):
        self.light.turn_on()
    
    def undo(self):
        self.light.turn_off()

class LightOffCommand(Command):
    def __init__(self, light):
        self.light = light
    
    def execute(self):
        self.light.turn_off()
    
    def undo(self):
        self.light.turn_on()

# Invoker
class RemoteControl:
    def __init__(self):
        self.commands = {}
        self.history = []
    
    def set_command(self, slot, command):
        self.commands[slot] = command
    
    def press_button(self, slot):
        if slot in self.commands:
            self.commands[slot].execute()
            self.history.append(self.commands[slot])
    
    def press_undo(self):
        if self.history:
            command = self.history.pop()
            command.undo()

# Usage
living_room_light = Light("Living Room")
bedroom_light = Light("Bedroom")

remote = RemoteControl()
remote.set_command(1, LightOnCommand(living_room_light))
remote.set_command(2, LightOffCommand(living_room_light))
remote.set_command(3, LightOnCommand(bedroom_light))

remote.press_button(1)  # Living room light ON
remote.press_button(3)  # Bedroom light ON
remote.press_undo()     # Undo bedroom light
remote.press_undo()     # Undo living room light
```

### Template Method Pattern

Template method defines algorithm skeleton, letting subclasses override specific steps.

```python
from abc import ABC, abstractmethod

class DataProcessor(ABC):
    def process(self):
        """Template method - defines algorithm structure"""
        self.read_data()
        self.validate_data()
        self.transform_data()
        self.save_data()
        self.cleanup()
    
    @abstractmethod
    def read_data(self):
        pass
    
    @abstractmethod
    def transform_data(self):
        pass
    
    def validate_data(self):
        """Default implementation - can be overridden"""
        print("Validating data...")
    
    def save_data(self):
        """Default implementation"""
        print("Saving data...")
    
    def cleanup(self):
        """Hook method - optional override"""
        pass

class CSVProcessor(DataProcessor):
    def read_data(self):
        print("Reading CSV file")
        self.data = "csv_data"
    
    def transform_data(self):
        print("Transforming CSV data")
        self.data = self.data.upper()
    
    def cleanup(self):
        print("Closing CSV file")

class JSONProcessor(DataProcessor):
    def read_data(self):
        print("Reading JSON file")
        self.data = "json_data"
    
    def transform_data(self):
        print("Transforming JSON data")
        self.data = {"data": self.data}
    
    def validate_data(self):
        print("Custom JSON validation")

# Usage
csv_proc = CSVProcessor()
csv_proc.process()

print("\n")

json_proc = JSONProcessor()
json_proc.process()
```

### Practical Command Example: Text Editor

```python
class TextEditor:
    def __init__(self):
        self.text = ""
    
    def get_text(self):
        return self.text
    
    def append_text(self, text):
        self.text += text
    
    def delete_text(self, length):
        self.text = self.text[:-length] if length <= len(self.text) else ""
    
    def replace_text(self, old, new):
        self.text = self.text.replace(old, new)

class EditorCommand(ABC):
    @abstractmethod
    def execute(self):
        pass
    
    @abstractmethod
    def undo(self):
        pass

class AppendCommand(EditorCommand):
    def __init__(self, editor, text):
        self.editor = editor
        self.text = text
    
    def execute(self):
        self.editor.append_text(self.text)
    
    def undo(self):
        self.editor.delete_text(len(self.text))

class DeleteCommand(EditorCommand):
    def __init__(self, editor, length):
        self.editor = editor
        self.length = length
        self.deleted_text = ""
    
    def execute(self):
        text = self.editor.get_text()
        self.deleted_text = text[-self.length:]
        self.editor.delete_text(self.length)
    
    def undo(self):
        self.editor.append_text(self.deleted_text)

class ReplaceCommand(EditorCommand):
    def __init__(self, editor, old, new):
        self.editor = editor
        self.old = old
        self.new = new
        self.previous_text = ""
    
    def execute(self):
        self.previous_text = self.editor.get_text()
        self.editor.replace_text(self.old, self.new)
    
    def undo(self):
        self.editor.text = self.previous_text

class CommandManager:
    def __init__(self):
        self.history = []
        self.redo_stack = []
    
    def execute(self, command):
        command.execute()
        self.history.append(command)
        self.redo_stack.clear()
    
    def undo(self):
        if self.history:
            command = self.history.pop()
            command.undo()
            self.redo_stack.append(command)
    
    def redo(self):
        if self.redo_stack:
            command = self.redo_stack.pop()
            command.execute()
            self.history.append(command)

# Usage
editor = TextEditor()
manager = CommandManager()

manager.execute(AppendCommand(editor, "Hello "))
print(editor.get_text())  # "Hello "

manager.execute(AppendCommand(editor, "World"))
print(editor.get_text())  # "Hello World"

manager.execute(DeleteCommand(editor, 5))
print(editor.get_text())  # "Hello "

manager.undo()  # Undo delete
print(editor.get_text())  # "Hello World"

manager.execute(ReplaceCommand(editor, "World", "Python"))
print(editor.get_text())  # "Hello Python"

manager.undo()
print(editor.get_text())  # "Hello World"

manager.redo()
print(editor.get_text())  # "Hello Python"
```

**Practice** (45 min):

**Exercise 6.10**: Transaction System with Commands
```python
# Create banking transaction system with undo/redo:
# 
# Receiver: BankAccount(balance)
# 
# Commands:
#   - DepositCommand(account, amount)
#   - WithdrawCommand(account, amount)
#   - TransferCommand(from_account, to_account, amount)
# 
# TransactionManager:
#   - execute(command)
#   - undo() - undo last transaction
#   - redo() - redo undone transaction
#   - get_history() - show transaction history
# 
# Demonstrate complete transaction workflow
```

**Exercise 6.11**: Report Generation Template
```python
# Create report generation system with template method:
# 
# Base: ReportGenerator (template method)
#   1. gather_data() - abstract
#   2. validate_data() - default implementation
#   3. format_header() - abstract
#   4. format_body() - abstract
#   5. format_footer() - default implementation
#   6. save_report() - abstract
# 
# Concrete Generators:
#   - PDFReportGenerator
#   - ExcelReportGenerator
#   - HTMLReportGenerator
# 
# Each implements required methods differently
# Show how template enforces structure
```

**Exercise 6.12**: Game Action System
```python
# Create game action system with Command pattern:
# 
# Game: Character(position, health, inventory)
# 
# Commands:
#   - MoveCommand(character, direction, distance)
#   - AttackCommand(character, target, damage)
#   - UseItemCommand(character, item)
#   - PickupCommand(character, item)
# 
# GameEngine:
#   - execute_command(command)
#   - undo_last_action()
#   - replay_actions() - replay entire game
# 
# Create macro commands (combine multiple commands)
# Demonstrate undo/redo and replay functionality
```

---

## Day 35: Advanced Composition Techniques

**Concepts** (45 min):

### Component Trees

```python
from abc import ABC, abstractmethod

class FileSystemComponent(ABC):
    @abstractmethod
    def get_size(self):
        pass
    
    @abstractmethod
    def display(self, indent=0):
        pass

class File(FileSystemComponent):
    def __init__(self, name, size):
        self.name = name
        self.size = size
    
    def get_size(self):
        return self.size
    
    def display(self, indent=0):
        print("  " * indent + f"📄 {self.name} ({self.size} KB)")

class Directory(FileSystemComponent):
    def __init__(self, name):
        self.name = name
        self.children = []
    
    def add(self, component):
        self.children.append(component)
    
    def remove(self, component):
        self.children.remove(component)
    
    def get_size(self):
        return sum(child.get_size() for child in self.children)
    
    def display(self, indent=0):
        print("  " * indent + f"📁 {self.name}/")
        for child in self.children:
            child.display(indent + 1)

# Build tree structure
root = Directory("root")
home = Directory("home")
user = Directory("user")

root.add(home)
home.add(user)

user.add(File("document.txt", 10))
user.add(File("image.png", 500))

downloads = Directory("downloads")
user.add(downloads)
downloads.add(File("movie.mp4", 2000))
downloads.add(File("music.mp3", 5))

# Use uniformly
root.display()
print(f"Total size: {root.get_size()} KB")
```

### Fluent Interface (Method Chaining)

```python
class QueryBuilder:
    def __init__(self):
        self._select = []
        self._from = None
        self._where = []
        self._order = []
        self._limit = None
    
    def select(self, *fields):
        self._select.extend(fields)
        return self  # Return self for chaining
    
    def from_table(self, table):
        self._from = table
        return self
    
    def where(self, condition):
        self._where.append(condition)
        return self
    
    def order_by(self, field, direction="ASC"):
        self._order.append(f"{field} {direction}")
        return self
    
    def limit(self, count):
        self._limit = count
        return self
    
    def build(self):
        query = f"SELECT {', '.join(self._select)}"
        query += f" FROM {self._from}"
        if self._where:
            query += f" WHERE {' AND '.join(self._where)}"
        if self._order:
            query += f" ORDER BY {', '.join(self._order)}"
        if self._limit:
            query += f" LIMIT {self._limit}"
        return query

# Fluent usage
query = (QueryBuilder()
         .select("id", "name", "email")
         .from_table("users")
         .where("age > 18")
         .where("status = 'active'")
         .order_by("name", "ASC")
         .limit(10)
         .build())

print(query)
# SELECT id, name, email FROM users WHERE age > 18 AND status = 'active' ORDER BY name ASC LIMIT 10
```

### Builder Pattern with Composition

```python
class Pizza:
    def __init__(self):
        self.size = None
        self.crust = None
        self.toppings = []
        self.cheese = None
        self.sauce = None
    
    def __str__(self):
        desc = f"{self.size} pizza with {self.crust} crust\n"
        desc += f"Sauce: {self.sauce}\n"
        desc += f"Cheese: {self.cheese}\n"
        desc += f"Toppings: {', '.join(self.toppings) if self.toppings else 'None'}"
        return desc

class PizzaBuilder:
    def __init__(self):
        self.pizza = Pizza()
    
    def set_size(self, size):
        self.pizza.size = size
        return self
    
    def set_crust(self, crust):
        self.pizza.crust = crust
        return self
    
    def set_sauce(self, sauce):
        self.pizza.sauce = sauce
        return self
    
    def set_cheese(self, cheese):
        self.pizza.cheese = cheese
        return self
    
    def add_topping(self, topping):
        self.pizza.toppings.append(topping)
        return self
    
    def build(self):
        return self.pizza

class PizzaDirector:
    """Knows how to build common pizzas"""
    
    @staticmethod
    def make_margherita():
        return (PizzaBuilder()
                .set_size("Medium")
                .set_crust("Thin")
                .set_sauce("Tomato")
                .set_cheese("Mozzarella")
                .add_topping("Basil")
                .build())
    
    @staticmethod
    def make_pepperoni():
        return (PizzaBuilder()
                .set_size("Large")
                .set_crust("Regular")
                .set_sauce("Tomato")
                .set_cheese("Mozzarella")
                .add_topping("Pepperoni")
                .build())
    
    @staticmethod
    def make_veggie():
        return (PizzaBuilder()
                .set_size("Medium")
                .set_crust("Whole Wheat")
                .set_sauce("Tomato")
                .set_cheese("Mozzarella")
                .add_topping("Mushrooms")
                .add_topping("Peppers")
                .add_topping("Onions")
                .add_topping("Olives")
                .build())

# Usage
# Custom pizza
custom = (PizzaBuilder()
          .set_size("XL")
          .set_crust("Stuffed")
          .set_sauce("BBQ")
          .set_cheese("Cheddar")
          .add_topping("Chicken")
          .add_topping("Bacon")
          .build())

print(custom)
print("\n")

# Pre-made recipes
margherita = PizzaDirector.make_margherita()
print(margherita)
```

**Practice** (45 min):

**Exercise 6.13**: HTML Builder with Fluent Interface
```python
# Create HTML builder with method chaining:
# 
# HTMLBuilder:
#   - html() - start HTML document
#   - head() - add head section
#   - title(text) - set title
#   - body() - add body section
#   - div(id=None, class_name=None) - add div
#   - p(text) - add paragraph
#   - h1/h2/h3(text) - add headings
#   - ul() / li(text) - add lists
#   - build() - return HTML string
# 
# Support nested elements
# Use method chaining for clean syntax
```

**Exercise 6.14**: Composite Organization Structure
```python
# Create organization hierarchy using Composite pattern:
# 
# Component: Employee(name, position, salary)
#   - get_salary() - return total salary
#   - display() - show hierarchy
# 
# Leaf: Developer, Designer, Tester
# Composite: Manager (has subordinates)
# 
# Build org chart:
#   CEO
#     ├── CTO
#     │   ├── Dev Team Lead
#     │   │   ├── Senior Dev
#     │   │   └── Junior Dev
#     │   └── QA Lead
#     │       └── Tester
#     └── CFO
#         └── Accountant
# 
# Calculate total payroll
# Display org chart
```

**Exercise 6.15**: Email Builder
```python
# Create email builder with fluent interface:
# 
# EmailBuilder:
#   - to(email) - add recipient (chainable for multiple)
#   - cc(email) - add cc
#   - bcc(email) - add bcc
#   - subject(text) - set subject
#   - body(text) - set body
#   - attach(file) - attach file
#   - priority(level) - set priority
#   - schedule(datetime) - schedule send time
#   - build() - return Email object
#   - send() - build and send
# 
# Create EmailDirector with templates:
#   - welcome_email(user)
#   - password_reset(user)
#   - newsletter(users, content)
# 
# Demonstrate fluent interface and director
```

---

## Day 36: Weekly Assignment - Week 6

**Time**: 1.4 hours  
**Due**: End of Day 36  
**Grading**: See rubric at end

### Assignment 6: Complete Security Analysis Platform

Build a comprehensive security analysis platform that integrates all design patterns learned this week. This is a major milestone that pulls together everything you've learned.

**System Overview**:
Create an enterprise-grade security platform with:
1. Multiple analysis engines (Strategy)
2. Event-driven architecture (Observer)
3. Command-based operations (Command)
4. Flexible report generation (Factory + Template Method)
5. Modular architecture (Composition)

### Part 1: Analysis Engine Framework (25 points)

**Strategy Pattern Implementation**:

```python
from abc import ABC, abstractmethod

class ThreatAnalysisStrategy(ABC):
    @abstractmethod
    def analyze(self, incident_data):
        """Returns analysis results dict"""
        pass
    
    @abstractmethod
    def get_risk_score(self):
        """Returns risk score 0-100"""
        pass

# Implement these strategies:
class SignatureBasedAnalysis(ThreatAnalysisStrategy):
    """Analyzes using known threat signatures"""
    pass

class BehaviorBasedAnalysis(ThreatAnalysisStrategy):
    """Analyzes behavior patterns"""
    pass

class MachineLearningAnalysis(ThreatAnalysisStrategy):
    """ML-based threat detection"""
    pass

class GeolocationAnalysis(ThreatAnalysisStrategy):
    """Analyzes based on geolocation"""
    pass

class ThreatAnalysisEngine:
    def __init__(self):
        self.strategies = []
        self.results = []
    
    def add_strategy(self, strategy):
        """OCP - can add strategies without modification"""
        self.strategies.append(strategy)
    
    def analyze_threat(self, incident_data):
        """Run all strategies"""
        self.results = []
        for strategy in self.strategies:
            result = strategy.analyze(incident_data)
            self.results.append(result)
        return self.aggregate_results()
    
    def aggregate_results(self):
        """Combine all strategy results"""
        pass
```

### Part 2: Event System with Observers (25 points)

**Observer Pattern for Real-time Monitoring**:

```python
class SecurityEventBus:
    """Central event bus using Observer pattern"""
    def __init__(self):
        self._subscribers = {}
    
    def subscribe(self, event_type, observer):
        pass
    
    def unsubscribe(self, event_type, observer):
        pass
    
    def publish(self, event_type, event_data):
        pass

# Implement these observers:
class AlertingObserver:
    """Sends alerts on critical events"""
    def update(self, event_type, data):
        if data['severity'] == 'CRITICAL':
            self.send_alert(data)

class MetricsObserver:
    """Tracks metrics and statistics"""
    def update(self, event_type, data):
        self.update_metrics(event_type, data)

class LoggingObserver:
    """Logs all events"""
    def update(self, event_type, data):
        self.log_event(event_type, data)

class ComplianceObserver:
    """Tracks compliance-related events"""
    def update(self, event_type, data):
        if self.is_compliance_relevant(data):
            self.record_compliance_event(data)

class AuditObserver:
    """Maintains audit trail"""
    def update(self, event_type, data):
        self.add_to_audit_trail(event_type, data)
```

### Part 3: Command System for Operations (20 points)

**Command Pattern for Incident Response**:

```python
class IncidentCommand(ABC):
    @abstractmethod
    def execute(self):
        pass
    
    @abstractmethod
    def undo(self):
        pass
    
    @abstractmethod
    def get_description(self):
        pass

# Implement these commands:
class IsolateSystemCommand(IncidentCommand):
    """Isolate compromised system from network"""
    pass

class BlockIPAddressCommand(IncidentCommand):
    """Block malicious IP in firewall"""
    pass

class QuarantineFileCommand(IncidentCommand):
    """Move file to quarantine"""
    pass

class EnableMonitoringCommand(IncidentCommand):
    """Enable enhanced monitoring"""
    pass

class NotifyTeamCommand(IncidentCommand):
    """Send notification to response team"""
    pass

class MacroCommand(IncidentCommand):
    """Execute multiple commands as one"""
    def __init__(self, commands):
        self.commands = commands
    
    def execute(self):
        for cmd in self.commands:
            cmd.execute()
    
    def undo(self):
        for cmd in reversed(self.commands):
            cmd.undo()

class ResponseOrchestrator:
    """Manages command execution"""
    def __init__(self):
        self.history = []
    
    def execute_command(self, command):
        pass
    
    def undo_last(self):
        pass
    
    def create_playbook(self, incident_type):
        """Create MacroCommand for incident type"""
        pass
```

### Part 4: Report Generation System (20 points)

**Factory + Template Method + Decorator**:

```python
# Template Method for reports
class SecurityReport(ABC):
    def generate(self):
        """Template method"""
        self.gather_data()
        self.analyze_data()
        self.format_report()
        return self.finalize()
    
    @abstractmethod
    def gather_data(self):
        pass
    
    @abstractmethod
    def format_report(self):
        pass
    
    def analyze_data(self):
        """Default implementation"""
        pass
    
    def finalize(self):
        """Default implementation"""
        return self.report_content

# Concrete reports
class IncidentReport(SecurityReport):
    pass

class ComplianceReport(SecurityReport):
    pass

class ExecutiveSummary(SecurityReport):
    pass

class TechnicalAnalysisReport(SecurityReport):
    pass

# Factory
class ReportFactory:
    @staticmethod
    def create_report(report_type, data):
        reports = {
            'incident': IncidentReport,
            'compliance': ComplianceReport,
            'executive': ExecutiveSummary,
            'technical': TechnicalAnalysisReport
        }
        if report_type in reports:
            report = reports[report_type]()
            report.data = data
            return report
        raise ValueError(f"Unknown report type: {report_type}")

# Decorator for report enhancements
class ReportDecorator(SecurityReport):
    def __init__(self, report):
        self.report = report

class EncryptedReport(ReportDecorator):
    """Encrypts report content"""
    pass

class CompressedReport(ReportDecorator):
    """Compresses report"""
    pass

class SignedReport(ReportDecorator):
    """Adds digital signature"""
    pass
```

### Part 5: Integration - Complete Platform (10 points)

```python
class SecurityAnalysisPlatform:
    """Main platform integrating all patterns"""
    
    def __init__(self):
        # Strategy
        self.analysis_engine = ThreatAnalysisEngine()
        
        # Observer
        self.event_bus = SecurityEventBus()
        
        # Command
        self.orchestrator = ResponseOrchestrator()
        
        # Factory
        self.report_factory = ReportFactory()
        
        # Setup
        self._setup_platform()
    
    def _setup_platform(self):
        """Initialize all components"""
        # Add analysis strategies
        self.analysis_engine.add_strategy(SignatureBasedAnalysis())
        self.analysis_engine.add_strategy(BehaviorBasedAnalysis())
        self.analysis_engine.add_strategy(MachineLearningAnalysis())
        
        # Register event observers
        self.event_bus.subscribe('incident', AlertingObserver())
        self.event_bus.subscribe('incident', MetricsObserver())
        self.event_bus.subscribe('incident', LoggingObserver())
        # etc.
    
    def process_security_incident(self, incident_data):
        """Complete incident processing workflow"""
        # 1. Analyze threat
        analysis_result = self.analysis_engine.analyze_threat(incident_data)
        
        # 2. Publish event
        self.event_bus.publish('incident', {
            'incident': incident_data,
            'analysis': analysis_result
        })
        
        # 3. Execute automated response
        playbook = self.orchestrator.create_playbook(incident_data['type'])
        self.orchestrator.execute_command(playbook)
        
        # 4. Generate reports
        report = self.report_factory.create_report('incident', {
            'incident': incident_data,
            'analysis': analysis_result
        })
        
        # 5. Apply report decorators
        report = SignedReport(EncryptedReport(report))
        
        return {
            'analysis': analysis_result,
            'report': report.generate(),
            'actions_taken': self.orchestrator.get_action_summary()
        }
```

**Demonstration Requirements**:

1. Process 5+ different incident types
2. Show all analysis strategies running
3. Demonstrate event observers receiving notifications
4. Execute commands with undo capability
5. Generate all report types
6. Show decorators enhancing reports
7. Demonstrate extensibility by adding new components

**Example Output**:
```
========================================
SECURITY ANALYSIS PLATFORM v2.0
========================================

Processing Incident: Advanced Persistent Threat
----------------------------------------------

[ANALYSIS PHASE]
Running analysis strategies...
  ✓ Signature-Based: Matched known APT group pattern
  ✓ Behavior-Based: Detected lateral movement
  ✓ ML-Based: 94% confidence malicious
  ✓ Geolocation: Origin: Eastern Europe (HIGH RISK)

Aggregated Risk Score: 96/100 [CRITICAL]

[EVENT NOTIFICATIONS]
Publishing to event bus...
  → Alerting Observer: CRITICAL alert sent
  → Metrics Observer: Updated threat metrics
  → Logging Observer: Logged to SIEM
  → Compliance Observer: GDPR notification required
  → Audit Observer: Added to audit trail

[AUTOMATED RESPONSE]
Executing incident playbook...
  ✓ Isolated compromised system: SERVER-001
  ✓ Blocked C2 IPs: 3 addresses
  ✓ Quarantined files: 5 files
  ✓ Enabled enhanced monitoring
  ✓ Notified incident response team

[REPORT GENERATION]
Generating reports...
  ✓ Incident Report (Technical)
  ✓ Executive Summary
  ✓ Compliance Report
  
Applying enhancements...
  ✓ Encrypted (AES-256)
  ✓ Digitally Signed

[SUMMARY]
Incident processed successfully
Total response time: 2.3 seconds
Actions taken: 8
Risk mitigated: 96% → 12%

========================================
EXTENSIBILITY DEMONSTRATION
========================================

Adding new analysis strategy...
  ✓ Added: ReputationAnalysis

Adding new observer...
  ✓ Added: ThreatIntelObserver

Adding new command...
  ✓ Added: SnapshotSystemCommand

Reprocessing incident with enhancements...
  ✓ All new components integrated seamlessly
  ✓ No existing code modified (OCP)

========================================
```

---

### Grading Rubric - Week 6 Assignment

**Total Points: 100**

| Category | Points | Criteria |
|----------|--------|----------|
| **Design Patterns** | 40 | |
| Strategy Pattern | 10 | Multiple strategies, clean interface |
| Observer Pattern | 10 | Event bus, multiple observers |
| Command Pattern | 10 | Commands with undo, macro commands |
| Factory + Template | 10 | Report generation system |
| **Integration** | 30 | |
| Platform architecture | 15 | All patterns work together |
| Workflow | 15 | Complete incident processing |
| **Code Quality** | 20 | |
| SOLID principles | 10 | All five applied correctly |
| Pattern implementation | 10 | Patterns implemented properly |
| **Demonstration** | 10 | |
| Comprehensive demo | 5 | All features shown |
| Extensibility | 5 | Easy to add new components |
| **Bonus** | +30 | See bonus challenges below |

**Bonus Challenges** (+6 points each):

1. **State Pattern**: Add incident state machine
2. **Proxy Pattern**: Add caching proxy for analysis results
3. **Chain of Responsibility**: Create escalation chain
4. **Memento Pattern**: Save/restore platform state
5. **Composite Pattern**: Nested incident grouping

**Testing Requirements**:
- [ ] All strategies execute correctly
- [ ] Observers receive appropriate events
- [ ] Commands execute and undo properly
- [ ] Reports generate in multiple formats
- [ ] Decorators enhance reports
- [ ] Can add new strategy without modifying engine
- [ ] Can add new observer without modifying event bus
- [ ] Can add new command without modifying orchestrator
- [ ] All patterns integrate seamlessly
- [ ] Complete workflow processes incidents correctly

**Submission**:
- Save as `week6_assignment.py`
- Include DESIGN_PATTERNS.md documenting each pattern
- Create UML diagrams showing pattern relationships
- Demonstrate extensibility with examples

</details>

---

<details>
<summary><h1>Week 7: Design Patterns & Best Practices</h1></summary>

**Focus**: Advanced Patterns, Testing, Performance, and Professional Practices

## Day 37 (Monday): More Design Patterns - Proxy and Chain of Responsibility

**Concepts** (45 min):

### Proxy Pattern

Proxy provides a surrogate or placeholder for another object to control access to it.

```python
from abc import ABC, abstractmethod
import time

# Subject interface
class Image(ABC):
    @abstractmethod
    def display(self):
        pass

# Real subject
class RealImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.load_from_disk()
    
    def load_from_disk(self):
        print(f"Loading image: {self.filename}")
        time.sleep(2)  # Simulate expensive operation
    
    def display(self):
        print(f"Displaying image: {self.filename}")

# Proxy
class ImageProxy(Image):
    def __init__(self, filename):
        self.filename = filename
        self.real_image = None  # Lazy loading
    
    def display(self):
        if self.real_image is None:
            self.real_image = RealImage(self.filename)
        self.real_image.display()

# Usage
print("Creating image proxies...")
image1 = ImageProxy("photo1.jpg")
image2 = ImageProxy("photo2.jpg")
print("Proxies created (images not loaded yet)")

print("\nDisplaying image1:")
image1.display()  # Loads and displays

print("\nDisplaying image1 again:")
image1.display()  # Just displays (already loaded)
```

### Virtual Proxy Example

```python
class ExpensiveObject:
    def __init__(self, data):
        print("Creating expensive object...")
        time.sleep(2)  # Simulate expensive creation
        self.data = data
        self.process_data()
    
    def process_data(self):
        print(f"Processing data: {self.data}")
        time.sleep(1)
    
    def get_result(self):
        return f"Result for {self.data}"

class LazyProxy:
    def __init__(self, data):
        self.data = data
        self._real_object = None
    
    def _get_real_object(self):
        if self._real_object is None:
            self._real_object = ExpensiveObject(self.data)
        return self._real_object
    
    def get_result(self):
        return self._get_real_object().get_result()

# Usage
print("Creating proxies...")
proxy1 = LazyProxy("data1")
proxy2 = LazyProxy("data2")
print("Proxies created instantly")

print("\nAccessing proxy1...")
print(proxy1.get_result())  # Object created on first access

print("\nAccessing proxy1 again...")
print(proxy1.get_result())  # Reuses existing object
```

### Protection Proxy

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def deposit(self, amount):
        self.balance += amount
        return self.balance
    
    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            return self.balance
        raise ValueError("Insufficient funds")
    
    def get_balance(self):
        return self.balance

class SecureBankAccountProxy:
    def __init__(self, account, user_role):
        self.account = account
        self.user_role = user_role
    
    def deposit(self, amount):
        if self.user_role in ['teller', 'admin']:
            return self.account.deposit(amount)
        raise PermissionError("Unauthorized to deposit")
    
    def withdraw(self, amount):
        if self.user_role in ['account_holder', 'admin']:
            return self.account.withdraw(amount)
        raise PermissionError("Unauthorized to withdraw")
    
    def get_balance(self):
        if self.user_role in ['account_holder', 'teller', 'admin']:
            return self.account.get_balance()
        raise PermissionError("Unauthorized to view balance")

# Usage
account = BankAccount(1000)

# Teller can deposit but not withdraw
teller_proxy = SecureBankAccountProxy(account, 'teller')
teller_proxy.deposit(500)
print(teller_proxy.get_balance())  # 1500

try:
    teller_proxy.withdraw(100)  # Raises PermissionError
except PermissionError as e:
    print(f"Teller error: {e}")

# Account holder can withdraw
holder_proxy = SecureBankAccountProxy(account, 'account_holder')
holder_proxy.withdraw(200)
print(holder_proxy.get_balance())  # 1300
```

### Chain of Responsibility Pattern

Chain of Responsibility passes request along chain of handlers until one handles it.

```python
from abc import ABC, abstractmethod

class Handler(ABC):
    def __init__(self):
        self.next_handler = None
    
    def set_next(self, handler):
        self.next_handler = handler
        return handler
    
    @abstractmethod
    def handle(self, request):
        pass

class AuthenticationHandler(Handler):
    def handle(self, request):
        if 'username' not in request or 'password' not in request:
            return {"error": "Missing credentials"}
        
        print("Authentication passed")
        if self.next_handler:
            return self.next_handler.handle(request)
        return {"status": "authenticated"}

class AuthorizationHandler(Handler):
    def handle(self, request):
        if request.get('role') != 'admin':
            return {"error": "Unauthorized"}
        
        print("Authorization passed")
        if self.next_handler:
            return self.next_handler.handle(request)
        return {"status": "authorized"}

class ValidationHandler(Handler):
    def handle(self, request):
        if 'data' not in request:
            return {"error": "Missing data"}
        
        print("Validation passed")
        if self.next_handler:
            return self.next_handler.handle(request)
        return {"status": "validated"}

class ProcessingHandler(Handler):
    def handle(self, request):
        print(f"Processing data: {request['data']}")
        return {"status": "success", "result": "Data processed"}

# Build chain
auth = AuthenticationHandler()
authz = AuthorizationHandler()
valid = ValidationHandler()
process = ProcessingHandler()

auth.set_next(authz).set_next(valid).set_next(process)

# Test requests
request1 = {
    'username': 'admin',
    'password': 'pass123',
    'role': 'admin',
    'data': 'important data'
}
print(auth.handle(request1))

print("\n")

request2 = {
    'username': 'user',
    'password': 'pass456',
    'role': 'user',
    'data': 'some data'
}
print(auth.handle(request2))  # Fails at authorization
```

**Practice** (45 min):

**Exercise 7.1**: Caching Proxy
```python
# Create a caching proxy for database queries:
# 
# RealDatabase:
#   - query(sql) - executes query (slow)
#   - insert(sql) - inserts data
# 
# DatabaseProxy:
#   - Caches query results
#   - Cache invalidation on inserts
#   - TTL (time-to-live) for cache entries
#   - get_cache_stats() - hits/misses
# 
# Demonstrate performance improvement with caching
```

**Exercise 7.2**: Support Ticket Chain
```python
# Create support ticket escalation chain:
# 
# Handlers:
#   - Level1SupportHandler (handles simple issues)
#   - Level2SupportHandler (handles moderate issues)
#   - Level3SupportHandler (handles complex issues)
#   - ManagerHandler (handles escalated issues)
# 
# Each handler decides if it can handle ticket or pass to next
# Track handling time and handler for each ticket
# Generate escalation report
```

**Exercise 7.3**: Access Control Proxy
```python
# Create file access control system:
# 
# RealFile:
#   - read()
#   - write(content)
#   - delete()
# 
# SecureFileProxy:
#   - Checks permissions before each operation
#   - Logs all access attempts
#   - Implements role-based access control
#   - Tracks access history
# 
# Roles: admin, editor, viewer
# Demonstrate different access levels
```

---

## Day 38: Testing OOP Code

**Concepts** (45 min):

### Unit Testing Basics

```python
import unittest

class Calculator:
    def add(self, a, b):
        return a + b
    
    def divide(self, a, b):
        if b == 0:
            raise ValueError("Cannot divide by zero")
        return a / b

class TestCalculator(unittest.TestCase):
    def setUp(self):
        """Run before each test"""
        self.calc = Calculator()
    
    def test_add(self):
        result = self.calc.add(3, 5)
        self.assertEqual(result, 8)
    
    def test_add_negative(self):
        result = self.calc.add(-1, 1)
        self.assertEqual(result, 0)
    
    def test_divide(self):
        result = self.calc.divide(10, 2)
        self.assertEqual(result, 5)
    
    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            self.calc.divide(10, 0)
    
    def tearDown(self):
        """Run after each test"""
        pass

if __name__ == '__main__':
    unittest.main()
```

### Testing Classes with Dependencies

```python
class EmailService:
    def send(self, to, subject, body):
        # In real code, would send email
        raise NotImplementedError("Real email sending")

class UserService:
    def __init__(self, email_service):
        self.email_service = email_service
        self.users = {}
    
    def register_user(self, username, email):
        if username in self.users:
            raise ValueError("User already exists")
        
        self.users[username] = {'email': email}
        self.email_service.send(
            email,
            "Welcome",
            f"Welcome {username}!"
        )
        return True

# Mock for testing
class MockEmailService:
    def __init__(self):
        self.sent_emails = []
    
    def send(self, to, subject, body):
        self.sent_emails.append({
            'to': to,
            'subject': subject,
            'body': body
        })

class TestUserService(unittest.TestCase):
    def setUp(self):
        self.email_service = MockEmailService()
        self.user_service = UserService(self.email_service)
    
    def test_register_user(self):
        result = self.user_service.register_user('alice', 'alice@example.com')
        self.assertTrue(result)
        self.assertIn('alice', self.user_service.users)
    
    def test_register_sends_email(self):
        self.user_service.register_user('bob', 'bob@example.com')
        self.assertEqual(len(self.email_service.sent_emails), 1)
        email = self.email_service.sent_emails[0]
        self.assertEqual(email['to'], 'bob@example.com')
        self.assertEqual(email['subject'], 'Welcome')
    
    def test_duplicate_user(self):
        self.user_service.register_user('charlie', 'charlie@example.com')
        with self.assertRaises(ValueError):
            self.user_service.register_user('charlie', 'charlie2@example.com')
```

### Test-Driven Development (TDD)

```python
# Step 1: Write test first (it will fail)
class TestBankAccount(unittest.TestCase):
    def test_initial_balance(self):
        account = BankAccount(100)
        self.assertEqual(account.get_balance(), 100)
    
    def test_deposit(self):
        account = BankAccount(100)
        account.deposit(50)
        self.assertEqual(account.get_balance(), 150)
    
    def test_withdraw(self):
        account = BankAccount(100)
        account.withdraw(30)
        self.assertEqual(account.get_balance(), 70)
    
    def test_withdraw_insufficient_funds(self):
        account = BankAccount(100)
        with self.assertRaises(ValueError):
            account.withdraw(150)

# Step 2: Implement just enough to pass tests
class BankAccount:
    def __init__(self, initial_balance):
        if initial_balance < 0:
            raise ValueError("Initial balance cannot be negative")
        self._balance = initial_balance
    
    def get_balance(self):
        return self._balance
    
    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit amount must be positive")
        self._balance += amount
    
    def withdraw(self, amount):
        if amount <= 0:
            raise ValueError("Withdrawal amount must be positive")
        if amount > self._balance:
            raise ValueError("Insufficient funds")
        self._balance -= amount

# Step 3: Refactor (if needed) while keeping tests passing
```

**Practice** (45 min):

**Exercise 7.4**: Test Shopping Cart
```python
# Write comprehensive tests for shopping cart:
# 
# ShoppingCart class to test:
#   - add_item(product, quantity)
#   - remove_item(product)
#   - update_quantity(product, quantity)
#   - get_total()
#   - apply_discount(percentage)
#   - clear()
# 
# Write tests for:
#   - Normal operations
#   - Edge cases (empty cart, invalid quantities)
#   - Discount calculations
#   - Multiple items
# 
# Use TDD - write tests first, then implement
```

**Exercise 7.5**: Test User Authentication
```python
# Test authentication system:
# 
# Classes:
#   - User(username, password_hash)
#   - AuthenticationService(user_repository)
# 
# Test cases:
#   - Successful login
#   - Failed login (wrong password)
#   - Account lockout after 3 failed attempts
#   - Password reset
#   - Session management
# 
# Use mocks for dependencies
```

**Exercise 7.6**: Test File Storage System
```python
# Test file storage with different scenarios:
# 
# FileStorage:
#   - save(filename, content)
#   - load(filename)
#   - delete(filename)
#   - exists(filename)
#   - list_files()
# 
# Test:
#   - Normal file operations
#   - Non-existent files
#   - File overwriting
#   - Large files
#   - Special characters in filenames
# 
# Use temporary directories for testing
```

**Exercise 7.6**: Test File Storage System
```python
# Test file storage with different scenarios:
# 
# FileStorage:
#   - save(filename, content)
#   - load(filename)
#   - delete(filename)
#   - exists(filename)
#   - list_files()
# 
# Test:
#   - Normal file operations
#   - Non-existent files
#   - File overwriting
#   - Large files
#   - Special characters in filenames
# 
# Use temporary directories for testing
```

---

## Day 39: Performance and Optimization

**Concepts** (45 min):

### Profiling and Performance Measurement

```python
import time
from functools import wraps

def timing_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

class DataProcessor:
    @timing_decorator
    def slow_method(self, data):
        time.sleep(1)
        return [x * 2 for x in data]
    
    @timing_decorator
    def fast_method(self, data):
        return [x * 2 for x in data]

processor = DataProcessor()
data = list(range(1000))
processor.slow_method(data)
processor.fast_method(data)
```

### Memory Optimization with __slots__

```python
import sys

# Without __slots__ - uses dictionary
class RegularClass:
    def __init__(self, x, y):
        self.x = x
        self.y = y

# With __slots__ - uses tuple
class OptimizedClass:
    __slots__ = ['x', 'y']
    
    def __init__(self, x, y):
        self.x = x
        self.y = y

# Memory comparison
regular = RegularClass(1, 2)
optimized = OptimizedClass(1, 2)

print(f"Regular: {sys.getsizeof(regular)} bytes")
print(f"Optimized: {sys.getsizeof(optimized)} bytes")

# Create many objects
regular_list = [RegularClass(i, i) for i in range(10000)]
optimized_list = [OptimizedClass(i, i) for i in range(10000)]
```

### Caching for Performance

```python
from functools import lru_cache

class Calculator:
    def __init__(self):
        self.call_count = 0
    
    @lru_cache(maxsize=128)
    def fibonacci(self, n):
        self.call_count += 1
        if n < 2:
            return n
        return self.fibonacci(n-1) + self.fibonacci(n-2)

calc = Calculator()
print(calc.fibonacci(10))
print(f"Calls: {calc.call_count}")

# Second call uses cache
calc.call_count = 0
print(calc.fibonacci(10))
print(f"Calls (cached): {calc.call_count}")
```

**Practice** (45 min):

**Exercise 7.7**: Optimize Data Processing Pipeline
**Exercise 7.8**: Implement Efficient Cache System
**Exercise 7.9**: Profile and Optimize Security Scanner

---

## Day 40: Error Handling and Logging Best Practices

**Concepts** (45 min):

### Custom Exceptions

```python
class SecurityException(Exception):
    """Base exception for security-related errors"""
    pass

class AuthenticationError(SecurityException):
    """Raised when authentication fails"""
    pass

class AuthorizationError(SecurityException):
    """Raised when user lacks permissions"""
    pass

class SecuritySystem:
    def authenticate(self, username, password):
        if not username or not password:
            raise AuthenticationError("Invalid credentials")
        return True
    
    def authorize(self, user, resource):
        if user.role != 'admin':
            raise AuthorizationError(f"{user.name} cannot access {resource}")
        return True
```

### Logging Best Practices

```python
import logging

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)

class SecurityMonitor:
    def __init__(self):
        self.logger = logging.getLogger(__name__)
    
    def log_event(self, event_type, details):
        self.logger.info(f"{event_type}: {details}")
    
    def log_error(self, error):
        self.logger.error(f"Error: {error}", exc_info=True)
```

**Practice** (45 min):

**Exercise 7.10**: Exception Hierarchy for SOC
**Exercise 7.11**: Comprehensive Logging System
**Exercise 7.12**: Error Recovery Mechanisms

---

## Day 41: Documentation and Code Quality

**Concepts** (45 min):

### Docstrings and Type Hints

```python
from typing import List, Dict, Optional

class SecurityIncident:
    """
    Represents a security incident in the SOC system.
    
    Attributes:
        incident_id (str): Unique identifier for the incident
        severity (str): Severity level (Low, Medium, High, Critical)
        status (str): Current status (Open, In Progress, Resolved, Closed)
    
    Example:
        >>> incident = SecurityIncident("INC001", "High")
        >>> incident.update_status("In Progress")
    """
    
    def __init__(self, incident_id: str, severity: str) -> None:
        """
        Initialize a new security incident.
        
        Args:
            incident_id: Unique identifier for the incident
            severity: Severity level of the incident
        
        Raises:
            ValueError: If severity is not valid
        """
        self.incident_id = incident_id
        self.severity = severity
    
    def get_details(self) -> Dict[str, str]:
        """
        Get incident details.
        
        Returns:
            Dictionary containing incident information
        """
        return {
            'id': self.incident_id,
            'severity': self.severity
        }
```

**Practice** (45 min):

**Exercise 7.13**: Document Existing Code
**Exercise 7.14**: Add Type Hints Throughout
**Exercise 7.15**: Create API Documentation

---

## Day 42: Weekly Assignment - Week 7

**Time**: 1.4 hours  
**Due**: End of Day 42

### Assignment 7: Professional-Grade Security Platform Enhancement

Enhance your security platform with professional practices:
1. Comprehensive testing suite
2. Performance optimization
3. Error handling and logging
4. Complete documentation

*(See full rubric in document)*

</details>

---

<details>
<summary><h1>Week 8: Capstone Project</h1></summary>

**Focus**: Building Complete Security Incident Management System

## Day 43 (Monday): Capstone Project - Architecture and Design

### Project Overview: Enterprise Security Incident Management System

You will build a complete, professional-grade Security Incident Management System that demonstrates everything you've learned:

**System Requirements**:
1. Multi-tier architecture
2. All major design patterns
3. SOLID principles throughout
4. Comprehensive testing
5. Performance optimization
6. Professional documentation

### Architecture Components

```python
"""
Enterprise Security Incident Management System (ESIMS)
=====================================================

Tier 1: Data Layer
------------------
- Incident Repository
- User Repository
- Asset Repository
- Configuration Storage

Tier 2: Business Logic Layer
----------------------------
- Incident Management Service
- Analysis Engine
- Response Orchestrator
- Notification System
- Report Generator

Tier 3: Presentation Layer
--------------------------
- CLI Interface
- Dashboard
- Report Viewer

Cross-Cutting Concerns
---------------------
- Logging
- Authentication
- Error Handling
- Caching
"""
```

---

## Day 44-45: Core Implementation

### Part 1: Domain Models

```python
from dataclasses import dataclass
from datetime import datetime
from enum import Enum
from typing import List, Optional

class Severity(Enum):
    LOW = "Low"
    MEDIUM = "Medium"
    HIGH = "High"
    CRITICAL = "Critical"

class IncidentStatus(Enum):
    OPEN = "Open"
    IN_PROGRESS = "In Progress"
    RESOLVED = "Resolved"
    CLOSED = "Closed"

@dataclass
class SecurityIncident:
    incident_id: str
    title: str
    description: str
    severity: Severity
    status: IncidentStatus
    created_at: datetime
    assigned_to: Optional[str] = None
    resolved_at: Optional[datetime] = None
    
    # Implement all required methods
```

### Part 2: Services Layer

```python
class IncidentService:
    """Core business logic for incident management"""
    
    def __init__(self, repository, event_bus, analyzer):
        self.repository = repository
        self.event_bus = event_bus
        self.analyzer = analyzer
    
    def create_incident(self, data):
        # Validation
        # Creation
        # Event publishing
        # Analysis triggering
        pass
    
    def update_incident(self, incident_id, updates):
        pass
    
    def assign_incident(self, incident_id, analyst_id):
        pass
    
    def resolve_incident(self, incident_id, resolution_notes):
        pass
```

---

## Day 46-47: Integration and Testing

### Comprehensive Test Suite

```python
class TestIncidentService(unittest.TestCase):
    """Test suite for IncidentService"""
    
    def setUp(self):
        self.repository = MockIncidentRepository()
        self.event_bus = EventBus()
        self.analyzer = ThreatAnalyzer()
        self.service = IncidentService(
            self.repository, 
            self.event_bus, 
            self.analyzer
        )
    
    def test_create_incident(self):
        # Test incident creation
        pass
    
    def test_assign_incident(self):
        # Test incident assignment
        pass
    
    # ... more tests
```

---

## Day 48: Final Presentation and Documentation

### Capstone Deliverables

1. **Complete Source Code**
   - All modules implemented
   - Clean, documented code
   - Follows all best practices

2. **Documentation Package**
   - Architecture document
   - API documentation
   - User guide
   - Deployment guide

3. **Test Suite**
   - Unit tests (80%+ coverage)
   - Integration tests
   - Performance benchmarks

4. **Demonstration**
   - Live demo of all features
   - Performance metrics
   - Extensibility examples

### Capstone Grading Rubric

**Total Points: 200**

| Category | Points | Criteria |
|----------|--------|----------|
| **Architecture** | 40 | |
| Design | 20 | Clean separation of concerns, proper layering |
| Patterns | 20 | Appropriate use of design patterns |
| **Implementation** | 80 | |
| Core functionality | 30 | All required features working |
| Code quality | 25 | Clean, readable, maintainable |
| SOLID principles | 25 | All five principles applied |
| **Testing** | 30 | |
| Unit tests | 15 | Comprehensive test coverage |
| Integration tests | 15 | System-level testing |
| **Documentation** | 30 | |
| Code documentation | 15 | Docstrings, comments, type hints |
| User documentation | 15 | README, guides, API docs |
| **Presentation** | 20 | |
| Demo | 10 | Live demonstration |
| Explanation | 10 | Clear articulation of design decisions |

---

## Capstone Project Detailed Specifications

### Required Features

#### 1. Incident Management
- Create, read, update, delete incidents
- Status workflow management
- Assignment and escalation
- Timeline tracking
- Related incident linking

#### 2. Analysis System
- Multiple analysis strategies
- Risk scoring
- Threat correlation
- Impact assessment

#### 3. Response Automation
- Automated playbooks
- Command execution
- Rollback capability
- Audit trail

#### 4. Notification System
- Multi-channel notifications
- Priority-based routing
- Template management
- Delivery tracking

#### 5. Reporting
- Multiple report types
- Export formats (PDF, Excel, JSON)
- Scheduled reports
- Custom report builder

#### 6. User Management
- Authentication
- Role-based access control
- Session management
- Activity logging

#### 7. Dashboard
- Real-time metrics
- Incident trends
- Performance indicators
- Customizable views

### Technical Requirements

#### Must Use These Patterns
- [ ] Factory Pattern (for object creation)
- [ ] Singleton Pattern (for configuration)
- [ ] Strategy Pattern (for analysis algorithms)
- [ ] Observer Pattern (for event handling)
- [ ] Command Pattern (for operations)
- [ ] Decorator Pattern (for functionality enhancement)
- [ ] Template Method (for report generation)
- [ ] Proxy Pattern (for access control or caching)
- [ ] Chain of Responsibility (for escalation)

#### Must Demonstrate SOLID
- [ ] Single Responsibility (each class one purpose)
- [ ] Open/Closed (extensible without modification)
- [ ] Liskov Substitution (proper inheritance)
- [ ] Interface Segregation (focused interfaces)
- [ ] Dependency Inversion (depend on abstractions)

#### Code Quality Standards
- [ ] Comprehensive docstrings (Google or NumPy style)
- [ ] Type hints on all functions
- [ ] Error handling with custom exceptions
- [ ] Logging throughout
- [ ] Configuration management
- [ ] 80%+ test coverage

### Submission Package

**File Structure**:
```
esims/
├── README.md
├── requirements.txt
├── setup.py
├── docs/
│   ├── ARCHITECTURE.md
│   ├── API.md
│   ├── USER_GUIDE.md
│   └── DEPLOYMENT.md
├── src/
│   ├── __init__.py
│   ├── models/
│   ├── services/
│   ├── repositories/
│   ├── patterns/
│   └── utils/
├── tests/
│   ├── unit/
│   └── integration/
└── examples/
    └── demo.py
```

**README.md Template**:
```markdown
# Enterprise Security Incident Management System (ESIMS)

## Overview
[Brief description of the system]

## Features
[List of major features]

## Architecture
[High-level architecture diagram and explanation]

## Installation
[Installation instructions]

## Usage
[Basic usage examples]

## Design Patterns
[List patterns used and where]

## SOLID Principles
[How each principle is applied]

## Testing
[How to run tests]

## Future Enhancements
[Possible improvements]
```

</details>

---

<details>
<summary><h1>Conclusion and Next Steps</h1></summary>

### Congratulations!

You've completed an intensive 8-week Python OOP curriculum covering:

✅ Python fundamentals (variables through dictionaries)  
✅ Object-oriented programming basics  
✅ Inheritance and polymorphism  
✅ Design patterns (creational, structural, behavioral)  
✅ SOLID principles  
✅ Testing and quality assurance  
✅ Professional development practices  
✅ Complete capstone project

### Skills Acquired

**Technical Skills**:
- Advanced Python programming
- OOP design and implementation
- Design pattern application
- Test-driven development
- Performance optimization
- Professional documentation

**Problem-Solving Skills**:
- System architecture design
- Pattern selection
- Trade-off analysis
- Refactoring strategies

**Professional Practices**:
- Code quality standards
- Documentation practices
- Testing methodologies
- Version control (implied)

### Continuing Your Journey

**Next Steps**:

1. **Enhance Your Capstone**
   - Add more features
   - Implement additional patterns
   - Improve performance
   - Expand test coverage

2. **Explore Related Topics**
   - Async programming
   - Database integration
   - Web frameworks (Flask/Django)
   - API development

3. **Build More Projects**
   - Apply patterns to different domains
   - Contribute to open source
   - Create portfolio projects

4. **Deepen Your Knowledge**
   - Study advanced patterns
   - Learn software architecture
   - Explore domain-driven design
   - Study system design

### Resources for Continued Learning

**Books**:
- "Design Patterns" by Gang of Four
- "Clean Code" by Robert C. Martin
- "Refactoring" by Martin Fowler
- "Python Cookbook" by David Beazley

**Online Resources**:
- Python documentation
- Real Python
- Talk Python podcasts
- PyVideo conference talks

**Practice Platforms**:
- LeetCode (OOP problems)
- CodeWars
- Project Euler
- Open source projects

### Final Assessment Checklist

Before submitting your capstone, verify:

- [ ] All required features implemented
- [ ] All design patterns used correctly
- [ ] SOLID principles demonstrated
- [ ] Comprehensive test suite (80%+ coverage)
- [ ] Complete documentation
- [ ] Code follows style guide (PEP 8)
- [ ] Type hints throughout
- [ ] Error handling implemented
- [ ] Logging configured
- [ ] Performance optimized
- [ ] Demo prepared
- [ ] README.md complete

### Acknowledgments

This curriculum was designed specifically for security professionals transitioning to software development, with emphasis on:
- Security-relevant examples
- SOC/incident response scenarios
- Enterprise-grade patterns
- Professional practices

### Contact and Support

Throughout this course, remember:
- **Debug systematically** using VSCode tools
- **Test continuously** with unit tests
- **Refactor fearlessly** with tests as safety net
- **Document thoroughly** for future you
- **Ask questions** and seek clarification
- **Practice daily** to reinforce learning

### Final Words

Software development is a craft that improves with practice. The patterns and principles you've learned here are tools in your toolbox. Knowing when and how to apply them comes with experience.

Your capstone project represents not just the culmination of this course, but the beginning of your journey as a software developer. The skills you've developed—analytical thinking, systematic problem-solving, and professional development practices—will serve you well regardless of the specific technologies you use.

**Best of luck with your capstone project and your future endeavors in software development!**

</details>

---

<details>
<summary><h1>Appendix: Quick Reference Guide</h1></summary>

### Design Patterns Cheat Sheet

**Creational Patterns**:
- **Factory**: Create objects without specifying exact class
- **Singleton**: Ensure only one instance exists
- **Builder**: Construct complex objects step by step

**Structural Patterns**:
- **Adapter**: Convert interface to expected interface
- **Decorator**: Add responsibilities dynamically
- **Proxy**: Control access to an object
- **Composite**: Treat objects and compositions uniformly

**Behavioral Patterns**:
- **Strategy**: Define family of interchangeable algorithms
- **Observer**: Define one-to-many dependency
- **Command**: Encapsulate request as object
- **Template Method**: Define algorithm skeleton
- **Chain of Responsibility**: Pass request along chain

### SOLID Principles Summary

**S** - Single Responsibility: One class, one responsibility  
**O** - Open/Closed: Open for extension, closed for modification  
**L** - Liskov Substitution: Subtypes must be substitutable  
**I** - Interface Segregation: Many specific interfaces better than one general  
**D** - Dependency Inversion: Depend on abstractions, not concretions

### Python OOP Syntax Reference

```python
# Class definition
class MyClass:
    class_var = "shared"  # Class variable
    
    def __init__(self, value):
        self.instance_var = value  # Instance variable
    
    def instance_method(self):
        return self.instance_var
    
    @classmethod
    def class_method(cls):
        return cls.class_var
    
    @staticmethod
    def static_method():
        return "no self or cls needed"
    
    @property
    def value(self):
        return self.instance_var
    
    @value.setter
    def value(self, new_value):
        self.instance_var = new_value

# Inheritance
class ChildClass(MyClass):
    def __init__(self, value, extra):
        super().__init__(value)
        self.extra = extra

# Abstract base class
from abc import ABC, abstractmethod

class AbstractClass(ABC):
    @abstractmethod
    def must_implement(self):
        pass

# Multiple inheritance
class Multi(Base1, Base2):
    pass

# Special methods
class SpecialMethods:
    def __str__(self):
        return "user-friendly string"
    
    def __repr__(self):
        return "developer string"
    
    def __eq__(self, other):
        return self.value == other.value
    
    def __lt__(self, other):
        return self.value < other.value
    
    def __add__(self, other):
        return self.value + other.value
    
    def __len__(self):
        return len(self.data)
    
    def __getitem__(self, key):
        return self.data[key]
```

---

**END OF CURRICULUM**

You now have a complete, professional 8-week Python OOP curriculum. Study hard, practice daily, and enjoy the journey of becoming a proficient object-oriented programmer!

For questions, clarifications, or additional challenges, continue to explore and experiment with the concepts presented. The best way to learn is by doing.

**Happy coding! 🐍**

</details>

---
