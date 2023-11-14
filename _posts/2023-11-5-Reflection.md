---
comments: true
layout: post
title: Reflection
description: My goals for the future and what I've accomplished
type: hacks
courses: { csp: {week: 12}}
---

**Key Takeaways from Passion Project:**

Using Flask framework for creating web applications with a focus on RESTful APIs. Organized well, separating database models, API routes, and the database initialization function.

Clear structure for defining the model and managing CRUD (Create, Read, Update, Delete) operations for API data.

Code focuses on the backend implementation. 

To fully utilize the API, created corresponding frontend components fetching data to interact with it.

**Improvements/Additional Learning:**

Additionally, error handling can be improved, especially in the case of database operations, where exceptions should be handled more explicitly and provide meaningful error messages.

Implementing more techniques learned from student teaching: Procedures, Algorithms, Libraries, etc...

Work toward making code cleaner, more efficient, and easier to test.

**Pseudo Code vs Python**

Example 1: Finding the Maximum of Two Numbers

Pseudo Code 

```script
Start
  Input num1
  Input num2
  If num1 > num2
    Display num1
  Else
    Display num2
  End If
Stop
```

Python

```python
num1 = int(input("Enter the first number: "))
num2 = int(input("Enter the second number: ")

if num1 > num2:
    print(num1)
else:
    print(num2)
```

Example 2: Calculating the Sum of Integers from 1 to N

Pseudo Code 

```script
Start
  Input N
  sum = 0
  For i from 1 to N
    sum = sum + i
  End For
  Display sum
Stop
```

Python

```python
N = int(input("Enter a number: "))
sum = 0

for i in range(1, N + 1):
    sum += i

print(sum)
```

Example 3: Checking if a Number is Even or Odd

Pseudo Code 

```script
Start
  Input number
  If number % 2 = 0
    Display "Even"
  Else
    Display "Odd"
  End If
Stop
```

Python

```python
number = int(input("Enter a number: ")

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```