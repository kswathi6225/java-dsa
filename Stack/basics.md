## 📌 **What is a Stack?**

A **stack** is a **linear data structure** that follows the **LIFO (Last In, First Out)** principle.
Think of a **stack of plates** – you put a plate on top and remove from the top first.

---

## 📌 **Basic Operations on Stack**

1. **push(x)** → Insert an element into the stack.
2. **pop()** → Remove the top element.
3. **peek() / top()** → View the top element without removing it.
4. **isEmpty()** → Check if the stack is empty.
5. **size()** → Return the number of elements.

---
```java
import java.util.*;

public class StackJCF {
    public static void main(String args[]) {
        Stack<Integer> stack = new Stack<>();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);

        while(!stack.isEmpty()) {
            System.out.println(stack.peek());
            stack.pop();
        }
    }
}
```
----

## 📌 **Java Implementation of Stack (Using Array)**

```java
class Stack {
    int arr[];
    int top;
    int capacity;

    // Constructor
    Stack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }

    // Push element onto stack
    public void push(int x) {
        if (top == capacity - 1) {
            System.out.println("Stack Overflow");
            return;
        }
        arr[++top] = x;
        System.out.println(x + " pushed");
    }

    // Pop element from stack
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow");
            return -1;
        }
        return arr[top--];
    }

    // Peek top element
    public int peek() {
        if (!isEmpty()) {
            return arr[top];
        }
        return -1;
    }

    // Check if stack is empty
    public boolean isEmpty() {
        return top == -1;
    }

    // Get stack size
    public int size() {
        return top + 1;
    }
}

public class Main {
    public static void main(String[] args) {
        Stack st = new Stack(5);

        st.push(10);
        st.push(20);
        st.push(30);

        System.out.println("Top element: " + st.peek());
        System.out.println("Removed element: " + st.pop());
        System.out.println("Stack size: " + st.size());
    }
}
```

---

## 📌 **Input & Output**

**Input (operations):**

```
push(10)
push(20)
push(30)
peek()
pop()
size()
```

**Output:**

```
10 pushed
20 pushed
30 pushed
Top element: 30
Removed element: 30
Stack size: 2
```

---

## 📌 **Time Complexity**

* **Push** → O(1)
* **Pop** → O(1)
* **Peek** → O(1)
* **isEmpty / size** → O(1)

---

