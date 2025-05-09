## Snippet 1: Stack Basics

A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle. Elements are added and removed from the same end, called the "top". Think of it like a stack of plates - you can only take from the top.

```python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        self.items.append(item)
    
    def pop(self):
        if not self.is_empty():
            return self.items.pop()
    
    def peek(self):
        if not self.is_empty():
            return self.items[-1]
    
    def is_empty(self):
        return len(self.items) == 0
```

## Snippet 2: Queue Basics

A queue is a linear data structure following the First-In-First-Out (FIFO) principle. Elements are added at the rear and removed from the front, like people waiting in line for a service.

```python
class Queue:
    def __init__(self):
        self.items = []
    
    def enqueue(self, item):
        self.items.append(item)
    
    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)
    
    def front(self):
        if not self.is_empty():
            return self.items[0]
    
    def is_empty(self):
        return len(self.items) == 0
```

## Snippet 3: Bracket Matching with Stack

Stacks excel at validating balanced expressions, like checking if brackets are properly matched in a formula. Push opening brackets onto the stack and pop when matching closing brackets are found.

```python
def is_balanced(expression):
    stack = []
    brackets = {')': '(', '}': '{', ']': '['}
    
    for char in expression:
        if char in '({[':
            stack.append(char)
        elif char in ')}]':
            if not stack or stack.pop() != brackets[char]:
                return False
    
    return len(stack) == 0
```

## Snippet 4: Queue Implementation with Two Stacks

A queue can be implemented using two stacks. Elements are pushed onto stack1 for enqueue operations. For dequeue, elements are moved to stack2 (reversing order) if stack2 is empty.

```python
class QueueUsingStacks:
    def __init__(self):
        self.stack1 = []  # for enqueue
        self.stack2 = []  # for dequeue
    
    def enqueue(self, item):
        self.stack1.append(item)
    
    def dequeue(self):
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop() if self.stack2 else None
```

## Snippet 5: Circular Queue

A circular queue optimizes array-based queue implementation by reusing space. When the rear reaches the end, it wraps around to the beginning if there's space, avoiding the need to shift elements.

```python
class CircularQueue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.queue = [None] * capacity
        self.front = self.size = 0
        self.rear = capacity - 1
    
    def enqueue(self, item):
        if self.size == self.capacity:
            return False
        self.rear = (self.rear + 1) % self.capacity
        self.queue[self.rear] = item
        self.size += 1
        return True
    
    def dequeue(self):
        if self.size == 0:
            return None
        item = self.queue[self.front]
        self.front = (self.front + 1) % self.capacity
        self.size -= 1
        return item
```

## Snippet 6: Priority Queue

A priority queue gives each element a priority and serves higher priority elements first. Often implemented using heaps, but this simple version uses a list with (priority, item) tuples.

```python
import heapq

class PriorityQueue:
    def __init__(self):
        self.elements = []
    
    def enqueue(self, item, priority):
        heapq.heappush(self.elements, (priority, item))
    
    def dequeue(self):
        if self.elements:
            return heapq.heappop(self.elements)[1]
        return None
```

## Snippet 7: Stack-based DFS

Depth-First Search uses a stack to explore as far as possible along each branch before backtracking. This makes stacks ideal for implementing iterative DFS traversals of graphs or trees.

```python
def dfs_iterative(graph, start):
    visited = set()
    stack = [start]
    
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            print(vertex, end=" ")
            visited.add(vertex)
            # Add neighbors in reverse order to match recursive DFS
            for neighbor in reversed(graph[vertex]):
                if neighbor not in visited:
                    stack.append(neighbor)
```

## Snippet 8: Queue-based BFS

Breadth-First Search uses a queue to explore all neighbors at the current depth before moving to nodes at the next depth level. Essential for finding shortest paths in unweighted graphs.

```python
def bfs(graph, start):
    visited = set([start])
    queue = [start]
    
    while queue:
        vertex = queue.pop(0)
        print(vertex, end=" ")
        
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```