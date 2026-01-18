# Technical Round Interview Questions & Answers 🖥️

## About This Round

The technical round evaluates your programming knowledge, problem-solving abilities, and understanding of core CS concepts. This document focuses on **C, Python, and SQL** - your strong areas.

> ⚠️ **Note:** If asked about Java, be honest that you're learning it. Explain that your C and Python experience provides a strong foundation to pick up Java quickly.

---

## Section 1: C Programming (Your Strength!)

### Q1: What are the main features of C?

**Answer:**
>
> 1. **Procedural Language**: Follows step-by-step procedure
> 2. **Low-level Access**: Can work with memory directly via pointers
> 3. **Fast & Efficient**: Close to hardware, minimal overhead
> 4. **Portable**: Can run on different machines with little modification
> 5. **Rich Library**: Standard library functions
> 6. **Foundation**: Basis for many other languages (C++, Java)

### Q2: Explain pointers in C with examples

**Answer:**
> Pointers are variables that store memory addresses of other variables.

```c
int a = 10;
int *ptr = &a;  // ptr stores address of a

printf("Value of a: %d\n", a);       // 10
printf("Address of a: %p\n", &a);    // memory address
printf("Value via ptr: %d\n", *ptr); // 10 (dereferencing)
```

**Why pointers matter:**

- Dynamic memory allocation
- Passing data by reference
- Working with arrays and strings
- Data structures (linked lists, trees)

### Q3: What is the difference between malloc() and calloc()?

| Feature | malloc() | calloc() |
|---------|----------|----------|
| Syntax | `malloc(size)` | `calloc(n, size)` |
| Initialization | No (garbage values) | Yes (zeros) |
| Parameters | 1 (total bytes) | 2 (count, size each) |
| Speed | Slightly faster | Slightly slower |

```c
// malloc - allocates 40 bytes (10 integers)
int *arr1 = (int*) malloc(10 * sizeof(int));

// calloc - allocates 10 integers, initialized to 0
int *arr2 = (int*) calloc(10, sizeof(int));

// Always free memory!
free(arr1);
free(arr2);
```

### Q4: Explain call by value vs call by reference

**Call by Value:**

```c
void swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}
// Original values NOT changed
```

**Call by Reference (using pointers):**

```c
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
// Original values ARE changed
swap(&x, &y);
```

### Q5: What are structures in C?

**Answer:**
> Structures group related data of different types under one name.

```c
struct Student {
    char name[50];
    int rollNo;
    float marks;
};

// Using structure
struct Student s1;
strcpy(s1.name, "Gaurav");
s1.rollNo = 101;
s1.marks = 85.5;
```

---

## Section 2: Python (Your Strength!)

### Q6: What are Python's key features?

**Answer:**
>
> 1. **Interpreted**: Executed line by line
> 2. **Dynamically Typed**: No type declaration needed
> 3. **Easy Syntax**: Readable, Pythonic code
> 4. **Extensive Libraries**: NumPy, Pandas, Flask
> 5. **Multi-paradigm**: Supports OOP and functional
> 6. **Portable**: Runs on Windows, Mac, Linux

### Q7: Explain List vs Tuple vs Set vs Dictionary

| Collection | Mutable | Ordered | Duplicates | Syntax |
|------------|---------|---------|------------|--------|
| **List** | Yes | Yes | Yes | `[1, 2, 3]` |
| **Tuple** | No | Yes | Yes | `(1, 2, 3)` |
| **Set** | Yes | No | No | `{1, 2, 3}` |
| **Dictionary** | Yes | Yes | Keys: No | `{"a": 1}` |

```python
# List - mutable, ordered
my_list = [1, 2, 3]
my_list.append(4)  # [1, 2, 3, 4]

# Tuple - immutable
my_tuple = (1, 2, 3)
# my_tuple[0] = 5  # Error!

# Set - unique elements
my_set = {1, 2, 2, 3}  # {1, 2, 3}

# Dictionary - key-value pairs
my_dict = {"name": "Gaurav", "age": 22}
```

### Q8: What is the difference between list and tuple?

| List | Tuple |
|------|-------|
| Mutable (can change) | Immutable (cannot change) |
| Slower | Faster |
| More memory | Less memory |
| Use for dynamic data | Use for fixed data |
| `[]` brackets | `()` parentheses |

### Q9: Explain List Comprehension

**Answer:**
> List comprehension is a concise way to create lists.

```python
# Traditional way
squares = []
for i in range(5):
    squares.append(i ** 2)

# List comprehension (one line!)
squares = [i ** 2 for i in range(5)]
# Output: [0, 1, 4, 9, 16]

# With condition
even_squares = [i ** 2 for i in range(10) if i % 2 == 0]
# Output: [0, 4, 16, 36, 64]
```

### Q10: What are *args and **kwargs?

**Answer:**

```python
# *args - variable number of positional arguments
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3, 4))  # 10

# **kwargs - variable number of keyword arguments
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Gaurav", age=22)
# name: Gaurav
# age: 22
```

### Q11: Explain exception handling in Python

**Answer:**

```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
except Exception as e:
    print(f"Other error: {e}")
else:
    print("No error occurred")
finally:
    print("This always runs")
```

### Q12: What is the difference between `==` and `is`?

**Answer:**

```python
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)   # True (same values)
print(a is b)   # False (different objects)
print(a is c)   # True (same object)
```

- `==` compares **values**
- `is` compares **identity** (memory location)

---

## Section 3: SQL (Your Strength!)

### Q13: What are the types of SQL commands?

| Type | Commands | Purpose |
|------|----------|---------|
| **DDL** (Data Definition) | CREATE, ALTER, DROP | Define structure |
| **DML** (Data Manipulation) | SELECT, INSERT, UPDATE, DELETE | Manipulate data |
| **DCL** (Data Control) | GRANT, REVOKE | Access control |
| **TCL** (Transaction Control) | COMMIT, ROLLBACK | Transaction management |

### Q14: Explain different types of JOINs

```sql
-- INNER JOIN - matching rows in both tables
SELECT * FROM A INNER JOIN B ON A.id = B.id;

-- LEFT JOIN - all from left, matching from right
SELECT * FROM A LEFT JOIN B ON A.id = B.id;

-- RIGHT JOIN - all from right, matching from left
SELECT * FROM A RIGHT JOIN B ON A.id = B.id;

-- FULL JOIN - all rows from both tables
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.id;
```

### Q15: Write a query to find the second highest salary

```sql
-- Method 1: Using LIMIT
SELECT salary FROM employees 
ORDER BY salary DESC 
LIMIT 1 OFFSET 1;

-- Method 2: Using subquery
SELECT MAX(salary) FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);
```

### Q16: What is the difference between WHERE and HAVING?

| WHERE | HAVING |
|-------|--------|
| Filters rows | Filters groups |
| Before GROUP BY | After GROUP BY |
| Cannot use aggregate functions | Can use aggregate functions |

```sql
-- WHERE filters before grouping
SELECT * FROM employees WHERE salary > 50000;

-- HAVING filters after grouping
SELECT department, AVG(salary) 
FROM employees 
GROUP BY department 
HAVING AVG(salary) > 50000;
```

### Q17: Explain GROUP BY with example

```sql
-- Count employees in each department
SELECT department, COUNT(*) as emp_count
FROM employees
GROUP BY department;

-- Average salary by department
SELECT department, AVG(salary) as avg_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC;
```

### Q18: What is normalization?

**Answer:**
> Normalization organizes data to reduce redundancy:
>
> - **1NF**: Atomic values, no repeating groups
> - **2NF**: 1NF + no partial dependencies
> - **3NF**: 2NF + no transitive dependencies

---

## Section 4: Data Structures & Algorithms

### Q19: Explain Time Complexity with Big O Notation

| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Array access by index |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Bubble sort |

### Q20: Write a function to reverse a string in Python

```python
# Method 1: Slicing (Pythonic)
def reverse_string(s):
    return s[::-1]

# Method 2: Two pointers
def reverse_string(s):
    s = list(s)
    left, right = 0, len(s) - 1
    while left < right:
        s[left], s[right] = s[right], s[left]
        left += 1
        right -= 1
    return ''.join(s)
```

### Q21: Write binary search in C

```c
int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    
    return -1;  // Not found
}
```

### Q22: What is the difference between Stack and Queue?

| Stack | Queue |
|-------|-------|
| LIFO (Last In First Out) | FIFO (First In First Out) |
| push/pop | enqueue/dequeue |
| Example: Undo functionality | Example: Print queue |

```python
# Stack using list
stack = []
stack.append(1)  # push
stack.pop()      # pop

# Queue using deque
from collections import deque
queue = deque()
queue.append(1)   # enqueue
queue.popleft()   # dequeue
```

---

## Section 5: SDLC & Software Engineering

### Q23: What is SDLC?

**Answer:**
> SDLC (Software Development Life Cycle) is a systematic process:
>
> 1. **Requirement Analysis**: Gather requirements
> 2. **Design**: System architecture
> 3. **Implementation**: Coding
> 4. **Testing**: Verify functionality
> 5. **Deployment**: Release to users
> 6. **Maintenance**: Ongoing support

### Q24: Explain Agile vs Waterfall

| Agile | Waterfall |
|-------|-----------|
| Iterative, incremental | Sequential, linear |
| Flexible to changes | Rigid phases |
| Continuous delivery | Delivery at end |
| Testing throughout | Testing after dev |
| Short sprints (2-4 weeks) | Long phases |

### Q25: What is Git? Explain basic commands

**Answer:**

```bash
git init              # Initialize repository
git clone <url>       # Clone remote repository
git add <file>        # Stage changes
git commit -m "msg"   # Commit with message
git push              # Push to remote
git pull              # Pull from remote
git branch            # List branches
git checkout <branch> # Switch branch
git merge <branch>    # Merge branch
```

---

## Section 6: Project-Based Questions

### Q26: Explain your Eye-Guard project

**Answer:**
> Eye-Guard is an AI-powered eye strain detection system developed as a team project:
>
> **Team:**
>
> - Gaurav Kumar Mehta (Backend) - That's me
> - Ayan Biswas (ML/AI)
> - Arpan Mirsha (Frontend)
> - Arka Bhattacharya (UI/UX)
>
> **My Contributions:**
>
> - Designed SQLite database schema for user data and sessions
> - Built Flask REST API endpoints for data handling
> - Implemented user session management
> - Created PDF report generation module
> - Integrated frontend with ML backend
>
> **Technologies I used:** Python, Flask, SQLite, REST APIs
>
> **Learning:** This project taught me API design, teamwork, and integrating different modules.

### Q27: If asked about TensorFlow/OpenCV

**How to answer:**
> "In our Eye-Guard project, my role was backend development. My teammate Ayan handled the machine learning using TensorFlow and OpenCV. I understand the overall system - it uses MediaPipe for face mesh detection and calculates Eye Aspect Ratio to detect strain. While I didn't write the ML code, I integrated the ML model's output with my Flask API to store results and generate reports."

---

## How to Handle Questions About Technologies You're Learning

### If asked about Java
>
> "I'm primarily experienced with C and Python. I've started learning Java and understand OOP concepts since they're similar. I'm confident I can pick up Java quickly with my strong programming foundation."

### If asked about REST APIs
>
> "I have basic experience building REST APIs with Flask in my Eye-Guard project. I understand the concepts of HTTP methods, status codes, and JSON data exchange. I'm eager to learn more about enterprise API development."

### If asked about MongoDB
>
> "I have used MongoDB at a basic level in our rental system project. I'm more experienced with SQL databases, but I understand the SQL vs NoSQL tradeoffs and am comfortable learning MongoDB in depth."

---

## Quick Tips for Technical Round

✅ Be honest about what you know and don't know  
✅ Think out loud - explain your approach  
✅ If stuck, explain how you would approach the problem  
✅ Relate questions to your project experience  
✅ It's okay to say "I don't know, but here's how I'd learn it"  
✅ Show enthusiasm for learning new technologies  

---

## Learning Resources 📚

### C Programming

- [GeeksforGeeks C](https://www.geeksforgeeks.org/c-programming-language/)
- [Learn C](https://www.learn-c.org/)

### Python

- [Real Python](https://realpython.com/)
- [Python Official Docs](https://docs.python.org/3/)

### SQL

- [SQLZoo](https://sqlzoo.net/)
- [Mode SQL Tutorial](https://mode.com/sql-tutorial/)

### DSA Practice

- [LeetCode](https://leetcode.com/)
- [HackerRank](https://www.hackerrank.com/)

---
*Focus on your strengths, be honest about learning areas!* 🚀
