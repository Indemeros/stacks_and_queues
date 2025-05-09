## Snippet 1: Stack Basics

A stack is like a pile of plates - you can only add or remove from the top. This is called Last-In-First-Out (LIFO). Imagine a stack of books: the last book you put on top is the first one you'll pick up. Stacks have simple operations: push (add to top), pop (remove from top), and peek (look at top without removing). They're great for tracking recent items or steps.

```python
# Simple stack using a list
stack = []
stack.append("item1")  # push
stack.append("item2")  # push
top_item = stack.pop()  # removes and returns "item2"
```

## Snippet 2: Queue Basics

A queue works like a line at a store - the first person to arrive gets served first (First-In-First-Out or FIFO). New items join at the back (enqueue) and leave from the front (dequeue). Think of a printer queue: documents print in the order they were sent. Queues are perfect when things need to be processed in the exact order they arrived.

```python
# Simple queue using a list
queue = []
queue.append("first")  # enqueue
queue.append("second")  # enqueue
first_item = queue.pop(0)  # dequeue returns "first"
```

## Snippet 3: Bracket Matching with Stack

Stacks are perfect for checking if brackets in code are balanced (every opening bracket has a matching closing bracket). When you see an opening bracket like '(' or '{', push it onto the stack. When you see a closing bracket, pop from the stack and check if it matches. If the stack is empty at the end, all brackets are matched properly!

```python
def is_balanced(text):
    stack = []
    for char in text:
        if char in "({[":
            stack.append(char)
        elif char in ")}]" and (not stack or not matches(stack.pop(), char)):
            return False
    return len(stack) == 0
```

## Snippet 4: Circular Queue

A circular queue is like a regular queue but connected end-to-end, like a circle. When we reach the end of the array, we wrap around to the beginning if there's space. This fixes the problem of wasting space at the front after dequeuing items. It needs two pointers: front (for dequeue) and rear (for enqueue), plus a way to track if it's full or empty.

## Snippet 5: Priority Queue

A priority queue is like a special line where people with emergencies get helped first. Each item has a priority value, and items with higher priority come out first, regardless of when they were added. This is different from regular queues where order of arrival matters. They're commonly used in hospital emergency rooms, task scheduling, and network routing.

## Snippet 6: Stack in Function Calls

When your program calls functions, the computer uses a stack behind the scenes called the "call stack." When a function is called, it's pushed onto the stack. When the function finishes, it's popped off. This lets the program remember where to return after each function completes. If you call too many functions without returning (like in infinite recursion), you get a "stack overflow" error.

## Snippet 7: Stack-based DFS

Depth-First Search explores a graph or tree by going as deep as possible before backtracking. A stack helps us remember where to go when we hit a dead end. We start at one node, then explore one neighbor completely before trying others. DFS is like exploring a maze by always following the left wall - you'll eventually explore the whole maze, going deep into each path before trying new routes.

## Snippet 8: Queue-based BFS

Breadth-First Search explores a graph level by level, like ripples spreading from a stone dropped in water. We use a queue to visit all neighbors at the current depth before moving deeper. BFS is perfect for finding the shortest path in unweighted graphs. Imagine searching for a book in a library by first checking nearby shelves, then gradually moving to farther shelves.