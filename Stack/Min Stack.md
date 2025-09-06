# 🥇 Min Stack (Design a Stack that supports `getMin()` in O(1))

We need to design a stack that supports:
1. `push(x)` → Push element `x` onto stack.
2. `pop()` → Removes the element on top.
3. `top()` → Get the top element.
4. `getMin()` → Retrieve the minimum element in constant time.

---

## ✅ Approach 1: Using Two Stacks
- Maintain:
  - **Main stack** → Stores all elements.
  - **Min stack** → Stores the minimum at each step.

### Code (Java)
```java
import java.util.*;

class MinStack {
    Stack<Integer> stack;
    Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }

    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }

    public void pop() {
        if (stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
        stack.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return minStack.peek();
    }
}

public class Main {
    public static void main(String[] args) {
        MinStack ms = new MinStack();
        ms.push(-2);
        ms.push(0);
        ms.push(-3);
        System.out.println(ms.getMin()); // -3
        ms.pop();
        System.out.println(ms.top());    // 0
        System.out.println(ms.getMin()); // -2
    }
}
````

---

## ✅ Approach 2: Using One Stack with Pairs (Value, Min)

* Store pairs `(value, currentMin)` in stack.

### Code (Java)

```java
import java.util.*;

class MinStack {
    Stack<int[]> stack;

    public MinStack() {
        stack = new Stack<>();
    }

    public void push(int val) {
        if (stack.isEmpty()) {
            stack.push(new int[]{val, val});
        } else {
            int currentMin = stack.peek()[1];
            stack.push(new int[]{val, Math.min(val, currentMin)});
        }
    }

    public void pop() {
        stack.pop();
    }

    public int top() {
        return stack.peek()[0];
    }

    public int getMin() {
        return stack.peek()[1];
    }
}
```

---

## ⏱ Complexity

| Operation | Two-Stack Approach | One-Stack Approach        |
| --------- | ------------------ | ------------------------- |
| `push`    | O(1)               | O(1)                      |
| `pop`     | O(1)               | O(1)                      |
| `top`     | O(1)               | O(1)                      |
| `getMin`  | O(1)               | O(1)                      |
| Space     | O(n) (two stacks)  | O(n) (pairs in one stack) |

---

## ✅ Key Points

* Both approaches guarantee **O(1) min retrieval**.
* Approach 2 is space-optimized (stores value + min together).
* Approach 1 is easier to implement and more intuitive.

```

---

👉 Do you want me to also give the **Python version** of Min Stack (with both approaches) for practice side by side with Java?
```
