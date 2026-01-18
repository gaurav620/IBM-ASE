# Coding Round Preparation 💻

## About This Round

The coding round tests your programming skills with DSA problems. You'll typically have 30-60 minutes to solve 2-3 problems. Focus on correctness, efficiency, and code quality.

---

## Section 1: Arrays & Strings

### Problem 1: Two Sum ⭐ (Easy)

**Problem:** Given an array of integers and a target, return indices of two numbers that add up to target.

```python
# Python Solution
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []

# Example
print(two_sum([2, 7, 11, 15], 9))  # Output: [0, 1]
```

```java
// Java Solution
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[] {map.get(complement), i};
        }
        map.put(nums[i], i);
    }
    return new int[] {};
}
```

**Time Complexity:** O(n) | **Space Complexity:** O(n)

---

### Problem 2: Reverse String ⭐ (Easy)

**Problem:** Reverse a string in-place.

```python
# Python Solution
def reverse_string(s):
    left, right = 0, len(s) - 1
    while left < right:
        s[left], s[right] = s[right], s[left]
        left += 1
        right -= 1
    return s

# Example
print(reverse_string(list("hello")))  # Output: ['o', 'l', 'l', 'e', 'h']
```

```java
// Java Solution
public void reverseString(char[] s) {
    int left = 0, right = s.length - 1;
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }
}
```

**Time Complexity:** O(n) | **Space Complexity:** O(1)

---

### Problem 3: Find Duplicates in Array ⭐⭐ (Medium)

**Problem:** Find all duplicate numbers in an array where 1 ≤ a[i] ≤ n.

```python
# Python Solution
def find_duplicates(nums):
    result = []
    for num in nums:
        index = abs(num) - 1
        if nums[index] < 0:
            result.append(abs(num))
        else:
            nums[index] = -nums[index]
    return result

# Example
print(find_duplicates([4, 3, 2, 7, 8, 2, 3, 1]))  # Output: [2, 3]
```

**Time Complexity:** O(n) | **Space Complexity:** O(1)

---

### Problem 4: Longest Substring Without Repeating Characters ⭐⭐ (Medium)

**Problem:** Find the length of the longest substring without repeating characters.

```python
# Python Solution (Sliding Window)
def length_of_longest_substring(s):
    char_set = set()
    left = 0
    max_length = 0
    
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)
    
    return max_length

# Example
print(length_of_longest_substring("abcabcbb"))  # Output: 3 ("abc")
```

**Time Complexity:** O(n) | **Space Complexity:** O(min(n, m))

---

## Section 2: Linked Lists

### Problem 5: Reverse Linked List ⭐ (Easy)

```python
# Python Solution
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_list(head):
    prev = None
    curr = head
    
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node
    
    return prev
```

```java
// Java Solution
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

**Time Complexity:** O(n) | **Space Complexity:** O(1)

---

### Problem 6: Detect Cycle in Linked List ⭐⭐ (Medium)

```python
# Python Solution (Floyd's Algorithm)
def has_cycle(head):
    slow = fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    
    return False
```

**Time Complexity:** O(n) | **Space Complexity:** O(1)

---

### Problem 7: Merge Two Sorted Lists ⭐ (Easy)

```python
# Python Solution
def merge_two_lists(l1, l2):
    dummy = ListNode(0)
    current = dummy
    
    while l1 and l2:
        if l1.val <= l2.val:
            current.next = l1
            l1 = l1.next
        else:
            current.next = l2
            l2 = l2.next
        current = current.next
    
    current.next = l1 if l1 else l2
    return dummy.next
```

**Time Complexity:** O(n + m) | **Space Complexity:** O(1)

---

## Section 3: Stack & Queue

### Problem 8: Valid Parentheses ⭐ (Easy)

**Problem:** Check if string has valid bracket matching.

```python
# Python Solution
def is_valid(s):
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    
    for char in s:
        if char in mapping:
            top = stack.pop() if stack else '#'
            if mapping[char] != top:
                return False
        else:
            stack.append(char)
    
    return len(stack) == 0

# Example
print(is_valid("()[]{}"))  # Output: True
print(is_valid("([)]"))    # Output: False
```

**Time Complexity:** O(n) | **Space Complexity:** O(n)

---

### Problem 9: Implement Queue using Stacks ⭐⭐ (Medium)

```python
# Python Solution
class MyQueue:
    def __init__(self):
        self.stack_in = []
        self.stack_out = []
    
    def push(self, x):
        self.stack_in.append(x)
    
    def pop(self):
        self._move()
        return self.stack_out.pop()
    
    def peek(self):
        self._move()
        return self.stack_out[-1]
    
    def empty(self):
        return not self.stack_in and not self.stack_out
    
    def _move(self):
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
```

---

## Section 4: Trees

### Problem 10: Binary Tree Inorder Traversal ⭐ (Easy)

```python
# Python Solution (Iterative)
def inorder_traversal(root):
    result = []
    stack = []
    current = root
    
    while current or stack:
        while current:
            stack.append(current)
            current = current.left
        current = stack.pop()
        result.append(current.val)
        current = current.right
    
    return result
```

---

### Problem 11: Maximum Depth of Binary Tree ⭐ (Easy)

```python
# Python Solution (Recursive)
def max_depth(root):
    if not root:
        return 0
    return 1 + max(max_depth(root.left), max_depth(root.right))
```

```java
// Java Solution
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}
```

**Time Complexity:** O(n) | **Space Complexity:** O(h)

---

### Problem 12: Validate Binary Search Tree ⭐⭐ (Medium)

```python
# Python Solution
def is_valid_bst(root, min_val=float('-inf'), max_val=float('inf')):
    if not root:
        return True
    
    if root.val <= min_val or root.val >= max_val:
        return False
    
    return (is_valid_bst(root.left, min_val, root.val) and 
            is_valid_bst(root.right, root.val, max_val))
```

---

## Section 5: Sorting & Searching

### Problem 13: Binary Search ⭐ (Easy)

```python
# Python Solution
def binary_search(nums, target):
    left, right = 0, len(nums) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1

# Example
print(binary_search([1, 2, 3, 4, 5, 6], 4))  # Output: 3
```

**Time Complexity:** O(log n) | **Space Complexity:** O(1)

---

### Problem 14: Merge Sort ⭐⭐ (Medium)

```python
# Python Solution
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

**Time Complexity:** O(n log n) | **Space Complexity:** O(n)

---

### Problem 15: Quick Sort ⭐⭐ (Medium)

```python
# Python Solution
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)
```

**Time Complexity:** O(n log n) avg, O(n²) worst | **Space Complexity:** O(log n)

---

## Section 6: Dynamic Programming

### Problem 16: Fibonacci Number ⭐ (Easy)

```python
# Python Solution (DP - Bottom Up)
def fibonacci(n):
    if n <= 1:
        return n
    
    dp = [0, 1]
    for i in range(2, n + 1):
        dp.append(dp[i-1] + dp[i-2])
    
    return dp[n]

# Space Optimized
def fibonacci_optimized(n):
    if n <= 1:
        return n
    
    prev, curr = 0, 1
    for _ in range(2, n + 1):
        prev, curr = curr, prev + curr
    
    return curr
```

---

### Problem 17: Climbing Stairs ⭐ (Easy)

**Problem:** How many distinct ways to climb n stairs if you can take 1 or 2 steps?

```python
# Python Solution
def climb_stairs(n):
    if n <= 2:
        return n
    
    prev, curr = 1, 2
    for _ in range(3, n + 1):
        prev, curr = curr, prev + curr
    
    return curr

# Example
print(climb_stairs(5))  # Output: 8
```

---

### Problem 18: Longest Common Subsequence ⭐⭐ (Medium)

```python
# Python Solution
def lcs(text1, text2):
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i-1] == text2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    
    return dp[m][n]

# Example
print(lcs("abcde", "ace"))  # Output: 3
```

---

## Section 7: Pattern-Based Problems

### Problem 19: Print Pattern - Diamond ⭐ (Easy)

```python
def print_diamond(n):
    # Upper half
    for i in range(1, n + 1):
        print(' ' * (n - i) + '*' * (2 * i - 1))
    
    # Lower half
    for i in range(n - 1, 0, -1):
        print(' ' * (n - i) + '*' * (2 * i - 1))

print_diamond(4)
# Output:
#    *
#   ***
#  *****
# *******
#  *****
#   ***
#    *
```

---

### Problem 20: Number Pyramid ⭐ (Easy)

```python
def number_pyramid(n):
    for i in range(1, n + 1):
        print(' ' * (n - i) + ' '.join(str(j) for j in range(1, i + 1)))

number_pyramid(5)
# Output:
#     1
#    1 2
#   1 2 3
#  1 2 3 4
# 1 2 3 4 5
```

---

## Problem-Solving Framework (UMPIRE)

When solving any coding problem, follow this approach:

1. **U**nderstand: Clarify the problem, inputs, outputs, constraints
2. **M**atch: Relate to known patterns (Two Pointers, Sliding Window, etc.)
3. **P**lan: Write pseudocode before coding
4. **I**mplement: Translate plan to code
5. **R**eview: Check edge cases, dry run
6. **E**valuate: Analyze time/space complexity

---

## Common Patterns to Remember

| Pattern | Use Case | Example |
|---------|----------|---------|
| **Two Pointers** | Sorted array, pairs | Two Sum II |
| **Sliding Window** | Subarray problems | Max subarray sum |
| **Fast/Slow Pointer** | Cycle detection | Linked list cycle |
| **Binary Search** | Sorted data, O(log n) | Search in rotated array |
| **BFS/DFS** | Graph/Tree traversal | Level order traversal |
| **Dynamic Programming** | Optimization, counting | Fibonacci, LCS |
| **Greedy** | Local optimal = Global | Activity Selection |

---

## Tips for Coding Round

✅ Read the problem carefully  
✅ Ask clarifying questions  
✅ Start with brute force, then optimize  
✅ Write clean, readable code  
✅ Handle edge cases (empty, null, single element)  
✅ Test with examples before submitting  
✅ Analyze and state time/space complexity  
✅ Practice on LeetCode, HackerRank daily  

---

## Practice Resources

- [LeetCode](https://leetcode.com) - Company-specific problems
- [HackerRank](https://hackerrank.com) - IBM partner platform
- [GeeksforGeeks](https://geeksforgeeks.org) - Concept explanations
- [NeetCode](https://neetcode.io) - Curated problem lists

---
*Happy Coding!* 🎯
