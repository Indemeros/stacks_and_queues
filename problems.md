## Problem 1: Valid Parentheses

**Problem Statement**  
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid. A string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

**Example Input/Output:**
- Input: "()" → Output: True
- Input: "()[]{}" → Output: True
- Input: "(]" → Output: False
- Input: "([)]" → Output: False
- Input: "{[]}" → Output: True

---

### 🔹 Hints
1. Think about the Last-In-First-Out nature of brackets - the last opening bracket you see must be matched by the next closing bracket.
2. Consider using a stack data structure to keep track of open brackets.

### 🔹 Brute Force Idea  
We could try to match and remove pairs of brackets repeatedly until no more matches can be made. If the string becomes empty, it's valid. However, this would be inefficient as we'd need multiple passes through the string.

---

### 🔹 Optimized Idea  
Use a stack to keep track of opening brackets. When we encounter a closing bracket, it should match the most recent opening bracket (the one at the top of our stack). If it doesn't match or if the stack is empty when we find a closing bracket, the string is invalid. If we've gone through the whole string and our stack is empty, the string is valid.

---

### 🔹 Code Fragment
```python
def isValid(s):
    stack = []
    mapping = {")": "(", "}": "{", "]": "["}
    
    for char in s:
        # If it's an opening bracket, push to stack
        if char in "({[":
            stack.append(char)
        # If it's a closing bracket
        elif char in ")}]":
            # Stack shouldn't be empty and top should match
            if not stack or stack.pop() != mapping[char]:
                return False
    
    # If stack is empty, all brackets were matched
    return len(stack) == 0
```

## Problem 2: Implement Queue using Stacks

**Problem Statement**  
Implement a queue using only two stacks. The queue should support all the regular queue operations: enqueue, dequeue, peek, and isEmpty.

**Example:**
```
MyQueue queue = new MyQueue();
queue.enqueue(1);
queue.enqueue(2);  
queue.peek();  // returns 1
queue.dequeue();  // returns 1
queue.isEmpty();  // returns false
```

---

### 🔹 Hints
1. How can you reverse the order of elements?
2. When should you transfer elements between stacks?

### 🔹 Brute Force Idea  
For every enqueue operation, pop all elements from stack1, push the new element, then push back all elements. For dequeue, simply pop from stack1. This ensures FIFO order but makes enqueue O(n).

---

### 🔹 Optimized Idea  
Use stack1 for enqueue operations and stack2 for dequeue. For enqueue, simply push to stack1. For dequeue, if stack2 is empty, pop all elements from stack1 and push to stack2 (which reverses their order), then pop from stack2. This gives amortized O(1) time complexity for both operations.

---

### 🔹 Code Fragment
```python
class MyQueue:
    def __init__(self):
        self.stack1 = []  # for enqueue
        self.stack2 = []  # for dequeue
        
    def enqueue(self, x):
        self.stack1.append(x)
    
    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop() if self.stack2 else None
        
    def peek(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2[-1] if self.stack2 else None
        
    def isEmpty(self):
        return not self.stack1 and not self.stack2
```

## Problem 3: Next Greater Element

**Problem Statement**  
Given an array, return an array where each element is the next greater element for the original array. If there is no greater element, use -1.

**Example Input/Output:**
- Input: [4, 5, 2, 25] → Output: [5, 25, 25, -1]
- Input: [13, 7, 6, 12] → Output: [−1, 12, 12, -1]

---

### 🔹 Hints
1. Can you use a stack to avoid nested loops?
2. Consider processing the array from right to left.

### 🔹 Brute Force Idea  
Use nested loops: for each element, scan to its right to find the first greater element. This has O(n²) time complexity.

---

### 🔹 Optimized Idea  
Use a stack to keep track of elements we've seen but haven't found the next greater element for. Process the array from right to left. For each element:
1. Pop elements from stack that are smaller than current element (they can't be the next greater for any future elements)
2. The next greater element for current is the top of stack (or -1 if empty)
3. Push current element to stack
This approach has O(n) time complexity.

---

### 🔹 Code Fragment
```python
def nextGreaterElements(nums):
    n = len(nums)
    result = [-1] * n
    stack = []
    
    for i in range(n-1, -1, -1):
        # Pop smaller elements
        while stack and stack[-1] <= nums[i]:
            stack.pop()
        
        # Assign next greater or -1
        if stack:
            result[i] = stack[-1]
        
        # Push current element
        stack.append(nums[i])
    
    return result
```

## Problem 4: Maximum of Sliding Window

**Problem Statement**  
Given an array and a sliding window size k, find the maximum element in each sliding window as it moves from left to right.

**Example Input/Output:**
- Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
- Output: [3,3,5,5,6,7]
  
Explanation:
```
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

---

### 🔹 Hints
1. Consider using a deque (double-ended queue) to efficiently track potential maximum values.
2. We only need to keep elements that could be the maximum of some window.

### 🔹 Brute Force Idea  
For each window position, find the maximum by scanning all k elements in the window. This would be O(n*k) time complexity.

---

### 🔹 Optimized Idea  
Use a deque to store indices of elements in current window that could potentially be maximum for some window. Maintain the deque such that:
1. Elements in deque are in decreasing order
2. Remove elements outside current window
3. Add new elements, removing smaller elements that can't be maximum
This gives O(n) time complexity as each element is processed at most twice.

---

### 🔹 Code Fragment
```python
from collections import deque

def maxSlidingWindow(nums, k):
    result = []
    dq = deque()  # stores indices
    
    for i in range(len(nums)):
        # Remove elements outside current window
        while dq and dq[0] < i - k + 1:
            dq.popleft()
        
        # Remove smaller elements as they can't be maximum
        while dq and nums[dq[-1]] < nums[i]:
            dq.pop()
        
        dq.append(i)
        
        # Add to result if we've reached window size
        if i >= k - 1:
            result.append(nums[dq[0]])
    
    return result
```