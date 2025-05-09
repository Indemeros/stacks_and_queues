## Question 1

**Q**: What is the time complexity of a stack's push and pop operations?

**A**: O(1)

---

## Question 2

**Q**: In a queue implemented using a standard array, what is the time complexity of the dequeue operation?

**A**: O(n), because removing from the front requires shifting all remaining elements.

---

## Question 3

**Q**: What data structure would you use to implement an "undo" functionality in a text editor?

**A**: A stack, because it follows the Last-In-First-Out (LIFO) principle, matching the behavior of undoing the most recent action first.

---

## Question 4

**Q**: How can we implement a queue using two stacks?

**A**: Use stack1 for enqueue and stack2 for dequeue. When dequeuing, if stack2 is empty, pop all elements from stack1 and push to stack2, then pop from stack2.

---

## Question 5

**Q**: What is the difference between a regular queue and a priority queue?

**A**: A regular queue follows FIFO order. A priority queue retrieves elements based on their priority values rather than insertion order.