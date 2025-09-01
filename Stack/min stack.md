Here’s a full breakdown of **Min Stack problem** with **different approaches, code, time & space complexities, and explanations** in **Markdown style** 👇

---

# 🥇 Min Stack Problem

A **Min Stack** is a special stack that, in addition to standard stack operations (`push`, `pop`, `top`), supports retrieving the **minimum element** in constant time `O(1)`.

---

## ✅ Approach 1: Using Two Stacks

We maintain:

* **Main stack** → for storing all elements.
* **Min stack** → for storing the minimum at each level.

### Code (Java)

```java
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
```

### Complexity

* **Push**: `O(1)`
* **Pop**: `O(1)`
* **Top**: `O(1)`
* **GetMin**: `O(1)`
* **Space**: `O(n)` (two stacks)

---

## ✅ Approach 2: Using One Stack with Pairing

Instead of two stacks, store a **pair** `(value, minSoFar)` at each level.

### Code (Java)

```java
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

### Complexity

* **Push**: `O(1)`
* **Pop**: `O(1)`
* **Top**: `O(1)`
* **GetMin**: `O(1)`
* **Space**: `O(n)` (one stack but storing pairs)

---

## ✅ Approach 3: Optimized Single Stack with Encoding

We store only one stack and track the **min value separately**.
If a new element is **smaller than current min**, we **encode** it before pushing.

Formula:

* Push encoded value: `2*val - min`
* Update min
* Decode during pop

### Code (Java)

```java
class MinStack {
    Stack<Long> stack;
    long min;

    public MinStack() {
        stack = new Stack<>();
    }

    public void push(int val) {
        if (stack.isEmpty()) {
            stack.push((long) val);
            min = val;
        } else if (val < min) {
            stack.push(2L * val - min);
            min = val;
        } else {
            stack.push((long) val);
        }
    }

    public void pop() {
        if (stack.isEmpty()) return;

        long top = stack.pop();
        if (top < min) {
            min = 2 * min - top;  // restore previous min
        }
    }

    public int top() {
        long top = stack.peek();
        if (top < min) return (int) min;
        return (int) top;
    }

    public int getMin() {
        return (int) min;
    }
}
```

### Complexity

* **Push**: `O(1)`
* **Pop**: `O(1)`
* **Top**: `O(1)`
* **GetMin**: `O(1)`
* **Space**: `O(1)` extra (only one stack and one variable)

---

## 🔥 Comparison of Approaches

| Approach           | Extra Space | GetMin Time | Idea                       |
| ------------------ | ----------- | ----------- | -------------------------- |
| Two Stacks         | O(n)        | O(1)        | Keep a min stack           |
| One Stack (Pair)   | O(n)        | O(1)        | Store `(val, minSoFar)`    |
| Optimized Encoding | O(1)        | O(1)        | Encode values to track min |

---

👉 If interviewer asks:

* Start with **Approach 1** (easy & intuitive).
* Then say: "We can optimize space using encoding trick with `O(1)` extra space."

---

Do you want me to **dry run the optimized encoding approach** with an example (say `push(5), push(2), push(8), pop()…`) so it’s crystal clear how the encoding/decoding works?
