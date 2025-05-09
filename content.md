📘 Topic: Stacks and Queues
🧠 Overview
Stacks and queues are fundamental linear data structures used for storing and retrieving data in a particular order. These structures are essential building blocks for solving various computational problems and are implemented across many algorithms and systems.

A stack follows the Last-In-First-Out (LIFO) principle, while a queue follows the First-In-First-Out (FIFO) principle, making them suitable for different types of operations and algorithms.

⏱ Operations and Time Complexity

## Stack Operations
| Operation | Time Complexity | Description |
|-----------|----------------|-------------|
| Push      | O(1)           | Add element to top |
| Pop       | O(1)           | Remove element from top |
| Peek/Top  | O(1)           | View top element without removal |
| isEmpty   | O(1)           | Check if stack is empty |
| Size      | O(1)           | Get number of elements |

## Queue Operations
| Operation | Time Complexity | Description |
|-----------|----------------|-------------|
| Enqueue   | O(1)           | Add element to rear |
| Dequeue   | O(1)           | Remove element from front |
| Front     | O(1)           | View front element without removal |
| isEmpty   | O(1)           | Check if queue is empty |
| Size      | O(1)           | Get number of elements |

❗ Implementation Approaches

## Stack Implementations
1. **Array-based**: 
   - Easy to implement
   - Fixed size (unless using dynamic arrays)
   - Memory efficient

2. **Linked List-based**:
   - Dynamic size
   - Extra memory for pointers
   - Push and pop at head for O(1) operations

## Queue Implementations
1. **Array-based**:
   - Circular array prevents wasting space
   - Fixed size limitation
   - Requires tracking front and rear indices

2. **Linked List-based**:
   - Dynamic size
   - Requires tracking front and rear pointers
   - Enqueue at rear, dequeue from front

💾 Space Complexity
Both stacks and queues typically have O(n) space complexity where n is the number of elements stored.

🔄 Common Applications

## Stack Applications
- **Function Call Management**: Call stack for tracking function calls and returns
- **Expression Evaluation**: Parsing arithmetic expressions, bracket matching
- **Undo/Redo Operations**: Tracking operations for reversing
- **Depth-First Search**: Tracking nodes to visit in graph traversal
- **Backtracking Algorithms**: Storing states during search

## Queue Applications
- **Breadth-First Search**: Level-order traversal in graphs and trees
- **CPU Scheduling**: Managing processes in operating systems
- **Buffering**: Managing data transfer between processes
- **IO Buffers**: Managing input/output operations
- **Print Queue Management**: Handling print jobs in order

📈 Comparing Stack vs Queue

| Aspect | Stack (LIFO) | Queue (FIFO) |
|--------|-------------|-------------|
| Order | Last-In-First-Out | First-In-First-Out |
| Ends | Single-ended | Double-ended |
| Access | Only top element | Front and rear elements |
| Use Case | When order reversal is needed | When processing in arrival order |
| Traversal | DFS | BFS |

## Variations

### Stack Variations
- **Min/Max Stack**: Tracks minimum/maximum element in O(1) time
- **Double-ended Stack**: Operations at both ends

### Queue Variations
- **Priority Queue**: Elements have priority values
- **Deque (Double-Ended Queue)**: Insertions/deletions at both ends
- **Circular Queue**: Array implementation that reuses space

🧩 Key Takeaways
- Stacks and queues provide O(1) time complexity for core operations
- The choice between stack and queue depends on the required access pattern
- Stack: Use when the most recently added item needs to be processed first (LIFO)
- Queue: Use when items need to be processed in the order they were added (FIFO)
- Both structures are essential for implementing many algorithms and systems
- Understanding their properties helps in choosing the right data structure for specific problems