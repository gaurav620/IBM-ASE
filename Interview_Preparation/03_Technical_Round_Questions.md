# Technical Round Interview Questions & Answers 🖥️

## About This Round

The technical round evaluates your programming knowledge, problem-solving abilities, and understanding of core CS concepts. IBM looks for Java, C++, Python, Node.js skills and SDLC understanding.

---

## Section 1: Programming Languages

### Java Questions

#### Q1: What are the main features of Java?

**Answer:**
>
> 1. **Platform Independent**: Write once, run anywhere (WORA)
> 2. **Object-Oriented**: Based on OOP concepts (Encapsulation, Inheritance, Polymorphism, Abstraction)
> 3. **Robust**: Strong memory management and exception handling
> 4. **Secure**: No explicit pointers, bytecode verification
> 5. **Multithreaded**: Built-in support for concurrent programming
> 6. **Automatic Memory Management**: Garbage collection

#### Q2: Explain OOP concepts with examples

**Answer:**

**1. Encapsulation**: Bundling data and methods that operate on that data within a class.

```java
public class Employee {
    private String name;  // private data
    
    public String getName() {  // public method
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```

**2. Inheritance**: A class can inherit properties and methods from another class.

```java
class Animal {
    void eat() { System.out.println("Eating..."); }
}
class Dog extends Animal {
    void bark() { System.out.println("Barking..."); }
}
```

**3. Polymorphism**: Same method behaves differently based on the object.

```java
class Shape {
    void draw() { System.out.println("Drawing shape"); }
}
class Circle extends Shape {
    @Override
    void draw() { System.out.println("Drawing circle"); }
}
```

**4. Abstraction**: Hiding implementation details, showing only functionality.

```java
abstract class Vehicle {
    abstract void start();  // abstract method
}
class Car extends Vehicle {
    void start() { System.out.println("Car started"); }
}
```

#### Q3: What is the difference between ArrayList and LinkedList?

| Feature | ArrayList | LinkedList |
|---------|-----------|------------|
| **Structure** | Dynamic array | Doubly linked list |
| **Access Time** | O(1) | O(n) |
| **Insert/Delete** | O(n) | O(1) at ends |
| **Memory** | Less overhead | More (node pointers) |
| **Use Case** | Frequent access | Frequent insert/delete |

#### Q4: Explain Exception Handling in Java

**Answer:**
> Exception handling manages runtime errors gracefully using:
>
> - **try**: Block containing code that may throw exception
> - **catch**: Handles the exception
> - **finally**: Always executes (cleanup code)
> - **throw**: Explicitly throw an exception
> - **throws**: Declare exceptions a method might throw

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero: " + e.getMessage());
} finally {
    System.out.println("Cleanup code here");
}
```

#### Q5: What is the difference between == and .equals() in Java?

**Answer:**
>
> - `==` compares **reference** (memory addresses)
> - `.equals()` compares **content/value**

```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);       // false (different objects)
System.out.println(s1.equals(s2));  // true (same content)
```

---

### Python Questions

#### Q6: What are Python's key features?

**Answer:**
>
> 1. **Interpreted**: Executed line by line
> 2. **Dynamically Typed**: No variable type declaration needed
> 3. **High-Level**: Abstracted from machine details
> 4. **Extensive Libraries**: NumPy, Pandas, TensorFlow, Flask
> 5. **Readable Syntax**: Clean, Pythonic code
> 6. **Object-Oriented and Functional**: Supports both paradigms

#### Q7: Explain List vs Tuple vs Set vs Dictionary

| Collection | Mutable | Ordered | Duplicates | Syntax |
|------------|---------|---------|------------|--------|
| **List** | Yes | Yes | Yes | `[1, 2, 3]` |
| **Tuple** | No | Yes | Yes | `(1, 2, 3)` |
| **Set** | Yes | No | No | `{1, 2, 3}` |
| **Dictionary** | Yes | Yes* | Keys: No | `{"a": 1}` |

*Python 3.7+ maintains insertion order

#### Q8: What are decorators in Python?

**Answer:**
> Decorators are functions that modify the behavior of other functions without changing their code.

```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function call
# Hello!
# After function call
```

#### Q9: Explain List Comprehension

**Answer:**
> List comprehension is a concise way to create lists.

```python
# Traditional way
squares = []
for i in range(5):
    squares.append(i ** 2)

# List comprehension
squares = [i ** 2 for i in range(5)]
# Output: [0, 1, 4, 9, 16]

# With condition
even_squares = [i ** 2 for i in range(10) if i % 2 == 0]
# Output: [0, 4, 16, 36, 64]
```

---

### JavaScript/Node.js Questions

#### Q10: What is the difference between var, let, and const?

| Feature | var | let | const |
|---------|-----|-----|-------|
| **Scope** | Function | Block | Block |
| **Hoisting** | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |
| **Reassignment** | Yes | Yes | No |
| **Redeclaration** | Yes | No | No |

```javascript
if (true) {
    var a = 1;   // accessible outside block
    let b = 2;   // block-scoped
    const c = 3; // block-scoped, immutable
}
console.log(a); // 1
console.log(b); // ReferenceError
```

#### Q11: Explain Promises and async/await

**Answer:**
> Promises handle asynchronous operations without callback hell.

```javascript
// Promise
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => resolve("Data fetched"), 1000);
    });
}

fetchData().then(data => console.log(data));

// async/await (cleaner syntax)
async function getData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

#### Q12: What is Event Loop in Node.js?

**Answer:**
> The Event Loop allows Node.js to perform non-blocking I/O operations despite JavaScript being single-threaded. It:
>
> 1. Executes code in the call stack
> 2. Offloads async operations to the OS/thread pool
> 3. Pushes completed callbacks to the callback queue
> 4. Picks tasks from queue when call stack is empty

---

## Section 2: Data Structures & Algorithms

#### Q13: Explain Time Complexity with Big O Notation

| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Array access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Bubble sort |
| O(2ⁿ) | Exponential | Recursive Fibonacci |

#### Q14: What is the difference between Stack and Queue?

| Feature | Stack | Queue |
|---------|-------|-------|
| **Order** | LIFO (Last In First Out) | FIFO (First In First Out) |
| **Operations** | push/pop | enqueue/dequeue |
| **Example** | Undo functionality | Task scheduling |

#### Q15: Explain Binary Search Tree (BST)

**Answer:**
> A BST is a tree data structure where:
>
> - Left subtree contains nodes with values less than parent
> - Right subtree contains nodes with values greater than parent
> - Both subtrees are also BSTs

**Operations:**

- Search: O(log n) average, O(n) worst
- Insert: O(log n) average
- Delete: O(log n) average

```java
class TreeNode {
    int val;
    TreeNode left, right;
    
    TreeNode(int val) {
        this.val = val;
    }
}
```

#### Q16: Write a function to reverse a linked list

```java
public ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode curr = head;
    
    while (curr != null) {
        ListNode next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    
    return prev;
}
```

---

## Section 3: SDLC & Software Engineering

#### Q17: What is Software Development Life Cycle (SDLC)?

**Answer:**
> SDLC is a systematic process for developing software:
>
> 1. **Requirement Analysis**: Gather and document requirements
> 2. **Design**: System architecture and design specifications
> 3. **Implementation**: Coding and development
> 4. **Testing**: Verification and validation
> 5. **Deployment**: Release to production
> 6. **Maintenance**: Ongoing support and updates

#### Q18: Explain Agile vs Waterfall

| Aspect | Agile | Waterfall |
|--------|-------|-----------|
| **Approach** | Iterative, incremental | Sequential, linear |
| **Flexibility** | High, welcomes change | Low, rigid phases |
| **Delivery** | Continuous (sprints) | End of project |
| **Testing** | Throughout development | After development |
| **Best For** | Dynamic requirements | Fixed, clear requirements |

#### Q19: What is Git? Explain basic commands

**Answer:**
> Git is a distributed version control system.

**Basic Commands:**

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

#### Q20: What is REST API?

**Answer:**
> REST (Representational State Transfer) is an architectural style for web services.

**Principles:**

1. **Stateless**: Each request is independent
2. **Client-Server**: Separation of concerns
3. **Uniform Interface**: Consistent resource access
4. **Cacheable**: Responses can be cached

**HTTP Methods:**

| Method | Purpose |
|--------|---------|
| GET | Retrieve data |
| POST | Create new resource |
| PUT | Update resource |
| DELETE | Remove resource |

---

## Section 4: Database Questions

#### Q21: What is the difference between SQL and NoSQL?

| Feature | SQL | NoSQL |
|---------|-----|-------|
| **Structure** | Tables, rows | Documents, key-value |
| **Schema** | Fixed | Flexible |
| **Scaling** | Vertical | Horizontal |
| **ACID** | Yes | Eventually consistent |
| **Examples** | MySQL, PostgreSQL | MongoDB, Cassandra |

#### Q22: What is Normalization?

**Answer:**
> Normalization organizes data to reduce redundancy:
>
> - **1NF**: Eliminate repeating groups, atomic values
> - **2NF**: 1NF + eliminate partial dependencies
> - **3NF**: 2NF + eliminate transitive dependencies
> - **BCNF**: 3NF + every determinant is a candidate key

#### Q23: Explain ACID properties

**Answer:**
>
> - **Atomicity**: All or nothing transactions
> - **Consistency**: Data remains valid after transaction
> - **Isolation**: Concurrent transactions don't interfere
> - **Durability**: Committed data persists even after failure

---

## Section 5: Project-Based Questions

#### Q24: Explain your Eye-Guard project technically

**Answer:**
> Eye-Guard is an AI-powered eye strain detection system:
>
> **Architecture:**
>
> - **Input**: Real-time webcam feed
> - **Processing**: MediaPipe for facial landmark detection (468 points)
> - **Algorithm**: Eye Aspect Ratio (EAR) calculation
> - **Model**: TensorFlow for classification (98% accuracy)
> - **Backend**: Flask REST API
> - **Frontend**: Interactive dashboard
> - **Output**: PDF reports with analytics
>
> **Technical Implementation:**
>
> ```python
> def calculate_ear(eye_landmarks):
>     # Compute distances
>     A = distance(p1, p5)  # Vertical
>     B = distance(p2, p4)  # Vertical
>     C = distance(p0, p3)  # Horizontal
>     
>     ear = (A + B) / (2.0 * C)
>     return ear
> ```
>
> **Challenges Solved:**
>
> - Real-time processing optimization
> - Lighting condition handling
> - Cross-browser compatibility

#### Q25: How would you improve your project for scale?

**Answer:**
> To scale Eye-Guard:
>
> 1. **Microservices**: Split into detection, analytics, and reporting services
> 2. **Message Queue**: Use RabbitMQ/Redis for async processing
> 3. **Caching**: Redis for session and result caching
> 4. **Load Balancing**: Nginx for distributing traffic
> 5. **Containerization**: Docker + Kubernetes for deployment
> 6. **CDN**: For static assets and faster delivery
> 7. **Database**: Switch to PostgreSQL for better concurrency

---

## Quick Tips for Technical Round

✅ Think out loud - explain your approach  
✅ Ask clarifying questions  
✅ Write clean, readable code  
✅ Consider edge cases  
✅ Know the time/space complexity  
✅ Be honest if you don't know something  
✅ Relate concepts to your projects  

---
*Best of luck!* 🚀

---

## Learning Resources 📚

### Java

- [Oracle Java Tutorials](https://docs.oracle.com/javase/tutorial/) - Official docs
- [GeeksforGeeks Java](https://www.geeksforgeeks.org/java/) - Complete guide
- [Javatpoint](https://www.javatpoint.com/java-tutorial) - Beginner-friendly

### Python

- [Real Python](https://realpython.com/) - Practical tutorials
- [Python Official Docs](https://docs.python.org/3/) - Reference
- [Automate the Boring Stuff](https://automatetheboringstuff.com/) - Free book

### JavaScript/Node.js

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - Best reference
- [JavaScript.info](https://javascript.info/) - Modern tutorial
- [Node.js Docs](https://nodejs.org/en/docs/) - Official

### DSA

- [NeetCode Roadmap](https://neetcode.io/roadmap) - Structured path
- [Visualgo](https://visualgo.net/) - Algorithm visualization
- [Abdul Bari YouTube](https://www.youtube.com/channel/UCZCFT11CWBi3MHNlGf019nw) - Video tutorials

### SDLC & Git

- [Atlassian SDLC Guide](https://www.atlassian.com/blog/software-teams/sdlc-phases) - Concepts
- [Git Official](https://git-scm.com/doc) - Documentation
- [Learn Git Branching](https://learngitbranching.js.org/) - Interactive

### SQL

- [SQLZoo](https://sqlzoo.net/) - Practice
- [Mode SQL](https://mode.com/sql-tutorial/) - Interactive
- [LeetCode SQL](https://leetcode.com/problemset/database/) - Problems

### Video Courses (YouTube)

- [Java Brains](https://www.youtube.com/user/koaborsa) - Java
- [Corey Schafer](https://www.youtube.com/user/schaaborsa) - Python
- [Traversy Media](https://www.youtube.com/user/TechGuyWeb) - Web Dev
