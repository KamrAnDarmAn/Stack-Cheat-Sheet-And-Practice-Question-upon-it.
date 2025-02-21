# Stack Cheat Sheet

## 1. Stack Overview

A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle. The last element inserted is the first to be removed.

### Applications of Stack:

- Function Call Stack
- Undo/Redo operations in text editors
- Expression Evaluation (Postfix, Prefix, Infix conversion)
- Backtracking (e.g., Maze solving, DFS)
- Parenthesis matching
- Memory management (Recursion)

## 2. Stack Abstract Data Type (ADT)

A stack ADT supports the following operations:

1. **push(x)** → Inserts element `x` at the top.
2. **pop()** → Removes and returns the top element.
3. **peek() / top()** → Returns the top element without removing it.
4. **isEmpty()** → Checks if the stack is empty.
5. **isFull()** → Checks if the stack is full (in case of array implementation).

## 3. Stack Implementation

### 3.1 Stack Using Arrays

```cpp
#include <iostream>
#define MAX 100 // Maximum size of stack
using namespace std;

class Stack {
    int top;
    int arr[MAX];

public:
    Stack() { top = -1; }
    bool isEmpty() { return top == -1; }
    bool isFull() { return top == MAX - 1; }
    void push(int x) {
        if (isFull()) { cout << "Stack Overflow!" << endl; return; }
        arr[++top] = x;
    }
    int pop() {
        if (isEmpty()) { cout << "Stack Underflow!" << endl; return -1; }
        return arr[top--];
    }
    int peek() { return (isEmpty()) ? -1 : arr[top]; }
};

int main() {
    Stack s;
    s.push(10);
    s.push(20);
    cout << "Top: " << s.peek() << endl;
    cout << "Popped: " << s.pop() << endl;
    return 0;
}
```

### 3.2 Stack Using Linked List

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node(int x) { data = x; next = NULL; }
};

class Stack {
    Node* top;
public:
    Stack() { top = NULL; }
    bool isEmpty() { return top == NULL; }
    void push(int x) {
        Node* newNode = new Node(x);
        newNode->next = top;
        top = newNode;
    }
    int pop() {
        if (isEmpty()) { cout << "Stack Underflow!" << endl; return -1; }
        int data = top->data;
        Node* temp = top;
        top = top->next;
        delete temp;
        return data;
    }
    int peek() { return (isEmpty()) ? -1 : top->data; }
};

int main() {
    Stack s;
    s.push(30);
    s.push(40);
    cout << "Top: " << s.peek() << endl;
    cout << "Popped: " << s.pop() << endl;
    return 0;
}
```

## 4. Problems & Solutions

### Problem 1: Reverse a String using Stack

```cpp
#include <iostream>
#include <stack>
using namespace std;

void reverseString(string str) {
    stack<char> s;
    for (char ch : str) s.push(ch);
    while (!s.empty()) { cout << s.top(); s.pop(); }
}

int main() {
    string str = "hello";
    reverseString(str);
    return 0;
}
```

### Problem 2: Check Balanced Parentheses

```cpp
#include <iostream>
#include <stack>
using namespace std;

bool isBalanced(string expr) {
    stack<char> s;
    for (char ch : expr) {
        if (ch == '(' || ch == '{' || ch == '[') s.push(ch);
        else {
            if (s.empty()) return false;
            char top = s.top(); s.pop();
            if ((ch == ')' && top != '(') || (ch == '}' && top != '{') || (ch == ']' && top != '['))
                return false;
        }
    }
    return s.empty();
}

int main() {
    string expr = "{[()]}";
    cout << (isBalanced(expr) ? "Balanced" : "Not Balanced") << endl;
    return 0;
}
```

## 5. Self-Practice Questions

1. Implement a stack using an array.
2. Implement a stack using a linked list.
3. Reverse a string using a stack.
4. Check if parentheses in an expression are balanced.
5. Convert infix expression to postfix notation.
6. Evaluate a postfix expression.
7. Implement a stack with min() function to return the minimum element in O(1) time.
8. Sort a stack using another stack.
9. Implement a queue using two stacks.
10. Implement two stacks using one array.
11. Find the next greater element for each element in an array using a stack.
12. Implement a stack that supports push, pop, top, and retrieving the maximum element.
13. Design a special stack that supports getMin(), getMax(), push(), and pop().
14. Implement a stack that supports middle element deletion in O(1) time.
15. Implement an LRU (Least Recently Used) Cache using a stack.
16. Check if a given stack sequence is valid or not.
17. Implement a stack that can store very large numbers.
18. Reverse a stack without using extra space.
19. Count the number of valid substrings using a stack.
20. Implement a monotonic increasing and decreasing stack.

This cheat sheet covers **everything** from **implementation, ADT, problems, and practice questions**—now it's time for you to master stacks! 🚀
