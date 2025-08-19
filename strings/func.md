Perfect 👌 Since you’ve already learned some Python basics (functions, loops, prime numbers, factorial, string reverse, lists, sets, tuples, etc.), let’s move on step by step into the **next Python concepts** that are very important:

---

## 📘 Next Topics to Learn in Python

### 1. **Dictionaries (`dict`)**

* A dictionary stores data in **key-value pairs**.
* Keys must be unique and immutable (like strings, numbers, tuples).
* Values can be of any data type.

```python
# Creating a dictionary
student = {"name": "Swathi", "age": 21, "course": "AIML"}

# Access values
print(student["name"])   # Swathi
print(student.get("age"))  # 21

# Add or update
student["age"] = 22
student["city"] = "Bangalore"

# Looping
for key, value in student.items():
    print(key, ":", value)

# Delete
del student["city"]
```

✅ **Use case:** When you want to map relationships (like ID → Name, Word → Meaning, etc.).

---

### 2. **List Comprehensions**

A short and powerful way to create lists.

```python
# Normal way
squares = []
for i in range(1, 6):
    squares.append(i**2)

# List comprehension way
squares = [i**2 for i in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]

# With condition
evens = [i for i in range(10) if i % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]
```

✅ **Use case:** Cleaner and faster list creation.

---

### 3. **Functions with Arguments**

You already know basic functions. Let’s go deeper.

```python
# Default arguments
def greet(name="Guest"):
    return "Hello " + name

print(greet())       # Hello Guest
print(greet("Swathi"))  # Hello Swathi

# Variable arguments (*args)
def add_all(*numbers):
    return sum(numbers)

print(add_all(1, 2, 3, 4))  # 10

# Keyword arguments (**kwargs)
def student_info(**data):
    for key, value in data.items():
        print(key, ":", value)

student_info(name="Swathi", age=21, branch="AIML")
```

---

### 4. **Recursion (function calling itself)**

Example: Factorial with recursion.

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n-1)

print(factorial(5))  # 120
```

---

### 5. **Modules & Import**

Python has built-in modules you can use.

```python
import math

print(math.sqrt(16))   # 4.0
print(math.factorial(5))  # 120
print(math.pi)  # 3.141592653589793
```

---

### 6. **Exception Handling**

To handle errors safely.

```python
try:
    num = int(input("Enter a number: "))
    print(10 / num)
except ZeroDivisionError:
    print("You cannot divide by zero!")
except ValueError:
    print("Invalid input! Please enter a number.")
finally:
    print("Execution finished")
```

---

### 7. **File Handling**

To read/write files.

```python
# Writing to a file
with open("data.txt", "w") as f:
    f.write("Hello Python\nWelcome to learning!")

# Reading from a file
with open("data.txt", "r") as f:
    content = f.read()
    print(content)
```

---

👉 These are the **next fundamental Python concepts** after lists/sets/tuples/loops.
Once you master these, we’ll move to **OOP (Classes & Objects), Generators, Decorators, and Advanced Python**.

---

Do you want me to **make an MD (Markdown) revision sheet** for these topics also (like we did earlier) 📒, or should I start **teaching you each one step-by-step with dry runs and examples**?
